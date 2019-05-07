# Ruby Data Types
- Ruby has 6 data types: booleans, symbols, numbers, strings, arrays, hashes
- Fixnums are whole numbers like 7
- Floats are decimals like 7.3
- A symbol is a representation of a piece of data. Symbols look like this `:my_symbol`
- Hashes function like dictionaries, they are composed of key/value pairs (like objects in JavaScript)
- Hashes look like this: `{"im a key" => "im a value!", "key2" => "value2"}`

# Reading Error Messages
- There are 4 error types: name errors, syntax errors, type errors, division errors

# Variable Assignment
- Ruby is a dynamically typed language. That means the value of a variable can change its type and does not need to be explicitly and permanently defined. You can change the value of a variable from a string to a number
- It is also a strongly typed language. A variable will never be automatically coerced to another type without you explicitly changing the type. Adding a number and a string  will raise a TypeError

## Pass-By-Value
- If you perform some action on the value of a variable like, `sound.upcase` for example, sound will still point to the original value. This is because when upcase does its thing, sound hands over only its value to upcase. In fact it hands over a copy of that value that upcase can operate on while still holding on to the original unaltered value. 
- In short, a variable makes a copy of the value it holds and passes the copy over to something else that alters or changes it. 

# Ruby Variable Types
- Local variables - have a local scope
- Global variables have a global scope. Declared like so: `$global_variable = "The whole program knows about me!"`
- Constants are written either in uppercase or they are capitalized. They have a global scope when defined globally. Constants cannot be defined within methods. When they are initialized, they should not be reassigned. 

# Methods and Arguments
- In Ruby, if you define a method with an argument, an argument is required when you invoke the method, otherwise you'll get an argument error
- Method arguments create local variables for you to refer to the value used when the method is actually invoked

# Method Default Arguments
- In order to define a method that optionally takes in an argument, we define our method to take in an argument with a default value. By doing this, we make it possible to call the method with or without arguments
``` Ruby
def greeting(name = "Ruby programmer")
  puts "Hello, #{name}"
end
```
- The default value of name above is "Ruby programmer", so if the method is invoked without arguments Ruby will assume the default value of name
- However the method can be invoked `greeting("Sophie)` in which case Ruby will reassign the variable `name` to the string `"Sophie"` inside the method. 
## Using Default Arguments and Required Arguments
- A method can be defined to take both required and default arguments but the default argument must be at the end of the argument list

# Return Values
- `puts` and `print` are both used to display in the console the results of evaluating Ruby code. Puts adds a new line after execution, print does not
- Everything in Ruby has a return value
- The return keyword will disrupt the execution of your method. If you use it, your method will return whatever you told it to and terminate

# String Interpolation
- To interpolate, you do this `#{name}`
- Interpolation will only work on strings wrapped in double quotes

# Debugging with Pry
- When you place the line `binding.pry` in your code, that line will get interpreted at runtime (as your program is executed). When the interpreter hits that line of code, your program will freeze and your terminal will turn into a REPL that exists right in the middle of your program, wherever you added binding.pry

# Method Scope
- Methods in Ruby create their own scope. Any local variable created outside of a method will be unavailable inside of a method. In addition, local variables created inside of a method fall out of scope once your outside the method

# Math in Ruby
- When you divide integers, Ruby returns integers without rounding. The decimal is just removed. When you divide floats, a float is returned. If you divide a float and an integer, a float will be returned. 

# Booleans and Truthiness
- Control flow is the idea that we can tell our program to execute certain lines of code based upon certain conditions
- In Ruby, only false and nil are falsey. Everything else is truthy (even 0)
- Use a single bang operator to determine if something is truthy or falsey
``` Ruby
!true #=> false
!false #=> true
```
- The double-bang operator `!!` will return true or false based on whether a value is truthy or falsey to begin with

## Boolean Operators
- For && to evaluate to true both values on either side of the symbols must evaluate to true
- For || to evaluate to true, only one value on either side of the symbols must evaluate to true
- A ! "not" reverses the logical state of the operand. If a condition is true, then ! will make it false
- To check if two values are equal we use the comparison operator `==`. If two values are equal then the statement will return true

# Statement Modifiers
- Allow you to put a conditional at the end of a statement
``` Ruby
this_year = Time.now.year
puts "Hey, its 2015!" if this_year == 2015
```
- Can also use unless in a statement modifier as well
``` Ruby
this_year = Time.now.year
puts "Hey, its not 2015!" unless this_year == 2015
```

