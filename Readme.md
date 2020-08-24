# Workshop Itinerary 

## Session 1: Kubernetes Overview  
  1. Part 1. Background overview of kubernetes  
    * Covers Docker, Docker Compose, Kubernetes  
    * Covers the basic concepts at the infrastrure level
      * Node pools etc
  2. Part 2. Kubernetes Concepts  
    * Pods  
    * Services  
    * Ingress  
    * Advanced configurations:  
      * Daemon Sets  
      * Jobs  
    * Not Covered:  
      * custom resource definitions  
      * role based access  
  3. Part 3. Deployments as Code  
    * Examples:
      * Deployment of pod
      * Deployment of services
      * Deployment of ingress

## Session 2: Live Coding 

The live coding sesison I plan to build a simple rest api and deploy it to kubernetes.  Make a couple changes and reploy the servce.


Goals: 
  * Build a simple rest api
  * Deploy rest api
    * deployment
    * service
    * demonstrate port-forwarding
  * Add ingress rule
   * show access from the internet
  * Make a change to the application 
    * Redeploy application 
    * verify application
  * Explain the kubectl cli
​
## Session 3: On-hands 
Prove template repositories some of which will have kubernetes configurations and some that do not.
​
Each person will be able to to deploy the existing applications with kubernetes config and then they can apply what they learned from session two to deploy the services that are not configured to their local kubernetes
​
If I have time I will set up a kubernetes instance that has a domain associated to it to allow people to mess with ingress rules as well.
​
## Session 4: Kubernetes Ecosystem
This session will go over a couple tools from the kubernetes ecosystem.
​
* Helm
  * The kubernetes "package manager"
  * Allows you to build kubernetes configurations that focuses on reproducability of the deployments.
​
* Istio
  * A control plan for kubernetes
  * Allows for side carts that provide in service mesh tls *tls everywhere*
  * Allows for canary deployments!!
    * (My favorite feature)
​
* Cloud Native foundation
  * Talk about the work still being done to expand on kubernetes
  * [https://landscape.cncf.io/](https://landscape.cncf.io/)
​
* Q/A wrap up.
Collapse




