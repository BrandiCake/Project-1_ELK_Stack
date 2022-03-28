Automated ELK Stack Deployment


The files in this repository were used to configure the network depicted below.


https://app.diagrams.net/#HBrandiCake%2FProject-1_ELK_Stack%2Fmain%2FPROJECT_1-ELK-STACK-DIAGRAM.drawio.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 
Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.


    The following ansible-playbooks are needed to create and install DVWA and the ELK-server:

    
    my-playbook-pentest.yml - used to install DVWA servers
    
    install-elk.yml - used to install ELK Server
    
    filebeat-playbook.yml - Used to install and configure Filebeat on Elk Server and DVWA servers
    
    metricbeat-playbook.yml - Used to install and configure Metricbeat on Elk Server and DVWA servers


This document contains the following details:

    - Description of the Topology
    
    - Access Policies
    
    - ELK Configuration
    
        - Beats in Us
        - Machines Being Monitored

    - How to Use the Ansible Build


Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting access to the network.

    What aspect of security do load balancers protect? 
    
    Load balancing ensures that the application will be highly available, in addition to restricting inbound access to the network. Load Balancers ensures availability to the webservers which is the Availability aspect of security in regards to the CIA Triad. Load Balancers also protect the system from DDoS attacks by shifting traffic
    
    What is the advantage of a jump box?
    
    The main advantage of using a JumpBox is having one origination point for administrative tasks. In order to conduct administrative tasks administrators are required to access the JumpBox before accessing the other servers. The load balancer also is responsible for distributing web traffic across multiple servers. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the LOGS and system TRAFFIC.

    -What does Filebeat watch for?

     Filebeat watches for log files/locations and collect log events. Filebeat watches for any information in the file system which has been changed and when it has changed.


    -What does Metricbeat record?
    
    Metricbeat records metric and statistical data from the operating system and from services running on the server. 

The configuration details of each machine may be found below.


        Name	      Function	              IP Address	       Operating System

        JumpBox	     Gateway	              10.0.0.4	         Linux(ubtntu 18.04)

        Web-1	       Server(Docker/DVWA)	  10.0.0.5	         Linux(ubtntu 18.04)

        Web-2	       Server(Docker/DVWA)	  10.0.0.6        	 Linux(ubtntu 18.04)

        Web-3.     	 Server(Docker/DVWA)	  10.0.0.8	         Linux(ubtntu 18.04)

        Elk-VM1	     Elk Stack	            10.1.0.4	         Linux(ubtntu 18.04)



Access Policies

The machines on the internal network are not exposed to the public Internet.

    Only the JumpBox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

       -76.29.75.133
    
    Machines within the network can only be accessed by SSH.

    
    Which machine did you allow to access your ELK VM? What was its IP address?
    
       -The ELK Stack is only acesible by SSH from the JumpBox from my home IP address: 76.29.75.133



A summary of the access policies in place can be found in the table below.


      Name	      Publicly Accessible	        Allowed IP Addresses

     Jump Box	         NO	                       10.0.0.4
     
     Web-1	           NO(Thru Load Balancer)	   10.0.0.5

     Web-2	           NO(Thru Load Balancer)	   10.0.0.6

     Web-3	           NO(Thru Load Balancer)	   10.0.0.8      

     Elk-VM1	         NO	                       10.1.0.




Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...


    What is the main advantage of automating configuration with Ansible?

      - This allows you to deploy to multiple servers using a single playbook
      
      - Free: Ansible is an open-source tool.
 
      - Very simple to set up and use: 

      - No special coding skills are necessary to use Ansible’s playbooks (more on playbooks later).


    The playbook implements the following tasks:

      - Install docker.io

      - Install Python-pip

      - Install docker container

      - Download and Configure ELK docker container
      
      - Sets Published Ports



The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

     !!!(I PROVIDED A FILE IN THE REPOSITORY WILL ALL SCREENSHOT)!!!



Target Machines & Beats


    This ELK server is configured to monitor the following machines:"

   
      - Web-1	      	   10.0.0.5

      - Web-2	           10.0.0.6

      - Web-3	           10.0.0.8 


    We have installed the following Beats on these machines:

      - Filebeat
      
      - Metricbeat


    These Beats allow us to collect the following information from each machine:
    
      - Filebeat watches for log files and/or locations and collect log events.
      
      - Metricbeat records metrics and statistical data from the operating system and from services running on the server. 


Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

    SSH into the control node and follow the steps below:

      Copy the filebeat-config.yml and metricbeat-config.yml file to /etc/ansible/files
      
      Update the configuration files to include private IP of Elk-Server to the ElasticSearch and Kibana sections of the config files.
      
      Run the playbook, and navigate to the ELK-Server-public-IP:5601/app/kibana to check that the installation worked as expected.


    Which file is the playbook? Where do you copy it?

      elk-playbook.yml - used to install ELK Server
      
        - filebeat-playbook.yml - Used to install and configure Filebeat on Elk Server and DVWA servers

        - metricbeat-playbook.yml - Used to install and configure Metricbeat on Elk Server and DVWA servers


     Where do you copy it?
     
        - /etc/ansible/

    Which file do you update to make Ansible run the playbook on a specific machine? 
    
        - /etc/ansible/hosts.cfg
    
    
    How do I specify which machine to install the ELK server on versus which to install Filebeat on?

        - In the /etc/ansible/hosts file you can modify to tell it where you want each to be installed ElkServers or FileBeat



    Which URL do you navigate to in order to check that the ELK server is running?
    
        - http://publicip(elkserver):5601

