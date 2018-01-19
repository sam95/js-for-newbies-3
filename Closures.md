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

### IIFE and Currying 🍭🍿
We have learnt about **anonymous** functions and **IIFE** in our previous code snippets. Let's see what **currying** means. 👋

Let **IIFE** code snippets alone, you might ask what does it even mean?
**IIFE** stands for **I**mmediately **I**nvoked **F**unction **E**xpression 👀. Let's take our previous code snippet. 👂
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
The function is executed immediately when it's created. When the code is compiled, the `counter` variable's value is filled with `0`. 😈

At the time of execution, the `add()` function will contain the below value.
```javascript
function add() {
    // counter is accessible by add() only.
    return counter += 1;
}
```
Very odd, but amazing approach as well! 🤓

So the question might be, how is this working? I still don't seem to understand it well. I will give you a hint to think about. ✊

The culprit in the whole of **IIFE**'s gameplay, in specific the above code snippet is the `();` before the first `add();` call. 😈

What's **currying**? 🙏

**Currying** is a way of constructing functions that allows you to partially pass a function's arguments. I did not understand that too. Let's take an example. 👐
```javascript
var greet = function(greeting, name) {
  console.log(greeting + ", " + name);
};
greet("Hello", "JS hackers");
```
Now we clearly understand the above code, where is **currying** here? Patience pays, look at the below code. 
```javascript
var greetCurried = function(greeting) {
  return function(name) {
    console.log(greeting + ", " + name);
  };
};

var greetHello = greetCurried("Hello");
greetHello("JS hackers"); //"Hello, JS hackers"
greetHello("JS junkies"); //"Hello, JS junkies"

```
The above code does the same job as the `greet()` written above. The `greetCurried("Hello")` returns a function to `greetHello`. 👌

The function returned to `greetHello` takes only one parameter. So while calling `greetHello` you need to give one parameter only. 😛

Now, Do you have a question?

Actually, I have a question. Wait for it. 😉

**currying** can get way too complicated at times. Here I have just depicted a very simple example. I have just got you started with this. There is a lot more to it which you'll have to explore. 😀

That's all Folks! 😃🎩