<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>DHCP Configuration – ACNS Packet Tracer Project</title>
</head>
<body>

<h1>DHCP Configuration Lab – ACNS Packet Tracer Project</h1>

<p>
This project was completed as part of my journey as an <strong>ACNS (Advanced Certificate in Network Security) student at Aptech</strong>. 
The objective of this Packet Tracer lab was to configure a router as a DHCP server to automatically assign IP addresses 
to client devices within a Local Area Network (LAN).
</p>

<hr>

<h2>Project Objectives</h2>
<ul>
    <li>Configure a router interface with a static IP address</li>
    <li>Enable DHCP service on the router</li>
    <li>Create a DHCP pool for automatic IP allocation</li>
    <li>Configure client PCs to obtain IP automatically</li>
    <li>Verify network connectivity</li>
</ul>

<hr>

<h2>Step-by-Step Configuration Process</h2>

<h3>Step 1: Access Router and Enter Configuration Mode</h3>
<pre>
enable
configure terminal
</pre>

<h3>Step 2: Configure Router Interface</h3>
<pre>
interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
</pre>
<p>
This command assigns the router as the default gateway for the network.
</p>

<h3>Step 3: Exclude Router IP from DHCP Pool</h3>
<pre>
ip dhcp excluded-address 192.168.10.1
</pre>
<p>
This prevents the router's IP address from being assigned to client devices.
</p>

<h3>Step 4: Create DHCP Pool</h3>
<pre>
ip dhcp pool ACNS_LAN
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 8.8.8.8
exit
</pre>

<p><strong>Explanation of Commands:</strong></p>
<ul>
    <li><strong>ip dhcp pool ACNS_LAN</strong> – Creates a DHCP pool</li>
    <li><strong>network</strong> – Defines the network range</li>
    <li><strong>default-router</strong> – Assigns the gateway to clients</li>
    <li><strong>dns-server</strong> – Assigns DNS server to clients</li>
</ul>

<h3>Step 5: Configure Client PCs to Use DHCP</h3>
<ul>
    <li>Open PC</li>
    <li>Go to Desktop</li>
    <li>Select IP Configuration</li>
    <li>Choose DHCP</li>
</ul>

<p>
The PCs will automatically receive:
</p>
<ul>
    <li>IP Address</li>
    <li>Subnet Mask</li>
    <li>Default Gateway</li>
    <li>DNS Server</li>
</ul>

<h3>Step 6: Verify Configuration</h3>

<p>On the PC:</p>
<pre>
ipconfig
ping 192.168.10.1
</pre>

<p>On the Router:</p>
<pre>
show ip dhcp binding
show ip dhcp pool
show ip interface brief
</pre>

<hr>

<h2>What I Learned</h2>
<ul>
    <li>How DHCP simplifies IP address management</li>
    <li>The DORA process (Discover, Offer, Request, Acknowledge)</li>
    <li>How routers function as DHCP servers</li>
    <li>How to verify and troubleshoot IP assignment</li>
</ul>

<hr>

<h2>Conclusion</h2>

<p>
This lab strengthened my practical understanding of dynamic IP configuration and LAN deployment. 
It bridges theoretical networking knowledge with hands-on implementation and builds a strong 
foundation for advanced networking concepts such as routing, VLANs, and network security.
</p>

<p>
More advanced networking and security labs coming soon. Stay tuned.
</p>

</body>
</html>
