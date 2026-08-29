## LAB 04 - Windows 10, Join PC to Domain (Helpdesk), RSAT Tool, Server Manager


## Objective
In this lab, I deployed and configured a Windows 10 virtual machine to serve as the Help Desk workstation for my **SuccessCompany.com** Active Directory home lab. The project covers installing Windows 10, configuring static IP addresses, optimizing the virtual machine, migrating the environment from VirtualBox to VMware Workstation, installing the Remote Server Administration Tools (RSAT), and joining the workstation to the Active Directory domain. By completing this lab, I established a fully functional domain-joined client capable of performing everyday Help Desk and system administration tasks in an enterprise environment.


## Steps
1. The process begins with downloading the Windows 10 Installation Media Tool from the official Microsoft website: Windows 10 Installation Media Tool.

<br />

<img width="1324" height="1258" alt="1" src="https://github.com/user-attachments/assets/fd67b7fc-0091-48c1-ad28-b33c8a96efb1" />

<br />
<br />

2. Open the media tool installer and click **Accept**. Next, select **Create installation media (USB flash drive, DVD, or ISO file) for another PC**. Save the download to your **Downloads** folder, and you should be able to access it from the VirtualBox ISO.

<br />

<img width="1124" height="370" alt="2" src="https://github.com/user-attachments/assets/8ad537c0-336a-41f7-b4e9-3fbe2fe7b291" />

<br />
<br />

3. Next, open your VirtualBox application and create a new virtual machine. Click **Machine** in the top-left corner, then select **New**.

<br />

<img width="1420" height="1692" alt="3" src="https://github.com/user-attachments/assets/9c815a2b-af8d-40ba-a661-54f74f73bdcc" />

<br />
<br />

4. Name the virtual machine **Windows 10 Project**. For the ISO image, navigate to the **Downloads** folder, click the dropdown icon, select **Other**, and choose the Windows 10 ISO file. Then, select **Skip unattended installation**.

<br />

<img width="1578" height="1096" alt="4" src="https://github.com/user-attachments/assets/b0429a79-c380-4c49-bf28-aed0c3d5b44b" />

<br />
<br />

5. Select **Hardware**. By default, the base memory is set to **2048 MB**. Increase it to **6081 MB**. Click **Finish**, then start the virtual machine. When the Windows Setup screen appears, click **Next**, followed by **Install Now**.

<br />

<img width="1082" height="806" alt="image" src="https://github.com/user-attachments/assets/49ac2018-46b4-4dea-b8b3-d90b7d497bdc" />

<br />

<img width="1086" height="790" alt="image" src="https://github.com/user-attachments/assets/dc8c636f-f51c-40be-ba6f-fc1315d897eb" />

<br />
<br />

6. Select **I don't have a product key**.

<br />

<img width="1098" height="738" alt="image" src="https://github.com/user-attachments/assets/02674703-e409-44f1-a231-70f8d6c98869" />

<br />
<br />

7. Select **Windows 10 Pro**, accept the Microsoft Software License Terms, and click **Next**.

<br />

<img width="1064" height="788" alt="image" src="https://github.com/user-attachments/assets/feafd780-4bf7-4cea-bf4f-3b23a7fe6d14" />

<br />
<br />

8. Select **Custom: Install Windows only (advanced)**, then click **Next** to begin the Windows 10 installation.

<br />

<img width="1090" height="806" alt="image" src="https://github.com/user-attachments/assets/6dfd2bc0-f158-485f-bd55-20bf692a8caf" />

<br />
<br />

9. Continue through the Windows setup wizard until you reach the region and keyboard configuration screens.

<br />

<img width="1074" height="810" alt="image" src="https://github.com/user-attachments/assets/b0077ad8-e904-44c7-9f93-779e1118aecd" />

<br />
<br />

10. Select **Set up for personal use**, then click **Next**.

<br />

<img width="1148" height="838" alt="image" src="https://github.com/user-attachments/assets/4ac36cb1-7b55-4be1-ae43-89ec141cc61c" />

<br />
<br />

11. Continue through the remaining Windows setup prompts until you reach the account creation screen.

<br />

<img width="1134" height="764" alt="image" src="https://github.com/user-attachments/assets/d1044a96-aeb3-4471-a5a8-81c954891efc" />

<br />
<br />

12. Enter **User** as the local account name. Skip creating a password, then click **Next** to continue.

<br />