# Ruby Case Statements
- Case statements allow us to run multiple conditions against the same value without repeating ourselves
``` Ruby
case name

  when "Alice"
    puts "Hello Alice"
  when "The White Rabbit"
    puts "Don't be late, White Rabbit!"
  when "Mad Hatter"
    puts "Welcome to the tea party Mad Hatter"
  when "The Queen of Hearts"
    puts "Please don't chop off my head!"
  else
    puts "Whoo are you?"
end
```

# Looping
- The loop keyword
``` Ruby
loop do
  puts "I have found the Time Machine!"
end
```
- This loop will execute an infinite number of times

## Stopping Loops with Breaks and Counters
- We can use the `break` keyword inside the body of a loop to exit the loop
``` Ruby
loop do
  puts "You'll see this exactly once"
  break # Exit the loop
end
```
- How to use a counter
``` Ruby
counter = 0
loop do
  # increment our counter by 1 and set it equal to the sum of its current value plus 1
  counter = counter + 1
  puts "Iteration #{counter} of the loop"

  if counter >=10 # If our counter is 10 or more
    break # Stop the loop
  end
end
```
# Times Constructor
- The below will execute 5 times. Remember that times has to be called on an integer
``` Ruby
5.times do
  puts "Penguins like to jump off icebergs!"
end
```
# While and Until
- `while` will keep executing a block as long as a specific condition is true
``` Ruby
counter = 0
while counter < 20
  puts "The current number is less than 20."
  counter += 1
end
```
- `until` will keep executing a block until a specific condition is true
``` Ruby
counter = 0
until counter = 20
  puts "The current number is less than 20"
  counter +=1
end
```
# Looping - Break and Gets
- The use of the break keyword is generally avoided. 
``` Ruby
counter = 1
while counter <= 5
  puts "The counter is at: #{counter}"
  break if counter == 3
  counter = counter + 1
end

puts "We're done looping!"
```
- The gets method accepts a single line of data from the keyboard
``` Ruby
def greeting
  puts "Please type your name:"
  name = gets
  puts "Your name is #{name}"
end

greeting
```
- The gets method used without `.chomp` appends a new line to the data you are using it to get

# Looping - For Constructor
``` Ruby
for counter in 1..40 do
  puts "The current number is #{counter}"
end
```
- 1..40 is a `range` object. Starts with 1 and ends with 40. 

# Using Arrays
- The shovel method allows you to shovel items on the end of an array
``` Ruby
famous_cats = ["Garfield", "Maru", "Nala Cat"]
famous_cats << "Sam"
puts famous_cats.inspect
# ["Garfield", "Maru", "Nala Cat", "Sam"]
```
- The `.push` method will add that element to the end of an array. It does the same thing as the shovel method
``` Ruby
famous_cats.push("Simon")
puts famous_cats.inspect
# ["Garfield", "Maru", "Nala Cat", "Simon"]
```
- The `.unshift` method adds an element to the front of an array
- The `.pop` method removes the last item from the end of an array. The pop method will also supply the removed element as its return
- The `.shift` method will remove the first item from the front of an array. The shift method will also supply the removed element as its return
- The last item of an array is stored at index -1
- We can also use the `.first` method on an array to access the first (0 index) element
- The `.sort` method rearranges the contens of an array by sorting them. For strings, alphabetically, for numerical values, from smallest to highest. The return value remains unchanged after using the .sort method. Because sort returns a new array, we generally store it in another variable. 
- You can call `.sort!` which won't require you to save the return value in a new variable
- The `.reverse` method reverses an array. You can also call `.reverse!`
- The `.include?` method will return a boolean of whether or not the array contains (or includes) the element submitted inside the parentheses
- The `.first` method will return the first element of the array. Does not change the return value of the orignal array
- The `.last` method will return the last element of the array. Does not change the original array
- The `.size` method will return the number of elements in the array

# Iteration and Abstraction
- Looping occurs when you tell your program to do something a certain number of times. Iteration occurs when you have a collection of data (for example, an array), and you operate on each member of that collection
- The goal of abstraction is to remove details

