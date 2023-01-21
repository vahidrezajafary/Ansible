# -Ansible Debug

Is a printing statement during execution and can be useful for debugging variables or expressions.

Parameters

<mark style="color:orange;">**1- msg**</mark>&#x20;

<mark style="color:orange;">**2- var**</mark>

<mark style="color:orange;">**3- verbosity**</mark>

### <mark style="color:green;">1- Explain msg :</mark>

```
---  
hosts: localhost     
tasks: 
- debug: msg="this is sample test"
```



### <mark style="color:green;">2- Explain Var</mark>

```yaml
---  
- name: Debug Example Uptime  
hosts: localhost     
tasks:  
- name: Find Uptime  
  shell: /usr/bin/uptime  
  register: result  
   
- name: Print uptime  
  debug:  
   msg: {{result}}
   
   
   
---
  - name: Debug Example Uptime  
    hosts: localhost     
    tasks:  
    - name: Find Uptime  
     debug:
       msg: "Server IP adress ={{ansible_default_ipv4.adress}}"
       msg: "Server Hostname is={{inventory_hostname}}"
```

### <mark style="color:green;">**3- Explain verbosity**</mark>

```
---  
- name: Debug Example Uptime  
hosts: localhost     
tasks:  
- name: verbocity is default
  debug:  
   msg: "verbocirty is default"   
  
- name: verbocity is 3
  debug:  
   msg: "verbosity is 3"   
   verbosity: 3
  
```

