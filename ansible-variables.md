# Ansible Variables

Ansible playbook supports defining the variable in two forms, Either as a separate file with full of variables and values like a properties file. or a Single liner variable declaration like we do in any common programming languages

<mark style="background-color:orange;">vars</mark> to define inline variables within the playbook

<mark style="background-color:orange;">vars\_files</mark> to import files with variables

Let’s suppose we want to add a few for our webserver like the server name and SSL key file and cert file etc.

{% hint style="danger" %}
Tips:

1- Allways use variables under \{{ variables-name\}}&#x20;

2- when use variables in start of Line shuld use "\{{ variables-name\}}" format

3- Dont use "Hyphen" in Variables Name
{% endhint %}

<mark style="color:orange;">**Method 1**</mark> : it can be done with <mark style="background-color:orange;">vars</mark> like this

{% code title="Tomcat_playbook.yml" %}
```yaml
---
- name: Install Apache Tomcat10 using ansible
  hosts: webserver
  remote_user: ubuntu
  become: true
  tasks:
    - name: Update the System Packages
      apt:
        upgrade: yes
        update_cache: yes
 
    - name: Create a Tomcat User
      user:
        name: tomcat
 
    - name: Create a Tomcat Group
      group:
        name: tomcat
 
    - name: Install JAVA
      apt:
        name: default-jdk
        state: present
 
 
    - name: Create a Tomcat Directory
      file:
        path: /opt/tomcat10
        owner: tomcat
        group: tomcat
        mode: 755
        recurse: yes
 
    - name: download & unarchive tomcat10 
      unarchive:
        src: https://mirrors.estointernet.in/apache/tomcat/tomcat-10/v10.0.4/bin/apache-tomcat- 10.0.4.tar.gz
        dest: /opt/tomcat10
        remote_src: yes
        extra_opts: [--strip-components=1]
 
    - name: Change ownership of tomcat directory
      file:
        path: /opt/tomcat10
        owner: tomcat
        group: tomcat
        mode: "u+rwx,g+rx,o=rx"
        recurse: yes
        state: directory
 
    - name: Copy Tomcat service from local to remote
      copy:
        src: /etc/tomcat.service
        dest: /etc/systemd/system/
        mode: 0755
 
    - name: Start and Enable Tomcat 10 on sever
      systemd:
        name: tomcat
        state: started
        daemon_reload: true
﻿
```
{% endcode %}



{% code title="variables_playboock.yml" %}
```yaml
----
- name: Install Apache Tomcat10 
  hosts: webserver
  remote_user: ubuntu
  become: true
  vars:
    - var_path_Tomcat: 
    - var_src_Tomcat: 
  
  tasks:
    - name: Update the System Packages
      apt:
        upgrade: yes
        update_cache: yes
 
    - name: Create a Tomcat User
      user:
        name: tomcat
 
    - name: Create a Tomcat Group
      group:
        name: tomcat
 
    - name: Install JAVA
      apt:
        name: default-jdk
        state: present
 
 
    - name: Create a Tomcat Directory
      file:
        path: {{var_path_Tomcat}}
        owner: tomcat
        group: tomcat
        mode: 755
        recurse: yes
 
    - name: download & unarchive tomcat10 
      unarchive:
        src: {{var_src_Tomcat}}
        dest: /opt/tomcat10
        remote_src: yes
        extra_opts: [--strip-components=1]
 
    - name: Change ownership of tomcat directory
      file:
        path: /opt/tomcat10
        owner: tomcat
        group: tomcat
        mode: "u+rwx,g+rx,o=rx"
        recurse: yes
        state: directory
 
    - name: Copy Tomcat service from local to remote
      copy:
        src: /etc/tomcat.service
        dest: /etc/systemd/system/
        mode: 0755
 
    - name: Start and Enable Tomcat 10 on sever
      systemd:
        name: tomcat
        state: started
        daemon_reload: true
```
{% endcode %}

<mark style="background-color:orange;">**Method 2**</mark>**:**<mark style="background-color:orange;">vars\_files</mark> to import files with variables

#### create  vars\_of\_tomcat.yml file

```
          path: /opt/tomcat10
          src: https://mirrors.estointernet.in/apache/tomcat/tomcat-10/v10.0.4/bin/apache-tomcat- 10.0.4.tar.gz
```

{% code title="Vars_files_tomcat.yml" %}
```yaml
----
- name: Install Apache Tomcat10 
  hosts: webserver
  remote_user: ubuntu
  become: true
  vars_files:
      - vars_of_tomcat.yml 
  
  tasks:
    - name: Update the System Packages
      apt:
        upgrade: yes
        update_cache: yes
 
    - name: Create a Tomcat User
      user:
        name: tomcat
 
    - name: Create a Tomcat Group
      group:
        name: tomcat
 
    - name: Install JAVA
      apt:
        name: default-jdk
        state: present
 
 
    - name: Create a Tomcat Directory
      file:
        path: {{var_path_Tomcat}}
        owner: tomcat
        group: tomcat
        mode: 755
        recurse: yes
 
    - name: download & unarchive tomcat10 
      unarchive:
        src: {{var_src_Tomcat}}
        dest: /opt/tomcat10
        remote_src: yes
        extra_opts: [--strip-components=1]
 
    - name: Change ownership of tomcat directory
      file:
        path: /opt/tomcat10
        owner: tomcat
        group: tomcat
        mode: "u+rwx,g+rx,o=rx"
        recurse: yes
        state: directory
 
    - name: Copy Tomcat service from local to remote
      copy:
        src: /etc/tomcat.service
        dest: /etc/systemd/system/
        mode: 0755
 
    - name: Start and Enable Tomcat 10 on sever
      systemd:
        name: tomcat
        state: started
        daemon_reload: true
```
{% endcode %}









####

