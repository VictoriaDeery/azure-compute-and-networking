<p align="center">
<img src="[https://logos-world.net/wp-content/uploads/2021/02/Microsoft-Azure-Symbol.png]" alt="Azure logo"/>
</p>

<h1>Azure Computing and Networking</h1>
This tutorial outlines how to create Virtual Networks and Subnets, Virtual Machines, and Network Security Groups. It looks at ICMP traffic between the two Virtual Machines using wireshark. This tutoorial also walksthrough configuration of a VM firewall using Azures's Network Security Group. And it shows how to observe SSH traffic, useful for connecting to and administstering on another's computer. And it descrbes observing DHCP traffic, DNS traffic, and RDP traffic <br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Create A Virtual Machine And Use It](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
  - Virtual Machines (Windows and Linux[Ubuntu])
  - Azure Network Security Groups (Firewall Resource)
- Remote Desktop
- Internet Information Services (IIS)
- Powershell
- WireShark

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Linux (Ubuntu)

<h2>List of Prerequisites</h2>

- Azure Account
- Each Section below builds off the previous sections above it

<h2>Creation Steps</h2>

  1. Create a Resource group
<img src="https://github.com/user-attachments/assets/4c4f6e0f-6ed4-40ae-b506-36f9b21a1e8e" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>  
1. Search and click on "Resource Groups" in Azure, then on "+Create." Name your Resource group and remember the region you choose. And click "Create" again.
  
<p>

  2. Create a Virtual Network and a Windows Virtual Machine
<img src="https://github.com/user-attachments/assets/102b664b-cfd5-4249-99c0-e3766be46284" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
2. To do this, search "virtual machine" and click it and "+Create" and select "azure virtual machine" in the generated dropdown. Then make sure it is in the appropriate subscription and resource group. Name your virtual machine and select a region for your virtual machine (VM). Scroll down to image and select "Windows 10 Pro" to create your Windows VM. For size, select one that has at least 2 vcpus, otherwise it may be slow (the prices listed are indicative of if the VM was perpetually left on). Scroll down and add a username and password, and make sure to keep track of them. Scoll further and select the checkbox under "Licensing". Then click "Next:Disks>" and then "Next:Networking>." At this point you may rename the network if you want by selecting the blue text that says "Create new," by "Virtual network" under "(new) windows-vm-vnet." You would write the network name of your choice and select "ok." Lastly double check the network name and region are what you would expect and then click "Review + create" and then "create."
</p>
<br />

<p>
  3. Create a Linux (Ubuntu) VM in the same resource group and virtual network as the Windows VM
<p>
<img src="https://github.com/user-attachments/assets/6af09202-acbc-4203-8a85-de063185c7ff" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
3. First search "virtual Machine" select it (you will see your previously made VM now here) and click "+Create" just as before. Now it is essential that the previously generated resource group and virtual network is selected here too. Select the same region as your first VM. Select Ubuntu 22 or 24 for image, and 2vcpus for size. For authetication type, select "password." Fill out the username and password then select  "Next:Disks>" and then "Next:Networking>." Remember to use the same Virtual Network and region as in step 2. Click "Review + create" and then "create."
</p>
<br />

<h2>ICMP traffic between  the two Virtual Machines Observation Steps</h2>

<p>
  1. Use Remote Desktop to connect to the Windows VM
<p>
1. Mac users must install "Microsoft Remote Desktop" whereas Windows users need to search "Remote Desktop Connection" in their computer search bar. In azure, go to virtual machine, and select the windows virtual machine we made in a previous step; in the information listed, find and copy the public ip address. paste this IP address into the Remote desktop connection for "computer" or "pc name." If it then shows your personal name, select "more choices" "use a different account" and use the username and password that you used to create the VMs. Decline all the setup offers it makes to you. Congrats! You're on the VM you made! 
</p>
2. Install WireShark, a protocol analyzer aka a packet sniffer, to visualize network traffic
<p>
  <img src="https://github.com/user-attachments/assets/228f4e4e-6996-4216-a9fc-cc0c903b78c7" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p>
2. On the Windows VM, open a brower tab, search "www.wireshark.org", select "download," then click the x64 installer. Once installed, open the fiile. selecct "yes" and "noted" through the installation process, making sure the "install Npcap" is selected when the page presents during the installation; USB cap is not needed at this time. select "agree" without selecting any of the 3 boxes. select "install," "next," and "finish." Close the web browser and then in the Windows VM Windows search bar, search and select "wireshark." 
</p>
In wireshark, select "ethernet," and then click the shark fin icon below "file" in the upper left. These constantly changing numbers are all of network traffic happening on the backend of the VM, more specifically, the numbers are different packets going to and from the VM.

<p>
  3. Filter for ICMP traffic. The picture belows shows ping executed using ICMP, confirming a connection between the 2 VMs created. 

  <img src="https://github.com/user-attachments/assets/6025a801-4619-4587-b9f8-c2e2838efc09" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <p>
    <p>
3. Recall the ping uses ICMP to test connectivity between devices. Since there is constant traffic, filtering for ICMP makes it easier to see this traffic in wireshark. So in the search bar above the running numbers, above the column heades, next to the bookmark icon, where it says "Apply a display filter," type "icmp" and hit enter so that we only see ICMP (ping) traffic.
</p>
Next retreive the private IP address of the Linux VM from azure and ping it from the Windows 10 VM power shell by typing ping followed by the linux VM private IP address. Notice is wireshark that there are requests and replies.
<p>
4. Looking Deeper
</p>
<br />


  <img src="https://github.com/user-attachments/assets/6e4ab849-0958-4139-9ccd-aebec5887f78" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
4.Expanding "Ethernet II" shows source and destination MAC addresses, layer 2 addressing in the OSI Model. The VM appears to be uniquely sequential, seeing as the manufacturer cannot burn a MAC address onto software. 
<p>
Expanding "Internet Protocol" shows source and destination private IP addresses, the network layer 3 in the OSI model
</p>
Expanding "Internet Control Message Protocol," ICMP, can even show you the payload of the ping, including the data sent and how many bytes it was.
</p>
5. In summary, Use the Windows public IP to sign into Remote Desktop>Use wireshark to filter ICMP>retreive Linux private IP address> Open Windows VM powershell then type ping follwed by the Linux VM private IP> if wireshark shows requests and replies, the two devices are connected
<br />

<h2>Configure a Firewall (Network Security Group) Steps</h2>
<p>
  
</p>
<img src="https://github.com/user-attachments/assets/5c4f3a0b-97ad-43fc-a503-e97dba283447" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
linux network security group
</p>
</p>
<img src="https://github.com/user-attachments/assets/b5e1ee94-d49c-428c-93d8-33da9924f7e4" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
make icmp blocking rule
</p>
</p>
<img src="https://github.com/user-attachments/assets/c4567250-ee2f-4a1e-9c77-35949a0083f8" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
changes from reply request in wireshark to requests only. poershell requests time out bc linux vm network security group block
</p>
</p>


pt 3
</p>
<img src="https://github.com/user-attachments/assets/68c16097-7186-4e91-928a-3a442557fdf2" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
connected to linux vm via ssh for admining their comp
</p>
</p>
<img src="https://github.com/user-attachments/assets/84e2808d-ce62-4255-8054-ef345d651f64" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
hmmm
</p>
</p>
<img src="https://github.com/user-attachments/assets/3875084e-11be-4fa0-842f-74e1547a740c" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
workaround to show dhscp steps using a file
</p>
---
dns


