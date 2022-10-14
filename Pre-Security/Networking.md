# Networking
## NETWORKING TOPOLOGIES
 
*Star topology* : *, this topology is at a higher cost than the others but have advantages such as : very scalable in nature (you can add devices easily), ..
And disadvantages : If the centralised hardware that connects devices fails, these devices will no longer be able to send or receive data. Thankfully, these centralised hardware devices are often robust.
 
*Bus topology* : this type of connection relies upon a single connection which is known as a backbone cable.  If this cable were to break, devices can no longer receive or transmit data along the bus. This bottleneck also results in very difficult troubleshooting because it quickly becomes difficult to identify which device is experiencing issues with data all travelling along the same route. 
However, bus topologies are one of the easier and more cost-efficient topologies to set up because of their expenses, such as cabling or dedicated networking equipment used to connect these devices.

*ring topology* : A ring topology works by sending data across the loop until it reaches the destined device, using other devices along the loop to forward the data. Interestingly, a device will only send received data from another device in this topology if it does not have any to send itself. 
The design of this topology does, however, mean that a fault such as cut cable, or broken device will result in the entire networking breaking.

## General Questions : 
What protocol does the `ping` command use ? ICMP (Internet Control Message Protocol).

What is the technical term for dividing a network up into smaller pieces? Subnetting.

How many bits are in a subnet mask? 32 (4x8).

What address is used to identify the start of a network? **Network Adress**

What address is used to identify devices within a network? **Host Adress**

What is the name used to identify the device responsible for sending data to another network? **Default Gateway**

What does ARP stand for? **Address Resolution Protocol**

What category of ARP Packet asks a device whether or not it has a specific IP address? **Request**

What address is used as a physical identifier for a device on a network? **MAC adress**

What address is used as a logical identifier for a device on a network? **IP adress**

**DHCP : Dynamic Host Configuration Protocol**

What type of DHCP packet is used by a device to retrieve an IP address? **DHCP Discover**

What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server? **DHCP Request**

Finally, what is the last DHCP packet that is sent to a device from a DHCP server? **DHCP ACK**


## OSI MODEL
### What is OSI Model ?

The OSI model (or Open Systems Interconnection Model) is an absolute fundamental model used in networking

The OSI model consists of seven layers which are illustrated in the diagram below. Each layer has a different set of responsibilities and is arranged from Layer 7 to Layer 1.

At every individual layer that data travels through, specific processes take place, and pieces of information are added to this data. However, for now, we only need to understand that this process is called encapsulation.

### Layer 7 : Application

The application layer of the OSI model is the layer that you will be most familiar with. This familiarity is because the application layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received.

### Layer 6 : Presentation

This layer acts as a **translator** for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. 

For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.

### Layer 5 : Session

Once data has been correctly translated or formatted from the presentation layer (layer 6), the session layer (layer 5) will begin to create a connection to the other computer that the data is destined for. When a connection is established, a session is created. Whilst this connection is active, so is the session.

The session layer will begin to divide up the data sent into smaller chunks of data and begin to send these chunks (packets) one at a time.

### Layer 4 : Transport

Layer 4 of the OSI model plays a vital part in transmitting data across a network and can be a little bit difficult to grasp. When data is sent between devices, it follows one of two different protocols that are decided based upon several factors:

- TCP
- UDP

TCP stands for Transmission Control Protocol. This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.

Not only this, but TCP incorporates error checking into its design. Error checking is how TCP can guarantee that data sent from the small chunks in the session layer (layer 5) has then been received and reassembled in the same order.

Now UDP stands for User Datagrem Protocol. This protocol is not nearly as advanced as its brother - the TCP protocol. It doesn't boast the many features offered by TCP, such as error checking and reliability.

In fact, any data that gets sent via UDP is sent to the computer whether it gets there or not. There is no synchronisation between the two devices or guarantee; just hope for the best, and fingers crossed. 

UDP is faster than TCP.

UDP is useful in situations where there are small pieces of data being sent. For example, protocols used for discovering devices (ARP and DHCP) or larger files such as video streaming (where it is okay if some part of the video is pixelated. Pixels are just lost pieces of data!)

### Layer 3 : Network 

The third layer of the OSI model (network layer) is where the magic of routing & re-assembly of data takes place.

Whilst some protocols at this layer determine exactly what is the "optimal" path that data should take to reach a device, we should only know about their existence at this stage of the networking module. 

Briefly, these protocols include OSPF (Open Shortest Path First) and RIP (Routing Information Protocol).

### Layer 2 : Data link

The data link layer focuses on the physical addressing of the transmission.

It receives a packet from the network layer (including the IP address for the remote computer) and adds in the physical MAC (Media Access Control) address of the receiving endpoint. 

Inside every network-enabled computer is a Network Interface Card (NIC) which comes with a unique MAC address to identify it.

### Layer 1 : Physical 

This layer is one of the easiest layers to grasp. Put simply, this layer references the physical components of the hardware used in networking and is the lowest layer that you will find. Devices use electrical signals to transfer data between each other in a binary numbering system (1's and 0's).

For example, ethernet cables connecting devices.

## Packets & Frames
### What is it ?

This process is called encapsulation. At this stage, it's safe to assume that when we are talking about anything IP addresses, we are talking about packets. When the encapsulating information is stripped away, we're talking about the frame itself.

