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















