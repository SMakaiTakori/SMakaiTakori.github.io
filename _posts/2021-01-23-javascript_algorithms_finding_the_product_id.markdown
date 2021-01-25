---
layout: post
title:      "JavaScript Algorithms, Finding the Product ID"
date:       2021-01-23 19:57:18 -0500
permalink:  javascript_algorithms_finding_the_product_id
---


 
I have been focusing on practicing algorithms in JavaScript to strengthen my JS skills and having a lot of fun doing it. There are so many resources out there and the main ones that I’ve found to help me are finding tutorials on YouTube and Udemy along with going to virtual coding meetups. By practicing with other devs, I learn so much by hearing feedback and potential strategies from different points of view for one single problem. It’s pretty cool when I think about it. One challenge we chose to tackle (using JavaScript) had the following instructions:

```
/* Write a function that properly extracts a "Product ID" from a URL. This ID is encoded in the URL in the following way:
It immediately follows -p-
It is terminated with -
Your function should return a string.
```
```

For example, given the following URLs 

example.com/product-p-8099-index.html, <--your function should return '8099'

example.com/products/gift-p-door801933-edit.html, <-- your function should return 'door801933'. 
```

After some deliberation, we decided as a group that using the split method would be the best approach. The split method is given to us by the prototype object in JavaScript and when used on a string, that string is essentially split into an array of substrings, and a new array is returned. With this knowledge we got to work creating a variable that would hold our substrings. This is our final solution, don't worry if you don't understand it, I will break it down below: 

```
const extractProductId = url => url.split('-p-')[1].split('-')[0]
 
```
The Breakdown...

We created an arrow function extractProductId which takes in a url, next we split that initial url on the ‘-p-’ giving us two substrings in an array. So, if the url was example.com/products/gift-p-door801933-edit.html , then we would now have an array that looks like this :

```
["example.com/product", "8099-index.html"]
```
The cool thing about the split method is that it can be chained on! Knowing this, we proceeded to split the second substring in the array that was returned to us, indicated by the index [1]. Once we split that on the ‘-’, we again ended up with a new array with two substrings, which gave us :

```
["8099", "index.html"]
```

Since the instructions ask us for the product ID, all that was left was to return the first substring, which we indicated by using the index[0]. 

This was a fun and challenging exercise and practicing the logic in a group setting reminded me that there is always more than one way to solve the same problem. You can try this challenge out for yourself in JSFiddle or your console. Happy Coding!

