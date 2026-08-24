## Lab 12 – Employee Offboarding & Access Revocation

Objectives

- Disable a departing employee’s Active Directory account to prevent further login.
- Reset the user’s password as an additional access-control measure.
- Create a Disabled Users OU to organize inactive employee accounts.
- Move the disabled account into the appropriate OU for administrative management.
- Preserve the user account for auditing instead of immediately deleting it.
- Verify account status using PowerShell and Get-ADUser.
- Demonstrate a basic employee offboarding and access-revocation workflow used in enterprise environments.

1. On DC01, open Active Directory Users and Computers.
   Find Gozi inside HR/ .Double-click Bob
<img width="1372" height="1540" alt="1" src="https://github.com/user-attachments/assets/633c70d5-6a36-481a-8d8b-d8a3c5aaf330" />

2. Disable the account
<img width="1400" height="1344" alt="2" src="https://github.com/user-attachments/assets/757ca1bd-f149-425b-82c1-21d970e08837" />

3.  Disabled confirmation
<img width="1372" height="1594" alt="3" src="https://github.com/user-attachments/assets/4e97d034-bc28-4bee-b177-6b6fbf4951f0" />

4. Select Reset Password.
Enter a new strong temporary password.
Confirm the password. #resetpassword1959
Click OK.
Because the account is disabled, Bob still cannot sign in.
<img width="1376" height="1574" alt="4" src="https://github.com/user-attachments/assets/51b4d077-7358-4174-8a78-0e0060b323df" />

5. Create a Disabled Users OU
This is to Separate inactive accounts from active employees.
Right-click:
successcompany.com
Select : New → Organizational Unit
Name it : Disabled Users
<img width="1352" height="1620" alt="5" src="https://github.com/user-attachments/assets/30ce2a0f-4bc3-43e2-b5fb-b50a4a5a12b6" />


6.  Move Bob to the Disabled Users OU
This is toOrganize the disabled account so administrators can easily identify former employees.
Find Bob in his current OU.
Right-click Bob.
Select Move.
Choose: Disabled Users
Click OK.
<img width="1372" height="1666" alt="6" src="https://github.com/user-attachments/assets/939be98d-5bce-471b-837b-76ec05fe2f24" />

7. Open the Disabled Users OU.
Confirm Bob appears there.
<img width="1370" height="1682" alt="7" src="https://github.com/user-attachments/assets/20be37e1-d14c-47b8-8f60-1a710184a6cd" />

8.  On DC.
On DC01, confirm BobMarley is disabled with powershell :
Get-ADUser BobMarley -Properties Enabled
<img width="1376" height="1324" alt="8" src="https://github.com/user-attachments/assets/ae505bbe-0c26-48e7-9616-a6f5df7294f4" />
