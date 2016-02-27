---
title: "Authentication and Authorization"
slug: authentication-and-authorization
---

## Replacing our User with Devise

We’re going to use Devise, an authentication gem, to allow signing in, signing out, recovery of password via email, and other common User actions.

*Q: What’s the difference between authentication and authorization?*

**Task: Read the "Getting Started" guide for Devise: ****[https://github.com/plataformatec/devise#getting-starte**d](https://github.com/plataformatec/devise#getting-started)

**Task: Generate a Devise user named User.**

**Task: Generate Devise views for your project.**

**Task: After running the migrations and completing the getting started guide, create a user in your app.**

Tip: rake routes will return a list of all of the routes your app currently responds to. Use this to check that the routes you create are what you expect them to be.

Pay close attention to the names of Devise methods.  It’s very common for Rails apps to implement helper methods like `#current_user`, even if they aren’t using Devise.  Common conventions like this are referred to as "Best Practices", and should be followed whenever possible unless you have a really good reason not to.  The benefit is that, as a Rails engineer, you can join nearly any project and expect `#current_user `to exist and behave normally.

While figuring out what your authentication looks like, this would be a good time to add  some high level tests that walk through signing a user in and checking that the user is signed in when you expect them to be.

### CanCanCan

Many applications require different ability levels between users, like an admin or a moderator.  The patterns that describe the implementation of user levels are referred to as authorization.  Because so many Rails apps implement these patterns, gems have been created and actively maintained that implement authorization quickly with a common DSL.  We’ll be using the CanCanCan (a fork of the no longer maintained CanCan) gem to implement authorization on top of the authenticated Users that Devise created for us.

**Task: as a quick introduction to the Can* DSL, digest this RailsCast:**

**[http://railscasts.com/episodes/192-authorization-with-canca**n](http://railscasts.com/episodes/192-authorization-with-cancan?autoplay=true)

**Task: follow the getting started guide and implement the base gem in your project: ****[https://github.com/CanCanCommunity/cancancan#readm**e](https://github.com/CanCanCommunity/cancancan#readme)

*Q: How are Roles related to Abilities?*

**Task: Allow Users to edit and delete their own Posts, but not the Posts of others.  Follow TDD!**

### Moderators

Subreddits are owned by the Users that create them, known as moderators.  A moderator can add more moderators by enlisting other subscribed users help them in moderating Subreddits.  Currently, our application has a single owner per Subreddit, but we’d like to allow many moderators per subreddit.

*Q: How does Rails implement many-to-many relationships?  How is this different than polymorphism?*

We need to create a join table that allows us to give many users many moderator roles.  Make sure to follow TDD!

RailsTutorial example: [https://www.railstutorial.org/book/following_users#sec-following](https://www.railstutorial.org/book/following_users#sec-following)

**Task: Following the example set forth by the RailsTutorial, allow multiple users to moderate multiple Subreddits.**

**Task: Allow the creating User (hint: Admin, a new role) of a subreddit to add and remove moderators.**

**Task: Add roles and abilities with CanCanCan so that Users are only allowed to edit and remove posts ****their own Posts.**

**Task: Allow moderators of a subreddit to add more moderators.**

### OAuth

Devise offers many configuration and extension options out of the box (check out the list here: [https://github.com/plataformatec/devise/wiki/Extensions](https://github.com/plataformatec/devise/wiki/Extensions)).   Many websites offer the ability for a user to login using their Facebook, Twitter, Google, or LinkedIn accounts, depending on the offering.  Let’s add Facebook authentication to our application.

OAuth is a protocol that allows a third-party service to authenticate users against an **authenticating service**, and is the protocol used across the web by sites that wish to allow Users to login with, say, a Facebook account.  Many providers offer OAuth: [https://en.wikipedia.org/wiki/List_of_OAuth_providers](https://en.wikipedia.org/wiki/List_of_OAuth_providers), including Reddit!  We’ll use the Omniauth extension for Devise to allow users to login with Facebook.  First, let’s understand how OAuth works:

**Task: Complete the OAuth tutorial: **[https://www.codecademy.com/courses/ruby-beginner-en-ifzi3/0/1?curriculum_id=5122e6618faaada4d20007ed](https://www.codecademy.com/courses/ruby-beginner-en-ifzi3/0/1?curriculum_id=5122e6618faaada4d20007ed)

*Q: What is Omniauth?*

*Q: What is an access token?  What is it used for?*

**Task: draw the steps necessary to authenticate using the OAuth protocol.**

**Task: Implement Facebook login using the Omniauth (OAuth2) gem: **[https://github.com/plataformatec/devise/wiki/OmniAuth:-Overview](https://github.com/plataformatec/devise/wiki/OmniAuth:-Overview)

