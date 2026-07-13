# all-installation-commands-for-devops
#nexus
cd /opt/
wget https://download.sonatype.com/nexus/3/nexus-3.94.0-12-linux-x86_64.tar.gz
tar -zxvf  nexus-3.94.0-12-linux-x86_64.tar.gz
useradd nexus
 chown -R nexus:nexus nexus-3.94.0-12 sonatype-work
 su -nexus
 cd /opt/
 cd  nexus-3.94.0-12/bin/
 ./nexus start =>its shows nexus start
 ./nexus stop =>its stop the nexus
#jenkins installation
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/rpm-stable/jenkins.repo
sudo yum upgrade
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-21-openjdk
sudo yum install jenkins
sudo systemctl daemon-reload
yum install -y java-21-amazon-corretto
systemctl start jenkins
#docker installation
yum install docker -y
yum install git -y
systemctl start docker
#kubectl installation
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   chmod +x kubectl
   sudo mv kubectl /usr/local/bin/kubectl
   #minikube installation
   curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
   sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
   sudo yum update -y
   sudo yum install docker -y
   sudo systemctl start docker
   sudo systemctl enable docker
   minikube start --driver=docker --force

   #kops installation
   curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
chmod +x kops
sudo mv kops /usr/local/bin/kops
aws s3 ls ==> its show the s3 bucket list 
#where u want to store the cluster use below command and create cluster
export STATE_KOPS_STORE=s3://"ur bucket name"
kops create cluster --name=tejkiran345.k8s.local --zones=us-east-1a,us-east-1b --control-plane-size=c7i-flex.large --control-plane-count=1 --control-plane-volume-size=24 --node-size=c7i-flex.large --node-count=3 --node-volume-size=25 --image=ami-091138d0f0d41ff90
kops update cluster --name tejkiran345.k8s.local --yes --admin
#To install the NGINX Ingress Controller in Kubernetes, use:
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
#install terraform
sudo yum install -y yum-utils shadow-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum install terraform
#installation for the aws cli to connect vscode to aws server
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi /qn
aws --version
Method 1: Using Windows Environment Variables
Press Win + R.
Type:
sysdm.cpl
Press Enter.
Go to the Advanced tab.
Click Environment Variables.
Under System variables, select Path → Edit.
Click New.
Add:
C:\Program Files\Amazon\AWSCLIV2\
Click OK on all windows.
Close all PowerShell/VS Code windows and open a new terminal.

Verify:

where.exe aws

Expected:

C:\Program Files\Amazon\AWSCLIV2\aws.exe

Then:

aws --version
