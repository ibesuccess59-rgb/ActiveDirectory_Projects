## Lab 3: Creating a Help Desk Account in Active Directory Using CMD

# Objectives

By the end of this lab, I will be able to:

* Enable the Active Directory Recycle Bin.
* Create a dedicated Help Desk account.
* Create a Help Desk security group.
* Delegate password reset permissions.
* Verify Active Directory objects using Command Prompt.
* Perform common Help Desk administrative tasks.


## Documentation

1.  Before creating the Help Desk account, enable the Active Directory Recycle Bin. This feature allows administrators to restore accidentally deleted Active Directory objects, such as users, groups, and organizational units, without performing an authoritative restore from backup.

This matters because one can Accidentally deleting a user account is a common administrative mistake. The Recycle Bin allows Help Desk and system administrators to recover deleted objects quickly while preserving their attributes, group memberships, and permissions.

1.2  Search for **Active Directory Administrative Center**.

<img width="1040" height="780" alt="1 2" src="https://github.com/user-attachments/assets/a2f782cf-0ad4-4bd2-a9d2-4656dde8f84c" />

1.3   Open the application.

1.4   Select your domain

<img width="1052" height="798" alt="1 4" src="https://github.com/user-attachments/assets/f91117e0-3f84-49b1-8016-ad3d467f68ed" />

1.5  In the **Tasks** pane, click **Enable Recycle Bin**.

<img width="1030" height="736" alt="1 5" src="https://github.com/user-attachments/assets/a9b85742-72b8-491f-b95c-3e712d3b46e2" />

1.6  Click **OK** to confirm.

<img width="1042" height="770" alt="1 6" src="https://github.com/user-attachments/assets/eeb59777-0e0d-4fcb-bfaf-d412b93e8bd9" />

**Note:** Once enabled, the Active Directory Recycle Bin cannot be disabled.

2. This next step is to Create an Organizational Unit for IT Administration,We would Create a dedicated Organizational Unit (OU) to store Help Desk and IT administrative accounts.

Organizational Units help organize Active Directory objects and allow administrators to apply permissions and Group Policies to specific departments without affecting the rest of the organization.

2.1  Open **Active Directory Users and Computers**.

<img width="1050" height="782" alt="2 1" src="https://github.com/user-attachments/assets/47a829d0-4d40-4c5b-b617-e7fc96411e2a" />

2.2  Right-click your domain.

2.3  Select **New → Organizational Unit**.

<img width="1056" height="782" alt="2 3" src="https://github.com/user-attachments/assets/84b8198c-853c-48b3-909c-ee9058b8c6a4" />

2.4  Name it: **IT-Administration**

<img width="1054" height="786" alt="2 4" src="https://github.com/user-attachments/assets/1fba4eaf-3d0c-4338-a392-049774172971" />

3.1  In this step we would Create the Help Desk Account under the IT-Administration Organizational unit. Rather than using a Domain Administrator account for everyday support tasks, organizations create Help Desk accounts with only the permissions necessary to perform assigned duties. This follows the **Principle of Least Privilege**, reducing security risks.


<img width="1042" height="768" alt="3 1" src="https://github.com/user-attachments/assets/1f9e46fe-1996-451d-8947-cea3ca05e9f7" />

3.2  Right-click inside the OU.

<img width="1086" height="828" alt="3 2" src="https://github.com/user-attachments/assets/1d9f3a6b-a52d-4409-b092-28f3def07d83" />

3.3  Select **New → User**.

<img width="1056" height="786" alt="3 3" src="https://github.com/user-attachments/assets/143b1592-4085-4b84-a254-7d451f29419a" />

3.4  Enter:

| Field           | Value      |
| --------------- | ---------- |
| First Name      | Help       |
| Last Name       | Desk       |
| User Logon Name | Helpdesk01 |

3.5  Click **Next**.

<img width="1042" height="784" alt="3 5" src="https://github.com/user-attachments/assets/c63b2894-5c52-48ba-b736-a39ec85049e9" />

3.6 Create a temporary password.

<img width="1054" height="802" alt="3 6" src="https://github.com/user-attachments/assets/7f657217-ccad-4f17-83f0-1f74d5a09c8b" />

3.7 Select:

* User must change password at next logon *

  <img width="1054" height="802" alt="3 7" src="https://github.com/user-attachments/assets/66dc5324-6d33-4208-bbde-8310045956f8" />

3.8 Click **Finish**.

<img width="1114" height="798" alt="3 8" src="https://github.com/user-attachments/assets/993d861a-f42d-4c8c-b390-80598972e2cd" />

3.8 (1) A new Help Desk account named **helpdesk01** appears in the OU.

<img width="1052" height="786" alt="3 8 1" src="https://github.com/user-attachments/assets/fe53ea35-45a6-489b-89c5-9d413ea0af28" />

