## 1. Ruby on Rails
- **Ruby Introduction** 
>Introducing students into the fundamentals of programming can still be considered as a real challenge. 
    Learning to program is generally considered hard, and programming classes often have high dropout rates. 
    Reasons for this have been analyzed in some detail. A major problem is that programming requires competencies in different fields, 
    and students do not only have to learn the syntax of a programming language and the semantics of language commands, 
    but also at the same time fundamentals in algorithmic thinking and fundamental algorithms, program design, and program comprehension.\
    Ruby in an object oriented programming language developed by Yukihiro Matsumoto. Ruby is inspired by other low level and object oriented programming language like Lisp, Smalltalk, and Perl and uses syntax that is easy for C and Java programmers to learn. Ruby, 
    A dynamic and open source programming language with a focus on simplicity and productivity, 
     has an element syntax that is natural to read and easy to write.\
     *Although it’s easy to program in Ruby, it is not a simple language*
     
### Generating rails app
 
> Rails is a web application development framework written in the ruby programming language.
  It is designed to make programming web applications easier by making assumptions about what every developer needs to get started.
- **Installing rails**\
Before you install rails, you should check to make sure that your system has the proper prerequisites installed. These include:\
  - **Installing Ruby**
    Open up a command line prompt. On macOS open Terminal.app,\
    on windows choose ``run`` from your start menu and type ``cmd.exe``. 
    verify that you have a current version of ruby installed by typing this command ``$ ruby –v``
    Rails requires ruby version 2.5.0 or later. If the version number returned is less than that number, 
    you’ll need to install a fresh copy of ruby.
  - **Installing SQLite3**
  You will also need an installation of the SQLite3 database. Many popular UNIX-like Oses ship with an acceptable version of SQLite3. \
  On windows,if you install rails through rails installer, you already have SQLite installed.
  Others can find installation instructions at the SQLite3 website.
  - **Installing Node.js and Yarn**
  Finally, you’ll need Node.js and Yarn installer to manage your application’s JavaScript. 
  Find the install instructions at the Node.js website and verify it’s installed correctly with the following command: ``$ node --version``
  The version of your node.js runtime should be greater than 8.16.0
  To install yarn, follow installation instructions at the Yarn website
  Running this command should print out yarn version: ``$ yarn –v`` it says something like “1.22.0” yarn has been installer correctly
  After all this installation, the system is ready to receive a proper installation as Rails itself
  To install Rails, use the gem install command provided by ruby Gems $ gem install rails 
  To verify that you have everything installed correctly, you should be able to run the following: ``$ rails --version``
  If it says something like ‘rails 6.0.0’, you are ready to continue.
### Model, View and Controller introduction 
> MVC background, MVC is a compound design pattern and was developed in 1979 by Trygve Reenskaug (Smalltalk)
  The Model View Controller principle divides the work of an application into 3 separate but closely cooperative subsystems.
  When interacting with our application, a browser sends a request, which is received by a web server and passed on to the Rails routing engine. The router receives the request and redirects to the appropriate controller class method based on the routing URL pattern.
  The controller then takes over. In some cases, the controller will immediately render a view for the browser. More commonly for dynamic sites, the controller interacts with a model.
  After invoking the model, the controller then renders the final view ``(HTML, CSS, and images)`` and returns the complete web page to the user's browser.
  
 ### Connecting rails to Database
 
 > Ruby on Rails and MySQL are both leading technologies in Web Development, 
   here is a guide for connecting MySQL with Ruby on Rails.\
**Step 1: Install MySQL in the System**\
   MySQL is a powerful database management system used for organizing and retrieving data. 
   To install MySQL, open terminal and type in these commands: sudo apt-get install mysql-server libapache2-mod-auth-mysql During the installation, 
   MySQL will ask you to set a root password. If you miss the chance to set the password while the program is installing, 
   it is very easy to set the password later from within the MySQL shell. 
   Once you have installed MySQL, we should activate it with this command: ``sudo mysql_install_db``
   Finish up by running the MySQL set up script: ``sudo /usr/bin/mysql_secure_installation`` The prompt will ask you for your current root password. 
   Type it in. Enter current password for root (enter for none): OK, *successfully used password, moving on…*\
**Step2: Create a Database in the Local**\
   To login to mysql, run following commands on terminal mysql -u root -p at the Enter password: prompt,
   enter root’s password now u can create a new database using ``create database your_db_name;``\
**Step3: Create a New Rails App using Mysql**\
  ``rails new app_name -d mysql``
    If we start a rails app using -d mysql then it automatically changes ``gem ‘sqlite3’``
    from your Gemfile and add the gem ‘mysql2
    **Step4: Change the Database.yml with your Mysql Database Name that we Created Earlier**\
 
 
