---
layout: post
title: ! 'RubyConf talk: David Chelimsky, Dave Astels: Behaviour Driven Development
  with RSpec'
typo_id: 1865
categories: rubyconf
---
Astels from google (et al). Chelimsky from Articulate Man (et al).

Tests are nice. Tests should focus on design and documentation. Behavior driven development (BDD) emphasizes design, documentation, and, of course, behavior.

They demonstrated some ping-pong pairing, with one guy writing a failing test, and then the other guy writing the simplest implementation to make the test pass, writing a new test, and passing it off to the first guy.

They gave the background/history of rspec. Hmmm.

There are three or so ways to write these rspec tests, up to an including writing english abstracts and test cases designed to be read and even added to by non-developers.

Features:

-   Clear reporting
-   Built-in mocking, but you can also use the other hot mocking libraries that the cool kids are using
-   Integration with autotest/heckle

There is a reasonably thriving community, and looks to be a good time. It certainly isn’t for everyone - ruby test unit may be all you need. [And screw this, enough hype, I’m gem installing ZenTest]