<img width="1158" height="840" alt="image" src="https://github.com/user-attachments/assets/e41d133f-f48b-4cbf-a498-681bb630d2dc" />

<br />
<br />

13. Windows 10 has now been installed successfully and is ready for configuration.

<br />

<img width="1142" height="868" alt="image" src="https://github.com/user-attachments/assets/94ac022a-db51-425d-9005-4e5d58ce2ea0" />

<br />
<br />

14. To follow best practices in our lab environment, we'll assign static IP addresses to both virtual machines. Using static IP addresses ensures reliable communication between the systems and is required for successfully joining the Windows 10 client to the Active Directory domain.

Next, switch to the Windows Server 2022 virtual machine. Open **Control Panel**, then navigate to **View network status and tasks** → **Change adapter settings**. Right-click the **Ethernet** network adapter, select **Properties**, and begin configuring the network settings.

<br />

<img width="990" height="1290" alt="15" src="https://github.com/user-attachments/assets/dd0e7c40-3021-45ac-a1b9-bdb2a0e922d1" />


<br />
<br />

15. Select **Internet Protocol Version 4 (TCP/IPv4)**, then click **Properties** to configure the static IP address for the Windows Server 2022 virtual machine.
<img width="1266" height="1366" alt="16" src="https://github.com/user-attachments/assets/b694c9a7-c35b-4f8b-99af-d28436e383e6" />

<br />
<br />
16. Enter the following static IP configuration for the Windows Server 2022 virtual machine, then click **OK** to save the changes.
Select Use the following IP address, then configure the static IP address as follows:

IP Address: 192.168.10.10
Subnet Mask: 255.255,255.0
Preferred DNS: 192.168.10.10

<br />

<img width="1266" height="1366" alt="16" src="https://github.com/user-attachments/assets/c37a28b1-b22b-4e54-ab49-904a32749e72" />

<br />
<br />

17. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to verify that the static IP address has been configured correctly.

<br />

<img width="1024" height="764" alt="24" src="https://github.com/user-attachments/assets/cc14b18f-8c34-44d6-bd50-e43258941bf0" />

<br />
<br />

18. While configuring the server's static IP address, I noticed that the virtual machine was running slowly. After some research, I realized that I hadn't installed **VirtualBox Guest Additions** on either virtual machine. To improve performance, click **Devices** from the VirtualBox menu.

<br />

<img width="1126" height="1190" alt="18" src="https://github.com/user-attachments/assets/e13aa763-d8d9-48ac-b7df-464ae26c4e9c" />

<br />
<br />

19. Next, click **Insert Guest Additions CD Image** to mount the Guest Additions installation media.

<br />

<img width="1124" height="1302" alt="19" src="https://github.com/user-attachments/assets/bc63af42-a90d-4a21-a660-f8aaa244b733" />

<br />
<br />

20. On the Windows 10 **PC01** virtual machine, open **This PC**, open the **VirtualBox Guest Additions CD**, and run **VBoxWindowsAdditions-amd64.exe** to begin the installation.

<br />

<img width="978" height="728" alt="20" src="https://github.com/user-attachments/assets/c9333523-a994-4c54-9f42-28f826762473" />

<br />

21. Follow the installation wizard by clicking **Next**, **Next**, and then **Install**. Once the installation is complete, click **Finish** to restart the virtual machine and apply the changes.

<br />

<img width="1002" height="760" alt="21" src="https://github.com/user-attachments/assets/40fa56d7-739a-4771-b382-aceeae89e1a8" />


<br />
<br />

22. After the virtual machine restarts, verify that **VirtualBox Guest Additions** has been installed successfully. You should notice smoother performance, improved display scaling, and better mouse integration.

<br />

<img width="1024" height="738" alt="22" src="https://github.com/user-attachments/assets/7c555069-7ffa-4a35-ab8a-5b98de1c69bf" />

<br />
<br />

23. Now configure a static IP address on the Windows 10 **PC01** virtual machine. Open **Control Panel**, navigate to **View network status and tasks** → **Change adapter settings**, right-click **Ethernet**, and select **Properties**.

<br />

<img width="1058" height="844" alt="23" src="https://github.com/user-attachments/assets/cbb98eec-62f7-4bfe-9df6-c00f55dee392" />


<br />
<br />

24. Select **Internet Protocol Version 4 (TCP/IPv4)**, click **Properties**, and enter the appropriate static IP configuration for the Windows 10 virtual machine. Once you've finished, click **OK** to save the settings.

<br />

