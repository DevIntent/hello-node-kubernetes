# hello-node-kubernetes
Host your NodeJS app in a Docker container that is replicated in [Kubernetes](http://kubernetes.io/)!

Estimated time to complete: 60 min

## Introduction

The goal of this codelab is for you to turn your code (a simple Hello World node.js app here) into a replicated
application running on Kubernetes. We will show you how to take code that you have developed on your machine, 
turn it into a Docker container image, and then run that image on [Google Container Engine](https://cloud.google.com/container-engine/).

Here’s a diagram of the various parts in play in this codelab to help you understand how pieces fit with one another. 
Use this as a reference as we progress through the codelab; it should all make sense by the time we get to the end 
(but feel free to ignore this for now).

![gke-diagram](https://cloud.githubusercontent.com/assets/3506071/14581350/cd6d65ca-03b8-11e6-993f-2cbb0d50f149.png)

Kubernetes is an open source project (available on [kubernetes.io](http://kubernetes.io/)) which can run on many different 
environments, from laptops to high-availability multi-node clusters, from public clouds to on-premise deployments, 
from virtual machines to bare metal.

For the purpose of this codelab, using a managed environment such as Google Container Engine (a Google-hosted version of 
Kubernetes running on Compute Engine) will allow you to focus more on experiencing Kubernetes rather than setting up the 
underlying infrastructure.

#### [Go to next step](step2.md)
