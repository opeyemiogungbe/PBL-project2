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

![Screenshot 2023-06-28 060701](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/f90508c2-9e42-4e6c-b784-5540272e9c30)

After succesful configuration of our web root directory, i'm going to link the config file from Nginx’s sites-enabled directory running the command:

`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

![Screenshot 2023-06-28 060855](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/3d9879ac-2468-4981-831d-3b66b709a48f) 


After this successful linking, i'm going to check for syntax error with the command: `sudo nginx -t`

I'm also going to disable default Nginx host that is currently configured to listen on port 80, runing the command: 

`sudo unlink /etc/nginx/sites-enabled/default` and reload my Nginx.

Since my web root folder var/www/Projectlemp is empty, i'm going to create an index.html file inside it to test if the server block works well using the echo command: 

`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`

The image below of my browser will show if my echo command works well:

![Screenshot 2023-06-28 061313](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/ffb23c58-0dd0-4126-817e-5221ae8e54bc)

Now that my LEMP stack is now fully configured. I'll be creating a PHP script for Nginx to handle .php files within the newly configured website using the nano command.

`sudo nano /var/www/projectLEMP/info.php` 

After putting the Php code inside the .Php file, i'll check my browser if the configuration was successful. the image below will show thhat:

![Screenshot 2023-06-28 061805](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/c73b394b-f29c-40aa-85a9-db91a408ae81)


![Screenshot 2023-06-28 062126](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/b021d130-f158-428a-9953-26506e933e92)


##  6 – RETRIEVING DATA FROM MYSQL DATABASE WITH PHP
In this step i'm going to create a test database (DB) with simple “To do list” and configure access to it, so the Nginx website would be able to query the data from the DB and display it. i'll be creating a new user with the mysql_native_password authentication method in order to be able to connect to the MySQL database from PHP.

After connecting to Mysql console, i'll be creating a new database called projectlemp database ( i decided to mix things up a bit) running the command: 

`mysql> CREATE DATABASE `projectlemp_database`;` 

![Screenshot 2023-06-30 085616](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/0078a60f-bbf8-40f6-aa59-78e569190ebb)


Now i'm going to be creating a new user and grant him full privileges on the database i just created running the command: 

`mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';` (Note: i changed the user password to a more secure password of my own) 

![Screenshot 2023-06-30 090011](https://github.com/opeyemiogungbe/PBL-project2/assets/136735745/2eeb1beb-4bd3-4414-a84a-ed4cbb5cf5ca)

Now i'm going to give the user permission over the projectlemp_database with the command:

`mysql> GRANT ALL ON projectlemp_database.* TO 'example_user'@'%'; then exit Mysql.
`


Now i'm going to test if the new user has the proper permissions by logging in to the MySQL console again, this time using the custom user credentials:

`mysql -u example_user -p` 
