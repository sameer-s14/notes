# Microprocessor

Microprocessor is like a small machine that is used in any equipment requires processing like traffic lite, remote control, or computers. The CPU is a microprocessor. The microprocessor is an integrated circuit that is made up of millions of transistors. However, not all microprocessors are CPUs.
Microprocessors have three parts: ALU, register, and control unit.
We give the microprocessor instruction to run our program, and those instructions (or simply codes) must be in the language the microprocessor speaks.
This language is called **Machine Code or Machine language**. In fact, all programs must be converted to machine code so that microprocessors can understand them.

# Types of Languages

## Binary Code

Read by hardware - not readable by humans

## Machine Code

Hexadecimal representation of binary code read by OS.

## Assembly Language

First Layer of Human readable code

## Middle-Level Languages

C, C++

## High Level / Scripting Language

JAVA, Python, Perl, Shell

# Javascript engine

1. Microprocessors can not understand Javascript language,so we need something to convert JS to the microprocessor language. They call it Javascript engine.
2. Javascript engine is a program that converts js into machine language.
3. Most of these engines are written in C and C++.
4. They all essentially do the same thing at a high level, but they do differ in their approach.

In order to avoid any confusion between these engines, they created a standard named ECMAScript.
So every JS engine must implement these standards.
Each year, Js contributors add some new features to JS, and they put a name for that standard like ecmascript 2015 specification or es5..

### v8

One of these js engines is created by google since they wanted to use it in Google chrome.
They call it V8.
One of the good things about v8 is it can be used stand-alone in c++ applications.

There are a lot of JS engines there, Firefox uses **SpiderMonkey**, which was the very **first js engine** created, and it is created by **the javascript creator itself**. It was used in **Netscape browser**, and later on, it became open-source and is currently maintained by Mozilla.

**Browsers**:**JS Engine**
Firefox : SpiderMonkey
Safari : JavascriptCore

### Module

A module in JavaScript is just a file containing related code.
In JavaScript, we use the import and export keywords to share and receive functionalities respectively across different modules.
The export keyword is used to make a variable, function, class or object accessible to other modules.
the simplest definition of module for me is it is a technique to reuse codes without having any code collision.


## What is passing by reference vs by value?

When we talk about passing, we either pass this variable to another function or assign it to another variable.
When a variable is declared, it is assigned a memory address
***var a = 10;***
![memory address table containing 2 rows having address and value](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*K0NA_3qkHvkcyA030jU6yQ.png)

## In javascript, we have two kinds of value:
### Primitive and reference

### Primitives value are:
boolean, string, number null undefined , Symbol
When we are working with Primitive types, javascript copies the value and assign it to another variable. So we have two variables that point to the different parts of memory with the same value.

### reference value are:
object or array
In non-primitive values, javascript doesn’t make a copy of the value when we assign or pass them to another variable or function. It makes a copy of the address of the variables in memory. So both of these variables are pointing to the same address in the memory

## What is first class function?
A programming language is said to have First-class functions when functions in that language are treated like any other variable. For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable.

## What are IIFE (Immediately invoked function expression) and closure
IIFE is a common JavaScript pattern that executes a function immediately after it’s defined.
**closure** - closure simply means when you define a function, it has access to all variables outside of the function when it was created.

## What is object literal?
JavaScript Object Literal is a data type used to define objects in JavaScript. It is a syntax for creating an object in JavaScript that is composed of key-value pairs. It is a lightweight and efficient way to create and store data.

## what is constructed function?
It is a normal function that creates an object. in javascript there are many other ways to create an object. constructed function is one of them.

## What is prototype in Javascript?
Every object in JavaScript has a built-in property, which is called its prototype. The prototype is itself an object, so the prototype will have its own prototype, making what's called a prototype chain. The chain ends when we reach a prototype that has null for its own prototype.
Feature is that if we create a object with construct function and property to its prototype it will have same memory.
**example**: 2 users having same name but 1st one users inbuilt function and second one is with prototype. 
console.log(user.getFullName2 === user2.getFullName2); // false because of diff memory
console.log(user.getFullName === user2.getFullName); // true because of same memory

## what is Reflect.apply?


## If you want to study Data Science and Machine Learning for free, check out these resources:

Free interactive roadmaps to learn Data Science and Machine Learning by yourself. Start here: https://aigents.co/learn/roadmaps/intro
The search engine for Data Science learning resources (FREE). Bookmark your favorite resources, mark articles as complete, and add study notes. https://aigents.co/learn
Want to learn Data Science from scratch with the support of a mentor and a learning community? Join this Study Circle for free: https://community.aigents.co/spaces/9010170/

