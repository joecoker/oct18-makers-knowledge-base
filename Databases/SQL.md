#
**SQL Hints And Tips**
#
######
In order to run tests on your databases, you will need to set up a test
database.

You will also need to ensure that you empty the test database table(s) before
each test.

This can be done with the use of the SQL TRUNCATE and CASCADE commands. CASCADE
will TRUNCATE all the tables linked to the table you mention.

For example:

```ruby
def setup_test_database
  connection = PG.connect(dbname: 'makers_bnb_test')
  connection.exec('TRUNCATE users RESTART IDENTITY CASCADE;')
end
