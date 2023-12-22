---
layout: post
title: ! 'RailsConf talk: Putting the BBC''s Catalogue on Rails - Matt Biddulph'
typo_id: 25
categories: railsconf
---
*Yep, that’s a BBC accent.*

-   We had to pull about seven million rows of legacy data over into our mysql database to get it rails-ready.
-   We went from the pipe delimited data file to a full-blown rails app in two months.
-   Luckily, the data model was completely redesigned in the 80’s when the data went from index cards to a library application (with a neat green screen), and the data model actually worked pretty well for the web.
-   One of the design concerns for the rails version of the catalogue was for the URL’s to be beautiful, and for each url to have a machine readable version (if there’s a page, it has an xml version)
-   One of the biggest issues (besides the sheer magnitude of data) was getting search to work well. We ended up using some of the built-in search features of mysql, which actually worked pretty well once some of the default mysql configurations were fixed.

### Getting ready for the big launch

-   We knew the site was going to get a ridiculous number of hits.
-   Deployment was hardest part - BBC locked the process down, didn’t allow access to the deployment box, didn’t allow gems, had some problems with dispatches blowing up and the mysqld process getting stopped (whoops)
-   The site did launch, and it was pretty neat. Unfortunately, the site is currently offline for the standard review process that takes place for all new BBC features.

### Q/A

Someone asked how long it took to do the initial import of the data from the legacy database to the new database. Answer: Two weeks of computer time. Cute.
