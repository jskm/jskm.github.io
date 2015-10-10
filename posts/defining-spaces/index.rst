.. title: Defining Spaces
.. slug: defining-spaces
.. date: 2015-09-04 04:41:00 UTC-04:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Here's what I've managed for defining spaces so far. Just kept blindly
using a number of scipy image processing functions till I managed to
figure out what they did. Quickly noticed that the `distance transform
function <https://en.wikipedia.org/wiki/Distance_transform>`__ had
potential, but I've spent an entire day trying to learn how to segment
the map using that data. Attached are a couple of plots I generated
showing the kind of information I've been able to extract. It looks like
taking the local maxima of the distance transform does reasonably well
for identifying distinct spaces. Now I think I need something similar to
the `watershed
transform <https://en.wikipedia.org/wiki/Watershed_(image_processing)>`__
to actually establish the boundaries of each room.

.. image:: /images/Spaces1.png

.. image:: /images/Spaces2.png