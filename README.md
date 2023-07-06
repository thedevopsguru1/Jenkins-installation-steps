# Jenkins-installation-steps
## Installing Dependencies:
## JAVA JDK & JRE
```
sudo yum install java-11-openjdk –y
```
### On amazon linux
```
sudo amazon-linux-extras enable corretto8
```
```
sudo yum install java-1.8.0-amazon-corretto-devel -y
```
```
sudo yum install java-1.8.0-amazon-corretto
```
## check Java version
```
java -version
```
![image](https://user-images.githubusercontent.com/107158398/177623532-0b70e8d1-c590-4908-b42a-3690b78ea390.png)

## Download binary from Jenkins.io for centos 7
```
sudo yum install wget -y
```
```
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
```
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```
```
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io-2023.key
```
```
sudo yum upgrade -y
```
## Install & Start Jenkins
```
sudo yum install jenkins -y
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl start jenkins
```
```
sudo systemctl enable jenkins

```
## NB: Make sure to use jenkins.anaeleboo.com url while setting up the jenkins master
 ## Open port 8080 using firewall
 ```
 firewall-cmd --permanent --add-port=8080/tcp
 ```
 ```
 firewall-cmd --reload
 ```
 ## Add Certificate
 ```
firewall-cmd --zone=public --add-service=https
```
```
firewall-cmd --add-forward-port=port=443:proto=tcp:toport=8443
```
```
firewall-cmd --runtime-to-permanent
```
```
firewall-cmd --reload
```
```
firewall-cmd --list-all
```
## AWS SECURITY GROUPS:
### Lb and jenkins should be in the same subnet
### Bastion sg: inbound : ssh from anywhere & outbound : ssh to jenkins-sg only
### Jenkins SG: inbound: ssh from bastion-sg & custom tcp 0n port 8080 from lb-sg , outbound: all traffic
###  LB-sg: inbound: http and  https 80 & 443 from anywhere and outbound: tcp custom tcp on port 8080 to jenkins-sg
### Healthcheck in Target group:  /login and port should be 8080 for jenkins
![image](https://github.com/thedevopsguru1/Jenkins-installation-steps/assets/126810742/33f4dca5-8674-4a79-85cc-c0ed30383c4b)

## NB: If you are using centos 7 instance , please change the user to centos ( remove ec2-user everywhere)

 
 
 
 
 
 
 
 
 ## Adding certificate
 https://middlewaretechnologies.in/2022/03/how-to-install-and-configure-a-secure-jenkins-server.html#:~:text=Procedure%201%20Step1%3A%20Configure%20the%20Jenkins%20repository%20...,Step8%3A%20Restart%20the%20Jenkins%20service%20...%20More%20items
 
 2-  https://www.youtube.com/watch?v=2uYL4az1BVU
