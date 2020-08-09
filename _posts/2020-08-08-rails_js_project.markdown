---
layout: post
title:      "Rails/JS Project "
date:       2020-08-09 00:45:30 +0000
permalink:  rails_js_project
---


For this project, I was tasked with building an application that utilized both Rails and Javascript. For the backend, I used the Rails api generator to handle the backend restful routing, database setup, and controller actions. The frontend consists of Javascript, HTML, and CSS. Honestly, when I first started this Javascript module, I thought the concepts were so different from what I had learned in the past Ruby projects and modules. After speaking with a developer friend who assured me many of the concepts were the same, I started to view Javascript in a different light.

Like Ruby, I saw Javascript was an object oriented language. Many of the tools used in Javascript are similar as well, I just had to get used to the different syntax and names of certain tools/methods. With practice, I found that the syntax started to come easier. I used my knowledge of Rails to help me understand what was happening with certain functions, keywords, and concepts that come with Javascript. Some of these similar concepts include methods for cycling through arrays, loops, constructor functions, scoping, and the this keyword.

My app is a simplified version of the old school Tamagotchi handheld game that was popular in the 90s. I had to use at least three fetch requests and two CRUD actions to complete the project requirements. My first step was to wireframe and decide exactly what my Models and associations would be, along with how I wanted the app to flow from a user’s standpoint. I created a Pet and an Activity model and decided that a Pet has_many :activities and of course Activity belongs_to :pet.

I wanted the user to be able to create a pet from the given choices, and then click on certain activities in order to update the pet’s current mood. I also wanted the user to be able to edit their current pet or owner’s name if they wanted. From mapping this out, I knew I would need two POST fetch requests and one PATCH, which would subsequently require my app to use the create and update CRUD actions.

In setting up my Pet and Activity classes with constructor functions, I compared this to using the initializer in Ruby where properties of the Model/Class are being passed in as arguments and initialized in order for us to use them when creating or manipulating instances of the object. Where Ruby uses the self keyword, Javascript uses this to refer to the object it belongs to. 

When writing out my fetch requests I found the syntax to be tricky, but with practice it became easier. I also learned to use the debugger along with console.log throughout pretty much every step, from event listeners to each of my fetch requests to ensure I was 1) grabbing the correct property/div I needed to change in the DOM, 2)  fetching and capturing the correct data I wanted to update/create, and 3) actually updating the DOM using object literals, which was pretty fun once I got the hang of it. 

I feel like I have learned so much about Javascript and there is still so much to keep learning, which I am looking forward to. Setting up both the back and front end for my own application really allowed me to see how an entire application works from routes to controller to updating the DOM so the user gets the experience you want. Thanks to Javascript’s asynchronous actions, updating the DOM seems so instantaneous to the user, however going through the process myself I am amazed at what I can now do using Rails and Javascript together. I am excited to see what else I can add, so I will be expanding on my app in the future. 

