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

11. <img width="1134" height="764" alt="image" src="https://github.com/user-attachments/assets/d1044a96-aeb3-4471-a5a8-81c954891efc" />

<br />
12. Enter "User" as the name, skip the password creation, and click Next.
<br />
<img width="1158" height="840" alt="image" src="https://github.com/user-attachments/assets/e41d133f-f48b-4cbf-a498-681bb630d2dc" />
<br />

13. Now we should have our Windows 10 ready.
<br />    
