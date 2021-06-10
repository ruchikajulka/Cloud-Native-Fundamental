# Cloud-Native-Fundamental
## Lesson 1 Notes -
Cloud-native refers to the set of practices that empowers an organization to build and manage applications at scale. They can achieve this goal by using private, hybrid, or public cloud providers. In addition to scale, an organization needs to be agile in integrating customer feedback and adapting to the surrounding technology ecosystem.

Containers are closely associated with cloud-native terminology. Containers are used to run a single application with all required dependencies. The main characteristics of containers are easy to manage, deploy, and fast to recover. As such, often, a microservice-based architecture is chosen in tandem with cloud-native tooling. Microservices are used to manage and configure a collection of small, independent services that can be easily packaged and executed within a container.

Kubernetes had its first initial release in 2014 and it derives from Borg, a Google open-source container orchestrator. Currently, Kubernetes is part of CNCF or Cloud Native Computing Foundation. CNCF was founded in 2015, and it provides a vendor-neutral home to open-source projects such as Kubernetes, Prometheus, ETCD, Envoy, and many more.

From a business perspective, the adoption of cloud-native tooling represents:

Agility - perform strategic transformations
Growth - quickly iterate on customer feedback
Service availability - ensures the product is available to customers 24/7
From a technical perspective, the adoption of cloud-native tooling represents:

Automation - release a service without human intervention
Orchestration - introduce a container orchestrator to manage thousands of services with minimal effort
Observability - ability to independently troubleshoot and debug each component

## Lesson 2 Notes - 

- About Monolith and Microservices 
   - https://nordicapis.com/whats-the-difference-between-monolith-and-microservices/
   - https://www.mulesoft.com/resources/api/microservices-vs-monolithic
    
- About Logging and Health Checks - 
    - https://logz.io/blog/logging-best-practices/
    - https://microservices.io/patterns/observability/health-check-api.html
    - https://prometheus.io/docs/instrumenting/writing_exporters/#metrics
    - https://www.tutorialspoint.com/log4j/log4j_logging_levels.htm
    - https://containerjournal.com/topics/container-ecosystems/enabling-distributed-tracing-for-microservices-with-jaeger-in-kubernetes/
    - https://www.youtube.com/watch?v=t7iVCIYQbgk

## Lesson 3 Notes -
a VM is composed of an operating system (OS) with a set of pre-installed libraries and packages. During execution, an application utilizes an OS filesystem, resources, and packages.

A set of VMs is managed through a hypervisor. A hypervisor provides the virtualization of the infrastructure which is composed of physical servers. As a result, a hypervisor is capable of creating, configuring, and managing multiple VMs on the available servers. For example, we are able to running applications A, B, and C on 3 separate VMs.

The utilization of VMs introduced standardization in infrastructure provisioning, in association with efficient use of available infrastructure. Instead of running an application per server, a hypervisor enables multiple VMs to run at the same time to host multiple applications. However, there is one downside to this mechanism: it is not efficient enough. For example, applications A, B, and C uses the same Operating System. Replicating an OS consumes a lot of resources, and the more applications we run the more space we allocate to the replication of the operating systems alone.