<img width="1024" height="764" alt="24" src="https://github.com/user-attachments/assets/4391ec96-9a6d-4870-8433-e9509196a130" />

<br />
<br />

25. Open **Command Prompt** on the Windows Server 2022 virtual machine and run the following command to verify the network configuration:

```cmd
ipconfig /all
```

Confirm that the static IP address, subnet mask, and DNS settings have been configured correctly.

<br />

<img width="994" height="536" alt="25" src="https://github.com/user-attachments/assets/3b8d51c5-ceeb-4fec-afdb-c0408b880d67" />

<br />
<br />

26. Open **Command Prompt** on the Windows 10 **PC01** virtual machine and run the following command:

```cmd
ipconfig /all
```

Verify that the Windows 10 client is using the correct static IP address, subnet mask, and DNS server before continuing with the domain join process.

<br />

<img width="1164" height="668" alt="26" src="https://github.com/user-attachments/assets/46c09ad2-b463-47a1-bc87-65159ef3008e" />


<br />


Step 27 – Confirm the Windows 10 IP Configuration

Open **Command Prompt** and run the following command:

```cmd
ipconfig /all
```

Confirm that the Windows 10 client is using the correct static IP address, subnet mask, and DNS server.

<br>

<img width="1008" height="536" alt="27" src="https://github.com/user-attachments/assets/cb1fbd77-6de1-474c-a714-1ef6dae14c2d" />

<br>

---

## Migrating the Lab to VMware Workstation

### Step 28 – Move the Virtual Machines to VMware Workstation

Due to VirtualBox having only one network adapter available for the lab, I moved both virtual machines to **VMware Workstation**.

VMware Workstation allowed me to configure two network adapters:

* A **Host-Only adapter** for communication between the virtual machines.
* A **NAT adapter** for internet access.

I completed the migration for both the Windows Server 2022 virtual machine and the Windows 10 virtual machine.

<br>

---

### Step 29 – Confirm the VMware Workstation Migration

The screenshot below shows the virtual machines after they were successfully moved to VMware Workstation.

<br>

<img width="1536" height="1010" alt="28" src="https://github.com/user-attachments/assets/e2eec883-7488-493e-9e0d-f6ea92423302" />

<br>

---

## Configure the VMware Network Adapters

### Step 30 – Plan the New IP Address Configuration

After migrating the virtual machines, I configured new static IP addresses for the Host-Only network adapters.

The NAT adapters would continue using DHCP to provide internet access.

#### Windows Server 2022 – Host-Only Adapter

| Setting         | Value           |
| --------------- | --------------- |
| IP address      | `192.168.65.10` |
| Subnet mask     | `255.255.255.0` |
| Default gateway | Leave blank     |
| Preferred DNS   | `127.0.0.1`     |

#### Windows 10 PC01 – Host-Only Adapter

| Setting         | Value           |
| --------------- | --------------- |
| IP address      | `192.168.65.20` |
| Subnet mask     | `255.255.255.0` |
| Default gateway | Leave blank     |
| Preferred DNS   | `192.168.65.10` |

The DNS server on PC01 points to the Windows Server 2022 domain controller.

The Host-Only adapters were configured with static IP addresses, while the NAT adapters remained configured to obtain their addresses automatically through DHCP.

From the screenshot:

* **Ethernet0** is the NAT adapter with the address `192.168.127.149`.
* **Ethernet1** is the Host-Only adapter, which originally received `192.168.65.130` before being configured with a static IP address.

<br>

<img width="1046" height="806" alt="30" src="https://github.com/user-attachments/assets/4fff5c32-87df-4378-826a-10be0607411f" />

<br>

---

### Step 31 – Rename the Network Adapters

Open **Network Connections** and select **Change adapter settings**.

Rename the network adapters for clarity:

* Rename the internet-facing adapter to **NAT**.
* Rename the internal lab adapter to **HOST ONLY**.

Using descriptive adapter names makes it easier to identify and manage each network connection throughout the rest of the project.

<br>

<img width="1366" height="990" alt="32" src="https://github.com/user-attachments/assets/dab4f337-60b1-4559-ba15-88f54a2578a8" />

<br>

---

### Step 32 – Configure the Server Host-Only Adapter

On the Windows Server 2022 virtual machine, right-click the **HOST ONLY** adapter and select **Properties**.

Select:

**Internet Protocol Version 4 (TCP/IPv4) → Properties**

Enter the following network information:

