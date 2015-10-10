.. title: Rewrite, NumPy, SciPy
.. slug: rewrite-numpy-scipy
.. date: 2015-08-22 05:17:00 UTC-04:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

I'm feeling pretty good now. Friday was a really productive day. I began rewriting the game in-place, tearing open the code and extracting it into neater compartments. Once I got into it, it became surprisingly easy to progress. I think it helped that, after cutting out each piece, being able to focus on returning the program to a working state kept me on track. In the last day and a half, I've been able to unravel the nest of patchwork hackery I'd put together and get the program looking sensible again.

After initially cleaning up the game loop, I started thinking about the possibility of live-coding. Did a little research, and found out how to spawn an IPython console in a separate thread, with access to the game's internal state. Being able to inspect and modify the game's map structure and other data makes it much easier to follow what the map generation process is doing. I've managed to put together a couple of nice debug mechanisms and visualization functions, which should help with future complications.

Unfortunately Python doesn't have enough support for full live-coding. I can reload changed modules, but it won't update existing objects. After hearing about Clojure's advantages here, I'm more motivated to finally look into it now. Maybe once I'm done with my ideas for the roguelike.

I've reworked map handling to use numpy, which substantially increased the speed of the dungeon generation algorithm. It can run several iterations on the current map size in tens of milliseconds, much better than the couple of seconds it took before. I improved the way terrain variation was implemented, and based it on a hash function as mentioned before. I also started putting together the entity-component system, but since I have no idea what it really ought to look like, I don't know whether I've created some kind of abomination. It's working for now and I've got characters moving again, but I'll call it placeholder.

UI is nonexistent and input handling is simplistic for now. The thing that caused me the most trouble yesterday was coming up with a scheduler for entity actions/updates. Struggled with it for a while and ended up just reimplementing the basic scheme I used before, but with slightly better separation of concerns.

The following is a screenshot showing scipy and matplotlib used to display isolated map regions. I've only figured out very basic usage so far, but maybe I can do something interesting in time.

.. image:: /images/ipython,%20scipy,%20matplotlib.png

The game is currently running on 32-bit Python 2.7, with libtcod 1.5.1, numpy 1.9.2, scipy 0.16.0, and IPython 4.0.0.

Libtcod is the main limitation here--I'm getting errors attempting to build a 64-bit version from the repo, and the Python bindings don't work properly on Python 3. I kind of want to switch to pyglet since there isn't really all that much benefit to being on libtcod aside from the simple console-like output. I don't want to try to implement my own tile engine at the moment though.

Never mind what I said about wilderness generation being next. I really want to get multiple maps and map transitions working. Then see if I can force the edges of the cell-automaton generated maps to link up. Roaming through endless random caves has potential, and I can use that as a starting point for basic gameplay.