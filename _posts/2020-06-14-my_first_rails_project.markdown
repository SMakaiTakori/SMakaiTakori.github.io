---
layout: post
title:      "My First Rails Project"
date:       2020-06-15 01:37:55 +0000
permalink:  my_first_rails_project
---


Building out this project was a good challenge, I learned so much! We were tasked with building an app using multiple models, a join table, nested routes, and implementing Omniauth. For my app, I chose to create a ‘Doggy Airbnb’ in which my users can browse through luxury dog hotels and book themselves a hotel reservation. 

My join table was the reservation model which ‘belongs_to’ both the Dog and Hotel models. By implementing a join table and establishing ‘has_many, through: ‘ macros, methods were created that associated all three models. Another benefit of setting these relationships up is the ability to use them to implement nested routes inside of the application. Before this module, I had seen nested routes on other web applications but never really paid attention to them. 

Nested routes are very important because they allow you to capture the relationships between models within the Restful routes. For example, one of my app’s nested routes is :

```
resources :hotels do
    resources :reservations 
  end
```
 
Because hotels ‘has_many’ reservations and reservations ‘belong_to’ a hotel, this route makes sense to the application flow. These associations along with the nested routes allows our user to book a hotel reservation. They are directed to the route /hotels/:hotel_id/reservations/new when they would like to book a new reservation. The ability to have the dynamic route with a :hotel_id allows the developer to associate this new reservation with that particular hotel_id. A second nested route I set created a similar route relationship between dogs and their reservations. By being able to access the :dog_id in our dynamic nested route, I could associate a specific dog with the reservations that belong_to them. 

An exciting part of this project was being able to implement OmniAuth using Google as the Provider a.k.a Strategy, another term for an authentication partner. OmniAuth is a gem that allows the developer to use multiple strategies, allowing the user to log in to my app using their credentials already established in the provider’s database. I set up a regular log in form but because of OmniAuth, I was also able to implement a login feature that allows users to log in to my app via their google account.

I did this by creating an omniauth.rb file to hold the Rack middleware for the Google strategy, using the built-in class OmniAuth::Builder which allows us to specify one or multiple providers.

```
Rails.application.config.middleware.use OmniAuth::Builder do 
  provider :google_oauth2, ENV["GOOGLE_CLIENT_ID"],ENV["GOOGLE_CLIENT_SECRET"], skip_jwt: true
end
```
 
This middleware works in tandem with a .env file that holds the client id and client secret provided by Google during the process of setting up the callback route and permissions. When a user clicks the ‘Log in with Google’ button, Google checks for the Client Id and Client secret associated with my app to make sure it has been authorized. They are then briefly redirected to localhost:3000/auth/google to sign in through the Google sign in page. The user can then sign in with their Google account or if they don’t have one, they can set one up. After telling Google it is ok to share their information with my app, the user is logged in and redirected back to my app’s home page via the callback route I set up with Google and in my routes.

 ```
get '/auth/google_oauth2/callback' => 'sessions#omniauth'
```

I ran into some trouble at one particular point in this setup. I kept getting a ‘ 404 missing client id’ error when I went to log in with google. This was because my .env file wasn’t in my root folder so Google couldn’t validate that it was really my app that was requesting access. Thankfully, I was able to figure it out and am very excited that it works now. I learned so much from building this Rails project out from top to bottom and can’t wait to add more features and styling!

