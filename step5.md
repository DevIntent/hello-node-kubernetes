# Create your cluster

Estimated time: 38 min remaining

Ok, you are now ready to create your Container Engine cluster. A cluster consists of a master API server hosted by 
Google and a set of worker nodes. The worker nodes are Compute Engine virtual machines. Let’s create a cluster with 
two [n1-standard-1](https://cloud.google.com/compute/docs/machine-types) nodes (this will take a few minutes to complete):
```sh
$ gcloud container clusters create hello-world \
                --num-nodes 2 \
                --machine-type n1-standard-1
Creating cluster hello-world...done.
Created [https://container.googleapis.com/v1/projects/kubernetes-codelab/zones/us-central1-f/clusters/hello-world].
kubeconfig entry generated for hello-world.
NAME         ZONE           MASTER_VERSION  MASTER_IP       MACHINE_TYPE   STATUS
hello-world  us-central1-f  1.2.1           146.148.46.124  n1-standard-1  RUNNING
```
**Note**: Alternatively, you could create this cluster via the Console: 
Compute > Container Engine > Container Clusters > New container cluster.

You should now have a fully-functioning Kubernetes cluster powered by Google Container Engine:

![clusters](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-11.png)

Each node in the cluster is a Compute Engine instance provisioned with Kubernetes and docker binaries. 
If you are curious, you can list all Compute Engine instances in the project:
```sh
$ gcloud compute instances list
NAME                ZONE          MACHINE_TYPE   INTERNAL_IP   EXTERNAL_IP    STATUS
gke-hello-world-... us-central1-f n1-standard-1  10.240.223.99 104.197.29.149 RUNNING
gke-hello-world-... us-central1-f n1-standard-1  10.240.22.199 104.197.53.8   RUNNING
```
But you really shouldn’t have to use anything Compute Engine-specific but rather stick to the `kubectl` 
Kubernetes command line.

It’s now time to deploy your own containerized application to the Kubernetes cluster!

#### [Go to step 6](step6.md)
#### [Go back to step 4](step4.md)
