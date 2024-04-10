#Configuring Git With Jenkins#

Git is one of the most popular tools for version control system. Easy to pull code from git repositories using jenkins if you use github plugin.
Prerequisites

**** Jenkins server - Where Jenkins Installation is mandatory ***

Install Git on Jenkins server
Install git packages on jenkins server

Command: yum install git -y

***Setup Git on jenkins console***

Step-1: Install git plugin without restart

Manage Jenkins >> Jenkins Plugins >> Available >> github

Step-2: Configure git path

Manage Jenkins > Global Tool Configuration > git
