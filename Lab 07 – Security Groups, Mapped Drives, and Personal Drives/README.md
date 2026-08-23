## Lab 7 – Security Groups, Mapped Drives, and Personal Drives

## Objectives
- Create and manage Security Groups in Active Directory to control access to shared folders and network resources.
- Configure Mapped Drives to automatically provide users with access to shared network locations.
- Set up Personal Drives to give individual users secure storage within the domain.
- Apply security group-based permissions and access control best practices to simplify administration and improve resource security.

1. Open Server Manager.
Select Tools in the upper-right corner.
Select Active Directory Users and Computers.
Expand the SuccessCompany.com domain.
Open the Organizational Unit where you want to store the groups ,we name it Security Groups.
<img width="1366" height="1602" alt="1" src="https://github.com/user-attachments/assets/0fc6bc8a-5d11-47a8-90ae-4ede32c38092" />

2. Right-click the selected OU.
Select New.
Select Group.
In the Group name field, enter:
IT management
Under Group scope, select:
Global
Under Group type, select:
Security
Select OK.
<img width="1366" height="1640" alt="2" src="https://github.com/user-attachments/assets/ea99196f-b814-4fb7-9eb0-7f89717fe546" />

3. Right-click the same OU.
Select New.
Select Group.
Enter:
Personal-Drive-Users
Select Global under Group scope.
Select Security under Group type.
Select OK.
<img width="1368" height="1630" alt="3" src="https://github.com/user-attachments/assets/bbdcc2ce-b2ce-4a3e-a682-ad65abcfdfb5" />

4. Now we Assign the user HelpDesk01 as the manager of the IT Management group
Double-click the HR group.
Open the Managed By tab.
Select Change.
Enter: HelpDesk01
<img width="1356" height="1622" alt="4" src="https://github.com/user-attachments/assets/ca2621a2-0ce9-48a8-a2ae-e073d84a7600" />

5. This confirms IT management OU is now managed by helpdesk
<img width="1368" height="1640" alt="5" src="https://github.com/user-attachments/assets/9767bae6-e533-4769-acd7-c28c7671eca5" />

6. Check Manager can update membership list if you want HelpDesk01 to manage group membership.
Select Apply.
Select OK.
<img width="1374" height="1574" alt="6" src="https://github.com/user-attachments/assets/8bdc84d5-06d8-4a8b-88d3-d1e694aae12f" />

7. Assign HelpDesk01 as the manager of Personal-Drive-Users
Double-click Personal-Drive-Users.
Open the Managed By tab.
Select Change.
Enter HelpDesk01.
<img width="1376" height="1648" alt="7" src="https://github.com/user-attachments/assets/a783ca94-cfb0-4835-8c86-d285b201a51c" />

8. This confirms Personal-Drive-users is managed by helpdesk01
<img width="1372" height="1664" alt="8" src="https://github.com/user-attachments/assets/d918c42f-de9d-49c2-be19-02d075cf0e7e" />

9. Check Manager can update membership list.
Select Apply.
Select OK.
<img width="1368" height="1678" alt="9" src="https://github.com/user-attachments/assets/4dd3aa9a-038d-4e68-a7bf-be2408e8e7d8" />

10. Now we add another user in It
<img width="1372" height="1646" alt="10" src="https://github.com/user-attachments/assets/7b6fdc07-8b26-4b8b-a9a8-7a502eb14855" />

11.  I created a new user Bob in IT Admin OU , Add bob to the IT management Security group
Double-click the IT management group.
Open the Members tab.
Select Add.
Enter: Bob
<img width="1376" height="1606" alt="11" src="https://github.com/user-attachments/assets/5993be9a-ee9b-4cf6-95be-aa72d9262314" />

12. Now this confirms Bob has joined the It management security groups
Select Apply.
Select OK.
<img width="1368" height="1616" alt="12" src="https://github.com/user-attachments/assets/cc9aeb01-4fcc-4c73-aaeb-c10c246b38d3" />

13. Add Bob to Personal-Drive-Users
Double-click Personal-Drive-Users.
Open the Members tab.
Select Add.
Enter Bob , click on checknames which confirms the user gozi
then click on ok
<img width="1370" height="1640" alt="13" src="https://github.com/user-attachments/assets/5aaa515c-3282-49fb-8698-14f56ad68fc5" />

