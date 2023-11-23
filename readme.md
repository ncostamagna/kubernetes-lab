

<!-- toc -->

- [K3s](#k3s)
  * [Setup](#setup)
  * [Start](#start)
- [Microk8s](#microk8s)
  * [Setup](#setup-1)
  * [Install Addons](#install-addons)
  * [Dashboard](#dashboard)
  * [Kubectl with MicroK8s](#kubectl-with-microk8s)
- [Kubernates](#kubernates)

<!-- tocstop -->

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


# Kubernates

```sh
kubectl apply -f pod-test1.yaml # we execute the yaml file

kubectl get all # get all objects
kubectl get pods # get all pods
kubectl get pods -o wide # get pods node

kubectl describe pod {nombre} # pod details
kubectl delete -f {nombre} # we delete a pod with its file name (pod-test1.yaml )
kubectl delete pod {nombre} # or with the object type (pod) and name (nginx)
```

We can't enter pod from out, if we want to see, we must execut the follow command

```sh
minikube ssh
docker ps # list inside minikube, dockers than has ran
```

where we start a pod, we can see it from out until we up a service

```sh

kubectl exec -it nginx bash # enter pod, nginx is the name of the pod

kubectl logs mipod # pod logs

# we setup curl
curl localhost # we can see how we recive the default html

kubectl port-forward nginx 8080:80 # nginx (pod name), from 80 (nginx) to 8080 of our machine

# In this way, if we execute:
curl localhost
# in our machine, we will able to enter without to enter to cluster
```