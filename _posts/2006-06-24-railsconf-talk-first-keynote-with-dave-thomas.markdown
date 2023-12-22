---
layout: post
title: ! 'RailsConf talk: First Keynote With Dave Thomas'
typo_id: 15
categories: railsconf
---
*Dave Thomas is the hot pragmatic programming guy apparently. His points follow:*

Good news everybody!\
\* People are using rails to actually do business!\
\* The trendline for rails is going in the right direction\
\* Matz in the man\
\* Core is the man (or something)

But There are still things to do. Unsolved problems according to Dave:

### Data Integration

-   It would be neat if validations were added to models automatically from the schema
-   Foreign key support should be better *\_\
    \* Primary keys are always integers? Is that cool?\
    \* Can we have composite primary keys please\
    \* Can we get better support for non-database-backed models
    \
    h3. Real World Crud
    \
    Scaffolding brings people to rails. Why not improve it a bit? Rails is supposed to be the poster child of rails 2.0, but the current scaffolding is the worst of web 1.0.\
    \* Make it configurable \
    \* Show off - use Ajax\
    \* Allow skinning.
    \
    h3. Deployment
    \
    “Who has deployed a rails app,” he asks. “Who enjoyed it?” \
    \* Capistrano is the best thing out there; let’s make it better.\
    \* In the real world, developers often cannot just push code out to production when they please; developers know what to deploy, and sysadmins know where, how, and when to deploy.\
    \* So how about if we had: \<pre\>cap —deploy-on [http://someserver.com](http://someserver.com)\</pre\>
    \
    So suggesting these kinds of things for inclusion in rails core raises the question, why? Well, people use rails because it makes their lives easier. The rails community places a high premium on writing code that others can use. If we can help to lower the bar in terms of barrier to entry for rails, we can make other peoples’ lives easier. “All developers deserve to be happy.”
    \
    *Good talk man - solid beginning for Railsconf.\_

