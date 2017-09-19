---
layout: post
title:  "Resize cluster in Google container engine"
date:   2017-09-19 23:52:59 +0000
author: anupvarghese
comments: true
---


```shell
gcloud container clusters resize my_cluster --size=0
Pool [default-pool] for [my_cluster] will be resized to 0.

Do you want to continue (Y/n)?  Y

Resizing my_cluster...done.
```

This will resize the cluster to 0 yet keep its configs intact without getting charged.
