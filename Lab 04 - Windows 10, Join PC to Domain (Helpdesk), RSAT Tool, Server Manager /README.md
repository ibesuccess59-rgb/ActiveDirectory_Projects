## LAB 04 - Windows 10, Join PC to Domain (Helpdesk), RSAT Tool, Server Manager

## Overview

This section of my home lab demonstrates how to join a Windows 10 client to an Active Directory domain, install Remote Server Administration Tools (RSAT), and use Server Manager to remotely manage Windows Server resources. These tasks simulate common Help Desk responsibilities in an enterprise environment.

## Objectives

* Join a Windows 10 PC to the **SuccessCompany.com** domain.
* Install and configure RSAT on Windows 10.
* Use Server Manager to remotely manage server roles and features.
* Perform basic Active Directory administration from a client machine.

## Documentation

In this lab, I created a Windows 10 virtual machine and configured it with a local administrator account before joining it to the **SuccessCompany.com** domain. After the domain join was complete, I installed the Remote Server Administration Tools (RSAT) to enable remote management of Active Directory and other Windows Server roles. Finally, I used Server Manager to connect to the domain controller and perform common administrative tasks from the Windows 10 client, simulating a real-world Help Desk environment.

1. The process begins with downloading the Windows 10 Installation Media Tool from the official Microsoft website: Windows 10 Installation Media Tool.
<br />
<img width="1324" height="1258" alt="1" src="https://github.com/user-attachments/assets/fd67b7fc-0091-48c1-ad28-b33c8a96efb1" />
<br />

2. Open the media tool installer and click 'Accept.' Next, select 'Create installation media (USB flash drive, DVD, or ISO file) for another PC.' Save the download to your 'Downloads' folder, and you should be able to access it from the VirtualBox ISO.
<br />
<img width="1124" height="370" alt="2" src="https://github.com/user-attachments/assets/8ad537c0-336a-41f7-b4e9-3fbe2fe7b291" />
<br />
<br />

3. Next, open your VirtualBox application and create a new virtual machine. Click Machine in the top-left corner, then select New.
<br />
<img width="1420" height="1692" alt="3" src="https://github.com/user-attachments/assets/9c815a2b-af8d-40ba-a661-54f74f73bdcc" />
<br />

4. Name the virtual machine "Windows 10 Project." For the ISO image, navigate to the Downloads folder, click the dropdown icon, select "Other," and choose the "Windows" ISO file. Then, select "Skip unattended installation.”
<br />
<img width="1578" height="1096" alt="4" src="https://github.com/user-attachments/assets/b0429a79-c380-4c49-bf28-aed0c3d5b44b" />
<br />

5. Select Hardware, and by default, the base memory is set to 2048 MB. Increase it to 6081 MB. Finally, click Finish and start the machine by pressing Start. On the Windows Setup screen, click Next, then Install Now.
<br />
<img width="1082" height="806" alt="image" src="https://github.com/user-attachments/assets/49ac2018-46b4-4dea-b8b3-d90b7d497bdc" />
<br />

<img width="1086" height="790" alt="image" src="https://github.com/user-attachments/assets/dc8c636f-f51c-40be-ba6f-fc1315d897eb" />
<br />

6. Select “I don’t have a product key”.
<br />
<img width="1098" height="738" alt="image" src="https://github.com/user-attachments/assets/02674703-e409-44f1-a231-70f8d6c98869" />
<br />

7. Make sure to select "Windows 10 Pro," check the box to accept the license terms, and click Next.
<br />
<img width="1064" height="788" alt="image" src="https://github.com/user-attachments/assets/feafd780-4bf7-4cea-bf4f-3b23a7fe6d14" />
<br />

8. Select "Custom: Install Windows only," then click Next to begin the installation of Windows 10.
<br />
<img width="1090" height="806" alt="image" src="https://github.com/user-attachments/assets/6dfd2bc0-f158-485f-bd55-20bf692a8caf" />
<br />

9. <img width="1074" height="810" alt="image" src="https://github.com/user-attachments/assets/b0077ad8-e904-44c7-9f93-779e1118aecd" />
<br />

