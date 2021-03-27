# kops

curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin/kubectl
wget https://github.com/kubernetes/kops/releases/download/1.6.1/kops-linux-amd64
chmod +x kops-linux-amd64
sudo mv kops-linux-amd64 /usr/local/bin/kops
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/installapt install zip 
apt install zip 
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws configure
aws s3 mb s3://clusters.k8s.appychip.vpc
aws s3 mb s3://clusters.k8s.qfit.vpc
export KOPS_STATE_STORE=s3://clusters.k8s.qfit.vpc
echo KOPS_STATE_STORE
echo ${KOPS_STATE_STORE}
kops --help
kops create --help
ssh-keygen
kops create cluster --cloud=aws --zones=ap-south-1a      --name=apsouth1.k8s.appychip.vpc --dns-zone=k8s.appychip.vpc      --dns private
kops edit ig --name=apsouth1.k8s.appychip.vpc nodes
kops edit ig --name=apsouth1.k8s.appychip.vpc master-ap-south-1a
kops update cluster apsouth1.k8s.appychip.vpc --yes

Cluster configuration has been created.
-----------------------------------------------------------------------------------------------
Suggestions:
 * list clusters with: kops get cluster
 * edit this cluster with: kops edit cluster apsouth1.k8s.appychip.vpc
 * edit your node instance group: kops edit ig --name=apsouth1.k8s.appychip.vpc nodes
 * edit your master instance group: kops edit ig --name=apsouth1.k8s.appychip.vpc master-ap-south-1a

Finally configure your cluster with: kops update cluster apsouth1.k8s.appychip.vpc --yes

------------------------------------------------------------------------------------------
Cluster is starting.  It should be ready in a few minutes.

Suggestions:
 * validate cluster: kops validate cluster
 * list nodes: kubectl get nodes --show-labels
 * ssh to the master: ssh -i ~/.ssh/id_rsa admin@api.apsouth1.k8s.appychip.vpc
The admin user is specific to Debian. If not using Debian please use the appropriate user based on your OS.
 * read about installing addons: https://github.com/kubernetes/kops/blob/master/docs/addons.md
 --------------------------------------------------------------------
