<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory: Group Policies and Managing Accounts</h1>
Welcome! This tutorial outlines examples and implementation of Group Policies within Active Directory. 

*(This tutorial requires <a href ="https://github.com/angelobreyes/configure-ad">Active Directory within Azure virtual machines</a>, please check it out first if you haven't.)* 

<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows Server 2022 (Virtual Machine)
- Windows 10 (21H2) (Virtual Machine)

<h2>Overview</h2>

  - Configuring Account Lockout Policy
  - Dealing with Account Lockouts
  - Enabling and Disabling Accounts

<h2>Configuration Steps</h2>

<h3>Managing Account Lockout Policy</h3>

  - Log in to DC-1 using admin account (Jane)

![image](https://github.com/user-attachments/assets/4f3ba5ff-07f5-4937-b144-310e82ab2653)

![image](https://github.com/user-attachments/assets/21cdd377-a807-419e-8a8f-458c1658396f)

![image](https://github.com/user-attachments/assets/18b50c8b-00fe-4006-95b9-f10a69b43047)

  - Within DC-1, 



<h3>Dealing with Account Lockouts</h3>

<h4>Log in to Client-1</h4>

  - From the previous lab, use your chosen User and log in to DC-1 with a <b>bad password</b> 10 times
  - This will result into that account being locked out

![image](https://github.com/user-attachments/assets/1ae32c2c-b51e-454d-a701-2f3a7d450317)

![image](https://github.com/user-attachments/assets/e806781e-12eb-42fa-9a76-f5c79d37b90c)



-----------------------------------------------------
Dealing with Account Lockouts
Get logged into dc-1
Pick a random user account you created previously
Attempt to log in with it 10 times with a bad password

Configure Group Policy to Lockout the account after 5 attempts:
How To Configure Account Lockout Threshold in Group Policy

Attempt to log in with it 6 times with a bad password

Observe that the account has been locked out within Active Directory
Unlock the account
Reset the password
Attempt to login with it

Enabling and Disabling Accounts
Disable the same account in Active Directory
Attempt to login with it, observe the error message
Re-enable the account and attempt to login with it.

Observing Logs
Observe the logs in the Domain Controller
Observe the logs on the client Machine
Precursor to cybersecurity and security operations: joshmadakor.tech/cyber
