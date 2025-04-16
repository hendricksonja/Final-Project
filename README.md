# Implementing and Securing a Blogging Platform


## AI Guidance
I encourage you to use ChatGPT etc. for all aspects of this project EXCEPT for:
- The database portion; you have to create the database on your own, normalize the data on your own, setup the tables on your own, etc.
- The Security Writeup.  Don't get AI to write it for you.

If you use AI on these portions, may you stub your toe on every door jam you come across for the rest of your life. Also I will find out and you will fail the assignment.


## Objective: 
This assignment is designed to help you understand the principles of database management, SQL querying, web application development, and the fundamentals of securing applications against common vulnerabilities.


## Learning Outcomes:

By the end of this project, you will be able to:

- Design and implement a relational database using MySQL.
- Develop a web interface using PHP to interact with the database.
- Understand and apply basic security measures to protect a web application.
- Identify and demonstrate SQL injection vulnerabilities and other security risks in web applications.


## Project Description:

You are tasked with creating a simple blogging platform using PHP and MySQL. This platform will include user authentication, posting blog entries, and a search functionality. The platform will be built on a Linux VM running Linux, Apache, MySQL, and PHP (LAMP stack).  Connection details will be provided later on.

---

## Tasks:


### Database Setup:
**THIS IS A NO-AI-ZONE**

1. Analyze and normalize the provided dataset to at least the 2nd normal form.
2. Create SQL scripts to generate the database schema including tables for users, posts, comments, etc.
3. Populate the database with initial data.


### Development of PHP Web Application:
*AI FRIENDLY ZONE. WEAPONS FREE.*

Implement PHP scripts for:
1. User registration and login.
2. Displaying all blog posts.
3. Adding new blog posts.
4. Searching for posts. 


### Web Interface:
*AI HIGHLY ENCOURAGED. GO GET EM.*
1. Create simple HTML forms and pages that interact with your PHP scripts.
2. Ensure forms are well structured and provide the necessary functionality for interacting with the database.


### Security Analysis:
**NO AI ALLOWED.**

Examine the vulnerabilities in the provided PHP scripts, especially focusing on SQL injection.
Document how these vulnerabilities can be exploited and propose measures to mitigate these risks.

---

## Deliverables:
### Database Schema and Scripts:
- SQL scripts for creating and populating database tables.

### PHP Scripts:
- Complete PHP scripts for handling user authentication, posting, and searching.

### HTML Files:
- HTML forms and pages for the functionalities implemented.

### Security Report:
- A detailed report that identifies vulnerabilities, describes potential exploits, and suggests mitigations.


### **Submission Guidelines:**
- Submit all your files in a compressed folder (.zip).
- Include a README file detailing the structure of your project and instructions on how to set up and run your application.
- Your security report should be submitted as a separate PDF document.


### Evaluation Criteria:
1. Functionality: How well does your application perform the required tasks?
2. Database Design: Efficiency and normalization of the database.
3. Code Quality: Clarity, use of best practices, and commenting.
4. Security Awareness: Understanding and documentation of security vulnerabilities.

---

## Resources

### Using Your Linux Server
Your server has the LAMP stack already implemented.  This is Linux, Apache, MySql and PHP.  You will be given a unique IP:Port combination for the following services on your server:
- SSH
- Web/Apache (HTTP only)
- SQL

Log into your server via SSH at your specific IP:Port by opening a terminal and typing
`ssh setup@IP -p Port`

You will need the specific IP, your port numbers, and the password.  I will give these to you in class or on Canvas, I don't want to post them publically on GitHub.


### Files
You can access the files for this project one of the following ways:

- The files are pre-loaded for you into `/var/www/html`
- Or you can pull them from this repo `https://github.com/hendricksonja/Final-Project/`
- Or you can clone the repo and work with the files that way.

You will have to edit some of the files to make them work for you, such as `db_connect.php`, where you need to put in the correct database name and credentials to connect to your specific database.


### Apache/Web
HTTPS is outside the scope of this project.  To acquire an SSL certificate you need to have a domain name attached to your IP, plus you need to setup Apache Virtual Hosts and that is, again, outside the scope of this project.


#### Change Default Web Page
Your web server is currently serving the default Apache page. You need to change which page is the default by editing the dir.conf file:
```
sudo nano /etc/apache2/mods-enabled/dir.conf
```

Ensure that whatever page you want to load when you go to your web site is the name of the first file here:
```
<IfModule mod_dir.c>
    DirectoryIndex {YOUR_FILE_NAME}.html index.html index.cgi index.pl index.php index.xhtml index.htm
</IfModule>
```

Then restart Apache:
```
sudo systemctl restart apache2
```

Check this link for more specifics: 
[https://www.digitalocean.com/community/tutorials/how-to-install-lamp-stack-on-ubuntu#changing-apache-s-directory-index-optional]


#### Other Apache Info 
There are many other things you can do with Apache.  I recommend that you spool through the following documents to get an understanding of what's happening.  (I actually expect nearly all of you to skip these links, but if I write this here, then when you don't read the documents and come to me with questions, I can just point you right back to these links.  Sooner or later, you will probably click them.  Save us both some time and energy and just read them now.)


**How to Install Apache** 

[https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04] 

This is for your information so you understand where it installed and where the files are. 
- NOTE: DO NOT do Step 1 and reinstall Apache, it is already installed for you.  
- ALSO NOTE: DO NOT do Step 5 where it says to use Apache Virtual Hosts.  You DO NOT need to do that. 
- OMG ANOTHER NOTE: Step 6 is the good stuff.  References to file locations etc. 


**Installing LAMP Stack on Ubuntu**

[https://www.digitalocean.com/community/tutorials/how-to-install-lamp-stack-on-ubuntu]

Another INFORMATIONAL article.  You DO NOT NEED to install the LAMP stack because, guess what, it's already installed for you.  However, if something isn't working, this might be a good article to check and see what's up.


### MySQL

This is the point of this project.  Do some research and figure out how it works and how to implement your stuff.  Godspeed, soldier.

(ok, fine, here is one link that could be helpful)
[https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-22-04]

NOTE: Guess what?  Don't do Step 1, MySQL is already installed.

#### Remote MySQL Access
If you want to allow an external application (like MySQL Workstation) to access your MySQL database, you need to open the port on the firewall"
```
sudo ufw allow 3306
```

You will also need to allow remote connections in MySQL:



### Firewall
[https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04#step-2-adjusting-the-firewall]
NOTE: It's already enabled, just check to make sure the correct ports are open, etc.


### PHP
While you technically do not need to make any substantial changes to your PHP scripts to make your website work, if you don't change anything you will get wrecked on the live-fire portion of this project.  Here's some tips:
[https://www.w3schools.com/php/]
[https://www.php.net/manual/en/tutorial.php]


### Security Info
[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu]
I HIGHLY recommend that you do steps 2 and 3 and look at step 4.  You don't need to do step 1 because the 'setup' account is already a regular user and not root.  Step 5 isn't really necessary because we are using password authentication and not SSH keys.

If you do not at least change the password of the 'setup' account, I will only say "I told you so" when one of your classmates SSHs into your server and pwns your entire database.


# Conclusion
You're in college, figure it out. Good luck.
