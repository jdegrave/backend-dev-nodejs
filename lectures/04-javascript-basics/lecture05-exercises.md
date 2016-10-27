# Exercise 1

Write a function that takes a phone number as an argument and performs the following:

- If the phone number is less than 10 digits assume that it is bad number
- If the phone number is 10 digits assume that it is good
- If the phone number is 11 digits and the first number is 1, trim the 1 and use the last 10 digits
- If the phone number is 11 digits and the first number is not 1, then it is a bad number
- If the phone number is more than 11 digits assume that it is a bad number

## Test Cases
console.log(phoneNumber('(123) 456-7890'));
console.log(phoneNumber('123.456.7890'));
console.log(phoneNumber('11234567890'));
console.log(phoneNumber('21234567890'));
console.log(phoneNumber('123456789'))

## Expected Result
1234567890
1234567890
1234567890
0000000000
0000000000


# Exercise 2

One of the simplest and most widely known ciphers is a Caesar cipher, also known as a shift cipher. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the ROT13 cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function that takes a ROT13 cipher and decodes it.

Hint: look into charCodeAt() - capital A is at ???, capital Z is at ???

## Test Cases
console.log(cipher('SERR CVMMN'))
console.log(cipher('LBH QVQ VG'));

## Expected Result
FREE PIZZA
YOU DID IT
