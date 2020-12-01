Automated ELK Stack Deployment



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.




![Project Elk ss](https://user-images.githubusercontent.com/67016167/100650738-601eef00-3312-11eb-9955-91ae935dffe2.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.


![filebeat ss](https://user-images.githubusercontent.com/67016167/100651184-1551a700-3313-11eb-93de-fb05593c4539.png)

This document contains the following details:

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build


Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting Traffic to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box?
Load Balancing is an important security role as computing moves more to the cloud. The off-loading function of a load balancer defends an organization against distributed denial-of-service (DDoS) attacks.

A Jump Box is used to control the access to other machines connected to it by allowing specific IP addresses to connect. Furthermore, it forwards those connections to their selected machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Logs and system Traffic.

What does Filebeat watch for? Filebeat monitors the log files or locations that are specified, collects log events, and forwards them. 

What does Metricbeat record? Metricbeat records and collects operating machine metrics.

The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

![Project Table ss](https://user-images.githubusercontent.com/67016167/100661127-fe19b600-3320-11eb-8276-1dc1a07ca425.png)

(CORRECTION for ElkDocker IP: 10.0.0.5)

The machines on the internal network are not exposed to the public internet. Only the Jump-Box machine can accept connections from the internet.

Access to this machine is only allowed from the following IP addresses: 166.7.XXX.XX/32

Machines within the network can only be accessed by SSH.

Which machine did you allow to access your ELK VM? Jump-Box-Provisioner.
What was its IP address? 52.170.46.43

A summary of the access policies in place can be found in the table below.

![Project Elk ss 3](https://user-images.githubusercontent.com/67016167/100756923-bf850980-33bb-11eb-90cc-36a6f4bf1875.png)

Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

TODO: What is the main advantage of automating configuration with Ansible? Automating with Ansible permits the creation of consistent, reproducable results throughout multiple machine configurations.

The playbook implements the following tasks:

TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
Install docker.io
Install python3.pip
Install docker module
Increase virtual memory
Use more memory

![Container ID ss ](https://user-images.githubusercontent.com/67016167/100763200-daa74780-33c2-11eb-8afa-14c1b2e9f208.png)
![Container ID ss](https://user-images.githubusercontent.com/67016167/100763037-ac296c80-33c2-11eb-98de-67432f7399c6.png)

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.

Target Machines & Beats

This ELK server is configured to monitor the following machines:

List the IP addresses of the machines you are monitoring

Web-1: 10.0.0.9

Web-2: 10.0.0.10

Web-3: 10.0.0.7

ElkDocker: 10.0.0.5


We have installed the following Beats on these machines:

Filebeat

Metricbeat



Specify which Beats you successfully installed 
These Beats allow us to collect the following information from each machine:

In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.

Filebeat monitors the log files or locations that you specify, such as Syslogs, displayed by Kibana here:

![image](https://user-images.githubusercontent.com/67016167/100766756-02001380-33c7-11eb-8212-ef3cb5461b6f.png)

Metricbeat monitors the metrics and statistics of the operating system, such as CPU usage, displayed by Kibana here:

![Screenshot 2020-12-01 112114](https://user-images.githubusercontent.com/67016167/100767181-76d34d80-33c7-11eb-80fc-4d2fdbd10eda.png)


Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the yml file to the ansible directory.
Update the cfg file to include remote users. 
Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it? yml file. You copy it to the /etc/ansible, /etc/ansible/files, and /etc/ansible/roles depending on the yml file.

Which file do you update to make Ansible run the playbook on a specific machine? You update /etc/ansible/hosts and /etc/ansible/ansible.cfg.

How do I specify which machine to install the ELK server on versus which to install Filebeat on? Specify the machine by editing the /etc/ansible/hosts file with the appropriate IP addresses.

_Which URL do you navigate to in order to check that the ELK server is running? http://<local.host>/app/kibana#/home.


As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.

nano /etc/ansible/ansible.cfg

nano /etc/ansible/hosts

ansible all -m ping

nano <your-playbook.yml>

ansible-playbook <your-playbook.yml>

ssh ansible@<XX.X.X.X>

curl <local.host>/setup.php


