# Lab 5: Join Windows 10 to Domain (Local User), Group Policy, RSOP Reports

## Objective

In this home lab, we expand our Active Directory environment by deploying a second Windows 10 virtual machine (PC02) to simulate an employee workstation. This allows us to perform realistic Help Desk and System Administration tasks in a multi-client environment, including creating Organizational Units (OUs), managing Active Directory users, configuring and enforcing Group Policy Objects (GPOs), and joining a workstation to the SuccessCompany.com domain.

Throughout the lab, we configure password and account lockout policies, verify Group Policy settings, and validate domain connectivity using various Command Prompt utilities. These exercises closely mirror the day-to-day responsibilities of Help Desk Technicians and Junior System Administrators in an enterprise Windows environment.

## Steps

**1.** To create the virtual machine, open VMware Workstation and select File → New Virtual Machine. Name the virtual machine PC02, browse to and select the Windows 10 ISO from your Downloads folder, choose Choose custom Installation, we selected 30 gb of disk capacity, store virtual disk as a single file, we click on hardware setting and select 2 cpu and then click Finish to complete the virtual machine creation.

![Step 1](https://github.com/user-attachments/assets/ff30d71b-a04c-4c1c-b6ea-999e3ba5001e)

**2.** The process will be the same as we did for our other Windows 10 virtual machine for the Helpdesk account. Select Next → Install now → I don't have a product key.

Select Windows 10 Pro, then click Next → Custom: Install Windows only → Next.

![Step 2.1](https://github.com/user-attachments/assets/54806059-6041-41fa-b7f0-4bd0d9f9430f)

![Step 2](https://github.com/user-attachments/assets/2164a6cd-d798-4302-bf71-2a8bddd0b575)

**3.** Continue with the same configurations as before for the Windows 10 Helpdesk account. Select Personal Use, then enter User for the name and put a password that can be remembered for this project

![Step 3](https://github.com/user-attachments/assets/2835c9ef-979a-40a7-a55a-9c81bb05ec37)

**4.** Now that PC02 has been created, the next step is to create a user account that will be used to sign in to this computer. To do this, open your PC01 (Help Desk) virtual machine and log in using the HelpDesk account. Make sure that your Windows Server 2022 (DC01) virtual machine is running, as it hosts Active Directory Users and Computers (ADUC), which we will use to create and manage domain user accounts.

At this point, our home lab consists of three running virtual machines:

- DC01 – Windows Server 2022 (Domain Controller)
- PC01 – Windows 10 (Help Desk workstation)
- PC02 – Windows 10 (Employee workstation)

This setup allows us to simulate real-world Help Desk scenarios, such as creating user accounts, resetting passwords, unlocking accounts, and verifying that users can successfully sign in after their issues have been resolved.

![Step 4](https://github.com/user-attachments/assets/ec5e1e8c-e560-4eb0-a54a-0906ceca725b)

**5.** On the Windows 10 Help Desk computer, open **Active Directory Users and Computers**. Right-click the **SuccessCompany.com** domain, then select **New → Organizational Unit**.

Name the first Organizational Unit **HR** and click **OK**. Repeat the same steps to create a second Organizational Unit named **IT**.

Once completed, the **HR** and **IT** OUs should appear under the **SuccessCompany.com** domain. These Organizational Units will help us organize users and computers based on their departments and make it easier to apply department-specific Group Policies.

![Step 5](https://github.com/user-attachments/assets/be352fbc-44c6-4869-b626-1760dcf84ceb)

**6.** Next, we'll create a new user account in Active Directory. In Active Directory Users and Computers (ADUC), expand your domain, right-click the Hr Organizational unit container, and select New → User. Enter Gozi as both the first and last name, then set the User logon name to Gozi. Click Next, create a password for the account, and leave all the password options unchecked. Finally, click Next, then Finish to create the new domain user account. under the HR organization Unit

![Step 6](https://github.com/user-attachments/assets/4f6a4b1d-be38-4b82-beb0-bf54c9081b18)

**7.**
![Step 7](https://github.com/user-attachments/assets/560c6a37-7cc0-41cb-a54f-1faa3b73d261)

**8.** Now we can see the new user Gozi in the HR container.

![Step 8](https://github.com/user-attachments/assets/24dc5dd9-644e-4c0a-ad75-542736a4b273)

**9.** To verify the users' locations, enable 'Advanced Features' by selecting the 'View' tab at the top, then choosing 'Advanced Features'.

![Step 9](https://github.com/user-attachments/assets/af0fcfe3-f729-451b-8b83-45951fa2ba24)

**10.** Next, we'll locate the Gozi user account using Active Directory's search feature. In Active Directory Users and Computers, right-click the SuccessCompany.com domain and select Find.
In the Find Users, Contacts, and Groups window, set the search location to Entire Directory. Enter Gozi in the search box, then click Find Now. Once the Gozi user account appears in the results, double-click it to open its properties.
From the properties window, select the Object tab to view details such as the account's distinguished name, creation date, and location within Active Directory.

![Step 10](https://github.com/user-attachments/assets/11dbab5c-c7ba-4400-9e9b-9df885cc224a)

![Step 11](https://github.com/user-attachments/assets/f6e3d738-a7db-4169-8760-4e05e68f6dd7)

![Step 12](https://github.com/user-attachments/assets/04bbfdc3-ca59-49ba-91d6-63d364d97a9a)

**13.** In the Objects tab, you should see that Gozi is part of the HR organizational unit, listed as SimoTech.com/HR/Bob.

![Step 13](https://github.com/user-attachments/assets/8df1ec34-85ed-4269-bc50-7d5b6ca36965)

**14.** Let's navigate to Group Policy Management in Server Manager using our Helpdesk account. From there, go to "Tools" and select "Group Policy Management."

![Step 14](https://github.com/user-attachments/assets/d35b2ac2-8681-4c35-9b5b-d4e4611af13b)

**15.** This will display the group policy for our domain controller. Select "Domains" → "SuccessCompany.com" → "Default Domain", Next, go to "Settings" and click "Show All" in the top-right corner. you can click on save report if you want.

![Step 15](https://github.com/user-attachments/assets/d9dbea8b-a6e7-44ec-a8b8-6981b3e6e49d)

![Step 15.1](https://github.com/user-attachments/assets/cbfbc899-783c-4673-bcdf-f7feb2f7eae3)

**16.** This report offers a comprehensive view of various policies, including account policies, password policies, and account lockout policies. It is an invaluable tool for understanding the policies applied to a user. For instance, we can observe that the Account Lockout Policy is configured with a threshold of 0 invalid logon attempts. This setting poses a security risk, as it allows unlimited login attempts, making the system vulnerable to brute-force attacks.

![Step 16](https://github.com/user-attachments/assets/8175b44c-1fd0-4c01-b568-ccfb3dba1804)

**17.** To modify this policy, right-click on "Default Domain Policy" and select "Edit."

![Step 17](https://github.com/user-attachments/assets/0538435a-d8f7-432e-b9a3-281cc85be918)

**18.** Select "Policy," navigate to "Windows Settings," then to "Security Settings," and double-click on "Account Policies."

![Step 18](https://github.com/user-attachments/assets/d61f2a93-c8c9-4cbd-95c4-44d90333a1e7)

**19.** Double-click "Account lockout duration," enable the "Define this policy setting" option, and set it to 30 minutes.

![Step 19](https://github.com/user-attachments/assets/acf8f6a4-e7b9-4992-ad21-0d398946754d)

**20.**
![Step 20](https://github.com/user-attachments/assets/3cb12b31-5923-4cef-8779-7e257ef22c42)

**21.** Next, we'll configure the Password Policy for our domain. Open the Default Domain Policy, navigate to the Password Policy settings, and change the Maximum password age to 90 days.
Setting the maximum password age to 90 days requires users to change their passwords every three months. This helps improve security by reducing the amount of time a compromised password can be used.

![Step 21](https://github.com/user-attachments/assets/cf538530-6dce-4e72-8b08-736dc3bc6874)

**22.** After configuring the policies, let's enforce them by right-clicking on "Default Domain Policy" and selecting "Enforced."

![Step 22](https://github.com/user-attachments/assets/a3016e2c-27b6-420b-8840-d77d3a49925c)

**23.** To verify that the Group Policy settings have been applied successfully, open Server Manager and navigate to Tools → Group Policy Management. Expand your domain, right-click Default Domain Policy, and select Edit or generate a Group Policy Results report, depending on your lab instructions. Under the Settings tab, click Show All to display every configured policy. Review the report and confirm that the changes have been applied correctly, including a Maximum password age of 90 days, along with the Account lockout threshold and Account lockout duration values i configured earlier. Verifying these settings ensures that the domain is enforcing the password and account lockout policies as intended.

![Step 23](https://github.com/user-attachments/assets/622c6887-683b-4b11-8d0b-a81d2260c261)

**24.** Next, switch to the PC02 virtual machine and open File Explorer. Right-click This PC and select Properties. Click Rename this PC (Advanced), then select Change. Update the computer name to PC02, click OK, and accept the prompt to restart the computer. Restarting the system completes the rename and ensures the new computer name is applied before joining it to the domain.

![Step 24](https://github.com/user-attachments/assets/357a1e51-ac6b-4843-9ddc-947a72d1cd94)

**25.**
![Step 25](https://github.com/user-attachments/assets/c48f62ef-d585-4267-b97a-ac7a02af8fb4)

**26.** After the restart, let's enable the Administrator account. Open File Explorer, right-click on This PC, and select Manage. In the Computer Management window, navigate to Local Users and Groups → Users. Right-click on Administrator, select Properties, and uncheck "Disable account". Then click Apply and OK to enable the account.

![Step 26](https://github.com/user-attachments/assets/ca536538-aeda-423c-9868-fc034afabdfe)

**27.** Right-click on the Administrator account again and select Set Password. Enter the desired password for the account and confirm it. Then click OK to apply the changes.

![Step 27](https://github.com/user-attachments/assets/bdcf4f98-6714-4d7f-8365-6c98c496f102)

**28.** After that, sign out of the PC and log into the administrator.

![Step 28](https://github.com/user-attachments/assets/7bdf43d6-0b68-4557-94bb-a0b9537449b8)

**29.** Now we have to join the PC02 to the Successcompany.com domain. First we enable to Network adapters, one for Host Only, One for Nat for internet connection incase we want to download or update something from pc02, we do that by right clicking on the PC02 virtual machine, select "settings" and then click on "Add", select "Network adapter", make the first one "host only" and the second one "NAT"

![Step 29](https://github.com/user-attachments/assets/10dfa8a8-d957-4d5f-8e1b-9102aec559a0)

**30.** Next, open Control Panel and go to View Network Status and Tasks. On the Host only Network adapter, Click on Change adapter settings, then right-click on the Ethernet connection and select Properties.
Double-click on Internet Protocol Version 4 (TCP/IPv4), and configure the static IP settings tO align with the server as follows as follows:
- IP Address: 192.168.65.30
- Subnet Mask: 255.255.255.0
- Default Gateway:
- Preferred DNS Server: 192.168.65.10
- Alternate DNS Server:

![Step 30](https://github.com/user-attachments/assets/493dcbd7-18c5-4831-8c4e-9395677b3b30)

**31.** On the NAT network adapter, leave everything as it is "Obtain IP address automatically"

![Step 31](https://github.com/user-attachments/assets/9d613719-1ce6-4863-977c-12fe38dffaf2)

**32.** Now lets open Command Prompt and ping our domain, Successcompany.com .

![Step 32](https://github.com/user-attachments/assets/d333043b-0926-4094-9b4f-9181db2b1c05)

**33.** Successfully joined successcompany.com

![Step 33](https://github.com/user-attachments/assets/e51b3023-785f-49e0-b985-66fe745f39af)

**34.** Afterward, restart the Vmware. Once restarted, check Active Directory Users and Computers → Computers under our Server Computer. You should see that PC02 has been successfully added to our domain, Successcompany.com.

![Step 34](https://github.com/user-attachments/assets/5dc348b5-e987-4e40-89c4-2306aa12bd8d)

**35.** Now when our PC is finish restarting, lets log in as Gozi on our local user account PC02

![Step 35](https://github.com/user-attachments/assets/52ad909b-34c9-4b5b-a89b-240d8e133719)

**36.** Finally, we'll run a few command-line tests to verify that our lab environment is working correctly. First, use the ping SuccessCompany.com command to confirm that PC02 can successfully communicate with the domain controller. Next, run ipconfig to verify that the computer has the correct IP address, subnet mask, default gateway, and DNS server configured.

Lastly, use the "net user Gozi /domain" command to confirm that the Gozi domain account is accessible through Active Directory. If all of these commands return the expected results, we can confidently confirm that PC02 has been successfully joined to the domain and that communication with the Active Directory environment is functioning as expected.

![Step 36](https://github.com/user-attachments/assets/757bf019-be14-4c42-930e-ea6982a59faf)

**37.** Congratulations! We have successfully completed this home lab by joining PC02 to the SuccessCompany.com domain and verifying that it can communicate with our Active Directory environment. Along the way, we created and managed domain user accounts, configured and reviewed password and account lockout policies, and explored Group Policy Management to better understand how domain-wide settings are applied.

To validate our configuration, we used several Command Prompt (CMD) tools to test network connectivity, verify IP configuration, and confirm communication with the domain. We also generated Resultant Set of Policy (RSOP) reports to review the Group Policy settings that were applied to the computer and user accounts. By completing these tasks, we successfully simulated common Active Directory administration and Help Desk responsibilities in a realistic Windows enterprise environment
