<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- IIS and Management Console
- PHP Manager and Rewrite Module
- PHP 7.3.8
- VC Redist and MySQL
- HeidiSQL



<h2>Installation Steps</h2>

<h3>Create Virtual Machine in Azure</h3>

<p> 1. Create resource group (name it osTicket, for example, or whatever you choose)
  </p>  <img width="787" alt="osTicket Install_ResourceGroup" src="https://github.com/user-attachments/assets/c75dd21f-1eb5-4084-8825-3f6266c192e6">

<br />
<p>
<p>
<p> 2. Create an Azure Virtual Machine Windows 10, with 4 vCPUs (name the VM osTicket, for example, or whatever you choose). Choose the resource group you previously created. 
  </p> <img width="832" alt="osTicket_Create VM" src="https://github.com/user-attachments/assets/ae3f8d22-3d9a-46fa-8227-943a268609db">
  <p>
  <p> Username:admin (or whatever you choose) Password: osTicketPassword1! (or whatever you choose)
    <p>
  <img width="780" alt="osTicket_VM admin credentials" src="https://github.com/user-attachments/assets/d427263f-bdc9-4815-9cdd-681f3546e6c0">
  <p> Check the box at the bottom of the page and click "review + create". The next page should show a green "Validation passed" box. Click create at bottom of the page.
  <p><img width="162" alt="osTicket_Validation passed" src="https://github.com/user-attachments/assets/7e161002-dcdb-402f-ae4b-7affdf5e15e2">
</p>

<br />
3. Open this: https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6 We'll use these files to osTicket and some of the dependencies. 
<p>
<p>4. In the Azure portal, go to your virtual machine, locate and copy the VM's public IP address.</p>
<img width="640" alt="osTicket_Public IP" src="https://github.com/user-attachments/assets/59554b13-a073-4d36-8494-4d224db88880">
<p>
<p>  <h3>Use Remote Desktop Connection app to connect to your VM.</h3>
  <p>5. In your Remote Desktop app, paste the VM's IP address and login with the username and password made when creating the VM.</p>
<img width="467" alt="osTicket_RemoteDesktop" src="https://github.com/user-attachments/assets/c6153109-eb71-467c-88bb-4b56c2108581">

</p>
<h3>Install/Enable IIS in Windows</h3>
<p>6. In the search bar of the Windows VM, type control panel, choose programs, then choose "turn Windows features on and off.
Check Internet Information Services box and expand. Check Web Management Tools box, expand and check IIS Management Console<p>
<img width="412" alt="osTicket_Internet Info Services" src="https://github.com/user-attachments/assets/d8b1b931-7d15-408e-9a71-f6f700931b7c">
</p>Check World Wide Web Services box. Check Application Development Features box, expand and check CGI. Check Common HTTP Features box
</p><img width="426" alt="osTicket_World Wide Services" src="https://github.com/user-attachments/assets/40a9ddfb-7601-4931-813a-95d94bf269be">
<p> To make sure the webserver is installed, open a web browser on the VM and go to 127.0.0.1 and it should direct here
  <img width="975" alt="osTicket_LocalHostPage" src="https://github.com/user-attachments/assets/5874b953-ba46-4b37-b410-a51510c1781a">

  <h3>Install Files</h3>
<p>7. From the Installation Files, download and install PHP Manager for IIS and the Rewrite Module</p>
<p>8. Create the directory C:\PHP</p><img width="306" alt="osTicket_PHP Folder" src="https://github.com/user-attachments/assets/f50b6919-5993-4e1e-a2e5-3de17586968d">
<p>9. From the Installation Files, download PHP 7.3.8 and unzip the contents into C:\PHP</p>
<p>10. From the Installation Files, download ad install VC_redist.x86.exe</p>
<p>11. From the Installation Files, download and install MySQL 5.5.62<p>
<p>  - Choose Typical Setup ->
- Launch Configuration Wizard (after install) 
- Standard Configuration
- Password1
</p>
<h3>Internet Information Services (IIS) Manager</h3>
<p>12. Open IIS as an Admin</p>
<img width="750" alt="osTicket_Open IIS" src="https://github.com/user-attachments/assets/41e0a9f8-be1f-4a14-9eb8-94ad44183df9">
<p>
<p>13. Register PHP from within IIS</p>
<img width="306" alt="osTicket_PHP Manager" src="https://github.com/user-attachments/assets/038d7553-9045-4334-a39c-87c68ac83bf4">
<p>
<p>
<img width="495" alt="osTicket_RegisterPHP" src="https://github.com/user-attachments/assets/4bb78ab3-2268-4cd3-a5c1-3174c1a1feb2"><p>
  <img width="553" alt="osTicket_PHP Path" src="https://github.com/user-attachments/assets/62830ad6-0762-4dd8-9c4a-8417a57706d9">
