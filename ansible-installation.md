---
description: >-
  When you have compared and weighed your options and decided to go for Ansible.
  Then install it on your system. Let's go step by step of the installation in
  different Linux distributions.
---

# Ansible Installation

### <mark style="color:orange;">Install Ansible on RedHat/Centos systems</mark> 

**Step 1:** Install the EPEL repo

```
 sudo yum install epel-release
```

**Step 2:** Install the Ansible package.

```
sudo yum install -y ansible  
```



### <mark style="color:orange;">Install Ansible on Debian/Ubuntu systems:</mark>

**Step 1:** First perform an update to the packages

```
 sudo apt update  
```

****

**Step 2:** Then install the software properties common package.

```
sudo apt install software-properties-common 
```



**Step 3:** And install the Ansible personal package archive.

```
 sudo apt-add-repository ppa:ansible/ansible  
```

****

**Step 4:** Install the Ansible.

```
 sudo apt update  
 sudo apt install ansible
```

### <mark style="color:purple;background-color:blue;">**All in one Code**</mark> &#x20;

```
 sudo apt update  && \
 sudo apt install software-properties-common && \
 sudo apt-add-repository ppa:ansible/ansible  && \
 sudo apt update  && \
 sudo apt install ansible
 
```

### <mark style="color:orange;">Setting Up the Inventory File</mark>

{% hint style="info" %}
**Note**: some Ansible installations won’t create a default inventory file. If the file doesn’t exist in your system, you can create a new file at `/etc/ansible/hosts` or provide a custom inventory path using the `-i` parameter when running commands and playbooks.
{% endhint %}

#### sudo nano /etc/ansible/hosts

```
[web_servers]
server1 ansible_host=188.15.16.17
server2 ansible_host=188.15.16.18
server3 ansible_host=188.15.16.19

[db_servers]
server1 ansible_host=10.10.10.1
server2 ansible_host=10.10.10.2
server3 ansible_host=10.10.10.3
```

### <mark style="color:orange;">Check your inventory:</mark>

```
ansible-inventory --list -y
```

#### <mark style="color:orange;">Testing Connection</mark> <a href="#step-3-testing-connection" id="step-3-testing-connection"></a>

```
ansible all -m ping -u root
ansible server1:server2 -m ping -u root
ansible servers -a "uptime" -u root

```

### <mark style="color:orange;"></mark> <mark style="color:orange;"></mark> <mark style="color:orange;"></mark>
