## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the config file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: cd /etc/ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly avaliable, in addition to restricting certain attacks to the network such as a DDoS.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? They make sure that no server is overworked. Jump boxes are used to access the different boxes on network in a more safe manner.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the box and system logs.
- _TODO: What does Filebeat watch for? logging centralized data
- _TODO: What does Metricbeat record? the box's health

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function    | IP Address | Operating System |
|----------|----------   |------------|------------------|
| Jump Box | Gateway     | 10.0.0.1   | Linux            |
| ELK      | logging data| 10.0.0.10  | Linux            |
| DVWA-VM1 | box         | 10.0.0.9   | Linux            |
| DVWA-VM2 | box         | 10.0.0.12  | Linux                 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 75.60.1.237

Machines within the network can only be accessed by ansible.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? The ansible box called upbeat_meninsky, and the IP is 172.17.0.3

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes/No                  | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? It can be pushed out to multiple machines rather than just one

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- create elk box with ssh key
  create playbook in ansible(include docker, python, increase virtual memory, and launch docker elk container
  run it
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring: 10.0.0.9 10.0.0.12

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed: filebeats, metricbelts

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Metricbeat collects data about the CPU usage and things similar to that
filebeat is creating logs

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to ansible folder.
- Update the host file to include the ip of the box that the playbook is going to
- Run the playbook, and navigate to the box created to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
	The one telling the box's what to install. Copy it into the ansible folder
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
hosts, write in [elkserver] instead of putting everything under webservers
- _Which URL do you navigate to in order to check that the ELK server is running? my elk ip at the port 5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._