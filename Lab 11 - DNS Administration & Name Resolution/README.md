Objectives:

- Configure Forward and Reverse Lookup Zones.
- Create and manage DNS A records and CNAME aliases.
- Configure secure dynamic DNS updates.
- Configure and verify PTR records for reverse name resolution.
- Test DNS name resolution using nslookup.
- Verify that clients can resolve hostnames and aliases to the correct IP addresses.
- Demonstrate basic DNS administration used in an Active Directory domain environment.

1. Open Server Manager.
Click Tools → DNS.
Expand DC01.
Expand Forward Lookup Zones.
Right-click Forward Lookup Zones.
Select New Zone.
<img width="1376" height="1186" alt="1" src="https://github.com/user-attachments/assets/c5ba4ec3-335c-4412-bdeb-d1c5d0aaa3e0" />

2. It takes us to the installation wizard of a new zone , click next , in zone type , choose primary zone.
<img width="1366" height="1532" alt="2" src="https://github.com/user-attachments/assets/119bb542-89fb-410c-8aca-33989769ad24" />

3. In the AD zone replication scope , choose to replicate to DNS servers in your domain. successcompanylab.com
<img width="1378" height="1536" alt="3" src="https://github.com/user-attachments/assets/ce02a5e4-1950-4646-b71c-f4f6c987a941" />

4. For Zone name , we use successcompanylab.com
<img width="1374" height="1444" alt="4" src="https://github.com/user-attachments/assets/b81678ef-3ac4-4afa-8037-179c2c0d73b9" />

5. Select Allow only secure dynamic updates if available. Click Next → Finish.
<img width="1368" height="1258" alt="5" src="https://github.com/user-attachments/assets/7b97e291-ce41-4f04-b7e2-6d0bcbbc0b47" />

6. Now we Create a Reverse Lookup Zone : A Reverse Lookup Zone does the opposite. It translates an IP address back into a hostname. In DNS Manager, right-click Reverse Lookup Zones. Select New Zone.
<img width="1402" height="1144" alt="6" src="https://github.com/user-attachments/assets/5e3969aa-8cad-484c-b073-91b7d5ade28d" />

7. In Zone type , we choose primary zone and click next
<img width="1390" height="1230" alt="7" src="https://github.com/user-attachments/assets/f752bfa0-bdc7-4d04-9a16-dd9b8e7fc9a2" />

8. In the active directory zone replication scope , Choose to all dns servers running on domain controller in this domain: successcompany.com
<img width="1390" height="1230" alt="8" src="https://github.com/user-attachments/assets/577d0db7-4e2d-41c5-ae80-7096a1051a58" />

9. In the reverse lookup zone name , choose ipv4 reverse lookup zone
<img width="1366" height="1448" alt="9" src="https://github.com/user-attachments/assets/36f38dd6-dd2f-43d0-9ada-2f52b7fda269" />

10. For the network ID , we use 192.168.65
<img width="1382" height="1160" alt="10" src="https://github.com/user-attachments/assets/62a33c4c-a248-4b45-abd9-9afa909d8153" />

11. In dynamic update , Select Allow only secure dynamic updates if available.
Click Next → Finish.
<img width="1384" height="1536" alt="11" src="https://github.com/user-attachments/assets/961e3863-a499-4967-9cee-0f7cdcd5e8ae" />

12. Create an A Record, An A record maps a hostname to an IPv4 address.
We'll create a fake file server entry for testing.
<img width="1390" height="1200" alt="12" src="https://github.com/user-attachments/assets/05612031-999d-44c4-8256-da11098a6584" />

13. Open DNS → DC01 → Forward Lookup Zones → successcompanylab.com
<img width="1372" height="1528" alt="13" src="https://github.com/user-attachments/assets/8f761ca9-b79a-43d0-8692-6311a5e0b0c5" />

14.  In the new host record  creation use , Name: FileServer
    IP address: 192.168.65.30. then click on add host
<img width="1374" height="1430" alt="14" src="https://github.com/user-attachments/assets/9cf87d7f-e4e4-41f7-bda5-43686fb3d0e2" />

15. Host record is succesfuly created.
<img width="1372" height="1440" alt="15" src="https://github.com/user-attachments/assets/b0128f66-4620-4c0b-acd0-eb757074bbcf" />

16. Click on the fileserver A record , click on properties and click on update associated pointer
<img width="1388" height="1190" alt="16" src="https://github.com/user-attachments/assets/2662fa80-03fd-4071-bf3e-0460de022eab" />

17. Create a CNAME Record ,A CNAME gives a computer or service an easier alias.
  Instead of users remembering:FileServer.successcompanylab.com
  You could let them use: Files.successcompanylab.com
  Right-click your successcompanylab.com zone.
<img width="1378" height="1536" alt="17" src="https://github.com/user-attachments/assets/d7b762c9-2782-43e9-8bbd-e9e8270784cd" />

18. Select: New Alias (CNAME)
    Alias name: Files
    For the fully qualified domain name of the target host, browse to or       	enter:FileServer.successcompanylab.com
    and click ok
<img width="1382" height="1540" alt="18" src="https://github.com/user-attachments/assets/29535d12-a93e-45d7-a92c-d9867a99cf3a" />

19. Confirmed CNAME
<img width="1380" height="1544" alt="19" src="https://github.com/user-attachments/assets/70fdfa06-43d0-41b5-8711-232f9da84b17" />

20. In DNS Manager, right-click DC01.
    Select Properties.
<img width="1364" height="1520" alt="20" src="https://github.com/user-attachments/assets/9eac893f-fbef-499b-abcf-3b626578a92f" />

21.  We put in nslookup FileServer.successcompanylab.com 192.168.65.10
    nslookup Files.successcompanylab.com 192.168.65.10.  command prompt result to prove our dns was successfully inputed.
<img width="1504" height="1296" alt="21" src="https://github.com/user-attachments/assets/b5399765-b143-4c5f-96c2-d52bd6fce37c" />








