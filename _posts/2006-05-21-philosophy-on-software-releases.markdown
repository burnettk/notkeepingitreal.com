---
layout: post
title: Philosophy On Software Releases
typo_id: 9
categories: software philosophy
---
I believe that releasing new software when it is done[1], and immediately when it is done, is a tremendous boon to the developer (and by definition the customer, unless you happen to be adding features the customer doesn’t want). I’ve dreamed about this a lot, and advocated for daily web rollouts at work for months, so naturally I was pleased to find that [Paul Graham](http://paulgraham.com) has argued this point in his essay, [The Other Road Ahead](http://paulgraham.com/road.html).

There seems to be much opposition to this idea in the software arena. Releases are often no fun, and many seem to think that releases are inherently difficult, time-intensive and error-prone - and should therefore be minimized. Some say that customers need to be conditioned not to expect what they want **now**. There is definitely truth in this. But for all of the reasons releases are tricky, I believe they should be done **more** and more incrementally.

#### Releases are difficult

Sure. Releases will be difficult as long as:

-   People assume that they happen only infrequently
-   There is a perception that it just isn’t worth the effort to make them work the way they should

If I used the vim text editor once a week, I wouldn’t bother creating/learning the cutesy shortcuts. Institute a continuous release policy and the process will improve guaranteed.

#### Releases are time-intensive

Yes, if there are many new features, QA can become a long and uncertain process. And when a bug is found, the amount of time that has passed since the code was written correlates fairly directly to the time that will be needed to fix the bug.

#### Releases are error-prone

Certainly, managing the complexities and anticipating the interactions between features of a large release is an unenviable task.

So if new code is ready, or if a feature the customer wants is finished to everyone’s satisfaction, I feel that there shouldn’t be a ton of hoops to jump through before the new software finds its way into production. Developers will ultimately be happier to see their creativity in finished form faster, customers will get their feature more rapidly, and potentially, delicious manna will pour down from heaven.
