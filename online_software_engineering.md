# Object Oriented Ruby
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
   - CM's can operate on all their instances via class variables and instance memoization but do not have access to instance scope
   - CM's are commonly used for Class-wide tasks such as querying or class-wide CRUD or operations (emailing all users)

* What is a Class Constructor?

   - A CC is any class method that instantiates an instance of the class. The built-in constructor for all classes is Class.new. To customize functionality, you could override the default initialize method but it is better to extend new by wrapping it in your own constructor
   - `Artist.new_from_url` is better than overriding initialize to accept a URL as you will want to be able to instantiate an Artist without a URL
   
