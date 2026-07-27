## Lab 2   Renaming Windows Server 2022 and Installing Active Directory

Now that the Windows Server 2022 virtual machine has been deployed, we can begin preparing it for the Active Directory Domain Services (AD DS) installation. As part of the initial server configuration, we'll first rename the computer to a descriptive hostname. This makes the server easier to identify within the network environment. To rename the server, open File Explorer, right-click This PC, and choose Properties.


## Objectives
-  Rename a Windows Server 2022 instance to meet organizational standards.
-  Install and configure Active Directory Domain Services (AD DS).
-  Create and manage user accounts, groups, and security policies within Active Directory.


## Documentation
1.  With Windows Server 2022 successfully installed, we can now begin configuring the server for our Active Directory home lab. Before installing the Active Directory Domain Services (AD DS) role, we'll rename the computer to a more descriptive hostname. To do this, open File Explorer, right-click This PC, and select Properties.

<img width="1056" height="812" alt="1" src="https://github.com/user-attachments/assets/407c4d01-f25c-4b57-9d27-227cb00b2008" />

2.  Click on properties

<img width="1028" height="784" alt="2" src="https://github.com/user-attachments/assets/647557ef-1564-4374-818d-9c273681339f" />

3.   In the "About" section, scroll down until you see "Rename this PC    
   (Advanced)" and click on it.

<img width="1042" height="796" alt="3" src="https://github.com/user-attachments/assets/f6697de7-b0b6-4984-af25-93c70e12d97b" />

4. Changed the server name to SuccessCompanyServer
   
   <img width="1296" height="778" alt="4" src="https://github.com/user-attachments/assets/997524d9-86d4-498d-baf2-ad34221d4a8b" />

5. A prompt will appear asking you to restart your virtual machine, which is 
   normal. Click "OK," then select "Restart Now" to apply the changes.

   <img width="1086" height="1020" alt="5" src="https://github.com/user-attachments/assets/dd763e76-da05-4061-b7b5-6aafdab78b1b" />

6. After restarting the virtual machine, sign in using the Administrator account. To confirm that the hostname change was successful, open File Explorer, right-click This PC, and select Properties. The Full computer name should display 	SuccessCompanyServer, indicating that the server has been successfully renamed and is ready for the next stage of the Active Directory configuration.

<img width="1024" height="776" alt="6" src="https://github.com/user-attachments/assets/d82e8578-2501-40ed-ae6b-6e7e17305144" />

7. To maximize system resources for our virtual lab, we'll configure Windows Server to prioritize performance. Open the Search bar, type About your PC, and select Advanced system settings. Under the Performance section of the System Properties window, click Settings. In the Performance Options window, select Adjust for best performance, then click Apply and OK. Disabling unnecessary visual effects helps reduce resource consumption and improves the overall responsiveness of the virtual machine.

<img width="1018" height="770" alt="7" src="https://github.com/user-attachments/assets/13da0a08-d0d7-44b4-b841-fe5f6f0f2cf3" />


8.<img width="1032" height="768" alt="8" src="https://github.com/user-attachments/assets/54788f73-6839-4716-b9f4-b25e158e110e" />


9.<img width="1022" height="784" alt="9" src="https://github.com/user-attachments/assets/f4836985-232e-48ec-a65e-97639f932998" />


10. <img width="1026" height="778" alt="10" src="https://github.com/user-attachments/assets/998f4ba5-3641-4a63-acea-4adf3d53d5fa" />


11. <img width="1018" height="774" alt="11" src="https://github.com/user-attachments/assets/655e6bdb-9811-47a1-914e-fc5588c3aeb5" />


12. <img width="1014" height="776" alt="12" src="https://github.com/user-attachments/assets/4728c94e-07c0-4a83-b13a-5953f23d273b" />


13. <img width="1036" height="772" alt="13" src="https://github.com/user-attachments/assets/dc4570b3-d243-4fb3-b894-a1501da9214b" />


14.<img width="1032" height="770" alt="14" src="https://github.com/user-attachments/assets/a34195cc-bd7b-420a-a463-c6ea085ac697" />


15. Select "Active Directory Domain Services," then click "Add Features" when prompted. After that, click "Next" to continue.
    <img width="1046" height="780" alt="15" src="https://github.com/user-attachments/assets/6b356cb3-fded-4c9a-a191-63800eec5579" />














