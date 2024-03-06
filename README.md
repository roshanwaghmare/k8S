# k8S

**Installing kubeadm**

https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/#installing-runtime

and refer this repository
https://github.com/LondheShubham153/kubestarter/blob/main/kubeadm_installation.md

````
 1  sudo apt update
    2  sudo apt-get install -y apt-transport-https ca-certificates curl
    3  sudo apt install docker.io -y
    4  sudo systemctl enable --now docker # enable and start in single command.
    5  sudo apt-get update
    6  # apt-transport-https may be a dummy package; if so, you can skip that package
    7  sudo apt-get install -y apt-transport-https ca-certificates curl gpg
    8  curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
    9  # This overwrites any existing configuration in /etc/apt/sources.list.d/kubernetes.list
   10  echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
   11  sudo apt-get update
   12  sudo apt-get install -y kubelet kubeadm kubectl
   13  sudo apt-mark hold kubelet kubeadm kubectl
   14  sudo kubeadm init
   15  mkdir -p $HOME/.kube
````
### These instructions are for Kubernetes 1.29.

Install Docker first

```
# using 'sudo su' is not a good practice.
sudo apt update
sudo apt-get install -y apt-transport-https ca-certificates curl
sudo apt install docker.io -y

sudo systemctl enable --now docker # enable and start in single command.
```

1.Update the apt package index and install packages needed to use the Kubernetes apt repository:
```
sudo apt-get update
# apt-transport-https may be a dummy package; if so, you can skip that package
sudo apt-get install -y apt-transport-https ca-certificates curl gpg

```

2. Download the public signing key for the Kubernetes package repositories. The same signing key is used for all repositories so you can disregard the version in the URL:
```
# If the folder `/etc/apt/keyrings` does not exist, it should be created before the curl command, read the note below.
# sudo mkdir -p -m 755 /etc/apt/keyrings
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.29/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
````

Note: In releases older than Debian 12 and Ubuntu 22.04, folder /etc/apt/keyrings does not exist by default, and it should be created before the curl command.

3. Add the appropriate Kubernetes apt repository. Please note that this repository have packages only for Kubernetes 1.29; for other Kubernetes minor versions, you need to change the Kubernetes minor version in the URL to match your desired minor version (you should also check that you are reading the documentation for the version of Kubernetes that you plan to install).
```
# This overwrites any existing configuration in /etc/apt/sources.list.d/kubernetes.list
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.29/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
4.Update the apt package index, install kubelet, kubeadm and kubectl, and pin their version:
````
sudo apt-get update
sudo apt-get install -y kubelet kubeadm kubectl
sudo apt-mark hold kubelet kubeadm kubectl
````
