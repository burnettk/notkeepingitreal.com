---
layout: post
title: ! 'RailsConf talk: Rails Acceptance Testing with Open Source Tools - Dave Hoover'
typo_id: 31
categories: railsconf
---
**Update:** After wondering for a while why my stupid notes from railsconf were getting top results for google searches on “Selenium”, i realized that I had mispelled Selenium (yeah, some other folks apparently thought there was another “i” in there as well). Whew, lucky I spotted that - now notkeepingitreal.com can get back to its relative anonymity.

Now, back to your regularly scheduled post:

Acceptance testing seems to be all about verifying that you can manipulate the interface to provoke the expected behavior from your application.

### Watir

-   Browser specific acceptance testing utility
-   Uses push mentality
-   Has IE and firefox browser compatibility, Firewater - nice name

### Selenium

-   Works across pretty much all browsers
-   Uses pull mentality

### Sahi

-   Smaller acceptance test utility
-   Tests are written in a variant of javascript. You start up a java virtual machine and hit the page in a browser through a proxy.

### Things we want in an acceptance test utility

-   Watir-like API
-   Compatibility of Selinium
-   ActiveRecord integration

Thoughtworks has been working with Selinium and is in fact actively developing and hacking on Selinium to try to make it work better for their situation and for the community at large. *Awesome, our quality assurance folks will appreciate.*
