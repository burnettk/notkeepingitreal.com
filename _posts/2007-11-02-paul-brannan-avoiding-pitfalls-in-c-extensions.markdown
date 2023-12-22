---
layout: post
title: ! 'RubyConf talk: Paul Brannan: Avoiding Pitfalls in C Extensions'
typo_id: 1857
categories: rubyconf
---
What’s a strategy for playing [werewolf](http://en.wikipedia.org/wiki/Mafia_%28game%29?) Paying attention to the details of what is going on. This is a also a good strategy for writing C extensions to ruby - maybe you’re pair programming and maybe you’re not, but if you have a bug, your code will likely crash hard; pay attention!

Don’t be afraid to write a ruby extension, but there are definitely things that you should be aware of before you start:

-   you will often have two objects that are representing the same thing, but one is the C object and one is the ruby object - do not give these variables the same name! Use a naming convention that differentiates them
-   ranges for your data types are important during conversions!
-   allocate resources and deallocate resources in the same place if possible!
-   do not destroy an object that does not belong to you!
-   check function return values!
-   make sure you use rb\_ensure!
-   executing arbitrary code and using tainted data are potential security concerns!
-   unit testing is hard, as many C libraries were not built with unit testing in mind, but functional tests that execute your extension code are quite necessary!
-   convert C*+ exceptions to ruby exceptions at C*+/Ruby boundaries and vice versa!
-   use the Pstore database if you need a database - it’s simple!
-   implement to\_s and inspect for any custom classes! they’re useful!
-   use virtual destructors when doing inheritance!
-   there are tools to help - Rice, etc!
-   damn straight!

