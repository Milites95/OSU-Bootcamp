## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

[Project Diagram](https://github.com/Milites95/OSU-Bootcamp/blob/6e714b0a91eafacdfbabb2bdaeaf6983192d9304/Project%201/Diagram/Project_Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - [ELK Server Install]  https://github.com/Milites95/OSU-Bootcamp/blob/6e714b0a91eafacdfbabb2bdaeaf6983192d9304/Project%201/Ansible/install_elk.yml


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting traffic to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Jump Box and system network.
- What does Filebeat watch for? Changes to file changes on the machine? (check this one)
- What does Metricbeat record? Collectt metrics from the operating system and from services running on the server. 

The configuration details of each machine may be found below.

| Name       | Function   | IP Address | Operating System |
|------------|------------|------------|------------------|
| Jump Box   | Gateway    | 10.0.0.4   | Linux/Unbuntu    |
| Web5       | Web access | 10.0.0.6   | Linux/Unbuntu    |
| Web6       | Web access | 10.0.0.7   | Linux/Unbuntu    |
| ELK Server | Log        | 10.1.0.5   | Linux/Unbuntu    |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: (Workstation Public IP Address)

Machines within the network can only be accessed by Jump Box: 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | Yes                 | Personal IP          |
| ELK Server    | Yes                 | Any                  |
| Load Balancer | Yes                 | Any                  |
| Web5          | No                  | 10.0.0.4 & 10.1.0.5  |
| Web6          | No                  | 10.0.0.4 & 10.1.0.5  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-Free: Ansible is an open-source tool.
-Very simple to set up and use: No special coding skills are necessary to use Ansible’s playbooks (more on    
 playbooks later).
-Powerful: Ansible lets you model even highly complex IT workflows.
-Flexible: You can orchestrate the entire application environment no matter where it’s deployed. You can also -customize it based on your needs.
-Agentless: You don’t need to install any other software or firewall ports on the client systems you want to  
 automate. You also don’t have to set up a separate management structure.
-Efficient: Because you don’t need to install any extra software, there’s more room for application resources  
 on your server.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-Install docker.io
-Install pip3
-Install Docker python module
-Increase virtual memory
-Download and launch a docker
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![ELK Docker ps](https://github.com/Milites95/OSU-Bootcamp/blob/4d005067c2b09557f9b03626781da1aa277be31c/Project%201/Images/ELK_Docker_ps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web5: 10.0.0.6
- Web6: 10.0.0.7

We have installed the following Beats on these machines:
- Microbeats 

These Beats allow us to collect the following information from each machine:
- Filebeats- Collects data about the file system. 
- Metricbeats- Collects machine metrics, such as uptime. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Node.
- Update the hosts file to include webservers and elk. 
- Run the playbook, and navigate to Kibana (http://[Host IP]/app/kibana#/home) to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? install_elk.yml It is copied onto the Web5, Web6 and the ELK server. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Update the hosts file with the ip of the specified machines. 
- _Which URL do you navigate to in order to check that the ELK server is running? Verify that you can access your server by navigating to http://[your.ELK-VM.External.IP]:5601/app/kibana. Use the public IP address of your new VM.

