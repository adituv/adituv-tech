---
layout: post
title: Getting Started with GH3 Modding
description: A complete-basics tutorial on the modding tools available for Guitar Hero 3 and how to use them.
modified: 2017-04-06
categories: [guitarhero, tutorials]
tags: [guitarhero, tutorials, queenbee, ghtcp, modding]
image:
    feature: modding-feature.jpg
---

This tutorial will walk you through using [GHTCP](#ghtcp) and [Queen Bee](#qb)
for some simple game tweaks, including texture replacement.  If you are already
comfortable with these things, you may want to skip this tutorial.

<!-- more -->

## GHTCP

**Guitar Hero Three Control Panel** is a program by MaXKilleR for managing custom
songs and setlists in Guitar Hero.  I won't be covering how to use it to do that
here though; there are plenty of tutorials out there already.  A later post
will cover how it handles custom songs and setlists.  The two things I will
cover here are the Texture Explorer, and the "FX Speed Boost" option.

### Texture Explorer

As the name suggests, the Texture Explorer gives you a list of all the textures
in the game files for you to extract or replace.  Due to the way the game works
you cannot add or remove textures, or change which ones are animated[^1].  For
the same reason, do not use the "Clone" button; that only duplicates the texture
in the game files, but does not make the game aware of the new texture.

In any case, you can access Texture Explorer through the Game Management menu
in GHTCP.  It scans all files in your game's DATA folder for textures every time
you start it up, so it takes a while.  When it's done, you have an interface
like this:

{% capture images %}
  {{ site.url }}/assets/images/posts/texture-explorer-1.png
{% endcapture %}
{% include gallery images=images caption="Texture Explorer on finishing texture discovery" cols=1 %}

In the leftmost column there is a list - grouped by directory - of all files
containing textures.  Some files are an individual texture and some are a
container with multiple textures inside them.  Double-click a file to load it,
then click one of the "Image X" entries in the next column to view the image.

{% capture images %}
  {{ site.url }}/assets/images/posts/texture-explorer-2.png
  {{ site.url }}/assets/images/posts/texture-explorer-3.png
{% endcapture %}
{% include gallery images=images caption="Texture Explorer on double-clicking a texture entry" cols=2 %}

You can extract and replace images in the game files using the "extract" and
"replace" buttons respectively.  However **only extract to a dds file, and
only replace with a png file**.  This is to avoid various texture explorer
bugs to do with transparency and dds file conversion.


[^1]: There is a method using a custom dll file for GH3+, but that is far beyond
      the scope of this tutorial.

[ghtcp]: https://drive.google.com/open?id=0B1I-tX15pao5cXQtTDlYcUxHbTQ
[queenbee]: https://drive.google.com/open?id=0B1I-tX15pao5a2RFd00wcUtZZ00
