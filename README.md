# Create File Shares and Manage Permissions

---

<p align="center">
<img src="https://github.com/user-attachments/assets/2f544d38-0a3f-492d-8528-369cc98ee75a" alt="Microsoft Active Directory Logo"/>
</p>

---

**Overview**
- On the Windows 2022 Server Domain Controller we will create four directories on the C Drive.
    - `read-access` which will only give our `Domain Users` **read** permissions.
    - `write-access` which will only give our `Domain Users` **read/write** permissions.
    - `no-access` which will only give ONLY our `Domain Admins` **read/write** permissions. (NOT our `Domain Users`).
    - `accounting` which will only give users who are members of the `ACCOUNTING` security group **read/write** permissions.

---
---
<br />


<h2>Create File Shares On The Windows 2022 Server Domain Controller</h2>



---
<br />
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

- We are going to create four directories, `read-access`, `write-access`, `no-access` and `accounting`.

1. Right-click the C Drive
2. Select `New`
3. Select `Folder` as shown below.

  <img src="https://github.com/user-attachments/assets/b18fb972-7da5-4219-a655-cdb6cf6f28a0" height="60%" width="60%" />



<h4>Name the folder and continue until there are four new directories for `read-access`, `write-access`, `no-access` and `accounting` as shown below.</h4>

  <img src="https://github.com/user-attachments/assets/156f075f-b6ab-4032-b93c-de372038617e" height="60%" width="60%" />


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


---
---
<br />


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














