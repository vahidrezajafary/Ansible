# Ansible Tower

Ansible Tower is like Ansible at a more enterprise level. It is a web-based solution for managing your organization with an easy user interface that provides a dashboard with all of the state summaries of all the hosts. And allows quick deployments, and monitors all configurations.\
\
The tower allows us to share the **SSH** credentials without exposing them, logs all the jobs, manage inventories graphically, and syncs them with a wide variety of cloud providers.

Previously, Ansible Tower called the **AWX** project, is the fix to this problem. Especially those that render better as graphical rather than text-based output, such as real-time node monitoring.

<figure><img src=".gitbook/assets/6.jpg" alt=""><figcaption></figcaption></figure>

### <mark style="color:green;">Prerequisites to Install Ansible Tower</mark>

* RedHat Enterprise Linux 6 64-bit
* RedHat Enterprise Linux 7 64-bit
* CentOS 6 64-bit
* CentOS 7 64-bit
* Ubuntu 12.04 LTS 64-bit
* Ubuntu 14.04 LTS 64-bit
* Ubuntu 16.04 LTS 64 bit



* You should have the latest stable release of Ansible.
* It required a 64-bit support kernel, runtime, and 20 GB hard disk.
* Minimum 2 GB RAM (4 GB RAM recommended) is required.
  * Minimum 2 GB RAM is recommended for Vagrant trial installations
  * And 4 GB RAM is recommended /100 forks

### <mark style="color:green;">Ansible Tower Features</mark>

<figure><img src=".gitbook/assets/7.png" alt=""><figcaption></figcaption></figure>

\
**1. Ansible Tower Dashboard:** It displays everything which is going on in your Ansible environment, such as the inventory status, the recent job activity, the hosts, and so on.

**2. Multi-Playbook Workflows:** It allows to chain any numbers of playbooks, any way of the usage of different inventories, runs different users, or utilizes various credentials.

**3. Real-Time Job Updates:** Ansible can automate the complete infrastructure. Also, you can see real-time job updates such as plays and tasks broken down by each machine either been successful or failure. Therefore you can see the status of your automation and know what's next in the queue.

**4. Scale Capacity with Cluster:** You can connect multiple Ansible Tower nodes into an Ansible Tower cluster as the clusters add redundancy and capacity, which allows scaling Ansible automation across the enterprise.

**5. Self-Service:** You can launch playbooks with just a single click through this feature.

**6. Remote Command Execution:** With this command, you can run simple tasks such as restart any malfunctioning service, add users, reset passwords on any host or group of hosts in the inventory.

**7. Manage and Track Inventory:** It manages your entire infrastructure by pulling inventory from public cloud providers such as Microsoft Azure, amazon web services, etc.

**8. Integrated Notification:** This notifies you when a job succeeds or fails across the entire organization at once, or customize on a pre-job basis.

**9. Schedule Ansible Jobs:** It schedule different kinds of jobs such as playbook runs, cloud inventory updates, and source control updates to run according to the need.

**10. REST API and Tower CLI Tool:** Every feature present in Ansible Tower is available through the Ansible Tower's REST API, which provides the ideal API for the systems management infrastructure. The Ansible Tower's CLI tool is available for launching jobs from CI systems such as Jenkins, or when you need to integrate with other command-line tools.





\
\
\
