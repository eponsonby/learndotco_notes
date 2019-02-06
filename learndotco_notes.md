# JavaScript Scope
- Scope is the current context of your code
- A variable declared in the outermost scope of a project is going to be global
- Variables declared with `var` are only available within that functions scope. Variables declared without `var` attach themselves to the global object
## Closures
- A closure is a combination of a function and the lexical environment within which that function was declared
- This environment consists of any local variables that were in-scope at the time the closure was created
- [MDN Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
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







