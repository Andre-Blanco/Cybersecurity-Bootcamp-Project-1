## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Diagrams/Azure%20Cloud.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

 DVWA: https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/DVWA.yml
ELK stack config.yml: https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/ELK%20stack%20config.yml
Filebeat config.yml: https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/Filebeat%20config.yml
Filebeat playbook.yml: https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/Filebeatplaybook.yml
Metricbeat config.yml:https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/metricbeat%20config.yml
Metricbeat playbook.yml: https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/metricbeatplaybook.yml

- How to Use the Ansible Build
Download ansible.cfg configuration file from https://ansible.com/ and copy to /etc/ansible directory.
Assign username and SSH public key for Web1 and 2 and ELK virtual machine.


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting network traffic to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for? Log files and locations you specify, forwarding them to Elastisearch and Logstash for review
- What does Metricbeat record? Metrics and statistics, forwarding them to Elastisearch and Logstash for review

The configuration details of each machine may be found below.

| Name                | Function      | IP                        | Operating system |
|---------------------|---------------|---------------------------|------------------|
| JumpBox-Provisioner | Gateway       | 20.124.251.185 / 10.0.0.4 | Linux            |
| Web 1               | Web Server    | 10.0.0.7                  | Linux            |
| Web 2               | Web Server    | 10.0.0.6                  | Linux            |
| ELK                 | ELK Server    | 20.94.221.163 / 10.1.0.4  | Linux            |
| Load Balancer       | Load Balancer | Static External IP        | Linux            |
| Workstation         | Access        | External IP               | Windows          |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Workstation Public IP, port 5601

Machines within the network can only be accessed by JumpBox-Provisioner and Workstation.
-Workstation public IP through port 22
-JumoBox-Provisioner IP 10.0.0.4, SSH through port 22

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses                 |
|---------------|---------------------|--------------------------------------|
| JumpBox       | No                  | Workstation Public IP, SSH port 22   |
| Web1          | No                  | 10.0.0.4 though port 22              |
| Web2          | No                  | 10.0.0.4 through port 22             |
| ELK           | No                  | Workstation Public IP, TCP port 5601 |
| Load Balancer | No                  | Workstation Public IP, HTTP port 80  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Using ansible allows easily and repeatedly configure and deploy applications across multiple machines

The playbook implements the following tasks:
- Specify machines and remote users
- Increase system memory
- Install “docker.io”, “python3-pip”
-Launch and expose containers

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/Andre-Blanco/Cybersecurity-Bootcamp-Project-1/blob/main/Ansible/ELK%20docker.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web1: 10.0.0.7
- Web2: 10.0.0.6

We have installed the following Beats on these machines:
- ELK Server, Web1 and Web2
- FileBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
- FileBeat: Collects log events
-MetricBeat: Collects system and metric statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Config file to ansible VM.
- Update the Config file to include private IPs of Web 1 and 2 and ELK server
- Run the playbook, and navigate to (your ELK IP)/app/kibana#/home to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? Update the appropriate config file, adding the ELK server internal IP under “ELK server” and web servers under [webservers]
- _Which URL do you navigate to in order to check that the ELK server is running?
(Your ELK server IP)/app/kibana#/home

