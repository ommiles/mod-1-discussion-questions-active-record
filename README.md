# ActiveRecord Discussion Questions

## Part One - Reading the Documentation

Looking at Documentation is an important part of programming. You don't have to memorize anything, but you should get familiar with the types of information you can find in different docs. For this exercise, using the ActiveRecord documentation [here](http://guides.rubyonrails.org/active_record_querying.html#retrieving-objects-from-the-database), take a look at the following methods:

1. `find`
2. `.find_by`
3. `.where`
4. `.all`
5. `.first`
6. `.destroy`

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
2. `Tweet.find(5)`
3. `Tweet.find_by(user_id: 7)`
4. `Tweet.where(user_id: 7)` 
5. `Tweet.create(user_id: 5, message: 'making some coffee')`
6. `Tweet.destroy(7)` 
