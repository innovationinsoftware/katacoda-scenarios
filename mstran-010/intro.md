![logo](mstran-010/assets/logo-sm.png)

## Objective

The objective of this scenario is to demonstrate how to use Istio ingress and egress rules to control access into a Kuberenetes cluster and outside of a Kubernetes cluster to an external URL.

## Please be advised ...

This scenario preloads a multi-node Kubernetes cluster and Load Balancer that are created using Kubernetes in Docker ([`KinD`](https://kind.sigs.k8s.io/)). There will be one control plane node and two worker nodes. You might see the cluster spinning up when you view the teminal pane in Lesson 1. ***Be patient. It might take a few minutes for the cluster to spin up and load.***

## Whatg you'll be doing

In this scenario, you are going to install a [demonstration microservice](https://hub.docker.com/r/reselbob/istiocode/) written under Node.JS and installed as a Docker container from [DockerHub](https://hub.docker.com/r/reselbob/istiocode/).

![Istio App](mstran-010/assets/istio-app.png)

The application has two subordinate services, `frontend` and `business`. `frontend` delegates to `business` to call `worldclockapi.com` to get the current time. However, because the microservice will be running under a Kubernetes cluster controlled by an Istio service mesh, users cannot access the `frontend` service by default. An ingress rule is needed to allow access. Part of this scenario is to apply a pre-installed ingress rule to Istio.

However, even if users could access the microservice, the microservice would not be fully operational because the subordinate service, `business` will still try to access, `worldclockapi.com`. Istio will not permit this unless an egress rule is set to allow calls to the external site. The final part of this scenario is to apply a pre-installed egress rule to Istio to allow access to `worldclockapi.com`.

In addition to working with the demonstration API you'll install the Isito Add On, [Kiali](https://kiali.io/) and [Grafana](https://grafana.com/). These tools allow you to manage and monitor activities within the Istio service mesh.

## Contents


This scenarios is divided into the following steps.

* **Step 1** - Confirm that Kubernetes and the Load Balancer are Installed
* **Step 2** - Install Istio
* **Step 3** - Implement an Ingress rule under Istio
* **Step 4** - Implement an Egress rule under Istio
* **Step 5** - Exposing the Istio Add-Ons to the outside world
* **Step 6** - Viewing the Istio Add-Ons in a web browser



## Executing command line instructions 

This scenario is completely interactive. The instructions you'll be given will be executed directly in the terminal window that is embedded directly in the Katacoda interactive learning environment. In the steps to come, when you see a command line instruction with a black background and check mark at the end, like so:

![Katacoda command line](mstran-010//assets/command.png)

just click on it and the command will execute in the interative terminal window.