10. Select “Personal use”.
<img width="1148" height="838" alt="image" src="https://github.com/user-attachments/assets/4ac36cb1-7b55-4be1-ae43-89ec141cc61c" />
<br />

11. <br /> <img width="1134" height="764" alt="image" src="https://github.com/user-attachments/assets/d1044a96-aeb3-4471-a5a8-81c954891efc" />   <br />

<br />
12. Enter "User" as the name, skip the password creation, and click Next.
<br />
<img width="1158" height="840" alt="image" src="https://github.com/user-attachments/assets/e41d133f-f48b-4cbf-a498-681bb630d2dc" />
<br />

<br />
13. Now we should have our Windows 10 ready.

 <img width="1142" height="868" alt="image" src="https://github.com/user-attachments/assets/94ac022a-db51-425d-9005-4e5d58ce2ea0" />
<br />
<br />
14. To follow best practices in our lab environment, we'll assign static IP addresses to both virtual machines. Using static IP addresses ensures reliable communication between the systems and is required for successfully joining the Windows 10 client to the Active Directory domain.
Next, switch to the Windows Server 2022 virtual machine. Open **Control Panel**, then navigate to **View network status and tasks** → **Change adapter settings**. Right-click the **Ethernet** network adapter, select **Properties**, and begin configuring the network settings.
<img width="1008" height="1288" alt="14" src="https://github.com/user-attachments/assets/044ce5aa-722f-4256-afcc-807d4a1b39bd" />
<br />
<br />
15. <br />
<img width="990" height="1290" alt="15" src="https://github.com/user-attachments/assets/eb0daeb3-7bb7-4394-8de7-f93510793203" />
 <br />
 16.  <br />
 <img width="1266" height="1366" alt="16" src="https://github.com/user-attachments/assets/c37a28b1-b22b-4e54-ab49-904a32749e72" />
  <br />
<br />
  17 Double-click on Internet Protocol Version 4 (TCP/IPv4).
  <img width="1002" height="1312" alt="17" src="https://github.com/user-attachments/assets/f5dd846a-1d64-4225-ab03-7e534cf04559" />
  <br />
  <br />
  18. While trying to set up my static ip on the server i noticed a lag , so i researched and figured out that i haven't installed Guest additions on my two virtual machines , This are the steps i took to install guest additions on my virtual machines, Click on devices 
  <img width="1126" height="1190" alt="18" src="https://github.com/user-attachments/assets/e13aa763-d8d9-48ac-b7df-464ae26c4e9c" />
  <img width="1124" height="1302" alt="19" src="https://github.com/user-attachments/assets/34ac15c0-dbd0-4419-b130-052d0107cf41" />
  <br />
  
 <br />
19.  Then click on insert guest additions
<img width="1124" height="1302" alt="19" src="https://github.com/user-attachments/assets/bc63af42-a90d-4a21-a660-f8aaa244b733" />
 <br />
 <br />
20. Now on the Windows PC01 ,We go to My PC , Open the Virtual Box guesst addition cd and click on VBoxWindowsAdditions-amd64.exe
<img width="978" height="728" alt="20" src="https://github.com/user-attachments/assets/c9333523-a994-4c54-9f42-28f826762473" />
 <br />
 <br />
21. Follow the installation process 
<img width="1002" height="760" alt="21" src="https://github.com/user-attachments/assets/bf3cee95-fef8-4bde-b219-4271cab62b69" />
 <br />

 <br />
22. click on finish when its done 
<img width="1024" height="738" alt="22" src="https://github.com/user-attachments/assets/3c88f9cd-1925-43c7-a92f-ff8da88b52e9" />
 <br />
 <br />
23. reboot the system
<img width="1024" height="738" alt="22" src="https://github.com/user-attachments/assets/458c91c8-b8ab-48a1-a623-4e0ecc4aee6d" />
 <br />
 <br />
24. After this virtual box the installation process is completed , Now Our system would run smoothly in this project , next step is to complete the set  up of static address in our Windows Server. with the details
 Now we go back to setting a static IP address for our windows server1
 
	Windows server details
	IPv4 address :   192.168.10.10
	Subnet mask :    255.255.255.0
	Default gateway: 
	Dns Servers	192.168.10.10
  
