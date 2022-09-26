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
