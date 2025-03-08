<p align="center">
<img src="[https://logos-world.net/wp-content/uploads/2021/02/Microsoft-Azure-Symbol.png]" alt="Azure logo"/>
</p>

<h1>Azure Computing and Networking</h1>
This tutorial outlines how to create Virtual Networks and Subnets, Virtual Machines, and Network Security Groups.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Create A Virtual Machine And Use It](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
  - Virtual Machines (Windows and Linux[Ubuntu])
  - Azure Network Security Groups (Firewall Resource)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Linux (Ubuntu)

<h2>List of Prerequisites</h2>

- Azure Account
- Item 2
- Item 3
- Item 4
- Item 5

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

<h2>Use Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
