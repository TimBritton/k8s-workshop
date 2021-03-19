---
marp: true
theme: gaia
_class: invert
---
# Kubernetes
![center bg](https://media.giphy.com/media/cOSp689PAhHUI/giphy.gif)
<!-- ![10% 10%](./img/kubernetes-logo.svg) -->

## A Microservice Oriented Guide

#### Tim Britton

---
# What is Microservice Architecture
- collection of loosely coupled applications that work together to create a single application.
- Applications are optimized to do one thing and do it well
- Applications should be the single source of truth for their concept.
---
# Microservice Architecture Tradeoffs
- Observability
- Tracing
- Fault Tolerance
- Deployment/Operational Complexity
- Cognitive Load
---
# What does help kubernetes solve

|Solved| Solved*| GL|
|:---|:---|:---|
|Observability|Tracing|Cognitive Load|
|Fault Tolerance|Deployment Complexity||

#### _* Some things are solved via kubernetes ecosystem extensions._
---

## How does k8s help solve these problems
### Covering
- Operational Complexity
- Fault Tolerance
- Observability 
### Not Covering:
- Tracing
- Cognitive Load
---
# Operational Complexity
- _Operational Complexity is the trade off for Application Simplicity_

#### Anatomy of a Deployment:
- Configuration
- Dependencies
- Access
---
# Configuration
- Environmental Variable, Configuration files
- Secrets management
- app resource requirements
  - ram
  - cpu shares
---
# Dependencies
- Database access?
- Other microservice access?
    - Service discovery?
---
# Access
- Exposing the application to internet
- Letting other applications in the mesh access it
---
### Brief overview K8s components
![bg left:30% 80%](./img/kubernetes-logo.svg)
- Pods
- Services
- Ingress
- Jobs
- ConfigMap
---
### Pod: The smallest unit of measurement
- A pod is a wrapper around a container or a group of containers
- Each pod has a QoS associated to it that k8s will use to schedule the pod
- A pod has labels which is utilized to manage and manipulate the containers associated with the pod.
---
### Services:  A load balancer for k8s pods
- Based on Envoy by Lift
- Two Types:
  - LoadBalancer
      - Has an External IP address
      - Usually utilizes the underlying cloud infrastructure ie AWS, Azure
  - ClusterIP
    - Has a DNS name in the cluster associated with it
    - All pods should have access to it
---
### Ingress: Reverse Proxy handling
- Provides TLS termination
- Allows for routing based on Request URI to a given service
- Associated to one namespace
---
### Jobs:  Scheduled Single Fire Workloads
- Allows Scheduling via Cron syntax
- Can access anything with in the K8s service mesh
- Configurable to clean up after itself or stick around