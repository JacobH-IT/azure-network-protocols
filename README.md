<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)
- Ubuntu Server 20.04

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/RUDUPkf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create 2 virtual machines, Linux and Windows, under the same resource group, location, and virtual network (v-net).
</p>
<br />

<p>
<img src="https://i.imgur.com/EcKY4Yy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use remote desktop to connect to the Windows 10 virtual machine using the public IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/Fp6Qh0F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install Wireshark inside the Windows 10 virtual machine, open it and start capturing through ethernet.
</p>
<br />

<p>
<img src="https://i.imgur.com/gDNrKsP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Apply an "icmp" filter on Wireshark and then find the private IP address of the Linux VM and ping it through command prompt.
</p>
<br />

<p>
<img src="https://i.imgur.com/EaJERmR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Observe the traffic after pinging the Linux server and try pinging a website; for example, Google.
</p>
<br />

<p>
<img src="https://i.imgur.com/ICzYw4Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Perpetually ping the Linux VM by using "ping [IP address] -t" in command prompt; in Azure's Network Security Group settings add an inbound rule for the Linux VM disabling ICMP traffic. 
</p>
<br />

<p>
<img src="https://i.imgur.com/0siq1Pt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter for ssh traffic in Wireshark; in Windows Powershell use ssh command to login to the Linux VM and obvserve the traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/pk0tRx4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter for dhcp traffic in Wireshark; use command "ipconfig /renew" and observe dhcp traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/8l5wXoz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter for dns traffic in Wireshark; use command "nslookup [any website]" and observe dns traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/5oQ8Qvb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filter for "tcp.port == 3389" and observe the immense traffic due to the remote desktop connection.
</p>
<br />
