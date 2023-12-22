---
layout: post
title: "Scheme and functional programming workshop 2013"
date: 2013-11-13 09:35
comments: true
categories: software scheme conj
---

Scheme has been around for 38 years. The scheme community is interested in cross-polinating with the clojure community, so they gave away free passes to the [2013 scheme and functional programming workshop](http://webyrd.net/scheme-2013/) to those folks attending Clojure Conj, including me.

I wanted to set up scheme on my box to try to fit in. Thomas Gilray, one of the presenters, who was sitting near me, didn't immediately say "yes yes" when I told him I was about to install mit-scheme, but indicated that he uses [racket](http://racket-lang.org/), which is apparently almost a superset of mit-scheme. I installed the dmg, since racket wasn't available through homebrew, started up the DrRacket application, and had a functioning repl:

``` racket
> "hello world"
"hello world"
```

Alexey Radul, Ph.D., MIT, and the keynote speaker, talked about propagators, which he had described in [the art of the propagator](http://web.mit.edu/~axch/www/art.pdf), one of his major academic projects. He agreed that his work is similar to functional reactive programming (FRP). The rest of the day was broken up into three sessions.

## Session 1 (Static Analysis)

### Entangled Abstract Domains for Higher-order Programs

Shuying Liang talked about using an [entangled abstract domain](https://github.com/shuyingliang/entangled-domain-py) to prove when a list is bound.

### Multi-core Parallelization of Abstract Abstract Machines

Leif Anderson researched whether static analysis processing could be sped up by using multiple cores. He concluded that, in the worst case, omega (infinite loop), multiple cores doesn't speed up analysis at all, and in the best cases, with functions like factorial, the speed up can almost keep up with your number of cores (he got 7.x times faster, and only had 8 logical cores). The source is [on github](https://github.com/LeifAndersen/CPSLambdaCalc).

### A Unified Approach to Polyvariance in Abstract Interpretations

Thomas Gilray explained that Abstract Interpretation is a general framework for Static Analysis that makes it easier to model computation, trading off precision (your abstraction isn't exactly the same as the program being analyzed). Here's [a paper](http://faculty.cs.byu.edu/~jay/conferences/2013-tfp/proceedings/tfp2013_submission_9.pdf) on a similar topic to that presented.

## Session 2 (miniKanren)

miniKanren is a relational, declarative programming language, and it inspired clojure's core.logic library.

### mu-Kanren: More with Less

Lispers love infinite lists. Jason Hemann pointed out, quoting someone, that "Infinity is only a problem if you try to print it." His project, [micro kanren](https://github.com/jasonhemann/microKanren) is 39 actual lines of scheme code, and needs a clojure port.

### rKanren: Guided Search in miniKanren

Cameron Swords demonstrated a [miniKanren implementation](https://github.com/cgswords/rkanren) that allows us to get back the answers we want first, by ranking clauses.

## Session 3 (General Scheming)

### lambda*: Beyond Currying

Jason Hemann argued that currying is pragmatic, and elaborated on a way to implement it in scheme with a library he wrote, [lambda*](https://github.com/jasonhemann/lambdastar).

### Automatic Cross-Library Optimization

The concept of inlining procedures (inline expansion) came up here, and it had come up earlier today as well. This is a common compiler optimization where the code in procedures is shoved into the calling procedure to speed up runtime performance. Some procedures in scheme can be inlined, and some not. Andrew Keep concluded that using library groups offers the best speedups, but when you can't write your scheme program with library groups in mind, you will often still get some speedups from [automatic cross-library optimization](http://www.cs.indiana.edu/~dyb/pubs/auto-xlib-opt.pdf).

### R7RS Scheme Standardization Update
Will Clinger reported that the current direction is to split the scheme language into two languages: 1) a small language suitable for education and 2) a larger language (more features) suitable for industry. Will said that the small language spec has been approved, so the first working group is finished with its task. Working group 2 is still on the task. There's more info at [scheme-reports](http://scheme-reports.org/).

All in all, I was glad I attended. I realized that I should read _The Reasoned Schemer_. The workshop was extremely academically-focused. I was able to get a fix of pragmatism by chatting with Gary and Paul ([revelytix](http://www.revelytix.com/)) over a break about leiningen plugins and polyglot clojure/java applications. We also wondered why 1) ruby has three types of functions and 2) if the only reason you have to .call ruby Procs is because of ruby's optional parentheses.
