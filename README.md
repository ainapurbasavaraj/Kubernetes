# Kubernetes

**What is Kubernetes?**
Kubernetes, or k8s for short, is a system for automating application deployment. Modern applications are dispersed across clouds, virtual machines, and servers. Administering apps manually is no longer a viable option.

K8s transforms virtual and physical machines into a unified API surface. A developer can then use the Kubernetes API to deploy, scale, and manage containerized applications.

Its architecture also provides a flexible framework for distributed systems. K8s automatically orchestrates scaling and failovers for your applications and provides deployment patterns.

It helps manage containers that run the applications and ensures there is no downtime in a production environment. For example, if a container goes down, another container automatically takes its place without the end-user ever noticing.

Kubernetes is not only an orchestration system. It is a set of independent, interconnected control processes. Its role is to continuously work on the current state and move the processes in the desired direction.

Check out our article on What is Kubernetes if you want to learn more about container orchestration.

**Kubernetes Architecture and Components**
Kubernetes has a decentralized architecture that does not handle tasks sequentially. It functions based on a declarative model and implements the concept of a ‘desired state.’ These steps illustrate the basic Kubernetes process:

An administrator creates and places the desired state of an application into a manifest file.
The file is provided to the Kubernetes API Server using a CLI or UI. Kubernetes’ default command-line tool is called kubectl.
Kubernetes stores the file (an application’s desired state) in a database called the Key-Value Store (etcd).
Kubernetes then implements the desired state on all the relevant applications within the cluster.
Kubernetes continuously monitors the elements of the cluster to make sure the current state of the application does not vary from the desired state.

![image](https://user-images.githubusercontent.com/46313049/173172996-82638b76-61d8-4bd8-b201-3e220ad5a577.png)

**What is Master Node in Kubernetes Architecture?**
The Kubernetes Master (Master Node) receives input from a CLI (Command-Line Interface) or UI (User Interface) via an API. These are the commands you provide to Kubernetes.

You define pods, replica sets, and services that you want Kubernetes to maintain. For example, which container image to use, which ports to expose, and how many pod replicas to run.

You also provide the parameters of the desired state for the application(s) running in that cluster.

![image](https://user-images.githubusercontent.com/46313049/173173033-0345156e-03e9-4baf-bac0-422efcc0e5cf.png)

**API Server**
The API Server is the front-end of the control plane and the only component in the control plane that we interact with directly. Internal system components, as well as external user components, all communicate via the same API.

**Key-Value Store (etcd)**
The Key-Value Store, also called etcd, is a database Kubernetes uses to back-up all cluster data. It stores the entire configuration and state of the cluster. The Master node queries etcd to retrieve parameters for the state of the nodes, pods, and containers.

**Controller**
The role of the Controller is to obtain the desired state from the API Server. It checks the current state of the nodes it is tasked to control, and determines if there are any differences, and resolves them, if any.

**Scheduler**
A Scheduler watches for new requests coming from the API Server and assigns them to healthy nodes. It ranks the quality of the nodes and deploys pods to the best-suited node. If there are no suitable nodes, the pods are put in a pending state until such a node appears.

**What is Worker Node in Kubernetes Architecture?**
Worker nodes listen to the API Server for new work assignments; they execute the work assignments and then report the results back to the Kubernetes Master node.

![image](https://user-images.githubusercontent.com/46313049/173173082-eedde548-ffda-41af-aa71-f0c613d74f46.png)


**Kubelet**
The kubelet runs on every node in the cluster. It is the principal Kubernetes agent. By installing kubelet, the node’s CPU, RAM, and storage become part of the broader cluster. It watches for tasks sent from the API Server, executes the task, and reports back to the Master. It also monitors pods and reports back to the control panel if a pod is not fully functional. Based on that information, the Master can then decide how to allocate tasks and resources to reach the desired state.

**Container Runtime**
The container runtime pulls images from a container image registry and starts and stops containers. A 3rd party software or plugin, such as Docker, usually performs this function.

**Kube-proxy**
The kube-proxy makes sure that each node gets its IP address, implements local iptables and rules to handle routing and traffic load-balancing.

**Pod**
A pod is the smallest element of scheduling in Kubernetes. Without it, a container cannot be part of a cluster. If you need to scale your app, you can only do so by adding or removing pods.

The pod serves as a ‘wrapper’ for a single container with the application code. Based on the availability of resources, the Master schedules the pod on a specific node and coordinates with the container runtime to launch the container.
