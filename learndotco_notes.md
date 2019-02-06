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
- JavaScript allows us to `push` elements on the end of an array
``` javascript
var superheroines = ["catwoman", "mystique"];
superheroines.push("wonder woman");
// superheroines is now "catwoman", "mystique", "wonder woman"
```
-  

