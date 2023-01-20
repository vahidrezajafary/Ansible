# Ansible ad-hoc Commands

Ad-hoc commands are one of the simplest ways of using Ansible. These are used when you want to issue some commands on a server or bunch of servers. The ad-hoc commands are not stored for future use, but it represents a fast way to interact with the desired servers.

The Ansible ad-hoc command uses the **/usr/bin/ansible** command-line tool to automate a single task on one or more managed nodes. The Ad-hoc commands are quick and easy, but they are not re-usable. The Ad-hoc commands demonstrate the simplicity and power of Ansible.

\
<mark style="color:green;">**Syntax**</mark>

{% code lineNumbers="true" %}
```
ansible <hosts> [-m <module_name>] -a <"arguments"> -u <username> [--become]  
```
{% endcode %}

<mark style="color:green;">**Explanation**</mark>

<mark style="color:orange;">**Hosts**</mark>**:** It can be an entry in the inventory file. For specifying all hosts in the inventory, use all or "\*".

\
<mark style="color:orange;">**Module\_name**</mark>**:** It is an optional parameter. There are hundreds of modules available in the Ansible, such as **shell, yum, apt, file,** and **copy**. By default, it is the **command.**

<mark style="color:orange;">**Arguments**</mark>**:** We should pass values that are required by the module. It can change according to the module used.

\
<mark style="color:orange;">**Username**</mark>**:** It specifies the user account in which Ansible can execute commands.

\
<mark style="color:orange;">**Become**</mark>**:** It's an optional parameter specified when we want to run operations that need sudo privilege. By default, it becomes false.



### <mark style="color:green;"></mark>

<mark style="background-color:red;"><mark style="color:red;">**Note:**<mark style="color:red;"></mark> <mark style="background-color:red;"></mark><mark style="background-color:red;">For this method to work, you must already have password-based SSH access to your server.</mark>

<pre data-line-numbers><code> ssh-keygen -t rsa -b 4096
 cd ~/.ssh
 ls -ltrh
<strong> ssh-copy-id username@remote_host
</strong><strong> ssh username@remote_host
</strong></code></pre>

#### <mark style="background-color:red;"><mark style="color:red;">Note:<mark style="color:red;"></mark><mark style="background-color:red;">Disabl Password Authentication on your Server</mark> <a href="#step-4-disabling-password-authentication-on-your-server" id="step-4-disabling-password-authentication-on-your-server"></a>

{% code lineNumbers="true" %}
```
sudo nano /etc/ssh/sshd_config
PasswordAuthentication no
sudo systemctl restart ssh
ssh username@remote_host
```
{% endcode %}

\
<mark style="color:orange;">How to Execute an Ansible Ad-hoc</mark>
-------------------------------------------------------------------

Use <mark style="color:blue;">**`ansible`**</mark><mark style="color:blue;">** **</mark><mark style="color:blue;">****</mark> command to execute ad hoc command.

### <mark style="color:orange;">Some common commands</mark>

{% code lineNumbers="true" %}
```
ansible all -a "/sbin/reboot" -f 12  
ansible all -a "df -h" -u root
ansible servers -a "uptime" -u root
ansible server1:server2 -m ping -u root
ansible all -m apt -a "name=vim state=latest" -u root
ansible abc -m copy -a "src = /etc/yum.conf dest = /tmp/yum.conf"  
ansible abc -m file -a "dest = /creatdir/uservahid/new mode = 888 owner = uservahid group = uservahid state = directory"   
ansible abc -m file -a "dest = /creatdir/uservahid/new state = absent"  
ansible all -m user -a "name=vahid password=*******"  
ansible all -m user -a "name=vahid state=absent"  
ansible webservers -m service -a "name=httpd state=started"  
ansible webservers -m service -a "name=httpd state=restarted"  
ansible webservers -m service -a "name=httpd state=stopped"  
```
{% endcode %}



{% hint style="info" %}
By default, Ansible will run the above ad-hoc commands from the current user account. If you want to change then pass the username in ad-hoc command as follows:

<mark style="background-color:orange;">ansible all -a "df -h" -u root</mark>
{% endhint %}

### <mark style="color:orange;"></mark>

\
\


\










