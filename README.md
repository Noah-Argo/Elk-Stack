## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Diagram](/Diagram/Project_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the config file may be used to install only certain pieces of it, such as Filebeat.

  - [Filebeat](/Ansible/roles/filebeat-playbook.yml)
  - [Metricbeat](/Ansible/roles/metricbeat-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- They protect against DDOS attack. Enable the user access from a single secure node that can be monitored as well.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the application and system logs.
- Filebeat watches the log files or locations that are specified.
- Metricbeat helps monitor your servers by collecting metrics from systems and services running on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web-1    | VM/Docker | 10.0.0.7   | Linux            |
| Web-2    | VM/Docker | 10.0.0.6   | Linux            |
| Elk-VM   | VM        | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 98.194.104.91

Machines within the network can only be accessed by jump-box.
- Jump-box-provisioner. 10.0.0.9

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 98.194.104.91        |
| Web-1    | No                  | 10.0.0.9             |
| Web-2    | No                  | 10.0.0.9             |
| Elk-VM   | Yes (HTTP)          | 10.0.0.9             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Allow the automation of all tasks daily to make them more efficient and less time consuming.

The playbook implements the following tasks:
- Install docker.io.
- Install python3-pip.
- Install the Docker module.
- Increase the virtual memory and use more memory.
- Download and launch the docker elk container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Images](/Ansible/Images/Docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1, Web-2

We have installed the following Beats on these machines:
- Metricbeat, Filebeat

These Beats allow us to collect the following information from each machine:
- Metricbeat collects metric data from your system.
- Filebeat collects audit logs, deprecation logs, server logs. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to "/etc/ansible".
- Update the hosts file to include...
- Run the playbook, and navigate to the elk server VM to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- The playbook is install-elk.yml, the file is in the roles directory in the ansible directory.
- Update the hosts file to include webservers. Put the IPs for the webservers whihc are 10.0.0.6 and 10.0.0.7.
- http://20.64.152.6:5601/app/kibana#/home

Bonus: ansible-playbook file-beat.yml
![Images](/Ansible/Images/Filebeat.png)
