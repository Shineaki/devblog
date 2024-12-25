---
date: 2024-11-30
authors:
  - Dev
categories:
  - Python
  - GameDev
---

# PyRouge #3

Last part of my journey of implementing  Py*Rouge*.

Content:

* Items and Inventory
* Ranged Scrolls and Targeting
* Saving and loading
* Delving into the Dungeon
* Increasing Difficulty
* Gearing up

<!-- more -->

## Part 8 - Items and Inventory

Another great chapter! We created some classes to support items & a basic inventory system. We implemented our first item: Health Potions, then we updated our procgen script to also generate these items in the rooms. Now we are able to pick up these potions and drink them to get some health back after fighting!

I also changed the colors a bit to make things more visible.

![Potions](../images/part_8_potions.png)


I really recommend this [tutorial](https://rogueliketutorials.com/) for everyone, because it is awesome and I feel like I learn a lot just by following (and basically copy-pasting code from the browser to the IDE) through.

<figure class="video_container">
    <video controls src="../../../../images/part_8_inventory.mp4" title="Title"></video>
</figure>

## Part 9 - Ranged Scrolls and Targeting

Just finished adding ranged scrolls:

* Confusion scroll (enemy AI changes to just wandering around for a few turns)
* Lighting scroll (deals huge damage to the closest enemy)
* Fireball scroll (deals AOE damage)

I also started uploading videos to Youtube instead, because embedding all of them here would increase the repo size significantly.

<iframe width="800" height="400" src="https://www.youtube.com/embed/zPSMPrQLOfc?si=KodIynhd0viCL5Mq" title="PyRouge - Part 9" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Part 10 - Saving and loading

We added a main menu, implemented saving (by pickling the engine) and loading. Now if I close the game it automatically saves the game state & I have the ability to load it back later _except_ if we died, because then it deletes existing save files & shuts down without saving - obviously :wink:

<iframe width="800" height="400" src="https://www.youtube.com/embed/6qbQJduhiJI?si=gPJMq35eoncfp5Ch" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

I spent at least 2 hours debugging the code, because ~5 chapters ago I decided to implement something differently and it broke during this chapter, causing the game to not handle inputs ... Why do I always do this. **ALWAYS.REFACTOR.AT.THE.END.**

## Part 11 - Delving into the Dungeon

The first part of this chapter was about adding the stairs, so we can actually delve deeper into the dungeon.
In the second part we implemented a simple leveling mechanic, each mob gives some exp and if a threshold is reached, we level up and can select from one of the following "improvements":

* +20 HP
* +1 Strength (+1 damage)
* +1 Agility (+1 defense)

## Part 12 - Increasing Difficulty

We implemented an improved item & monster spawning "strategy". On the first few levels basically we only spawn 1-2 Orcs (easier to kill enemies) and as we dive deeper into the dungeon the maximum number of monsters increases and we also spawn Trolls (harder to kill). Similar setup with items: first we only spawn health potions, but then we increase the probability of spawning scrolls too.

Obviously this is not sufficient yet for a real game, because if you level up twice and increase your defense then even the Trolls can't damage you, so some additional monsters / stat updates / more complex combat logic is required, but it is a good start.

<iframe width="800" height="400" src="https://www.youtube.com/embed/BrtAxKXXgms?si=kMNLO55DPZ0hdTSO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Part 13 - Gearing up

We added the possibility of picking up and equipping items! There are two types of items currently: weapons (dagger with +2 Attack and sword with +4 attack) and armors (leather with +1 defense and chain mail with +3 defense).

Now our hero is officially broken, because as soon as you level once and upgrade your defense literally nobody can damage you. 

## Next Steps

Well, this was fun! During the tutorial I came up with the following vague plans for the future:

* Collect & organize roguelike guides/tutorials/etc (from Roguebasin, roguelikedev subredit, etc)
* Read up on roguelike combat balancing
    * Stats, chances, how to make it fun
* Read up on and implement dungeon generation algorithms
    * This will probably be my first step
* Move things to PyGame
    * For some reason I would love to re-implement the same thing but using PyGame and some sprites and continue the development from there
* Implement the same thing in Dart (with Flutter + Flame)
    * For web / mobile / desktop
    * Obviously this would be a large jump, because I probably cannot use tcodlib & numpy arrays for the map related things (path finding, los, etc)
* Think about how to implement the same thing in multiplayer
    * As I said before I really want to implement something in multiplayer, so this goal will always linger around
    * The issue is that this turn based setup would (probably?) have to change in order to make it fun for multiplayer, but going from turn based to real-time feels like a huge jump right now


... that's all for now, but I will keep going tomorrow! :wink: