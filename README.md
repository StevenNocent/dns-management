<p align="center">
<img src="https://static.wixstatic.com/media/2ebf04_ca1cd7d0964640f584a9cf257cf5c460~mv2.png" alt="DNS Management"/>
</p>

<h1>DNS Management of A-Records, CNAME Records and Local DNS Cache</h1>
This tutorial provides step-by-step instructions on how to create A and CNAME DNS records, as well as experiment with the local DNS cache within an Azure virtual machine (VM) that is running Active Directory.<br />

<h2>Video Demonstration</h2>

- ### [YouTube: DNS Management of A-Records, CNAME Records and Local DNS Cache](https://youtu.be/KF1kglVWND4)

[![YouTube](https://static.wixstatic.com/media/2ebf04_597db4dd83f14d68b5be79644bccd4f9~mv2.png)](https://youtu.be/KF1kglVWND4)
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Command Prompt
- Windows Server Manager

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Steps</h2>

- Deploy virtual machine 2: Remote desktop connect into virtual machine 2 from the Active Directory tutorial, which is running Windows 10 Pro Version 21H2.
- Ping two random host names: Open Command Prompt and attempt to ping the host names "Keyframe" and "Kermit". The ping requests will fail, as the hosts do not exist.
- Create DNS records: Successfully ping both host names by navigating to the DNS Manager within Server Manager. Then, create a DNS A-Record for "Keyframe" and a CNAME record for "Kermit."
- Flush DNS cache: Use the "ipconfig /flushdns" command to clear the contents of the local DNS cache. This cache stores information about recently resolved DNS queries, including the IP addresses of websites that have been visited.

<h2>Actions and Observations</h2>
<p align="left">Previous Tutorial in Sequence: <a href="https://github.com/stevennocent/configure-ad"
>Configuring On-Premises Active Directory within Azure VMs</a></p>
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f70557f3029046b2969a62226a5cbe59~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 1: Connect to Virtual Machine 2 running Windows 10 Pro, Version 21H2 from the Active Directory Lab using Remote Desktop Connection.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_63ae497882d944d49830faae2f03aad9~mv2.png" height="40%" width="40%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 2: Log in using the admin user created from the Active Directory Lab.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_45d443faac9d44ff9de169517ba8eec5~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 3: Minimize VM2 and return to the Azure Portal to retrieve the IP address of virtual machine 1, which is running Windows Server 2022. Remote desktop connection into it as well.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cf57d7591a484ae8be626d22470129ee~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 4: Return to virtual machine 2, launch the command prompt, and try to ping "keyframe".
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_83c34d98baf94f77b4ec66f0742897ed~mv2.png" height="80%" width="80%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 5: Since we don't have an A-Record for keyframe, the ping request will fail. To fix this, go back to the Domain Controller (VM1) and open Server Manager, then navigate to Tools and select DNS.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_886a366090a54b2eb94c6a7f9c72c6cb~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 6: In the DNS Manager, select the Domain Controller from the Forward lookup zones and choose the domain name selected for the root.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_cf1eb3a1ffeb42c5a2f8010da171cd98~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 7: This is where the A-Records are stored. Right-click and select "New Host (A or AAAA)" to create a new A-Record.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_fa7dd77e27a943fdb5eb91446d132de1~mv2.png" height="30%" width="30%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 8: Type "keyframe" for the name and enter virtual machine 1's Private IP address as the IP address for keyframe. Click "Add Host" to create a new A-Record.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_3b921b2deeb347ec92fb39bc398d9212~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_f953aa8dbcd2436695921fb5f6ea142d~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_42c39a8729e74747a06b649ece83a9c3~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 9: Try pinging "keyframe" from Command Prompt in VM2. The request will be resolved for the IP address assigned to "keyframe" during the creation of the A-Record. The following commands can also display the DNS:
<ul>
  <li>nslookup keyframe</li>
  <li>ipconfig /displaydns</li>
 </ul>
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_b1d26e273e3d44bfbc5e787f2b032641~mv2.png" height="35%" width="35%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_af22ce2560734c94a64ddd9cd00f4cae~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 10: Return to the Domain Controller and modify the IP address of keyframe to 8.8.8.8. Then, flush the DNS cache with the command "ipconfig /flushdns" and observe any changes in VM2.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_7c68bd03f57949548190af92093369e0~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 11: Attempt to ping a name, such as "Kermit," and observe how the request cannot be resolved.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_2b88b24648b24cec99f19efbd811c3d4~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 12: To create a CNAME record for "Kermit," return to the Domain Controller, right-click and select "New Alias (CNAME)."
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_d61935406a854cedaa6cf4260f63c00f~mv2.png" height="35%" width="35%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 13: Enter a name of your choice such as Kermit for the Alias name, and www.google.com for the Fully Qualified Domain Name (FQDN) for target host and click "OK" to create a CNAME record.
</p>
<br />

<p>
<p align="center"> 
<img src="https://static.wixstatic.com/media/2ebf04_67b20cae657b403aa5800f7ec2a4804c~mv2.png" height="60%" width="60%" alt="DNS Management of A-Records, CNMAE Records and Local DNS Cache"/>
</p>
<p>
Step 14: Go to Virtual Machine 2 and try to ping Kermit again. The request should resolve for www.google.com, demonstrating how names or aliases such as Kermit can be mapped to a true domain name.
</p>
<br />

<p align="center">🚶🏾 <b><i>The journey with a 1000 miles begins with one step. ~ Confucius</b></i> 🗻</p>