<img width="1024" height="764" alt="24" src="https://github.com/user-attachments/assets/1ea6e27d-44db-47d4-9db5-a8438cd3ccc5" />
<br />

<br />
25.  Confirm the Static IP address Settings in the command prompt
<img width="994" height="536" alt="25" src="https://github.com/user-attachments/assets/dddebc93-78f7-4e53-b5a1-c6dc294efd37" />
<br />
<br />
26. Next,  Control Panel → Network and Internet → Network and Sharing Center →   Change adapter settings.
Right-click Ethernet. Click Properties. Open IPv4 Properties.
Enter the following 
IP Address	192.168.10.20
Subnet Mask	255.255.255.0
Default Gateway	Leave blank (or 192.168.10.1 if appropriate)
Preferred DNS	192.168.10.10
<img width="1164" height="668" alt="26" src="https://github.com/user-attachments/assets/84e62e99-118b-4034-833f-36edbac04435" />
<br />
<br />
27. To confirm: Open Command Prompt.
Run: ipconfig /all
<img width="1008" height="536" alt="27" src="https://github.com/user-attachments/assets/cb1fbd77-6de1-474c-a714-1ef6dae14c2d" />
<br />

28.  Due to the virtual box having only just one network adapter , we moved our virtual machines to Vm work station where we can have two adapters , one connected as host only and the other one for NAT to enable internet access, I moved my Virtual machines to vm ware works station , I did the same for both my windows server and windows 10
29.  <img width="1536" height="1010" alt="28" src="https://github.com/user-attachments/assets/e2eec883-7488-493e-9e0d-f6ea92423302" />
30.  Now we set a new static IP address for both the windows server and the windows pc 01 below:
Server 2022 (Host-only adapter):

IP address: 192.168.65.10
Subnet mask: 255.255.255.0
Default gateway: (leave blank)
Preferred DNS: 127.0.0.1

Windows 10 client (Host-only adapter):

IP address: 192.168.65.20
Subnet mask: 255.255.255.0
Default gateway: (leave blank)
Preferred DNS: 192.168.65.10 (points to the server)

We would set it on the host only network and dhcp on the NAT network
From this screenshot we can see the NAT is ethernet 0 with the address of 192.168.127.149

And the ethernet 1 is the Host only network 192.168.65.130 would be made static.

<img width="1046" height="806" alt="30" src="https://github.com/user-attachments/assets/4fff5c32-87df-4378-826a-10be0607411f" />

31. Now we click on network connections , click on change adapter settings , and rename our network NAT and HOST ONLY for clarity going forward
<img width="1366" height="990" alt="32" src="https://github.com/user-attachments/assets/dab4f337-60b1-4559-ba15-88f54a2578a8" />

32.  Now we set our IP address to the following by clicking on Right-click host only → Properties. Open IPv4 settings.
Select Internet Protocol Version 4 (TCP/IPv4) → click Properties.

Windows Server 2022 — Ethernet1 (Host-only)

IP address: 192.168.65.10
Subnet mask: 255.255.255.0
Default gateway: (leave blank)
Preferred DNS server: 127.0.0.1

<img width="1366" height="990" alt="32" src="https://github.com/user-attachments/assets/18ac925b-6a38-4528-99ad-38dee05c2b69" />

33.   NAT is set as DHCP
    <img width="1352" height="976" alt="33" src="https://github.com/user-attachments/assets/110227ea-6674-4f88-b5ad-0ca19ee1952f" />

34.  Confirmation of ip address through CMD with ipconfig /all
<img width="1368" height="982" alt="34" src="https://github.com/user-attachments/assets/f27ecf90-56d7-433f-b48b-a223803c4614" />

35.  The same done for the windows 10 PC01

Windows 10 PC01 — Ethernet1 (Host-only)

IP address: 192.168.65.20
Subnet mask: 255.255.255.0
Default gateway: (leave blank)
Preferred DNS server: 192.168.65.10
<img width="1014" height="830" alt="35" src="https://github.com/user-attachments/assets/96bb4985-81f3-43fa-a09c-fba215241eeb" />

36.  Confirmation of NAT as DHCP
<img width="998" height="780" alt="36" src="https://github.com/user-attachments/assets/c97e5d30-6c2b-457c-ada6-fddbe0ff28fa" />

37.  Confirmation of IP addresses through ipconfig /all
<img width="998" height="712" alt="37" src="https://github.com/user-attachments/assets/72e70fea-63cb-421f-9631-1b354b80d45b" />

38.  Open CMD, run ping 192.168.65.10 (DC IP) and nslookup www.successcompany.com to confirm connection
<img width="1046" height="592" alt="38" src="https://github.com/user-attachments/assets/931e0ffd-6a9e-49c0-aaef-56ca9d52a7f2" />

39.  On The server IP address , we changed the DNS IP address from 127.0.0.1 to 192.168.65.10 , This resolved the error we got from "nslookup successcompany.com"
<img width="998" height="720" alt="39" src="https://github.com/user-attachments/assets/76013000-21e2-4b54-9429-c0f88eee44d9" />

40.  Next, switch to the Windows 10 project machine and enable the built-in Administrator account. Open File Explorer, right-click on This PC, and select Manage to launch the Computer Management console.
<img width="1020" height="954" alt="40" src="https://github.com/user-attachments/assets/46292d65-6553-4f13-93e2-fe65b9b6bb59" />

41.  Expand Local Users and Groups, then select Users. Right-click on Administrator and click Properties.
    <img width="1006" height="984" alt="41" src="https://github.com/user-attachments/assets/079f32a7-6932-4b1c-9d47-060f91e0ace0" />

42.  The Account is disabled option is checked by default. Uncheck it, then select Apply and click OK.
    <img width="1032" height="1158" alt="42" src="https://github.com/user-attachments/assets/f6a506c8-169c-4804-9a81-7173595eaa4e" />

43.  Next, click on Administrator again and select Set Password → Proceed. Create a password, then click OK. A prompt will appear confirming that your password has been set.
<img width="1006" height="910" alt="43" src="https://github.com/user-attachments/assets/263f0414-d008-47c7-9997-7e894948d9e4" />

44.  <img width="984" height="912" alt="44" src="https://github.com/user-attachments/assets/cf84447e-b39b-4d65-b548-77f77034c2bd" />

45.  Restart save changes
    <img width="932" height="986" alt="45" src="https://github.com/user-attachments/assets/ef38035c-44a3-4095-b267-dbb6d56c9995" />

46.  Login into administrator
    <img width="1234" height="1154" alt="46" src="https://github.com/user-attachments/assets/69066e4f-05d8-4290-ac10-b19eff786027" />

47.  Since the default 'User' account can be accessed without a password, we will remove it to enhance security and prevent unauthorized access. Open File Explorer, right-click This PC, and choose Manage. Navigate to Local Users and Groups and select Users. To delete the 'User' account, right-click on it and select Delete.
    <img width="1018" height="908" alt="47" src="https://github.com/user-attachments/assets/08d422a4-f339-408d-abf9-9acc5d94b7a8" />

48.  To confirm that the 'User' account has been successfully removed, log out and ensure that the only password-protected account remaining is the 'Administrator' account. We have now successfully set up our local Help Desk account. This procedure removes weak default accounts, enhancing the security of Windows 10.
<img width="998" height="714" alt="48" src="https://github.com/user-attachments/assets/da61d26e-ba20-45ec-b559-cb56e01d6daa" />

49.  Next, we'll install the Remote Server Administration Tools (RSAT) to enable local management of Active Directory from the Windows 10 machine. Open the search bar, type *Optional Features*, and select **Add an optional feature**. Then, click **Add a feature** to begin installing the required RSAT components.**
<img width="1010" height="1302" alt="49" src="https://github.com/user-attachments/assets/56fc08a3-1fef-49f7-a2de-b23796b63ecf" />

50.  Type "RSAT" in the search bar for a quicker search, then install the following 7 features:

