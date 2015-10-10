.. title: Infinite World
.. slug: infinite-world
.. date: 2015-08-26 10:21:00 UTC-04:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

It took about 16 hours, but I managed to stitch multiple maps together
with only rare defects on the edges. It looks really good to me, and the
errors are likely just because I cut a couple of corners in the
smoothing phase of the generation algorithm. Currently the game has no
viewport concept, rendering a map per screen and switching maps when you
walk off the border. I'm intending to redesign it for smooth scrolling,
but that's been more of a challenge. I've been struggling with designing
a world model for the game, to abstract away the individual maps and
unify location handling.

As for what I might work on next... I could try spawning creatures
and giving them basic behaviors. That sounds a bit complicated, though.
Useful behavior for NPCs requires giving meaning to spaces in the world,
and that might take a while to figure out. I wanted to prototype
communication/interaction systems, but combat systems will be easier to
get started on, and they don't need particularly intelligent behavior.

Pathfinding could be worth looking at. I just found `this
blog <http://paleoludic.com/writing/>`__, which has an interesting
approach to roguelike game structure. It's rather different from what
I've done so far, though. What I've got right now is an infinite world,
so I don't know if `Dijkstra
maps <http://www.roguebasin.com/index.php?title=The_Incredible_Power_of_Dijkstra_Maps>`__
are feasible.

There are also field-of-view and line-of-sight algorithms. I'm looking
at `Restrictive Precise Angle
Shadowcasting <http://www.roguebasin.com/index.php?title=Restrictive_Precise_Angle_Shadowcasting>`__
for the FOV algorithm.
`FastLOS <http://www.roguebasin.com/index.php?title=FastLOS>`__ looks
interesting; I'd have to implement it to understand what it actually
does.

I haven't actually set up an event system, so inter-object communication
is kind of limited at the moment. There are also a whole lot of
optimization issues. Making the maps larger is very costly and I'll have
to rewrite some of the drawing and update routines.

I may also look at increasing terrain complexity, creating more
interesting features. Maybe wilderness or town maps as I mentioned
before. That's somewhat easier to make visible progress on with the
current state of the game. And there are lots of links to terrain
generation material. A few such:

On noise:

* https://code.google.com/p/fractalterraingeneration/w/list

* http://staffwww.itn.liu.se/~stegu/simplexnoise/simplexnoise.pdf

* http://staffwww.itn.liu.se/~stegu/simplexnoise/SimplexNoise.java

* https://github.com/caseman/noise

| You might have already seen this one before:
| http://www-cs-students.stanford.edu/~amitp/game-programming/polygon-map-generation/

| And the more general:
| http://www-cs-students.stanford.edu/~amitp/gameprog.html

| There's this very interesting demo:
| http://tinykeep.com/dungen/
| With explanation:
| https://www.reddit.com/r/gamedev/comments/1dlwc4/procedural_dungeon_generation_algorithm_explained/
