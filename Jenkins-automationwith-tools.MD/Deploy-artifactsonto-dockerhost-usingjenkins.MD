

#Pre-requisites#

1. Jenkins server
2. Docker-host Server

*** Integration between Docker-host and Jenkins ***

Step-1: Install "publish Over SSH"

        Manage Jenkins > Manage Plugins > Available > Publish over SSH

Step-2: Enable connection between Docker-host and Jenkins

    Manage Jenkins > Configure System > Publish Over SSH > SSH Servers

    SSH Servers: - Name: docker-host

    Hostname:<ServerIP>

    username: dockeradmin

    Advanced > chose Use password authentication.

    password: dockeradmin

*** Steps to create "Deploy_on_Docker_Host" Jenkin job ***

From Jenkins home page select "New Item"

Enter an item name: Deploy_on_Docker_Host

Copy from: Deploy_on_Tomcat_Server

    Source Code Management:
    
    Repository: Git hub link
        
    Poll SCM : * * * * *

    Build:

    Root POM:pom.xml

    Goals and options: clean install package

    Post-build Actions
        
    Send build artifacts over SSH
            
    SSH Publishers
            
    SSH Server Name: docker-host
        
    Source files: webapp/target/*.war
    
    Remove prefix: webapp/target
                
    Remote directory: //home//ansadmin or .

Save and run the job now.
