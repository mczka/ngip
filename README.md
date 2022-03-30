https://github.com/rancher/k3os

# AWS EC2 with k3OS 

version v0.22.2+k3s2/kernel 5.4.0-88 + alpine userspace

https://github.com/rancher/k3os/releases/download/v0.22.2-k3s2r0/k3os-amd64.iso


# takeover orginal ubuntu-focal-20.04 OS:

vi /tmp/config.yaml
k3os:
  datasource: aws

wget https://raw.githubusercontent.com/rancher/k3os/master/install.sh

chmod +x install.sh

sudo ./install.sh --takeover --debug --tty ttyS0 --config /tmp/config.yaml --no-format /dev/nvme0n1p1 https://github.com/rancher/k3os/releases/download/v0.22.2-k3s2r0/k3os-amd64.iso

# setup k3s

wget https://raw.githubusercontent.com/mczka/ngip/master/mysite-home.yaml

wget https://raw.githubusercontent.com/mczka/ngip/master/html-home/index.html

kubectl create configmap mysite-home-html --from-file index.html

kubectl apply -f mysite-home.yaml

wget https://raw.githubusercontent.com/mczka/ngip/master/mysite-iaas.yaml

mkdir html;
cd html

wget https://raw.githubusercontent.com/mczka/ngip/master/html-iaas/index.html

wget https://raw.githubusercontent.com/mczka/ngip/master/html-iaas/iaas.svg

kubectl create configmap mysite-iaas-html --from-file html

kubectl apply -f mysite-iaas.yaml


# test 

kubectl get configmap

kubectl get pods

kubectl get ingressroute


http://rancher.regnumtuum.com

http://ip.regnumtuum.com

http://ip.regnumtuum.com/iaas
