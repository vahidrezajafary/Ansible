# Ansible Roles

Roles provide a framework for fully independent or interdependent collections of files, tasks, templates, variables, and modules.

The role is the primary mechanism for breaking a playbook into multiple files. This simplifies writing **complex playbooks** and makes them easier to reuse. The breaking of the playbook allows you to break the playbook into reusable components.

Each role is limited to a particular functionality or desired output, with all the necessary steps to provide that result either within the same role itself or in other roles listed as dependencies.

Roles are not playbooks. Roles are small functionality that can be used within the playbooks independently. Roles have no specific setting for which hosts the role will apply.

Top-level playbooks are the bridge holding the hosts from your inventory file to roles that should be applied to those hosts.

### &#x20;<mark style="color:orange;">**Creating a Role**</mark>

The directory structure for roles is essential to creating a new role, such as:

**Role Structure**

The roles have a structured layout on the file system. You can change the default structured of the roles as well.

**For example,** let us stick to the default structure of the roles. Each role is a directory tree in itself. So the role name is the directory name within the /roles directory.

{% code lineNumbers="true" %}
```
ansible-galaxy -h   
```
{% endcode %}

### <mark style="color:orange;">Usage</mark>

{% code lineNumbers="true" %}
```
ansible-galaxy [delete|import|info|init|install|list|login|remove|search|setup] [--help] [options] ...   
```
{% endcode %}

<mark style="color:orange;">**Options**</mark>

* \-h: (help) it shows this help message and exit.
* \-v: (verbose) Verbose mode (-vvv for more, -vvvv to enable connection debugging).
* \--version: it shows program version number and exit.

Roles are stored in separate directories and have a particular directory structure

```
[root@ansible-server]# tree  
.  
`-- role1  
    |-- defaults  
    |   `-- main.yml  
    |-- handlers  
    |   `-- main.yml  
    |-- meta  
    |   `-- main.yml  
    |-- README.md  
    |-- tasks  
    |   `-- main.yml  
    |-- tests  
    |   |-- inventory  
    |   `-- test.yml  
    `-- vars  
        `-- main.yml  
```

### <mark style="color:orange;">Explanation</mark>

* The YAML file in the default directory contains a list of default variables that are to be used along with the playbook.
* The handler's directory is used to store handlers.
* The meta-directory is supposed to have information about the author and role dependencies.
* The tasks directory is the main YAML file for the role.
* The tests directory contains a sample YAML playbook file and a sample inventory file and is mostly used for testing purposes before creating the actual role.
* The vars directory contains the YAML file in which all the variables used by the role will be defined. The directory templates and the directory files should contain files and templates that will be used by the tasks in the role.

### &#x20;