![image](https://user-images.githubusercontent.com/44070137/121231347-4c72b900-c85e-11eb-9bbc-e3b64539eda1.png)

A Dockerfile is a set of instructions used to create a Docker image. Each instruction is an operation used to package the application, such as installing dependencies, compile the code, or impersonate a specific user. A Docker image is composed of multiple layers, and each layer is represented by an instruction in the Dockerfile. All layers are cached and if an instruction is modified, then during the build process only the changed layer will be rebuild. As a result, building a Docker image using a Dockerfile is a lightweight and quick process.
- https://docs.docker.com/engine/reference/builder/#from
- https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

Once a Dockerfile is constructed, these instructions are used to build a Docker image. A Docker image is a read-only template that enables the creation of a runnable instance of an application. In a nutshell, a Docker image provides the execution environment for an application, including any essential code, config files, and dependencies.

- https://docs.docker.com/engine/reference/commandline/build/
- https://docs.docker.com/engine/reference/commandline/run/

The image needs to be pushed to a public Docker image registry, such as DockerHub, Harbor, Google Container Registry, etc. for other engineers on the team to access it.

- https://docs.docker.com/registry/introduction/
- https://docs.docker.com/engine/reference/commandline/tag/
- https://docs.docker.com/engine/reference/commandline/push/
- https://www.docker.com/blog/demystifying-open-container-initiative-oci-specifications/
- https://buildpacks.io/docs/app-journey/

### Kubernetes
A container orchestrator framework is capable to create, manage, configure thousands of containers on a set of distributed servers while preserving the connectivity and reachability of these containers. Kubernetes currently is a graduated CNCF project, which highlights its maturity and reported success from end-user companies. 
Portability
Kubernetes is a highly portable tool. This is due to its open-source nature and vendor agnosticism. As such, Kubernetes can be hosted on any available infrastructure, including public, private, and hybrid cloud.

Scalability
Building for scale is a cornerstone of any modern infrastructure, enabling an application to scale based on the amount of incoming traffic. Kubernetes has in-build resources, such as HPA (Horizontal Pod Autoscaler), to determine the required amount of replicas for a service. Elasticity is a core feature that is highly automated within Kubernetes.

Resilience
Failure is expected on any platform. However, it is more important to be able to recover from failure fast and build a set of playbooks that minimizes the downtime of an application. Kubernetes uses functionalities like ReplicaSet, readiness, and liveness probes to handle most of the container failures, which enables powerful self-healing capability.

Service Discovery
Service discovery encapsulates the ability to automatically identify and reach new services once these are available. Kubernetes provide cluster level DNS (or Domain Name System), which simplifies the accessibility of workloads within the cluster. Additionally, Kubernetes provides routing and load balancing of incoming traffic, ensuring that all requests are served without application overload.

Extensibility
Kubernetes is a highly extensible mechanism that uses the building-block principle. It has a set of basic resources that can be easily adjusted. Additionally, it provides a rich API interface, that can be extended to accommodate new resources or CRDs (Custom Resource Definitions).

Operational Cost
Operational cost refers to the efficiency of resource consumption within a Kubernetes cluster, such as CPU and memory. Kubernetes has a powerful scheduling mechanism that places an application on the node with sufficient resources to ensure the successful execution of the service. As a result, most of the available infrastructure resources are allocated on-demand. Additionally, it is possible to automatically scale the size of the cluster based on the current incoming traffic. This capability is provisioned by the cluster-autoscaler, which guarantees that the cluster size is directly proportional to the traffic that it needs to handle.

![image](https://user-images.githubusercontent.com/44070137/121583898-da85a580-c9fe-11eb-8bd9-c0c9fdb16d16.png)

A Kubernetes cluster is composed of a collection of distributed physical or virtual servers. These are called nodes. Nodes are categorized into 2 main types: master and worker nodes. The components installed on a node, determine the functionality of a node, and identifies it as a master or worker node.
The suite of master nodes, represents the control plane, while the collection of worker nodes constructs the data plane.

![image](https://user-images.githubusercontent.com/44070137/121584003-f8530a80-c9fe-11eb-9dda-37839c42b53f.png)

The control plane consists of components that make global decisions about the cluster. These components are the:

kube-apiserver - the nucleus of the cluster that exposes the Kubernetes API, and handles and triggers any operations within the cluster
kube-scheduler - the mechanism that places the new workloads on a node with sufficient satisfactory resource requirements
kube-controller-manager - the component that handles controller processes. It ensures that the desired configuration is propagated to resources
etcd - the key-value store, used for backs-up and keeping manifests for the entire cluster
There are two additional components on the control plane, they are kubelet and k-proxy. These two are special and important as they are installed on all node. You can see the Data Plane below for more details.

![image](https://user-images.githubusercontent.com/44070137/121584070-0acd4400-c9ff-11eb-945e-5dee1e3f3b39.png)

The data plane consists of the compute used to host workloads. The components installed on a worker node are the:

kubelet - the agent that runs on every node and notifies the kube- apiserver that this node is part of the cluster
kube-proxy - a network proxy that ensures the reachability and accessibility of workloads places on this specific node
Important Note: The kubelet and kube-proxy components are installed on all the nodes in the cluster (master and worker nodes). These components keep the kube-apiserver up-to-date with a list of nodes in the cluster and manages the connectivity and reachability of the workloads.

New terms
CRD - Custom Resource Definition provides the ability to extend Kubernetes API and create new resources
Node - a physical or virtual server
Cluster - a collection of distributed nodes that are used to manage and host workloads
Master node - a node from the Kubernetes control plane, that has installed components to make global, cluster-level decisions
Worker node - a node from the Kubernetes data plane, that has installed components to host workloads.

- https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/
- https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/
- https://kubernetes.io/blog/2016/07/autoscaling-in-kubernetes/
- https://kubernetes.io/docs/concepts/overview/components/

Provisioning a Kubernetes cluster is known as the bootstrapping process. (https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/).
To access a Kubernetes cluster a kubeconfig file is required. A kubeconfig file has all the necessary cluster metadata and authentication details, that grants the user permission to query the cluster objects. A Kubeconfig file has 3 main distinct sections:
- Cluster - encapsulates the metadata for a cluster, such as the name of the cluster, API server endpoint, and certificate authority used to check the identity of the user.
- User - contains the user details that want access to the cluster, including the user name, and any authentication metadata, such as username, password, token or client, and key certificates.
- Context - links a user to a cluster. If the user credentials are valid and the cluster is up, access to resources is granted. Also, a current-context can be specified, which instructs which context (cluster and user) should be used to query the cluster.
- https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/

Kubernetes provides a rich collection of resources that are used to deploy, configure, and manage an application. Some of the widely used resources are:

- Pods - the atomic element within a cluster to manage an application
- Deployments & ReplicaSets - oversees a set of pods for the same application
- Services & Ingress - ensures connectivity and reachability to pods
- Configmaps & Secrets - pass configuration to pods
- Namespaces - provides a logical separation between multiple applications and their resources
- Custom Resource Definition (CRD) - extends Kubernetes API to support custom resources

![image](https://user-images.githubusercontent.com/44070137/121587197-84b2fc80-ca02-11eb-9b80-bf06e168aced.png)
There are use cases where 2-3 containers run within the same pod, however, it is highly recommended to keep the 1:1 ratio between your pods and containers.
To deploy an application to a Kubernetes cluster, a Deployment resource is necessary. All the pods are placed on the cluster nodes. A note can host multiple pods for different applications. A Deployment contains the specifications that describe the desired state of the application. Also, the Deployment resource manages pods by using a ReplicaSet. A ReplicaSet resource ensures that the desired amount of replicas for an application are up and running at all times.
![image](https://user-images.githubusercontent.com/44070137/121587780-29cdd500-ca03-11eb-9375-3e997b4889ab.png)

- https://kubernetes.io/docs/concepts/workloads/pods/
- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
- https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy

