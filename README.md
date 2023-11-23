
<p align="center">
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/app-hardening-banner.jpg" alt="osTicket logo"/>
</p>

<h1>Web Application Vulnerabilities</h1>
This tutorial outlines a application security engineer at Replicants, testing web vulnerabiltiies on new web applications created.<br />


<h2>Environments and Technologies Used</h2>

- Oracle VM (Virtual box)
- Vagrant

<h2>List of Prerequisites</h2>

- Dot dot slash attacks
- Web application vulnerability assessments
- Injection
- Brute force attacks
- Broken authentication
- Burp Suite
-Web proxies
-Directory traversal
-Beef
-Cross-site scripting
-Malicious payloads

<h2>Installation Steps</h2>

<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Enable%20ISS%20(Lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/ISS%20complete%20(Lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
World Wide Web Services -> Application Development Features -> [X] CGI. Checked by checking the local host, 127.0.0.1 to loot back.
</p>
<br />

<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Web%20Platform%20install%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Installed web platforms: PHP Manager for ISS, Rewrite module, PHP 7.3.8, VC_redist.x86.exe
</p>
<br />

<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/My%20SQl%20setup%20Typical%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Standard%20Configuration%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Root%20password%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Os%20ticket%20installer.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Install my SQL, Typical setup, Launch configuration WIzard (after install), Standard Configuration, Setup Root Password. What this does is installing a database for this computer. 
</p>
<br />

<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/configuring%20the%20osticket%20php%20manager%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/Assisging%20permissions%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/heidi%20sql%20server%20(lab%203).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/osticket-prereqs/blob/main/Diagrams/osticket%20successfully%20installed%20(lab3).png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back to IIS, sites -> Default -> osTicket, Double-click PHP Manager, Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Assign Permissions: ost-cofig.php, Downloaded and installed HeidiSQL, continued setting up osticket in the browser
</p>
<br />
