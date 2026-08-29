## LAB 1 - Installing Virtual Box and Windows Server 2022

This documentation outlines the first phase of my Active Directory Home Lab project, which involves setting up the virtualization environment. Before deploying Windows Server, the required tools must be downloaded and installed.

## Objectives
This repository documents a comprehensive home lab project focused on installing and configuring VirtualBox and Windows Server 2022. The key objectives include:

- Demonstrating the setup and installation process of VirtualBox as a virtualization platform.
- Installing and configuring Windows Server 2022 in a virtualized environment.
- Creating a foundation for further experiments involving Active Directory, system administration, and IT operations.

## Steps

In this documentation, I will outline the initial steps of setting up my Active Directory home lab. This includes downloading and preparing the essential tools: VirtualBox and Windows Server 2022.


1.   The process begins by downloading Oracle VirtualBox from the official website (https://www.virtualbox.org/wiki/Downloads). As my host operating system is Windows, I selected the Windows hosts installation package. VirtualBox will serve as the virtualization platform used to host all virtual machines throughout this project.

<img width="1422" height="1678" alt="1" src="https://github.com/user-attachments/assets/6b1dce8b-e330-422f-93cf-6f85a2ec9972" />
   
   
3.   Next, we’ll download Windows Server 2022 from the official Microsoft Evaluation Center at https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2022.

<img width="1436" height="1634" alt="2" src="https://github.com/user-attachments/assets/d5850db8-bd9e-4cea-b51c-ce425cd812a0" />


4.  To download the Windows Server 2022 evaluation, you will need to complete the registration process by providing the required information. Microsoft offers a 180-day free evaluation, allowing you to explore and test the operating system without a license.
   <img width="1444" height="1618" alt="3" src="https://github.com/user-attachments/assets/93f769a2-9885-4299-8d99-2238d5fe4052" />

   
5. After filling our information, we can finally download the ISO which will be the 64-bit edition (English).                                                                                                                                                 <img width="1452" height="1614" alt="4" src="https://github.com/user-attachments/assets/cd5cc879-9973-4f3a-bc65-ddf492406908" />

6. Finally our windows server ISO download and Virtual box is in our downloads folder.

<img width="1424" height="1686" alt="6" src="https://github.com/user-attachments/assets/560acc40-ba1a-426f-b614-209653fca7b1" />

7. Once all the required files have been downloaded and installed, launch Oracle VirtualBox to begin configuring the virtual environment for Windows Server 2022. From the VirtualBox menu, click Machine and select New to create a new virtual machine

<img width="1424" height="1686" alt="6" src="https://github.com/user-attachments/assets/2a0ee66c-3752-441f-92cf-e68fa486a913" />

8. Begin by assigning a name to the virtual machine. For this project, I will use "Success Windows Server 2022 Lab." Next, under the ISO Image section, click the dropdown menu and select Other. Browse to the Downloads folder, locate the Windows Server 2022 ISO file that was downloaded earlier, and select it. This will attach the installation media to the virtual machine, allowing us to install the operating system in the next step.

<img width="1432" height="1684" alt="7" src="https://github.com/user-attachments/assets/befd1919-57cd-45f9-a57f-8fc74427091a" />

9.  Next, click on "Skip Unattended Installation." Then, proceed to configure the hardware settings for the virtual machine.

<img width="1464" height="1692" alt="8" src="https://github.com/user-attachments/assets/5d5e9d7a-41fe-4453-bd11-4f4ee6172972" />

10.   By default, the base memory is set to 2048 MB, which is enough to install and run Windows Server 2022. However, since my computer has 16 GB of RAM, I'll increase the allocation to 4096 MB (4 GB) to provide better performance for my Active Directory home lab while ensuring my host operating system continues to run smoothly. To check how much RAM your computer has, open Task Manager, navigate to the Performance tab, and select Memory. There, you'll be able to see your total installed RAM and decide how much memory you can safely allocate to your virtual machine

<img width="1948" height="1154" alt="9" src="https://github.com/user-attachments/assets/72667cbb-6f32-4ad2-9e3f-9edc1b6dbc51" />

10. We would also use 2 cpu's

<img width="1550" height="1058" alt="10" src="https://github.com/user-attachments/assets/311566f0-d6ad-46d1-b58b-7a0c6ff4c18b" />

11. 50gb for hard disk is perfect. Now we click on " create a virtual hard disk now " then click "finish"

<img width="1560" height="1074" alt="11" src="https://github.com/user-attachments/assets/cdc50e60-77c8-4e08-830b-2129f471609f" />

12.  Now we boot by clicking the start button

<img width="1324" height="1610" alt="12" src="https://github.com/user-attachments/assets/de9db877-46ec-4e6b-8709-1c4a89b5fc47" />

13.  Click "Next," then select "Install Now" to begin the installation process.

<img width="1190" height="1390" alt="13" src="https://github.com/user-attachments/assets/3dab51f3-9fea-45bf-a69d-6afcda065d60" />

14 Click on Install

<img width="1166" height="1088" alt="14" src="https://github.com/user-attachments/assets/ee6041d4-6d23-4588-a3fd-2c9d3befff4d" />

15 In the operating system selection screen, choose "Windows Server 2022 Standard Evaluation (Desktop Experience)," then click "Next" to continue.

<img width="1290" height="1566" alt="15" src="https://github.com/user-attachments/assets/17fd46fa-70af-429c-9a13-fc7ae76d8d85" />

16 Accept the terms and click "Next." In the next step, when prompted to choose the type of installation, 

<img width="1240" height="1512" alt="16" src="https://github.com/user-attachments/assets/19d5c3cf-58f1-439b-bb92-5c2070bae129" />

17. select "Custom" to proceed

<img width="1266" height="1520" alt="17" src="https://github.com/user-attachments/assets/8e76a978-1a55-470f-a208-77ab85e36b4e" />

18. Click "Next," and the installation of Windows Server will begin.

<img width="1242" height="1496" alt="18" src="https://github.com/user-attachments/assets/d8905bed-6988-44f1-93a5-59e903e02954" />

19. Installing Microsoft server operating system

<img width="1244" height="1510" alt="19" src="https://github.com/user-attachments/assets/b4e19bdb-1d09-442b-885b-5cbf3c521a17" />

20. Create a password for our account “Administrator”.

<img width="1214" height="1402" alt="20" src="https://github.com/user-attachments/assets/ddeac309-8c7f-4205-92f1-da41b2174c1c" />

21. press Ctrl + Alt + Del" to bring up the login screen. After entering your password, you can log into your Windows Server 2022 account as the administrator.

<img width="980" height="1546" alt="21" src="https://github.com/user-attachments/assets/c0a1d74b-857b-45c9-9a14-01ba7c272e36" />

22. we have now successfully installed Windows Server 2022 and Virtual Box!

<img width="1220" height="1624" alt="22" src="https://github.com/user-attachments/assets/b104d913-4c96-4f4d-a93a-871a5473bb80" />

## Conclusion

In this lab, I successfully set up the virtualization environment that will be used throughout my Active Directory Home Lab series. I learned how to install Oracle VirtualBox, download and deploy Windows Server 2022, configure virtual machine hardware settings, and complete the Windows Server installation process. This lab provided the foundation required for building an enterprise-style Windows Server environment and prepared me for the next phase of the project, where I will configure Active Directory Domain Services (AD DS) and promote the server to a Domain Controller.

## Skills Demonstrated
-   Oracle VirtualBox Installation
-   Windows Server 2022 Installation
-   Virtual Machine Configuration
-   Virtual Hardware Management (CPU, RAM, Storage)
-   ISO Deployment
-   Windows Server Administration Fundamentals
-   Technical Documentation













   









