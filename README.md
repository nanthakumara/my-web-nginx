# my-web-nginx
This example is to deploy a sample Nginx web server in Docker container using Github repo + Jenkins Pipeline
We have used AmazonLinux2 AMI for this demo

Pre-requisites:
1. Github account
2. Jenkins Server
3. An AWS account to launch EC2 Instance (Jenkins+Git)
4. Dockerhub account

Step 1: Github account
Login to you github account to create your own repository to have the required deployment files.
For this demo we are using Dockerfile + Index.html 

Step 2: EC2 Instance
1. Launch an EC2 Instance using any Linux based OS
2. Install Java
   #yum remove java*
   #yum install java
   #cd /opt/
   #wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/jdk/8u201-b09/42970487e3af4f5aa5bca3f542482c60/jdk-8u201-linux-x64.tar.gz"
    #tar xzf jdk-8u201-linux-x64.tar.gz
    #cd jdk1.8.0_201/
    #alternatives --install /usr/bin/java java /opt/jdk1.8.0_201/bin/java 2
    #alternatives --config java
    #alternatives --install /usr/bin/jar jar /opt/jdk1.8.0_201/bin/jar 2
    #alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_201/bin/javac 2
    #alternatives --set jar /opt/jdk1.8.0_201/bin/jar
    #alternatives --set javac /opt/jdk1.8.0_201/bin/javac
    #java -version
 3. Install Jenkins
     #wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins.io/redhat/jenkins.repo
     #rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
     #yum install jenkins -y
     #service jenkins start
     #cat /var/lib/jenkins/secrets/initialAdminPassword ("This is give you Jenkins Initial password")
 4. Install GIT
    #yum install git
 5. Install Docker
    #yum install docker 
    #service docker start ("To start docker")
    #docker info ("Will give you docker information")
    Kindly change the docker.sock permission "chmod 766 /var/run/docker.sock"
    
    
