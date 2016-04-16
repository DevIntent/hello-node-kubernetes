# 6. Create your pod

Estimated time: 31 min remaining

From now on we’ll be using the standard Kubernetes command line tool: `kubectl` 
(already set up in your Cloud Shell environment).

A kubernetes **pod** is a group of containers, tied together for the purposes of administration and networking. 
It can contain a single container or multiple. Here we’ll simply use one container built with your Node.js image 
stored in our private container registry. It will serve content on port 8080.

Let’s now create a pod with the `kubectl run` command (replace `PROJECT_ID` with your own project name):
```sh
$ kubectl run hello-node \
    --image=gcr.io/PROJECT_ID/hello-node:v1 \
    --port=8080
CONTROLLER  CONTAINER(S)  IMAGE(S)                     SELECTOR        REPLICAS
hello-node  hello-node    gcr.io/..../hello-node:v1    run=hello-node  1
```
Note you can also [create pods from JSON or YAML templates](https://cloud.google.com/container-engine/docs/kubectl/create).

Now is probably a good time to run through some of the following interesting `kubectl` commands 
(none of these will change the state of the cluster, 
[full documentation](https://cloud.google.com/container-engine/docs/kubectl/)):
```sh
$ kubectl get pods
$ kubectl logs
$ kubectl cluster-info
$ kubectl config view
$ kubectl get events
```
At this point you should have our container running under the control of Kubernetes but we still have to make it 
accessible to the outside world.

#### [Go to step 7](step7.md)
#### [Go back to step 5](step5.md)
