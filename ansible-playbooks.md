# Ansible Playbooks

Playbooks are the files where the Ansible code is written. Playbooks are written in YAML format. **YAML** means "Yet Another Markup Language," so there is not much syntax needed. **Playbooks** are one of the core features of Ansible and tell Ansible what to execute, and it is used in complex scenarios. They offer increased flexibility.

\
Playbooks contain the steps which the user wants to execute on a particular machine. And playbooks are run sequentially. Playbooks are the building blocks for all the use cases of Ansible.

Ansible playbooks tend to be more configuration language than a programming language.Through a playbook, you can designate specific roles to some of the hosts and other roles to other hosts. By doing this, you can orchestrate multiple servers in very different scenarios, all in one playbook.\


## <mark style="color:green;">Playbook Structure</mark>

Each playbook is a collection of one or more plays. Playbooks are structured by using Plays. There can be more than one play inside a playbook.

\
<mark style="color:orange;">**Create a Playbook**</mark>

Let's start by writing an example YAML file. First, we must define a task. These are the interface to ansible modules for roles and playbooks.

One playbook with one play, containing multiple tasks looks like the below example.

{% code title="sample-playbook.yaml" %}
```
---
  - name: Playbook
    hosts: webservers
    become: yes
    become_user: root
    tasks:
      - name: ensure apache is at the latest version
        yum:
          name: httpd
          state: latest
      - name: ensure apache is running
        service:
          name: httpd
          state: started
```
{% endcode %}

{% hint style="info" %}
### <mark style="color:orange;">How to Execute an Ansible Playbook</mark>

\
Ansible playbook can be executed with <mark style="color:blue;">**`ansible-playbook`**</mark> command. like you have <mark style="color:blue;">**`ansible`**</mark><mark style="color:blue;">** **</mark><mark style="color:blue;">****</mark> command to execute ad hoc command. This is dedicated for ansible playbooks
{% endhint %}

### <mark style="color:orange;">Here are some YAML tags are given below, such as:</mark>

| Tags  | Explanation                                                                                                                                                                                                                                                                                                                                                                                              |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name  | It specifies the name of the Ansible Playbooks.                                                                                                                                                                                                                                                                                                                                                          |
| Hosts | It specifies the lists of the hosts against which you want to run the task. And the host's Tag is mandatory. It tells Ansible that on which hosts to run the listed tasks. These tasks can be run on the same machine or the remote machine. One can run the tasks on the multiple machines, and the host's tag can have a group of host's entry as well.                                                |
| Vars  | Vars tag defines the variables which you can use in your playbook. Its usage is similar to the variables in any programming language.                                                                                                                                                                                                                                                                    |
| Tasks | Tasks are the lists of the actions which need to perform in the playbooks. All the playbooks should contain the tasks to be executed. A task field includes the name of the task. It is not mandatory but useful for debugging the playbook. Internally each task links to a piece of code called a module. A module should be executed, and arguments that are required for the module you want to run. |



{% hint style="info" %}
## <mark style="color:orange;">Ansible Play vs Ansible Playbook?</mark>

**A **<mark style="color:blue;">**play**</mark> <mark style="color:blue;"></mark><mark style="color:blue;"></mark> is an ordered set of tasks which should be run against hosts selected from your inventory.

**A **<mark style="color:blue;">**playbook**</mark> is a text file that contains a list of one or more plays to run in order.
{% endhint %}

```
---
  # Play1 - WebServer related tasks
  - name: Play Web - Create apache directories and username in web servers
    hosts: webservers
    become: yes
    become_user: root
    tasks:
      - name: create username apacheadm
        user:
          name: apacheadm
          group: users,admin
          shell: /bin/bash
          home: /home/weblogic

      - name: install httpd
        yum:
          name: httpd
          state: installed
        
  # Play2 - Application Server related tasks
  - name: Play app - Create tomcat directories and username in app servers
    hosts: appservers
    become: yes
    become_user: root
    tasks:
      - name: Create a username for tomcat
        user:
          name: tomcatadm
          group: users
          shell: /bin/bash
          home: /home/tomcat

      - name: create a directory for apache tomcat
        file:
          path: /opt/oracle
          owner: tomcatadm
          group: users
          state: present
          mode: 0755
```

#### <mark style="color:orange;">How to Perform a Syntax Check on the Playbook</mark>

```
➜ ansible-playbook – syntax-check sampleplaybook.yml -i ansible_hosts
```

{% hint style="info" %}
### How to Dry Run the playbook without making Actual Changes

\
you can actually run the playbook with Dry Run feature to see what changes would be made to the server without having to perform the actual changes.

to do that. you just have to add <mark style="color:blue;background-color:orange;">`-C`</mark> to your ansible-playbook startup command



&#x20;<mark style="background-color:orange;">ansible-playbook -C sampleplaybook.yml -i ansible\_hosts</mark>
{% endhint %}

\
\
\


\
\
\
