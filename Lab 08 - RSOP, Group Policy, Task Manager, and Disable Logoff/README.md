## Lab 08 - RSOP, Group Policy, Task Manager, and Disable Logoff

## Objectives
- Generate RSOP Reports: Use Resultant Set of Policy (RSOP) to verify and analyze the effective Group Policy settings applied to domain users and computers.
- Configure Group Policy: Create and apply Group Policy Objects (GPOs) to enforce administrative settings across domain-joined systems.
- Manage Task Manager: Configure Group Policy to control user access to Task Manager for security and administrative purposes.
- Disable the Log Off Option: Implement a Group Policy setting to remove or disable the Log Off option on domain-joined computers.
- Troubleshoot Group Policy: Use tools such as RSOP, gpupdate, and gpresult to verify policy application and diagnose Group Policy issues

## Steps
1. To do this, open Server Manager on your Windows Server 2022 account. Then, select Tools and click on Group Policy Management. In the Group Policy Management console, select Group Policy Objects under the SimoTech.com domain. From here, we can configure the Group Policy to disable Task Manager.
<img width="1644" height="1646" alt="1" src="https://github.com/user-attachments/assets/a1022332-7178-40da-856d-f659ae19be7e" />

2. Next, expand Group Policy Objects, right-click it, and select New to create a new Group Policy Object. Name the policy Task Manager and click OK. Once the policy has been created, select Task Manager under Group Policy Objects, then open the Delegation tab. Click Add, search for the Bob user account, and add it to the policy so the appropriate permissions can be assigned.
<img width="1950" height="1656" alt="2" src="https://github.com/user-attachments/assets/414db922-234c-4c4a-90c7-09da94325fcf" />

3. <img width="1740" height="1630" alt="3" src="https://github.com/user-attachments/assets/cb30ee24-7112-498d-b48b-e82155d71b20" />

4. Right-click on Task Manager, select Edit, then go to User Configuration → Clck on policies -> Administrative Templates → System. Next, select Ctrl+Alt+Del Options.
<img width="1336" height="1536" alt="4" src="https://github.com/user-attachments/assets/ce2b05e1-b628-4737-9f9e-b793284078dd" />

5. Here we will enable “Remove Change Password”
<img width="1328" height="1572" alt="5" src="https://github.com/user-attachments/assets/051974ab-78a7-4678-8dba-5b4ad7357ce1" />

6. and “Remove Task Manager”
<img width="1336" height="1624" alt="6" src="https://github.com/user-attachments/assets/67f09b46-1c59-4abb-be40-3120056f5d15" />

7. Then back on the Group Policy Management, grab the “Task Manager” and move it to “HR”. Select “Yes”
<img width="1328" height="1632" alt="7" src="https://github.com/user-attachments/assets/5ec70183-c8a0-40aa-83a0-10c3fb3cfd74" />

8. Select “Enforced” by right-clicking on it.
<img width="1334" height="1300" alt="8" src="https://github.com/user-attachments/assets/47d1c081-4a67-4168-ae25-af003296b066" />

9.  Now, on Gozi's account, which is under HR on PC02, open CMD and type the command gpupdate /force. This will immediately refresh the Group Policy settings for both the computer and user accounts.
<img width="1318" height="976" alt="9" src="https://github.com/user-attachments/assets/f13b4630-bdb6-4b7e-8d25-770e1234ece5" />

10. After updating the Group Policy on Gozi's computer, right-click on the taskbar, and you'll see that Task Manager is now greyed out, indicating that access has been successfully disabled.
<img width="1424" height="1436" alt="10" src="https://github.com/user-attachments/assets/772ab1d2-ac37-45b0-a892-a93caf24367b" />

11.  If we press Ctrl+Alt+Del on the virtual machine, we will see that the Change Password option has been removed, reflecting the changes made through Group Policy.
<img width="1422" height="1436" alt="11" src="https://github.com/user-attachments/assets/da0ba245-d174-4ac6-9a91-78fc1a2aba1e" />

12. To check which group policies have been applied to Gozi's computer, open the command line and type gpresult /r. This will display the results of the Group Policy settings for both the computer and user accounts.
<img width="1434" height="1436" alt="12" src="https://github.com/user-attachments/assets/0e8cdccd-ba37-4dda-8312-2f3c58dc6c04" />

13. If you type taskmgr in the command line, a prompt will appear stating that Task Manager is disabled, confirming that the Group Policy to disable Task Manager has been successfully applied.
<img width="1428" height="1458" alt="13" src="https://github.com/user-attachments/assets/ad0b04da-7062-4aea-96ef-638c7752aabc" />

14. If you run Command Prompt as Administrator and then type taskmgr, Task Manager should open, as administrative privileges can bypass the policy restrictions applied to regular users.
<img width="1418" height="1482" alt="14" src="https://github.com/user-attachments/assets/62269e44-01e3-41fb-84cd-66a45a0be755" />

15. To generate a Group Policy report, go to Group Policy Management, right-click on Group Policy Results, and select Group Policy Results Wizard.... This will guide you through the process of generating a detailed report on the applied Group Policy settings.
<img width="1298" height="1604" alt="15" src="https://github.com/user-attachments/assets/9527744e-d20e-47e5-bf7a-e1870e89c395" />

16. Click Next, then select Another Computer and click Browse. Type in SuccessCompany\PC02 and select it.
<img width="1304" height="1162" alt="16" src="https://github.com/user-attachments/assets/69d228a8-b77f-4a68-b814-91e4e36fb6f7" />

17. After Clicking on Next , It failed to connect , It says ensure that the Windows management instrumentation service is enabled  on target computer.
<img width="1300" height="1170" alt="17" src="https://github.com/user-attachments/assets/0f4f060d-8fdb-43f2-bf1c-272bc2aeb98c" />

18. So we used  Enable-NetFirewallRule -DisplayGroup "Windows Management Instrumentation (WMI)" to Enable WMI Firewall Rules on gozi's account pc02
<img width="1332" height="964" alt="18" src="https://github.com/user-attachments/assets/03d4af8d-8d65-4560-9c7c-f0d0ebee39df" />

19. After enabling the WMI with powershell , we click next , then select the user Successcompany\Gozi , then click next again and finish the group policy result wizard
<img width="1344" height="1148" alt="19" src="https://github.com/user-attachments/assets/b84fa8c6-838e-4b3d-a590-853854bedce9" />

20. This will generate a report for Bob's Group Policy settings.
<img width="1312" height="1170" alt="20" src="https://github.com/user-attachments/assets/1e9480c4-b86c-4e6b-af81-9ab66065fc20" />

21. <img width="1312" height="1170" alt="20" src="https://github.com/user-attachments/assets/0f11722f-8831-4b34-ab7c-8d8c67ec7610" />

We have successfully leveraged RSOP commands, explored Group Policy settings, utilized Task Manager, disabled logoff functionality, removed the ability to change passwords, and restricted access to Task Manager and troubleshooting enabling the WMI with powershell.


