---
title: "Comments"
slug: comments
---
# Polymorphism and Duck-typing

Since comments can be related to Posts and other Comments, we’ll begin by reviewing Rail’s implementation of polymorphic relationships and duck typing.

**Task: review polymorphism in Rails:** [https://www.railstutorial.org/book/following_users](https://www.railstutorial.org/book/following_users#sec-the_relationship_model)

**Task: review duck-typing:** [http://rubylearning.com/satishtalim/duck_typing.html](http://rubylearning.com/satishtalim/duck_typing.html)

*Q: Compare and contrast duck-typing and class inheritance.*

**Task: Make comments invalid without a polymorphic owner.**

# Validations and Database Constraints

While Rails validations make it easy to ensure that a Comment is not valid without a parent, there are other common ways to enforce these validations much more performantly.  For example, database-level constraints are common in financial or big-data applications where the application is the bottleneck of many computations.

**Task: Review the PostgreSQL implementation of database constrations:** [http://www.postgresql.org/docs/8.2/static/ddl-constraints.html](http://www.postgresql.org/docs/8.2/static/ddl-constraints.html)

*Q: What are some reasons that ActiveRecord validations are preferred over database constraints in Rails?
Q: Considering your answer to the previous question, what are some types of data that would be good to validate in a Rails application using database constraints?*

# Updating the Comments Controller

**Task: Do not allow comments to be deleted, only to be nilled out by removing the author and content.**

*Q: Given the context of Reddit, why would we want to nullify posts instead of deleting them?*

**Task: when a comment is created, the user should be redirected to the owning object, not CommentsController#show.**

# Integrate partials for Comments

Capybara is a commonly used integrational testing library for Ruby.  Using Capybara, we can write tests that simulate actual user interaction with our application, like logging in or clicking post links.

**Task: Read a getting started guide for Capybara:** [http://www.sitepoint.com/basics-capybara-improving-tests/](http://www.sitepoint.com/basics-capybara-improving-tests/)

**Task: Read the Capybara documentation:** [http://www.rubydoc.info/github/jnicklas/capybara](http://www.rubydoc.info/github/jnicklas/capybara)

**Task: Implement the following acceptance tests using Capybara while implementing Comments:**

* User signs up and creates a post.

* User logs in and comments on a post.

* User creates a comment then deletes the comment.

* User logs in and comments on a Comment.

