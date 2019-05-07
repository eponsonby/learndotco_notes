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

   When you have primitive data and you want to "reify" it into a more abstract representation of that data in your program
