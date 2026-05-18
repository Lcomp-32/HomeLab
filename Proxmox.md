

The Proxmox install was pretty straightforward with minimal hiccups.

1. Flashed USB and installed Proxmox
2. Network Configuration
   *Used a ethernet connection to my ISP router to host the Proxmox GUI locally so it can be accessed from my office without a physical connection
   *configured the USB to Ethernet dongle as the primary network interface instead of wireless
   *Made my linux bridge and dongle node UP so Proxmox can could reach the network
   *Refreshed networking
3. GUI setup
   *Setup the GUI for my first node of my homelab


Issue #1:
I was not very familiar with how the dongle would be reconized internally and my knowledge of Linux Bridges were very minimal. However, I was able to troubleshoot the issue once I read documentation confered with
Claude to fill any knowledge gaps. The issue was that the "enx" dongle was not configured with vmbr0. Vmbr0 is the outer Linux Bridge that ultimately gives access to the internet. Vmbr0 by default wanted the wireless NIC connection instead of a wired one. To configure I just switched names of the NIC to the enx dongle which solved that issue. 
