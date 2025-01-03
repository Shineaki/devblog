---
date: 2024-11-18
authors:
  - Dev
categories:
  - Python
  - GameDev
---

# PyRouge #2

I continue my journey with the implementation of Py*Rouge*.

Content:

* Field of view
* Placing Enemies and kicking them
* Doing (and taking) some damage
* Creating the Interface


<!-- more -->

## Part 4 - Field of view

Implemented! I think it looks great and it improves a lot on the feel of the whole thing :smiley:
Also, now I know that I can embed videos too, I had no idea mkdocs can do that. And I installed a spell checker to help with the typos.

<figure class="video_container">
    <video controls src="../../../../images/pyrouge/rouge_fov.mp4" title="Title"></video>
</figure>

## Part 5 - Placing Enemies and kicking them

Enemies are now generated - 80% for an Orc (O) and 20% for a Troll (T). They do not move yet and they do not attack / take damage yet.
I will try to add various monsters with different stats, based on the level we are on (like in the real Rogue).

<figure class="video_container">
    <video controls src="../../../../images/pyrouge/rouge_enemies_1.mp4" title="Title"></video>
</figure>

## Part 6 - Doing (and taking) some damage

Part 6 starts of with a huge refactoring session. I took over those changes, then we continue with some [pathfinding from the tcod](https://python-tcod.readthedocs.io/en/latest/tcod/path.html) library.
Now the enemies chase the player and:

* Wait if they cannot see the player
* Move towards the player if it is inside the FOV (and distance > 1)
* Attack the player (if distance = 1)

<figure class="video_container">
    <video controls src="../../../../images/pyrouge/rouge_part_6_enemies_chasing.mp4" title="Title"></video>
</figure>

And after some combat implementation now we can kill enemies (and they can kill us). The consol log is not visible, but it shows the damage we deal (and receive). I assume later this will be visible on the screen as well.

The combat is simple, the damage dealt equals attacker attack power minus the enemy defense, I guess this will also be improved later with a chance to miss / critical hit, deal damage on a range instead of a fixed value, etc.

<figure class="video_container">
    <video controls src="../../../../images/pyrouge/rouge_part6_fight_enemies.mp4" title="Title"></video>
</figure>


## Part 7 - Creating the Interface

Today we added a lots of stuff on the UI: a health bar, an expandable chat log and mouse hover over text!
Slowly it starts to resemble a game :smiley:

<figure class="video_container">
    <video controls src="../../../../images/pyrouge/rouge_part_7_interface.mp4" title="Title"></video>
</figure>

## Final Part

I continue this journey in [Part Three!](rogue_part_3.md)
