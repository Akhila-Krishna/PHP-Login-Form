
Chapter 1

INTRODUCTION




LAMP stands for Linux, Apache, MySQL, and PHP. Together, they provide a proven set of software for delivering high-performance web applications. Each component contributes essential capabilities to the stack.

The reason they call it a stack is because each level derives off it's base layer. Your Operating system, Linux, is the base layer. Then Apache, your web daemon sits on top of your OS. Then your database stores all the information served by your web daemon, and PHP (or any P* scripting language) is used to drive and display all the data, and allow for user interaction.



Github link of our project:
https://github.com/NithinWarrier/php-login-form













Chapter 2

SOFTWARE REQUIREMENTS SPECIFICATIONS






Linux based web servers consist of four software components. These components, arranged in layers supporting one another, make up the software stack. Websites and Web Applications run on top of this underlying stack. The common software components that make up a traditional LAMP stack are:

    • Linux
      The operating system (OS) makes up our first layer. Linux sets the foundation for the stack model. All other layers run on top of this layer.
      
    • Apache
      The second layer consists of web server software, typically Apache Web Server. This layer resides on top of the Linux layer. Web servers are responsible for translating from web browsers to their correct website.
      
    • MySQL
      Our third layer is where databases live. MySQL stores details that can be queried by scripting to construct a website. MySQL usually sits on top of the Linux layer alongside Apache/layer 2. In high end configurations, MySQL can be off loaded to a separate host server.
      
      
    • PHP
      Sitting on top of them all is our fourth and final layer. The scripting layer consists of PHP and/or other similar web programming languages. Websites and Web Applications run within this layer.
































Chapter 3

INSTALLATION OF LAMP SERVER


Before You Begin
1:Update your system:
				$ sudo apt-get update
		 ... and then install the LAMP stack:
				$ sudo apt-get install lamp-server

Install and Configure Apache
To install Apache you must install the Metapackage apache2.
Install Apache 2.4 from the Ubuntu repository:
				$ sudo apt-get update
                     $ sudo apt-get install apache2
Restart for it to work:
       $ sudo /etc/init.d/apache2 restart
									or
       $ sudo service apache2 restart
To check Apache 2 installation with your web browser, go to the URI http://localhost
If you read "It works!", which is the content of the file /var/www/index.html
, this proves Apache works.


Install MySQL
To install MySQL, open terminal and type in these commands:
				$ sudo apt-get install mysql-server libapache2-mod-auth-					   mysql php5-mysql
During the installation, MySQL will ask you to set a root password. If you miss the chance to set the password while the program is installing, it is very easy to set the password later from within the MySQL shell.
Once you have installed MySQL, we should activate it with this command:
				$ sudo mysql_install_db
Finish up by running the MySQL set up script:
				$ sudo /usr/bin/mysql_secure_installation
The prompt will ask you for your current root password.Type it in:
				Enter current password for root (enter for none): 

				OK, successfully used password, moving on...
Then the prompt will ask you if you want to change the root password. Go ahead and choose N and move on to the next steps.


Install PHP
To only install PHP5:
				libapache2-mod-php5
Enable this module by doing
				$ sudo a2enmod php5
which creates a symbolic link:
				4/etc/apache2/mods-enabled/php5 pointing to 								/etc/apache2/mods-availble/php5
Relaunch Apache 2 again:
				$ sudo service apache2 restart 4. Installing MYSQL with PHP 				   5
Use any method to install
				$ mysql-server libapache2-mod-auth-mysql php5-mysql
Quick Install Using Tasksel
Instead of installing Apache, MySQL, and PHP separately, tasksel offers a convenient way to get a LAMP stack running quickly.
Install tasksel if not already installed by default.
				$ sudo apt install tasksel
Use tasksel to install the LAMP stack
				$ sudo tasksel install lamp-server
Enter the prompt for a MySQL root password. See the steps below for Apache configurations, creating a virtual host, and installation of PHP modules for WordPress installation.

















Chapter 4

AFTER INSTALLING MySql


1.Set mysql bind address

Before you can access the database from other computers in your network,
you have to change its bind address. Note that this can be a security prob-
lem, because your database can be ac- cessed by other computers than your own. Skip this step if the applications which require mysql are running on the same machine. type:
				$ sudo nano /etc/mysql/my.cnf
and change the line:
				bind-address = localhost to your own internal ip address e.g. 				192.168.1.20
				bind-address = 192.168.1.20


2.Set mysql root password

Before accessing the database by console you need to type:
				$ mysql -u root
At the mysql console type:
				$ mysql > SET PASSWORD FOR 				   				  				   âĂŹrootâĂŹ@âĂŹlocalhostâĂŹ = PASS-
WORD(âĂŹyourpasswordâĂŹ);

A successful mysql command will show:
Query OK, 0 rows affected (0.00 sec)