#### Windows Server 2022 – Ethernet1 Host-Only Adapter

| Setting              | Value           |
| -------------------- | --------------- |
| IP address           | `192.168.65.10` |
| Subnet mask          | `255.255.255.0` |
| Default gateway      | Leave blank     |
| Preferred DNS server | `127.0.0.1`     |

<br>

<img width="1366" height="990" alt="32" src="https://github.com/user-attachments/assets/18ac925b-6a38-4528-99ad-38dee05c2b69" />

<br>

---

### Step 33 – Configure the Server NAT Adapter for DHCP

The NAT adapter was configured to obtain its network settings automatically.

In the IPv4 properties, select:

* **Obtain an IP address automatically**
* **Obtain DNS server address automatically**

This allows VMware's NAT service to assign the adapter an IP address and provide internet connectivity.

<br>

<img width="1352" height="976" alt="33" src="https://github.com/user-attachments/assets/110227ea-6674-4f88-b5ad-0ca19ee1952f" />

<br>

---

### Step 34 – Verify the Server IP Configuration

Open **Command Prompt** on the Windows Server 2022 virtual machine and run:

```cmd
ipconfig /all
```

Confirm that:

* The Host-Only adapter is using the static IP address `192.168.65.10`.
* The NAT adapter received an IP address automatically through DHCP.
* The subnet mask and DNS settings are correct.

<br>

<img width="1368" height="982" alt="34" src="https://github.com/user-attachments/assets/f27ecf90-56d7-433f-b48b-a223803c4614" />

<br>

---

### Step 35 – Configure the Windows 10 Host-Only Adapter

Repeat the same process on the Windows 10 PC01 virtual machine.

Right-click the **HOST ONLY** adapter, select **Properties**, and open the IPv4 settings.

Enter the following information:

#### Windows 10 PC01 – Ethernet1 Host-Only Adapter

| Setting              | Value           |
| -------------------- | --------------- |
| IP address           | `192.168.65.20` |
| Subnet mask          | `255.255.255.0` |
| Default gateway      | Leave blank     |
| Preferred DNS server | `192.168.65.10` |

The preferred DNS server points to the Windows Server 2022 domain controller.

<br>

<img width="1014" height="830" alt="35" src="https://github.com/user-attachments/assets/96bb4985-81f3-43fa-a09c-fba215241eeb" />

<br>

---

### Step 36 – Configure the Windows 10 NAT Adapter for DHCP

Configure the NAT adapter on PC01 to obtain its network settings automatically.

Select:

* **Obtain an IP address automatically**
* **Obtain DNS server address automatically**

This adapter will provide PC01 with internet access.

<br>

<img width="998" height="780" alt="36" src="https://github.com/user-attachments/assets/c97e5d30-6c2b-457c-ada6-fddbe0ff28fa" />

<br>

---

### Step 37 – Verify the Windows 10 IP Configuration

Open **Command Prompt** on PC01 and run:

```cmd
ipconfig /all
```

Confirm that:

* The Host-Only adapter is using `192.168.65.20`.
* The NAT adapter received its address automatically through DHCP.
* The preferred DNS server for the Host-Only adapter is `192.168.65.10`.

<br>

<img width="998" height="712" alt="37" src="https://github.com/user-attachments/assets/72e70fea-63cb-421f-9631-1b354b80d45b" />

<br>

---

## Test Network and DNS Connectivity

### Step 38 – Test Communication with the Domain Controller

Open **Command Prompt** on PC01.

Run the following command to test communication with the Windows Server 2022 domain controller:

```cmd
ping 192.168.65.10
```

Next, run the following DNS lookup command:

```cmd
nslookup www.successcompany.com
```

These commands verify that PC01 can communicate with the domain controller and resolve the domain name through DNS.

<br>

<img width="1046" height="592" alt="38" src="https://github.com/user-attachments/assets/931e0ffd-6a9e-49c0-aaef-56ca9d52a7f2" />

<br>

---

### Step 39 – Correct the Server DNS Configuration

The original DNS setting on the Windows Server 2022 Host-Only adapter was configured as `127.0.0.1`.

After experiencing an error while running:

```cmd
nslookup successcompany.com
```

I changed the preferred DNS server from:

```text
127.0.0.1
```

to:

```text
192.168.65.10
```

This allowed the server to use its own static IP address for DNS resolution and resolved the lookup error.

<br>

