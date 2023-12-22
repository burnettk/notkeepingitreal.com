---
layout: post
title: ! 'RubyConf talk: Jim Weirich: Advanced Ruby Class Design'
typo_id: 1853
categories: rubyconf
---
Most of Jim’s talk was spent chilling out with my workmate Jeffmo in the car on the way to Charlotte, North Carolina. Jeffmo apparently lost all the contents of his wallet on one occasion, including \$2000, only to have it turn up six months later (with all of its contents).

Jim was discussing how one might go about implementing a pure-ruby SQL abstraction. A node for a table, a node for a column, a node for an operator, and a node to represent your mother as well. The code examples were neat, but at the end of the day, his basic conclusion was that it’s impossible because, among other things, you can’t override || and && in ruby.

He offered encouragement to experiment with out-of-the-box solutions for problems, even though a standard approach suffices in most situations - made me think of [gabe](http://gironda.org).
