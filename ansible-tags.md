# Ansible Tags

If you have a large playbook, it becomes useful to be able to run only a specific part of it rather than running everything in the playbook. Ansible supports a tag attribute for this reason.

When you execute a playbook, you can filter tasks based on the tags in two ways, such as:

1. On the command line, with the **-tags** or **-skip-tags** options.
2. In Ansible configuration settings, with the **TAGS\_RUN** and **TAGS\_SKIP** options.

In Ansible, tags can be applied to many structures, but its simplest use is with individual tasks. Let's see an example that tags two tasks with different tags, such as:

```yaml
---
  - name: Playbook
    hosts: webservers
    become: yes
    become_user: root
    tasks:
      - name: ensure apache is at the latest version
        yum:
          name: httpd
          state: latest
        tags: check_latest_v    
      - name: ensure apache is running
        service:
          name: httpd
          state: started
        tags: start_service
```

```
ansible-playbook example.yml --tags=check_latest_v,start_service  
```

And if you want to run a playbook without certain tagged tasks, then you can use the **-skip-tags** command-line option.

```
ansible-playbook example.yml --skip-tags=start_service 
```
