#Integration of Ansible with Jenkins#

Step-1: Install "publish Over SSH"

Manage Jenkins >> Manage Plugins >> Available >> Publish over SSH.

Step-2: Enable connection between Ansible and Jenkins

 Manage Jenkins > Configure System > Publish Over SSH > SSH Servers
 
 SSH Servers:
 
 Hostname < EC2 IP Address>
 
 username: ansadmin
 
 password: ansadmin

#Test the connection "Test Connection"#
