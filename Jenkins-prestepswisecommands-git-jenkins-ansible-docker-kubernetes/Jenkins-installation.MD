#Installation of Jenkins of EC2 Linux Server#

## Getting Started with Jenkins

To begin using Jenkins:

1. Download : Choose the appropriate package for your operating system from the [official Jenkins download page](https://jenkins.io/download/).
2. Installation: Follow the installation instructions tailored to your OS for a smooth setup experience.
3. Configuration: Customize Jenkins using its intuitive web interface and configure your projects for automated building and testing.

For detailed installation guides and usage instructions, please refer to the `docs` directory within this repository.


***After Jenkins Installation Finishes:***

Check with the below command to ensure its properly working or not using

#Start Jenkins Service#

service jenkisn start

*** Accessing Jenkins***

By default it runs on port 8080: http:<EC2 IP ADDRESS>:8080.

*** Configuration of Jenkins once installation completion ***

The default Username is admin

Grab the default password from the server which will resides in the secrets using the "cat" command.
    
Command: cat /var/lib/jenkins/secrets/initialAdminPassword
   

*** To make sure Jenkins Jobs are running***

***Sample Use case: ****

Create “new item”
Enter an item name – xyz-project
Chose Freestyle project
Under the Build section Execute shell: echo "Welcome to Jenkins Demo"
Save job
Build job
Check "console output"




