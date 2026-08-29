## Lab 7 – Security Groups, Mapped Drives, and Personal Drives

## Objectives
- Create and manage Security Groups in Active Directory to control access to shared folders and network resources.
- Configure Mapped Drives to automatically provide users with access to shared network locations.
- Set up Personal Drives to give individual users secure storage within the domain.
- Apply security group-based permissions and access control best practices to simplify administration and improve resource security.

## Steps
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

32. Now we Test file permissions
Inside the IT folder:
Right-click an empty area.
Select New.
Select Text Document. Name the file:
IT-Test-Bob.txt
<img width="1336" height="1002" alt="32" src="https://github.com/user-attachments/assets/ab09502d-9bd5-4d25-b871-cfc74cf9b1fc" />

33.  Open the file.
Type a short sentence.
<img width="1300" height="956" alt="33" src="https://github.com/user-attachments/assets/e71cc148-9866-476c-b337-42299725214b" />

34. Rename the file to IT-TextExam-Bob.txt
<img width="1344" height="954" alt="34" src="https://github.com/user-attachments/assets/62e8f7b3-6110-4fa8-b3eb-7cc13ebdf309" />

35. Delete the file. This confirms that Bob has Modify access.
<img width="1346" height="996" alt="35" src="https://github.com/user-attachments/assets/866797d9-c076-4967-b629-ad5ae3b12902" />

36. Now Map the IT shared folder to a network drive on a domain-joined computer, allowing authorized users to access shared departmental resources through a drive letter while verifying that the assigned permissions function correctly.
<img width="1356" height="1004" alt="36" src="https://github.com/user-attachments/assets/9af595c3-d19f-4617-a20d-a811f4c0fb86" />

37. Configure the mapped drive
Under Drive, select:
I:
Under Folder, enter:
\\Successcompanys\it
<img width="1340" height="972" alt="37" src="https://github.com/user-attachments/assets/687fb5c8-a504-4098-8a2a-ccfc25c76f39" />

38. Confirm the mapped drive
Open This PC.
Confirm that the following drive appears:
IT (\\Successcompanys) (I:)
<img width="1370" height="1000" alt="38" src="https://github.com/user-attachments/assets/ba69455d-ea27-459c-8ee3-a63bacf713d0" />

39. Double-click the I: drive.
Now can Create another test file.
<img width="1334" height="988" alt="39" src="https://github.com/user-attachments/assets/b4c90850-eda4-4a1b-8197-85eef2903f62" />

40. and as well Edit and delete the file.
<img width="1372" height="976" alt="40" src="https://github.com/user-attachments/assets/1719247d-69d2-49e5-b5de-5993bcfacf9d" />

41. Now lets Automatically Map the IT Drive Using Group Policy
Automatically map the HR drive for users who belong to the HR security group.
Before testing this scenario, remove the manually mapped I: drive to prevent a conflict.
Remove the manually mapped drive
On PC02:
Open This PC.
Right-click the I: drive.
Select Disconnect.
<img width="1358" height="1016" alt="41" src="https://github.com/user-attachments/assets/ff5d9a38-9198-402d-8ab7-859cc18e4d47" />

42. Open Server Manager.
Select Tools.
Select Group Policy Management.
Expand:
Forest: SuccessCompany.com
Domains
SuccessCompany.com
<img width="1368" height="1558" alt="42" src="https://github.com/user-attachments/assets/6e1a7a45-c58a-4378-b453-6e64faa0cc23" />

43.  Right-click the IT OU.
Select Create a GPO in this domain, and Link it here.
Enter:
IT Mapped Drive Policy
Select OK.
<img width="1366" height="1478" alt="43" src="https://github.com/user-attachments/assets/e281f1a9-d771-4e9b-9247-3d96d4ca4116" />

44. screenshot showing the GPO linked to the IT Admin OU.
<img width="1362" height="1186" alt="44" src="https://github.com/user-attachments/assets/0dc2a352-af61-4f2a-8518-9cdf4fee3836" />

45. Open the Drive Maps section
Right-click IT Mapped Drive Policy.
Select Edit.
Navigate to:
User Configuration
Preferences
Windows Settings
Drive Maps
<img width="1352" height="1378" alt="45" src="https://github.com/user-attachments/assets/23501d9d-38a3-4246-803b-614a88d72737" />

46. Create the mapped drive preference
Right-click Drive Maps.
Select New.
Select Mapped Drive.
Under Action, select: Update
In Location, enter:
\\Successcompanys\IT
In Label as, enter: IT Admin Department Drive
Under Drive Letter, select:
Use I:
Check: Reconnect
Click apply and okay
<img width="1372" height="1562" alt="46" src="https://github.com/user-attachments/assets/61ae94f1-a75f-42b0-8f76-da49e31fe18f" />

47. Configure item-level targeting
Open the Common tab.
Check:
Item-level targeting
<img width="1368" height="1352" alt="47" src="https://github.com/user-attachments/assets/422d1923-0188-475a-ba9d-8f8d8c5fd701" />

48. Select Targeting.
Select New Item.
Select Security Group.
Under Group, select the browse button.
Enter: IT
Select Check Names.
Select OK.
<img width="1362" height="1524" alt="48" src="https://github.com/user-attachments/assets/58a6cd60-24c5-4b6d-a31e-aee5e16b950c" />

49. screenshots showing:
The mapped drive settings
The I: drive letter
The IT security group in item-level targeting
<img width="2190" height="1072" alt="49" src="https://github.com/user-attachments/assets/e4337560-a023-4c9b-a184-e8cbe31afafe" />

