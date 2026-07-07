# all-installation-commands-for-devops
#kubectl installation
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
   chmod +x kubectl
   sudo mv kubectl /usr/local/bin/kubectl
   
   #kops installation
   curl -Lo kops https://github.com/kubernetes/kops/releases/download/$(curl -s https://api.github.com/repos/kubernetes/kops/releases/latest | grep tag_name | cut -d '"' -f 4)/kops-linux-amd64
chmod +x kops
sudo mv kops /usr/local/bin/kops
kops create cluster --name=tejkiran345.k8s.local --zones=us-east-1a,us-east-1b --control-plane-size=c7i-flex.large --control-plane-count=1 --control-plane-volume-size=24 --node-size=c7i-flex.large --node-count=3 --node-volume-size=25 --image=ami-091138d0f0d41ff90
#To install the NGINX Ingress Controller in Kubernetes, use:
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
#install terraform
sudo yum install -y yum-utils shadow-utils
sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/AmazonLinux/hashicorp.repo
sudo yum install terraform
