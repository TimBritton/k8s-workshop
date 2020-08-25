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

