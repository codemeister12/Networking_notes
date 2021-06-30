# Networking_notes
======================================================================
Configuration(default gateway)
======================================================================

	• with privileges enter into CMD "ipconfig"
  •  command "route print" This command prints out all of the gateways on the network
  • To access Network 1 enter in "route add 192.168.5.0 mask 255.255.255.0 192.168.1.10 -p" 
  
  Now in the persistent routes you will see This network added
 
===========================================================================
Persistent Routes:
  Network Address          Netmask  Gateway Address  Metric
   192.168.56.255  255.255.255.255     192.168.56.1       1
      192.168.5.0    255.255.255.0     192.168.1.10       1
===========================================================================
