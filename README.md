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
