# 1. A Journey through Kubernetes

In order to talk about kubernetes in the right context we need to talk about why kubernetes exists and what problems it solves.

Kubernetes is broadly defined as a container orchestrator but what is the purpose of a container orchestrator?  Container orchestrator came from the need to manage fleets of containers due to a shift in architecture to an architectural pattern called Microservice Architecture.

# 2. What is Microservice Architecture
Microservice Architecture can be summed up as a collection of loosely coupled applications that work together to create a single application. 

The goal of this architecture is to build these services that are optimized to do their one job very well and isolate that one job to that service exposing it via some sort of API.

Which is great because you keep all the logic within that one service and that service becomes the single source of truth right?  

The answer is yes, but.  

The but being that there are trade offs.  Some of these trade offs can be handled with tools like kubernetes but others are tradeoffs that can be challenging to overcome.

Trade offs:
- Observability - When you have 100+ services running how do you know how its performing
- Tracing - When an operation communicates with many other services how do we identify the cause of an issue
- Cognitive Load - The more services you have the harder it is for a single person to understand the whole picture
- Fault Tolerance - What happens when a single service goes down?  How does your application handle it.
- Deployment Complexity - when a service communicates with many other services a botched deployment can cause an outage

__There are other trade offs I am not listing__


# 3. What does help kubernetes solve

|Solved| Solved*| GL|
|:---|:---|:---|
|Observability|Tracing|Cognitive Load|
|Fault Tolerance|Deployment Complexity||

* Distributed Tracing is solved via extensions to kubernetes but not by kubernetes itself.

* Deployment Complexity is solved by kubernetes but there are extensions to kubernetes that makes it even easier to handle.

_It should be stressed that kubernetes is not a silver bullet but it is a good tool for managing and orchestrating your fleet of microservices._

# 4. How does k8s help solve these problems

## Tackling Deployment Complexity

When utilizing a microservice architecture the operational complexity is the trade off for application simplicity.  We design our applications to do one thing and do that one thing very well.  But eventually you need to coordinate with other services to accomplish complex tasks.  

When deploying a microservice there are three main things that need to be understood:

1. What is the configuration required to deploy this application?
  * Environment variables, config files
  * Secrets management, (database passwords etc)

2. What does this microservice talk to?  
    * Databases, other services etc
    * service discovery

3. How is this application exposed to the internet or other services?
  * load balancing, exposing the application to the internet.

If you were to use a traditional tool chain you would have to either capture this information in a wiki or flat file somewhere or configure a series of applications to handle each of the cases.

Luckily enough K8s provides a way to handle each of these cases.

### Terminology Run Down

In order to understand how kubernetes helps solves these problems we need to run down the basic ideas about kubernetes.

#### Pod

The pod is the smallest unit of measurement in kuberetes.  A pod is 1 or more containers that work together to accomplish a goal.  

_Usually a pod is a single container.  In the case that its not a single container its usually a series of containers that share a given resource whether thats a disk or need to be on a shared machine.  This is an advanced topic._

#### Service

Services allow you to expose pods to the service mesh or to the internet as a whole.  A service is associated to any number of pods via the label selectors.

The service will allow provide an in service mesh dns name for applications to connect to.

#### Ingress

Ingress allows the user to route http/https traffic to a given service. 

#### Configmap

Configmaps allow configuration files or just configuration values to be persisted in the cluster.

#### Persistent Volumes

Persistent Storage space for containers that require it.

#### Namespace
Pods, Ingress definitions, and services are all associated to specific namespaces.  If you try to change a resource from a different namespace you need to specifically say what namespace you are working in.

### Bringing it together

In Kubernetes you deploy pods via Yaml files and the cli application called kubectl.  

The deployment yaml file defines:
- The name of the pod
- The configuration of the containers in that pod
- The resource constraints imposed on the pod

#### Example Deployment:
``` yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
spec:
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        resources:
          limits:
            memory: "100Mi"
            cpu: "100m"
        ports:
        - containerPort: 80
```

#### Example Service

``` yaml

apiVersion: v1
kind: Service
metadata:
  name: nginx # exposes this service as nginx.<namespace>
spec:
  selector:
    app: nginx
  type: LoadBalancer
  ports:
  - port: 8080
    targetPort: 80
```

#### Whats going on
- Deploys an nginx container that runs on port 80
- Deploys a service pointing to this container exposing it to the internet on port 8080


# 5. Miscellaneous 

<!-- #### Example Job
``` yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: pi
spec:
  template:
    spec:
      containers:
      - name: pi
        image: perl
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
      restartPolicy: Never
  backoffLimit: 4

``` -->