<img width="998" height="720" alt="39" src="https://github.com/user-attachments/assets/76013000-21e2-4b54-9429-c0f88eee44d9" />

<br>

---

## Configure the Windows 10 Local Administrator Account

### Step 40 – Open Computer Management

Switch to the Windows 10 PC01 virtual machine.

Open **File Explorer**, right-click **This PC**, and select **Manage**.

This opens the **Computer Management** console, where the built-in local Administrator account can be enabled and configured.

<br>

<img width="1020" height="954" alt="40" src="https://github.com/user-attachments/assets/46292d65-6553-4f13-93e2-fe65b9b6bb59" />

<br>

---



41. Expand **Local Users and Groups**, then select **Users**. Right-click on the **Administrator** account and select **Properties**.

<br />

<img width="1006" height="984" alt="41" src="https://github.com/user-attachments/assets/079f32a7-6932-4b1c-9d47-060f91e0ace0" />

<br />
<br />

42. By default, the **Account is disabled** option is selected. Uncheck this option, then click **Apply** followed by **OK** to enable the built-in Administrator account.

<br />

<img width="1032" height="1158" alt="42" src="https://github.com/user-attachments/assets/f6a506c8-169c-4804-9a81-7173595eaa4e" />

<br />
<br />

43. Next, right-click on the **Administrator** account again and select **Set Password**. Click **Proceed**, create a secure password, and then click **OK**. A confirmation message will appear indicating that the password has been successfully set.

<br />

<img width="1006" height="910" alt="43" src="https://github.com/user-attachments/assets/263f0414-d008-47c7-9997-7e894948d9e4" />

<br />
<br />

44. Click **OK** to acknowledge the confirmation message and complete the password configuration.

<br />

<img width="984" height="912" alt="44" src="https://github.com/user-attachments/assets/cf84447e-b39b-4d65-b548-77f77034c2bd" />

<br />
<br />

45. Restart the Windows 10 virtual machine to apply the changes.

<br />

<img width="932" height="986" alt="45" src="https://github.com/user-attachments/assets/ef38035c-44a3-4095-b267-dbb6d56c9995" />

<br />
<br />

46. After the system restarts, sign in using the newly enabled **Administrator** account and the password you created in the previous steps.

<br />

<img width="1234" height="1154" alt="46" src="https://github.com/user-attachments/assets/69066e4f-05d8-4290-ac10-b19eff786027" />

<br />
<br />

47. Since the default **User** account does not require a password, we'll remove it to improve the security of our Windows 10 Help Desk workstation. Open **File Explorer**, right-click **This PC**, and select **Manage**. Navigate to **Local Users and Groups → Users**, right-click the **User** account, and select **Delete**.

<br />

<img width="1018" height="908" alt="47" src="https://github.com/user-attachments/assets/08d422a4-f339-408d-abf9-9acc5d94b7a8" />

<br />
<br />

48. To verify that the **User** account has been removed successfully, sign out and confirm that the **Administrator** account is now the only local account available. We have now successfully secured our Windows 10 Help Desk workstation by removing the unsecured default account.

<br />

<img width="998" height="714" alt="48" src="https://github.com/user-attachments/assets/da61d26e-ba20-45ec-b559-cb56e01d6daa" />

<br />
<br />

49. Next, we'll install the **Remote Server Administration Tools (RSAT)** so that we can manage Active Directory and other Windows Server roles directly from the Windows 10 workstation. Open the search bar, type **Optional Features**, select **Add an optional feature**, and then click **Add a feature**.

<br />

<img width="1010" height="1302" alt="49" src="https://github.com/user-attachments/assets/56fc08a3-1fef-49f7-a2de-b23796b63ecf" />

<br />
<br />

50. Search for **RSAT** to quickly locate the available administration tools. Install the following components:

- RSAT: Active Directory Certificate Services Tools
- RSAT: Active Directory Domain Services and Lightweight Directory Services Tools
- RSAT: DHCP Server Tools
- RSAT: DNS Server Tools
- RSAT: Group Policy Management Tools
- RSAT: Remote Desktop Services Tools
- RSAT: Server Manager

Click **Install** and wait for all seven components to finish installing. Once the installation is complete, restart the virtual machine.

<br />

<img width="884" height="822" alt="50" src="https://github.com/user-attachments/assets/1a1c58a6-9120-4bdc-a8c9-14e3b42c3932" />

<br />

<img width="1052" height="1360" alt="51" src="https://github.com/user-attachments/assets/b10fdbf9-4737-4585-b78e-3b7b5629f934" />

