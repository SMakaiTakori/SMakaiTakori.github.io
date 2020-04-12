---
layout: post
title:      "Sinatra Project - Building the My Wishlist App"
date:       2020-04-12 14:49:42 -0400
permalink:  sinatra_-_building_the_my_wishlist_app
---

This project was inspired by Amazon’s wishlists feature and so wanted to see if I could create one myself. The goal was to create this app so that it can store and keep track of all the user’s wishlists. 

We were tasked with creating our own MVC web application using Sinatra and ActiveRecord. Sinatra is built on Rack and allows us to handle HTTP requests, directing them to routes in our controller and allowing us to send the proper response back. ActiveRecord allows us to create our database and tables and set up relationships between our models. MVC stands for models, views, and controllers which is the core structure of this and many other web applications. The idea behind this file structure, is to implement separation of concerns so that the application code is well organized and to optimize functionality. 

Models are written using Ruby classes and used to connect to the database utilizing migration tables to set up relationships between our objects and persist data. Views are written as .erb files, using both HTML and embedded Ruby that contain the information we want to send back to the browser so the user can see the information they requested. Controllers are like the middle man, they receive the request sent from the browser/user, and with the use of GET, POST, DELETE, and PATCH methods, run the code based on the request by using models, and finally the particular view defined in the code is rendered so the user can see the requested information in their browser. 

I learned so much regarding the information flow from the server, browser, and application and how they all talk to each other through the use of the established routes inside the controllers.This flow then extends to the other pathways established between the controller, models, and views. At first, it was a lot to wrap my head around because there are so many pathways utilized in the back end. From the time a user signs up and logs in, clicking ‘like’ buttons and submitting forms, to sending the user back the information they request, to the time the user logs out. It’s kind of amazing how all these different pieces work together to show you a post, meme, or whatever the user requests to view. Pretty cool!

I also learned about the use of cookies and sessions. I have heard of cookies before and of course we all get those notices that sometimes come up when visiting a new website, where it tells the user the site uses cookies and asks your permission to use them. Even though I had heard of them, I never really got how they worked, until I had to work with them in order to build this My Wishlist application. I had to get used to how cookies and sessions worked and they definitely gave me trouble during certain points while building this app. 

Since HTTP is stateless, meaning each new request is treated as an individual request, the server doesn’t keep track of what or if the user is logged in, unless you have this block of code in your controller :

```
configure do
 enable :sessions
 set :session_secret, "secret"
end
```

By establishing this block in my controller, I essentially was giving each controller action access to sessions when a request is processed. In the controllers, I used this session hash to keep track of each user so the browser and server knew exactly which user was logged in and by extension what views were rendered. For example, I made it so a user can’t see the delete and edit buttons while viewing another user’s wishlist. They are only allowed to see and use these features if they are logged in to their own account and viewing their own wishlists. This is just one example of how important sessions are. If we didn’t keep track of which user was logged in, it would be so easy to manipulate another user’s creations, which we can all agree would not be good user experience. 

The main issue I had regarding sessions was that whenever I created and logged in as a new user, a session hash was created in order to keep track of that user. What I quickly realized though is that everytime I visited my port, I was still logged in due to me enabling sessions in my application controller and establishing the session[:user_id] as the user id when every user signs up. This was an issue for me because I was doing a lot of testing to make sure my users could sign up and login(I had a ton of users) which I wasn't able to do because the session persisted. At first, I didn’t have a logout button, which would have been handy because creating this route allows the user’s session to be deleted. Therefore, in order to test out other features, I had to remember to go into the browser and manually delete the session every time, which became annoying. Thankfully, I learned from this and established a logout route which made my life so much easier! 

