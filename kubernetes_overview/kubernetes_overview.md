# Kubernetes Overview 


Kubernetes is a platform for container orchestration commonly used with the docker container runtime.

In this document I plan to give an overview of the software and explain why its usually used for different audiences.

## For Developers

From a software engineer Kubernetes allows for the developer to design self contained applications that can be packaged as container images and deployed out to the cluster via configuration as a file.  

That allows the developer to focus on generating a docker image that is functional and not worry about anything but the input configuration usually injected via environment variables or config file.

This application can be exposed other applications via services and routed to from the edge via ingress. 

A secondary benefit of kubernetes for developers is not requiring the deployment of dependant databases or services to their local machine for testing.  Kubernetes allows users to port-forward any private services from the cluster to their local machine.

## For Devops

One of the biggest benefits of kubernetes for devops is the reduced burden of maintaining a virtual machine for each application.  

Kubernetes uses node pools and rather having to spin up a virtual machine for an application you deploy it to the kubernetes cluster and allow it to determine where that application best fits based on the resource requirements of that application.  K8s will then deploy that application to a node and expose it to the virtualized network within the cluster exposing it as a dns name to all applications.

K8s also enables the ability for applications to be exposed to the internet in seconds via automatically spinning up a load balancer if needed or exposing the application via **Ingress**.  

Ingress associates a given service to a specified route matcher allowing for multiple applications to be served at the same domain and be routed to in an expressive way.

As for non webservices kubernetes has a concept of Jobs which allow for applications to be run on cron and even has baked in functionality for preventing runs from overlapping.

## Summary

Kubernetes is a flexible tool for deploying applications that abstracts much of the low level problems such as right sizing virtual machines and exposing services to each other in a secure fashion.

For developers we are able to focus on developing containerized applications and utilize other services that are already deployed to the cloud in a easier fashion than we have in the past.

## Workshop

In the following workshop I plan to go over kubernetes from a microservice perspective and deep dive on the different components that combine together to empower developers and devops to build and deploy applications fast and easy.

### Session 1: Kubernetes from a Microservice based approach
Covers the building blocks of kubernetes from a microservice standpoint demonstrating the benefits.

Session Notes: [Microservices](./microservices.md)

### Session 2: Kubernetes Live Coding
Covers the `kubectl` cli and covers the different levers you can pull with the various kubernetes configuration files.

### Session 3: Kubernetes Onhands training

You will be provide a series of applications where you can deploy and orchestrate the deployments in whatever cluster you wish.  I will also try to provide a cluster with ingress with tls configured.