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

