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

![Screenshot 2023-06-28 053948](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/e7bd877d-c08e-435d-b0c4-8c59a395cd42)

Now that Mysql is successfully installed, i'll go to the next step which is installing Php.

 ## 3 – INSTALLING PHP

I'm going to install PHP to process code and generate dynamic content for my web server. i'm going to install php-fpm, which stands for “PHP fastCGI process manager”, and tell Nginx to pass PHP requests to this software for processing. Additionally, i'll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. To install these two, i'm going to run the command:

`sudo apt install php-fpm php-mysql`

## 4- CONFIGURING NGINX TO USE PHP PROCESSOR

In this stage, i'm going to create a directory structure called Projectlemp withing our default directory var/www/html. creating this directory will allow Nginx to serve me when hosting multiple website.

First i'm going to create a root directory for my domain running the command:

`sudo mkdir /var/www/projectLEMP`

Then i'm going to open a new configuration file in Nginx’s sites-available directory using the Nano command-line Editor instead of vi or vim. i'm running the command `sudo nano /etc/nginx/sites-available/projectLEMP`

The image below will show my configuration: 

