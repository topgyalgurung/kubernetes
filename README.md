# kubernetes

## Running first Hello World application 
```
$ minikube status 
🤷  Profile "minikube" not found. Run "minikube profile list" to view all profiles.
👉  To start a cluster, run: "minikube start"

$ minikube start
$ kubectl get nodes 
NAME       STATUS   ROLES                  AGE   VERSION
minikube   Ready    control-plane,master   22s   v1.22.2

$ kubectl get all
NAME                 TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
service/kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   108s


$ kubectl create -f helloworld.yaml  # -f is file
deployment.apps/helloworld created 

$ kubectl expose deployment helloworld --type=NodePort 
service/helloworld exposed

$ minikube service helloworld

```
