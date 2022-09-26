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

This layer acts as a **translator** for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.
















