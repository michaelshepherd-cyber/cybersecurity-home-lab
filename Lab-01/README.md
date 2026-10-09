# cybersecurity-home-lab
**Lab 1
Overview**

I built a small network from scratch using virtual machines: a pfsense firewall acting as the router and security perimeter, an ubuntu workstation protected behind it on the LAN, and a Kali Linux machine placed on an isolated segment for future testing. The objective was to create a connected network through a firewall with three disconnected VMs

**Skills Demonstrated:** network segmentation, firewall deployment, DHCP, subnetting, perimeter design

The environment I created was the pfsense VM which was the firewall/router. The pfsense machine connected to the WAN(NAT), LAN, OPT1 networks. The ubuntu desktop was the protected workstation behind the pfsense firewall on the LAN 192.168.1.0/24. Kali Linux has been set up as an isolated test and configured to the OPT1 network connection. 

**Network Design**

Internet

   |
 pfSense   WAN  (gets internet via NAT)
 
   |       LAN  192.168.1.1  <-- protected segment
   
   |       OPT1 (reserved for isolated Kali segment)
   
   |
 Ubuntu  192.168.1.x  (address assigned automatically by pfSense)


 **What I did**
1. I configured three network adapters on the pfsense VM -- one NAT adapter for the internet-facing WAN, and two VirtualBox Internal network adaptors named LAN and OPT1 to create private, isolated segments

2. Assigned the interfaces inside pfsense (em0->WAN, em1->LAN, em2->OPT1) so the firewall knew which segment each NIC served

3. Placed Ubuntu on the LAN and confirmed it automatically received an IP address, gateway, and DNS from the pfsense DHCP server

4. Verified end to end connectivity -- Ubuntu could reach the firewall, and reach the internet through the firewall. This proved traffic was being routed and filtered as designed.

5. Accessed and secured the pfsense dashboard, changing the default admin password.

**What I learned**

I learned the practical differences between Virtual Box NAT, Bridged, and Internal Network modes. I learned the Internal Network is used to build isolated segments -- the same concept as VLANs and separate switches in a physical network. 

How a firewall uses separate interfaces (WAN/LAN/OPT1) to enforce security boundary, and how DHCP, gateways, and subnets fit together to make a segment functional. 

Why segmentation matters defensively: the kali host is deliberately placed on its own segment so that, in later labs, I can control exactly what it is allowed to reach. The principle of containing a host rather than trusting it. 

**Real world Relevance**

This lab mirrors the perimeter of almost any corporate network: an untrusted outside, a protected internal segment, and separated zones for higher-risk systems. Understanding how traffic is routed and where it can be inspected is the foundation for detection and incident-response work in the labs that follow. 
