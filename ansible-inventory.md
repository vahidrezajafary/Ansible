# Ansible Inventory

Ansible works against multiple managed hosts in your infrastructure at the same time, using a list or group of lists is known as the inventory.

Once an inventory is defined, you use patterns to select the hosts or groups you want to run against to Ansible.

The default location for inventory is a file called **/etc/ansible/hosts**. You can also specify a different inventory file at the command line using the **-i \<path>** option. You can pull the inventory file from dynamic or cloud sources or different formats (YAML, ini). Ansible has inventory plugins to make it flexible and customize.

#### Hosts and group

The format is /etc/ansible/ hosts are in INI like format, such as:

```
  
[webservers]  
10.10.10.1
10.10.10.2 
  
[dbservers]  
10.10.11.1
10.10.11.2
10.10.11.3 

[monitoring_servers]
10.10.12.1
```

{% hint style="info" %}
If you have hosts that run on a non-standard SSH port, then you can put the port number after the hostname with the colon



srv1-example.com:5450

10.10.15.1:5450&#x20;
{% endhint %}

#### Hosts Variables

You can assign the variables to the hosts that will be used in playbooks, such as:

```
path: /opt/tomcat10
src: https://mirrors.estointernet.in/apache/tomcat/tomcat-10/v10.0.4/bin/apache-tomcat- 10.0.4.tar.gz
```



