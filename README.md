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

  - From the previous lab, use your chosen User and log in to Client-1 with a <b>bad password</b> 5-6 times
  - This will result into that account being locked out

![image](https://github.com/user-attachments/assets/1ae32c2c-b51e-454d-a701-2f3a7d450317)

![image](https://github.com/user-attachments/assets/e806781e-12eb-42fa-9a76-f5c79d37b90c)

![image](https://github.com/user-attachments/assets/9c051bf3-4e03-45e5-b90a-a524e2f7e967)

<br />

<h4>Unlock the account within the Domain Controller</h4>

  - Log in to DC-1 as admin account (Jane)

![image](https://github.com/user-attachments/assets/9e579d20-48a6-4c8a-9f31-42e21b86dd10)

![image](https://github.com/user-attachments/assets/1bce3c94-9da0-4e9b-879f-feb21ff2de73)

![image](https://github.com/user-attachments/assets/ef65ec6e-44c5-4e22-9455-617994a8ee04)

  - Go to Active Directory Users and Computers

![image](https://github.com/user-attachments/assets/a73f20b9-b068-43f7-9101-963f08f98ba5)

  - Within ADUC, click _EMPLOYEES and look for the account -> once found, right click and select Properties

![image](https://github.com/user-attachments/assets/f536b85e-f8fe-44e9-ad91-a060f7e2235d)

  - Click Account -> click checkbox Unlock account -> click Apply -> Click OK

![image](https://github.com/user-attachments/assets/3e94f9ec-22d9-4ed5-91dc-03bd1f838682)

<br />

<h4>Reset the account's password</h4>

  - Right click on the same account -> click Reset Password

![image](https://github.com/user-attachments/assets/4be3672f-513c-4d67-9eec-34dac89f2593)

  - Fill new password -> click Unlock Account -> click OK

![image](https://github.com/user-attachments/assets/48b17b1a-ee20-40d7-a10f-9bbb1850892f)

![image](https://github.com/user-attachments/assets/f8cd373e-6dc9-40ec-88c4-6d5e173ffd1f)

<br />

<h4>Attempt to log in to Client-1 with the unlocked account</h4>

![image](https://github.com/user-attachments/assets/f03cf8f7-8ce0-4acf-a3c3-8574afdb1e3d)

![image](https://github.com/user-attachments/assets/464943ad-97e5-4a4a-9388-b7e57040dd77)

![image](https://github.com/user-attachments/assets/f4c0d979-a7d3-47bf-b4f4-fef0fcfb6991)

![image](https://github.com/user-attachments/assets/dea9ead1-eda7-4104-9952-2f3fbcff6502)

<br />

<h3>Enabling and Disabling Accounts</h3>

<h4>Disable the same account in Active Directory</h4>

  - Log in to DC-1 as admin account (Jane)

![image](https://github.com/user-attachments/assets/9e579d20-48a6-4c8a-9f31-42e21b86dd10)

![image](https://github.com/user-attachments/assets/1bce3c94-9da0-4e9b-879f-feb21ff2de73)

![image](https://github.com/user-attachments/assets/ef65ec6e-44c5-4e22-9455-617994a8ee04)

  - Go to Active Directory Users and Computers

![image](https://github.com/user-attachments/assets/a73f20b9-b068-43f7-9101-963f08f98ba5)

  - Click _EMPLOYEES and look for the same account -> right click on account -> click Disable Account

![image](https://github.com/user-attachments/assets/9d39a3e8-3f99-46dd-a4e5-54755f9aadac)

  - Click OK

![image](https://github.com/user-attachments/assets/f58dc1e6-7a06-4371-a2bc-a0466579f271)

  - Attempt to log in to Client-1 with it and observe the error message

![image](https://github.com/user-attachments/assets/59b152d4-1551-42f5-8734-da994aed12f6)

![image](https://github.com/user-attachments/assets/278220f1-ce52-4010-a9ad-cfc129c197a5)

![image](https://github.com/user-attachments/assets/712053f5-a18a-455a-9088-0ab1de285935)

<h4>Re-enable the account and attempt to login</h4>

  - Go back to DC-1, 

-----------------------------------------------------





Observing Logs
Observe the logs in the Domain Controller
Observe the logs on the client Machine
Precursor to cybersecurity and security operations: joshmadakor.tech/cyber
