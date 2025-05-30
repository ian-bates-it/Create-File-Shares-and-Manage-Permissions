<p align="center">
<img src="https://github.com/user-attachments/assets/2f544d38-0a3f-492d-8528-369cc98ee75a" alt="Microsoft Active Directory Logo"/>
</p>

# Create File Shares and Manage Permissions

**Overview**
- On the Windows 2022 Server Domain Controller we will create four directories on the C Drive.
    - `read-access` which will only give our `Domain Users` **read** permissions.
    - `write-access` which will only give our `Domain Users` **read/write** permissions.
    - `no-access` which will only give ONLY our `Domain Admins` **read/write** permissions. (NOT our `Domain Users`).
    - `accountants` which will only give users who are members of the `ACCOUNTING` security group **read/write** permissions.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Users and Computers

<h2>Operating Systems Used </h2>

- Windows Server 2022 Datacenter Azure edition (Domain Controller)

<!--
- Windows 10 Pro (21H2) (Client)
Add confirmation on client system later
-->

<h2>High-Level Configuration Steps</h2>

- Part 1: [Create File Shares on our Windows 2022 Server Domain Controller](https://github.com/ian-bates-it/Create-File-Shares-and-Manage-Permissions?tab=readme-ov-file#create-file-shares-on-the-windows-2022-server-domain-controller)
- Part 2: [Setup Share Acces For A New `ACCOUNTING` Security Group](https://github.com/ian-bates-it/Create-File-Shares-and-Manage-Permissions?tab=readme-ov-file#accounting-directory-share-access)
- Part 3: [Add a Domain User to the `ACCOUNTING` Security Group](https://github.com/ian-bates-it/Create-File-Shares-and-Manage-Permissions?tab=readme-ov-file#add-a-user-to-the-accounting-security-group)


<h2>Prerequisites</h2>

1. Complete [Chapter 1 of Active Directory Home Lab series, Creating a Windows 10 Pro and Windows 2022 Server Virtual Machines in Azure.](https://github.com/ian-bates-it/Azure-Virtual-Machine-Setup)

2. Complete [Chapter 2 of the Active Directory Home Lab series, Configuring the Windows 10 Pro (Client) to use the static private IP of our Windows 2022 Server Domain Controller as its DNS Server.](https://github.com/ian-bates-it/Azure-Controller-Client-Configuration)

3. Complete [Chapter 3 of the Active Directory Home Lab series, Installing Active Directory on a Windows 2022 Server VM and promoting it to a Domain Controller.](https://github.com/ian-bates-it/Install-Active-Directory-on-Windows-2022-Server)

<!--
4. Complete [Chapter 4 of the Active Directory Home Lab series, Create Organizational Units and Users in Active Directory.](https://github.com/ian-bates-it/Active-Directory-Users-And-Computers)
-->

4. Complete [Chapter 5 of the Active Directory Home Lab series, Joining a Windows 10 Pro Client to a Windows 2022 Server Domain Controller.](https://github.com/ian-bates-it/Join-A-Client-To-A-Domain)

5. Complete [Chapter 6 of the Active Directory Home Lab Series, Creating 100 Domain Users with a PowerShell Script.](https://github.com/ian-bates-it/Create-Active-Directory-Users-With-PowerShell-Script)


<br />
<br />

---


<br />
<br />

---

<h1>Part 1:</h1>

<h2>Create File Shares On The Windows 2022 Server Domain Controller</h2>

<h3>Log into the Windows 2022 Server Domain Controller</h3>


- Using Remote Desktop, log in with the public IP address for the Windows 2022 Server as shown below.

  <img src="https://github.com/user-attachments/assets/ffe9d33a-159b-4191-b8c6-213463f36c78" height="70%" width="70%" />



---
<br />
<h3>Open File Explorer (WIN + E)</h3>

- Open the File Explorer with WIN + E or from the Start Charm as shown below.


  <img src="https://github.com/user-attachments/assets/d1d5a594-0563-400e-a3ae-abba504cdcac" height="60%" width="60%" />



---
<br />
<h3>Navigate to Windows (C:) Drive</h3>

- Navigate to `This PC` > `Windows (C:)` drive as shown below.

    <img src="https://github.com/user-attachments/assets/3969965a-9775-43a5-bc69-79754883d56f" height="50%" width="50%" />




---
<br />
<h3>Create Four New Directories on the C Drive</h3>

- We are going to create four directories, `read-access`, `write-access`, `no-access` and `accountants`.

1. Right-click the C Drive
2. Select `New`
3. Select `Folder` as shown below.

 <img src="https://github.com/user-attachments/assets/b18fb972-7da5-4219-a655-cdb6cf6f28a0" height="60%" width="60%" />


<h4>Name the folder and continue until there are four new directories for `read-access`, `write-access`, `no-access` and `accountants` as shown below.</h4>

   <img src="https://github.com/user-attachments/assets/955db602-59dc-4d52-b5df-89ffe086df80" height="60%" width="60%" />

<!--
  <img src="https://github.com/user-attachments/assets/156f075f-b6ab-4032-b93c-de372038617e" height="60%" width="60%" />
-->


---
<br />

<h3>Give `Domain Users` `read` Access To The `read-access` Directory</h3>


1. Right-click the `read-only` directory.
2. Select `Properties` as shown below.

  <img src="https://github.com/user-attachments/assets/4c5c3823-132e-4156-9cc6-8bd843162a3a" height="50%" width="50%" />

<br />
   
3. Select the `Sharing` tab.
4. Select the `Share` button as shown below.

  <img src="https://github.com/user-attachments/assets/3e4f8e1b-d122-4b2a-ab88-9b43a784093c" height="40%" width="40%" />

<br />


5. Type `Domain Users` in the text box.
6. Select the `Add` button as shown below.


  <img src="https://github.com/user-attachments/assets/1b6aa92e-2b65-4008-89f3-c89adf89519d" height="40%" width="40%" />

<br />

7. Our `Domain Users` will now have `read` access to the `read-access` directory. Select the `Share` button as shown below to complete this process.

  <img src="https://github.com/user-attachments/assets/fc95ed0a-2a54-46cb-a2e5-f19e8f6dc8fc" height="40%" width="40%" />


**Confirm with the `Done` button**

  <img src="https://github.com/user-attachments/assets/d9af8305-6d73-4893-a7b9-6beee8c4a86e" height="30%" width="30%" />



---
<br />

<h3>Give `Domain Users` `read/write` Access To The `write-access` Directory</h3>

- Duplicate steps **1 to 6** [described above](https://github.com/ian-bates-it/Create-File-Shares-and-Manage-Permissions/blob/main/README.md#give-domain-users-read-access-to-the-read-access-directory) for the `write-access` directory.
- After `Domain Users` have been added to the `Network Access` for the `write-access` directory, set the `Permission Level` to `Read/Write` as shown below.

  <img src="https://github.com/user-attachments/assets/a26618e6-0324-4037-8ff0-498e5339cd8d" height="40%" width="40%" />


**Confirm read/write access and close the Network Access window**

  <img src="https://github.com/user-attachments/assets/ab373528-9503-4fae-8760-5941ba4e0fb0" height="40%" width="40%" />



---
<br />

<h3>Give `Admin Users` `read/write` Access To The `no-access` Directory</h3>


- Duplicate steps **1 to 4** [described above](https://github.com/ian-bates-it/Create-File-Shares-and-Manage-Permissions/blob/main/README.md#give-domain-users-read-access-to-the-read-access-directory) for the `no-access` directory.
- Then add the `Domain Admins` group as outlined below.

<br />

5. Type `Domain Admins` in the text box.
6. Select the `Add` button as shown below.

  <img src="https://github.com/user-attachments/assets/4980ee07-03bb-4521-903a-4c3e54e2b224" height="40%" width="40%" />


<br />

7. Set the `Permission Level` to `Read/Write` as shown below.

  <img src="https://github.com/user-attachments/assets/05c20b06-d2f2-4f8e-b728-4643a54eb6a2" height="40%" width="40%" />


**Confirm the settings and close**


  <img src="https://github.com/user-attachments/assets/2cca064c-b0a6-40f6-b32b-35437c16197e" height="40%" width="40%" />



<!--

---
---
<br />


<h2>Verify the Share Permissions on a Windows 10 Pro Client VM</h2>



---
<br />

<h3>Log into the Windows 10 Pro Client VM</h3>

-->


<br />
<br />

---

<h1>Part 2:</h1>

<h2>Accounting Directory Share Access</h2>



---
<br />

<h3>Create A New OU for our `ACCOUNTING` Security Group</h3>

- In the Windows 2022 Server Domain Controller, open `Active Directory Users and Computers`

- To keep things organized, I elected to create another `Organizational Unit` to hold our new `Accounting` security group.
- Right-click the domain, select `New` and select `Organizational Unit` as shown below.

  <img src="https://github.com/user-attachments/assets/bc900ec3-9892-4e6e-9357-b762ab454b2c" height="60%" width="60%" />

---
<br />

- Name the new Organizational Unit and select `OK`
- Here, I named mine, `_DEPARTMENTS` as shown below


  <img src="https://github.com/user-attachments/assets/79a07334-6488-4bb3-a1ed-57def043e9ae" height="40%" width="40%" />


---
<br />

<h3>Create The `ACCOUNTING` Security Group</h3>

- You may need to refresh after creating the `_DEPARTMENTS` OU.
- Then follow the steps outlined below. 

1. Right-click the `_DEPARTMENTS` OU
2. Select `New`
3. Select `Group` as shown below


  <img src="https://github.com/user-attachments/assets/3699d7c3-8f89-4051-abfc-d0397780d8e0" height="50%" width="50%" />



<br />

<h3>Add Group Name For The `ACCOUNTING` Security Group</h3>

4. Add the desired `Group name`. In this example, our security group will be called `Accounting`.
5. Group scope is set to `Global`.
6. Group type is set to `Security`.
7. Select `OK` as shown below.


  <img src="https://github.com/user-attachments/assets/6c1b10b8-68f3-4555-8c54-3156519a2096" height="40%" width="40%" />

<br />

- Now our `_DEPARTMENTS` OU has an `Accounting` global Security Group as shown below.

  <img src="https://github.com/user-attachments/assets/d4a0b63f-de6f-4670-874f-fcda3028599f" height="40%" width="40%" />





---
<br />

<h3>Create a File Share named `accountants` for Security Group `ACCOUNTING` with `READ/WRITE` permissions </h3>

1. Right click the `accountants` folder.
2. Select `Properties`.
3. Under the `Sharing` tab, Select the `Share` button as shown below.

  <img src="https://github.com/user-attachments/assets/c242cf7d-d5ce-4aae-834a-4d05af2a0ca6" height="70%" width="70%" />

<br />
<br />

4. In the `Network access` tab type in the `ACCOUNTING` Security Group we previously added above
5. Change the `Permission Level` to from `Read` to `Read/Write`.
6. Click the `Share` button to confirm these changes as shown below. 

  <img src="https://github.com/user-attachments/assets/b75c2066-6418-4ce4-b273-3e39a1a00d43" height="60%" width="60%" />


<br />
<br />

7. Now our `accountants` folder is shared with `Read/Write` permissions to users in the `ACCOUNTING` security group as shown below in the confirmation window. Press the `Done` button to complete.

  <img src="https://github.com/user-attachments/assets/300f99be-5504-4f50-82b4-68e268bbfa2c" height="60%" width="60%" />



<br />
<br />

---

<h1>Part 2:</h1>

<h3>Add A User To the `ACCOUNTING` Security Group</h3>


1. Click on the `_DEPARTMENTS` Organizational Unit.
2. Double click the `ACCOUNTING` Security Group to view its properties.
3. Select the `Members` tab of the `ACCOUNTING` Security Group.
4. Click the `Add` button as shown below.


  <img src="https://github.com/user-attachments/assets/235bd905-a7a2-4933-8f29-571596f5bb05" height="60%" width="60%" />


<br />
<br />

- Using [one of the Active Directory Users we created with PowerShell in our `_EMPLOYEES` organizational unit at this link here](https://github.com/ian-bates-it/Create-Active-Directory-Users-With-PowerShell-Script?tab=readme-ov-file#create-100-active-directory-domain-users-with-powershell), we will add one of them to the `ACCOUNTING` Security Group.
- In this example, I selected user `austin.taylor`.

5. Type the name of the active directory user in the `Enter the object names to select` text field.
6. Select `Check Names` to make sure you have properly identified the user.
7. Then select the `OK` button to complete the process.

  <img src="https://github.com/user-attachments/assets/3553a243-db64-4fca-abcf-64638f032e90" height="70%" width="70%" />

<br />
<br />

8. Click `Apply`
9. Click `OK` to complete this process as shown below.

  <img src="https://github.com/user-attachments/assets/b98a13bc-3b41-4a77-8650-b8fba984ff36" height="70%" width="70%" />


---

---
<br />

<h3>Conclusion: Now only user `austin.taylor` has `Read/Write` access in the `ACCOUNTING` Security Group</h3>

- This completes the process. Our user `austin.taylor` has `Read/Write` access to the `accountants` file share as a member of our Active Directory `ACCOUNTING` Security Group. 

- You can confirm this by double-clicking the `ACCOUNTING` Security Group and selecting the `Members` tab.
- As shown below, Active Directory user `Austin.Taylor` is a member of our `ACCOUNTING` Security Group.

  <img src="https://github.com/user-attachments/assets/ad8f75d4-e8b1-49ce-b2b3-5189a6d4c241" height="80%" width="80%" />



---
<br />










