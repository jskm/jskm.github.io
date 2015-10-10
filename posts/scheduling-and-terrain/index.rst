.. title: Scheduling and Terrain
.. slug: scheduling-and-terrain
.. date: 2015-08-17 08:05:00 UTC-04:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

I've done more work on the roguelike prototype. Ran into a couple more challenges than I intended to deal with. I want to make the game turn-based, but I had to use a real-time game loop to avoid having very clunky and unresponsive input. So the UI updates at 60 fps, but I need the game entities to update in step with the player. I had to set up a very crude scheduler for entities along with an action queue system. At least now I can have my NPCs carry out move, wait, and loop instructions.

Also had to start defining terrain characteristics so that I could start map generation. I'm currently using JSON to define symbol sets and colors for different terrain types, but it'll get much more complicated before it's capable of everything I'll need. I spent way too long trying to coordinate terrain patterns and colors. Finally, though, I've got the first dungeon generation algorithm working. Uses some simple cellular automaton rules, based on `this article`_. It looks pretty much like I wanted it to, but this method creates space as pretty much an unstructured blob. I'll have to eventually figure out how to establish/guarantee connectivity, find useful spaces for distributing dungeon features and monsters, and so on.

.. image:: /images/cellular%20automaton%20cave%20generation.png

The code at this point is a horrible mess. I'll need to rewrite it to use an entity-component system before I can get any actual gameplay going. For now, I'll just try to work out other methods of dungeon and overworld generation, and try to produce a decent map representation that can handle the features I require.

`Here's a good post`_ that lays out several of the basic systems needed for a roguelike game. I'm glad I stumbled across it since it kept me from having to discover them through trial and error.

.. _this article: http://www.roguebasin.com/index.php?title=Cellular_Automata_Method_for_Generating_Random_Cave-Like_Levels
.. _Here's a good post: https://groups.google.com/d/msg/rec.games.roguelike.development/aIUAF_cGpds/Z02w9PNRvBEJ

