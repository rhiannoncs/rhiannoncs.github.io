---
layout: post
title:      "Storyteller, a Rails App"
date:       2018-05-10 12:10:28 -0400
permalink:  storyteller_a_rails_app
---


For my first Rails project, I decided to create a collaborative storytelling app.  It's called Storyteller, and the Github repository is [here](https://github.com/rhiannoncs/storyteller-rails-app).  My 7-year old son really likes to code games using Scratch but when I code apps like my job-hunting Sinatra app, he thinks it's kind of booooring (his words).  So, I wanted to make something he would think was fun and interesting.  Mission accomplished; he thinks this project is a lot of fun and he was asking me questions about how Ruby and Rails works.

## Project Overview

Without being logged in, the only thing that a visitor can do is view stories that have their privacy setting set to public, look at auto-generated writing prompts and log in or create an account.

After creating an account a user can view their dashboard, which enables them to join teams, create new teams, start new stories, view stories they have contributed to, view stories that have not been updated recently, view writing prompts, submit writing prompts and view their profile.

Looking at a story lets the user read it and if they are a member of the team that controls that story, add to the story and edit the story details.  If a user has made a contribution to the story, that user can edit their own contributions to the story, but not anyone else's.

Viewing a team page enables a user to join if the team is open for membership; otherwise it shows a message that the team is not accepting new members.

A user's profile is only viewable by logged-in users - it shows the user's contact information and public stories they have contributed to.

## The Planning Process

I created a long document with an overview of what I would like the app to do, the models and model relationships I would need, and then what each view would need to include.  While things definitely evolved along the way, I stuck with my initial plan for the most part, and this made it very straightforward for creating the app.

I have six models in my app, each with relationships with other models, validations, methods, its own controller and its own views. I also have sessions and application controllers, layouts and helpers. In making this app, I became aware of just how large Rails apps can get very quickly!

## Coding

While coding the app was fairly straightforward, I did encounter some challenges along the way.  Facebook has updated its restrictions on using a secure domain for login recently and figuring out how to make that work with my local application took some research.

There were also many instances where I knew ways to make something work in general, but I had to figure out how to do them in the Rails-preferred way.  I definitely now understand what is meant when Rails is described as opinionated.  I'm sure it is good for me to learn best practices, though occasionally it feels like beating my head against the wall to determine the exact syntax necessary.

I also did a lot of reading on the MVC framework and custom helpers, trying to make sure I was always putting my logic in the correct place and making things as DRY as possible.
