---
layout: post
title:      "JS Fun with Algorithms"
date:       2021-01-09 22:09:06 +0000
permalink:  js_fun_with_algorithms
---

This past week, I attended my first algorithm centered workshop with the BootCampers Collective group. It was a 2 hour problem-solving session where we chose algorithms we wanted to tackle as a group. I was nervous at first, but I quickly realized that all of the developers were at varying levels in their coding journeys and everyone just wanted to learn. Everyone was encouraging of each other and we ended up tackling 4 algorithm challenges during the session. I had the best time trying to solve these problems, learned so much, and met some great developers.

The instructions for one of the algorithms were as follows:

// Given a letter, return its position in the alphabet
// For example, given 'a', return 1, given 'y', return '25' 

We agreed that the first thing we wanted to do was create a string representing the alphabet. To do this we decided to write a variable holding the string of alphabet characters to which we would apply the split method, creating an array of alphabet characters.

`const alphabet = 'abcdefghijklmnopqrstuvwxyz'.split('')`

Next, we decided that the best approach was for us to iterate over this new array using the indexOf() method to find the index of each character in the array. When iterating through the array, each character’s index was returned plus one, this is because the index number for the first character in the array would be 0.

`return alphabet.indexOf(letter.toLowerCase()) + 1;`

It worked! When console logging our function ‘a’ or ‘A’ returned 1, where ‘d’ returned 4.

We then decided to do something I have never actively tried to do, we tried to break our function. We realized that if the user entered a number or any other non-string character into the function, it would break! Also, if each character in the array somehow contained more than one letter(‘abc’, ‘def’,etc...) 0 would be returned. So, using the typeof method we decided to add a validation at the top of our function to prevent this from happening non-string characters from being passed in and added a check for the length of each letter in the array, if either of these were true, null would be returned. 

`if (typeof letter !== 'string' || letter.length > 1) return null`

Our final solution looked like this.

`const getLetterPosition = letter => {
if (typeof letter !== 'string' || letter.length > 1) return null
  const alphabet = 'abcdefghijklmnopqrstuvwxyz'.split('')
   return alphabet.indexOf(letter.toLowerCase()) + 1;
}`
 
`console.log(getLetterPosition('a')) /// 1
console.log(getLetterPosition('A')) /// 1
console.log(getLetterPosition('d')) /// 4`

We solved some other algorithms as well and each one had its own challenges but with everyone working together it was a really fun way to practice algorithms while also collaborating with other developers. I will be writing more posts on other challenges as we go through them. I am definitely looking forward to the next one. If you want to join us, sign up for their next meetup at this link https://www.meetup.com/Bootcampers-Collective/event

