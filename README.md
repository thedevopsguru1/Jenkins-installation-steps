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
