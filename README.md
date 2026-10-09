# cybersecurity-home-lab
Lab 1
Overview
I built a small network from scratch using virtual machines: a pfsense firewall acting as the router and security perimeter, an ubuntu workstation protected behind it on the LAN, and a Kali Linux machine placed on an isolated segment for future testing. The objective was to create a connected network through a firewall with three disconnected VMs

Skills Demonstrated: network segmentation, firewall deployment, DHCP, subnetting, perimeter design

The environment I created was the pfsense VM which was the firewall/router. The pfsense machine connected to the WAN(NAT), LAN, OPT1 networks. The ubuntu desktop was the protected workstation behind the pfsense firewall on the LAN 192.168.1.0/24. Kali Linux has been set up as an isolated test and configured to the OPT1 network connection. 

Network Design
Internet
