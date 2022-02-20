---
title: "Simulturn Devlog Part 2: Pathing Rework"
date: 2022-02-20T00:00:00+02:00
categories:
  - Blog
tags:
  - Game Dev
---

In today's devlog, we'll be starting with a little bit of game design discussion while I explain my reworking of the path laying system I built last time. If you played the first build, or go back to look at it, you'll find that it gave the player a lot of freedom to draw the paths they would like within the distance given. This was the first step into the system my game will be fundamentally based on, and as the fundamental system, it needs to be readable and reliable for everyone playing. 

As fun as it was drawing paths for the different characters, no player will actually have fun sitting down for a game just to find themselves calculating "the enemy's character goes at 5m/s, so I can expect them to be within this meter radius at this time," especially when that enemy can also just spend their turn squiggle dodging seemingly randomly. There's no weight to any one decision if the only decisions are all shots in the dark. Not to mention, drawing paths of nearly 50 points per character and iterating through the calculations for both players causes unnecessary processing that can be cut down on.

The solution is to cut back on some of the freedom of movement. Each character will have a set amount of actions that can be used to travel or attack, that can be spent in either way depending on the situation. If used on travel, than each singular action point will refer to a set distance in a straight line, and can be compounded to make a flowing path reminiscent of the system before. The distance per action needs to be small enough that the player is not able to dodge every attack coming their way, while also large enough to make it a worthy option choosing to reposition rather than attack back. In the future as well, there will be abilities that charge up attacks with small amounts of movement included, allowing for more options with the trade-off of reduced movement and attack telegraphing.

![Prototype in action](/assets/images/BlogPictures/Devlog2.3.gif)

By rebuilding the path system to be somewhat simpler, I was able to easily solve a problem that path drawing would inherently encounter if left unchecked. Because the computer checks the mouse position upon each frame rather than per micro-movement, there are opportunities for the mouse to drag points of the path past the maximum distance. This would namely happen when the mouse was moved quickly allowing it to cross more distance between frames, which can be seen here.

![Game not working properly](/assets/images/BlogPictures/Devlog2.1.gif)

Some players could get a movement increase just by dragging their input quickly, which would incentivize unwanted behavior in competitive matches. With a little math however, these points can be "clamped" to their desired location. In a way, the solution is to find a point on the circle drawn around the previous point that has our desired radius, and is closest to the new mouse position. Then, the line would be drawn towards the mouse, but will go no further than needed. If you want to see the math needed to find this kind of point, I added the functions to the [Desmos Graphing Calculator][desmos] as a live demonstration to test accuracy. And here's what it looks like during gameplay:

![Game working properly](/assets/images/BlogPictures/Devlog2.2.gif)

[Play the game here!](https://playerpeter1231.itch.io/simulturn-tactics-prototype){: .btn .btn--warning}

[desmos]: https://www.desmos.com/calculator/chqpnwrxql