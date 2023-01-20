# Ansible Modules

Ansible modules are discrete units of code which can be used from the command line or in a playbook task.

The modules also referred to as task plugins or library plugins in the Ansible.

Ansible ships with several modules that are called **module library**, which can be executed directly or remote hosts through the playbook.

Users can also write their modules. These modules can control like **services, system resources, files,** or **packages,** etc. and handle executing system commands.

Let's see how to execute three different modules from the command line.

```
ansible webservers -m service -a "name=httpd state=started"  
ansible webservers -m ping  
ansible webservers -m command -a "/sbin/reboot -t now"  
```

Each module supports taking arguments. Mainly all modules take **key=value** arguments, space delimited.

Some module takes no arguments, and the shell/command modules take the string of the command which you want to execute.

From playbook, Ansible modules execute in a very similar way, such as:

```
- name: reboot the servers  
  command: /sbin/reboot -t now  
```

Here is another way to pass arguments to a module that is using **YAML syntax**, and it is also called complex args.

```
- name: restart webserver  
  service:  
    name: httpd  
    state: restarted  
```



Modules should be idempotent and avoid making any changes if they detect that the current state matches the desired final state. When using Ansible playbooks, these modules can trigger "**change events**" in the form of notifying "**handlers**" to run additional tasks.

\
