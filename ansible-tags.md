# Ansible Tags

If you have a large playbook, it becomes useful to be able to run only a specific part of it rather than running everything in the playbook. Ansible supports a tag attribute for this reason.

When you apply tags on things, then you can control whether they are executed by adding command-line options.

When you execute a playbook, you can filter tasks based on the tags in two ways, such as:

1. On the command line, with the **-tags** or **-skip-tags** options.
2. In Ansible configuration settings, with the **TAGS\_RUN** and **TAGS\_SKIP** options.

In Ansible, tags can be applied to many structures, but its simplest use is with individual tasks. Let's see an example that tags two tasks with different tags, such as:

```yaml
tasks:  
- yum:  
    name: "{{ item }}"  
    state: present  
  loop:  
  - httpd  
  - memcached  
  tags:  
  - packages  
  
- template:  
    src: templates/src.j2  
    dest: /etc/foo.conf  
  tags:  
  - configuration  
```