14. Select Apply.
Select OK.
<img width="1366" height="1658" alt="14" src="https://github.com/user-attachments/assets/afd587c8-e28d-4cb9-9931-f7a398787e49" />

15. Create the 	IT folder
On DC01:
Open File Explorer.
Open This PC.
Open the C: drive.
Create a folder named: Shares
<img width="1366" height="1660" alt="15" src="https://github.com/user-attachments/assets/a7ced78d-742b-4da5-8322-02c1cd9256d0" />

16. Open the Shares folder. Create another folder named: IT
<img width="1362" height="1668" alt="16" src="https://github.com/user-attachments/assets/6287f5ba-54de-4061-9351-2be1a3f7a4ef" />

17. Right-click the IT folder.
Select Properties.
Open the Sharing tab.
Select Advanced Sharing.
Check Share this folder.
Confirm the share name is : IT
<img width="1360" height="1681" alt="17" src="https://github.com/user-attachments/assets/7b8e3b6a-3c4f-43a6-8c3d-27f995cf8875" />

18. Select Permissions, Configure share permissions
<img width="1366" height="1600" alt="18" src="https://github.com/user-attachments/assets/0d2e2484-4599-4954-891e-82407f495577" />

19. Remove Everyone if it is listed.
Select Add.
Enter:IT , Select OK
<img width="1366" height="1654" alt="19" src="https://github.com/user-attachments/assets/748cdfaa-ff6e-4cdc-bac2-244a32467837" />

20. Select the IT group , Under permission Allow : Change , Read
<img width="1364" height="1670" alt="20" src="https://github.com/user-attachments/assets/f51759f3-4fcb-435c-8323-6532d9cfc34c" />

21. Select Add again.
Add HelpDesk01
<img width="1242" height="1636" alt="21" src="https://github.com/user-attachments/assets/72711ca3-e99a-4b42-b72d-96b88995acd5" />

22. Under permission Allow: Change , Read. Select Apply.
Select OK.
Select OK again.
<img width="1256" height="1600" alt="22" src="https://github.com/user-attachments/assets/01aa48c1-7121-4839-93c8-50f8b1c90ac8" />

23. Network path is \\Successcompanys\it
<img width="1030" height="1502" alt="23" src="https://github.com/user-attachments/assets/b154970e-19d5-44c4-a0aa-426000438b4c" />

24. Now we Configure NTFS permissions ,In the IT folder properties, open the Security tab.
Select Advanced.
Select Disable inheritance.
<img width="1366" height="1626" alt="24" src="https://github.com/user-attachments/assets/f600e350-c694-4d9a-9ae9-cd1929d93a7e" />

25. Select: Convert inherited permissions into explicit permissions on this object
<img width="1376" height="1202" alt="25" src="https://github.com/user-attachments/assets/8a9c12a6-e00f-42dd-befc-8b02f3bd6d0a" />

26. Remove unnecessary standard user entries, such as:
Users
Authenticated Users
<img width="1370" height="1216" alt="26" src="https://github.com/user-attachments/assets/99178fce-9d30-47b2-aaf7-ee6e8a20b3b1" />

27. Select Add.
Select Select a principal.
Enter: IT , Check Names ,  Select OK.
<img width="1364" height="1592" alt="27" src="https://github.com/user-attachments/assets/4b367d25-1fc2-4d3c-99b1-550cab44845d" />

28.  Under Basic permissions, allow:
Modify
Read and execute
List folder contents
Read
Write , select OK
<img width="1370" height="1586" alt="28" src="https://github.com/user-attachments/assets/cce8896d-404d-484a-b34d-9daef9fc0dff" />

29. Add HelpDesk01 permissions
Select Add.
Select Select a principal.
Enter:
HelpDesk01
<img width="1372" height="1234" alt="29" src="https://github.com/user-attachments/assets/56be4d60-8900-4e20-b0ef-f7b99406a628" />

30. Allow Modify.
Select OK.
Select Apply.
Select OK.
<img width="1376" height="1406" alt="30" src="https://github.com/user-attachments/assets/b8b468d9-5239-496d-9a48-6af300d39e1a" />

31. Test the UNC path
On PC02:
Sign in as Bob.
Open File Explorer.
Enter: \\Successcompanys\it . Confirm the folder opens.
<img width="1370" height="972" alt="31" src="https://github.com/user-attachments/assets/39fd227c-6577-4e6b-86c6-c79312c1c0a7" />


















