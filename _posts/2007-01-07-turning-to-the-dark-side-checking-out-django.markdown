---
layout: post
title: Turning to the Dark Side - Checking out Django
typo_id: 1566
categories: django software rails experimentation
---
Working with ruby on rails for a while has made me curious about django, the web development framework written in ruby’s buddy language, python. The tipping point for actually checking it out came after my friend [Matt Langeman](http://langeman.net/) told me about the [django beta book](http://www.djangobook.com/en/beta/).

So I’m rocking along with the book, which is luckily very hands-on. The good stuff begins in [chapter two](http://www.djangobook.com/en/beta/chapter02), where they go over how to set up your system to actually run django.

I’ve already got python:

    > python
    Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
    [GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2

So on to this django framework itself. Somewhere near the beginning of chapter two, the authors say that “Most people will want to install the latest official release.” I will soon begin to doubt this when I see the number of errors that can be produced by *simply following along with the examples* in the book (granted, some of these struggles certainly have to do with my specific environment). Anyway, onwards:

    > wget http://www.djangoproject.com/download/0.95/tarball/

I unpack the app, create a project and run: “python manage.py runserver” and I’m off to the races and no wait, I can’t hit anything on 127.0.0.1 since I’m not running locally.

How about “python manage.py runserver 0.0.0.0:8000” much better. I manage to arrive at the welcome page in my browser: “It worked! Congratulations on your first Django-powered page.”

While moving through [chapter three](http://www.djangobook.com/en/beta/chapter03/) and setting up urls.py (some sort of distant relative of rails routes), I’m slapped with the error: “ImportError at /now/ No module named mysite.views”.

Damn, I didn’t call my project “mysite” like a good tutorial-follower. I change “mysite to”survey" in urls.py and I’m golden again for a minute

After a very short minute, I get “AttributeError at /now/ ‘function’ object has no attribute ‘rindex’”.

Someone from django-users@googlegroups has apparently had this issue before, and I get referred to [the django docs](http://www.djangoproject.com/documentation/url_dispatch/). I discover that the cool kids (or maybe just the kids that aren’t using django edge) use a string for the second argument of the so-called “tuple.”

Bad:

    (r'^now/$', current_datetime),

Good:

    (r'^now/$', 'survey.views.current_datetime'),

The page loads, displaying the current time. The book reminds me that I have just created my first dynamic page with django. Fair enough.

So I’m rolling along in [chapter four](http://www.djangobook.com/en/beta/chapter04/) by now, and the authors are wanting me to start up the interactive python interpreter by typing “python,” which I do. I also type: “from django.template import Template”, but am greeted with an error: \

    raise EnvironmentError, "Environment variable %s is undefined." % ENVIRONMENT_VARIABLE
    EnvironmentError: Environment variable DJANGO_SETTINGS_MODULE is undefined.

Apparently i was supposed to set up this environment variable before firing up my interactive python client. After running: “export DJANGO\_SETTINGS\_MODULE=survey.settings” on the command line (where survey is the name of the project I created), I try to import Template again. ERROR: “EnvironmentError: Could not import settings ‘survey.settings’ (Is it on sys.path? Does it have syntax errors?): No module named survey.settings”. So at this point I’m wondering why God doesn’t love me. Someone with a searchable chat archive, however, does love me. I’m told to run:

    export PYTHONPATH=~

This apparently worked because my django project was one level below my home directory. I finally get the simple interactive python example to work.

[Chapter four](http://www.djangobook.com/en/beta/chapter04/) is all about django’s templating system. One distinguishing feature of django templates is that they are limited. Rails templates allow arbitrary ruby code, whereas their django counterparts allow variable injection, looping, and other assorted goodies, but do not evaluate **just any** python code you throw between tags.

So as I’m getting ready to use my first real template in a separate file, I need to set up the path to my templates. I try to do it the cool-guy way:

    TEMPLATE_DIRS = (
        os.path.join(os.path.basename(__file__), 'templates'),
    )

And I get an error when I try to hit a page: “NameError: name ‘os’ is not defined”. Not cool. Luckily the fix is simple. I add the line “import os” before setting up TEMPLATE\_DIRS in the settings.py file. No more errors, so I throw the sample template current\_datetime.html into the templates directory and try to fire up the page in my browser:

    TemplateDoesNotExist at /now/
    current_datetime.html

The “Template-loader postmortem” that comes up in my browser seems to be telling me that it’s trying the find the file under settings.pyc/templates/, which seems wrong. So hell, I want to get back to the book, and I don’t *have* to be a cool-kid at the moment - I’ve probably got some time here before rolling out my first production django site - I hardcode the absolute path for TEMPLATE\_DIRS. Bingo: fixed.

In talking about templates, the authors make a statement that sounds slightly more than controversial for someone coming from a rails worldview: “Because that’s business logic, it belongs in the view.” This highlights a major difference in language between the rails and django clans. The authors really wanted to make the point that business logic does not belong in the **template** (which is basically what rails folks would call a “view”). The way django relates to MVC (or MTV as they sometimes seem to call it) is clarified a bit more in [chapter five](http://www.djangobook.com/en/beta/chapter05/).

As I’m reading along, I learn that “python manage.py shell” is the equivalent of rails’ “./script/console”. I’m also able to connect to the MySQL database on my box successfully from the python prompt *with the django settings* on my first try. Sweet. I’m patting myself on the back when the book blindsides me with a note that I have not yet created a django app. *Mutter I could have sworn that I* . The authors patiently explain to me that an “app” is a portable set of django functionality, and that I must create an app in order to make use of django’s **models**. I’m right about at the point where’s I’m ready to go create an app on the command line when I realize that, *ohmygod, the funny things in the left margin of this book are comments!* Man I bet that would have been useful. :) It seems like the authors probably could have said one or two things about the comments on the first page of the book - or maybe they assumed that people were paying attention

In any case, this django stuff is a good time. I will likely continue on with creating an app, connecting to a database, and all sorts of delightful things in chapter five and beyond, but I’ll try to keep my two cents contained to the comments in [the book](http://www.djangobook.com/en/beta). Your two cents can go in the comments below.
