---
date: 2024-12-15
authors:
  - Dev
categories:
  - Python
  - GameDev
---

# Roguelike development with PyGame - Week 1

Let's dive into PyGame

<!-- more -->

## Day 1

### PyGame-ce :crown:

Turns out PyGame is not really extended anymore, so we should use PyGame-ce (Community Edition). 

It's not a big deal, because I barely started implementing something and ce is completely backwards compatible with pygame (with some additional features, larger community, etc)

### Moving Around, Animations :video_game:

This will be though, lol. I actually had to implement my own animation logic (by measuring time between updates, loading the next frames, etc). This is quite a unique experience after using Unity & Godot :laughing:

I just bought a book called [Game Programming Patterns](https://gameprogrammingpatterns.com/) where the author dives into quite some low-level topics. When I initially looked at them, I was like ... what the heck, most of these things are handled by the engine without me having to know about them ... Now it might be the time to actually start reading the book :book:.

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_animated_movement.gif){ width="600" }
</figure>

### Tiles

I created a simple baseclass for tiles, which seems to be working, but probably not that efficient, so I will have to read up on how to properly do this in PyGame.

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_tiles.gif){ width="600" }
</figure>

#### Goal   

I also created a dummy dungeon with [Tiled](https://www.mapeditor.org/), just to see how it would look like in the end.

My current issue is that the walls seem to be shifted in the X direction, so they don't line up to the tile borders (I don't know if this is intended or not), so I will probably have to fix that in order to make my life easier later.

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_tiled.png)
</figure>

After filling it up with some props it is not such an eyesore anymore. Obviously getting here just from code will be an adventure, but thankfully Christmas season is around the corner, so we might have some free-time to work on it.

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_tiled_filled.png)
</figure>

### Map Generation 

I initialized the map procgen script (based on the PyRogue implementation), but I am way too tired to keep going, so I will call it a day.

Also, doing this with sprites will be a lot harder, since the walls are not a single character (like with tcodlib), 
but will actually have to connect, based on rules about their neighbors ... so it will be fun. 

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_map_gen_1.png)
</figure>

I also plan to extract the whole map generation & visualization part to a separate script where I can test other algorithms & can record some fancy videos about how they work. 

#### Adding walls around rooms

Okay, I couldn't stop working on this, so here are some updates. I created a tilemap where I only added the tiles that I need & aligned the walls correctly. This is how it looks right now (The bottom right corner is just some leftover from messing around)

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_procgen_tileset.png){ width="300" }
</figure>

Then I continued implementing the procgen script to generate rooms & walls around them. First I don't differentiate between left/right/top/bottom walls, I only have 3 type of tiles: void (gray area), wall & floor.

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_procgen_walls_1.png){ width="600" }
</figure>

After that I started differentiating corners from walls, I added 4 additional type of sprites: TL_C (Top-Left Corner), TR_C (Top-Right Corner), BL_C (Bottom-Left Corner), BR_C (Bottom-Right Corner). I haven't implemented the part where I actually render the correct images, so it looks like this:

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_procgen_walls_2.png){ width="600" }
</figure>

And after differentiating between top/bottom/left/right walls too & correctly implementing the sprite rendering, it starts to look okay:

<figure markdown="span">
    ![PyGame](../images/pygame/2024_12_08_procgen_walls_3.png){ width="600" }
</figure>

My current "naive" solution will not work for too long, because in the next step we will have to add hallways too, where I can't define the wall types so easily, instead I will have to check the neighboring wall types and decide on the correct sprite based on that. But I leave that for tomorrow.

## Day 2