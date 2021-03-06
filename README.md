# homework_12_reverse_engineering_code
# Unit 14 Sequelize Homework: Reverse Engineering Code

Config Folder: stores all info we need to connect to mysql database.
  middleware/isAuthenticate.js - makes sure that routes only run if user(s) are logged in; if they are not, it redirects them back to home.
    config/config.json - contains login information to connect to the three different databases for development, testing, and production environments. 
    config/passport.js - logic that does user login authentication. it first checks what the user enter is a valid email, and if it is, then checks if the password associated with the email is correct.

Models Folder: holds files that act as templates for the MySQL tables when we run the server. These are similar to schemas and seed-files.
  models/index.js - in Models is used to consolidate all the models into one file and export them out. It also is useful in that programs target any file called index.js.
  models/user.js - is used to generate the users table in the mysql database. It is similar to a schema. On server startup, a users table is generated if it doesnt exist.

Public Folder: constains all code that will be shown in the front end and any logic used for the front end.
  public/login.js - the javascript code for the login.html webage. The logic in the file ensures that all the necessary information is there when a user is logged in and only allows the user to login with the correct email and password. This is where we call the our api, which in turns access the MySQL database and does user authenication.
  public/member.js - the javascript code for the members.html file. It just does a GET call to get the user info and displays it on the page.
  public/signup.js - the javascript code for the signup.html page. This page is where users are directed to when they want to create a new account. This file does a POST call to create a new user in the database.
  public/stylesheets - folder houses css. This project uses bootstrap.
  public/stylesheets/styles.css - contains the actual Cascading Stylesheet overrides for overriding bootstrap classes and any custom CSS styles desired for the application front end 

Routes Folder: contains all CRUD calls to the MySQL database
  reoutes/api-routes.js - contains CRUD calls associated with creating, getting, and logging out a new user.
  routes/html-routes.js - contains all routes associated with redircted the user between the login.html, members.html, and signup.html and checks login status
 
Package.Json: 
  - package.json contains all information for NPM and for node run, build, deployment, author data, and other metadata. By running 'npm i' in the terminal of a project that contains a package.json already, NPM will download all necessary files associated with the project. 

Server.js: 
  - server.js file contains the data to connect our routes and models to a listening port. It is also where we enable our app to work with json data and any middleware packages that may be needed for the project.