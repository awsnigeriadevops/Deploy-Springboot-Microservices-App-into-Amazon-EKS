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

## Install Pre-requisites:
    ### AWS CLI:
        - curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" 
        - sudo apt install unzip
        - sudo unzip awscliv2.zip  
        - sudo ./aws/install
        - aws --version

    ### Install eksctl:
        - curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
        - sudo mv /tmp/eksctl /usr/local/bin
        - eksctl version

    ### Install kubectl
        - sudo curl --silent --location -o /usr/local/bin/kubectl   https://s3.us-west-2.amazonaws.com/amazon-eks/1.22.6/2022-03-09/bin/linux/amd64/kubectl
        - sudo chmod +x /usr/local/bin/kubectl 
        - kubectl version --short --client

