---
layout: post
title: ! 'RubyConf talk: Charlie Nutter (and his homie): JRuby: Ruby for the JVM'
typo_id: 1859
categories: rubyconf
---
So who doesn’t know what JRuby is? (eerie silence). Cool, well we won’t talk about that toooo much, but it’s a java implementation of ruby. Lots of IDEs are getting support for ruby these days, and a lot of that is actually because of JRuby, since IDEs written in java were able to jack the jruby parser and utilize it for their own devious purposes (variable renaming, syntax highlighting, etc).

The jruby compiler is the first ruby compiler for a general-purpose VM. It’s ready for use! We’d recommend ahead-of-time compilation rather than just-in-time compilation for many apps. Lots of neat compiler optimizations are in there - cached literals, using native java features, etc. The ObjectSpace\#each\_object method has also been removed unless you pass a certain flag into jruby since it’s really slow to implement that particular method in java.

Jruby does **not** support standard C ruby extensions, but they would recommend pulling in native java libraries instead, as (they reckon) most of the things you would want to accomplish have already been implemented in java. Rmagick is currently being ported.

It is possible, as one might expect, to pull in java from ruby with jruby. A common use-case for this is to create GUIs with java swing, and the ruby swing abstraction actually does a lot to simplify the swing API and make it more enjoyable to use.

Upcoming features are Hibernate-backed persistence, Ruvlets (Ruby Servlet-like API), Rspec, and many others. Good times.
