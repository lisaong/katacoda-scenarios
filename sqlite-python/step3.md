In this step, you will learn about importing CSV data into an SQLite database.

#### CSV data vs. SQLite

While dealing with CSV data is simple, importing data to SQLite is helpful when you have a large amount of data, especially data from multiple CSV files.

There are several helper libraries and examples available for importing data from CSV. In this tutorial, we will try the simple `csv2sqlite` library.

First, run the following command to import `users.csv` into the `users` table. This will also create a new SQLite database file called `test_import.db`.

`python csv2sqlite.py users.csv test_import.db users`{{execute}}

Import a second table, `jobs` from `jobs.csv`:

`python csv2sqlite.py jobs.csv test_import.db jobs`{{execute}}

#### Querying data

One the database is created, we'll use python to query the database contents.

**Replace** the contents of `query.py` with the following code:

<pre class="file" data-filename="query.py" data-target="replace">
#!/usr/bin/python
# -*- coding: utf-8 -*-

import sqlite3 as lite
import sys

con = lite.connect('test_import.db')

with con:

    cur = con.cursor()
    cur.execute("SELECT users.name, users.age, jobs.profession FROM jobs INNER JOIN users ON users.ID = jobs.uid")

    rows = cur.fetchall()

    for row in rows:
        print row
</pre>

Run the query to show the imported data:

`python query.py`{{execute}}

#### Foreign keys?

You may notice that the CSV importer script, `csv2sqlite`, does not define a foreign key relationship. It assumes that all data, including the primary keys, are already populated in the CSV file.

Once a table is created, SQLite does not support altering that table to add a foreign key constraint. This is a limitation of SQLite's `ALTER TABLE` functionality.

The lack of foreign key will not affect your ability to do queries like the `INNER JOIN` above. Foreign keys are enforced at `INSERT` time. This is OK as long as you ensure that your CSV data is set up properly, where the `Uid` entries in `jobs.csv` refer to a valid `Id` entry in `users.csv`.