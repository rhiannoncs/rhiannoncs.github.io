---
layout: post
title:      "Storyteller, now with jQuery!"
date:       2018-08-23 20:09:59 +0000
permalink:  storyteller_now_with_jquery
---


I took my Storyteller app, which I wrote about [here](http://rhiannonshoults.com/storyteller_a_rails_app), and added some features using jQuery for a more streamlined experience.  The Github repo is [here](https://github.com/rhiannoncs/storyteller-rails-app).

## Getting Started

As usual, understanding how everything works together in the Rails framework was one of the major challenges.  The Flatiron curriculum gave a good overview of the asset pipeline and I thought I understood it, but getting all of my JavaScript files to load and jQuery to work gave me some trouble.  It turned out that I was listing the required files in my application.js file in the wrong order.  jQuery needs to be loaded first, followed by the individual files, and then the tree at the end.  Which makes perfect sense when you think about it, but it's interesting to really delve into what the Rails "magic" can deal with to smooth the development process out and what it just can't overcome.

## Features

The first thing I worked on was the random prompt generator on my front page.  When I created this initially, it worked by reloading the page which caused the controller to choose a different randomly selected prompt.  At the time I knew this was stupid and I was looking forward to learning JavaScript so I could implement this in a more seamless way.  I think the most complicated thing about integrating JavaScript into a Rails app is that you don't have access to the Ruby methods and the database from JavaScript files.  This involves having to think of a way to pass data back and forth through requests.  To make the prompt generator, I created a `random` route in my Prompts Controller.  It is essentially a show resource page, but the prompt is selected not by a passed in id, but by the controller selecting a random prompt.

I next wanted practice grabbing details and adding them to a page, so I created buttons to load details about a story on a team's show page.  Throughout the app I am using Active Model Serialized JSON and converting the received data into JavaScript Model Objects.

The next feature I added was probably the most complicated.  I wanted to create a public story browser by putting a link at the bottom of a story's show page that would load in the data from the next story that is marked as public, that is, not team members only.  This would be the main way that a user without an account would use the site.  What was complicated was determining which story should be selected as the next public story, since you can't query the database from JavaScript functions.  I went through a few iterations of this feature, but I eventually ended up adding a `next_public` instance method to my Ruby Story class and adding this to the serializer, which enabled me to access that data when creating the JavaScript Story Object and then update the data in the "Next Public Story" button with the id of the targeted story.  I learned a lot through this process.

To load a full index of items, I added a feature to the user dashboard where, on the press of a button, a fetch request is made to the prompts index route, which then creates Prompts from each and appends the content of those Prompts to the dashboard page without a refresh.

The final feature was to get rid of the separate page for adding a submission to a story, which felt very clunky, and adding the form to the bottom of the story show page (for stories that the user is allowed to add to).  Then I used jQuery to post to the submissions route, creating the submission and appending its content directly to the page.  It is a much more seamless experience.

## Further Thoughts

I definitely have ideas for how I would like to further update this app for my portfolio.  Obviously I need to do a lot of front-end work, there is no styling at the moment and it is ugly as sin.  There are also more features that could be converted to jQuery functions so that there are not so many pages in the app.  It gets very complicated to implement a lot of those with this app because so much of it is privacy restricted, and making sure that that all gets retained when updating the features is complex.  It is definitely worth doing, though - this has been a valuable learning experience for me.
