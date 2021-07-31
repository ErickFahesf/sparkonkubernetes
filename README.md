# Spark on Kubernetes
This repository storages files to configure spark on kubernetes cluster. 

I'm going to show the steps for configure spark on k8s. Each cloud provider has own kubernetes engine, choice a cloud provider to use a kubernetes engine. In this project, i used the Oracle Kubernetes Engine, it's a resource on Oracle Cloud Infrastructure. You can create your cluster Kubernetes on OCI following the steps here https://www.oracle.com/webfolder/technetwork/tutorials/obe/oci/oke-full/index.html .


## Step Zero: Prerequisites
1 - You have a Kubernetes cluster installed and running.

2 - You need to have the kubectl command line tool installed in you machine.

3 - Integrate the kubectl with kubernetes cluster.

## Step One: Create namespace
```
$ kubectl create -f namespace-spark-cluster.yaml
```
Create a new context to configure kubectl to work with our namespace.
```
$ CURRENT_CONTEXT=$(kubectl config view -o jsonpath='{.current-context}')
$ USER_NAME=$(kubectl config view -o jsonpath='{.contexts[?(@.name == "'"${CURRENT_CONTEXT}"'")].context.user}')
$ CLUSTER_NAME=$(kubectl config view -o jsonpath='{.contexts[?(@.name == "'"${CURRENT_CONTEXT}"'")].context.cluster}')
$ kubectl config set-context spark --namespace=spark-cluster --cluster=${CLUSTER_NAME} --user=${USER_NAME}
$ kubectl config use-context spark
```
## Step Two: Start master service
This service is for Spark cluster.
```
kubectl create -f spark-master-controller.yaml

```
Create a logical service endpoint that Spark workers can use to access the master pod.
```
kubectl create -f spark-master-service.yaml
```

