# k8s
k8s - Kubernetes reference

## Kubernetes Networking

#### Underlay network
Underlay network is closer to the physical layer. It includes switches, routers, VLANs and so on. It is the basis on which overlay networks are built. It tends to be less scalable due to technical limitations. However, since it’s closer to the actual hardware, it is slightly faster than an overlay.  
#### Overlay network
Overlay network refers to the virtual network layer. In this type, you’ll hear terms like veth (virtual eth or virtual network interface), and VxLAN. It is designed to be highly scalable than the underlying network. For example, while VLANs in the underlying network support only 4096 identifiers, VxLAN can reach up to 16 million ones. Kubernetes supports both networking models, so you can base your model of choice on other factors than whether or not the cluster can handle it. 

#### Kubernetes dictates the following requirements on any networking implementation:
* all Pods can communicate with all other Pods without using network address translation (NAT).
* all Nodes can communicate with all Pods without NAT.
* the IP that a Pod sees itself as is the same IP that others see it as.

Given these constraints, we are left with four distinct networking problems to solve:
* Container-to-Container networking
* Pod-to-Pod networking
* Pod-to-Service networking
* Internet-to-Service networking
