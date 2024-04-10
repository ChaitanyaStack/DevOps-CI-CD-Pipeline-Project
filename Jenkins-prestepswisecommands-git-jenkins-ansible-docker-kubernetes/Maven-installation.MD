#Installation and Configuration of Maven (build tool) on Jenkins server#

# Integrating Maven with Jenkins

## Prerequisites

A running instance of Jenkins

## Installation of Maven on Jenkins Server

To incorporate Maven into your Jenkins setup, begin by installing the Maven package on your Jenkins server:

1. **Download Maven**: Obtain the Maven binaries from the [official Maven download page](https://maven.apache.org/download.cgi). Choose the appropriate version for your needs.

2. **Installation Steps**:

   Create a directory for Maven:
   Commands:
   
   mkdir /opt/maven
   cd /opt/maven
    
   Download and extract latest version of Maven version from official website and extract it
      
   
    
3. **Configure Environment Variables**:
   
   Edit `~/.bash_profile` to include `M2_HOME` and `M2` variables and append them to the `PATH`:
   vi ~/.bash_profile
   # Add the following lines
   export M2_HOME=/opt/maven/apache latest version
   export M2=$M2_HOME/bin
   export PATH=$PATH:$M2_HOME:$M2
      
4. **Verify Installation**:

To ensure Maven is properly installed, log off and log back in, then execute:
Command: mvn --version
      

At this point, Maven is installed on the Jenkins server and ready for use.

## Configuring Maven in Jenkins

Next, let's configure Jenkins to use Maven:

1. **Install Maven Plugins**:

Navigate to **Manage Jenkins > Manage Plugins**.


2. **Set Up Maven in Global Tool Configuration**:

Go to **Manage Jenkins > Global Tool Configuration**.

Add a Maven installation and specify the path to the Maven you've installed.

By following these guidelines, Maven is integrated into Jenkins environment, enhancing your CI/CD pipeline with Maven's build capabilities.

