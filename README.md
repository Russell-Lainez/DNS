![image](https://github.com/user-attachments/assets/f89dd5d5-7c63-4239-a373-6945f8145066)

<h1>DNS and DNS Manager Demonstration</h1>
In this demonstration, I will show how to utilize DNS and DNS Manager to locate computer resources through verifying A-Records, relying on the DNS cache, and creating a CNAME. 


<h2>Environments, Applications, and Services Used </h2>

- Microsoft Azure (Virtual Machines/Virtual Network)
- Remote Desktop
- Client Computer: Windows 10Pro (22H2)
- Domain Controller: Windows Server 2022 Datacenter
- DNS Manager 
- PowerShell
  
![image](https://github.com/user-attachments/assets/199bc314-b926-49fa-b3d7-d24d02e765a7)

<h2>Walkthrough</h2>

<h3>Creating and Verifying DNS A-Records</h3>

1. While logged in as an administrator in the client profile, I opened PowerShell to ping “mainframe.” Expectedly, I received an error which indicates “mainframe” was not found on the DNS local cache, Host File, or the DNS server.

![image](https://github.com/user-attachments/assets/0354a5b1-992e-49f1-ae69-2e5937eafcd4)

2. Within the domain controller, I opened DNS manager and created an A-record named mainframe with the IP address of the domain controller (10.0.0.4).

![image](https://github.com/user-attachments/assets/679f0468-6113-4999-84cf-e16822f8b96a)

3. To verify the A-record, I went back to the client computer and typed “nslookup mainframe” and “ping mainframe” to check the record. With the newly created A-Record, I successfully received back the private IP address of the domain controller.

![image](https://github.com/user-attachments/assets/178128d4-2863-493a-87cb-ac7439d9520a)

<h3>Utilizing and Clearing DNS Cache</h3>

1. To show how DNS cache functions, I changed the “mainframe” A-record to the random IP address of 8.8.8.8.

![image](https://github.com/user-attachments/assets/68f8b12c-5882-4807-ac01-06cacc9736c1)

2. I pinged the main from the client computer and verified it still provided the IP address of 10.0.0.4.
   
![image](https://github.com/user-attachments/assets/042581f1-5f18-4aa7-bb2a-3be97342140b)


3. I typed “ipconfig /flushdns” to clear out the local cache.

![image](https://github.com/user-attachments/assets/c12522fd-5e80-4f63-9fbd-bae484f3faa3)

4. I pinged the mainframe again and now see the new IP address (8.8.8.8).

![image](https://github.com/user-attachments/assets/3eca77cf-4ea1-449b-80fa-fa5cf67cddc3)

<h3>CNAME Record</h3>

1. To create a CNAME record, I went to the domain controller and created an A-record called “search” under the alias www.google.com

![image](https://github.com/user-attachments/assets/d36af4a6-247d-4af6-98fc-5cf8861aa9b7)

2. Back in the client computer, I pinged “search” and received google’s IP address. I then typed “nslookup search” and checked the alias and verified it reflects the alias is my.domain.com

![image](https://github.com/user-attachments/assets/518709aa-ccd0-436e-b6b1-71b18cb4df58)










