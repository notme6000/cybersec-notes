# Virtualization – Class Notes

## 1. Introduction to Virtualization

**Virtualization** is a technology that allows multiple virtual instances of computing resources (such as servers, operating systems, storage, or networks) to run on a single physical hardware system.

It enables efficient utilization of hardware by dividing one physical machine into multiple isolated virtual machines (VMs).



## 2. Key Concepts

### 1. Host Machine

The physical computer that provides hardware resources (CPU, RAM, storage).

### 2. Guest Machine (Virtual Machine)

A software-based virtual computer that runs its own operating system inside the host.

### 3. Hypervisor

A software layer that creates and manages virtual machines by allocating hardware resources.



# Types of Virtualization

## 1. Hardware (Server) Virtualization

### Definition

Dividing a physical server into multiple virtual servers using a hypervisor.

### Benefits

* Better hardware utilization
* Reduced cost
* Server consolidation
* Easier backup and recovery

### Example Hypervisors

* VMware (ESXi)
* Microsoft (Hyper-V)
* Oracle Corporation (VirtualBox)



## 2. Desktop Virtualization

### Definition

Running desktop operating systems on a centralized server and accessing them remotely.

### Advantages

* Centralized management
* Improved security
* Remote access

### Example

Virtual Desktop Infrastructure (VDI)



## 3. Operating System Virtualization (Containers)


### Definition

Multiple isolated user-space instances share the same OS kernel.

### Popular Platforms

* Docker
* Kubernetes

### Difference from VMs

* Containers share the host OS kernel.
* VMs run separate operating systems.



## 4. Storage Virtualization

### Definition

Combining multiple physical storage devices into one logical storage unit.

### Benefits

* Simplified storage management
* Better scalability
* Improved disaster recovery



## 5. Network Virtualization

### Definition

Creating virtual networks independent of physical network hardware.

### Examples

* Virtual LAN (VLAN)
* Software-Defined Networking (SDN)



# Types of Hypervisors

## Type 1 Hypervisor (Bare-Metal)

![Image](https://www.manageengine.com/network-monitoring/images/bare-metal-hypervisor.jpg)


### Characteristics

* Installed directly on hardware
* High performance
* Used in enterprise environments

### Examples

* VMware ESXi
* Microsoft Hyper-V



## Type 2 Hypervisor (Hosted)


### Characteristics

* Runs on top of an existing operating system
* Suitable for labs and testing
* Easy to install

### Examples

* Oracle VirtualBox
* VMware Workstation



# Advantages of Virtualization

* Cost reduction
* Efficient resource usage
* Easy scalability
* Disaster recovery support
* Isolation between environments
* Faster deployment



# Disadvantages of Virtualization

* Initial setup cost
* Performance overhead
* Single point of failure if host fails
* Requires skilled management



# Virtualization vs Cloud Computing

| Virtualization                            | Cloud Computing                             |
| -------------------------------------- | ------------------------------------------- |
| Technology that creates virtual resources | Service delivery model using virtualization |
| Runs on local infrastructure              | Can be public, private, or hybrid           |
| Focuses on resource optimization          | Focuses on service availability             |

Cloud platforms that use virtualization include:

* Amazon Web Services
* Microsoft Azure
* Google Cloud Platform



# Applications of Virtualization

* Data centers
* Software testing labs
* Cybersecurity labs
* Development environments
* Disaster recovery systems
* Cloud infrastructure



