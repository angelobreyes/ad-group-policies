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

<h3>Configuring Account Lockout Policy</h3>

  - Log in to DC-1 using admin account (Jane)

![image](https://github.com/user-attachments/assets/4f3ba5ff-07f5-4937-b144-310e82ab2653)

![image](https://github.com/user-attachments/assets/21cdd377-a807-419e-8a8f-458c1658396f)

![image](https://github.com/user-attachments/assets/18b50c8b-00fe-4006-95b9-f10a69b43047)

  - Within DC-1, type gpmc.msc on the search bar and click gpmc.msc

![image](https://github.com/user-attachments/assets/11bfdda4-54ea-455f-80a7-c67cf874ba41)

  - Within Group Policy Management, expand the following:
      
  - Forest -> Domains -> mydomain.com -> right click Default Domain Policy -> click Edit

![image](https://github.com/user-attachments/assets/1e358db9-820f-43f2-8b5c-6cdd931e06b9)

  - Expand the following:
  - Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Click Account Lockout Policy

![image](https://github.com/user-attachments/assets/b3ef200d-9538-4816-b17c-7f2844238041)

<br />

<h4>There are 3 primary settings that you need to configure:</h4>
  
  - <b>Account Lockout Duration</b>: The time in minutes that an account remains locked before it is automatically unlocked.

  - Right click Account lockout duration -> Properties 

![image](https://github.com/user-attachments/assets/c0ac9157-625b-4e37-8531-44dbb8c7ba15)

  - Click checkbox -> Set time -> Click Apply -> Click OK -> Click OK

![image](https://github.com/user-attachments/assets/f1756fe1-d526-4b84-8418-6bafa8670c4f)

![image](https://github.com/user-attachments/assets/5a19394a-b7ac-421a-a577-35007276dfff)

![image](https://github.com/user-attachments/assets/c723bdbc-b58f-4e0b-b271-b964c3c7091f)

<br />

  - <b>Account Lockout Threshold</b>: The number of failed logon attempts that will trigger an account lockout.
      - This is automatically set but you can change it the same way

  - <b>Reset Account Lockout Counter After</b>: The time in minutes after which the failed logon attempts counter is reset to 0, assuming there are no additional failed logon attempts.
      - This is automatically set but you can change it the same way

<br />

  - Go back to Group Policy Management -> Click Default Domain Policy -> Click Settings -> Scroll down
  - You can see the policy is now in place

![image](https://github.com/user-attachments/assets/10aa7ed5-1861-43ea-b0a6-973ba1223e69)

<h4>Enforce Group Policy</h4>

  - Log in to Client-1 using admin account (Jane)

![image](https://github.com/user-attachments/assets/d56a0907-571b-43db-9c5e-236cdc532ce5)

![image](https://github.com/user-attachments/assets/6339a3fe-d9ee-4c00-afe9-d1257a2218dd)

![image](https://github.com/user-attachments/assets/76eae0a2-afcd-481e-b165-2cead0082b15)

  - Within Client-1, type command in search box and click Command Prompt

![image](https://github.com/user-attachments/assets/484016eb-0a86-40e1-b5fc-882f80a53d35)

  - Within Command Prompt, type gpupdate /force and press Enter

![image](https://github.com/user-attachments/assets/2978eec7-bcd8-4e2f-9203-ca29b0c662ad)

![image](https://github.com/user-attachments/assets/53bd62b3-c5fe-4150-8c5f-dc430f6dba2c)

  - Log out of Client-1

![image](https://github.com/user-attachments/assets/905e54b0-7f18-4392-bd1f-114a144f9613)

<br />

<h3>Dealing with Account Lockouts</h3>

<h4>Log in to Client-1</h4>

  - From the previous lab, use your chosen User and log in to Client-1 with a <b>bad password</b> 10 times
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
