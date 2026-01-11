Installed minikube on my pc

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube


Installed kubectl 

curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/kubectl


Started minikube 

minikube start --driver=docker

Verified the nodes :
 
 kubectl get nodes
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   68m   v1.34.0

Created the namespace.yaml 
 kubectl apply -f namespace.yaml

Create a pod in the above namespace
  kubectl apply -f pod.yaml

Installed K9s

curl -sS https://webinstall.dev/k9s | bash
source ~/.bashrc

Verified the pods in K9s

entered "S" key after selecting the pod to enter shell of that pod.

Checked the logs both using k9s (shortcut key 'l')and shell command "kubectl logs mypod -n junaid-pod-creation"



Able to view the ip of the pod (10.244.0.6)
