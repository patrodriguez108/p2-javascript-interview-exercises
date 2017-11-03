# JavaScript Fundamental Interview Questions

1. What is the difference between undefined and not defined in JavaScript?

A function would output undefined if there were no implicit return and/or if the return is null.

A function would be unable to process if a variable of a function is not defined.

2. What is the output?
  ```js
  var y = 1;
  if (function f(){}) {
    y += typeof f;
  }
  console.log(y);
  ```
  
 The output is "1undefined". The function function f() is defined within an if block, so the logic within that if block executes. In that if block we are redefining y by adding typeof, which outputs a string indicating the type of undefined operand. Because there is no logic in the function f, f() returns undefined. Executing type of f returns a string stating "undefined". So that argument in the conditional statement is adding the output of y, which is 1, with the output of f(), which is the string "undefined" Therefore the output of y is not "1undefined"
  
3. What is a “closure” in JavaScript? Provide an example

Closure is defining a variable within an outer scope that can and will be accessed within the scope of children functions.

  ```
  var bleh = "whaa"

  function okay() {
    return "Okay but " + bleh
  }
  ```

4. What is pass by value and pass by reference?

When a variable that is defined in an outer scope is passed into a function, that value is copied within the scope of the function and processes this copy as a local variable. The original variable in the outside scope remains unchanged. This is passing by value.

Passing by reference would be when that variable defined in the outside scope is passed into a function and redefines the value of the variable within the outer scope after the function is run. This is impossible when using Javascript.

5. What is the difference between the function declarations below?

  ```js
  var foo = function(){
    // Some code
  };
  ```
  **vs**
  ```js
  function bar(){
    // Some code
  };
  ```
 
 It's just a matter of syntax. Both are valid ways to define a function.
  
6. What is the output for the code below?
  ```js
  $.ajax({
    method: 'GET',
    url: '/foo'
  })
  .done(function(response) {
    console.log('done callback response', response)
  })

  console.log('outside response', response)
  ```
  
 The output would state that response is undefined
 
 
7. If the jsLevelUp() was called, why would it lead to an error? How could it be fixed?
  ```js
  var jamie = new User({
    id: 1,
    name: 'jamie',
    gender: 'other',
    jsLevel: 1
  })

  jamie.jsLevelUp()
  /*
    After calling jsLevelUp() it will cause the following error:

    jsLevel is not defined for jQuery
  */

  function User(attribute) {
    this.id = attribute.id || null
    this.name = attribute.name || ''
    this.gender = attribute.gender || ''
    this.jsLevel = attribute.jsLeve || 0
  }

  User.prototype.jsLevelUp = function() {
    var id = this.id
    $.ajax({
      method: 'PUT',
      url: '/users/' + id
    })
    .done(function(response) {
      /* HINT it has to do with this line */
      this.jsLevel = response.jsLevel
    })
  }
  ```
We would need to define a prototype function called .jsLevelUp()

8. What does this do and why would it be useful?
  ```js
  (function() {
    console.log('I am self invoking')
  })()
  ```
It would call on the function without needing to write any extra characters below
  
9. Implement the following function `add(num1)(num2)`. For example: `add(1)(1)` = 2

  ```
  function add(num1) {
    return function addToThis(num2) {
      return num1 + num2
    }
  }
  ```

10. Write a function that prints out the amount of times it has been invoked.

  ```
  i = 0

  function invokeMe() {
    i += 1
    console.log(i)
  }
  ```
