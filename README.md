# ELK-Stack
UT ELK Stack Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting the access to the network.

_What aspect of security do load balancers protect? What is the advantage of a jump box?_
Load balancers distribute network traffic evenly across numerous servers to protect from a DDoS attack. The jumpbox minimizes hostile access by requiring ssh and keys that only the administrator should know. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
Filebeat collects any changes to log files (log events) and sends them to ELK for indexing.
Metricbeat colllects statistics and metrics from any predetermined output and sends them to ELK for indexing.

**The configuration details of each machine may be found below.**

| Name                 | Function | IP Address | Operating System |
|----------------------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 10.0.0.4   | Linux            |
| ELK-Server           | Stack    | 10.1.0.4   | Linux            |
| Web-1                | Server   | 10.0.0.5   | Linux            |
| Web-2                | Server   | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
104.57.185.33

Machines within the network can only be accessed by the jumpbox admin.
The ELK VM is accessible through
Public IP: 104.57.185.33

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses     |
|----------------------|---------------------|--------------------------|
| Jump-Box-Provisioner | No                  | 10.0.0.4                 |
| ELK-Server           | Yes                 | Any                      |
| Web-1                | Yes                 | 104.57.185.33 / 10.0.0.4 |
| Web-2                | Yes                 | 104.57.185.33 / 10.0.0.4 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because there will be little to no configuration errors across multiple servers utilizing the playbook.

The playbook implements the following tasks:
- Update/ download docker.io to the machine
- install Python 3
- Install Python Docker Module
- Download and launch a docker web container (DVWA)
- Enable Docker Service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://user-images.githubusercontent.com/86381270/147844192-b45708dc-5085-48e0-af8e-f7f51a369a2f.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log events. Will show, for example, successful/ unsuccessful login attempts
- Metricbeat collects system statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk-Ansible.yml file to /etc/ansible/roles/Elk-Ansible.yml.
- Update the host file in /etc/ansible so the program will be ready to run
- Run the playbook, and navigate to http://[insert_your_IP]:5601/app/kibana to check that the installation worked as expected.
