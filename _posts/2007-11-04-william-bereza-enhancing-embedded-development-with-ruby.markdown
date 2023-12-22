---
layout: post
title: ! 'RubyConf talk: William Bereza: Enhancing Embedded Development with Ruby'
typo_id: 1867
categories: rubyconf
---
This guy was creating an embedded system, and basically just wanted to test out ruby. Hard to blame a guy for that.

Back in the day, we had low-level languages, slow computers, and less tools. These days we have high-level languages, fast computers, and mad tools. So programming is easier **except on embedded devices, which remain in a scenario similar to that of the aforementioned “back in the day”**.

If only there were a way to bring testing, continuous integration, and other best practices to the embedded world..

**Maybe ruby could help**.

They had a couple rake targets: rake test:system and rake test:units. There was black box testing of the hardware, and mocking of various bits of the hardware.

They were able to link in with the continuous integration system used by the rest of the company (for rails projects, etc), since the embedded project build task was written in rake.

Results of using this rubyized system:

-   DRY C code
-   readable system code
-   readable system tests
-   tests!
-   customers were happy
-   developers were happy
-   lovefest and a half

