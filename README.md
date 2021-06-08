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

