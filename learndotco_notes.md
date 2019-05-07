# JavaScript Scope
- Scope is the current context of your code
- A variable declared in the outermost scope of a project is going to be global
- Variables declared with `var` are only available within that functions scope. Variables declared without `var` attach themselves to the global object
## Closures
- A closure is a combination of a function and the lexical environment within which that function was declared
- This environment consists of any local variables that were in-scope at the time the closure was created
- [MDN Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- The inner function is the closure
- (https://medium.freecodecamp.org/javascript-closures-simplified-d0d23fa06ba4)
## Shadowy variables
``` javascript
var animal = 'dog';
function makeZoo() {
    var animal = 'cat';
    conosle.log(`I think Ill put this ${animal} in the zoo.`);
}
makeZoo(); // I think I'll put this cat in the zoo
animal // dog
```
- This is called shadowing, when the inner variable shadows the outer variable of the same name. Only the one declared inside the makeZoo function is used within the function and only the one declared outside the function is available outside of it.

# JavaScript Arrays
- JS arrays contain all types of values and can be of mixed types
- You can create arrays in two different ways
  * Array Literals look like this:
  ``` javascript
  var myArray = [2, 3, 5, 7, 11];
  ```
  * The array constructor looks like this:
  ``` javascript
  var evenNumbers = new Array();
  ```
## Adding an Element
- JavaScript allows us to `push` elements on the end of an array
``` javascript
var superheroines = ["catwoman", "mystique"];
superheroines.push("wonder woman");
// superheroines is now "catwoman", "mystique", "wonder woman"
```
-  We can also `unshift` elements onto the beginning of an array
``` javascript
var cities = ["New York", "San Francisco"]
cities.unshift("Philadelphia")
// cities is now "Philadelphia, "New York", "San Francisco"
```
- Both of these actions change the underlying array. They **mutate** its value
- The **spread operator** spreads out the arrays contents, it creates a new array in place, rather than modifying the original one
``` javascript
var cities = ["New York", "San Francisco"]
["Philadelphia", ...cities] // "Philadelphia", "New York", "San Francisco"
cities // ["New York", "San Francisco"]
```
- Can also be used at the beginning of the array
``` javascript
var cities = ["New York", "San Francisco"]
[...cities, "Philadelphia"] // ["New York", "San Francisco", "Philadelphia"]
```
- To preserve the new array, we need to assign it to a variable:
``` javascript
var cities = ["New York", "San Francisco"]
// we can assign it to the existing cities variable
cities = ["Philadelphia", ...cities]
// but if we have a const
const cats = ["Milo", "Garfield"]
// We need a new variable
const newCats = ["Felix", ...cats]
```
- While we *can* add elements to an array at specific indexes it's best not to. Adding elements directly inserts `undefined` if the length of the array also needs to be increased, which can lead to unexpected behavior
## Accessing an Element
- You can get elements out of arrays if you know their index, array elements' indexes start at 0
``` javascript
var celebrities = ["Oprah", "Huffington"]
console.log(celebrities[0]);
// will print "Oprah"
```
## Removing an Element
- To remove an element from the beginning of an array, use the `shift` method. This method **mutates** the array
``` javascript
const days = ["Monday", "Tuesday", "Wednesday"]
days.shift() // returns the removed element, in this case, Monday
```
- Use the `slice` method to remove an element from an array **without** mutation
- The first argument specifies where the slice starts, the second specifies where it ends
- To remove one element from the beginning use `slice(1)`
``` javascript
var cats = ["Garfield", "Otis"]
cats = cats.slice(1) // ["Otis"]
cats // ["Otis"]
```
- `cats = cats.slice(1)` sets the variable cats to the new array. Use a different variable to avoid mutation
- Use negative indexes to get the last `n` elements of an array
``` javascript
var cats = ["Milo", "Garfield", "Otis"]
cats.slice(-2) // ["Garfield, "Otis"]
cats.slice(-1) // ["Otis"]
```
- To remove an element from the end of an array, use the `pop` method. This method **mutates** the array
``` javascript
var iceCreams = ["chocolate", "vanilla", "strawberry"]
iceCreams.pop() // returns the removed element, in this case, "strawberry"
iceCreams // ["chocolate, "vanilla"]
```
- Use `slice` to remove an element from the end of an array without mutating it
``` javascript
var iceCreams = ["chocolate", "vanilla", "strawbery"]
iceCreams.slice(0, iceCreams.length - 1) // ["chocolate", "vanilla"]
iceCreams // ["chocolate", "vanilla", "strawberry"]
```
- To remove an element from the middle of an array, use the `splice` method
- The `splice` method takes an index in the array as the first argument, the # of elements to remove as the second argument, and any number of elements to add after that. All arguments are optional. With no arguments, `splice` returns an empty array and does nothing to the target array
``` javascript
let items = [1, 2, 3, 4]
items.splice(1)
// this will remove everything after index 1 (inclusive) and return the removed items [2, 3, 4]
items // 1

items = [1, 2, 3, 4]
items.splice(1, 1)
// at index 1, remove 1 item. It returns the removed items: [2]
items // [1, 3, 4]

items = [1, 2, 3, 4]
items.splice(1, 1, 6, 7)
// at index 1, remove 1 item and add 6 and 7
// it returns the removed item: [2]
// and adds the items to be added starting at the removal index
items // [1, 6, 7, 3, 4]
```
- `slice` combined with the `spread operator` makes removing from the middle of an array much easier
``` javascript
var items = [1, 2, 3, 4, 5]
// the below slices from the start up to (not including) index 2 and then a slice from index 3 to the end
[...items.slice(0, 2), ...items.slice(3)] // [1, 2, 4, 5]
```
# JavaScript Objects
- In programming, "associative data structures" are like dictionaries. They contain pairs of keys and values. 
- In JS, the barebones associative data structure is called an *object*. That means that, in an object, you can look up something by its key and get back its value
- You might hear people refer to objects as 'dictionaries'
## Creating Objects
- Two ways to create an object: with the literal syntax and with the `Object` constructor. A constructor constructs objects
- Literal Syntax:
``` javascript
var meals = {};
```
- The curly braces above are an object
- The Object Constructor:
``` javascript
var meals = new Object();
```
- You can also initialize an object with key-value pairs when you create it
``` javascript
var meals = { breakfast: "oatmeal" };
// or equivalently
var meals = new Object({breakfast: 'oatmeal'})
```
- In the above example, `breakfast` is the key and `oatmeal` is the value
- Note that all keys in JavaScript objects are strings. If you create a key with a number, it becomes a string, like this '1'
- Note also that keys must be unique. If you were to initialize the following object:
``` javascript
var meals = {
    breakfast: 'eggs',
    breakfast: 'bacon'
}
```
- And then checked the value of meals, it would be `{ breakfast : 'bacon' }`. Only the last key-value pair to use breakfast as the key gets saved. Values don't have to be unique though
``` javascript
var meals = {
    breakfast: 'avocado',
    lunch: 'avocado',
    dinner: 'avocado'
}
```
- If you have a variable `const first meal = 'breakfast'` and tried to create an object `var meals = { firstMeal: 'oatmeal' }`, the meals object key would be `firstMeal`, not `breakfast`
- You can use in ES6, wrap the key in square brackets so that you can use variables as object keys
```javascript
var meals = { [firstMeal]: 'Oatmeal'}
```
- We can access the values in an object using dot notation or square-bracket notation. Note that when we use dot notation, we do not wrap the key in quotes, the key must be able to be treated as a string.
``` javascript
meals.breakfast /// 'oatmeal'
meals['breakfast'] /// 'oatmeal'
```
- Could also do the following but we must use bracket notation if we can to access values that belong to a variable key
``` javascript
meals[firstMeal] // 'oatmeal'
```
## Adding to an Object
- We can initialize an object with some key-value pairs
``` javascript
var meals = {
    breakfast: 'oatmeal'
    lunch: 'burrito'
    dinner: 'steak'
}
```
- We can also add new key-value pairs to objects using dot syntax
``` javascript
meals.snack = 'yogurt';
```
- We can also add key-value pairs using bracket notation
``` javascript
meals['second breakfast'] = 'bagel'
```
- We can also use variables as keys
``` javascript
var sweetMeal = 'dessert'
meals[sweetMeal] = 'cake';
meals.dessert // cake
meals[sweetMeal] // cake
```
- We can also update key-value pairs using the key
``` javascript
meals.breakfast = 'cereal'
```
- The above changes are all *destructive*. If we apply these changes to an object by passing the object to a function, the original object will change
``` javascript
function destructivelyUpdateObject(obj, key, value) {
    obj[key] = value

    return obj
}
const recipe = { eggs: 3 }
destructivelyUpdateObject(recipe, 'flour', '3 cups')
//returns { eggs: 3, flour: '3 cups' }
// but also
recipe // { eggs: 3, flour: '3 cups' }
```
- `Object.assign()` can be used to create a new object that stores both the old and new properties
- Can be used to create a new object and pass it properties from existing objects. The first value is the target object that gets modified. All the values afterward can be any number of objects. It then copies them from left to right onto the target object. (But if two objects share a key, the right-most object's value for that key will win).
``` javascript
Object.assign({}, { foo: 'bar'})
// { foo: 'bar'}

Object.assign({ eggs: 3 }, { flour: '1 cup' })
// { eggs: 3, flour: '1 cup' }

Object.assign({ eggs: 3 }, chocolate: '1 cup', flour: '2 cups'}, { flour: '1/2 cup' })
// { eggs: 3, chocolate: '1 cup', flour: '1/2 cup' }
``` 
- `Object.assign()` allows us to rewrite the above function in a non-destructive way
``` javascript
function UpdateObject(obj, key, value) {
    return Object.assign({}, obj, { [key]: value })
}
// It's impt that we merge everything into a new object
// such as the empty {}, otherwise the obj object will be modified

const recipe = { eggs: 3 }
updateObject(recipe, 'chocolate', '1 cup')
// returns { eggs: 3, chocolate: '1 cup'}
recipe // { eggs: 3 }
// recipe has not changed
```
- This function can also be shortened as follows
``` javascript
function updateObject(targetObject, updatesObject) {
    return Object.assign({}, targetObject, updatesObject)
}
```
## Deleting a Key-Value Pair
- We can delete key-value pairs as follows
``` javascript
var meals = { breakfast: 'oatmeal', lunch: 'turkey', dinner: 'steak' };
// the delete operator returns true if it has successfully
// deleted, false otherwise
delete meals.dinner; // true

meals;
// returns { breakfast: 'oatmeal', lunch: 'turkey' }
```
## Changing a Value
- We can update a value as follows
``` javascript
var meals = {
    breakfast: 'oatmeal',
    lunch: 'turkey',
    dinner: 'steak'
};
meals.breakfast = ['oatmeal', 'banana'];
meals;
// {
//    breakfast: ['oatmeal', 'banana'],
//    lunch: 'turkey'
//    dinner: 'steak'
// }
```
- We can change a value non-destructively using Object.assign():
``` javascript
var meals = {
    breakfast: 'oatmeal',
    lunch: 'turkey',
    dinner: 'steak'
};

Object.assign({}, meals, { breakfast: ['oatmeal', 'banana'] })
// returns {
//    breakfast: ['oatmeal', 'banana'],
//    lunch: 'turkey',
//    dinner: 'steak'    
//    }
meals
// still {
//    breakfast: 'oatmeal',
//    lunch: 'turkey', 
//    dinner: 'steak'
//    };
```

# Javascript Intro to Looping
## The For Loop
- This loop is the most common. Looks like this
``` javascript
for ([initialization]; [condition]; [iteration]) {
    [loop body];
}
```
- Initialization: an expression (including assignment expressions) or variable declaration. Typically used to initialize a counter variable. This expression may optionally declare new variables with the var keyword
- Condition: an expression evaluated before each loop iteration. If this statement evaluates to true, the statement is executed
- Iteration: a statement executed at the end of each iteration. Typically this involves incrementing or decrementing a counter, bringing the loop ever closer to the end
- Loop body: code which runs on every iteration as long as the condition evaluates to true
- Use a `for` loop when you know how many times you want the loop to run (for example, when you have an array of known size)
- Example of a `for` loop
``` javascript
for (var i = 1; i < 100; i++) {
    console.log("Hello, world the " + i + " time")
}
```
## The While Loop
- Similar to an if statement except that its body will keep executing until the condition evaluates to false. Looks like this:
``` javascript
while ([condition]) {
    [loopbody];
}
```
- While loops are best used when we don't know how many times a loop needs to run - that is the condition is dependent on a dynamic function/return value
- Example of a while loop:
``` javascript
function maybeTrue() {
    return Math.random() >= 0.5; // returns a random # between 0 (inclusive) and 1 (exclusive)
}
// run until maybeTrue returns false
// this means the body of the loop might never run
while (maybeTrue()) {
    console.log("And I ran; I ran so far away!");
}
```
## The Do-While Loop
- Almost exactly the same as the while loop, except for the fact that the loops body is executed at least once before the condition is tested. Looks like this:
``` javascript
do {
    [loop body];
} while ([condition]);
```
- do-while loops are rarely used since very few situations require a loop that blindly executes at least once.
``` javascript
var i = 0;

function incrementVariable() {
    i = i + 1;
    return i;
}
 do {
     console.log("doo-bee-doo-bee-doo");
     } while (incrementVariable() < 5);
```
- review "Beatles Loops Lab" on learn.co for good examples

# The DOM
- The DOM (Document Object Model) provides a way of manipulating HTML and XML documents. 
- The highest level of the DOM tree is the window object. Think of the window as the browser window. The window contains the entire DOM document. All components of your HTML file will be accessible from within the window. 
- The document object represents any web page loaded in the browser. The document contains all the nodes that represent the HTML elements of the page. We use the document object to traverse through the HTML and manipulate the elements. 
- We can select elements in the document with JavaScript and jQuery. 
- Developers use a library called jQuery for interacting with the DOM. 
 
 # Traversing Nested Objects
 





