---
description: >-
  When you have compared and weighed your options and decided to go for Ansible.
  Then install it on your system. Let's go step by step of the installation in
  different Linux distributions.
---

# Ansible Installation

### <mark style="color:orange;">Install Ansible on RedHat/Centos systems</mark> 

**Step 1:** Install the EPEL repo

{% code lineNumbers="true" %}
```
 sudo yum install epel-release
```
{% endcode %}

**Step 2:** Install the Ansible package.

{% code lineNumbers="true" %}
```
sudo yum install -y ansible  
```
{% endcode %}



### <mark style="color:orange;">Install Ansible on Debian/Ubuntu systems:</mark>

**Step 1:** First perform an update to the packages

{% code lineNumbers="true" %}
```
 sudo apt update  
```
{% endcode %}

****

**Step 2:** Then install the software properties common package.

{% code lineNumbers="true" %}
```
sudo apt install software-properties-common 
```
{% endcode %}



**Step 3:** And install the Ansible personal package archive.

{% code lineNumbers="true" %}
```
 sudo apt-add-repository ppa:ansible/ansible  
```
{% endcode %}

****

**Step 4:** Install the Ansible.

{% code lineNumbers="true" %}
```
 sudo apt update  
 sudo apt install ansible
```
{% endcode %}

\
\
