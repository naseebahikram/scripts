### Automated ELK Stack Deployment

---
The files in this repository were used to configure the network depicted below.

- [Azure Network Diagram](https://github.com/naseebahikram/scripts/blob/main/Diagrams/Elk-Diagram.jpeg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 

---
The files in this repository were used to configure the network depicted below.

- [Azure Network Diagram](https://github.com/naseebahikram/scripts/blob/main/Diagrams/Elk-Diagram.jpeg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 

  - [Docker](https://github.com/naseebahikram/scripts/tree/main/Ansible/Docker)
  - [Filebeat](https://github.com/naseebahikram/scripts/tree/main/Ansible/Filebeat)
  - [Elk](https://github.com/naseebahikram/scripts/tree/main/Ansible/Elk)
  - [Metricbeat](https://github.com/naseebahikram/scripts/tree/main/Ansible/Metricbeat)
  - [Host and Config File](https://github.com/naseebahikram/scripts/tree/main/Ansible/General)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

---
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting access to the network.

**What aspect of security do load balancers protect?**

  - Load balancers protect against DDoS attacks. The way they do it is by shifting the attack traffic and dispersing it elsewhere. 

**What is the advantage of a jump box?**

  - The advantage of a jump box is that you're able to access and manage devices in separate security zones. Also any tools that are used within that box are maintained in that system. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

**What does Filebeat watch for?**

  - Filebeat monitors and collects log files. It also forwards data to be indexed. 

**What does Metricbeat record?**

  - Metricbeat records metrics and statistics from the system and running services. 

The configuration details of each machine may be found below.

|  Name     |  Function  | IP Address               | Operating System |
| ----------| ---------- |------------              |------------------|
| Jump Box  | Gateway    | 10.0.0.4/20.213.124.173  | Linux            |
| Web 1     | Webserver  | 10.0.0.5/20.211.0.225    | Linux            |
| Web 2     | Webserver  | 10.0.0.6/20.211.0.225    | Linux            |
| Elk       | Elk Server | 10.1.0.5/20.89.43.217    | Linux            |


---
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

  -  $HOST_IP

Machines within the network can only be accessed by Docker.

  - We went to our Jumpbox and started a Docker container. Through that, we would SSH into the Elk-VM.The IP is 10.1.0.5.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses          |
|----------|---------------------|----------------------         |
| Jump Box | No                  |  10.0.0.4, 10.0.0.5, 10.1.0.5 |

---
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

  - When using ansible playbooks, it allows each download and configuration to run through each step. If there is a problem at any of the steps, it shows you. Ansible also allows us to also rerun through specific installations without multiple programs being downloaded.
 
The playbook implements the following tasks:

- Specify group of machines
- Install Docker.io
- Install Python-pip
- Increate Virtual Memory
- Download and Launch Elk Docker
- Publish ports 5044, 5601, 9200

- [ELK.yml](https://github.com/naseebahikram/scripts/blob/main/Ansible/Elk/elk.yml)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

- [Launching and Exposing the Container](https://github.com/naseebahikram/scripts/blob/main/Diagrams/Launching%20and%20Exposing%20the%20Container.png)

---
### Target Machines & Beats
This ELK server is configured to monitor the following machines:

  - Web-1: 10.0.0.5
  - Web-2: 10.0.0.6
  - Elk-VM: 10.1.0.5

We have installed the following Beats on these machines:

  - [Filebeat Installation](https://github.com/naseebahikram/scripts/blob/main/Diagrams/Verify%20Installation%20and%20Playbook%20Filebeat.png)
  - [Metricbeat Installation](https://github.com/naseebahikram/scripts/blob/main/Diagrams/Verify%20Installation%20and%20Playbook%20Metricbeat.png)

These Beats allow us to collect the following information from each machine:

  - Filebeat allows us to collect log files from specific files and web servers. Metricbeat monitors virtual machines statistics. 

---
### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to ansible folder.
- Update the hosts and configuration file to include the remote users and ports 
- Run the playbook, and navigate to [PUBLICIP of Elk-VM]:5601/app/kibana to check that the installation worked as expected.
---
