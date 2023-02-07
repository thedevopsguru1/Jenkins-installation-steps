# Jenkins-installation-steps
## Installing Dependencies:
## JAVA JDK & JRE
```
sudo yum install java-11-openjdk –y
```
## check Java version
```
java -version
```
![image](https://user-images.githubusercontent.com/107158398/177623532-0b70e8d1-c590-4908-b42a-3690b78ea390.png)

## Download binary from Jenkins.io for centos 7
```
yum install wget -y
```
```
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```
```
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
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
systemctl enable jenkins
```
 ## Open port 8080 using firewall
 ```
 firewall-cmd --permanent --add-port=8080/tcp
 ```
 ```
 firewall-cmd --reload
 ```
 ## Adding certificate
 https://middlewaretechnologies.in/2022/03/how-to-install-and-configure-a-secure-jenkins-server.html#:~:text=Procedure%201%20Step1%3A%20Configure%20the%20Jenkins%20repository%20...,Step8%3A%20Restart%20the%20Jenkins%20service%20...%20More%20items
