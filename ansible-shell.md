# Ansible Shell

Ansible shell module is designed to execute the shell commands against the target UNIX based hosts. Ansible can run except any high complexes commands with pipes, redirection. And you can also perform the shell scripts using the Ansible shell module.

The main advantage of the Ansible shell is except any high complexes commands with pipes and semicolons can be a disadvantage from the security perspective as a single mistake could cost a lot and break the system integrity.

* The Ansible shell module is designed to work only with LINUX based machines and not for the windows. For windows, you should use the <mark style="color:orange;">**win\_shell**</mark>
* Ansible shell module can be used to execute shell scripts. Ansible has a dedicated module named script, which is used to copy the shell script from the control machine to the remote server.

Let see the syntax of how to use the Ansible shell module in the playbook and Adhoc:

####

{% hint style="info" %}
```
sudo nano /etc/ansible/hosts

[web_servers]
server1 ansible_host=188.15.16.17
server2 ansible_host=188.15.16.18
server3 ansible_host=188.15.16.19
```
{% endhint %}



```
---  
-name: Shell command example   
Hosts: web_servers
tasks:  
-name: check date with the shell command  
shell:  
"date"  
register: datecmd  
tags: datecmd  
-debug: msg= "{{datecmd.stdout}}"  

```

In the above example, we are running our playbook against a hostgroup named **web\_servers** and executing a simple date command and saving the output of that command into a **Register** variable named **datecmd**.

At the last line, we retrieve the registered variable and printing only the date command output stored in the **stdout** property of **datecmd**.
