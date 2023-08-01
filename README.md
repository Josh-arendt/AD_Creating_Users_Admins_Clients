# AD_Creating_Users_Admins_Clients 
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating Users, Admins, and Clients for Active Directory</h1>
A step-by-step tutorial which outlines the process of adding users to Active Directory, assigning Domain Admins, and adding a client PC to the server domain. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Services
- Personal Computer


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Broad Concepts </h2>

- Step 1 Create Active Directory Users.
- Step 2 Assign a user to the Domain Admins security group.
- Step 3 Add a Client PC to the server domain.
- Step 4 Allow users to access the domain via the client PC.

<h2>Detalied Deployment and Configuration Steps</h2>

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/18fa74a0-4bae-48b8-9f64-8772faefd935)
 
</p>
<p>
Inside the domain controller, open "Active Directory Users and Computers."
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/8408dc97-f5b1-469b-b451-6e38ef29417a)
 
</p>
<p>
Find the directory for your domain ("mydomain.com" for this example). Once inside the directory, right click, select "new", and select "Organizational Unit" (OU) and name it "_EMPLOYEES." Create another OU and name it "_ADMINS." 
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/c972fb52-9960-40c5-af9a-1975c53913bc)

</p>
<p>
Inside the "_ADMINS" folder, right click and select "new" and select "user." Name the user (John Doe for this example). Next, we are going to assign John Doe to Domain Admin. 
To do this, right click John Doe and select "Add to a group."
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/dc1a79f9-9f5e-46db-89ad-e9a2b3802bb1)

</p>
<p>
Type "Domain Admins" in the text box. Click "Okay."
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/957054ce-710f-4e1e-9b08-31dd56acf16f)

</p>
<p>
Now you should be able to access the domain controller as an admin. To test this, log out of the domain controller and log back in as your newly created admin. 
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/75b38429-1e4a-47a0-9183-3f02f49277fd)

</p>
<p>
At this point, we are going to add a client PC to our domain. Since our client PC is set up as an Azure VM, find the virtual NIC for the client PC. 
We will need to change it's DNS server to the private IP of our domain controller. (10.0.0.4 for this example) 
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/2d2d4549-dc72-47c3-87fc-12733bd82010)

</p>
<p>
After changing the DNS server, restart the client VM.  
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/3a2b4bfd-d6f7-43fb-9c30-c6e613121f83)

</p>
<p>
Once the VM has restarted, log back in to the client PC.  
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/9b02f2ad-a480-4302-b647-71b06568ee24)

</p>
<p>
After you have logged in, right-click the Windows icon and select "System."  
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/2cde5cc0-3dd6-45f8-b212-ecff79608f60)

</p>
<p>
Look on the right hand side and select "Rename this PC (Advanced)." Select "Change." 
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/e7de167d-8dcb-4948-b39b-7f3e9088fb60)

</p>
<p>
Type in the name of your domain. (mydomain.com for this example) Select "Okay." 
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/f8995b38-258a-403e-967f-4d0f4d28229c)

</p>
<p>
Enter the user name and password of an account with permisson to join the domain.  
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/78cf43af-8139-43f5-999d-f5203972abcb)

</p>
<p>
Restart the Client VM.   
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/adab8af2-2fa5-486b-859d-55b2b52d866b)

</p>
<p>
Back on the domain controller, check to see if the client PC has been added to the "Computers" folder.    
<br />

<p>
  
  ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/658aba46-256f-4d3e-926c-9c0d24b9680f)

</p>
<p>
For extra organizational practice, create a folder named "_CLIENTS" in the domain directory. Add the client PC to that folder.     
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/b495b11a-2986-4429-a48e-31a5ac950d79)

</p>
<p>
The last step we need to configure is allowing users to log in to the domain via the client PC. To start, log into the client PC as the domain admin.       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/dd5f5d41-2e12-4b83-8b79-ed18a540a340)

</p>
<p>
Right click the Windows icon, select "System."       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/61d0b0f5-234d-4332-8980-bb0ef5162084)

</p>
<p>
Select "Remote Desktop."       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/3dd082b1-37a3-4018-9961-e5cf032fbed3)

</p>
<p>
Select "Select users that can remotely access this PC."       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/ee2a6513-2f24-4dbd-bb6c-7df05359a52a)

</p>
<p>
Select "Add."       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/0e3687b3-de62-4324-9454-9c09be8ec89c)

</p>
<p>
In the text field, tyep "Domain Users." Select "Okay."       
<br />

<p>
  
 ![image](https://github.com/Josh-arendt/AD_Creating_Users_Admins_Clients/assets/140751318/d2f54895-7b76-46f7-b97d-61e30ad0d740)

</p>
<p>
Select "okay." Congratualtions!!! Now any domain user can log in to the client PC.      
<br />
