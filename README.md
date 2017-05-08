# React-Redux-Flask #

Boilerplate application for a Flask JWT Backend and a React/Redux Front-End with [Material UI](http://www.material-ui.com/).

Connect to different databases including MySQL, PostgresSQL or SQLite.

* Python 2.7+ or 3.x
* Pytest
* Heroku 
* Flask
* React
* Redux
* React-Router 2.0
* React-Router-Redux
* Babel 6
* SCSS processing
* Webpack

![screenshot](http://i.imgur.com/ZIS4qkw.png)

### Install Front-End Requirements
```sh
$ cd static
$ npm install
```

### Run Back-End

```sh
$ python manage.py runserver
```

### Test Back-End

```sh
$ python test.py --cov-report=term --cov-report=html --cov=application/ tests/
```

### Run Front-End

```sh
$ cd static
$ npm start
```

### Build Front-End

```sh
$ npm run build:production
```

### New to Python?

If you are approaching this demo as primarily a frontend dev with limited or no python experience, you may need to install a few things that a seasoned python dev would already have installed.

Most Macs already have python 2.7 installed but you may not have pip install. You can check to see if you have them installed:

```
$ python --version
$ pip --version 
```

If pip is not installed, you can follow this simple article to [get both homebrew and python](https://howchoo.com/g/mze4ntbknjk/install-pip-on-mac-os-x)

After you install python, you can optionally also install python 3

```
$ brew install python3
```

Now you can check again to see if both python and pip are installed. Once pip is installed, you can download the required flask modules:

```
$ sudo pip install flask flask_script flask_migrate flask_bcrypt 
```

Now, you can decide on which database you wish to use. 

#### Create a MySQL Database 

If you decide on MySQL, install the free community edition of [MySQL](https://dev.mysql.com/downloads/mysql/) and [MySQL Workbench](https://www.mysql.com/products/workbench/)

1. start MySQL from the System Preferences
2. open MySQL Workbench and [create a database](http://stackoverflow.com/questions/5515745/create-a-new-database-with-mysql-workbench) called mydatabase but don't create the tables since python will do that for you
3. Install the MySQL connector for Python, add the DATABASE_URL configuration, and create the database and tables

```
$ sudo pip install mysql-connector-python-rf
$ export DATABASE_URL="mysql+mysqlconnector://username:password@localhost/mydatabase"
$ python manage.py create_db
```

Note: you do not need to run "python manage.py db upgrade" or "python manage.py db migrate" if its your first go at it

4. Run Back-End

```
$ python manage.py runserver
```

If all goes well, you should see ```* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)``` followed by a few more lines in the terminal.

5. open a new tab to the same directory and run the front end

```
$ cd static
$ npm install
$ npm start
```

6. open your browser to http://localhost:3000/register and setup your first account


#### Migrate from MySQL to PostgresSQL
 
PostgreSQL is an open source object-relational database. 
 
1. You can easily [install Postgres on a Mac via Brew](http://exponential.io/blog/2015/02/21/install-postgresql-on-mac-os-x-via-brew/)

By now, you'll have Postgres installed, started, and you'll be logged on. 

2. Login or Signup for [Heroku](https://www.heroku.com)

3. Create a new app and connect to your github under the Deploy tab. 

4. Add [Heroku Postgres](https://www.heroku.com/postgres) as an add-on under the Resources tab. 

5. View your Postgres credentials and connection strings by clicking on the Heroku Postgres :: Database link and then click the "View Credentials" button

6. Now you'll want to attempt to connect to your PostgresSQL db instead of MySQL. This time, you need to migrate the connection from MySQL to PostgreSQL.      

7. Upgrade and migrate the existing database and setup the python postgres connection via [psycopg2](https://wiki.postgresql.org/wiki/Psycopg2_Tutorial)

```
$ createdb 'mydatabase'
$ export DATABASE_URL="postgresql://username:password@localhost/mydatabase"
$ pip install psycopg2
$ python manage.py db upgrade
$ python manage.py db migrate
```

8. Run the back-end and start the Front-end
```
$ python manage.py runserver
```

9. CMD-T to tab to a new terminal screen in the same directory. Instead of using npm start this time, try [yarn](https://code.facebook.com/posts/1840075619545360) start.

```
$ cd static
$ yarn start
```


### General DB Connection Strings
```sh
$ export DATABASE_URL="postgresql://xyvresnxxhiqae:ff208e2baaa5bbd74d47f6bbd3b6d25088e3ce6f0d41ad38a00565c62e864dc7@localhost/mydatabase"

or

$ export DATABASE_URL="mysql+mysqlconnector://username:password@localhost/mydatabase"

or

$ export DATABASE_URL="sqlite:///your.db"

More about connection strings in this [flask config guide](http://flask-sqlalchemy.pocoo.org/2.1/config/)

```


## Heroku Deployment - coming soon



## Zeit Deployment - not possible yet... 

Zeit does not currently support persistence so you can install Postgres on with Docker.

Deploying to [Zeit](https://zeit.co/) via [Docker](https://www.docker.com/)




