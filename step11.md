# 11. Cleanup

Estimated time: 4 min remaining

Time for some cleaning of the resources used (to save on cost and to be a good cloud citizen).

To delete the dervice, we need to get the service name first:
```sh
$ kubectl get service
NAME                       CLUSTER-IP    EXTERNAL-IP       PORT(S)    AGE
hello-node-2142604176-x8   10.124.132.1   123.132.123.151   8080/TCP   1h
```
Then we can delete the service, which also deletes your external load balancer:
```sh
$ kubectl delete services hello-node-2142604176-x8
service "hello-node-2142604176-x8" deleted
```

Delete the running pods:
```sh
$ kubectl delete rc hello-node
```
Delete your cluster:
```sh
$ gcloud container clusters delete hello-node
   Waiting for cluster deletion...done.
   name: operation-xxxxxxxxxxxxxxxx
   operationType: deleteCluster
   status: done
   target: /projects/kubernetes-codelab/zones/us-central1-f/clusters/hello-world
   zone: us-central1-f
```
This deletes the Google Compute Engine instances that are running the cluster.

Finally delete the Docker registry storage bucket hosting your image(s):
```sh
$ gsutil ls
gs://artifacts.<PROJECT_ID>.appspot.com/
$ gsutil rm -r gs://artifacts.<PROJECT_ID>.appspot.com/
Removing gs://artifacts.<PROJECT_ID>.appspot.com/...
```
Of course, you can also delete the entire project but note that you must first disable billing on the project. 
Additionally, deleting a project will only happen after the current billing cycle ends.

#### [Go to step 12](step12.md)
#### [Go back to step 10](step10.md)
