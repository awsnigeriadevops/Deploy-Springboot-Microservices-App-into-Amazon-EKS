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
    - curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
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

## Create IAM Role with Administrator Access
## Assign the role to EC2 instance

## Switch to Jenkins user
    - sudo su - jenkins

## Create EKS Cluster with two worker nodes using eksctl
    eksctl create cluster --name study-group-eks --region us-east-1 --nodegroup-name study-group-nodes --node-type t3.small --managed --nodes 2 

## Create ECR Repo

## Install Docker
    - sudo apt update
    - sudo apt install docker.io -y

    Add Ubuntu user to Docker group
    - sudo usermod -aG docker $USER
    exit the terminal and log back in

    ### Start Docker
    - sudo systemctl start docker
    - sudo systemctl enable docker
    - sudo systemctl status docker

## Add jenkins user to Docker group
    - sudo usermod -a -G docker jenkins

## Restart Jenkins service
    - sudo service jenkins restart

## Reload system daemon files
    - sudo systemctl daemon-reload

## Restart Docker service as well
    sudo service docker stop
    sudo service docker start

## Restart Jenkins from the UI and Login again

## Install Plugins inside Jenkins
    - Docker, Docker Pipeline, Kubernetes CLI

## Create Maven3 variable under Global tool configuration in Jenkins
    - Name: Maven3
    - MAVEN_HOME: 

## Create Credentials for connecting to Kubernetes Cluster using kubeconfig



## Create Pipeline and Copy the pipeline code from below
   
## 
    - eksctl get cluster --name demo-eks --region us-east-1
    This should confirm that EKS cluster is up and running.

    - Kubectl get nodes
    - eksctl get cluster --name demo-eks --region us-east-1

## Get config file and save it locally
    sudo cat /var/lib/jenkins/.kube/config

## Add Credentials in Jenkins
    - Global Credentials
    - Kind: Secret file

## Generate Pipeline Syntax
    - sample step : withKubeConfig
    - credentials: the saved kubeconfig file

## Check deployment
    kubectl get pods
    kubectl get deployments
    kubectl get services