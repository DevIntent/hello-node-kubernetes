# 7. Allow external traffic

Estimated time: 26 min remaining

The [replication controller](https://cloud.google.com/container-engine/docs/replicationcontrollers/) is a critical 
(and awesome) piece of the Kubernetes architecture. 

The **replication controller** is responsible for ensuring that a specified number of pod "replicas" are running at any 
given time (more on that in the next section) and it will create or delete replicas to reach the desired state.

To create the Replication Controller, the following needs to be done:
```sh
nano replicationController.json
```

Paste the contents of [this gist](https://gist.github.com/Splaktar/47a76f2dc9e053073e6278bdb5dfec5c) into the file and save.

```sh
kubectl create -f replicationController.json`
replicationcontroller "hello-node" created
```

By default, the pod is only accessible by its internal IP within the cluster. In order to make the `hello-node` container 
accessible from outside the kubernetes virtual network, you have to expose the pod as a kubernetes service.

We can expose the pod with the `kubectl expose` command and the `--type="LoadBalancer"` flag 
which creates an external IP to accept traffic:
```sh
$ kubectl expose rc hello-node --type="LoadBalancer"
```
The flag used in this command specifies that we’ll be using the load-balancer provided by the underlying infrastructure 
(in this case the [Compute Engine load balancer](https://cloud.google.com/compute/docs/load-balancing/)) and 
`“rc”` is a reference to the replication controller.

The Kubernetes master creates the load balancer and related Compute Engine forwarding rules, target pools, and 
firewall rules to make the service fully accessible from outside of Google Cloud Platform.

More details on defining and configuring replication controllers can be found 
[here](https://cloud.google.com/container-engine/docs/replicationcontrollers/operations).

**Note**: If you’re interested in what Container Engine does under the covers with Compute Engine VMs, you can check how 
all of your VMs are tagged with a common prefix (`kubectl get nodes`). This tag can be used to operate on all of the VMs 
in your container cluster with a single command.

To find the publicly-accessible IP address of the service, simply request `kubectl` to list the `hello-node` cluster service:
```sh
$ kubectl get services
NAME         CLUSTER_IP    EXTERNAL_IP     PORT(S)    SELECTOR         AGE
hello-node   10.3.246.12   23.251.159.72   8080/TCP   run=hello-node   53s
kubernetes   10.3.246.12   <none>          443/TCP    21m
```
Note there are 2 IP addresses listed, both serving port `8080`. One is the internal IP that is only visible inside your 
cloud virtual network; the other is the external load-balanced IP. In this example, the external 
IP address is `23.251.159.72`.

You should now be able to reach the service by pointing your browser to this address: `http://<EXTERNAL_IP>:8080`

![external-ip](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-12.png)

#### [Go to step 8](step8.md)
#### [Go back to step 6](step6.md)
