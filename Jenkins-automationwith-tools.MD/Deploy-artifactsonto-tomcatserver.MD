#Pre-requisites#

1. Jenkins server
2. Tomcat Server

#Adding Deployment steps#

Install 'deploy to container' plugin. This plugin needs to deploy on tomcat server.

Install 'deploy to container' plugin without restart
        
  Manage Jenkins >> Jenkins Plugins >> available >> deploy to container

    
Jenkins should need access to the tomcat server to deploy build artifacts. setup credentials to enable this process. use credentials option on Jenkins home page.

Setup credentials
        
Credentials >> Jenkins >> Global credentials >> Add Credentials
            
Username : deploy

Password : deploy

id : deployer

Description: user to deploy on tomcat vm

*** Steps to create "Deploy_on_Tomcat_Server" Jenkin job ***

From Jenkins home page select "New Item"

Enter an item name: Deploy_on_Tomcat_Server

Copy from: My_First_Maven_Build

Source Code Management:

Repository: URL
  

Poll SCM : * * * * *

Build:
        
Root POM:pom.xml

Goals and options: clean install package

Post-build Actions
        
Deploy war/ear to container

WAR/EAR files : **/*.war
            
Containers : 
                
Credentials: deployer (user created on above)
                
Tomcat URL : http://<PUBLIC_IP>:8080

Save and run the job now.
