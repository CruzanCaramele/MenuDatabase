#Restaurant Menu Database

This is a small project demonstrating the use of an Object Relational Mapper to perform operations on a database. This uses SQLAlchemy to perform the operations on SQLite database.

These operations are [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) operations

##Contents
1. *database_setup.py file* : this is the database configuration file. This has 4 components including the configuration part, class definition part, table definition part for tables in the database and the mapper which defines the columns in the database
2.  *lotsofmenu.py file* : this populates data into the database
3. *restaurantmenu.db file* : this is the database file 


## Requirements to run program Locally on a Computer
1. Install python from [python's website][1]
   -version 2.7
2. Install [Vagrant](https://www.vagrantup.com/downloads.html) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
3. Clone this repository [here](https://github.com/CruzanCaramele/Ubuntu-Virtual-Environment---Vagrant-Virtualbox.git) from GitHub to get the virtual environment to run the database on.
4. Clone this repository [here](https://github.com/CruzanCaramele/MenuDatabase.git) and save it in the vagrant folder from step 3



### Running the Tournament Results
The aim for this is to run tournament_test.py file which contains unit tests that will test the functions within tournament.py file

1. Launch the terminal program on your computer e.g git bash on Windows
2. Navigate to the Vagrant folder from the terminal:
	- hp (master *) vagrant $

3. type in the command " vagrant up ":
	- hp (master *) vagrant $ vagrant up

4. type in the command " vagrant ssh "
	- hp (master *) vagrant $ vagrant ssh

5. change directory to the tournament folder:
	- vagrant@vagrant-ubuntu-trusty-32:~$ cd /vagrant/restaurant
	- vagrant@vagrant-ubuntu-trusty-32:/vagrant/restaurant$

### CRUD Operations Examples to perform on the database
1. CREATE 
New Restaurant and called it Pizza Palace:
myFirstRestaurant = Restaurant(name = "Pizza Palace")
session.add(myFirstRestaurant)
sesssion.commit()
New menu item and added it to the Pizza Palace Menu:
cheesepizza = menuItem(name="Cheese Pizza", description = "Made with all natural ingredients and fresh mozzarella", course="Entree", price="$8.99", restaurant=myFirstRestaurant)
session.add(cheesepizza)
session.commit()

2. READ
Read out information in our database using the query method in SQLAlchemy:
firstResult = sesson.query(Restaurant).first()
firstResult.name

items = session.query(MenuItem).all()
for item in items:
    print item.name


3. UPDATE
In order to update and existing entry in our database, we must execute the following commands:
-	Find Entry
-	Reset value(s)
-	Add to session
-	Execute session.commit()
Find the veggie burger that belonged to the Urban Burger restaurant by executing the following query:
veggieBurgers = session.query(MenuItem).filter_by(name= 'Veggie Burger')
for veggieBurger in veggieBurgers:
    print veggieBurger.id
    print veggieBurger.price
    print veggieBurger.restaurant.name
    print "\n"
Update the price of the veggie burger to $2.99:
UrbanVeggieBurger = session.query(MenuItem).filter_by(id=8).one()
UrbanVeggieBurger.price = '$2.99'
session.add(UrbanVeggieBurger)
session.commit() 


4. DELETE
To delete an item from our database we must follow the following steps:
-	Find the entry
-	Session.delete(Entry)
-	Session.commit()
Delete spinach Ice Cream from our Menu Items database with the following operations:
spinach = session.query(MenuItem).filter_by(name = 'Spinach Ice Cream').one()
session.delete(spinach)
session.commit() 






[1]: http://python.org
