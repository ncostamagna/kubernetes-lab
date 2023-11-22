# K3s

For more information you can see the official website: https://k3s.io/

## Setup

```sh
curl -sfL https://get.k3s.io | sh -

sudo k3s kubectl get node

mkdir -p ~/.kube
sudo k3s kubectl config view --raw | tee ~/.kube/config
chmod 600 ~/.kube/config

kubectl get nodes
```

## Start

```sh
sudo k3s kubectl get node


```

# Microk8s

Is better than K3s, you can see the website: 

## Setup 

```sh
sudo snap install microk8s --classic --channel=1.23/stable

sudo usermod -a -G microk8s [user]

sudo chown -f -R [user] ~/.kube
```

## Install Addons

```sh
microk8s enable dns dashboard storage 
```

## Dashboard

```sh
microk8s dashboard-proxy
```

If you have problems with chrome, you can use firefox

## Kubectl with MicroK8s

You can see the configuration in microK8s

```sh
microk8s config
```

If you want to use the kubectl, you need to set this configuration in the .kube folder

```sh
cd $HOME
mkdir .kube
cd .kube
microk8s config > config
```