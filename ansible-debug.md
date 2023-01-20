# -Ansible Debug

IS a printing statement during execution and can be useful for debugging variables or expressions.

Parameters

msg&#x20;

var

&#x20;verbosity

msg

<pre><code>---  
hosts: localhost     
tasks: 
<strong>- debug: msg="this is sample test"
</strong><strong>
</strong></code></pre>

<pre><code>---  
- name: Debug Example Uptime  
hosts: localhost     
tasks:  
- name: Find Uptime  
  shell: /usr/bin/uptime  
  register: result  
   
- name: Print uptime  
<strong>  debug:  
</strong>   msg: {{result}}
   
   
   
---
  - name: Debug Example Uptime  
<strong>    hosts: localhost     
</strong>    tasks:  
<strong>    - name: Find Uptime  
</strong>     debug:
       msg: "Server IP adress ={{ansible_default_ipv4.adress}}"
       msg: "Server Hostname is={{inventory_hostname}}"
</code></pre>

