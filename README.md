# README

Set up a development environment and start a new project
<h2>Getting Started</h2>
-Go to one of the terminals within your coding environment and type the following:
  $ cd /vagrant/src
-Create a new application that uses postgres
  $ rails new splurty --database=postgresql
-Open newly created Splurty application in your text editor
-Go to database.yml file and edit:
  username: postgres
  password: password
  host: localhost
  comment out last two lines on file for username and password.
-Change directory inton your Splurty project
  $ cd /vagrant/src/splurty
-Create your initial database
  $ rake db:create
-Start the server:
  $ rails server -b 0.0.0.0 -p 3000
-In the second terminal window, type following command to move into Splurty folder:
  $ cd /vagrant/src/splurty
-Set up web development pipeline:
  create new Github repository
  create project in heroku and then deploy it to heroku


<h2>Build out the homepage</h2>
  $ rails generate controller quotes
-Edit config/routes.rb and add following line:
  root 'quotes#index'
-Open app/controllers/quotes_controller.rb and add index method:
  def index
  end
-Create new view file for index page at app/views/quotes/index.html.erb and add some HTML:
  <h1>Welcome to my Awesome Quote Generator Application</h1>


<h2>Set up the database for quotes</h2>
There will be a form for the user to fill out with form fields author and saying.
-Run the following in the terminal to create model and migration file:
  $ rails generate model quote
-Go to migration file (db/migrate/XXXX_create_quotes.rb) and add these two t.strings in the table:
  t.string :saying
  t.string :author
-Run line in terminal:
  $ rake db:migrate


<h2>Show a quote from database on page</h2>
-Open app/controller/quotes_controller.rb and add this iside the index method:
  @quote = Quote.first
-Go into app/views/quotes/index.html.erb and change Welcome message to following line to pull quote from rails databse:
  <h1><%= @quote.inspect %></h1>
-If you go load your localhost, you will see the output is nil. Go into your terminal and type the following:
  $ rails console
-Create an example quote to be stores directly into the database:
  > Quote.create(saying: 'Let\'s get coding!', author: 'Raquele Crotti')
-Feel free to add a couple more quotes just to get a few in your database then type:
  > exit
-Adjust app/views/quotes/index.html.erb to pull quotes from database on homepage:
  <h1><%= @quote.saying %></h1>
  <h2><%= @quote.author %></h2>
-Now that we are able to pull quotes when we refresh the localhost, let's make them random. Edit inside index method in app/controllers/quotes_controller.rb to look like this:
  @quote = Quote.order("RANDOM()").first
-Be sure to take the same steps to push app to Heroku.

<h2>Download Bootstrap</h2>

















