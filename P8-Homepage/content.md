---
title: "The Homepage"
slug: homepage
---
# The Front Page

The front page of reddit is composed of the posts from all of the subreddits that you are subscribed to. To begin with, let’s just have the front page show the most popular posts from each subreddit.

**Task: Add a FrontPageController with a single action, `#index`.**

**Task: Ensure that when no user is signed in, the homepage displays the highest voted posts from all subreddits.**

**Task: Give users the ability to subscribe to a subreddit.  Only subscribed subreddits should show on the front page when the User is logged in.**

# Pagination

We need to paginate our posts so that we can show multiple pages of content.  Kaminari is a commonly used gem for pagination.  Another is will_paginate.

[https://github.com/amatsuda/kaminari](https://github.com/amatsuda/kaminari)

[https://github.com/mislav/will_paginate](https://github.com/mislav/will_paginate)

**Task: Use either Kaminari or will_paginate to paginate the front page and subreddits.**

# Ranking

Let’s look at how reddit ranks posts. There are 3 main ways.

* Most recent

* Most popular

* Trending (Sum votes over time *t*)

Recent posts are sorted from newest to oldest and the most popular posts have the most votes of all time.  We should allow the user to sort the posts of any given subreddit by newest to oldest and by number of votes.

**Task: Allow the user to sort the page by most recent, most popular, and trending.**

# Trending

Trending posts may need more explanation. What exactly constitutes a trending post? Trending posts are posts that receive a lot of votes over a short period of time. The longer a post has been around, the less a vote is worth. Now, how much less is a vote worth after one hour than it is worth right after posting? There are a number of answers. There is an excellent article exploring different ways of deciding how much a vote is worth over a period of time.

[https://medium.com/hacking-and-gonzo/how-reddit-ranking-algorithms-work-ef111e33d0d9#.eo55kdyw5](https://medium.com/hacking-and-gonzo/how-reddit-ranking-algorithms-work-ef111e33d0d9#.eo55kdyw5) 

**Task: Implement any ranking algorithm to sort Posts by votes over time. Bonus points if it’s fast.**

# Load

Take the sorting algorithm you just wrote, and try it with 100 posts, then 1000 posts, then 10,000 with the Rails console. How is is performing?

*Q: What’s the Big O of your sorting algorithm?  Check with an instructor to make sure you're correct.*

**Task: Add 100,000 Posts to your database under any subreddit.**

**Task: Add logging around the front page index action to time the page load. **

**Task: Graph the load time over number of posts from the previous task.  Explain the pattern and describe the line of best fit.**

**Task: Improve the sorting speed at higher scale.**

