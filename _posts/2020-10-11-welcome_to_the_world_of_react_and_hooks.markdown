---
layout: post
title:      "Welcome to the World of React and Hooks!"
date:       2020-10-11 17:55:11 +0000
permalink:  welcome_to_the_world_of_react_and_hooks
---


For my final project with Flatiron school, I was tasked with implementing a web application utilizing a Ruby on Rails backend along with a React and Redux frontend. I decided to build a Pinterest Clone where the user can search for any images they want or choose from a preset list of suggested categories. I also wanted my user to have the ability to select images they like and ‘pin’/save those images. Using React along with Redux was new and challenging. 

React is a popular library and is similar to using vanilla JS however it has a lot of extra convenient features which make building an application a bit smoother. One of these features is Hooks, which was introduced in the newer version of React (16.8). Even though it wasn’t a requirement/our curriculum didn’t cover hooks, I thought it would be a fun challenge and great practice to build my application using some of these new functions and I was right!

The official definition of Hooks, according to reactjs.org, is they are functions that allow us to ‘hook’ into React state and lifecycle methods using functional components. One of the best things about Hooks, is that they don’t require the use of class components and thus we don’t have to worry about calling this.props. Hooks require less code and therefore better readability and can also be reused. React provides us with some built-in Hooks and you can also choose to create custom ones. In my app, I chose to implement both the useState and useEffect Hooks. 

The State Hook, useState, allowed me to set my state within my functional components. React keeps the state intact even when the component re-renders. For useState, as you can see below in my code, I set the initial state (this can be an object, array, or string depending on what you want returned). In my code below we can see that useState returns the current state value(query, favorite) and also a function that allows you to update it (setQuery, setFavorite). 

const [query, setQuery] = useState('');  
const [favorite, setFavorite] = useState([]); 

This useState Hook can be called on an eventhandler to automatically update the state, like I did in my two different components below. 

const handleClick = (e) => {
        setFavorite([...favorite, e.target.src])
        alert('You saved your pin!')}
onChange= {(e) => setQuery(e.target.value)}

This Hook is similar to how this.state and this.setState are used in a class component except for the fact that Hooks don’t require state to be an object if you decide you don’t need that.

The Effect hook, useEffect,  came into play when I needed to implement side effects from my components. Side effects are just operations that can affect other components. Utilizing useEffect allowed me to forego implementing componentDidMount, componentDidUpdate, and componentWillUnmount. This hook basically implements the same functionality as these class methods but bundled into a single API.By default, React runs these side effects after every render and by declaring them inside the component, gives them access to its props and state. 

useEffect(() => {
        fetchCategories();
            if (selected) {
            fetchPins(selected)}
      }, [fetchCategories, selected]);

In the above code, I used this Hook to implement my fetch requests and also was able to utilize my selected state so when users select a category, that selection was passed in to my fetchPins action to search for that specific selection under the condition that the user actually selects something. 

The useEffect Hook did give me some trouble at first until I remembered that it takes in a second argument. I quickly learned that I either had to pass in an empty array or the state/fetch requests I wanted the hook to pay attention to. So, for this example my second argument was [fetchCategories, selected]. I had to do this because if the user changed their selection, I would need the fetch action to return images using that updated selected state. If I didn’t put fetchCategories in then I would just get stuck in an endless loop of fetching in the console which was not fun! So, beware and make sure you utilize that second argument for this Hook. 

By implementing these Hooks, I was able to learn so much and can see why Hooks are pretty cool. They do so much with less code, are more efficient, and you don’t have to worry about using this or class components at all. There are many more Hooks that I haven’t yet used, but I plan on building more apps in React and even adding onto this one so I can further my knowledge on what these awesome functions can do.   
