---
layout: post
title: ! 'RailsConf talk: Deploying Rails Applications - James Duncan Davidson'
typo_id: 33
categories: railsconf
---
“Much of what I was going to say has already been said.”

-   I’ve been presenting talks like these for ten years.
-   I did tomcat. How many people have used that? (almost everyone raises their hand)
-   When I wrote ant on an airplane, I didn’t really think it would be around for this long. It just goes to show that things need to be designed well up-front, because they just might end up hanging around even if they aren’t.
-   EJB’s came from vendors selling software that seemed like it should work. Rails was extracted from a hot application that already worked.

### Deployment

-   You can do cool things like posting to an rss feed for each of your deployments.
-   You should control the whole environment to which you are deploying.

### Deadly mines

-   Watch out for personal data in log files.
-   Think about open database sockets.
-   Guard file permissions

### Yep

-   We need to use http as a pipe. It worked for unix.
-   Mongrel is pretty hot.

