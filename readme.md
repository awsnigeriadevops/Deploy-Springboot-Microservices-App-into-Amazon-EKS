# Deploy-Springboot-Microservices-App-into-Amazon-EKS

## Create EC2 to setup Jenkins
    - Amazon Machine Image (AMI) - Ubuntu Server 20
    - Instance type - t2.medium
    - Allow port 8080 SG

## SSH into instance :
    - `sudo apt update`
    - install Maven, it automatically installs Java: `sudo apt install maven -y`
    - `mvn --version`
    - `java -version`

## Setup Jenkins
    - curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
    - echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
    - sudo apt update
    - sudo apt install jenkins -y