# Page 1

The lineinfile is one of the most powerful modules in the Ansible toolbox. Ansible lineinfile module is used to insert a line, modify, remove, and replace an existing line.

Ansible lineinfile module saves your time when you work with the file and modify their content on the run, such as adding a new line in the file or updating, replace a line in the file when specific text is found, and much more.

Ansible lineinfile provides many parameters to do the job quickly. You can also use the condition to match the line before modifying, removing using the regular expressions. You can reuse and modify the matched line using the backreference parameter.

{% hint style="info" %}
**NOTE: Ansible lineinfile can be used only for working a single line in a file. If you want to replace multiple lines, replace the module, and if you're going to insert, update, remove a block of lines in a file use blockinfile module.**
{% endhint %}

The below example will write the line "Inserting a line in a file" to the file "_remote\_server.txt_". The new line will be added to the EOF. If the line is already existing, then it will not be combined.

You can also set the **create** parameter, which says if the file is not present, then create a new file. The default value for the state is **present**.

### <mark style="color:orange;">Insert a Line</mark>

```
- hosts: loc  
  tasks:  
    - name: Ansible insert lineinfile   
      lineinfile:  
        dest: /home/javaTpoint/remote_server.txt  
        line: Inserting a line in a file.  
        state: present  
        create: yes
```

### <mark style="color:orange;">Removing a Line</mark>

Set the state parameter to absent or remove the line specified. All the occurrence of that line will be removed.

```
- hosts: loc  
  tasks:  
    - name: Ansible lineinfile remove the line  
      lineinfile:  
        dest: /home/javaTpoint/remote_server.txt  
        line: Removed lines.  
        state: absent 
```

### <mark style="color:orange;">Replacing or Modifying a Line</mark>

To modify a line, you need to use the Ansible backrefs parameter along with the regexp parameter. This should be used with state=present.

If the regexp does not match any line, then the file is not changed. If the regexp matches a line or multiple lines, then the last matched line will be replaced. The grouped elements in regexp are populated and can be used for modification.

In the below example, we are commenting on a line. The full line is captured line by placing them inside the parenthesis to '\1'. The '#\1' replaces the line with '#' followed by what was captured.

You can have multiple captures and call them by using '\1', '\2', '\3' etc.



<mark style="color:orange;">**Commenting a line with Ansible lineinfile backrefs**</mark>

```
- name: Ansible lineinfile regexp replace the example  
  lineinfile:  
    dest: /etc/ansible/ansible.cfg  
    regexp: '(inventory = /home/fedora/inventory.ini.*)'  
    line: '#\1'  
    backrefs: yes  
```

<mark style="color:orange;">**Uncommenting the line with lineinfile regexp**</mark>

```
- name: Ansible lineinfile backrefs example  
  lineinfile:  
    dest: /etc/ansible/ansible.cfg  
    regexp: '#(inventory = /home/fedora/inventory.ini.*)'  
    line: '\1'  
    backrefs: yes 
```

\
\
