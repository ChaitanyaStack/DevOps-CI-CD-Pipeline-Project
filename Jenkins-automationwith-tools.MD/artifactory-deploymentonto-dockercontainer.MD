# Deploy Executable Artifacts on Docker Container #

Pre configurations:

1. Proper Jenkins Server- with Jenkins Installed on it.
  
2. Docker Server - with Docker installed on it.
   
3. Docker file should be saved under the directory or path "/home/dockeruser/" in user home directory and set necessary permissions to the directory and to the docker file to have an access by the Jenkins User.
   
5. Copy the file to the ./webapps.war (where the primary location for the build artifacts)

# Sample Integration streps to configure the Jenkins and Docker to have proper sequence of deployment of artifacts #

Step-1: Install "publish Over SSH"

Manage Jenkins >> Manage Plugins >> Available >> Publish over SSH

Step-2:  Enable connection between Docker-host and Jenkins

Manage Jenkins >> Configure System >> Publish Over SSH >> SSH Servers
        
SSH Servers: - Name: docker-host

Hostname:< EC2 ServerIP Address>

username: dockeradmin

Advanced >> chose Use password authentication.

password: dockeradmin

#Steps to create "Deploy_on_Container" Jenkin job#

From Jenkins home page select "New Item"

Enter an item name: Deploy_on_Container

Copy from: Deploy_on_Docker_Host

Github Repo:

Poll SCM : * * * * *   # Trigger the pipelines for every single commits #

Build:

Root POM:pom.xml
Goals and options: clean install package

Post-build Actions

Send build artifacts over SSH

SSH Publishers

  SSH Server Name: docker-host
  
  Transfers > Transfer set
  
  Source files: webapp/target/*.war
  Remove prefix: webapp/target
  Remote directory: //home//ansadmin or .
  Exec command:
  # Sample Docker File in Building Images and Generating Container out of Images #
  cd /home/dockeradmin;
  docker build -t simple-devops-image .; #Build Image#
  docker run -d --name simple-devops-container -p 8080:8080 simple-devops-image; # Creates Container out of it#

Save and run.
