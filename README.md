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


Step 2: Local DNS Cache Exercise
- Go back to DC-1 and change mainframe's record address to 8.8.8.8, click apply then ok 

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/226d7318-247b-4259-98a7-f3c2b565ec59)

- In Client-1, using the Command Prompt, ping "mainframe" again, you will notice that it still pings to the old IP address, observe the local dns cache by using "ipconfig /displaydns"  

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/00295dc1-2dc3-469b-9e29-3f97aa490492)

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/340a4c5a-4c31-4670-a364-5619868523f4)

-Flush the DNS cache by using "ipconfig /flushdns", if you get a notification saying "the requested operation requires elevation", it means that you will need to reopen the Command Prompt and run the application as an administrator, continue using the flushdns and displaydns command and you will observe that the cache is now empty 

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/ccc12756-07b2-42ea-bbbc-7eb5c86116ee)

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/fb5ddddb-22fe-46ad-b948-1da6373441e9)

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/4f52d5c7-c34f-4d3e-a71a-cecba2729a13)

- Attempt to ping "mainframe" again and observe that the address of the new record we put as 8.8.8.8 is showing up

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/45cd509c-e051-409a-92e2-efd7335f672a)


-Step 3: CNAME Records
-In DC-1 within the server manager, create a CNAME record that points the host "search" to "www.google.com" 

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/e379e7ba-b4ca-45fe-a8a9-bf97493e98f6)

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/64a99d11-d0f6-4485-a117-49303992712d)

- In Client-1, attempt to ping and nslookup "search" and observe the results of the CNAME record

![image](https://github.com/thechristinaq/Understanding-Domain-Name-System-DNS-/assets/165831241/053a2680-a484-4aa9-a638-57d9905f1255)




