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
  - cpu
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
---
