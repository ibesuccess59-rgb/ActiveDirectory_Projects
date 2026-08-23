## LAB 9   Windows Server Backup & Active Directory Disaster Recovery

Objective
- Install Windows Server Backup.
- Create a backup of Active Directory.
- Enable Active Directory Recycle Bin.
- Delete a test user.
- Restore the deleted user.
- Verify the restored account works.

1. On DC01, open:
Server Manager → Manage → Add Roles and Features , Click Next until you reach:
Features , Check: Windows Server Backup
<img width="1674" height="1530" alt="1" src="https://github.com/user-attachments/assets/6f33edbc-f812-4864-95e0-e2dd5cfec0d9" />

2. Installation completed
<img width="1676" height="1284" alt="2" src="https://github.com/user-attachments/assets/cdd5e9e8-a03e-47cd-bea1-a0c2323f2156" />

3. Open: Server Manager → Tools → Windows Server Backup
<img width="1670" height="1475" alt="3" src="https://github.com/user-attachments/assets/6bf8bde2-9ded-4050-9ac0-90a8e8c5f2e8" />

4. Click on at the top left local backup , then  On the right side, click: Backup Once
<img width="1360" height="1318" alt="5" src="https://github.com/user-attachments/assets/d8aa6d61-8476-4e1c-bdfd-f4be7dfcb2ae" />

5. In backup option , select different option and click next
<img width="1360" height="1318" alt="5" src="https://github.com/user-attachments/assets/7996db84-8715-40e9-ab66-5a3a00f592fa" />

6. Here we choose custom , then we click on next
<img width="1358" height="1526" alt="6" src="https://github.com/user-attachments/assets/75668370-481b-477b-a01c-92bb61332eb1" />

7. Here we choose add items , Then in this interface we choose system state and click ok and click next 
 #Note .We choose System State because it includes important Active Directory information.
<img width="1374" height="1216" alt="7" src="https://github.com/user-attachments/assets/09385cf3-3ca7-4640-9de7-745bbc675010" />

8. In this specify destination type , we choose Remote shared folder , \\SUCCESSCOMPANYS\ADBackup . This is an external disk drive :E then we click on inherit , and click next
<img width="1384" height="1196" alt="8" src="https://github.com/user-attachments/assets/606ca5da-c4e5-461e-856b-047f5ab9bcbf" />

9. <img width="1366" height="1522" alt="9" src="https://github.com/user-attachments/assets/9505e7a8-6013-412f-a29f-a15135090805" />

10. On the confirmation page , click on backup
<img width="1210" height="1338" alt="10" src="https://github.com/user-attachments/assets/bee6d38e-16ac-45ae-ab83-3991fd7ad32d" />

11. Before the next part of this lab , a screenshot of a Verified Active Directory Recycle Bin: Confirmed that AD Recycle Bin is enabled for the SuccessCompany domain, allowing accidentally deleted Active Directory objects to be recovered
<img width="1228" height="1206" alt="11" src="https://github.com/user-attachments/assets/86ced92c-3cf5-434b-8225-02ddf08cf951" />

12. Backup successful on our external disk drive :E
<img width="1336" height="1086" alt="12" src="https://github.com/user-attachments/assets/a41eb249-3186-4ec9-a59b-366a9c12f9ae" />

13. Now we test recovery in our active directory , go to active directory and computers , right click on the user bob under IT administration , then click on delete
<img width="1370" height="1226" alt="13" src="https://github.com/user-attachments/assets/a9afd972-dce3-46f6-b592-927f13e711cb" />

14. Confirmation of Bob , being deleted
<img width="1360" height="1226" alt="14" src="https://github.com/user-attachments/assets/205f9358-5f2c-4d5c-9675-d1cb6df26668" />

15. To restore the user , go to active directory administrative center, then click on successcompany(local)
<img width="1366" height="1318" alt="15" src="https://github.com/user-attachments/assets/65bcabe7-a603-49cf-8c1f-9c4b77ed97cf" />

16. Double click on deleted objects
<img width="1374" height="1280" alt="16" src="https://github.com/user-attachments/assets/ffec4bee-b7a0-4614-aadc-706a94dd3f81" />

17. Select bob Marley
<img width="1398" height="1428" alt="17" src="https://github.com/user-attachments/assets/ff9de31d-dbaa-4427-821e-f64494cb070d" />

18. Select restore to , and click on IT administration
<img width="1396" height="1214" alt="18" src="https://github.com/user-attachments/assets/dedae673-bf72-4958-9d3e-d0ce40a1cf05" />

19. Bob Has been restored to our active directory users and computers 
<img width="1368" height="1218" alt="19" src="https://github.com/user-attachments/assets/c08e599f-1f5c-4a9a-b16f-20a44a5594d2" />
