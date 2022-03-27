# Project-1_ELK_Stack
Project 1 ELK-Stack, Kibana, Azure

The files in this repository were used to construct the network below.

https://app.diagrams.net/#HBrandiCake%2FProject-1_ELK_Stack%2Fmain%2FPROJECT_1-ELS-STACK-DIAGRAM.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.
  
  /etc/ansible/install-elk-playbook.yml

This document contains the following details:
•	Description of the Topology
•	Access Policies
•	ELK Configuration
o	Beats in Use
o	Machines Being Monitored
•	How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
•	What aspect of security do load balancers protect?
o	Load balancers protects the system from DDoS attacks by shifting attack traffic.
o	Load Balancing contributes to the Availability aspect of security in regards to the CIA Triad.
•	What is the advantage of a jump box?
o	The advantage of a jump box is to give access to the user from a single node that can be secured and monitored.
o	The advantage of a JumpBox is the orgination point for launching Administrative Tasks. This ultimately sets the JumpBox as a SAW (Secure Admin Workstation). All Administrators when conducting any Administrative Task will be required to connect to the JumpBox (SAW) before perfoming any task/assignment.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the changes to the Logs and system traffic.
•	What does Filebeat watch for?
o	Filebeat watches for any information in the file system which has been changed and when it has.
o	Filebeat watches for log files/locations and collects log events
•	What does Metricbeat record?
o	Metricbeat takes the metrics and statistics that collects and ships them to the output you specify.

