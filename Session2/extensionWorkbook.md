# Code Academy: Session 3

> Think Like A Programmer in NodeJS

## Introduction
So you've just finished looking at data types, variables and functions in the first part of this session.

So now we're going to look at logic and loops.

We know from previous that we have a boolean value, true or false, this is what we get when we evaluate a condition. It is either true or false.

## If

This is more of a logic check.

The syntax is:
```if (condition) { doSomething(); }```

This means that if the condition evaluates to ```true``` then the code block will execute.
If false it'll just move on.

So for example:
```javascript
var number = 4;

if (number < 5) {
    console.log("The number is smaller than 5");
}

// Output
>> The number is smaller than 5
```
but in this example if the ```number``` is larger than 5, nothing will happen. Try this by adding another log statement after the if statement and changing the number.

Conditions don't just have to be based on numbers, you can evaluate strings, objects and lists.

```javascript
var listOfFruit = ["apple", "orange", "banana"];
if ("apple" in listOfFruit){
    console.log("Apple is in the list");
}
```

## While

This is a loop, in this instance, based on the condition given.

The syntax is:
```while (condition) { doSomething(); }```

So in this, the code in the {} will execute until the condition is no longer true.

```javascript
while (true) {
    console.log("Hello");
}
```
This is called an infinite loop and the statement will be executed unendingly. Try it. I dare you.

## For

```javascript
for (i = 0; i < 5; i++) {
    console.log("Number is: ", i);
}
```

## Fun Exercise: The Guessing Game
