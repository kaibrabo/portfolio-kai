---
layout: post
title: Wiki Waki
thumbnail-path: "img/wiki_home.png"
short-description: a wikipedia project using Ruby on Rails

---

{:.center}
![]({{ site.baseurl }}/img/wiki_home.png)


## Explanation

Founded on the principle concepts of Wikipedia, I created Wiki Waki as a Ruby on Rails project.

Introducing Wiki Waki, a online encyclopedia with extra features to subscription members.  ANyone is allowed to view the content in the form of "Wikis". To create public Wikis, a user must sign up, and to create private Wikis, a user muts pay a fee.  Premium members, the users who pay a fee, will always have the option to downgrade to a standard user.

My role was to design and implement a functional encyclopedia application using Ruby on Rails.

{:.center}
![]({{ site.baseurl }}/img/wiki_login.png)

## Problem

The first task for this project was to figure which language and framework to use.  When dealing with creating posts, in this case Wikis, I had a previous project completed with Ruby on Rails.  It seemed similar in functionality and purpose.  I needed to CRUD Wikis as well as create and upgrade users.

{:.center}
![]({{ site.baseurl }}/img/wiki_index.png)

## Solution

Firstly, I built out the Wikis controller and model because every user, even guests, are able to view Wikis.  Next, I created standard users and gave them the ability to CRUD public Wikis.  Third, I gave the option to upgrade and create private Wikis.  This task also incorporated the downgrading option for users from Premium to standard.  I used Stripe to process charges, Devise for User Authentication and Pundit for User Authorization of roles.

## Results

Ruby on Rails enabled me to get a working application finished within a brief period.  This being my first full fledge application on the Rails framework, I was able to practice and solidify using RoR.

I would go on to build other Rails apps with new features and scalability.  


## Conclusion

I was underestimated the learning curve of Ruby on Rails.  This project is the second introduction to the OOP framework and RoR was relatively easy to read as the syntax was fluid.  Taking into consideration that I now know Ruby on Rails, it will be my most useful scripting language, and I will readily use on any new project.
