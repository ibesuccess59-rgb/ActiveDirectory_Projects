# Lab 6: Common Active Directory Issues, CMD Commands, PC Offline

## Overview

In this lab, I simulated and resolved common issues encountered in an Active Directory environment using built-in Windows administrative tools and Command Prompt (CMD). The lab focuses on troubleshooting user authentication problems, verifying domain connectivity, diagnosing Group Policy issues, and restoring communication with domain-joined computers that have gone offline. These are common tasks performed by Help Desk and IT Support technicians in enterprise environments.

## Objectives

- Troubleshoot and resolve common Active Directory issues, including login failures, account lockouts, and password-related problems.
- Use Command Prompt (CMD) tools to diagnose domain connectivity, DNS resolution, authentication, and network issues.
- Troubleshoot and restore communication with domain-joined computers that are offline or unable to contact the domain controller.
- Verify and troubleshoot Group Policy application using built-in Windows tools.
- Develop practical troubleshooting skills commonly used in Help Desk, Desktop Support, and System Administration roles.

---

### Simulate a failed login

**1.** Start PC02, Select other user on the windows sign in screen, Enter "Successcompany/Gozi", Enter an incorrect password several times, continue until windows displays an account lockout or login failure

![Step 1](https://github.com/user-attachments/assets/b9a6a9d7-cfe8-4d94-8497-deb6e2645029)

**2.** Sign in to DC01 using adminitrator account, open server manager, select tools, open active directory and users, expand successcompany.com

![Step 2](https://github.com/user-attachments/assets/a1f2ff08-c733-4fc3-9380-5845e65c6762)

**3.** Open the Organizational Unit (OU) containing the Gozi user account, right-click Gozi, select Properties, and then open the Account tab to view and manage the user's account settings.

![Step 3](https://github.com/user-attachments/assets/f22c809b-2a3c-4285-836c-c218ccb4c674)

**4.** From the screenshot you can see that the account has been locked out due to a wrong password being put in multiple times, now on the accout tab, select unlock account, select apply, select OK.

![Step 4](https://github.com/user-attachments/assets/711bc068-f9cd-479f-b496-b4e2d7ad4fac)

**5.** Next step is to reset the password, Right-click the **Gozi** user account and select **Reset Password**. Enter and confirm a temporary password, we would select **User must change password at next logon** , and then click **OK** to apply the new password.

![Step 5a](https://github.com/user-attachments/assets/1f17907e-51ae-4cb1-86ab-f5108ef5cc5d)

![Step 5b](https://github.com/user-attachments/assets/4af1a171-8316-4076-a52c-bb6ded6cbb7c)

**6.** Return to PC02, select the Gozi account, and enter the temporary password. Windows displays a message stating that the user's password must be changed before signing in. Click OK.

![Step 6](https://github.com/user-attachments/assets/7d24e1de-cf75-4595-a00b-f13ae8e558de)

**7.** Enter the temporary password in the first field, enter a new password in the second field, confirm the new password in the third field, and press Enter or select the arrow.

![Step 7](https://github.com/user-attachments/assets/bdd56882-3c30-46ea-b5f9-137760cd6f82)

**8.** Windows displays a message stating that the password has been changed. Click OK and confirm that Gozi can successfully sign in to PC02.

![Step 8](https://github.com/user-attachments/assets/db79665f-83d9-41b5-a603-13a4fe4012a2)

**9.** On PC02, we opened Command Prompt and ran: `ipconfig /all`
We verified the Host-Only network adapter had the following configuration:
- IPv4 Address: 192.168.65.30
- Subnet Mask: 255.255.255.0
- DNS Server: 192.168.65.10
- DHCP: Disabled

This confirmed that PC02 was configured with a static IP address and was using our Domain Controller as its DNS server.

![Step 9](https://github.com/user-attachments/assets/9bfaa098-722e-4f6c-99b1-640d85079ca7)

**10.** Next we Verify DNS and Domain Controller Discovery
Next, we tested whether PC02 could resolve the Active Directory domain.
We ran: `nslookup successcompany.com`
The query returned the IP address of our Domain Controller.

We then ran: `nltest /dsgetdc:successcompany.com`
The command successfully located: `\\SuccessCompanyServer.successcompany.com`
It also displayed the Domain Controller IP: 192.168.65.10
This confirmed that PC02 could successfully locate an Active Directory Domain Controller.

![Step 10](https://github.com/user-attachments/assets/a1aa68b4-fcc4-4063-b065-c6b51d0c373a)

**11.** Next we'd Open the PC02 Network Adapter
To demonstrate DNS troubleshooting, we opened:
Control Panel
→ Network and Internet
→ Network Connections
We right-clicked the HOST ONLY adapter and selected:
Properties

![Step 11](https://github.com/user-attachments/assets/98aab263-4f5a-4495-9f49-678b0cfb9d2a)

**12.** Now lets Simulate a DNS Misconfiguration

We selected: Internet Protocol Version 4 (TCP/IPv4) and opened Properties.
To simulate a common Active Directory DNS problem, we changed the Preferred DNS Server from the Domain Controller to: 8.8.8.8
PC02 still had its static IP address: 192.168.65.30

![Step 12](https://github.com/user-attachments/assets/42919e15-0fcc-4993-9658-a61fc0689963)

**13.** Verify the Incorrect DNS Configuration
We ran: `ipconfig /all`
again.
The HOST ONLY adapter now showed:
DNS Servers: 8.8.8.8
This confirmed that the DNS misconfiguration had been applied successfully.

![Step 13](https://github.com/user-attachments/assets/cab52d15-c587-436c-9482-efba5395a466)

**14.** Verify the Domain Controller Network Configuration
On DC01, we ran: `ipconfig /all`
We confirmed the Domain Controller's Host-Only interface was configured with:
- IPv4 Address: 192.168.65.10
- Subnet Mask: 255.255.255.0
- DNS Server: 192.168.65.10

This confirmed that DC01 was correctly using itself as the DNS server for the Active Directory environment.

![Step 14.1](https://github.com/user-attachments/assets/67e750a1-3323-4c80-ba87-9d353d28e797)

**15.** Restore the Correct DNS Server on PC02
We changed the HOST ONLY adapter DNS configuration back to the Domain Controller:
Preferred DNS Server: 192.168.65.10
We then ran: `ipconfig /all` and verified:
- IPv4 Address: 192.168.65.30
- DNS Server: 192.168.65.10

PC02 was now using the correct Active Directory DNS server again.

![Step 14.2](https://github.com/user-attachments/assets/da34199e-950a-477e-8039-6f2731b76c77)

**16.** Test Connectivity to the Domain Controller
After restoring the DNS configuration, we tested basic network connectivity from PC02.
We ran: `ping 192.168.65.10`

![Step 14.3](https://github.com/user-attachments/assets/3844baa7-4444-4512-9456-cb3e27c1c2af)

**17.** On DC01, open Active Directory Users and Computers, expand successcompany.com, and open the HR Organizational Unit.
Right-click the Gozi user account, select Properties, and open the Account tab.
Under Account expires, select End of and choose a date that has already passed.
Click Apply and then click OK.

![Step 15](https://github.com/user-attachments/assets/9d1c16e4-41b0-446f-a29e-6b1ba186388b)

**18.** Return to PC02 and attempt to sign in using the Gozi account.
Confirm that Windows displays the message:
The user's account has expired.

![Step 16](https://github.com/user-attachments/assets/d98523ec-06dd-46c6-b996-b15933568d88)

**19.** Return to DC01, open the Gozi account properties again, and open the Account tab.
Under Account expires, select Never.

![Step 17](https://github.com/user-attachments/assets/7902bf28-eade-4ad6-9848-a5f0593812bd)

**20.** Return to PC02 and sign in using Gozi's current password.
Confirm that the user can successfully sign in after the expiration setting has been removed.

![Step 18](https://github.com/user-attachments/assets/e791f585-1ab1-48dc-841a-e638e2357cdf)
