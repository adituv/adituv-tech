---
layout: post
title: 'Getting Started with GH3 Modding, Part 1'
description: A complete-basics tutorial on GHTCP's Texture Explorer
modified: 2017-04-07
categories: [tutorials]
tags: [guitarhero, tutorials, ghtcp, modding, textures]
image:
    feature: modding-feature.jpg
---

This tutorial covers using Texture Explorer within GHTCP to make texture
replacements, and the details of the FX Speed Boost option.  It is intended as
a guide for beginners to modding; if you are already familiar with Texture
Explorer, you may want to skip this tutorial.

<!--more-->

## GHTCP

**Guitar Hero Three Control Panel** ([download][ghtcp]) is a program by MaXKilleR
for managing custom songs and setlists in Guitar Hero.  I won't be covering how
to use it to do that here though; there are plenty of tutorials out there
already.  A later post will cover how it handles custom songs and setlists.  The
two things I will cover here are the Texture Explorer, and the "FX Speed Boost"
option.

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

Other than the fretboards, the vast majority of useful textures are in the ZONES
folder, particularly in `global_gfx.tex`.

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

### FX Speed Boost

For the "FX Speed Boost" option, there is not so much to say.  The option edits
your `qb.pak.xen` file (more on this in [Part 2: Queen Bee][queen-bee]) to
replace some scripts that create visual effects with scripts that do nothing.
This is supposed to speed up your game a little by reducing the effects on
screen, but as most modern computers can run Guitar Hero 3 at several hundred
fps it is mostly just for personal choice.

The scripts it replaces are:

`do_starpower_stagefx`
: removing the heart and bat animations, etc, when you have star power active

`first_gem_fx`
: removing the shine accompanying the first note of a chart

`hit_note_fx`
: removing hit flame animations and most spark particles

`guitarevent_multiplier4xon_spawned`
: removing the flames around the character's hands when the multipilier is 4x

`guitarevent_starsequencebonus`
: removing the star particles and lightning on completing a star power phrase

As FX Speed Boost doesn't allow choosing only some of these, I recommend not
using the option at all, instead making the changes in Queen Bee directly, or
using my Extra Settings mod which provides all these options and a few more.

[ghtcp]: https://drive.google.com/open?id=0B1I-tX15pao5cXQtTDlYcUxHbTQ
[queen-bee]: /tutorials/getting-started-with-gh3-modding-queen-bee
