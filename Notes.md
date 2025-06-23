# 1. Kubernetes Primer
# 2. kubernetes principles of operation
# 3. Getting kubernetes
# 4. Working with pods
# 5. Virtual clusters with namesapces
# 6. kubernetes deployments
# 7. kubernetes services
# 8. ingress
# 9. wasm on kubernetes
# 10. Service Discovery deep dive
# 11. kubernetes storage
# 12. Configmaps and secrets
# 13. statefulsets
# 14. API Security and RBAC
# 15. Kubernetes API
# 16. Threat Modeling kubernetes
# 17. Real-world kubernetes security
<br>













</br>



## 1. Kubernetes Primer

**Important Kubernetes background**

- kubernetes is an orchestrator of containerized cloud-native microservices applications or
`Kubernetes deploys, scales, self-heals, and updates applications where individual application features are packaged and deployed as containers.`
- It’s open-sourced under the Apache 2.0 license and is owned and managed by the Cloud Native Computing Foundation (CNCF).
     ORCHESTRATION :
```
- An orchestrator is a system that deploys applications and dynamically responds  to changes. For ex, kubernetes can :
  1. Deploy Applications
  2. Scale them up and down based on demand
  3. Perform rollouts and rollbacks
 and a lot....
```
  CONTAINERIZATION :
```
- It is the process of packaging applications and dependencies as images and then running them as containers
```
  CLOUD-NATIVE :
```
- cloud-native applications posses cloud-like features such as auto-scaling, self-healing, automated-updates, rollbacks and more.

Simply🤭running a regular applications in the public cloud doesnot make it cloud-native
```
  MICROSERVICES :
```
- Microservices applications are built from many small, specialized, In-dependent parts that work together to form a useful application.
```

where did kubernetes come from ?🤔
- kubernetes was developed by a group of google engineers partly in response to AWS and Docker.
    - AWS changed the world when it invented modern cloud computing, and the rest of the industry needed to catch up. one of the companies catching up was google, they'd build their own cloud but needed a way to abstract the value of AWS and make it easy as possible for customers to get off AWS and onto their cloud.
     - At the sametime, Docker was taking the world by storm, and users needed help managing explosive container growth.
 
  This led a group of google engineers to take the lessons they'd learned using their Internal container management tools and create a new tool called `kubernetes`

👉 Two biggest reasons kubernetes is important to the industry is :
1. It abstracts Infrastructure (Such as AWS) and 2. It simplifies applications portability

**Kubernetes and Docker **

- All the early version of kubernetes shipped with docker as its container-runtime. Meaning kubernetes used Docker for low-level tasks such as creating, starting, and stopping containers. However, Two things happened :
  1. Docker got bloated [Excessive in size or amount ]
  2. People created lots of docker alternatives
 
As a result, K8s project created the container runtime interface (CRI) to make the runtime layer pluggable. This means now you can pick and choose the best runtimes for your needs.  For ex: some runtimes provide better isolations, some provide better performance, some work with wasm containers, and more

- K8s 1.24 finally removed support for `Docker as a runtime` as it was bloated and overkill for what kubernetes needed. Since then, most new kubernetes clusters ship with **cotnainerd** as the default runtime. Fortunately, containerd is a stripped-down version of docker optimized for kubernetes, that fully supports applications containerized by docker. In fact, Docker, containerd, and kubernetes all work with images and containers that implement the **open container initiative (OCI)** standards.

- In 2016, 2017 Docker swarm, Mesosphere DCOS, and kubernetes competed to become the industry standard conatiner orchestrator. Kubernetes won. However, Docker swarm is still being developed and is still used by small companies needing a simple alternative to kubernetes

**kubernetes - what's in the name ** 

- The word Kubernetes originates from the Greek word for **helmsman** which is the person who steers a ship. You can see this in the logo, which is a ship’s wheel.
- Some of the original engineers wanted to call kubernetes seven of nine. Because, kubernetes got inspiration from google's borg project and borg project got it's name from famous borg drone from TV series "Start Trek Voyager " is called seven of  nine. Copy right laws didn't allow this, so they gave the logo seven spokes as a subtle reference to seven of nine.
- You'll often see it shortened to k8s and pronounced as "kates". The number 8 replaces the eight characters between "K" and "S"

