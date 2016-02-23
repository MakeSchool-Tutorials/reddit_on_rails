---
title: "Building Reddit"
slug: building-reddit
---

# Introduction

We are using [Ruby on Rails](http://rubyonrails.org/) to build a Reddit clone so we can focus on learning how to build a well-architected, stable and scalable web application. This project is presented in a similar fashion as a project spec might be provided to an engineer by an architect.  We’ll focus on a TDD approach to creating an application by writing our failing tests before writing the code to correct them.  We’ll use gems accepted by the open-source community to learn the correct nomenclature for common programming patterns, and will require you to understand the documentation for these tools prior to implementing them.  We’ll focus on following community-accepted best-practices.

By the end of this tutorial, you will have accomplished the following:

1. Follow TDD to develop a robust and stable web application.

2. Learn how responsibility is divided between parts of a Rails application.

3. Understand the common libraries and the nomenclatures used in web applications.

## Pair Programming

You should do this tutorial in pairs using pair programming techniques.  That means that when you're programming, there's two people sitting on one computer.  One person is the driver, types on the keyboard.  The other person, the observer, reads each line of code as it's typed, and discusses what's happening and why with the driver.  You should switch roles often - every 30 minutes.

For more information, see [this guide](http://www.wikihow.com/Pair-Program).

Once you've picked a partner, use [this link](https://classroom.github.com/group-assignment-invitations/7a656a92e5e6bbe3329533de3af9360f) to accept the assignment and create groups.  Both partners should accept the assignment, though you'll start by working on one computer.  Make sure to put any design documents and any related resources into your repository.

## Why / What is Reddit?

Reddit is a simple web application that we’ll use to cover many of the concepts that would be required during development of a production-ready application.  Hopefully some of you have heard of or used Reddit before, but if not, you can read about it on [wikipedia](https://en.wikipedia.org/wiki/Reddit).  Users can create and comment on posts, and comment on comments.  We recommend creating a Reddit account, creating a subreddit, creating a post, and commenting on another user’s post.  

**Optional: Create a Reddit account**

**Optional: Create a subreddit (topic doesn’t matter)**

**Optional: Create a post in your subreddit**

**Optional: Add another student as a moderator to your subreddit**

**Optional: Comment on the post you created for your subreddit**

**Optional: Attempt to edit and delete a post in your subreddit from another user.**

# Notes on this Tutorial

Be sure to follow TDD and use the tools we’ll introduce in the next lesson to ensure adequate coverage.  Don’t be afraid to ask for guidance, and don’t be discouraged if you’re asked to reimplement aspects of your application due to inadequate testing or suboptimal implementation.  This project is a good candidate for pair programming.

**Optional: watch an expose of live, hilarious pairing here: **[https://www.youtube.com/watch?v=sn7prRGGp4**Q](https://www.youtube.com/watch?v=sn7prRGGp4Q)

# Learning through doing

Throughout this tutorial you will be learning how to build a project from the ground up in the same way you might build a project in a professional environment. You will be expected to digest documentation and apply it to your project without step-by-step direction from an instructor or the tutorial. 

An important part of performing well on a team is understanding the best practices and style guides implemented by the team.  An excellent place to start is here: [https://github.com/styleguide/ruby](https://github.com/styleguide/ruby). This style guide is widely accepted by the Ruby FOSS (free open source software) community.

**Task: Read and reference the Ruby style guide for all code written for this project.**

All of your work should follow strict Test Driven Development (TDD) as covered in the Hartl tutorial, and you should be regularly reviewing and critiquing your partner’s work. Be sure to apply the patterns and styles you have learned thus far in the rails curriculum.  Instead of being guided through the steps necessary to build a feature, you’ll be directed at the community-accepted documentation to absorb, understand, and implement.  You’ll be using the SimpleCov gem to help ensure adequate test coverage.

Approach this project as if you were delivering it to real customers.  We’ll craft user stories (a style of describing a feature ask), and spend time reflecting on our application from the perspective of our users.

# Why Reddit?

Reddit presents several interesting problems for us to solve together. There are complex database relations between users, their posts, and the subreddits those posts belong to. This tutorial will focus primarily on getting you from rails new to Reddit, but feel free to talk to your instructor about extending the application in other directions. 

## Supplemental Materials

Ruby is a very pragmatic language, and design standards have been constructed on the shoulders of giants. Digesting these resources will both greatly improve your Ruby prowess in addition to providing a much better understanding of how software is architected and maintained.  All of these resources provide best-practices that are applicable to most object-oriented languages and open source codebases.

**Optional: Digest the following canonical Ruby resources**

* [Community Ruby style guide](https://github.com/styleguide/ruby)

* [The Pragmatic Programmer](https://pragprog.com/the-pragmatic-programmer/extracts/tips)

* [Practical Object Oriented design in Ruby](http://www.poodr.com/)

