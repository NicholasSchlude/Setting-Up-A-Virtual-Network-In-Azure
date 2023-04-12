# Setting-Up-A-Virtual-Network-In-Microsoft-Azure
Below will outline the steps I took to make a virtual network using Microsoft Azure 

<b> <h2> Environments, Software and OS used</h2>
- Microsoft Azure 
- Windows 10 Pro 
- Ubuntu Server 20.04 
- WireShark </b>

<h2>Lab</h2>
<br>1. Prior to this lab, I signed up Microsoft Azure's free account with $200 worth of credits to practice this lab. I signed up and a screenshot of the Azure Home Portal is shown below. 
  
![image](https://user-images.githubusercontent.com/55405034/231606965-0149dcf0-b279-4495-a938-5a7188e12e47.png) </br>

<br> 2.	The first things necessary for this lab was creating the virtual machines. I chose to use a virtual Windows 10 machine and a virtual ubuntu server. In order to do this, I created a Resource Group called “RG-VNL” and chose the region “West US 3.” </br>

3. Once that was completed, I created the Virtual Windows 10 Machine and named it “VM1”. I will be referring to this VM as VM1 the rest of the lab. Before finishing the completion of VM1, I set up a virtual network and allowed RDP to be open so I was able to remote in. Below is a screen shot of the resources that were created once the deployment of the machine was created. 

![image](https://user-images.githubusercontent.com/55405034/231607158-f6b16925-46cb-47cb-b385-5a849afb5ba0.png)

<br> 4.	Once I completed VM1, I made Virtual Ubuntu Server which I called “VM2”. I will be referring to this vm as VM2 for the rest of this lab. I created another virtual machine and placed it inside the RG-VNL Resource Group. I completed the same steps as before, and below is a screenshot of the new resources in the RG-VNL. </br>

![image](https://user-images.githubusercontent.com/55405034/231607895-7f00e9a8-edfd-4077-a720-b167dc004668.png)

<br> 5.	Azure has a feature called “Network Watcher” that can graphically display the topology of the Virtual Network I created automatically. Below is a screenshot of the topology that I created for this lab. </br>

![image](https://user-images.githubusercontent.com/55405034/231608040-c9d31280-331a-4e1b-923c-25e0ba830126.png)

<br> 6. With the resources created, the first thing I did was remote into VM1 using RDP 3389. Below is a screenshot of the desktop after remoting in. </br>

![image](https://user-images.githubusercontent.com/55405034/231608475-51027fc6-c359-4266-b705-b44e7901d453.png)

<br> 7.	The first thing after the resources were created was download WireShark into VM1 to analyze network traffic. Below is a screenshot of WireShark prior to starting packet captures. </br>

![image](https://user-images.githubusercontent.com/55405034/231608716-c719abb4-9031-41bc-b7e3-fde48612470f.png)

<br> 8.	I started a packet capture and started to see the network traffic being captured. I wanted to ping VM2 to test the virtual network connectivity, and applied an icmp filter so I can only see my ping traffic and know that I was able to communicate with VM2. Below is a screenshot of proof that VM2 and VM1 can communicate. </br>

![image](https://user-images.githubusercontent.com/55405034/231608799-b507ff19-86af-4086-917f-1327b2919d80.png)

<br> 9. Once I saw VM1 and VM2 communicate, I set up a Firewall on VM2 to block ICMP traffic. I went to “Inbound Security Rules” and created a rule on VM2 to block all inbound ICMP traffic. Below are screenshots of the security rule I added, and the WireShark packet captures after applying the rule. </br>

![image](https://user-images.githubusercontent.com/55405034/231609001-eeb27a6d-3df3-4cff-93ca-86a69d25db7b.png)

![image](https://user-images.githubusercontent.com/55405034/231609044-4bdfae1f-d8b6-4c0e-a0ba-3166c677e39c.png)

<br> 10.	After Denying ICMP traffic and using a firewall rule, I turned off the rule and allowed ICMP traffic again before using SSH to remote into VM2. Below is a screenshot showing I successfully used ssh to log into VM2. </br>

![image](https://user-images.githubusercontent.com/55405034/231609219-9dd259c2-7277-4827-a0fa-bbaab6a483da.png)

<br> 11.	After successfully using ssh, I applied a DHCP filter to WireShark, and inside the terminal used ipconfig / renew just to show some DHCP traffic. </br>

![image](https://user-images.githubusercontent.com/55405034/231609467-8703a852-4073-4010-89b5-17ad51f57d7d.png)

<br> 12.	After applying the DHCP filter to WireShark, I applied the DNS and filter to show DNS traffic. I used nslookup inside the terminal for www.microsoft.com and received the following results. </br>

![image](https://user-images.githubusercontent.com/55405034/231609538-7689d7ea-a821-4ebd-b494-0025eef90d9f.png)

<br> 13.	The last thing I did for this lap was apply the TCP filter for RDP 3389 to show an active connection within RDP. </br>

![image](https://user-images.githubusercontent.com/55405034/231609655-362aedae-1e70-4f9f-a89b-0623c896a361.png)

<br> This concludes the activities I did for this lab, hope you enjoyed! </br>

