# Bootstrap k8s


* What is Kubernetes?

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, management, and orchestration of containerized applications. It provides a framework for automating the deployment, scaling, and management of containerized applications. Kubernetes is designed to be highly extensible and can be used to manage containerized workloads and services efficiently.

* Why is Kubernetes?

Kubernetes was developed to solve the problem of efficiently managing containerized applications at scale. It addresses the challenges of deploying, scaling, and maintaining containerized applications, making it easier to manage complex, distributed systems. Kubernetes simplifies the management of containers, optimizes resource utilization, and provides a consistent and declarative approach to application deployment and scaling.

* What is a cluster?

In the context of Kubernetes, a cluster is a collection of nodes (physical or virtual machines) that work together to run containerized applications. Clusters consist of a control plane (which manages the cluster) and worker nodes (where containers run). The control plane manages the scheduling, scaling, and monitoring of applications, while the worker nodes host the containers.

* What is a node?

A node, in the context of Kubernetes, is a worker machine within a cluster. It is responsible for running containers and managing their runtime environment. Each node has the necessary services and tools installed for running Kubernetes, including a container runtime (like Docker or containerd), kubelet (a component that communicates with the control plane), and other essential services.

* What is a pod?

A pod is the smallest deployable unit in Kubernetes. It represents a single instance of a running process in a cluster, which may contain one or more containers. Containers within the same pod share the same network namespace and can communicate with each other easily. Pods are used to encapsulate and deploy one or more closely related containers together on the same node.

* In what way(s) are Kubernetes and Docker related?

Kubernetes and Docker are related but serve different purposes. Docker is a platform for developing, shipping, and running applications in containers. Kubernetes, on the other hand, is an orchestration platform for automating the deployment, scaling, and management of containerized applications. While Kubernetes can work with various container runtimes, including Docker, it can also work with containerd, CRI-O, and others. In recent versions, Docker has shifted its focus from orchestration to just being a container runtime, and Kubernetes has become the dominant choice for container orchestration.

* What is a Kubernetes namespace?

A Kubernetes namespace is a virtual, logical partition within a cluster that allows you to divide cluster resources into multiple, isolated groups. Namespaces are used to organize and segregate resources like pods, services, and replication controllers. They are often used to provide multi-tenancy support, allowing different teams or applications to run in the same cluster without interfering with each other. Namespaces provide a way to scope and manage resources within a Kubernetes cluster.

### Step 1:

* Listing existing pods in the cluster:
```
kubectl get pods
```
* Printing more details about the pod:
```
kubectl describe pod <pod-name>
```
* Fetching and following the pod container’s logs.
```
kubectl logs -f <pod-name> -c <container-name>
```
* Executing the ‘date’ command inside the running container:
```
kubectl exec -it <pod-name> -c <container-name> -- date
```
* Deleting the pod:
```
kubectl delete pod <pod-name>
```

### Step 2:

Make sure to do the following:

```
> kubectl config current-context
> kubectl config use-context minikube
> kubectl apply -f <pod name>
> kubectl exec <pod name> -- printenv
```

### Step 3:

Add the following to verify the container connection
```
> kubectl port-forward [pod-name] 8080:8080

On another terminal bash:

> curl localhost:8080/
```

### Step 4:

```
kubectl describe service [service-name] | grep Endpoints
kubectl exec -it hello-world -c hello-world -- ping hello-world.default.svc.cluster.local
```

### Step 5:

```
> kubectl port-forward <pod-name> 8080:8080
> kubectl scale deployment hello-world-deployment --replicas=3
> kubectl rollout undo deployment/hello-world-deployment --to-revision=1
```