Packets are an efficient way of communicating data across networked devices such as those explained in Task 1. Because this data is exchanged in small pieces, there is less chance of bottlenecking occurring across a network than large messages being sent at once.

### TCP/IP

TCP (or Transmission Control Protocol for short) is another one of these rules used in networking.

This protocol is very similar to the OSI model that we have previously discussed in room three of this module so far. The TCP/IP protocol consists of four layers and is arguably just a summarised version of the OSI model. These layers are:

- Application
- Transport
- Internet
- Network Interface

One defining feature of TCP is that it is connection-based, which means that TCP must establish a connection between both a client and a device acting as a server before data is sent.

Because of this, TCP guarantees that any data sent will be received on the other end. This process is named the Three-way handshake.

TCP packets contain various sections of information known as headers that are added from encapsulation. Let's explain some of the crucial headers in the table below:

![image](https://user-images.githubusercontent.com/112873207/192270035-9026a9f5-a722-41b3-bb7e-98366e7940a2.png)

The Three-way handshake communicates using a few special messages - the table below highlights the main ones:

![image](https://user-images.githubusercontent.com/112873207/192270899-7f124963-360d-4ab7-a270-c32d656cc1b9.png)

### UDP/IP

The User Datagram Protocol (UDP) is another protocol that is used to communicate data between devices.

UDP packets are much simpler than TCP packets and have fewer headers. However, both protocols share some standard headers, which are what is annotated in the table below:

![image](https://user-images.githubusercontent.com/112873207/192273066-351a79ce-bc68-4722-964b-43a571543e5c.png)

![image](https://user-images.githubusercontent.com/112873207/192273499-9c307936-54a6-4898-acdb-76c83d3f5142.png)

### Port 101

While the standard rule for web data is port 80, a few other protocols have been allocated a standard rule. Any port that is within 0 and 1024 (1,024) is known as a common port. Let's explore some of these other protocols below :

![image](https://user-images.githubusercontent.com/112873207/192274171-9211ed85-34ec-4a19-a0c0-5c99a45e8bf8.png)

## Extending your network

### Port Forwarding 

It is easy to confuse port forwarding with the behaviours of a firewall (a technology we'll come on to discuss in a later task). However, at this stage, just understand that port forwarding opens specific ports (recall how packets work). In comparison, firewalls determine if traffic can travel across these ports (even if these ports are open by port forwarding).

Port forwarding is configured at the router of a network.

What is the name of the device that is used to configure port forwarding? **Router**

### Firewalls 101

A firewall is a device within a network responsible for determining what traffic is allowed to enter and exit. Think of a firewall as border security for a network. An administrator can configure a firewall to permit or deny traffic from entering or exiting a network based on numerous factors such as:

- Where the traffic is coming from? (has the firewall been told to accept/deny traffic from a specific network?)
- Where is the traffic going to? (has the firewall been told to accept/deny traffic destined for a specific network?)
- What port is the traffic for? (has the firewall been told to accept/deny traffic destined for port 80 only?)
- What protocol is the traffic using? (has the firewall been told to accept/deny traffic that is UDP, TCP or both?)

Firewalls come in all shapes and sizes.

From dedicated pieces of hardware (often found in large networks like businesses) that can handle a magnitude of data to residential routers (like at your home!) or software such as Snort, firewalls can be categorised into 2 to 5 categories.

We'll cover the two primary categories of firewalls in the table below:

![image](https://user-images.githubusercontent.com/112873207/192290411-dff588e6-d605-46ce-a5a8-58d3bf248d26.png)

What layers of the OSI model do firewalls operate at? layer 3 and layer 4.

### VPN - Basics

A Virtual Private Network (or VPN for short) is a technology that allows devices on separate networks to communicate securely by creating a dedicated path between each other over the Internet (known as a tunnel). Devices connected within this tunnel form their own private network.

![image](https://user-images.githubusercontent.com/112873207/192301539-c700e196-8b4d-4c91-9587-f735618f379c.png)

The devices connected on Network #3 are still a part of Network #1 and Network #2 but also form together to create a private network (Network #3) that only devices that are connected via this VPN can communicate over.

Let's cover some of the other benefits offered by a VPN in the table below:

![image](https://user-images.githubusercontent.com/112873207/192302193-695d270e-48da-46cb-8970-d2578a6fe806.png)

What VPN technology only encrypts & provides the authentication of data? PPP

What VPN technology uses the IP framework? IPSec

### LAN Networking Device

What is a `Router` ? It's a router's job to connect networks and pass data between them. It does this by using routing (hence the name router!).

Routers operate at Layer 3 of the OSI model. 

Different protocols will decide what path should be taken, but factors include:

- What path is the shortest?

- What path is the most reliable?

- Which path has the faster medium (e.g. copper or fibre)?

What is a `Switch` ? A switch is a dedicated networking device responsible for providing a means of connecting to multiple devices. Switches can facilitate many devices (from 3 to 63) using Ethernet cables.

Switches can operate at both layer 2 and layer 3 of the OSI model. However, these are exclusive in the sense that Layer 2 switches cannot operate at layer 3.

These switches are solely responsible for sending frames to the correct device.

Layer 3 switches are more sophisticated than layer 2, as they can perform some of the responsibilities of a router. Namely, these switches will send frames to devices (as layer 2 does) and route packets to other devices using the IP protocol. 

A technology called VLAN (Virtual Local Area Network) allows specific devices within a network to be virtually split up.

