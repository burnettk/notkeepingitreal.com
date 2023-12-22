---
layout: post
title: ! 'RailsConf talk: Rails Deployment on Shared Hosts - Geoffrey Grosenbach'
typo_id: 19
categories: railsconf
---
-   The nubyonrails.com guy
-   This session is about therapy. If you have had problems with shared hosting in the past, **it’s not your fault**.

So why do people choose to use shared hosting? It’s cheap and it’s easy.

And why is it such a big struggle? There are many pigs sucking at the same teet.

### Recommendations

-   Keep your app small. Use less resources.
-   Cache - page caching tends to work great in a shared hosting environment, assuming it can work for your app.
-   Don’t use typo *\_\
    \* Don’t use Lighttpd - Apache is usually the default, and the systems guys tend to like the defaults.\
    \* Use capistrano.\
     \<pre\>\
    \* set :checkout, :export\
    \* set :restart\_via, :run\
    \* set :use\_sudo, false\
     \</pre\>\
    \* redefine the :restart task so it reaps the proper dispatch.fcgi, etc\
    \* Write tests!\
    \* Use the reaper \
    \* Monitor that stuff \
    \* Possibly just avoid shared hosting alltogether and go with a virtual private server.
    \
    h3. Troubleshooting
    \
    \* The same stuff always goes wrong\
    \* Check you shebang line \
    \* ./script/server to see if the app can even load in webrick\
    \* ./script/console to see if you can even hit your database\
    \* tail -f your logs\
    \* And if none of that works just wait, someone else may be screwing with something
    \
    Buy my book: Rails Deployment from the pragmatic programmers.
    \
    *This [Geoffrey](http://geoffreygrosenbach.com), representing properly.\_

