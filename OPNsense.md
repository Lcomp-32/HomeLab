
OPNsense is the firewall I will be using for this project. It is a multifunctional firewall that also preforms as a DHCP server and a DNS server. The wide scope of use cases for this software is
the reason I chose it for my lab. 


I first set up the Linux bridges to their appropate sides of the Firewall. vtnet0(vmbr0) -> WAN; vtnet1 (vmbr1) -> LAN

<img width="1314" height="303" alt="image" src="https://github.com/user-attachments/assets/42a78915-e3e6-4a82-8b80-c9a53bebec49" />


After not being to connect to the WebGUI of OPNsense, I realized that the current configuration with OPN sense was not recongnizing the two vlans on the vmbr1. To set that up, I just added the interfaces
VLANs through the prompts. Then to add them to the config I selected both of them to be an optional LAN interface. This will allow OPNsense to recognize the VLANs and their traffic.

<img width="715" height="205" alt="image" src="https://github.com/user-attachments/assets/0e8a74a9-d989-4f18-a463-7ccaeb939720" />

***ISSUE ONE: ***
The interactions with the dhcp and assigning IP was not what I was expecting. The issue came from first vtnet1 and vtnet0 where fliped in the config during my VLAN config. After I switched
the two bridges the second part of the issue was realized. DHCP would not assign an IP for the LAN interface. After looking through the documenation I found that the defaults do not
Include this functionallity. Since this was the case and the best way to config it was through the GUI, I assigned a static IP (which will work in my small network, but I wanted to leverage
DHCP for the experience).


After the previous steps I assumed that I could access the GUI now. I was wrong. The address was still the default one, so renewing the IP would fix this issue because right now other devices
have the same IP. To fix this I had to use the DHCP aspect of OPNsense to assign a IP to the WebGUI by selecting option 2. 
<img width="714" height="338" alt="image" src="https://github.com/user-attachments/assets/18c78181-510d-4f0c-bfb6-8d575b930f1a" />