50. On PC02, sign in as Bob.
Open Command Prompt and run:
gpupdate /force

When the update completes
Sign out.
Sign back in as Bob.
Open This PC.
Confirm that I: appears automatically.
<img width="1362" height="1008" alt="50" src="https://github.com/user-attachments/assets/fba74087-8893-44ed-a62f-f39a57a2ee61" />

51. <img width="1368" height="988" alt="51" src="https://github.com/user-attachments/assets/03f46e51-18e3-4f65-a380-793c11943a87" />

52. Create the Personal Drives Root Folder
Objective
Create a central location where each domain user receives a private personal folder.
A Personal Drive (also called a Home Drive) is a private network folder assigned to an individual user. It provides each user with their own secure storage location on a file server. Create the Personal folder

On DC01:
Open: C:\Shares

Create a new folder named:
Personal
<img width="1380" height="1634" alt="52" src="https://github.com/user-attachments/assets/089616fd-474c-470e-acdd-9bcd34160549" />

53. Right-click the Personal folder.
Select Properties.
Open the Sharing tab.
Select Advanced Sharing.
Check Share this folder.
Confirm the share name is:
Personal
<img width="1310" height="1658" alt="53" src="https://github.com/user-attachments/assets/e010f434-6672-4c39-9cb4-270df6b2b88c" />

54. Select Permissions.
Configure share permissions
Remove Everyone.
<img width="1364" height="1526" alt="54" src="https://github.com/user-attachments/assets/2d847bfb-3ef9-495f-8b1c-9cf13869e9f6" />

55.   Select Add.
Add : Personal-Drive-Users
<img width="1364" height="1414" alt="55" src="https://github.com/user-attachments/assets/ddc1f09c-9fb2-4ddc-b456-9ec1cf5da9c6" />

56. Allow:
Change
Read
<img width="1366" height="1348" alt="56" src="https://github.com/user-attachments/assets/2b378d09-6d0c-4603-97d3-784938a832e5" />

57. Add HelpDesk01
Allow:
Change
Read
Select Apply.
Select OK. Note the network path is  \\Successcompanys\Personal
<img width="1032" height="1232" alt="57" src="https://github.com/user-attachments/assets/23b34c75-6edd-42e3-b406-64661fee4c5f" />

58. Configure advanced NTFS permissions
Open the Security tab.
Select Advanced.
Select Disable inheritance.
<img width="1380" height="1332" alt="58" src="https://github.com/user-attachments/assets/a6a910d7-b5d0-4e1e-a18f-a8ba19c7e551" />

59. Select: Convert inherited permissions into explicit permissions
 Keep:
SYSTEM
Administrators
Domain Admins, if listed
<img width="1376" height="1432" alt="59" src="https://github.com/user-attachments/assets/120018b9-a9c5-46cd-8d8a-84ddd2d70836" />

60. Remove standard entries that would allow all users to access every personal folder.
<img width="1349" height="1442" alt="60" src="https://github.com/user-attachments/assets/6d4ef1f1-3c5c-4eab-aa70-2df1609ad623" />

61. Add Personal-Drive-Users permissions
Select Add.
Select Select a principal.
Enter:
Personal-Drive-Users
Select Check Names.
Select OK.
<img width="1360" height="1424" alt="61" src="https://github.com/user-attachments/assets/ee452b0c-57b8-4d6e-b97e-46135cc08b2d" />

62. Under Applies to, select : This folder only
<img width="1366" height="1048" alt="62" src="https://github.com/user-attachments/assets/a865cb7c-a897-41be-9701-a03eb2592b8a" />

63. Select Show advanced permissions if needed.
Allow:
List folder/read data
Read attributes
Read extended attributes
Create folders/append data
Read permissions
Select OK.
This allows users to access the root and create their personal folder without allowing them to open another user’s folder.
<img width="1411" height="1322" alt="63" src="https://github.com/user-attachments/assets/3dd557dd-8fbd-413b-94e8-213cb36de4d8" />

64.  Add CREATOR OWNER
Allow:
Full Control
<img width="1228" height="1412" alt="64" src="https://github.com/user-attachments/assets/85c46409-9476-4134-b6f5-77075e7359bc" />

65. Add Help Desk access
Select Add.
Select Select a principal.
Enter HelpDesk01
Select Check Names.
Select OK.
Allow Modify.
Under Applies to, select:
This folder, subfolders and files
Select OK.
Select Apply.
Select OK.
<img width="1202" height="1482" alt="65" src="https://github.com/user-attachments/assets/2092c1d2-0d85-43fa-ac11-39da66d497db" />

66. Configure Helpdesk’s Personal Home Drive
Objective
Assign Gozi a personal folder that automatically maps as I: when Gozi signs in.
On DC01:
Open Active Directory Users and Computers.
Find Helpdesk.
Right-click Helpdesk.
Select Properties.
Open the Profile tab.
<img width="1372" height="1348" alt="66" src="https://github.com/user-attachments/assets/74a44730-d90f-4ba9-b68b-b52f18fa0289" />

67. Sign in to PC02 as Helpdesk01.
Confirm that I: appears under This PC.
Create a personal test file.
Confirm that the file is stored on DC01.
<img width="1380" height="882" alt="67" src="https://github.com/user-attachments/assets/cb242bdc-4b94-43cf-837f-ae201953455b" />







