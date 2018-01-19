## Closures 😬
What are closures? Why are they required in the first place? 🤔

Let's look at an example to learn their importance. We have seen how every function can access a global variable. Let us take a very simple example to count the number of times a function is called. (Phew! Easy right? 😏)
```javascript
var counter = 0;

function add() {
    counter += 1;
}
add();
add();
add();

// value of the counter is 3.
```
Everything in the above code is nice and good 😇. But there are a lot of restrictions for this to work. 😮

1. `counter` should be accessible and changed only by `add()` method.
2.  No other program should alter the variable `counter`.

It is highly unlikely to work if we have restrictions like the above ☝. Let's try this in another way.
```javascript
function add() {
    var counter = 0;
    counter += 1;
}
add();
add();
add();
```
If we declare the variable `counter` inside the function, where are we going to store the incremented value every time? This approach does not work as well. 👎

What if we have a nested function? Good idea, seems to work. Let's try it out. 🖖
```javascript
function add() {
    var counter = 0;
    function plus() {counter += 1;}
    plus();    
    return counter; 
}
```
Oops, there are a lot of problems with the above code too, `plus()` is visible only to the `add()` function 👊. How are we gonna call it from outside? 😓

Also, we need to find a way to execute the below line only once. That is a big problem too. 😪
```javascript
var counter = 0;
```

So how do we approach this? 😴 **`closures`** to the rescue.
```javascript
var add = function () {
    var counter = 0;
    return function () {
      return counter += 1;
    }
}();
add();
add();
add();
```
Woohoo! We have solved the problem 👏👍. But the above code looks very very scary and odd 😱. Let's try to break it down bit by bit.

The below line is executed only once 😐. Confused? Wait for me till I go through the whole flow!
 ```javascript
 var counter = 0;
 ```
 The best part is that, `counter` can still be accessed even after parent function has been closed! That's the beauty of **`closures`**. 💍

Whenever a function is created, it creates a closure over its outer variables. That means, even though the function is complete the variables that were declared in the function still exist because of the presence of inner function. 💪
 
By this, we have made `counter` private. The `counter` is protected by the scope of an anonymous function, can be changed by `add()` only. ✌👌