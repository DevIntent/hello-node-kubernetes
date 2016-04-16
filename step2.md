# Setup and Requirements

Estimated time: 58 min remaining

## Self-paced environment setup
If you don't already have a Google Account (Gmail or Google Apps), you must [create one](https://accounts.google.com/SignUp). 
Sign-in to Google Cloud Platform console ([console.cloud.google.com](http://console.cloud.google.com/)) and 
create a new project:

![gcp](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-3.png)
![new-project](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-4.png)

Remember the project ID, a unique name across all Google Cloud projects (the name above has already been taken and 
will not work for you, sorry!). It will be referred to later in this codelab as `PROJECT_ID`.

Next, you'll need to [enable billing](https://console.developers.google.com/billing) in the Developers Console in 
order to use Google Cloud resources and 
[enable the Container Engine API](https://console.developers.google.com/project/_/kubernetes/list).

Running through this codelab shouldn’t cost you more than a few dollars, but it could be more if you decide to use more 
resources or if you leave them running (see “cleanup” section at the end of this document). Google Container Engine 
pricing is documented [here](https://cloud.google.com/container-engine/docs/#pricing).

New users of Google Cloud Platform are eligible for a [$300 free trial](https://console.developers.google.com/billing/freetrial?hl=en).

Google Cloud Shell
While Google Cloud and Kubernetes can be operated remotely from your laptop, in this codelab we will be using 
[Google Cloud Shell](https://cloud.google.com/cloud-shell/), a command line environment running in the Cloud. 
This Debian-based virtual machine is loaded with all the development tools you’ll need (docker, gcloud, kubectl and more),
it offers a persistent 5GB home directory, and runs on the Google Cloud, greatly enhancing network performance and 
authentication. This means that all you will need for this codelab is a browser (yes, it works on a Chromebook).

To activate Google Cloud Shell, from the developer console simply click the button on the top right-hand side 
(it should only take a few moments to provision and connect to the environment):

![activate-cloud-shell](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-5.png)
![cloud-shell](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-6.png)

Once connected to the cloud shell, you should see that you are already authenticated and that the project is 
already set to your `PROJECT_ID`:
```
$ gcloud auth list
Credentialed accounts:
 - <myaccount>@<mydomain>.com (active)
```
```
$ gcloud config list project
[core]
project = <PROJECT_ID>
```
If the project is not set, simply issue the following command:
```
$ gcloud config set project <PROJECT_ID>
```
Looking for you `PROJECT_ID`? Check out what ID you used in the setup steps or look it up in the console dashboard:
![console-dash](https://codelabs.developers.google.com/codelabs/hello-kubernetes/img/img-7.png)

Finally, set the default zone and project configuration:
```
$ gcloud config set compute/zone us-central1-f
$ gcloud config set compute/region us-central1
```
You can pick and choose different zones too. Learn more about zones in 
[Regions & Zones documentation](https://cloud.google.com/compute/docs/zones).

**Note**: If you run gcloud on your own machine, the config settings would be persisted across sessions.  
But in Cloud Shell, you will need to set this for every new session or reconnection.

#### [Go to step 3](step3.md)
#### [Go back to step 1](README.md)
