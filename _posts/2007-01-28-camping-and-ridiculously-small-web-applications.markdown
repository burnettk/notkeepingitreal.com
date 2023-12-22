---
layout: post
title: Camping and Ridiculously Small Web Applications
typo_id: 1570
categories: software experimentation
---
So I sat down to create a website today and, as one might expect someone who wanted to create a rails application to do, ran the command:

    rails deployer

I knew I didn’t need a database for this particular application, so, as one might expect someone without a strong grasp of [language](http://notkeepingitreal.com/language) to do, I googled for [words that don’t exist](http://dictionary.reference.com/search?q=databaseless): [databaseless rails application](http://www.google.com/search?&q=databaseless%20rails%20application).

The friendly people in the search results, who apparently also enjoy making up words, were busy discussing how to go about prying rails free from ActiveRecord’s evil clutches (ActiveRecord being the database layer built into rails). There was, however, a lone voice calling out, “maybe rails is overkill for your application if you don’t need a database.”

“A web application not built in rails?,” I thought, “That’s frickin’ ridiculous!”

Two hours later the job was done. The secret? [Why the lucky stiff](http://whytheluckystiff.net/) and his mini-framework, [Camping](http://code.whytheluckystiff.net/camping/). As it turns out, Camping is a neat little web framework. The best thing (I can’t believe I’m saying this) is that all of the code for the entire application can be, if you so choose, in one file. So when I went to archive away the code in [subversion](http://subversion.tigris.org/), I didn’t have to engage in witchcraft like [setting up the svn ignore property](http://svnbook.red-bean.com/en/1.1/ch07s02.html) on multiple files and directories, or pulling lots of libraries into the application by way of svn externals.

The flip side to all of this is that when I installed [the recommended gem](http://code.whytheluckystiff.net/camping/wiki/CampingOmnibus), it grabbed what seemed to be a **heck of a lot** of other gems as dependencies. Rails has moved away from this kind of server-dependent configuration by encouraging people to package all of their application’s dependencies into the application itself. But I still think it’s cool that the application is in one file. :)

So by all means, [give camping a shot](http://code.whytheluckystiff.net/camping) the next time you want to write an afternoon-sized web application.
