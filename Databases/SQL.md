#
**SQL Hints And Tips**
#
######
In order to run tests on your databases, you will need to set up a test
database.

You will also need to ensure that you empty the test database table(s) before
each test.

This can be done with the use of the SQL TRUNCATE and CASCADE commands. CASCADE
will cascade the TRUNCATE effect to all the tables linked to the table you
mention.

You will also need to restart the numbering of the id numbers with RESTART
IDENTITY, as otherwise, SQL will continue from the last id number, even if you
have deleted all the records.

For example:

```ruby
def setup_test_database
  connection = PG.connect(dbname: 'makers_bnb_test')
  connection.exec('TRUNCATE users RESTART IDENTITY CASCADE;')
end
```

For more details, see the PostgreSQL documentation about TRUNCATE.
https://www.postgresql.org/docs/%EF%BC%99.6/sql-truncate.html
