---
layout: post
title:      "Most Anticipated Books - A CLI Gem"
date:       2018-02-17 17:09:34 +0000
permalink:  most_anticipated_books_-_a_cli_gem
---


The specifications for the first portfolio project for Flatiron's Online Web Developer program are to create a command line application that scrapes data from a website and allows the user to interact with it.  I learned so much creating this program - the Github repository for it can be found [here](https://github.com/rhiannoncs/most-anticipated-books-cli-gem).

### The Planning Process

As I came up with potential projects, I used Chrome developer tools to inspect sites I was thinking about scraping, to see if the data I would want for a project would be somewhat easily accessible. Sites that hid information in JavaScript files or seemed otherwise difficult were rejected.

I wanted to create an app that would add something in the execution, not just display information that could easily be found just by looking through a single website. I settled on using one of my favorite annual book lists - [The Millions' Most Anticipated Books Preview](https://themillions.com/2018/01/most-anticipated-the-great-2018-book-preview.html). 

The Millions lists the books' titles, authors and translators, and gives a brief description and an Amazon link. I decided to create something value-added by combining the information from the Millions with information about each book that could be found on Amazon, like publication date, ISBN, publisher and genres. I wanted to create an app in which the user could explore the list in multiple ways, using that information.

I wrote notes on what I wanted the CLI to do and what other objects I would require - Book, Author, Genre and Translator - including their attributes and methods. I also sketched out the bare bones of what I would want the scraper to gather from the sites.

### Coding

I used Bundler to get my basic gem setup in place and created my Github repository. It was great practice to have to figure out how to get my file structures and dependencies set up - this was really frustrating in places, but I learned a lot.

I first wrote the basic CLI, putting in `puts` statements as placeholders for where my methods would eventually go.

Next, I tackled the scraper. This was easily the most challenging part. Through the process of using Nokogiri to scrape data I learned that The Millions was not very consistent in how they created the page I was scraping. Sometimes the titles used `em` and sometimes they used `i`, sometimes the anchor tags were nested inside the text formatting and sometimes it was the other way around. I learned a lot about scraping and Regex through this process, as well as working on the Amazon scraper, which was just as complicated.

My Book, Author, Translator and Genre objects came next. This process was fairly straightforward - the curriculum had prepared me well for how to organize objects and get them to interact with one another. I created the methods I thought I would need for the CLI, though I eventually ended up rewriting most of them as the CLI finalized.

As I returned to the CLI, its structure began to take shape. I initially had it set up as basically one linear method that called on methods from `Book` and `Genre`, but as I played with it I realized that in order for the user to be able to return to the menu and traverse all of the options the way I wanted, breaking the code up into multiple methods worked better. I focused a lot on user input validation in creating the CLI to try to keep invalid input from breaking it.

Up to this point, I had been testing the CLI with a few manually created `Book` objects. Once I started testing with the scraper pulling in all of the data I started getting 504 errors from the Amazon servers. Research led me to putting a user agent into my scraper, which fixed the issue.

### Refactoring & Gem Creation

After getting my program to work, I went through to clean it up. I identified some spots in my scraper with repetition and separated that out into another method.  In using my program I realized that while I had written my `list_by_genre` and `list_by_author` methods to require the user to type out the genres and author names, it would be more user-friendly to rewrite these to use numbered lists to reduce typing and the need for correct spelling.

Next I consulted the Bundler documentation to learn how to make my files into a gem, and was finished.

### Thoughts on Personal Improvement

Making this program from scratch was a great experience - I couldn't even list all of the things I learned. I have been making a list for myself of things I know I need to work on for the future.

* Performance: Getting the data loaded in from the scraper at the beginning of the program is slow, as it scrapes each individual Amazon page. I feel there must be a way to speed up this process; I need to research this for future projects.
* Using Rspec, Pry and other testing tools: Throughout the process I was falling back on the process I have always used - testing my code incrementally, and using lots of print / `puts` statements. I know that writing my tests using Rspec and debugging using Pry would be faster, I just need to make myself learn it and form new habits.
* Commit more often: I was getting better at this as I neared the end of the project, but I am definitely prone to getting involved in what I am doing and forgetting to commit as often as I should.
* Comments: I realize I have none! I know what my program does and how it does it, but it would be more difficult than is necessary if someone else came in and tried to work on it. This is definitely a habit I need to be building.

I am really eager for my evaluation so that I can learn more about how I could be improving my process and code!
