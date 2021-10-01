# kubernetes

- [Kubernetes in 5 mins](https://youtu.be/PH-2FfFD2PU)
- [Kubernetes vs. Docker: It's Not an Either/Or Question](https://youtu.be/2vMEQ5zs1ko)

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
#### Making it Production Ready
- add, change and delete labels
```
  $ kubectl get pods 
  $ kubectl get pods --show-labels

# change or overwrite 
$ kubectl label pod/helloworld app=helloworldapp --overwrite
pod/helloworld labeled

# delete label
$ kubectl label pod/helloworld app-

## selectors
# WORKING WITH Labels 
$ kubectl get pods --selector env=production
$ kubectl get pods --selector env=production --show-labels

# Search by multiple labels 
$ kubectl get pods --selector dev-lead=karthik,env=production
$ kubectl get pods --selector dev-lead!=karthik,env=production
$ kubectl get pods --selector dev-lead=karthik,env=production --show-labels

$ kubectl get pods -l 'release-version in (1.0,2.0)'
$ kubectl get pods -l 'release-version notin (1.0,2.0)'

$ kubectl delete pods -l dev-lead=karthik
pod "homepage-dev" deleted
pod "homepage-prod" deleted
pod "homepage-staging" deleted


```
