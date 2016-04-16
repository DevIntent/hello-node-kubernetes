# 4. Create a Docker container image

Estimated time: 50 min remaining

Next, create a `Dockerfile` which describes the image that you want to build. Docker container images can extend from 
other existing images so for this image, we'll extend from an existing Node image.
```Dockerfile
$ nano Dockerfile
FROM node:0.12
EXPOSE 8080
COPY server.js .
CMD node server.js
```
This “recipe” for the Docker image will start from the `node` image found on the Docker hub, expose port 8080, 
copy our `server.js` file to the image and start the node server as we previously did manually.

Save this `Dockerfile` and build this image by running:
```sh
$ docker build -t gcr.io/PROJECT_ID/hello-node:v1 .
```
Once this completes (it’ll take some time to download and extract everything) you can test the image locally with the 
following command which will run a Docker container as a daemon on port 8080 from our newly-created container image:
```sh
$ docker run -d -p 8080:8080 gcr.io/PROJECT_ID/hello-node:v1
325301e6b2bffd1d0049c621866831316d653c0b25a496d04ce0ec6854cb7998
```
And again take advantage of the Web preview feature of CloudShell:

![web-preview](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-8.png)

Or use ‘curl’ or ‘wget’ from your CloudShell prompt if you’d like:
```sh
$ curl http://localhost:8080
Hello World!
```

**Note**: Here’s the [full documentation](https://docs.docker.com/reference/run/) for the `docker run` command.

Let’s now stop the container:
```sh
$ docker ps
CONTAINER ID        IMAGE                              COMMAND
2c66d0efcbd4        gcr.io/PROJECT_ID/hello-node:v1    "/bin/sh -c 'node    
$ docker stop 2c66d0efcbd4
2c66d0efcbd4
```
Now that the image works as intended we can push it to the 
[Google Container Registry](https://cloud.google.com/tools/container-registry/), a private repository for your 
Docker images accessible from every Google Cloud project (but also from outside Google Cloud Platform):
```sh
$ gcloud docker push gcr.io/PROJECT_ID/hello-node:v1
```
If all goes well, you should be able to see the container image listed in the console: 
Compute > Container Engine > Container Registry. We now have a project-wide Docker image available which Kubernetes 
can access and orchestrate as we’ll see in a few minutes.

![gcr](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-10.png)

**Note**: While here we used a generic domain for the registry (gcr.io), you can also be more specific about which zone 
and bucket to use, details are documented [here](https://cloud.google.com/container-registry/docs/#pushing_to_the_registry).

If you’re curious, you can navigate through the container images as they are stored in Google Cloud Storage by 
following this [link](https://console.cloud.google.com/storage/browser/). 

**Note**: The full link should read https://console.cloud.google.com/storage/browser?project=PROJECT_ID

#### [Go to step 5](step5.md)
#### [Go back to step 3](step3.md)
