# ActiveRecord Discussion Questions

## Part One - Reading the Documentation

Looking at Documentation is an important part of programming. You don't have to memorize anything, but you should get familiar with the types of information you can find in different docs. For this exercise, using the ActiveRecord documentation [here](http://guides.rubyonrails.org/active_record_querying.html#retrieving-objects-from-the-database), take a look at the following methods:

1. `.find`
2. `.find_by`

Takes one or more args representing different columns in table.  Record is returned.  If record is not found, nil is returned (not error!).  Consider adding a conditional for your find_by methods.

3. `.where`

Takes a key value pair as args and returns an array of elements matching the conditional.  If no match found, empty array is returned.

4. `.all`

No arguments accepted, but can be chained by other methods or used with WHERE.  Returns an empty array if no match found.

5. `.first`

If no parameter is established, returns the first record by the primary key by default if no order method used.  Returns nil if no matching params.

```
customer = Customer.order(:first_name).first
=> #<Customer id: 2, first_name: "Fifo">
```

6. `.destroy`

Can take in an integer (like id) or array of integers.
Once retrieved, an Active Record object can be destroyed which removes it from the database.

Returns the object that has been destroyed if method is successful, if not, returns false (good to use in conditionals).

With your table mates and answer the following questions about each methods

1. What argument or arguments does the method take?
2. What type of object does the method return?
3. What happens if none of the parameters match? (i.e. what if `Tweet.find(5)` can't find that tweet? How about `Tweet.find_by(id: 6)`? 


## Part Two - Name that SQL! 

Pretend that you have a `tweets` table with two columns - `message` and `user_id`. Given the code below, write in a notebook or on a whiteboard what SQL statements will fire when the following methods are called? 

```
class Tweet < ActiveRecord::Base

end
``` 

1. `Tweet.all` 

```
SELECT tweets.* FROM tweets
```

2. `Tweet.find(5)`

```
SELECT tweets.* FROM tweets WHERE (id == 5)
```

3. `Tweet.find_by(user_id: 7)`

```
SELECT tweets.* 
FROM tweets 
WHERE (id == 7)
```

4. `Tweet.where(user_id: 7)` 

```
SELECT tweets.* 
FROM tweets 
WHERE (id = 7)
```

5. `Tweet.create(user_id: 5, message: 'making some coffee')`

```
sql = <<-SQL 
INSERT INTO tweets (user_id, message)
VALUES (5,"making some coffee")
SQL

DB[:conn].execute(sql)
```

6. `Tweet.destroy(7)` 

```
DELETE FROM tweets WHERE (id = 7)
```