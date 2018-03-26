In this step, you will learn about structuring data across multiple tables.

#### Create multiple tables

We can structure our data across multiple tables. This keeps our data structured, fast and organized.  If we would have a single table to store everything, we would quickly have a big chaotic mess. What we will do is create multiple tables and use them in a combination.

We will create two tables and use a foreign key to denote the relationships. The foreign key is a constraint that enforces an "exist" relationship between tables. For more information on foreign keys, see: https://sqlite.org/foreignkeys.html.

We will create two tables, a `Users` table and a `Jobs` table. The `Users` table is similar to the previous step, and contains user information. The `Jobs` table contains the jobs that each user performs.

The `Jobs` table contains a foreign key, `Uid`, which is linked to the `Id` column in the `Users` table. By setting this foreign key, we tell SQLite that the `Jobs.Uid` column must contain ids from the `Users.Id` column.

The script below will create a new database called test2.db. **Replace** the contents of `create.py` with the following code:

<pre class="file" data-filename="create.py" data-target="replace">
#!/usr/bin/python
# -*- coding: utf-8 -*-

import sqlite3 as lite
import sys

con = lite.connect('test_foreign.db')

with con:

    cur = con.cursor()

    # Enable foreign key support
    cur.execute("PRAGMA foreign_keys = 1")

    # Create Users table
    cur.execute("CREATE TABLE Users(Id INTEGER PRIMARY KEY, Name TEXT)")
    cur.execute("INSERT INTO Users VALUES(1,'Michelle')")
    cur.execute("INSERT INTO Users VALUES(2,'Howard')")
    cur.execute("INSERT INTO Users VALUES(3,'Greg')")
    cur.execute("INSERT INTO Users VALUES(4,'Laura')")

    # Create Jobs table, with foreign key Uid that references Users.Id
    cur.execute("CREATE TABLE Jobs(Id INTEGER PRIMARY KEY, Profession TEXT, Uid INTEGER, FOREIGN KEY(Uid) REFERENCES Users(Id))")
    cur.execute("INSERT INTO Jobs VALUES(1,'Scientist',1)")
    cur.execute("INSERT INTO Jobs VALUES(2,'Marketeer',2)")
    cur.execute("INSERT INTO Jobs VALUES(3,'Developer',3)")
</pre>

This line creates the `Jobs` table, with the foreign key constraint: 

```
cur.execute("CREATE TABLE Jobs(Id INTEGER PRIMARY KEY, Uid INTEGER, Profession TEXT, FOREIGN KEY(Uid) REFERENCES Users(Id))")
```
Run the script to create a database:

`python create.py`{{execute}}

#### Querying data

Once the database is created, we'll use python to query the database contents.

**Replace** the contents of `query.py` with the following code:

<pre class="file" data-filename="query.py" data-target="replace">
#!/usr/bin/python
# -*- coding: utf-8 -*-

import sqlite3 as lite
import sys

con = lite.connect('test_foreign.db')

with con:

    cur = con.cursor()
    cur.execute("SELECT users.name, jobs.profession FROM jobs INNER JOIN users ON users.ID = jobs.uid")

    rows = cur.fetchall()

    for row in rows:
        print row
</pre>

`python query.py`{{execute}}

This will output the users and their jobs from both tables.

```
(u'Michelle', u'Scientist')
(u'Howard', u'Marketeer')
(u'Greg', u'Developer')
```

#### Testing foreign key constraint

We will test the foreign key constraint by inserting a job that has an *invalid* user id.

**Replace** the code in `query.py` with the following code (delete the old code):

<pre class="file" data-filename="query.py" data-target="replace">
#!/usr/bin/python
# -*- coding: utf-8 -*-

import sqlite3 as lite
import sys

con = lite.connect('test_foreign.db')

with con:

    cur = con.cursor()

    # Enable foreign key support
    cur.execute("PRAGMA foreign_keys = 1")

    # Insert a job that has an invalid user id.
    cur.execute("INSERT INTO Jobs VALUES(4,'Database Engineer',999)")

    # Query the users and jobs again
    cur.execute("SELECT users.name, jobs.profession FROM jobs INNER JOIN users ON users.ID = jobs.uid")

    rows = cur.fetchall()

    for row in rows:
        print row
</pre>

Run the script again:

`python query.py`{{execute}}

This should fail:

```
Traceback (most recent call last):
  File "create.py", line 26, in <module>
    cur.execute("INSERT INTO Jobs VALUES(4,'Database Engineer',999)")
sqlite3.IntegrityError: FOREIGN KEY constraint failed
```

Do you know why this is the case? Can you fix `query.py` so that it will work?
