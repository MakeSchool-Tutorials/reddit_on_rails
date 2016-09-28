---
title: "Subreddits"
slug: subreddits
---

# Adding some features

We created the Subreddit object in the last section.  Next, we need to write the user stories, and implement the tests and logic for the object.

Some stories to start with are:

* *As a user, I can post content to a subreddit.*

* *As a user, I can edit posts I’ve added to a subreddit.*

* *As a user, I can delete posts I’ve added to a subreddit.*

**Task: Add additional user stories around subreddits.  Run these by your teammates, and then write test cases that will fulfill your feature set. Make your tests green by building out the stories you agreed to add.**

# Validations

We're going to need to validate a few things on our subreddits.  We should review Rails validations here on this page: [http://guides.rubyonrails.org/active_record_validations.html](http://guides.rubyonrails.org/active_record_validations.html)

**Task: Ensure that every subreddit is named with a maximum_length of 21 characters, and doesn’t contain any special characters.**

**Task: Ensure that subreddit names are unique.**

# Slugs

Slugging is the practice of routing based on something other than the primary key. An example of a slug on Reddit would be r/funny rather than r/<primary-key>.

## Routing

Now that we’ve added and validated our slugs, we need to add routes so we can use them.  The first step that we'll do is add our route in the routes.rb. If you look over what we have now we'll see that it's mostly resources. We'll be adding our own matcher. You can read more about routing here: [http://guides.rubyonrails.org/routing.html](http://guides.rubyonrails.org/routing.html).

Next, let's add a route that matches localhost:3000/subreddits/<slug> and send that to Subreddits#show controller action.  If the slug is presented, use it to look up the correct subreddit.  If not, defer to the primary key of the Subreddit.

**Task: Write a user story that captures slugs.**

**Task: Add a slug field to Subreddit, following TDD.**

**Task: Validate the slug to prevent whitespace, slashes, ensure uniqueness, and prevent other special characters.**

# Improving performance

One of the downsides of using a slug is that it’s slower than looking up an object by its primary key. In most modern databases, the primary key is automatically indexed. Most of the time, it won’t matter unless your table is really big. See explanation [here](http://stackoverflow.com/questions/12431107/performance-of-string-comparison-vs-int-join-in-sql).

We’re going to add an index. If you don't know about indexes already, the database uses them to  allows us to quickly search a field. An index adds an additional cost of maintaining the index whenever you create, delete or modify an entry, so indexes should be used sparingly. A good rule of thumb is add indexes on things that you will write queries for, and never on text fields.

**Task: read more about indexes here:** [https://www.dreamhost.com/blog/2013/08/27/mysql-indexing-basics/](https://www.dreamhost.com/blog/2013/08/27/mysql-indexing-basics/)

*Q: How does an index make accessing a database table faster?*

*Q: What kind of lookup would not benefit from an index?*

## Production Considerations

If you tried to add an index to a table that already had data, the database may not allow it. Indexes can't be created for entries on columns that have empty rows, for example a Subreddit without a slug.  In these cases, we would need to backfill the data before adding the index.  We'll run into this situation many times in production code, sometimes we want to add something new but provide some kind of default code that populates something.

Let's modify our migration file to include some code that goes through all the subreddits and verifies that slugs are present. This code should run before the index is created by the migration.  Because of our after create callback we won't have to worry about future models, just our existing ones.

**Task: using the Rails migration generator, add an index for the slug column on Subreddit.**

# Testing

Always start development with plan and a test.  Here are some cases you’ll want to make sure you’ve caught:

1. The app throws an error when creating any subreddit with illegal characters.

2. The app throws an error when creating a subreddit with the duplicate name.

3. The app automatically fills in the slug field after both a create and an update.

4. The app should route correctly if there is a subreddit with the proper name,

5. The app should throw a 404 if there is no subreddit with that name.

