# README

# Spurty - Quote Generator Application
A database-powered quote generator with a mobile-first design. HTML5, CSS Ruby, Rails, Active Record & PostgreSQL, Twitter Bootstrap, Deployment via Heroku.</h3>

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Setup](#setup)
* [Status](#status)
* [Sources](#sources)
* [Contact](#contact)

## General info
A spunky first project in UC Berekely's Coding Bootcamp program. Splurty is a fully-functioning web application that generates random quotes from Ruby on Rails database to display on homepage to users. Users are able to contribute their own quotes in a bootstrap modal pop-up form to add to database. App also features well-designed about page, nav bar, footer, hyperlinks and photo of author.</h3>


## Technologies 
Project is created with:
* ruby '2.5.3' [Install Ruby on Rails](https://github.com/university-bootcamp/coding-environment/blob/master/README.md#coding-environment-installation-guide)
* gem 'rails', '~> 5.2.1'
* Heroku [Heroku sign up](https://signup.heroku.com/t/platform?c=70130000001xDpdAAE&gclid=CjwKCAiAzuPuBRAIEiwAkkmOSM8vVAtL7RKLqoIVrshH7VuxMysxD2e1555A3dwyDU4sOSOxy6zujxoCXBIQAvD_BwE)
* gem 'bootstrap', '~> 4.3', '>= 4.3.1' [Install Bootstrap](https://github.com/twbs/bootstrap-rubygem)
* gem 'pg', '>= 0.18', '< 2.0' [Install PostgreSQL](https://www.ibm.com/cloud/databases-for-postgresql)
* HTML5 [HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
* CSS [Cascading Style Sheets](https://www.w3schools.com/html/html_css.asp)

## Setup   
Set up a development environment and start a new project
###Getting Started
- Go to one of the terminals within your coding environment and type the following:
  ```
  $ cd /vagrant/src
  ```
Create a new application that uses postgres
  ```
  $ rails new splurty --database=postgresql
  ```
- Open newly created Splurty application in your text editor
- Go to database.yml file and edit:
  ```
  username: postgres
  password: password
  host: localhost
  ```
  comment out last two lines on file for username and password.
- Change directory inton your Splurty project
  ```
  $ cd /vagrant/src/splurty
  ```
- Create your initial database
  ```$ rake db:create
  ```
- Start the server:
  ```
  $ rails server -b 0.0.0.0 -p 3000
  ```
- In the second terminal window, type following command to move into Splurty folder:
  ```$ cd /vagrant/src/splurty
  ```
- Set up web development pipeline:
  create new Github repository
  create project in heroku and then deploy it to heroku


###Build out the homepage
  ```
  $ rails generate controller quotes
  ```
- Edit config/routes.rb and add following line:
  ```
  root 'quotes#index'
  ```
- Open app/controllers/quotes_controller.rb and add index method:
  ```
  def index
  end
  ```
- Create new view file for index page at app/views/quotes/index.html.erb and add some HTML:
  ```
  <h1>Welcome to my Awesome Quote Generator Application</h1>
  ```


###Set up the database for quotes
There will be a form for the user to fill out with form fields author and saying.
- Run the following in the terminal to create model and migration file:
  ```
  $ rails generate model quote
  ```
- Go to migration file (db/migrate/XXXX_create_quotes.rb) and add these two t.strings in the table:
  ```
  t.string :saying
  t.string :author
  ```
- Run line in terminal:
  ```
  $ rake db:migrate
  ```


###Show a quote from database on page
- Open app/controller/quotes_controller.rb and add this iside the index method:
  ```
  @quote = Quote.first
  ```
- Go into app/views/quotes/index.html.erb and change Welcome message to following line to pull quote from rails databse:
  ```
  <h1><%= @quote.inspect %></h1>
  ```
- If you go load your localhost, you will see the output is nil. Go into your terminal and type the following:
  ```
  $ rails console
  ```
- Create an example quote to be stores directly into the database:
  ```
  > Quote.create(saying: 'Let\'s get coding!', author: 'Raquele Crotti')
  ```
- Feel free to add a couple more quotes just to get a few in your database then type:
  ```
  > exit
  ```
- Adjust app/views/quotes/index.html.erb to pull quotes from database on homepage:
  ```
  <h1><%= @quote.saying %></h1>
  <h2><%= @quote.author %></h2>
  ```
- Now that we are able to pull quotes when we refresh the localhost, let's make them random. Edit inside index method in app/controllers/quotes_controller.rb to look like this:
 ```
 @quote = Quote.order("RANDOM()").first
 ```
- Be sure to take the same steps to push app to Heroku.

## Status
Project is fully-functioning, simple and complete. You can find it delpoyed on heroku via: <https://splurty-raquele-crotti.herokuapp.com/>


## Sources
This app was created during my time completing UC Berkeley Extension's  Coding Bootcamp Program.

## Contact 
* [Portfolio](https://www.raquelecrotti.com/)
* [LinkedIn](https://www.linkedin.com/in/raquele-crotti/)
* [Github](https://github.com/Raquele-Crotti)





















