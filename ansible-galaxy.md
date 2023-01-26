# Ansible Galaxy

Ansible Galaxy is a galaxy website where users can share roles and to a command-line tool for **installing, creating,** and **managing** roles.

{% embed url="https://galaxy.ansible.com/home" %}

#### <mark style="color:orange;">Configure Ansible for Amazon Web Services</mark>

## Configure Ansible for AWS <a href="#a9db" id="a9db"></a>

* AWS Access key
* Python boto3 requires 3.6+
* Ansible collection `amazon.aws`



Step 1 : Amazon IAM Access Key&#x20;

Make env.sh

```
#!/bin/bash
export AWS_ACCESS_KEY_ID="RED-CODE"
export AWS_SECRET_ACCESS_KEY="GREEN-CODE"
export AWS_DEFAULT_REGION="us-east-1"
```

#### <mark style="color:orange;">Install Python boto3 SDK</mark>

```
pip3.8 install boto3
pip3.8 list | grep boto
```

#### <mark style="color:orange;">Install Ansible</mark> <mark style="color:orange;"></mark><mark style="color:orange;">`amazon.aws`</mark> <mark style="color:orange;"></mark><mark style="color:orange;">collection</mark> <a href="#776c" id="776c"></a>

```
ansible-galaxy collection install --force amazon.aws
ansible-galaxy collection list amazon.aws
```

#### <mark style="color:orange;">Run Ansible Playbook</mark> <a href="#375e" id="375e"></a>

```
source env.sh
ansible-playbook ami_search.yml 
```

```



```



\