RSAT: Active Directory Certificate Services Tools
RSAT: Active Directory Domain Services and Lightweight Directory Services Tools
RSAT: DHCP Server Tools
RSAT: DNS Server Tools
RSAT: Group Policy Management Tools
RSAT: Remote Desktop Services Tools
RSAT: Server Manager

Click Install (7). Once the installation is complete, restart the virtual machine.

<img width="884" height="822" alt="50" src="https://github.com/user-attachments/assets/1a1c58a6-9120-4bdc-a8c9-14e3b42c3932" />

51.  <img width="1052" height="1360" alt="51" src="https://github.com/user-attachments/assets/b10fdbf9-4737-4585-b78e-3b7b5629f934" />

52.  Now we have restarted our computer and Now that the administrative tools have been installed, we can verify the installation by clicking the Windows icon in the bottom-left corner and locating the *Windows Administrative Tools* folder.
<img width="1302" height="1626" alt="52" src="https://github.com/user-attachments/assets/46617ec5-23a6-4d13-a12c-5137b47501f2" />

53.  open Microsoft edge and download the TeamViewer Full Client 64-bit. We will be using TeamViewer in our upcoming home labs.
<img width="1014" height="1406" alt="53" src="https://github.com/user-attachments/assets/caac99f4-ae54-4e11-82af-9e98011e0df9" />

54.  <img width="1308" height="1578" alt="54" src="https://github.com/user-attachments/assets/13503fe8-18f3-4148-bdcc-07828143f25a" />

55.  Since we're continuing your Enterprise Active Directory Help Desk Lab, here are the exact steps to join your Windows 10 (PC01) machine to the SuccessCompany.com domain.
Open System Properties ,Press Windows + R, type sysdm.cpl, and press Enter.
Click the Computer Name tab. Click Change...Join the Domain
Under Member of, select Domain. Enter: SuccessCompany.com
<img width="1336" height="1584" alt="55" src="https://github.com/user-attachments/assets/212237e4-6b5b-4ef1-bc27-99da76a109ae" />

56.  To verify that PC01 has been successfully joined to the SuccessCompany.com domain, open Active Directory Users and Computers on the Windows Server 2022 domain controller (DC01). Expand the domain, select the Computers container, and confirm that PC01 appears in the list. This computer will serve as our Help Desk workstation throughout the remainder of the lab
<img width="1384" height="1442" alt="56" src="https://github.com/user-attachments/assets/05fc2a0e-4b7f-457a-9c33-58ae0ce0c1f9" />

57.  Next, on the Windows Server 2022 machine, still in Active Directory Users and Computers, select IT Administration , right-click on Helpdesk, and choose Reset Password. Create a new password for the Helpdesk account. Afterward, use this new password to log into the Windows 10 virtual machine. pass is **************
<img width="1308" height="1028" alt="57" src="https://github.com/
  user-attachments/assets/372236ec-23fb-4bf8-b26e-ce021732ec09" />

58.  Next, on the Windows Server 2022 machine, still in Active Directory Users and Computers, select Users, right-click on Helpdesk, and choose Reset Password. Create a new password for the Helpdesk account. Afterward, use this new password to log into the Windows 10 virtual machine.
<img width="1342" height="1620" alt="58" src="https://github.com/user-attachments/assets/fae41e93-84d8-4c8c-a3f5-a92d61aeb1aa" />

59.  Due to our security setting that says new account must put a password before signing in , we create a new password for the helpdesk01 user
<img width="1360" height="1652" alt="59" src="https://github.com/user-attachments/assets/24e03e2d-5ebd-4237-b0b5-8c95a68f57d6" />

60.  Login Successful . !
    <img width="1346" height="1714" alt="60" src="https://github.com/user-attachments/assets/47f04663-a073-4e40-ab6b-1f215fb3cd29" />

61.  Congratulations! We have successfully set up Windows 10, joined the PC to the domain, and installed the RSAT tools, google and TeamViewer.

<img width="1344" height="1058" alt="61" src="https://github.com/user-attachments/assets/3b6a75c7-1b2c-4cbe-9518-8fa97f44d5a3" />

