---
layout: post
title:  "Getting started with Kubernetes on ACS"
date:   2017-03-18 14:29:59 +0000
categories: kubernetes azure acs
author: anupvarghese
---
Azure Container Services(ACS) is the new container solution from Azure. Also, it supports Kubernetes. I was trying to start a Kubernetes cluster on ACS, here are the steps I took to get it up and running.

***Get ACS Engine & Prepate docker container***

Clone the ACS engine from [here](https://github.com/Azure/acs-engine)

Run `./scripts/devenv.sh` from the cloned path

By running the above script, our Docker container would be ready & we can `bash` into it by
 ```shell
docker run -it --privileged -v /var/run/docker.sock:/var/run/docker.sock -v /path/to/repo/acs-engine:/gopath/src/github.com/Azure/acs-engine -w /gopath/src/github.com/Azure/acs-engine acs-engine /bin/bash
```
_You can also run it locally but I choose Docker for keeping the packages out of my local environment_

***Create Kubernetes Cluster***

We are now ready to `az login` with Azure credentials to fire some Azure CLI commands

Create a resource group to manage the over all process

`az group create -n my-cluster -l "eastus"`

We are now ready to create the Kubernetes cluster

`az acs create -n mb-cluster -g my-cluster --dns-prefix my-cluster --orchestrator-type kubernetes`

If everything runs properly, we will get `my-cluster` up and running

***Warning***

This process creates Azure D Series servers for master & nodes and it may be expensive. If you would like to try this process and then be sure to remove the resource to remove all the servers after the trial.

`az resource delete -n my-cluster` will remove the resource and cluster properly
