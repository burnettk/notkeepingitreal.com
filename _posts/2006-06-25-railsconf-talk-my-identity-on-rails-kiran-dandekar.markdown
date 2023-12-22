---
layout: post
title: ! 'RailsConf talk: My Identity On Rails - Kiran Dandekar'
typo_id: 18
categories: railsconf
---
-   Red Sox Fan, PhD from MIT, works for Verisign, country music fan, from India, not an alcoholic
-   In the real world, people see me in different ways depending on the context: family, friends, business, hobby.
-   On the web, I’m put into a box. Each site requires me to enter my personal info in the way they want, and I must remember each of my usernames and passwords.
-   This is site-centric, not user-centric
-   When traveling, an airline asks for and accepts any state driver’s license as identification. The driver’s license is interoperable, multi-purpose and portable.
-   GET ME ONE OF THOSE FOR THE WWW!

### An Open Identity system should be

-   Extensible
-   User managed
-   Open
-   Perpetual (not just used once)

### Sites already on board:

-   Livejournal, wikimedia, zoomr, schtuff, railsweenie

### It’s about you

-   The general idea is that when you go to a site, you are redirected back to **your** site, where you log in. The site that you intended to go to communicates to your site and confirms your identity, allowing you into the site you wanted to go to in the first place. And best of all, once you do login once, you’re on: Single Sign On!
-   There are attributes that you control. You can specify the attributes that you want to share with each site.
-   Some attributes (such as age, like if you are on a site selling alcoholic beverages) need to be **verified**. Certain companies would then be in the business of verifying OpenID attributes.

### Other Technical Presenter Guy

-   The CTO of verisign went through a setup of an OpenID client in rails. *Pretty hot*.
-   Some sites may **require** certain attributes, so there may be opt-in/opt-out. A lot of the parts of the implementation are still under discussion.
-   There is a serious question about how sites will know which OpenID servers to trust. It is neat to think that you could have your information hosted on your own website, but who are you anyway, that you would be trusted? There has been talk of servers being trusted if they are a “friend of a friend.”

*Awesome stuff, if it ever works out in practice. [Jeffmo](http://jeffmo.us) is skeptical. Matt Pelletier from [eastmedia](http://identity.eastmedia.com) has been working on this as well, and he gave a talk on the topic Sunday morning.*