# Enumerators Introduction
- Enumerators allow for iterative actions on data structures, specifically over hashes and arrays
- A **hash** is another type of collection. It stores data in associated pairs. 
- Enumerator methods allow us to iterate over every member of a collection and do something to each member of that collection
``` Ruby
students = ["Harry Potter", "Ron Weasley", "Hermione Granger"]

def turn_into_frog(student)
    puts "Poof! #{student} is a frog!"
end

students.each do |student|
    turn_into_frog(student)
end
# The above would output
"Poof! Harry Potter is a frog!"
"Poof! Ron Weasley is a frog!"
"Poof! Hermione Granger is a frog!"
#without having to call the turn_into_frog method for each student in the student array
```
- The defining characteristic of .each is that its return value is the original data structure that it was called upon
- `.collect` and `.map` are similar to `.each` except that when you call .collect or .map on an array or a hash, a **new** array or hash object is returned, not the original one. The original array does not change
- If you need the return value of your method to be a collection that's been modified by what's happening within the block, then use .collect (you can also use .each to accomplish this).
- The `.select` method returns a new collection containing all of the elements in the submitted collection for which the block's conditional is true
``` Ruby
cool_nums = [1, 2, 3, 4]

def even_nums(nums)
    nums.select do |x|
        x.even?
    end
end

even_nums(cool_nums)
#=> [2, 4]
```
- The `.find` method is similar to .select but instead of collecting and returning all of the items for which a condition is true, .find returns only first item for which it is true
``` Ruby
[1, 3, 5, 7].find do |num|
    num.odd?
end
#=> 1
```
- The `.delete_if` method will delete from the collection any items that return true for a certain condition
- The `.include?` method is used to determine if a collection contains a specific element
``` Ruby
[1, 2, 3].include?(1)
#=> true
```
- Calling `.any?` on a collection will return true if the code in the block evaluates to true for any element in the collection. The .any? method passes each element of the array it is called on to the code in between the `do`...`end` keywords

# Yield and Blocks
- The yield keyword, when used inside the body of a method, will allow you to call that method with a block of code and pass the torch, or yield, to that block.
- Think of the yield keyword as saying "Stop executing the code in this method, and instead execute the code in this block. Then return to the code in the method.
``` Ruby
def yielding
    puts "the program is executing the code inside the method"
    yield
    puts "now we are back in the method"
end
```
- The yield keyword can take parameters. If you use yield and give it an argument, it will pass that argument to the block and that data will become available to the code in the block.
``` Ruby
def yielding_with_arguments(num)
    puts "the program is executing the code inside the method"
    yield (num)
    puts "now we are back in the method"
end
```

