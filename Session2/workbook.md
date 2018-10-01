# Code Academy: Session 2

> Think Like A Programmer in NodeJS

## Introduction
Today we're looking at programming in NodeJS. This is an introductory session to programming in NodeJS, we will cover some fundamental programming concepts, doing little examples for each thing, seeing how far we can get.

All languages have different syntax and all are accompanied with documentation. If you want to do some more reading on NodeJS https://nodejs.org/api/. You'll find that a lot of things online talk about servers and webpages, so here we're trying to abstract that all away for you so you just learn what you need to know to make something happen!

### Learning Objectives
1. Understand what NodeJS and how it relates to Javascript
1. Understand what some basic data types are
2. Know what a variable is
3. Understand what a function is and how you write one

## Part One: NodeJS Basics
You'll have heard me talk about NodeJS and Javascript and perhaps you've heard JSON or "Javascript Object Notation".
So these are all different things, Javascript is a programming language and that's where we get the keywords and syntax from. 
NodeJS is built using Javascript, and includes a bunch of extra things like package management, and provides a framework for making webapps. JSON is just a standard way of talking about and writing in code about an object, this makes it easy to transfer data between different applications and languages because the objects will always be in a known format.

- **NodeJS - Framework**
- **Javascript - Language**
- **JSON - Standardized way of describing an object**

## Part Two: Data types
Some programming languages are "typed" and this means that when you're using them you have to know what it is that you're passing around in your variables, when you reference any data then its type or "class" will dictate what it looks like and what you can do with it.

We're using NodeJS, which as we said before is built on Javascript which is not a typed language.

But to understand things later on then it's useful to understand these basic data types and the differences between them.

- Char : this is just a letter, eg ```'a'```, ```'b'``` or ```'c'``` etc
- Boolean : this is a value that is either ```true``` or ```false```
- Int : this is a whole value number, eg ```1```, ```2```, ```57``` etc
- Double : this is a number with a decimal point, eg ```1.4```, ```7.5```, ```105.81``` etc
- List : this is a list of things in [], eg ```['a', 'b', 'c'] or [1, 2, 3]```
- Object : this is a number of key-value pairs contained in {}, eg ```person = { name: "Maddie", role: "analyst" }```


## Part Three: Variables
When writing some code you'll want to be able to use and refer to different pieces of data. To do this, you hold them in a "container".

Variables have a syntax similar to this:
```javascript
var variableName = "Some Data";
console.log(variableName);

//Output
>> Some Data 
```

You can add variables together, proivided it makes sense to do so, if it doesn't Node can do some weird things that might not make sense in your program:
```javascript
var cost = 34;
var bird = "pigeon"

console.log(cost + bird);
//Output
>> "34pigeon"
```

## Part Four: Functions
A function is essentially a process that you can code up and then call from different parts of your program.

The syntax for this is:

```javascript
function functionName() {
    
    something = someNewThing;

}
```

Functions can also include parameters, and this would look like ```functionName(parameter1, parameter2)``` you can then use those pieces of data by using ```parameter1``` in the function.
Look at the example below.

You can use parameters to pass data around between different functions. 

Have a go at writing a function.

As example try: 
```javascript
function sayHello(){
    console.log("Hello");
}

function sayHelloTo(name){
    console.log("Hello, " + name);
}

sayHello();
sayHello("Pat");
```


#### If you've finished and there's still time, there is an extension workbook, and a further extension workbook.
