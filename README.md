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
    from your Gemfile and add the gem ‘mysql2\
 **Step4: Change the Database.yml with your Mysql Database Name that we Created Earlier**\
    Go to cd your_app_name/config/ and open database.yml. Rename it as the following:
    development:
    adapter: ```mysql2```
    database: ```your_db_name```
    host: ```localhost```
    username: ```your_mysql_user_name```
    password: ```root's password```
    encoding: ```utf8```
    That’s it now u can create the rails application using MySQL.
    
  ### Authentication in rails
       > Authentication Methods in Rails. Authentication is the process of establishing, and subsequently confirming,
           a site user's identity. It is how an app recognizes, who you are. 
           In this article, we'll go through a few methods that you can add authentication to your Rails application
           Those are the steps used to authenticate in rails but it comes after creating a new rails application.\
 **Step 1. Add devise gem**\
       ```- Open up your Gemfile and add this line
          - gem 'devise' and
          -  run
          -  bundle install
             to install the gem. 
         Also remember to restart the Rails server.```
         
**Step 2. Set up devise in your app**
        Run the following command in the terminal.
         ```rails g devise:install```
    
**Step 3. Configure Devise**
Ensure you have defined default url options in your environments files. Open up ``config/environments/development.rb`` and add this line:
   ``config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }``
  before the end keyword.
  *Open up app/views/layouts/application.html.erb and add:*
  ``<% if notice %>
      <p class="alert alert-success"><%= notice %></p>
    <% end %>
    <% if alert %>
      <p class="alert alert-danger"><%= alert %></p>
    <% end %>
    right above
       <%= yield %>``
  Open up *app/views/ideas/show.html.erb* and remove the line that says:
  ``<p id="notice"><%= notice %></p>``
  Do the same for *app/views/comments/show.html.erb.* 
  These lines are not necessary as we’ve put the notice in the *app/views/layouts/application.html.erb* file.
  **Step 4. Setup the User model**
  We’ll use a bundled generator script to create the User model.
   ``rails g devise user
     rails db:migrate``
Coach: Explain what user model has been generated. What are the fields?
**Step 5. Create your first user**
    Now that you have set everything up you can create your first user. Devise creates all the code and routes required to create accounts, log in, log out, etc.
    Make sure your rails server is running, open http://localhost:3000/users/sign_up and create your user account.
**Step 6. Add sign-up and login links**
All we need to do now is to add appropriate links or notice about the user being logged in in the top right corner of the navigation bar.
In order to do that, edit ``app/views/layouts/application.html.erb`` add:

    <p class="navbar-text float-right">
    <% if user_signed_in? %>
      Logged in as <strong><%= current_user.email %></strong>.
      <%= link_to 'Edit profile', edit_user_registration_path, :class => 'navbar-link' %> |
      <%= link_to "Logout", destroy_user_session_path, method: :delete, :class => 'navbar-link'  %>
    <% else %>
      <%= link_to "Sign up", new_user_registration_path, :class => 'navbar-link'  %> |
      <%= link_to "Login", new_user_session_path, :class => 'navbar-link'  %>
    <% end %>
    </p>
    right after
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="/ideas">Ideas</a>
        </li>
        ...
      </ul>
 Finally, force the user to redirect to the login page if the user was not logged in. Open up ``app/controllers/application_controller.rb`` and add:\
  ``before_action :authenticate_user!``
after *class ApplicationController < ActionController::Base*
Open your browser and try logging in and out from.

### Rails app deployment 
        Software deployment refers to the process of making the application work on a target device, whether it be a test server, 
        production environment or a user's computer or mobile device.
        This steps will guide you on how to deploy an app in rails

**- Check your Ruby and Rails versions:**
        ``$ ruby --version
        ruby 2.6.5p114 (2019-10-01 revision 67812)
        $ gem list rails
        rails (6.0.2.1)
        If you don't have the latest versions, install rvm according to the instructions on their website and then install the latest Ruby on Rails:
        rvm install 2.6.5
        rvm use 2.6.5
        gem update --system && gem install bundler rails``
  **- Create a new app:**
  rails new demo\
  **- Set the ruby version that you want to use in .ruby-version:**
  ``cd demo/
  echo "2.6.5" > .ruby-version``
  
  **- Edit the Gemfile and add a production group with the gems pg (PostgreSQL) and unicorn (the Rack HTTP server). Wrap the sqlite3 gem in a group for                                        development and test so that it doesn't get installed in production. Add the mina gem for the development environment:**
  
  ``group :production do
  gem 'pg'
  gem 'unicorn'
end

group :development, :test do
  gem 'sqlite3'
  gem 'mina', '1.2.3'
end``

If you like, you can also use the unicorn server during development by declaring the dependency outside of the :production group.
This tutorial was tested with Mina version 1.2.3 - if there are newer versions available, it's recommended to use 1.2.3 first and then update to the new version.

**- Install all dependencies locally skipping those from the production group:**
``bundle install --without=production``
**- Generate a controller for serving a page and a model:**
``bin/rails generate controller welcome index
  bin/rails generate model counter name:string value:integer``
 **- Edit config/routes.rb and set the welcome controller as root route:**
    >Rails.application.routes.draw do
      ``root 'welcome#index'``
      # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
       end
       
   **- Edit app/controllers/welcome_controller.rb and make it use the model object:**
   
       class WelcomeController < ApplicationController
        def index
            counter = Counter.find_or_create_by(name: "default")
            counter.value = (counter.value || 0) + 1
            counter.save!
            render plain: "Counter #{counter.value}; #{Rails.version}/#{RUBY_VERSION}"
            end
         end``
   **- Migrate the database and run the application locally:**
   ``bin/rake db:migrate
    bin/rails s``
   **- Create a local git repository and commit the app:**
        ``- git init
          - git add .
          - git commit -m "demo project"``
    **- Create a Git repository on Github and push the project to the repository, for example:**
     ``- git remote add origin git@github.com:example/rails-demo.git
       - git push -u origin master``
       
  ## 2. Online Questions and Answers

   **• What is MVC in Ruby on Rails?** 
This is the model-view-controller (MVC) architectural pattern, which enforces a separation between business logic from the input and presentation logic associated with a graphical user interface (GUI)

   **• What is authentication and authorization?**

Authentication is a confirmation of user identity, while authorization determines whether you can access a particular resource.

   **• What is a Devise?**

Devise is the cornerstone gem for Ruby on Rails authentication.

   **• Explain what is “Yield” in Ruby on Rails?**\
A Ruby method that receives a code block invokes it by calling it with the “Yield”.

   **•  Explain what is ORM (Object-Relationship-Model) in Rails?**
ORM or Object Relationship Model in Rails indicate that your classes are mapped to the table in the database, and objects are directly mapped to the rows in the table.

   **• What is Rolify and CanCanCan?**
Rolify is Roles library which supporting scope on resource object without any authorization enforcement. CanCanCan is an authorization library which restricts what resources a given user is allowed to access. All permissions are defined in a single location (the Ability class).

  



  
    
 
 
