# PBL- PROJECT 2 WEB STACK IMPLEMENTATION (LEMP STACK)

## 1 – INSTALLING THE NGINX WEB SERVER

After connecting my AWS/Ubuntu on my terminal and updating the necessary packages through the package manager. i'm goimg to install Nginx web server.

### What is Nginx:

NGINX is a popular webserver that is known for its reliability, speed and scalability. It has the ability to handle a lot of connections and high-traffic website with speed. i'm going to install the webserver by running the command: 

`sudo apt install nginx -y` the flag y means an automatic yes to any necessary request made during installation.

And i'm going to verify our installation by running the command: 

`sudo systemctl status nginx` 
![Screenshot 2023-06-28 052818](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/4ce7a53f-62f8-4005-9c60-0fa68d7d5dbe)

After successful installation of the Nginx , i'm going to check my web browser to also confirm if our Nginx is working perfectly and share the image below:
![Screenshot 2023-06-28 053054](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/e756bcb2-dc46-43c6-a1e6-91f38a2b12f5)


## 2- INSTALLING MYSQL

 As i stated in my project 1 report, MySql is a Database Management System (DBMS) to be able to store and manage data for our site in a relational database. so i'm going to go ahead and instaall MySql running the command: 

` sudo apt install mysql-server`

and check for successful  installation running the command: 

`sudo mysql` 
![Screenshot 2023-06-28 053521](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/557f6770-b622-4e43-9996-701b291f0ca2)


After this sucessful installation, i'm going to set up a password for the root user before running the interactive script and setting up the necessary password. i'll run the command below to show our password was setup successfully: 

` sudo mysql -p` the p flag is meant to prompt for the password after changing the root use Password.

