---
layout: post
title: ! 'RubyConf talk: Shinohara and Kiwamu Kato: Introduction to AP4R, Asynchronous
  Processing for Ruby'
typo_id: 1855
categories: rubyconf
---
One of these homies just got married last month - his good. They also re-wrote their company’s 10-year-old package processing system (most recently in java) in ruby - their good.

Their messaging system, AP4R is:

-   LIGHTWEIGHT AND ROBUST, apparently
-   open-source
-   simple to use
-   used by various companies, including their 500-person firm in Japan
-   backed by the mascot apar, an armadillo, which is the most important feature
-   able to handle “busy” tasks and “heavy” tasks independently, resulting in better performance
-   able to play nice with capistrano (deployment goodness)
-   testable with functional tests (shortcut but fast-running) and async tests (better tests but slower)

They demo’d a shopping cart application, and the performance gains that can be had by using AP4R to processing the **slow back-end processes** asyncronously, while giving the user immediate feedback.

There are features planned for upcoming releases! Sounds like AP4R is a living organism, and well worth looking into for the right application.
