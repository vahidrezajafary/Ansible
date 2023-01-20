# Ansible Templates

Ansible template module helps to template a file out to a remote server.

\


### What does Ansible template module do

Ansible template module does two things

1. Replace the Jinja2 interpolation syntax variables present in the template file with actual values
2. copy (scp) the file to the remote server.

### Example of Ansible template module

Save this script as old.`sh` or `old.sh.j2`   the J2 is an identifier and file extension for Jinja2 files but it’s not mandatory to save the source/template file with that extension.

```
#!/bin/bash

# Script find and type of files which are N days older

find {{DIR}} -type f -name {{FILEEXT}} -mtime +{{DAYSOLD}}
```

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

#### Ansible Playbook with Ansible template

Here is the ansible playbook to copy this file to the remote server and execute.

```
---
    - name: Template Example
      hosts: web_servers
      tasks:
        - name: Template module to interpolate variables and copy the file
          template:
            src: old.sh
            dest: /tmp/old.sh
            owner: root
            group: root
            mode: 0755
        
        - name: Execute the script
          become: true
          shell:
            /tmp/old.sh
          register: scroutput
          
        - debug: var=scroutput.stdout_lines
```
