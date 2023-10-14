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