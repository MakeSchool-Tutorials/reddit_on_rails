---
title: "Voting"
slug: Voting
---

# Voting

Reddit is centered around voting.  A user can vote up or down on a specific submission or comment.  

**Task: Create user stories for voting.**

# Vote - Models

Votes need to have 3 fields. A reference to the User, an integer (1 to represent an upvote, -1 to represent a downvote) determining if they’re an upvote or downvote, and a relationship to either a post or a comment. Let's create a polymorphic relationship where vote belong to a "votable" object which can be either a post or a comment.

**Task: Using TDD, create a Vote object with a polymorphic owner.**

We also want to limit it so that there is only one vote per votable object for each user. We can add uniqueness constraints using validate_uniqueness_of but how do we ensure that it will work for a vote from each user? For that we can learn about :scope in a validation, this allows us to specify a uniqueness constraint given another field's unique constraint. 

Read more about validations with scopes here: [http://guides.rubyonrails.org/active_record_validations.html](http://guides.rubyonrails.org/active_record_validations.html) 

**Task: Add a test to ensure that a Post cannot be voted on by the same user twice.**

**Task: Add a uniqueness constraint that prevents voting twice.**

# Voting and Views

When you vote on something in Reddit you increase its score. If you downvote you can move score into negative values. The score of any submission or comment is the total # of upvotes - the total # of downvotes. We want to create a method on our submission model to help us calculate this so that we can keep our code DRY. Let's create that method and use it in our view to display the karma of any post. We'll only do it for submissions for now. 

**Task: Use ActiveRecord to calculate the number of votes for a post by subtracting the number of downvotes from the number of upvotes.**

Tip: now you might be realizing why we used an integer to represent upvotes and downvotes. You can use SQL’s SUM operation to get the current upvotes - downvotes.

**Optional: Use SQL’s SUM to calculate a Comment or Posts score.**

# Adding Voting

We have all this voting code but a user can't vote yet! We need to create our voting buttons and hook them up. Let's only add voting to posts and comments first to make things less complicated.

Rails allows us to do asynchronous updates to the model. You have already learned about link_to and path_helpers in the Rails Tutorial.

**Task: Review** [http://guides.rubyonrails.org/routing.html#singular-resources.](http://guides.rubyonrails.org/routing.html#singular-resources.)

**Task: Review** [http://guides.rubyonrails.org/routing.html#controller-namespaces-and-routin](http://guides.rubyonrails.org/routing.html#controller-namespaces-and-routing)[g](http://guides.rubyonrails.org/routing.html#controller-namespaces-and-routing) 

But if we specify that this is a remote link_to, it will retrieve POST without redirecting.  

**Task: Review** [http://guides.rubyonrails.org/working_with_javascript_in_rails.html#link-to](http://guides.rubyonrails.org/working_with_javascript_in_rails.html#link-to). 

**Task: Create a remote link that allows you to upvote or downvote a submission.**

# Updating the Vote

Posts that have already been voted on should show a colored arrow. We can use view helpers to determine which css class to put on our link_to to style it differently.

**Task: Create a helper method that will return the class 'upvoted' for upvoted buttons if they have that votable item has an upvote. Make another method that does the same for a downvote but returns a class 'downvoted'.**

**Task: add some rules to our css file to modify the our css so that things with 'upvoted' and**** 'downvoted' class are a different color to indicate that a user has upvoted or downvoted this.**

**Extra credit: Use javascript to apply the css to the post without having to refresh the page.**