<br />
<br />

51. After restarting the virtual machine, verify that the RSAT tools were installed successfully by opening the **Start Menu** and locating the **Windows Administrative Tools** folder.

<br />

<img width="1302" height="1626" alt="52" src="https://github.com/user-attachments/assets/46617ec5-23a6-4d13-a12c-5137b47501f2" />

<br />
<br />

52. Open **Microsoft Edge** and download the **TeamViewer Full Client (64-bit)**. TeamViewer will be used in future home lab projects to simulate remote desktop support scenarios commonly performed by Help Desk technicians.

<br />

<img width="1014" height="1406" alt="53" src="https://github.com/user-attachments/assets/caac99f4-ae54-4e11-82af-9e98011e0df9" />

<br />

<img width="1308" height="1578" alt="54" src="https://github.com/user-attachments/assets/13503fe8-18f3-4148-bdcc-07828143f25a" />

<br />
<br />

53. Next, we'll join **PC01** to the **SuccessCompany.com** Active Directory domain. Press **Windows + R**, type **sysdm.cpl**, and press **Enter**. Select the **Computer Name** tab and click **Change**.

Under **Member of**, select **Domain**, enter **SuccessCompany.com**, and complete the domain join process.

<br />

<img width="1336" height="1584" alt="55" src="https://github.com/user-attachments/assets/212237e4-6b5b-4ef1-bc27-99da76a109ae" />

<br />
<br />

54. To verify that **PC01** has successfully joined the **SuccessCompany.com** domain, open **Active Directory Users and Computers** on **DC01**. Expand the domain, open the **Computers** container, and confirm that **PC01** appears in the list. This workstation will be used throughout the remaining Help Desk labs.

<br />

<img width="1384" height="1442" alt="56" src="https://github.com/user-attachments/assets/05fc2a0e-4b7f-457a-9c33-58ae0ce0c1f9" />

<br />
<br />

55. Next, on the Windows Server 2022 machine, open **Active Directory Users and Computers**. Navigate to **IT Administration**, right-click the **Helpdesk** account, and select **Reset Password**. Create a new password for the account and use it to sign in to the Windows 10 virtual machine.

<br />

<img width="1308" height="1028" alt="57" src="https://github.com/user-attachments/assets/372236ec-23fb-4bf8-b26e-ce021732ec09" />

<br />
<br />

56. Next, navigate to the **Users** container in **Active Directory Users and Computers**, right-click the **Helpdesk** account, and select **Reset Password**. Assign a new password and use the updated credentials to sign in to the Windows 10 virtual machine.

<br />

<img width="1342" height="1620" alt="58" src="https://github.com/user-attachments/assets/fae41e93-84d8-4c8c-a3f5-a92d61aeb1aa" />

<br />
<br />

57. Since our security policy requires users to change their password during their first sign-in, create a new password for the **Helpdesk01** account to complete the login process.

<br />

<img width="1360" height="1652" alt="59" src="https://github.com/user-attachments/assets/24e03e2d-5ebd-4237-b0b5-8c95a68f57d6" />

<br />
<br />

58. Login successful! We have now successfully authenticated using the **Helpdesk** account.

<br />

<img width="1346" height="1714" alt="60" src="https://github.com/user-attachments/assets/47f04663-a073-4e40-ab6b-1f215fb3cd29" />

<br />
<br />

59. Congratulations! We have successfully:

- Installed Windows 10.
- Configured the network.
- Joined **PC01** to the **SuccessCompany.com** domain.
- Installed the **RSAT** tools.
- Installed **Google Chrome** and **TeamViewer**.

The Windows 10 Help Desk workstation is now fully configured and ready for the remaining Active Directory administration labs.

<br />

<img width="1344" height="1058" alt="61" src="https://github.com/user-attachments/assets/3b6a75c7-1b2c-4cbe-9518-8fa97f44d5a3" />

<br />



## Conclusion

In this lab, I successfully built and configured a Windows 10 Help Desk workstation for my enterprise Active Directory environment. I installed Windows 10, configured static networking, optimized the virtual machine, migrated the lab to VMware Workstation, installed the Remote Server Administration Tools (RSAT), and joined **PC01** to the **SuccessCompany.com** domain. With the workstation fully integrated into the domain, it is now ready to perform Active Directory administration, remote server management, user account support, and other real-world Help Desk responsibilities that will be demonstrated throughout the remaining labs in this series.
