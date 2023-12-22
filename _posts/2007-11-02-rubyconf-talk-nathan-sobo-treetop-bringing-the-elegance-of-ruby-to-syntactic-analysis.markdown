---
layout: post
title: ! 'RubyConf talk: Nathan Sobo: Treetop: Bringing the Elegance of Ruby to Syntactic
  Analysis'
typo_id: 1856
categories: rubyconf
---
These slight technical difficulties. Handled fairly elegantly. Hot guy.

I was surpised with how many of you said you had written a parser when Jim Weirich asked the question this morning, since I would have expected very few folks to have written parsers with classic context-free generated grammars. And then again, I was surpised with how few of you said you had written a parser when Jim Weirich asked the question this morning, since I know that **lots** of folks have written parsers - at least parsers like regular expressions to parse strings.

Parsing Expression Grammars are mad hot since they can do recursion - and Treetop is a Parsing Expression Grammar.

Arbitrary ruby is not allowed inside of a treetop grammar as at yet - maybe in the future.

And this live coding followed. Good times parsing a mathematical expression and testing the various pieces.

One of the cool things about Treetop is that it does not “lex”, unlike many other parsers. There are cool posibilities with sharing well-constructed grammars and reusing grammars inside of other grammars to construct more complex grammars. Neat. Really enjoyable presentation.