**Kubernetes : The operating system of the cloud**

- kubernetes is the de facto platform for cloud-native applications, and we sometimes call it the **operating system (OS) of the cloud**. This because it abstracts the differences between cloud platforms the same way that operating systems like linux and windows abstract the differences between servers :
   - linux and windows abstract server resources and schedule application processes
   - Kubernetes abstracts cloud resources and schedules application microservices

As a quick example, you can schedule applications on kubernetes with-out caring if they're running on AWS, Azure, Civo Cloud, GCP or your on-premises datacenter. This makes kubernetes a key enabler for :
- Hybrid Cloud
- Multi-cloud
- Cloud migrations

**Application Scheduling :**
- one of the main things an OS does is simplify the scheduling of work tasks.
    For ex: computers are complex collection of hardware resources such as cpu, memory, storage and networking. Thankfully modern operating systems hide most of this, making the world of application development a far friendlier place. For ex, how many developers need to care which CPU cor, memory DIMM, or flash chip their code uses ? Most of the time,  we let the OS decide.

  kubernetes does a simmilar thing with clouds and data centers.

  At high level, a cloud or data center is complex collection of resources and services. Kubernetes abstracts most of this, making the resources easier to consume. Again, how often do you care which compute node, which failure zone, or which storage volume your app uses ? Most of the time, you'll be happy to let kubernetes decide.
  


## 2. kubernetes principles of operation

**kubernetes from 40K feet**
- kubernetes is both cluster and an orchestrator .

**kubernetes : cluster **
- kubernetes is one or more nodes providing CPU, Memory and other resources for application use.

kubernetes supports two node types:
1. control plane nodes (system services)
2. Worker nodes (user apps)

- Both types can be physical servers, virtual machines, or cloud instances, and both can run on ARM and AMD64/x86-84. Control plane nodes must be linux, but worker nodes can be linux or windows.

- control plane nodes implement the kubernetes intelligence, and every cluster needs at least one. However, you should have three or five for high availability (HA)
- Every control plane node runs every control plane service. These include  the API Server, the scheduler, and the controller that implement cloud-native features such as self-healing, autoscaling and rollouts.
- Worker nodes are where you run your business applications

**kubernetes : Orchestrator**

- orchestrator is the jargon for a system that deploys and manages applications.
- Kubernetes is the industry-standard orchestrator and can intelligently deploy applications across nodes and failure zones for optimal performance and availability. It can also fix things when they break, scale things when demand changes, and manage rollouts and rollbacks.

**control plane and worker nodes**
- a kubernetes cluster is one or more control plane nodes and worker nodes.
- Almost all cloud-native apps are linux apps and require linux worker nodes. However, you'll need one or more windows worker nodes if you have cloud-native windows apps. Fortunately, a single kubernetes cluster can have a mix of linux and windows worker nodes, and kubernetes is intelligent enough to schedule apps to the correct nodes.

- The control plane is a collection of system  services that implement brains of kubernetes. It exposes the API, scheduled apps, implements self-healing, manages scaling operations, and more.
- The simplest clusters run a single control plane node and are best suited for labs and testing. For production clusters, you should run three or five control plane nodes and spread them across availability zones for high availability

Most clusters run every control plane service 

**Control plane nodes and worker nodes**

**packaging apps for kubernetes**

**The declarative model and desired state**

**Pods**

**Deployments**

**Services**

## 3. Getting kubernetes
## 4. Working with pods
## 5. Virtual clusters with namesapces
## 6. kubernetes deployments
## 7. kubernetes services
## 8. ingress
## 9. wasm on kubernetes
## 10. Service Discovery deep dive
## 11. kubernetes storage
## 12. Configmaps and secrets
## 13. statefulsets
## 14. API Security and RBAC
## 15. Kubernetes API
## 16. Threat Modeling kubernetes
## 17. Real-world kubernetes security
