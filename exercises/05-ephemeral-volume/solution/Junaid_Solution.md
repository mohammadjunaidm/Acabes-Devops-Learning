Created a new namespace as Junaid with the below yaml
 
	apiVersion: v1
	kind: Namespace
	metadata:
	  name: junaid
	  labels:
	    name: junaid


Created the pod using the yaml attached.
kubectl apply -f nginx-pod.yaml	

SSH into the container and verified the path . Screenshot attached.
