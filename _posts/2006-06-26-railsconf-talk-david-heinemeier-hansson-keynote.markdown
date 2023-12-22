---
layout: post
title: ! 'RailsConf talk: David Heinemeier Hansson Keynote'
typo_id: 30
categories: railsconf
---
-   Dave Thomas’ **suggestions** were good, but not necessarily the **tone** of his message.
-   Sometimes people say that we should be operating more in the “real world”. But I’m pretty confident **not** living in the real world. That way we’re not subjected to the same constraints that people in the real world experience.
-   Rails has been doing quite well recently
-   “But this talk is not really about gloating, it’s about CRUD.”
-   Not only does CRUD have a bad name, it also has a bad reputation.
-   Recently, there has been a bit of a renaissance in the http space - POST and GET are not good enough any more! We need the PUT and DELETE verbs as well.
-   So now we’ve got for\_form(:person, :method =\> ‘put’) to do the update, and the URL looks like /person/1 (look ma, no /update!)
-   “Decisions are bad” - with conventions, we don’t need to waste valuable brain cycles on the silly stuff. Constraints are liberating.
-   has\_many :though has given us the ability to **give a name** to an abstract thing that used to be just a cross table between a many to many relationship.
-   Model beyond “things.” We can have models and controllers for things we can’t touch, like subscriptions and memberships.

*Man, there’s something really eerie about this guy wanting us to do everything his way*

-   If you’re building a new rails app and you want to use composite primary keys, **you’re insane**.
-   We’ve been so successful because we **have** been so opinionated.
-   But additionally, although rails will have many opinions, it is still possible to do things your way. It’s like ruby, where you can go right ahead and call private methods using .send(:some\_method) if you know what you’re doing.
-   URL extensions are great? Sure! index.php isn’t great, because it exposes your implementation details for no reason. But index.rss now that’s hot.
-   ActiveResource is not done yet and he’s been working on it for two days. Seems like a long time.
-   “As I’ve been messing around with these new verbs and this ActiveResource stuff, I’ve found that it’s just so easy; it’s not painful, it’s not like soap.”

*Good talk dude. Over at [his blog](http://loudthinking.com), you’ll find plenty more where that came from.*
