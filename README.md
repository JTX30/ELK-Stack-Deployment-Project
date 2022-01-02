# ELK-Stack-Deployment-Project
The files in this repository were used to configure the network depicted below.
![Network Diagram](https://user-images.githubusercontent.com/89861177/147864434-dd9253d5-2056-4818-b3d9-3e64db6ba165.JPG)
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

/etc/ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network.
Load balancers help against Ddos attacks and the jumpbox provisioner adds a bit of extra security seeing as all admins must log in to perform any administrative tasks on the jumpbox provisioner. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems of the VM’s on the network and system metrics.
Filebeat monitors log files while metricbeat records metrics and statistics.


The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.9   | Linux |
| DVWA1 |  10.0.0.10   | Web Server  |   Linux |
| DVWA2  |  10.0.0.11  |  Web Server  |  Linux |
| ELK  |  10.1.0.4  |  Monitor |  Linux  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 
Whitelisted IP which changes each time the VM is started: 
52.186.152.164

Machines within the network can only be accessed by each other.
The JumpBox Provisioner can access the ELK Server. The JumpBox’s IP is: 10.0.0.9

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|ELK   |             No        | 10.1.0.4    |
| Jump Box |     No        | 10.0.0.9    |
|  Web1      |      No        | 10.0.0.10  |
|    Web2     |     No        |10.0.0.11   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
This allows you to deploy multiple servers with just a single playbook.

The playbook implements the following tasks:
- install docker.io
- install Pyhton-pip
- install docker container
- launch docker container: ELK

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.10 and Web-2 10.0.0.11

We have installed the following Beats on these machines:
Filebeat & Metricbeat have both been installed. 

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat collects metrics from the operating system and from services running on the server.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the plsbook file to etc/Ansible.
- Update the config file to include web servers/elk server private IP address’ 
- Run the playbook, and navigate to the ELK-Server to check that the installation worked as expected.

: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? /etc/ansible/file/filebeat-configuration.yml

- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Edit the /etc/ansible/hosts file to add webserver/elkserver ip addresses

- Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana

