# 8. Scale up your app

Estimated time: 18 min remaining

One of the powerful features offered by Kubernetes is how easy it is to scale your application. Suppose you suddenly 
need more capacity for your application; you can simply tell the replication controller to manage a new number of 
replicas for your pod:
```sh
$ kubectl scale rc hello-node --replicas=3
$ kubectl get pods
NAME               READY     STATUS    RESTARTS   AGE
hello-node-6uzt8   1/1       Running   0          8m
hello-node-gxhty   1/1       Running   0          34s
hello-node-z2odh   1/1       Running   0          34s
```
You now have three replicas of your application, each running independently on the cluster with the load balancer 
you created earlier and serving traffic to all of them.
```sh
$ kubectl get rc hello-node
CONTROLLER   CONTAINER(S)   IMAGE(S)                    SELECTOR         REPLICAS
hello-node   hello-node     gcr.io/..../hello-node:v1   run=hello-node   3
```
Note the **declarative approach** here - rather than starting or stopping new instances you declare how many instances 
you want to be running. Kubernetes reconciliation loops simply make sure the reality matches what you requested and 
take action if needed.

Here’s a diagram summarizing the state of our Kubernetes cluster:

![gke-diagram](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-13.png)

#### [Go to step 9](step9.md)
#### [Go back to step 7](step7.md)
