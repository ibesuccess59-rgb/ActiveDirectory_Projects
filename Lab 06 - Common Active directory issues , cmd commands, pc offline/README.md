## Lab 6 Common Active Directory Issues, CMD Commands, PC Offline

 In this lab, I simulated and resolved common issues encountered in an Active Directory environment using built-in Windows administrative tools and Command Prompt (CMD). The lab focuses on troubleshooting user authentication problems, verifying domain connectivity, diagnosing Group Policy issues, and restoring communication with domain-joined computers that have gone offline. These are common tasks performed by Help Desk and IT Support technicians in enterprise environments.

## Objectives
-  Troubleshoot and resolve common Active Directory issues, including login failures, account lockouts, and password-related problems.
-  Use Command Prompt (CMD) tools to diagnose domain connectivity, DNS resolution, authentication, and network issues.
-  Troubleshoot and restore communication with domain-joined computers that are offline or unable to contact the domain controller.
-  Verify and troubleshoot Group Policy application using built-in Windows tools.
Develop practical troubleshooting skills commonly used in Help Desk, Desktop Support, and System Administration roles.

## Lab Environment
-  Domain Controller: DC01
-  Domain: SuccessCompany.com
-  Client Computers: PC01 and PC02
-  Domain User: Gozi
-  Help Desk Account: Helpdesk01
-  Server IP Address: 192.168.65.10
-  PC01 IP Address: 192.168.65.20
-  Preferred DNS Server: 192.168.65.10

Scenario 1 – Troubleshooting Login Problems and Account Lockouts

In this scenario, the domain user Gozi cannot sign in to PC02 because the account is locked, disabled, expired, or using an incorrect password.

Simulate a failed login
1.  Start PC02 , Select other user on the windows sign in screen ,Enter "Successcompany/Gozi", Enter an incorrect password several times, continue until windows displays an account lockout or login failure

2.  Sign in to DC01 using adminitrator account , open server manager , select tools , open active directory and users, expand successcompany.com

3.  Open the Organizational Unit (OU) containing the Gozi user account, right-click Gozi, select Properties, and then open the Account tab to view and manage the user's account settings.

4.  From the screenshot you can see that the account has been locked out due to a wrong password being put in multiple times , now on the accout tab , select unlock account , select apply, select OK.

5.  Next step is to reset the password , Right-click the **Gozi** user account and select **Reset Password**. Enter and confirm a temporary password, select **User must change password at next logon** if required, and then click **OK** to apply the new password.

6. Now we test the login , return to pc02, Sign in using successcompany\Gozi, enter the correct or temporary password , confirm that the login is successful

7. A confirmation message appears stating that the password for Gozi has been changed. Click OK to close the message.

8. Return to PC02, select the Gozi account, and enter the temporary password. Windows displays a message stating that the user’s password must be changed before signing in. Click OK.

9. Enter the temporary password in the first field, enter a new password in the second field, confirm the new password in the third field, and press Enter or select the arrow.

10. Windows displays a message stating that the password has been changed. Click OK and confirm that Gozi can successfully sign in to PC02.
