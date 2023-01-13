**Project 2. - LEMP stack implementation**


**STEP 1 (INSTALLING NGINX)**

To begin this project I created a new instance and ssh into the instance on my terminal. 


<img width="1512" alt="Screenshot 2022-12-03 at 13 46 48" src="https://user-images.githubusercontent.com/114743648/212192079-ca55b57f-1d87-42be-a351-57c88c0e1210.png">

Then I had to update my servers package index using the code *sudo apt update*. This enabled me to install Nginx. I used the command *sudo systemctl status nginx* to see if Nginx was up and running and it was because it turned green.
<img width="1512" alt="Screenshot 2022-12-03 at 13 51 06" src="https://user-images.githubusercontent.com/114743648/212201601-6737b9f4-7a49-4b4e-aeaf-aebb593edf75.png">

Using the *curl* command I found my local IP <img width="1512" alt="Screenshot 2022-12-09 at 18 48 45" src="https://user-images.githubusercontent.com/114743648/212201919-c105389f-2117-49b6-96d2-8a25d448dd2a.png">
I edited my inbound rule and added HTTP.<img width="1512" alt="Screenshot 2022-12-09 at 19 06 30" src="https://user-images.githubusercontent.com/114743648/212202084-80da5b96-6458-4454-b182-e6e06fcb709e.png">

After this my nginx server was correctly installed.<img width="1512" alt="Screenshot 2022-12-09 at 19 07 42" src="https://user-images.githubusercontent.com/114743648/212202169-08217474-5a35-447d-9e2d-82baa1f06274.png">

**STEP 2 (INSTALLING MYSQL)**

Firstly I installed the mysql server using *sudo apt install mysql-server*. Then I had to make a unique password to log into it.
<img width="1512" alt="Screenshot 2022-12-09 at 19 12 02" src="https://user-images.githubusercontent.com/114743648/212202726-d2e0ca83-ed00-40f4-8e9a-a359a3bfe567.png">


**STEP 3 (INSTALLING PHP)**

In this part of the project I installed php-fpm and php-mysql at once using *sudo apt install php-fpm php-mysql*.
Php-fpm stands for stands for “PHP fastCGI process manager”. It allows php based websites to perform more efficiently. Php-mysql allows PHP to communicate with MySQL-based databases.
<img width="1512" alt="Screenshot 2022-12-09 at 20 56 11" src="https://user-images.githubusercontent.com/114743648/212203502-f8d77155-cc97-48d7-a120-bba1bab0e52e.png">


**STEP 4(CONFIGURING NGINX TO USE PHP PROCESSOR)**

I created a root directory for my domain and took ownership using the *chown* command.
Then I open a new configuration file in Nginx’s sites-available directory using VIM editor.
<img width="1512" alt="Screenshot 2022-12-11 at 20 18 28" src="https://user-images.githubusercontent.com/114743648/212207017-30d0df08-854f-4f8d-a72c-50bdc6145074.png">
Afterwards I pasted a configuration into the blank file then activated it.
I then had to disable the default Nginx host that was configured to listen on port 80 using the code *sudo unlink /etc/nginx/sites-enabled/default*. When this was complete I reloaded Nginx to apply the changes made.
Now the website was active. To test it I created an index.html file and wrote in an *echo* command.
<img width="1512" alt="Screenshot 2022-12-11 at 20 26 08" src="https://user-images.githubusercontent.com/114743648/212208160-939ada82-5c29-4bd8-89b2-0f38ad42e76c.png">

**STEP 5 (TESTING PHP WITH NGINX)

I tested PHP with Nginx by creating a test PHP file in my document root. I opened a new file in VIM called info.php and enetered the lines "<?php phpinfo();" into it which allowed me to access the page in my web browser.
<img width="1512" alt="Screenshot 2022-12-14 at 16 19 05" src="https://user-images.githubusercontent.com/114743648/212209176-6d1ea734-d2e9-43e5-a858-b13091a3cbfa.png">


**STEP 6 (RETRIEVING DATA FROM MYSQL DATABASE WITH PHP)**

For this final step I had to create a test database with a To Do list and configure access to it so that the Nginx website would be able to inuire data from the test database and display it.
I had to start by creating a database with a new user and password in mysql.
<img width="1512" alt="Screenshot 2022-12-14 at 21 01 54" src="https://user-images.githubusercontent.com/114743648/212209875-09bd5e81-cdac-41e8-a828-d24a547b347f.png">

Next I had to confirm that I had access to my database by using the code *mysql> SHOW DATABASES;* which gave me the following output. 
<img width="1512" alt="Screenshot 2023-01-13 at 16 16 46" src="https://user-images.githubusercontent.com/114743648/212367940-689f46d2-6830-4609-ab9a-0d0ca7bc6718.png">

Then I inserted a few rows of content into the test table to get this output.
<img width="1512" alt="Screenshot 2023-01-13 at 16 17 31" src="https://user-images.githubusercontent.com/114743648/212369157-119efd11-59db-4965-83d3-5cfd4741a6ca.png">

When this was complete I exited from the mysql console. I then had to create a PHP script so that it could connect to mysql and query my content. I used VIM to create a new PHP file in my web root directory and copied some todo_list content in the file. I saved it and was then was able to access the page in my browser using my public IP address. I ended up with the following 
<img width="1512" alt="Screenshot 2022-12-15 at 12 35 18" src="https://user-images.githubusercontent.com/114743648/212370207-ff7570f8-7e2f-4f6f-a198-3af021bcbc44.png">






































