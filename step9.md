# 9. Roll out an upgrade to your app

Estimated time: 13 min remaining

As always, the application you deployed to production requires bug fixes or additional features. 
Kubernetes is here to help you deploy a new version to production without impacting your users.

First, let’s modify the application. In the cloud console, edit `server.js` and update the response message:
```javascript
response.end("Hello Kubernetes World!");
```

We can now build and publish a new container image to the registry with an incremented tag:
```sh
$ docker build -t gcr.io/PROJECT_ID/hello-node:v2 . 
$ gcloud docker push gcr.io/PROJECT_ID/hello-node:v2
```

**Note**: Building and pushing this updated image should be much quicker as we take full advantage of the Docker cache.

We’re now ready for kubernetes to smoothly update our replication controller to the new version of the application:
```sh
$ kubectl rolling-update hello-node \
    --image=gcr.io/PROJECT_ID/hello-node:v2 \
    --update-period=2s
Creating hello-node-324d23dd3e0e2474d6b76dc599abb519
At beginning of loop: hello-node replicas: 2, hello-node-324d23dd3e0e2474d6b76dc599abb519 replicas: 1
...
At end of loop: hello-node replicas: 0, hello-node-324d23dd3e0e2474d6b76dc599abb519 replicas: 3
Update succeeded. Deleting old controller: hello-node
Renaming hello-node-324d23dd3e0e2474d6b76dc599abb519 to hello-node
hello-node
```
You should see in the standard output how the rolling update actually works:

1. A new replication controller is created based on the new image
1. The replica count on the new and old controllers is increased/decreased by one respectively until the desired number of 
replicas is reached
1. The original replication controller is deleted

While this is happening, the users of the services should not see any interruption. After a little while they will start
accessing the new version of your application. You can find more details on rolling updates in 
[this documentation](https://cloud.google.com/container-engine/docs/rolling-updates).

Hopefully with these deployment, scaling and update features you’ll agree that once you’ve setup your environment (your GKE/Kubernetes cluster here), Kubernetes is here to help you focus on the application rather than the infrastructure.

#### [Go to step 10](step10.md)
#### [Go back to step 8](step8.md)
