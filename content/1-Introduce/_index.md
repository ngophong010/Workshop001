---
title : "Introduction"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
#### What is NetDevOps | Network DevOps?
You may also hear the terms **Network DevOps** or **NetDevOps**. Maybe you are already a Network engineer and have a great grasp on the network components within the infrastructure you understand the elements used around networking such as DHCP, DNS, NAT etc. You will also have a good understanding of the hardware or software-defined networking options, switches, routers etc.

But if you are not a network engineer then we probably need to get foundational knowledge across the board in some of those areas so that we can understand the end goal of **Network DevOps**.

But in regards to those terms, we can think of **NetDevOps** or **Network DevOps** as applying the DevOps Principles and Practices to the network, applying version control and automation tools to the network creation, testing, monitoring, and deployments.

If we think of **Network DevOps** as having to require automation, we mentioned before about DevOps breaking down the silos between teams. If the networking teams do not change to a similar model and process then they become the bottleneck or even the failure overall.

Using the automation principles around provisioning, configuration, testing, version control and deployment is a great start. Automation is overall going to enable speed of deployment, stability of the networking infrastructure and consistent improvement as well as the process being shared across multiple environments once they have been tested. Such as a fully tested Network Policy that has been fully tested on one environment can be used quickly in another location because of the nature of this being in code vs a manually authored process which it might have been before. A really good viewpoint and outline of this thinking can be found here. [Network DevOps](https://www.thousandeyes.com/learning/techtorials/network-devops)

### Networking The Basics

#### Network Devices
If you prefer this content in video form, check out these videos from Practical Networking:

- [Network Devices - Hosts, IP Addresses, Networks - Networking Fundamentals - Lesson 1a](https://www.youtube.com/watch?v=bj-Yfakjllc&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=1)
- [Network Devices - Hub, Bridge, Switch, Router - Networking Fundamentals - Lesson 1b](https://www.youtube.com/watch?v=H7-NR3Q3BeI&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=3)

**Host** are any devices which send or receive traffic.
![Host](/Workshop001/images/1.introduce/001-host.png) 

**IP Address** the identity of each host.
![IP Address](/Workshop001/images/1.introduce/002-IPAddress.png) 

**Network** is what transports traffic between hosts. If we did not have networks there would be a lot of manual movement of data!

A logical group of hosts which require similar connectivity.
![Network](/Workshop001/images/1.introduce/003-network.png) 

**Switches** facilitate communication **within** a network. A switch forwards data packets between hosts. A switch sends packets directly to hosts.

- Network: A Grouping of hosts which require similar connectivity.
- Hosts on a Network share the same IP address space.

![Switch](/Workshop001/images/1.introduce/004-switches.png) 

**Router** facilitates communication between networks. As we said before that a switch looks after communication within a network a router allows us to join these networks together or at least give them access to each other if permitted.

A router can provide a traffic control point (security, filtering, redirecting) More and more switches also provide some of these functions now.

Routers learn which networks they are attached to. These are known as routes, a routing table is all the networks a router knows about.

A router has an IP address in the networks they are attached to. This IP is also going to be each host's way out of their local network also known as a gateway.

Routers also create the hierarchy in networks I mentioned earlier.
![Switch](/Workshop001/images/1.introduce/005-router.png) 

### Switches vs Routers
**Routing** is the process of moving data between networks.
- A router is a device whose primary purpose is Routing.

**Switching** is the process of moving data within networks.
- A Switch is a device whose primary purpose is switching.

This is very much a foundational overview of devices as we know there are many different Network Devices such as:
- Access Points
- Firewalls
- Load Balancers
- Layer 3 Switches
- IDS / IPS
- Proxies
- Virtual Switches
- Virtual Routers

Although all of these devices are going to perform Routing and/or Switching.

