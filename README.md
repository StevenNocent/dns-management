<p align="center">
<img src="https://static.wixstatic.com/media/2ebf04_ca1cd7d0964640f584a9cf257cf5c460~mv2.png" alt="DNS Management"/>
</p>

<h1>DNS Management of A-Records, CNAME Records and Local DNS Cache</h1>
This tutorial demonstrates how to create Domain Name System (DNS) A and CNAME Records. experiment with the local DNS cache within an Azure virtual machine (VM) that is running Active Directory.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: DNS Management of A-Records, CNAME Records and Local DNS Cache](https://youtu.be/KF1kglVWND4)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>
<p align="left"> Prerequisite Lab Prior To This Lab: <a href="https://github.com/stevennocent/configure-ad"
>Configuring On-premises Active Directory within Azure VMs</a></p>
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f70557f3029046b2969a62226a5cbe59~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
1. Remote desktop connection into virtual machine 2 running Windows 10 Pro, Version 21H2 from the Active Directory Lab.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_63ae497882d944d49830faae2f03aad9~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
2. Login as the admin user created from the Active Directory Lab.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_45d443faac9d44ff9de169517ba8eec5~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
3. Minimize VM2 and go back to the Azure Portal to get the IP address of virtual machine 1 running Windows Server 2022 and remote desktop connection into it.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cf57d7591a484ae8be626d22470129ee~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
4. Go back to virtual machine 2 and launch command prompt and attempt to ping keyframe.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_83c34d98baf94f77b4ec66f0742897ed~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
5. The ping request will fail because we don not have an A-Record for keyframe. Go back to the Domain Controller (VM1) → Server Manager → Tools → DNS.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_886a366090a54b2eb94c6a7f9c72c6cb~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
6. Click the Domain Controller from the DNS Manager → Forward lookup zones → Select the domain name chosen for root.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cf1eb3a1ffeb42c5a2f8010da171cd98~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
7. This is essentially where are A-Records are. Right-Click, the click New Host (A or AAAA) to create a new A-Record.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_fa7dd77e27a943fdb5eb91446d132de1~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
8. For the name type “keyframe” and type in virtual machine 1’s Private IP address as the IP address for keyframe and click Add Host.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_3b921b2deeb347ec92fb39bc398d9212~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f953aa8dbcd2436695921fb5f6ea142d~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_42c39a8729e74747a06b649ece83a9c3~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
9. Attempt to ping keyframe for VM2 from Command Prompt. Request will resolve for the IP address we assign to keyframe when creating an A-Record. The following commands will also display the DNS:
- nslookup keyframe
- ipconfig /displaydns
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_b1d26e273e3d44bfbc5e787f2b032641~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_af22ce2560734c94a64ddd9cd00f4cae~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
10. Go back to the Domain Controller and edit keyframe’s IP to 8.8.8.8 and observe changes in VM2 after flushing the DNS cache with the ipconfig /flush DNS command.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_7c68bd03f57949548190af92093369e0~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
11. Ping any name such as Kermit and observe how the request could not be resolved.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_2b88b24648b24cec99f19efbd811c3d4~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
12. Create a CNAME record for Kermit by going back to the domain controller, Right-Clicking → New Alias (CNAME).
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_d61935406a854cedaa6cf4260f63c00f~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
13. Type in Kermit or any name of your choice for Alias name and www.Google.com for the Fully qualified domain name (FQDN) for target host and click ok.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_67b20cae657b403aa5800f7ec2a4804c~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
14. Go to virtual machine 2 and attempt to ping Kermit once again. The request should resolve for www.Google.com. This demonstrates how we can map names or aliases such as Kermit to a true domain name.
</p>
<br />

<p align="center"><b><i>🙌💥People may hear your words, but they feel your attitude. ~ John C. Maxwell🙌💥</b></i></p>
