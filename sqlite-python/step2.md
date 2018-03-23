In this step, you will create and insert data into a new database.

#### Create database

The script below will store data into a new database called user.db. Copy or type it into the app.py file.

<pre class="file" data-filename="create.py" data-target="replace">
!/usr/bin/python
# -*- coding: utf-8 -*-
import sqlite3 as lite
import sys
 
con = lite.connect('user.db')
 
with con:
    cur = con.cursor()
    cur.execute("CREATE TABLE Users(Id INT, Name TEXT)")
    cur.execute("INSERT INTO Users VALUES(1,'Michelle')")
    cur.execute("INSERT INTO Users VALUES(2,'Sonya')")
    cur.execute("INSERT INTO Users VALUES(3,'Greg')")
# This is your Editor pane. Write the Dockerfile here and 
# use the command line to execute commands
</pre>

SQLite is a database management system that uses tables. These tables can have relations with other tables: it’s called relational database management system or RDBMS.  The table defines the structure of the data and can hold the data.  A database can hold many different tables. The table gets created using the command:

```
cur.execute("CREATE TABLE Users(Id INT, Name TEXT)")
```

We add  records into the table with these commands:

```
    cur.execute("INSERT INTO Users VALUES(2,'Sonya')")
    cur.execute("INSERT INTO Users VALUES(3,'Greg')")
```
The first value is the ID. The second value is the name.  Once we run the script the data gets inserted into the database table Users.

Run the script to create a database:

`python app.py`{{execute}}

#### Querying data

One the database is created, we'll use python to query the database contents.

<pre class="file" data-filename="query.py" data-target="replace">
#!/usr/bin/python
# -*- coding: utf-8 -*-
 
import sqlite3 as lite
import sys
 
 
con = lite.connect('user.db')
 
with con:    
 
    cur = con.cursor()    
    cur.execute("SELECT * FROM Users")
 
    rows = cur.fetchall()
 
    for row in rows:
        print row
</pre>

This will output all data in the Users table from the database.