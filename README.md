# How does a computer know what its IP configuration is?

Most likely, a computer received its IP configuration from a DHCP (Dynamic Host Configuration Protocol) server. Not only did the server give the PC an IP address, but it also told the PC where the default gateway was---and more than likely---how to find a DNS server.

<a href="https://www.youtube.com/watch?v=72snZctFFtA">link for info below</a>

A DNS server stands for Domain Name System being one of the most important and overlooked parts of the Internet. Without DNS the internet would collapse. Dns is used to translate an actual name into IP address. The dot at the dot at the end of a domain name represents the root of the Interent's namespace you search for a domain name your browser and your os will first determine if they know what the IP ADDRESS is already. It could be configured on your computer or it could be in memory or cache. The os is configured to ask a resolving name server for ip addresses it does not know. The only thing that all resolving name servers should know is where to find the root name servers, and the root will reply saying that It doesn't know the ip, but it does know where to find the com name servers. The Com name servers are called the Top level Domain name servers or TLD. The resolving name servers then takes all of this information from the root name servers, puts it in it's cache then goes directly to the com TLD servers. When the resolving name servers queriest about the domain the com TLD servers reply saying that it doesn't know but it referrs the resolving name servers to the domain.com servers. The resolving name servers takes all of this information from the com TLD servers and puts it in it's cache. The set of name servers are the ANS? The COM TLD ame serverse knew where to find the ANS with the help of the Domains registar, when a domain is purchased the registrar is told which authoratative name servers that domain should use they notify the organization responsible for the TLD the registry. Telling them to update the TLD name servers</p>

- A computer will receive it's IP configuration in one of two ways, statically(manually set) or dynamically(through a service like DHCP). Static address assignment works fine for very small and stable networks, but quickly becomes unwieldy and error prone as the network grows.

# Static IP addressing.
  >> The administrator assigns an IP number and subnet mask to each host in the network.
      - Each network interface is going to be available to connect to the network requires this information.
  >> The administrator assigns a default gateway location and DNS server location to each host in the network.
      - These are required if access outside of the network is going to be allowed (default gateway) and human friendly naming conventions are allowed to find network resources (DNS server)

# Dynamic IP addressing.
  >> The administrator configures a DHCP server to handle the assigning process, which automates the process.
     - The DHCP server listens on a specific port for IP information requests.
     - Once it receives a request, the DHCP server responds with the required information.


# Typical DHCP process.
  >> Upon boot up, a PC that is configured to request an IP configuration sends a DHCP discovery packet.
     - The discovery packet is sent to the broadcast address 255.255.255.255.67 (UDP port 67).
  >> The DHCP server receives the discovery packet and responds with an offer packet.
     - The offer packet is sent to the MAC address of the computer using UDP port 68.
  >> The computer receives the offer packet from the DHCP server and returns a request packet(requesting the proper IP configuration) to the DHCP server.
  >> Once the DHCP server receives the request packet, it sends back an acknowledgement packet, which contains the required IP configuration information.
  >> Upon receipt of the acknowledgement packet, the PC changes its IP configuration to reflect the information received.


# Components and processes of DHCP.
 <h2> Ports used. </h2>
    >> Pc sends discovery packet to 255.255.255.255.67.
    >> DHCP sends offer packet to the PC's MAC address on port 68.
    
 <h2> Address scope. </h2>
    >> Administrator configures the IP address range with one that is available to be handed out.
    
 <h2> Address reservations. </h2>
    >> Administrator reserves specific IP addresses to be handed out to specific MAC addresses. These are used for devices that should always have the same IP address (e.g.., servers and routers).
    >> Allows for these addresses to be changed from a central location instead of having to log into each device separately.
    
     // side note (UDP(port 67) = 255.255.255.255)
<h2> Leases. </h2>
  >> Configuration parameters are only good to a specified amount of time.
  >> Leases are configured by the admin.

<h2> Options. </h2>
  >> Default gateway location
  >> DNS server addresses (there can be more than one).
  >> Time server addresses.
  >> Many additional options

<h2> Preferred IP configuration. </h2>
  >> A PC can have a preferred IP address.
  >> The admin can configured the DHCP server to either honor the preference or ignore it.


<h2> Under the right circumstances, a DHCP server isn't required to reside on the local network segment</h2>

Broadcast transmissions cannot pass through a router. If there is not a DHCP server on the local network segment, the router can be configured to be a DHCP relay. When a DHCP relay(which can also be called an IP helper)
receives a discovery packet from a node, it will forward that packet to the network segment on which the DHCP server resides. 
This allows for there to be fewer configured DHCP servers in any given network, reducing the amount of maintenance that an admin needs to perform.

<li> A network segment is an electrical connection between networked devices using a shared medium </li>

# DNS records.
  
  <h2> A record. </h2>
    >> Maps hostnames to their IPv4 address. 
  
  <h2> AAAA(Quadrouple A) record. </h2>
    >> Maps hostnames to their IPv6 address.
  
  <h2> CNAME record. </h2>
    >> Maps canonical(alias) names to hostnames.
  
  <h2> PTR record. </h2>
    >> Pointer record that points to a canonical name.
  
  <h2> MX record. </h2>
  >> Maps to the email server taht is specified for a specific domain. It is the record that determines how email travels from sender to recipient.
