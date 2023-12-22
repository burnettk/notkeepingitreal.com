---
layout: post
title: ! 'RubyConf talk: Evan Phoenix: Rubinius 1.0'
typo_id: 1860
categories: rubyconf
---
I like to run my talks like Roller Derby: fast, enjoyable, hard-hitting and the metaphor breaks down.

Our goal is to TAKE OVER THE WORLD for ruby.

Ruby itself, and the various implementations of ruby in other runtimes (see past two posts), have lots of lines of C, Java, and .NET, but almost **no lines of ruby**. Rubinius is working to make the C lines of code/Ruby lines of code ratio smaller and smaller. Rubinius is **ruby for ruby programmers**.

As far as performance, [rubinius](http://rubini.us) is faster than ruby 1.8 in 24 of 31 yarv tests.

The community is awesome - thanks. If you submit one patch, you get commit access, and we’ve never revoked anyone’s commit access!

We’re eventually looking to make a squeek-like dialect that would allow us to generate the core C code. This would allow us to work towards a goal of having **0 developer-maintained lines of C code** in rubinius.

Feel good presentation - nice job!
