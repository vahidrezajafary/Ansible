# Ansible Playbooks

Playbooks are the files where the Ansible code is written. Playbooks are written in YAML format. **YAML** means "Yet Another Markup Language," so there is not much syntax needed. **Playbooks** are one of the core features of Ansible and tell Ansible what to execute, and it is used in complex scenarios. They offer increased flexibility.

\
Playbooks contain the steps which the user wants to execute on a particular machine. And playbooks are run sequentially. Playbooks are the building blocks for all the use cases of Ansible.

Ansible playbooks tend to be more configuration language than a programming language.Through a playbook, you can designate specific roles to some of the hosts and other roles to other hosts. By doing this, you can orchestrate multiple servers in very different scenarios, all in one playbook.\


## <mark style="color:green;">Playbook Structure</mark>

Each playbook is a collection of one or more plays. Playbooks are structured by using Plays. There can be more than one play inside a playbook.

The function of the play is to map a set of instructions which is defined against a particular host.

\
Create a Playbook

Let's start by writing an example YAML file. First, we must define a task. These are the interface to ansible modules for roles and playbooks.

One playbook with one play, containing multiple tasks looks like the below example.

{% code title="sample-playbook.yaml" %}
```
---  
   name: install and configure DB  
   hosts: testServer  
   become: yes  
  
   vars:   
      oracle_db_port_value : 1521  
     
   tasks:  
   -name: Install the Oracle DB  
      yum: <code to install the DB>  
      
   -name: Ensure the installed service is enabled and running  
   service:  
      name: <your service name>  
```
{% endcode %}



### <mark style="color:orange;">Here are some YAML tags are given below, such as:</mark>

| Tags  | Explanation                                                                                                                                                                                                                                                                                                                                                                                              |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name  | It specifies the name of the Ansible Playbooks.                                                                                                                                                                                                                                                                                                                                                          |
| Hosts | It specifies the lists of the hosts against which you want to run the task. And the host's Tag is mandatory. It tells Ansible that on which hosts to run the listed tasks. These tasks can be run on the same machine or the remote machine. One can run the tasks on the multiple machines, and the host's tag can have a group of host's entry as well.                                                |
| Vars  | Vars tag defines the variables which you can use in your playbook. Its usage is similar to the variables in any programming language.                                                                                                                                                                                                                                                                    |
| Tasks | Tasks are the lists of the actions which need to perform in the playbooks. All the playbooks should contain the tasks to be executed. A task field includes the name of the task. It is not mandatory but useful for debugging the playbook. Internally each task links to a piece of code called a module. A module should be executed, and arguments that are required for the module you want to run. |

\


\
\
\
