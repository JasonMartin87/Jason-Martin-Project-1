## Scripts

Linux & Ansible Scripts GW Cyber Security

## Cloud Network

This is a collection of Linux Scripts and Ansible Scripts from my CyberClass.

Most of the scripts are used to configure cloud servers with differnt docker containers.

The final setup was 4 servers running vulnerable DVWA containers along with a jump box and a server running an ELK stack container.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://i.imgur.com/651R3zQ.png/to/img.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of each yaml may be used to install only certain pieces of it, such as Filebeat.

  - Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancers protects the system from DDoS attacks by shifting attack traffic. The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the filesystem and system performance.
- What does Filebeat watch for?
Filebeat monitors the log files or locations that you specify, retrieves log events, and forwards them either to Elasticsearch or Logstash for indexing.

- What does Metricbeat record?
Metricbeat takes the statistics that it collects and sends them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
|  Web01   |  Server  | 10.1.0.7   | Linux            |
|  Web02   |  Server  | 10.1.0.9   | Linux            |
|  Web03   |  Server  | 10.1.0.10  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses
Home Public IP Address 72.196.202.189     

Machines within the network can only be accessed by Jump Box VM.
- Which machine did you allow to access your ELK VM? What was its IP address?
Jump Box VM: VNET IP 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.196.202.189       |
|  Web01   | No                  |    Local Vnet        |
|  Web02   | No                  |    Local Vnet        |
|  Web03   | No                  |    Local Vnet        |
|  Elk     | Yes                 | 72.196.202.189       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
Advantage is that you can put commands into multiple servers from a single playbook.

The playbook implements the following tasks:
1. The playbook was configured to install the docker.io and python 3.
2. To sucessfully ensure that the docker was running, you would run [sudo systemctl status docker].
3. Lastly, you would run the Elk container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://i.imgur.com/y30iGMb.png/to/img.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1: 10.1.0.7
- Web 2: 10.1.0.9
- Web 3: 10.1.0.10

We have installed the following Beats on these machines:
- Metricbeat
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat is used to send system logs information from the Web servers into a readable format.
- Metricbeat would then report the system's metrics of how much resources the machines are using. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- *Copy the elk-stack-playbook.yml file to /etc/ansible.*
- *Update the host file to include the Elk's virtual machine's IP address.*
- *Run the playbook, and navigate to http://[Elk_VM_Public_IP]:5601/app/kibana to check that the installation worked as expected.*

_TODO: Answer the following questions to fill in the blanks:
1. Which file is the playbook? Where do you copy it?
- filebeat-playbook.yml and then copied to /etc/ansible/roles directory
2. Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- You woudl have to update filebeat-config.yml. You can specify which machine to install by updating the host files with the ip addresses of web servers and elk server and selecting which group to run on in th ansible.
4. Which URL do you navigate to in order to check that the ELK server is running?
- http://[your.ELK-VM.External.IP]:5601/app/kibana

