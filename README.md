# Spark on Kubernetes
This repository storages files to configure spark on kubernetes cluster. 

I'm going to show the steps for configure spark on k8s. Each cloud provider has own kubernetes engine, choice a cloud provider to use a kubernetes engine. In this project, i used the Oracle Kubernetes Engine, it's a resource on Oracle Cloud Infrastructure. You can create your cluster Kubernetes on OCI following the steps here https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html .


## Step Zero: Prerequisites
1 - You have a Kubernetes cluster installed and running.

2 - You need to have the kubectl command line tool installed in you machine.

3 - Integrate the kubectl with kubernetes cluster.

## Step One: Create namespace
