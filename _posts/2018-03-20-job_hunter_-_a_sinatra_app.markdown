---
layout: post
title:      "Job Hunter - a Sinatra App"
date:       2018-03-20 20:23:35 +0000
permalink:  job_hunter_-_a_sinatra_app
---


In searching for an idea for my CRUD app, I wanted to create something that seemed like it would be useful in my life. I sometimes research companies and job postings to get an idea of what is out there so I can hit the ground running after I complete the Flatiron program. As I’m doing this I save stuff in Evernote - lists of companies with their websites, copy and pasted job postings so that I remember what tech skills certain companies are generally looking for, etc. I thought it would be fun to create an app specifically designed for maintaining this information.

The Github repository for this project can be found [here](https://github.com/rhiannoncs/job-hunter-sinatra-app).

## The Planning Process
I started by planning out my object models and their relationships. I knew I needed user accounts for the site, with user ids and passwords that could be authenticated. Users have many actions, which belong to that user. I also created models for companies, job postings, company contacts and skills. Since postings have many skills and skills can have many job postings, I created a join table called skill_postings to handle this relationship. The most complex relationship in my models is that companies have many skills through postings, which are obtained through the skill_postings table. Skills also have many companies, with the relationships working in reverse. It was fun to get this working within my app, and exciting to see how seamless the ActiveRecord associations can be - ActiveRecord is amazing!

I next planned out what each page and form in my app should do, including who should be able to access what and have which permissions. Without being logged in, a visitor can only access the log in and sign up pages.  Once logged in, a user can see companies, contacts and postings that anyone has created. Only a logged in user can see their own actions, and the pages that list every company, posting and action a user has created. Only the user who created a resource can edit or delete that resource. Every action, contact, company, posting and skill has its own detailed listing page.  I also created a skill ranking page that shows every skill ranked by the number of postings that mention that skill.

## Coding

My app loads to an index page with links to log in or create an account. Once logged in, a user is directed to a dashboard that lists all of their recent activity and contains links to create resources and view resources. A layout page places a header with links to the login and logout pages at the top. If a user is already logged in, the login page redirects to the user dashboard.

My major challenge while making this app was managing the complexity of the skill and posting associations. Once I had that managed it was surprising how easily it came together. ActiveRecord makes a lot of things very simple.

## Thoughts on Personal Improvement
In my CLI blog post, I listed things I realized I needed to work on during my coding process. I would say I largely did a better job of remembering to commit at regular intervals. There were a few points at the beginning where I would get involved in what I was doing and would forget, but I eventually got into a good routine. I think that part of this was transitioning from the Learn IDE process where it is handling all of that for me to my local environment where I was having to remember. I was definitely better about using Pry to debug. The combination of Shotgun and Pry made it very easy to test what was going on with my code - it puts print statements to shame! I am still not commenting in my code - I need to be better about that so that other people can come in and look at what I am doing.

In looking forward to things I would like to be doing better, I would like to start trying to write Rspec tests with Capybara. Test-driven development seems core to the Ruby community - when I look at Ruby/Rails postings, it is almost always listed as a skill employers want to see. It also just seems like good practice - sometimes I will think I have tested every contingency and edge case and then I hit an unexpected error. I feel like Rspec is probably the answer there.

Learning the process for using Sinatra to get an app running on the web was fun. I’m looking forward to moving on to Rails!
