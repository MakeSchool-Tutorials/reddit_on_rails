---
title: "Modeling"
slug: modeling
---

Tips:

* Google the answers to quiz items if you’re not sure what the answer is.

* Remember to TDD!  Simplecov should report at least 90% coverage!

# User Stories

Let’s consider Reddit’s basic use cases. We can express the functionality we're building using statements called *user stories* in which we detail the who and the what (and sometimes why) for each feature.  User stories generally follow this format:

 As a <role>, I want <feature> so that <reason>.

Here are some example Reddit user stories:

* As a user, I want to be able to change my password.

* As a user, I want to be able to comment on posts.

Next, we need to figure out how to represent these stories in our models. 

**Task: Create at least five more user stories.**

## Entity-Relationship-Diagrams

**ERDs **([https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model))** **are a common way to represent the objects and relationships represented by a relational database. In the example below you can see that each rectangle represents a table (a Rails **Model**), each model has many attributes, and the arrows between objects represent primary/foreign-key joins (ActiveRecord **Relationships**).  Generally, our **nouns** will be our models. The relationships between the objects will be **verbs of possession**.  For example, a **Post** will have many **Comments**, indicating a one-to-many relationship between the two objects.

**Task: Read the article linked and ensure you understand the various styles in ERDs.**

*Q: What sort of relationship does the curled arrow on Comment represent?*

**Task: redraw the provided ERD using another style.**

Given the ERD, we can see the models, their relationships to one another, and some of their attributes (not diagrammed are the primary and foreign keys).

*Q: Based on the connections between models, which type of relationships does each model have with its peers?*

*Q: Describe the cardinality of each relationship shown in the ERD.*

Another subtlety should be noted here: both **post** and **comment** persist their data in a field called **content**.  **Normalization of parameter names** is an important part of application design.  First and foremost, it allows a style guide to develop organically for the application, and it allows us to more easily construct interfaces, shims, and duck-types later in the applications life.

To get started, let’s use the Rails generators covered in the Rails tutorial to construct the models described in the ERD presented earlier in this lesson.  Draft the commands in a text editor first, and then compare them to the commands provided in the solutions section below.

**Task: generate models according the ERD.**

*Q: Why does the order of model generation matter? Does the order of columns matter?*

## Testing and Validations

Now that we’ve generated most of our base models, we need to add validations before starting to connect them with one another. Every attribute on a model should have a test, and every validation for every attribute should have a test. Since we’re not hacks, we’ll write our tests first.  For now, only give the User an email address -- we’ll implement User later.

**Task: Using TDD, check that the correct attributes exist on the models you generated.**

**Task: Brainstorm validations necessary for each model, then add them using TDD**.

### First Relationships

The ERD gives us a good idea of how objects are related, so we’ll follow that for this exercise.

**Task: Using the ERD and your knowledge of Rails ActiveRecord Relations, add the appropriate relationships to the models you generated.  Make sure to follow TDD!**

