# Exercise 1

Write a function such that each lowercase letter becomes uppercase and each uppercase letter becomes lowercase.

## Test Cases

console.log(alternateCase('hello world'));  
console.log(alternateCase('HELLO WORLD'));  
console.log(alternateCase('hello WORLD'));  
console.log(alternateCase('HeLLo WoRLD'));  
console.log(alternateCase('12345'));  
console.log(alternateCase('1a2b3c4d5e'));  
console.log(alternateCase('String.prototype.charCodeAt'));  
console.log(alternateCase(alternateCase('Hello World')));  

## Expected Results

HELLO WORLD  
hello world  
HELLO world  
hEllO wOrld  
12345  
1A2B3C4D5E  
sTRING.PROTOTYPE.CHARcODEaT  
Hello World  


# Exercise 2

Write a function that accepts a string as an argument and returns the reverse of it

## Test Cases

console.log(reverseString('Hello, World!'));  
console.log(reverseString('This is a test'));  
console.log(reverseString('Javascript is great!'));  
console.log(reverseString('wRjuUJvJxbnyTB3?sCLAp2mbGL3xe8'));  
console.log(reverseString('A'));  

## Expected Results

!dlroW ,olleH  
tset a si sihT  
!taerg si tpircsavaJ  
8ex3LGbm2pALCs?3BTynbxJvJUujRw  
A
