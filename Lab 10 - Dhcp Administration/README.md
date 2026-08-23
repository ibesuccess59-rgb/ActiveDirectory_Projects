## LAB 10 DHCP Administration 

## Objectives
- Configure DHCP scopes.
- Configure reservations.
- Configure exclusions.
- Configure DHCP options.

1. Open Server Manager, Click Manage → Add Roles and Features, Click Next until you reach Server Roles. Check:DHCP Server
<img width="1380" height="1210" alt="1" src="https://github.com/user-attachments/assets/e6017643-0b6f-4c1f-9e73-55c4a70e2154" />

2. Click Add Features. Click Next → Install.
<img width="1360" height="1250" alt="2" src="https://github.com/user-attachments/assets/96bb1188-200b-494b-a2a1-f2b3a7175639" />

3. Fearured being installed , click on close after installation is completed.
<img width="1368" height="1214" alt="3" src="https://github.com/user-attachments/assets/8476c3b4-d643-4741-b4d7-8d877afea38c" />

4. Open DHCP Manager ,Go to: Server Manager → Tools → DHCP , click on successcompany , then click on IPv4
<img width="1386" height="1090" alt="4" src="https://github.com/user-attachments/assets/7387c987-19a7-4289-9bd1-8b24db25d1eb" />

5. To create new scope , Right-click IPv4. Select New Scope. Click Next.
Name it: SuccessCompany LAN
<img width="1386" height="1072" alt="5" src="https://github.com/user-attachments/assets/1565c54a-6b84-4e4e-8ed5-d32687863d3f" />

6. Configure the IP range
Use:
Start IP: 192.168.65.100
End IP:   192.168.65.200
Subnet Mask: 255.255.255.0
<img width="1384" height="1160" alt="6" src="https://github.com/user-attachments/assets/3eb1daf0-98b5-435e-a2dd-4e29e7de3217" />

7. Configure Exclusions, This Prevent DHCP from assigning addresses you want reserved for servers or infrastructure.
In the exclusion page, enter:
Start IP: 192.168.65.100
End IP:   192.168.65.120
Click Add.
This means dhcp will not lease those addresses , we can use them for things like DC , printers , servers , network devices 
<img width="1410" height="1136" alt="7" src="https://github.com/user-attachments/assets/a8be4c47-a48c-4ea4-b5e2-6f85c0b80ffe" />

8. We leave the lease duration as it is , on the configure dhcp options tab , click on next , On the router getway , we do not need on as we use NAT with our VMware so we leave it blank and click next
<img width="1370" height="1126" alt="8" src="https://github.com/user-attachments/assets/5c1fbd79-5e60-474f-85d1-212a604bec26" />

9. In the domain name and dns server , leave as is , click on next , In the WINS section , skip it and click next
<img width="1374" height="1442" alt="9" src="https://github.com/user-attachments/assets/8f85b361-03be-4b0a-89f1-d0b8ea3bc314" />

10. In activate scope , Choose: Yes, I want to activate this scope now , click next and then finish
<img width="1386" height="1540" alt="10" src="https://github.com/user-attachments/assets/5f71a370-5a5d-4582-a43d-43618d16b6e7" />

11. This is the active DHCP SCOPE WE CREATED
<img width="1366" height="1544" alt="11" src="https://github.com/user-attachments/assets/52996322-d86a-4596-8e98-e9a05ffb33cc" />

12. Now we confirm the DHCP SCOPE in PC02 ,

Go to Network and Internet → Network Connections.
Right-click the network adapter.
Select Properties. Double-click:Internet Protocol Version 4 (TCP/IPv4) ,

Obtain an IP address automatically
Obtain DNS server address automatically
<img width="1346" height="948" alt="12" src="https://github.com/user-attachments/assets/6267d4be-b74c-4f4d-82c7-16e8f6f869d7" />

13. Open Command Prompt and run: ipconfig /all , Our Address is now 192.168.65.132
<img width="1368" height="986" alt="13" src="https://github.com/user-attachments/assets/9ee8ed2c-db57-40a3-a3af-9564b995e36c" />










