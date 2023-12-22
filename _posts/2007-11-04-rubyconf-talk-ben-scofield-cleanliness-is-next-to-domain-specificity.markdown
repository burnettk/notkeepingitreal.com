---
layout: post
title: ! 'RubyConf talk: Ben Scofield: Cleanliness Is Next to Domain Specificity'
typo_id: 1869
categories: rubyconf
---
I. Linguistics

-   We are programming languages - they can certainly be compared to natural languages
-   Regional dialects are crazy. Can I get a coke? Pop is delicious.
-   Jargons and cants differ not in grammar but in vocabulary. [Hmmm](/blog/2006/04/22/language).
-   Creoles and pigeons differ in both grammar and vocabulary from their parent languages
-   Getting back to ruby, are domain specific languages (DSLs) really languages? Or are they dialects, or something else?
-   DSLs are really just about changing the words we use
-   Linguistic determinism is crap
-   The eskimos do not have 33 billion words for snow. For one, “the eskimos” is not one group of people with one language. Additionally, there may be lots of **snow-related** words in any given native alaskan language; however, there are lots of **snow-related** words in English as well.
-   Tests are testing something that is **already there**. Specifications come **before** something else - this leads you in the right - or at least the test first - direction

​II. Refactoring

-   He showed a bit of shit code to get flight information from [kayak](http://kayak.com) and refactored it into a class with a more readable API
-   Use symbols instead of strings to avoid using quotes everywhere
-   Avoid parens when that makes things more readable
-   We will never model the domain exactly, so there is always room for improvement

Cool talk!
