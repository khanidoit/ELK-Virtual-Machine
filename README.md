# ELK-Virtual-Machine
This repository contains information and setup guide for setting up an ELK environment in Azure, leveraging docker and ansible.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!(Images/ELK Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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
- 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file and system logs.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function                         | IP Address |   |   |
|----------------------|----------------------------------|------------|---|---|
| Jump-Box-Provisioner | Gateway (Ansible and Docker Host | 10.0.0.5   |   |   |
| ELK-VM               | Kibana                           | 10.1.0.4   |   |   |
| Web-3                | DVWA Container                   | 10.0.0.9   |   |   |
| Web-2                | DVWA Container                   | 10.0.0.7   |   |   |
| Web-1                | DVWA Container                   | 10.0.0.6   |   |   |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible              | Allowed IP Addresses                    | Public IP Address |
|----------------------|----------------------------------|-----------------------------------------|-------------------|
| Jump-Box-Provisioner | Gateway (Ansible and Docker Host | 64.137.157.38, 10.0.0.0/24. 10.1.0.0/24 | 64.137.157.38     |
| ELK-VM               | Kibana                           | 10.0.0.0/24, 10.1.0.0/24                | 13.64.233.115     |
| Web-3                | DVWA Container                   | 10.0.0.0/24, 10.1.0.0/24                | 52.188.127.138    |
| Web-2                | DVWA Container                   | 10.0.0.0/24, 10.1.0.0/24                | 52.188.127.138    |
| Web-1                | DVWA Container                   | 10.0.0.0/24, 10.1.0.0/24                | 52.188.127.138    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- Install Docker
- Install Python
- Increase virtual memory utilization to 262144
- Download and launch ELK docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  | Function       | IP Address |   |   |
|-------|----------------|------------|---|---|
| Web-1 | DVWA Container | 10.0.0.6   |   |   |
| Web-2 | DVWA Container | 10.0.0.7   |   |   |
| Web-3 | DVWA Container | 10.0.0.9   |   |   |

We have installed the following Beats on these machines:
- Filebeat (refer to filebeat.yml file)
- Metricbeat (refer to metricbeat.yml file)

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to capture system log changes at the base VM level.
Metricbeat allows us to capture base VM performance indicators such as CPU, memory etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to your ansible playbook locations (i.e /etc/ansible/playbooks)
- Update the install-elk file to include the host group you would like to install ELK on. This should be configured in the Ansible hosts file.
- Run the playbook, and navigate to http://[your.ELK-VM.External.IP]:5601/app/kibana to check that the installation worked as expected.
