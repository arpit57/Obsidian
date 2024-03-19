
![[Pasted image 20240311234213.png]]


![[Pasted image 20240311234321.png]]
## Virtualization vs Dockeriation
## 1. Introduction[](https://www.baeldung.com/cs/virtualization-vs-containerization#introduction)

**Virtualization and containerization are the two most frequently used mechanisms to host applications in a computer system**. Virtualization uses the notion of a virtual machine as the fundamental unit. Containerization, on the other hand, uses the concept of a container. Both of these technologies play a crucial role and have their merits and demerits.

In this article, we’ll introduce both these technologies and compare some of the characteristics.

## 2. Virtualization[](https://www.baeldung.com/cs/virtualization-vs-containerization#virtualization)

**[Virtualization](https://www.baeldung.com/cs/virtualization-intro) helps us to create software-based or virtual versions of a computer resource**. These computer resources can include computing devices, storage, networks, servers, or even applications.

It allows organizations to **partition a single physical computer or server into several virtual machines (VM)**. Each VM can then interact independently and run different operating systems or applications while sharing the resources of a single computer.

### 2.1. How Does Virtualization Work?[](https://www.baeldung.com/cs/virtualization-vs-containerization#1-how-does-virtualization-work)

**Hypervisor software facilitates virtualization**. A hypervisor sits on top of an operating system. But, we can also have hypervisors that are installed directly onto the hardware. **Hypervisors take physical resources and divide them up so that virtual environments can use them**.

When a user or program issues an instruction to the VM that requires additional resources from the physical environment, the hypervisor relays the request to the physical system and caches the changes. There are two types of hypervisors, Type 1 (Bare Metal) and Type 2 (Hosted).

![virt v contain 1](https://www.baeldung.com/wp-content/uploads/sites/4/2020/07/virt-v-contain-1.png)

The main feature of virtualization is that it lets you run different operating systems on the same hardware. Each virtual machine’s operating system (guest OS) does all the necessary start-up activities such as bootstrapping, loading the kernel, and so on. However, each guest OS is controlled through elevated security measures so that they don’t acquire full access to the underlying OS.

## 3. Containerization[](https://www.baeldung.com/cs/virtualization-vs-containerization#containerization)

Containerization is a lightweight alternative to virtualization. This involves encapsulating an application in a container with its own operating environment. Thus, instead of installing an OS for each virtual machine, containers use the host OS.

### 3.1. How Does Containerization Work?[](https://www.baeldung.com/cs/virtualization-vs-containerization#1-how-does-containerization-work)

**Each container is an executable package of software that runs on top of a host OS**. A host can support many containers concurrently. For example, in a microservice architecture environment, this set up works as all containers run on the minimal, resource-isolated process that others can’t access.

![virt v contain 2](https://www.baeldung.com/wp-content/uploads/sites/4/2020/07/virt-v-contain-2.png)

The preceding diagram demonstrates the layout of containerized architecture. We can consider a container as the top layer of multilayered cake:

1. At the bottom of the layer, there are physical infrastructures such as CPU, disk storage, and network interfaces
2. Above that, there is the host OS and its kernel. The kernel acts the bridge between the software of the OS and the hardware resources
3. The container engine and its minimal guest OS sits on top of the host OS
4. At the very top, there are binaries, libraries for each application and the apps that run on their isolated user spaces

**Containerization evolved from a Linux feature known as _cgroups_.** It’s a feature for isolating and controlling resource usage for an operating system process.

For example, it defines the amount of CPU and RAM or the number of threads that a process can entitle to access within the Linux kernel. _cgroups_ later became Linux Containers (LXC) with more advanced features for namespace isolation of components, such as routing tables and file systems.

## 4. Comparison[](https://www.baeldung.com/cs/virtualization-vs-containerization#comparison)

Let’s summarise the comparison between virtualization and containerization on various aspects:

|Area|Virtualization|Containerization|
|---|---|---|
|Isolation|Provides complete isolation from the host operating system and the other VMs|Typically provides lightweight isolation from the host and other containers, but doesn’t provide as strong a security boundary as a VM|
|Operating System|Runs a complete operating system including the kernel, thus requiring more system resources such as CPU, memory, and storage|Runs the user-mode portion of an operating system, and can be tailored to contain just the needed services for your app using fewer system resources|
|Guest compatibility|Runs just about any operating system inside the virtual machine|Runs on the same operating system version as the host|
|Deployment|Deploy individual VMs by using Hypervisor software|Deploy individual containers by using [Docker](https://www.baeldung.com/docker-java-api) or deploy multiple containers by using an orchestrator such as [Kubernetes](https://www.baeldung.com/kubernetes)|
|Persistent storage|Use a Virtual Hard Disk (VHD) for local storage for a single VM or a Server Message Block (SMB) file share for storage shared by multiple servers|Use local disks for local storage for a single node or SMB for storage shared by multiple nodes or servers|
|Load balancing|Virtual machine load balancing is done by running VMs in other servers in a failover cluster|An orchestrator can automatically start or stop containers on cluster nodes to manage changes in load and availability.|
|Networking|Uses virtual network adapters|Uses an isolated view of a virtual network adapter. Thus, provides a little less virtualization|
![[Pasted image 20240319153302.png]]
traditional deployment

![[Pasted image 20240319153321.png]]
virtualized deployment

![[Pasted image 20240319153341.png]]
container deployment


## Docker commands 

- **Docker version**: Displays the currently installed Docker version information.
- **Docker search**: Searches for images in the Docker Hub registry.
- **Docker pull**: Downloads an image from a registry (like Docker Hub) to your local machine.
- **Docker run**: Creates and starts a container from a specified image.
- **Docker ps**: Lists the currently running containers.
- **Docker stop**: Stops a running container.
- **Docker restart**: Restarts a stopped or running container.
- **Docker kill**: Forcibly stops a running container.
- **Docker exec**: Executes a command inside a running container.
- **Docker login**: Logs in to a Docker registry (like Docker Hub).
- **Docker commit**: Creates a new image from changes made to a container.
- **Docker push**: Uploads a local image to a remote registry.
- **Docker network**: Manages Docker networks, allowing containers to communicate with each other.
- **Docker history**: Shows the history of an image, including the layers and commands used to build it.
- **Docker rmi**: Removes one or more images from your local machine.
- **Docker ps -a**: Lists all containers, both running and stopped.
- **Docker copy (docker cp)**: Copies files or directories between a container and the local filesystem.
- **Docker logs**: Fetches the logs of a container.
- **Docker volume**: Manages Docker volumes, allowing containers to store and access persistent data.
- **Docker logout**: Logs out from a Docker registry.

## Docker compose

Docker Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services, networks, and volumes. Then, with a single command, you create and start all the services from your configuration.

### Why?

- **Simplification**: It simplifies the process of managing and deploying multi-container applications.
- **Configuration as code**: Allows you to define your Docker environment in a code-like format, making it easy to understand, version control, and share.

### How?

- **Define services**: You list out the services your application needs in a `docker-compose.yml` file, specifying the images, ports, volumes, and other configurations.
- **Networking**: Docker Compose sets up a single network for your app by default, allowing containers to communicate with each other.
- **Volumes**: You can specify shared or persistent storage volumes to be used by the containers.

### When?

- Use Docker Compose when you have an application that requires multiple Docker containers to work together, such as a web application with a separate database and caching service.

### Where?

- Docker Compose can be used in development, testing, and production environments. It is particularly useful in development workflows where you can define and start an application’s entire environment with one command.