4.0 Creating the HelpDesk-Technicians Security Group

In this lab, I created a **HelpDesk-Technicians** security group and added my Help Desk user account as a member. Using security groups instead of assigning permissions directly to users follows Active Directory best practices and makes permission management easier.

4.1  Open **Active Directory Users and Computers**. --> Right-click your domain.-->
-->Select **New → Organizational Unit** --> Name it **GroupOU** (or **Groups**).
<img width="1054" height="778" alt="4 1" src="https://github.com/user-attachments/assets/cd6daf61-b411-4c78-8189-aba154d46d49" />

4.2  Steps to Create the HelpDesk-Technicians Group
Right-click **GroupOU** --> Select **New → Group**.

<img width="1088" height="794" alt="4 2" src="https://github.com/user-attachments/assets/8109e861-1d38-4f61-a09c-9b967b7694d5" />

4.3 Click **OK**.

<img width="1038" height="804" alt="4 3" src="https://github.com/user-attachments/assets/733c5f8b-a852-41b5-8cb5-130aedc7d27a" />

<img width="1022" height="816" alt="4 3 (2)" src="https://github.com/user-attachments/assets/62adcaf1-07b9-4afd-9283-b146cc9d2be8" />

4.4 In this step we Add the Help Desk User , Open the HelpDesk-Technicians security group, navigate to the Members tab, click Add, select the helpdesk01 user account, and then click OK to add the user to the group.

<img width="1164" height="830" alt="4 4" src="https://github.com/user-attachments/assets/d0d277ac-ba91-4e94-b08f-8d7373ca41cb" />


<img width="1056" height="802" alt="4 4 (2)" src="https://github.com/user-attachments/assets/ad3b1dc4-8a8e-42b1-904d-cbf14c4a9b41" />

<img width="1052" height="794" alt="4 6" src="https://github.com/user-attachments/assets/237c1ea7-89dc-40d9-b3b6-9b68a81e623e" />

5.0  Delegate Password Reset Permissions

Objective
Allow Help Desk staff to reset user passwords without granting full Domain Administrator privileges.

Why This Matters
Help Desk technicians frequently reset passwords and unlock accounts. Delegating only the permissions they require improves security by limiting administrative access.

5.1  Right click on users OU and click on delegate

<img width="1022" height="778" alt="5 1 Right click on users OU and click on degate control" src="https://github.com/user-attachments/assets/78ab0a6b-c805-4abc-b41a-a20ac601bbbf" />

5.2  Click on add 

<img width="1020" height="728" alt="5 2 click on add " src="https://github.com/user-attachments/assets/02824fe5-7af5-4088-b2dc-6a9490fd480d" />

5.3 Type "Helpdesk-Technicians" ( A security group)

<img width="1048" height="792" alt="5 3 Type helpdesk-Technicians(A Security group)" src="https://github.com/user-attachments/assets/15516ecf-214a-40b2-bf77-cf1294360f55" />

5.4  Choose reset user passwords and force password change at next logon

<img width="1054" height="796" alt="5 4 Choose reset user passwords and force password change at next logon" src="https://github.com/user-attachments/assets/03734ad5-1976-40e7-ba89-b30b3bdf2ecd" />

5.5 Complete the wizard

<img width="926" height="640" alt="5 6 Complete the wizard" src="https://github.com/user-attachments/assets/7a5fd9d4-6cf8-4054-995f-0321f59e4f58" />

6.0  Verify the account using command prompt , The following commands Verify that the help desk account and security group were successfully created , Command line tools allow administrators to quickly verufy active directory objects and are commonly used in troubleshooting and automation

6.1 Open command prompt and run
net user helpdesk01 /domain

<img width="1344" height="1148" alt="6 1" src="https://github.com/user-attachments/assets/80b6c334-0c90-4a0f-85eb-7e2b2c3a8fe1" />

6.2 Run
net group "HelpDesk-Technicians" /domain

<img width="1338" height="1106" alt="6 2 Command to show help desk technicians" src="https://github.com/user-attachments/assets/a1cc7a6c-4d9c-4969-8f7e-2efc9e0cb279" />

## Conclusion

In this lab, I enabled the Active Directory Recycle Bin, created a Help Desk user and security group, delegated password reset permissions, and verified the configuration using Command Prompt. These tasks demonstrate core Active Directory administration and Help Desk best practices.

## Skills Acquired
-  Active Directory Users and Computers (ADUC)
-  Active Directory Administrative Center (ADAC)
-  Organizational Unit (OU) Management
-  User and Security Group Management
-  Permission Delegation
-  Principle of Least Privilege (PoLP)
-  Command Prompt Verification
-  Windows Server 2022 Administration
