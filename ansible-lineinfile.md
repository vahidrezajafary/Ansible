# Ansible lineinfile

Ansible lineinfile module could be the saviour of your day when you want to work with files and especially modify their content on the run, like adding a new line in the file or updating a line in the file or replace a line in the file when certain text is found and much more.

lineinfile has a various set of examples and it provides many parameters to get your job done easily. In this post, we are going to see the ansible lineinfile module in action with examples.

### <mark style="color:orange;">The Ansible lineinfile module</mark>

\
Ansible lineinfile module is helpful when you want to add, remove, modify a single line in a file.  You can also use conditions to match the line before modifying or removing using the regular expressions. You can reuse and modify the matched line using the back reference parameter.

Consider yourself having any of these following requirement

1. Add a line when it is not already present.
2. Change the port number in the configuration file
3. Disable the SSL when the SSL is enabled
4. Add a new entry in the /etc/hosts file
5. Upgrade the package version when the installed version is matching your regular expression
6. Remove a username from /etc/passwd file using regex

Hope this sets the context. Before we proceed with the examples Something to be highlighted.

{% hint style="info" %}
> Ansible Lineinfile can be used only for working a single line in a file. If you want to replace mutiple lines try [replace](https://docs.ansible.com/ansible/latest/modules/replace\_module.html#replace-module) module or use [blockinfile](https://docs.ansible.com/ansible/latest/modules/blockinfile\_module.html#blockinfile-module) if you want to insert/update/remove a block of lines in a file.
{% endhint %}

### <mark style="color:orange;">Ansible lineinfile examples</mark>

We have gathered various examples of ansible lineinfile here.  These are examples we have covered in this post. you can choose to read all or any specific example.

* Validate if a line is present without any modification
* Validate if a line is present in the file and **add** if it does not exist
* Replace a Line in a file If it is found with ansible lineinfile
* Remove a line from the file if it is found – All the instances
* Insert before a matching line using **insertbefore** parameter
* Insert after the matching line using **insertafter** parameter
* validate the changes are correct before saving

\
<mark style="color:orange;">**Example 1: Validate if a line is present in the file without any modification.**</mark>

\
**This is just to validate if a line is present in the file or not**. It will not modify the file irrespective of whatsoever the result is. this is just like running the quick find command

The Example given below is to find whether or not the String “**validate**” is found in the remote file.

{% hint style="info" %}
**As mentioned earlier. There would be no action taken whatsoever.**
{% endhint %}

In this example we are going to check if the vahiddate is and print the message If it is there or not and take no action. This is being done with the help of `checkmode=yes`

\


```
vi /etc/vahid/sample_ansible_file.txt
This is just to validate if a line is present in the file or not
```

```
---
  - name: Examples of lineinfile
    hosts: node-01
    
    tasks:
      - name: "Example1: Validate if a String or line is present in the file"
        become: yes
        become_user: root
        tags: example1
        lineinfile:
          path: /etc/vahid/sample_ansible_file.txt
          line: "validate"
          state: present
          backup: yes
        check_mode: yes
        register: example1out
```

{% hint style="danger" %}
&#x20;It is recommended to always have the **`backup: yes`** parameter in your playbook when you are using the lineinfile. This would make sure the file is backed up before any changes are made. This would help in case if you want to roll back.
{% endhint %}



```
Here is the Quick ad-hoc command to check what is the actual LogLevel in the remote httpd.conf file

ansible node-01 -m shell -a "grep -i validate /etc/vahid/sample_ansible_file.txt" -i ansible_hosts
```

#### <mark style="color:orange;">Example2: Validate if a String or line is present in the file and</mark> <mark style="color:orange;"></mark>_<mark style="color:orange;">**add**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">if it does not exist</mark>_

In the same playbook, we have just seen if we remove the check mode it would be a valid playbook which searches  for a line and adds it when there are no matches found

\
But there is a problem here the line you are mentioning to be added would be added only at the End Of File or Last line. This can be controlled with insert\_before and insert\_before directives which will be discussed later in this article.

```
---
  - name: Examples of lineinfile
    hosts: node-01
    
    tasks:
      - name: "Example2: Add the line if it does not exist"
        become: yes
        become_user: root
        tags: example2
        lineinfile:
          path: /etc/vahid/sample_ansible_file.txt
          line: "validate"
          state: present
          backup: yes
        register: example2out
```

The result of this would result in a invalid configuration file as the entry would be added at the End Of File.

<mark style="color:orange;">**Example3: Replace a line in a file with ansible lineinfile.**</mark>

In the example2 we have seen how to add a new line with lineinfile module. Now we are going to see how to replace a line when a Certain line is found.

Though you can use the ansible replace module to replace. The Lineinfile module can also be used to replace a line.

{% hint style="info" %}
In the below example, we are commenting on a line. The full line is captured line by placing them inside the parenthesis to '\1'. The '#\1' replaces the line with '#' followed by what was captured.

You can have multiple captures and call them by using '\1', '\2', '\3' etc.
{% endhint %}

\


```yaml
    ---
  - name: Examples of lineinfile
    hosts: web
    
    tasks:
      - name: "Example1:  commenting on a line"
        become: yes
        become_user: root
        tags: example1
        lineinfile:
          path: /etc/vahid/sample_ansible_file.txt
          # The String to Search
          regexp: '(inventory = /home/fedora/inventory.ini.*)'  
          # The String to Replace
          line: '#\1'
          state: present
          backup: yes
        
        register: example1out
```

{% hint style="info" %}
#### Would it Replace all the Matching Lines? What if there are More than one Matches

#### If there are more than one matches in the file. Ansible Lineinfile would replace only the last line matched or found.

If you would like to replace all the occurrences, you must consider using the replace module and not lineinfile.\

{% endhint %}

### <mark style="color:orange;">Removing a Line</mark>

Set the state parameter to absent or remove the line specified. All the occurrence of that line will be removed.

```
 ---
  - name: Examples of lineinfile
    hosts: all   
    tasks:
      - name: "Example1: Ansible lineinfile remove the line "
        become: yes
        become_user: root
        tags: example1
        lineinfile:
          path: /etc/vahid/sample_ansible_file.txt
          line: Removed lines. 
          state: absent  
          backup: yes
        register: example1out  
```

\


\
\
