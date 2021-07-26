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

There was a clear need to optimize the usage of the available infrastructure. As a result, the virtualization of the Operating System was introduced. This prompted the appearance of containers, which represent the bare minimum an application requires for a successful execution e.g. code, config files, and dependencies. By default, there is a better usage of available infrastructure.

Multiple VMs on a hypervisor are replaced by multiple containers running on a single host operating system. The processes in the containers are completely isolated but are able to access the OS filesystem, resources, and packages. The creation and execution of containers is delegated to a container management tool, such as Docker.

The appearance of containers is unlocked by OS-level virtualization and as a result, multiple applications can run on the same OS. By nature, containers are lightweight, as these encapsulate only the application code and essential dependencies. Consequently, there is a better usage of available infrastructure and a more efficient pathway to release a product to consumers

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
- Deployments & ReplicaSets - oversees a set of pods for the same application (requires for application management)
- Services & Ingress - ensures connectivity and reachability to pods (application reachability)
- Configmaps & Secrets - pass configuration to pods (application configuration)
- Namespaces - provides a logical separation between multiple applications and their resources (application context)
- Custom Resource Definition (CRD) - extends Kubernetes API to support custom resources

![image](https://user-images.githubusercontent.com/44070137/121587197-84b2fc80-ca02-11eb-9b80-bf06e168aced.png)
There are use cases where 2-3 containers run within the same pod, however, it is highly recommended to keep the 1:1 ratio between your pods and containers.
To deploy an application to a Kubernetes cluster, a Deployment resource is necessary. All the pods are placed on the cluster nodes. A note can host multiple pods for different applications. A Deployment contains the specifications that describe the desired state of the application. Also, the Deployment resource manages pods by using a ReplicaSet. A ReplicaSet resource ensures that the desired amount of replicas for an application are up and running at all times.

A Service resource provides an abstraction layer over a collection of pods running an application. A Service is allocated a cluster IP, that can be used to transfer the traffic to any available pods for an application. There are 3 widely used Service types:

- ClusterIP - exposes the service using an internal cluster IP. If no service type is specified, a ClusterIP service is created by default.
- NodePort - expose the service using a port exposed on all nodes in the cluster.
- LoadBalancer - exposes the service through a load balancer from a public cloud provider such as AWS, Azure, or GCP. This will allow the external traffic to reach the services within the cluster securely.

To enable the external user to access services within the cluster an Ingress resource is necessary. An Ingress exposes HTTP and HTTPS routes to services within the cluster, using a load balancer provisioned by a cloud provider. Additionally, an Ingress resource has a set of rules that are used to map HTTP(S) endpoints to services running in the cluster. To keep the Ingress rules and load balancer up-to-date an Ingress Controller is introduced.
For example, as shown in the image above, the customers will access the go-helloworld.com/hi HTTP route (1), which is managed by an Ingress (2). The Ingress Controller (3) examines the configured routes and directs the traffic to a LoadBalancer (4). And finally, the LoadBalancer directs the requests to the pods using a dedicated port (5).

![image](https://user-images.githubusercontent.com/44070137/121588824-5f26f280-ca04-11eb-99e3-4b9305f83f80.png)

- https://kubernetes.io/docs/concepts/workloads/pods/
- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
- https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/
- https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#strategy
- https://kubernetes.io/docs/concepts/services-networking/service/
- https://kubernetes.io/docs/concepts/services-networking/ingress/
- https://kubernetes.io/docs/concepts/configuration/configmap/
- https://kubernetes.io/docs/concepts/configuration/secret/
- https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/

Kubernetes is widely known for its support for imperative and declarative management techniques. The imperative approach enables the management of resources using kubectl commands directly on the live cluster. This technique is best suited for development stages only, as it presents a low entry-level bar to interact with the cluster.

On the other side, the declarative approach uses manifests stored locally to create and manage Kubertenest objects. This approach is recommended for production releases, as we can version control the state of the deployed resources. However, this technique presents a high learning curve, as an in-depth understanding of the YAML manifest structure is required. Additionally, using YAML manifests unlocks the possibility of configuring more advanced options, such as volume mounts, readiness and liveness probes, etc.

YAML Manifest structure
A YAML manifest consists of 4 obligatory sections:

apiversion - API version used to create a Kubernetes object
kind - object type to be created or configured
metadata - stores data that makes the object identifiable, such as its name, namespace, and labels
spec - defines the desired configuration state of the resource

- https://kubernetes.io/docs/tasks/manage-kubernetes-objects/imperative-command/
- https://kubernetes.io/docs/tasks/manage-kubernetes-objects/declarative-config/
- https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/
- https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/

Kubernetes provides methods to handle some of the low-level failures and ensure the application is healthy and accessible. Some of these resources are:

- ReplicaSets - to ensure that the desired amount of replicas is up and running at all times
- Liveness probes - to check if the pod is running, and restart it if it is in an errored state
- Readiness probes - ensure that traffic is routed to that pods that are ready to handle requests
- Services - to provide one entry point to all the available pods of an application

https://kubernetes.io/docs/reference/kubectl/cheatsheet/
- Dockerfile - set of instructions used to create a Docker image
- Docker image - a read-only template used to spin up a runnable instance of an application
- Docker registry - a central mechanism to store and distribute Docker images
- CRD - Custom Resource Definition provides the ability to extend Kubernetes API and create new resources
- Node - a physical or virtual server
- Cluster - a collection of distributed nodes that are used to manage and host workloads
- Master node - a node from the Kubernetes control plane, that has installed components to make global, cluster-level decisions
- Worker node - a node from the Kubernetes data plane, that has installed components to host workloads
- Bootstrap - the process of provisioning a Kubernetes cluster, by ensuring that each node has the necessary components to be fully operational
- Kubeconfig - a metadata file that grants a user access to a Kubernetes cluster
- Pod - smallest manageable uint within a cluster that provides the execution environment for an application
- ReplicaSet - a mechanism to ensure a number of pod replicas are up and running at all times
- Deployment - describe the desired state of the application to be deployed
- Service - an abstraction layer over a collection of pods running an application
- Ingress - a mechanism to manage the access from external users and workloads to the services within the cluster
- Configmap - a resource to store non-confidential data in key-value pairs.
- Secret - a resource to store confidential data in key-value pairs. These are base64 encoded.
- Namespace - a logical separation between multiple applications and associated resources.
- Imperative configuration - resource management technique, that operates and interacts directly with the live objects within the cluster.
- Declarative configuration - resource management technique, that operates and manages resources using YAML manifests stored locally.

Cloud Foundry - Cloud Foundry is an open-source PaaS, a stand-alone software package that can be installed on any available infrastructure; private, public, or hybrid cloud. Due to its open-source nature, there is no vendor lock-in and the community can contribute to its future releases and definition of the roadmap. As such, Cloud Foundry offers a production-grade release process through a solid developer experience, that enables any application to be deployed with ease.
Note: some offerings of Cloud Foundry, can be deployed on top of Kubernetes, meaning that its main components are running as pods within a cluster.
Cloud Foundry consists of multiple components that provide these core capabilities:
- Routing - handle the incoming external traffic and route it to applications
- Authentication - identity management to user accounts
- Application lifecycle - controls the application deployments, monitors their status, and reconciles any new changes to reach the desired state of the application.
- Application storage and execution - handle the availability of artifacts to applications
- Service - use service brokers to provisions on-demand the dependency services for an application, such as a database or third-party APIs
- Messaging - ensure the communication between Cloud Foundry components
- Metrics and logging - aggregates the system and application metrics and logs
- https://docs.cloudfoundry.org/concepts/overview.html
- https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html
- https://www.suse.com/c/moving-a-cloud-foundry-hello-world-app-to-kubernetes-src/
It is pivotal to understand the application functionalities and available resources. This is especially the case when a microservice-based design is chosen, and solutions suck as IaaS (Infrastructure as a Service), PaaS (Platform as a Service), SaaS (Software as a Service) are available from a multitude of vendors. Choosing the most suitable deployment tooling will lead to the efficient delivery of the product.
Considering that the application code is available, these are the steps to adopt each proposed solution:
Kubernetes:
- create an OCI (Open Container Initiative) compliant image, usually created by using Docker
- deploy a Kubernetes cluster with a valid ingress controller for the routing of requests
- deploy an observability stack, including logs and metrics
- create the YAML manifests for the application deployment
- create a CI/CD pipeline to push the Kubernetes resources to the cluster
Cloud Foundry:
- write a manifest file to provide main application deployment parameters
- deploy Cloud Foundry or use Cloud Foundry PaaS solutions from 3rd part vendors
- deploy the application to Cloud Foundry (via CLI or UI)
- Note: Cloud Foundry will create the OCI compliant image by default, and it will provide the routing capacities as well.
- Cloud Foundry provides a better developer experience for application deployment, as it offers a greater level of component abstraction (no need to manage the underlying infrastructure). However, a PaaS solution locks-in the customer to a specific vendor. On the other side, Kubernetes offers full control over the container orchestration, providing more flexible management of the application.

FaaS: https://www.redhat.com/en/topics/cloud-native-apps/what-is-faas?source=searchresultlisting

CI/CD -
![image](https://user-images.githubusercontent.com/44070137/124809582-43910800-df2e-11eb-8044-677fcf5dc9c8.png)


- Build - compile the application source code and its dependencies. If this stage fails the developer should address it immediately as there might be missing dependencies or errors in the code.
- Test - run a suite of tests, such as unit testing, integration, UI, smoke, or security tests. These tests aim to validate the behavior of the code. If this stage fails, then developers must correct it to prevent dysfunctional code from reaching the end-users.
- Package - create an executable that contains the latest code and its dependencies. This is a runnable instance of the application that can be deployed to end-users.
- Deploy - push the packaged application to one or more environments, such as sandbox, staging, and production. Usually, the sandbox and staging deployments are automatic, and the production deployment requires engineering validation and triggering.

Important links (github) -
- https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions
- https://docs.github.com/en/actions/learn-github-actions/introduction-to-github-actions#create-an-example-workflow
- https://github.com/marketplace?type=actions

## Configuration Manager 

Helps in managing and scaling manifest files. A CI/CD pipeline is essential to automate and standardize the application release process. New changes are propagated through multiple environments, including the production cluster, and ensure that the consumers can use the latest features. In an ideal situation, all clusters are similarly configured, such that the engineering team can inspect a realistic simulation of a production deployment. This implies that a set of nearly similar manifests are required for each cluster, sandbox, staging, and production. To reduce the management overhead of overseeing a similar suite configuration for each cluster, templating is necessary.

## Push-based model
![image](https://user-images.githubusercontent.com/44070137/126387010-717deeec-87d9-4b18-ad44-398fc0824792.png)
In a push-based model, as shown in the image below, the developer commits new code to the Git repository (1), which triggers the Continuous Integration stages (2). The code is packaged and distributed using an image registry, such as DockerHub (3). The Continuous Delivery stage is triggered once the YAML manifests are updated to reference the new image tag (4). A Continuous Delivery tool then pushed the updated manifests to multiple clusters (5).This model is fully operational and many tools within the ecosystem offer this deployment approach, e.g. Jenkins and CircleCI. However, there is one downside to this model: changes should be actively propagated to all environments. If this is not fulfilled, a scenario might be reached where multiple changes need to be deployed to production, which increases the failure rate and complicated the recovery procedures. Hence, wide awareness is required of features pushed to a production environment.

## Pull-based model
In a pull-based CI/CD approach, the release process is still be triggered by a developer that pushed new features to the source code (1). The package (2) of the application is similar, resulting in a new image stored in DockerHub (3). However, once the YAML manifests are updated with the new image tag, a pull-based Continuous Delivery tool identifies new changes (4) and applies them to a Kubernetes cluster (5). As a result, this simplifies the process of application release, as new features can be applied automatically as soon as they are available. 
![image](https://user-images.githubusercontent.com/44070137/126387702-306f33ab-7531-4a1e-9f24-65efe9cade5c.png)



