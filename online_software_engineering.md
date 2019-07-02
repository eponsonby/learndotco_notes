# Object Oriented Ruby
## Intro to Object Orientation
(These notes are from the Week 4 [Intro to OOP lecture](https://docs.google.com/document/d/1oplSBW2D5CuAds6VR4SHLHh3UgJo7f-yBrFL8DNx_vQ/edit))
* In OOP, we make self-contained stateful entities that can manage themselves. For example instance variables, that are able to keep data inside of them to give that thing state. For example a car has a state, the engine can either be on or off. OOP allows us to represent state.

* Properties and Methods
  - So how do we get our objects to have the characteristics and behavior that we want? Characteristics = Properties or Instance Variables. This is the data that defines our object. For example a dog could have weight and breed
  - Syntactically, we use instance variables with an @ prefix
  - Note, we only use instance variables inside classes
  - Behaviors = methods, these are the actions our dog can take
  - Syntactically, methods look like functions, except they exist inside of a classes

* Instance Methods vs Class Methods
  - We call the behavior of our classes class methods and the behavior of our objects instance methods
  - If the method does something particular to an individual (for example when a dog walks, eats, this pertains only to the particular dog)
  - If the method transcends the individual, this would be appropriate for the class (for example, creating new instances, keeping track of how many individual objects of the class exist)
``` Ruby
  # Instance Method
  def method_name(arg)
    # method body
  end
```
``` Ruby
  # Class Method
  def self.method_name(arg)
    # method body
  end
```
* Instance Variables vs Class Variables
  - We have variables associated with individual instances and those that are associated with class
  - For our dog, instance methods may include `@name`, `@weight`
  - Our dog class variables may include `@@all`
  - Instance variables should be defined in your initialize method
  - Class variables should be defined outside of a method, usually at the top of the classes

* Initialize
  - Sets up all of our properties, or instance variables of the individual object we are currently instantiating
  - We never call initialize directly, we call the class method `.new` Why?
  - Initialize gets called by the class method new, which is inherited by every Ruby class. The method new is a class method which allocates memory for the new object we are creating and then calls our initialize method if we defined one. We don't want to have to manually manage our computer's memory so Ruby does it for us. The class is thus put in charge of all this setup via the new method, which involves allocating memory for the new object and calling the initialize method in order to give the new object all of its unique data

* Readers and Writers
  - In Ruby you cannot access instance variables outside of the class (well you can but it's cheating, don't worry about it)
  - You need to write methods that give access to the object's instance variables to those using your object
  - If you want to be able to read your instance variables, you have to make reader methods
  - If you want to be able to set your instance variables after initialization, you have to make writer methods
  - It does get tedious to write readers and writers for every single class you neeed to write. There are some built in class methods that write code for us (this is called metaprogramming - code that is writing code)

* Self
  - Self means different things in different locations
  - If your code comes across a variable that is not defined locally, Ruby will implicitly add self to the front of the variable. So if you reference an instance variable without the @ and you have a reader or writer, that is what will be used. Otherwise you'll get a NoMethodError
  - Inside an instance method, self refers to that one specific instance
  - Outside of a method or inside of a class method, self refers to the class itself, not the object
  - `attr_accessor`, `attr_reader`, `attr_writer` are class methods. Self is implicitly added to the front of them, which is why they work

* Pillars of OOP
  - Encapsulation
    - Mechanism to restrict direct access to an object's properties
    - Bundle setting data in the object with other custom actions within a method
  - Abstraction
    - Abstraction is a black box concept. We only care about inputs and outputs, we don't care about all the complicated stuff on the inside
    - Its the idea of taking something complicated and reducing it to its interface with the outside world (inputs and outputs)
  - Inheritance
    - Mechanism in which a child class obtains properties and methods of a parent class
  - Polymorphism
    - The ability to present the same interface for different underlying data types and actions
    






## Object Models
### Remembering objects
* an @@ before a variable name indicates a class variable, like this: `@@class_variable`
* Class variables can be used to keep track of every instance the class creates
* To define a class method we use the `def self.method_name` syntax
* The self in this example is a reminder that the method will not be called on a particular instance of the class but rather the class itself

### Advanced Class Methods
* Class reader methods are very similar to instance reader methods. A class reader method is a method for reading the data stored in a class variable
* Class Finders - if you have a class called Person and you've set a class variable called `@@all` equal to an array of all new instances of persons you create, how would you find an individual by name in that array? You could use iteration and `.find` each time but that would be unsustainable in a large program. Instead, define a method that will teach our Person class *how* to search
* Finder class methods are responsible for finding instances based on some property or condition

### Object Orientation: Mechanics (Video)
* Why and When to Instantiate Objects?

   - Every time you want to represent a new individual in your program, you should instantiate an object of that type
   - When you have primitive data and you want to "reify" it into a more abstract representation of that data in your program. Reification - when you take a primitive and make it into something more abstract, like an instance, you are "reifying" it
   - When you want to marry some data with logic that relates to a singular concept even if its global (like a connection to an API or data source)

* What is a Singleton Class?

   - A singleton is a class that never has any instances instantiated or defined
   - Commonly used to simply group related methods and data together but to never have multiple instances represented in your program. Below is an example of a singleton. You'll never call `ErrorLogger.new` which is a giveaway that it's a singleton
   ``` Ruby
   class ErrorLogger
     def self.warn!
     end

     def self.info!
     end

     def self.export
     end
   end
   ```
   - Another example would be connection to GitHub. You'll never have more than one connection to GitHub

* When Should You Use Instance Variables?
   - An IV represents a singular property of an individual. It is the mechanic in code that allows for different things of the same family to have different values for the same property
   - For example, every person has their own name and their own DNA, thus a person class would define `@name` and `@dna` for instances
   - Its scope is defined to a singular instance

* When/Why Should You Use Instance Methods?
   - IM's are things that only individuals can do, provide a mechanism for an object to expose their internal state to the outside world
   - IM's can manipulate/mutate the internal state of an object, like changing a song's name
   - IM's also provide functionality for an individual object, like saving an instance into a database or storage

* When to use attr_accessor vs. custom reader/writer

   - The `attr_accessor` macro will provide a naive interface for reading and writing to an instance variable
   - Anytime you need something more complex you should build your own reader/writer

* When and How to Use Class Methods

   - CM's operate on the entire class and expose the class' scope to the rest of your program
   - CM's can operate as custom constructors (very useful for this) instantiating instances in new and more complex ways
   - CM's can operate on all their instances via class variables and instance memoization (Memoization simply means remembering something. When you memoize something, you teach the object how to remember it.) but do not have access to instance scope
   - CM's are commonly used for Class-wide tasks such as querying or class-wide CRUD or operations (emailing all users)

* What is a Class Constructor?

   - A CC is any class method that instantiates an instance of the class. The built-in constructor for all classes is Class.new. To customize functionality, you could override the default initialize method but it is better to extend new by wrapping it in your own constructor
   - `Artist.new_from_url` is better than overriding initialize to accept a URL as you will want to be able to instantiate an Artist without a URL

* When and Why to Use a Class Variable

   - CV's are for properties that belong to the entire class
   - A class level variable is commonly used for instance memoization

* What is Self?

   - Whenever an object needs to refer to itself, the keyword `self` is used
   - In an instance method, self will always refer to the instance itself
   - In a class method, self will always refer to the class itself
   - Self can be thought of as the thing that will receive this method call

## OO Tic Tac Toe
### Procedural vs Object Oriented Ruby
* In procedural programming, we have data and we have the procedures or instructions for operating on that data
* In PP data and procedures are two separate things
* in OOP, we have units of code that contain both data and instructions, such that an object operates on its own data structure

# ORM's and Active Record
# ORM's
### Updating Records in an ORM
* A class instance gets assigned a unique id right after being inserted into the database, with the save method
``` Ruby
def save
   if self.id
      self.update
   else
      sql = <<-SQL
         INSERT INTO songs (name, album)
         VALUES (?, ?)
      SQL
      DB[:conn].execute(sql, self.name, self.album)
      @id = DB[:conn].execute("SELECT last_insert_rowid() FROM songs")[0][0]
   end
end
```
* The Update method
``` Ruby
def update
   sql = "UPDATE songs SET name = ?, album = ? WHERE id = ?"
   DB[:conn].execute(sql, self.name, self.album, self.id)
end
```
* The Create Method
``` Ruby
def self.create(name, grade)
   student = Student.new(name, grade)
   student.save
   student
end
```
### Dynamic Orm's




