# Deploying Using Ansible Playbooks on Docker Containers#

Pre Configurations:

1. Jenkins Server
2. Docker-host server with Docker installed on it
3. Ansible server with Ansible installed on it
4. Create a dockerfile under the directory "/opt/docker" on Ansible server or host or node

Sample Commands for Docker file to build and create images under the Ansible server inside the Ansible playbooks:

Default location for ansible playbooks: vi /etc/ansible/

*** Docker file: ***

docker build -t demo-image .

docker run -d --name demo-container -p 8081:8080 demo-image.


*** Integration between Ansible-Controller and Jenkins ***

Step-1: Install "publish Over SSH"

        Manage Jenkins > Manage Plugins > Available > Publish over SSH

Step-2: Enable connection between Ansible-control-node and Jenkins

        Manage Jenkins > Configure System > Publish Over SSH > SSH Servers

        SSH Servers: - Name: ansible-server

        Hostname:<ServerIP>

        username: ansadmin

        Advanced >> chose Use password authentication

        password: ansadmin


# Steps to create "Deploy_on_Container_using_ansible" Jenkin job #

From Jenkins home page select "New Item"

Enter an item name: Deploy_on_Container_using_ansible

Copy from: Deploy_on_Container

Source Code Management:

Repository: https://github.com/yankils/hello-world.git

Branches to build : */master

Poll SCM : - * * * *

Build:

Root POM:pom.xml

Goals and options: clean install package

Post-build Actions:

Send build artifacts over SSH:

SSH Publishers

SSH Server Name: ansible-server

Transfers > Transfer set

Source files: webapp/target/*.war
            
Remove prefix: webapp/target
            
Remote directory: //opt//docker
            
Exec command:

ansible-playbook -i /opt/docker/hosts /opt/docker/create-docker-image.yml;

Save and run the job now.