# Blocks vs.Procs vs. Lambdas
- A closure is a block of functional code with variables that are bound to the environment that the closure is called in
- A closure
    - Can be passed around like an object (but that doesn't mean it is an object)
    - Can be defined in one scope and called in a different scope
    - Remembers the variables within its scope at the time of creation. When its called, it can access those variables even if they might not be in that current scope
- **Blocks** are a simple form of a closure in Ruby. Blocks **are not** objects. 
- Example of a block:
``` Ruby
array.each do |x|
    puts x
end
```
- **Procs** are a type of closure in Ruby that behave similarly to blocks but with a few key differences
     - A proc can be assigned to a local variable
     - A proc instance is executed by calling the `call` method  on it
     - More than one proc can be passed to a method
     - Essentially, a proc is a block turned into an object by being assigned to an instance of the Proc class
``` Ruby
greeting = Proc.new { "Hello!" }
greeting.call
=> "Hello!"
```
- A **Lambda** isn't that much different than a proc in functionality. The key differences are:
    - A Lambda expects a certain amount of arguments and checks for them; procs just return nil for the missing argument but do not throw an error
    - Procs and Lambdas return differently. Lambdas return to the calling method and procs return immediately without going back to the caller

# Collect and Return Values
- The most important thing to remember about `each` is that it does not change the return value. It implicitly returns the original array
- `map` and `collect` are different
``` Ruby
toppings = ["Pickles", "Mushrooms", "Onions"]

def hamburger(toppings)
    toppings.collect do | topping|
        puts "I love #{topping} on my burgers!"
    end
end
```
- The above method will return `[nil, nil nil]`. This is because we are using puts which always has a nil return value
- If we do the following instead:
``` Ruby
def hamburger(toppings)
    toppings.collect do |topping|
        "I love #{topping} on my burgers!"
    end
end
```
- The return value will be:
``` Ruby
["I love Pickles on my burgers!",
 "I love Mushrooms on my burgers!",
 "I love Onions on my burgers!"]
 ```

# Sorting
- Compares two elements. Returns 0 if they are the same, -1 if the first is less than the second, and 1 if the first is greater than the second
``` Ruby
array = [7, 3, 1, 2, 6,5 ]

array.sort do |a, b|
    if a == b
        0
    elsif a < b
        -1
    elsif a > b
        1
    end
end
```

## The Spaceship Operator
- The spaceship operator ( <=>) is also called the combined comparison operator
    - Returns 0 if the first operand equals the second
    - Returns -1 if the first operand is less than the second
    - Returns 1 if the first operand is greater than the second
- So instead of using if & else like above, we can simply call .sort with the following:
``` Ruby
array = [7, 3, 1, 2, 6, 5]

array.sort do |a, b|
    a <=> b
end

# => [1, 2, 3, 5, 6, 7]
```

## Abstraction: .sort
``` Ruby
dishes = ["steak", "apple pie", "vegetable soup"]

dishes.sort
# => ["apple pie", "steak", "vegetable soup"]
```

# About Hashes
- Hashes are a type of data structure
- Similar to arrays. However hashes are not indexed by number
``` Ruby
hash = {"key" => "value", "another_key" => "another_value"}
```
- Keys in hashes can be any type of data: strings, integers, or symbols
- If you try to add a second key that duplicates an existing key, you will overwrite the value of the existing key *instead* of adding a new key/value pair
## Creating Hashes
- The literal constructor
``` Ruby
my_hash = {}
#=> {}
```
## Retrieving Data from Hashes
``` Ruby
pets = {"cat" => "Maru", "dog" => "Pluto"}
pets["cat"]
#=> "Maru"
```
## Adding Keys and Values to Hashes
``` Ruby
person = {
  "name" => "Erin"
  "age" => 30
}

person["hometowm"] = "Houston, Tx"
person["favorite thing"] = "books"
person["favorite thing"] #=> "books"
```

# Ruby Symbols
## What is a Symbol?
``` Ruby
:i_am_a_symbol
:name_is_erin
```
- A symbol is similar to a string but a symbol can't be changed
- Symbols are useful as hash keys because of their immutability (can't be changed)

## Strings are Mutable
- Every time you create a string, it creates a new object in memory, even if the string text is identical to another one you've already created. Ruby has to store them separately because either one may change in the future

## Symbols are Immutable
- This means that its state can't be modified after it is created. It will always be the same size in memory. 

## Why Use Symbols as Hash Keys?
- Since all copies of a symbol have the same object_id, they use up less memory. Keys don't need to be mutable. Since they don't need to be mutable we use immutable memory-saving symbols as hash keys
- When writing key/value pairs where the key is a symbol, we can write it like this:
``` Ruby
flatiron_school = {instructor: "Isaac Newton"}
```
- In the above example "instructor" is a symbol

# Introduction to Nested Hashes
## Why Use Nested Hashes?
- Hashes can be nested. Meaning, a key in a hash can point to a value that is a collection of objects i.e. an array or even another hash

#Hash Iteration - Each
- The each iterator can also be used to iterate over hashes. Because hashes store data in key/value pairs, we will be iterating over those pairs
``` Ruby
hash = {key1: "value1", key2: "value2"}
hash.each do  |key, value|
  puts "#{key}: #{value}"
end
```
- When we iterate over a hash, the #each method yields the key/value pair together into the block
- Remember, the return value is always the original hash. #each returns the original collection on which you are calling the method

#Hash Iteration - Collect
- #collect and #map are the same thing
- We use collect to iterate over a collection of data and return a collection of the data
- We'll most often see collect used to collect the values of the hashes keys and/or collect data that we've operated on over the course of an iteration 
- Here's an example
``` Ruby
birthday_kids = {
  "Timmy" => 9,
  "Sarah" => 6,
  "Amanda" => 27
}

birthday_kids.collect do |kids_name, age|
  age
end

# => [9, 6, 27]
```
- Note the return value in the above example is an array of the values we collected
- We can also operate on the the values like in the example below
``` Ruby
birthday_kids.collect do |kids_name, age|
  age * 7
end

# => [63, 42, 189]
```
















