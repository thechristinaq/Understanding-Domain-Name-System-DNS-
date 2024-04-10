<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab we will be experimenting and gaining a deeper understanding of how DNS works.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>
- Windows Server 2010
- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Step 1: A-Record Exercise
- Step 2: Local DNS Cache Exercise
- Step 3: CNAME Records

<h2>Tutorial Steps</h2>

Step 1: A-Record Exercise
- Log into DC-1 and Client-1 VM with your domain admin account using Remote Desktop Connection
- From Client-1, try to ping "mainframe" using the Command prompt, you will notice that it fails, next try to typing nslookup "mainframe" and that it fails as well since it does not have a DNS record

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/0074f26f-0a20-405d-8ab6-a0b8d8e17bb4)

- In the DC-1 VM, go into the server manager application, go to tools, DNS, a DNS manager will pop up, click DNS, DC-1, forward lookup zones, mydomain.com (or the domain you created) right click on the mydomain.com folder, click New Host (A or AAAA), create a DNS A-record for "mainframe" and have it point to DC-1's Private IP address

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/360d89d8-aa5d-4fd0-9458-9ed4d3b27596)

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/41e1b0e8-f079-4f69-9d7e-bf5d8148462b)

- Go back to Client-1 and try to ping and nslookup "mainframe" and observe that it works

 ![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/d091020e-f293-4b6e-b335-29e6a99ead94)
 