<p>Open the php-cgi image and click ok</p>
</p><img width="697" alt="osTicket_PHP cgi" src="https://github.com/user-attachments/assets/8977a1b6-72cf-4ae7-bd1e-a4d81703d423">
<p> Click the name of the server then click restart</p>
<img width="690" alt="osTicket_Restart1" src="https://github.com/user-attachments/assets/ea347c19-6e3b-4bcd-8341-35386050894e">
<h3>Install osTicket</h3>
<p>14. Download osTicket from the Installation File Folder</p>
<p>15. Extract and copy "upload" folder to c:\inetpub\wwwroot</p>
<img width="705" alt="osTicket_wwwroot" src="https://github.com/user-attachments/assets/c9f2ff95-ef46-4c2a-a53b-c960c90a72d9">
<p>16. Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”</p>
<p>17. Open IIS, stop and restart the server</p>
<img width="690" alt="osTicket_Restart1" src="https://github.com/user-attachments/assets/ea347c19-6e3b-4bcd-8341-35386050894e">
<p><p>
  <p>
<p> 18. Go to sites > Default Website > osTicket. On the right, click "Browse *.80"</p>
<img width="627" alt="osTicket_Browse 80" src="https://github.com/user-attachments/assets/0407e08a-cb79-4c88-978f-ab137bee8e9f">
<h3>Enable Extensions</h3>
<img width="491" alt="osTicket_osBefore" src="https://github.com/user-attachments/assets/9cb624a9-590d-4f90-8021-4828ede1586f">

<p>19. Go back to IIS, sites -> Default -> osTicket
<p></p>Double-click PHP Manager
<p></p>Click “Enable or disable an extension”
<p></p>Enable: php_imap.dll
<p></p>Enable: php_intl.dll
<p></p>Enable: php_opcache.dll
 <p> <img width="315" alt="osTicket_PHP enable" src="https://github.com/user-attachments/assets/6c5ec822-b392-4e54-a93e-89fb5e0f97f8">
<p></p>Refresh the osTicket site in your browse, observe the changes
<p></p><img width="487" alt="osTicket_osAfter" src="https://github.com/user-attachments/assets/1dea1227-58e1-4fc5-859f-b676d9fc3735"><p></p>
<h3>Rename: ost-config.php</h3>
<p>20. From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</p>
<P></P>To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
<h3>Assign Permissions: ost-config.php</h3>
<p>21. Right click ost-config.php and choose Properties. Click the security tab and choose Advanced. Disable inheritance -> Remove All Permissions -> Apply -> Yes -> Ok</p>
<p>In the properties menu, click Edit</p>
<img width="350" alt="osTicket_NewPermissions" src="https://github.com/user-attachments/assets/96a1f5f9-f1e4-4200-9512-117639e58c88">
<p>Click Add, type everyone in the text box and click Check Names > ok > check Full Control > Apply > ok</p>
<h3>Continue Setting up osTicket in the browser</h3>
<p>22. Click Continue in osTicket Installer</p>
<p> Name: Helpdesk</p>
<p> Default email (receives email from customers)</p>
<p>23. From the Installation Files, downlod and install HeidiSQL</p>
<p> 24. Open HeidiSQL > Create a new session<p>
  <img width="254" alt="osTicket_Heidi" src="https://github.com/user-attachments/assets/0d3d64e6-8309-4853-8451-0ad2afcf1f4c">

  <p>Username: root. Password: Password1 > connect to the session <p>
    <p>Create a database called osTicket</p>
    <img width="447" alt="osTicket_Database" src="https://github.com/user-attachments/assets/d15b7baf-f1e7-449b-9fa1-c458b18d95c0">
    <h3>Continue Setting Up osTicket in Browser</h3>
    <p>25. MySQL Database: osTicket<p>
<p>MySQL Username: root<p>
<p>MySQL Password: Password1<p>
<p>Click “Install Now!”<p>
<img width="570" alt="osTicket_InstallNow" src="https://github.com/user-attachments/assets/9618d443-b4bc-427d-8b51-178118f058f1">
<h2>Congratulations, you installed osTicket!</h2>
<p>Browse to your help desk login page: http://localhost/osTicket/scp/login.php<p>

<p>End Users osTicket URL:
http://localhost/osTicket/<p>

<p>Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
<p></p>Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>













