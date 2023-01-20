# Ansible Variables

In playbooks, the variable is very similar to using the variables in a programming language. It helps you to assign a value to a variable and use it anywhere in the playbook. You can put the conditions around the value of the variables and use them in the playbook accordingly.

#### Creating Valid Variable Names

Before start using variables, it's important to know what valid variable names are.

Variable names should be letters, numbers, and underscores. The variable should always start with a letter.

foo\_port and foo2 both are the correct or valid variable names.

Foo-port, foo port, foo.port, and 10foo all are invalid variable names.

YAML supports dictionaries that map keys to values. For instance:

```
foo:  
  field1: one  
  field2: two  
```

Then you can reference a specific field in the dictionary using either bracket notation or dot notation:

```
foo['field1']  
foo.field1  
```

Both will reference the same value "one". But, if you choose to use dot notation, be aware that some keys can cause problems because they collide with the attributes and methods of python dictionaries. You should use bracket notation instead of dot notation if you use keys which start and end with two underscores or any of the known public attributes:

#### Example

```
- hosts : <your hosts>   
vars:  
tomcat_port : 8080   
```

In the above example, defined a variable name **tomcat\_port** and assigned the value 8080 to the variable and can use it in your playbook wherever required.

The below code is from one of the roles (install-tomcat), such as:

```
block:   
   - name: Install Tomcat artifacts   
      action: >   
      yum name = "demo-tomcat-1" state = present   
      register: Output   
            
   always:   
      - debug:   
         msg:   
            - "Install Tomcat artifacts task ended with message: {{Output}}"   
            - "Installed Tomcat artifacts - {{Output.changed}}"   
```

#### Explanation

* **block:** The Ansible syntax to execute a given block.
* **name:** It is used in logging and helps in debugging which all blocks were successfully executed.
* **action:** The action is an Ansible keyword used in YAML.
* **register:** The output of the action tag is registered by using the register keyword.
* **always:** It is also an Ansible keyword; it says that below will still be executed.
* **msg:** It displays the message.

