.. title: Events, Scrolling
.. slug: events-scrolling
.. date: 2015-08-27 16:02:00 UTC-04:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

For events, I was thinking of using publish/subscribe to connect the
game's components and systems with each other. In that case I'd try to
use an existing library, and
`PyPubSub <http://pubsub.sourceforge.net/>`__ might be an option. Might
also consider extracting the `dispatch
module <https://github.com/django/django/tree/master/django/dispatch>`__
from Django
(`docs <https://docs.djangoproject.com/en/1.8/topics/signals/>`__) if
it's independent enough. Though I don't know enough about the
performance consequences of something like this, and performance is
going to be a significant issue soon.

I'll need to do another rewrite soon, because the code is not at all
designed to handle a scrolling viewport. Too much of it is based on
assumptions about the screen being a single map. There are a lot of
design issues to work out before that can happen properly, and at the
same time I should think about reducing the amount of unnecessary work
done on each frame. I likely won't be able to manage that before
Saturday.

In the end, scrolling might be something that's better off dropped,
because it substantially complicates many parts of the game. It depends
on whether I'd be able to find the right abstraction to limit that.
