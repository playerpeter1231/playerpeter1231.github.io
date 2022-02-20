---
title: "Simulturn Devlog Part 1"
date: 2022-02-18T00:00:00+02:00
header:
  overlay_image: /assets/images/BlogPictures/Devlog1.4.png
  overlay_filter: 0.75
  excerpt: The start of my big new project!
categories:
  - Blog
tags:
  - Game Dev
---

While I have a couple of projects that I have on the verge of finishing, I have also put myself on a time crunch to add a new game to my portfolio to show my process building a new project. I've been wanting to start a specific project for a few years anyway, so may as well use this time as an excuse to jump right on in.

The goal for this project is to build a prototype game that can run on mobile, and can be easily be converted into a 3D space once the game feels good. To describe the game (without giving too much away!), it will be a tactics game where the moves are input beforehand, and played out realtime once both players are ready. This way, no one player has to wait for the either outside of finishing turns quickly.

Starting out, my goal for today's code was to create instantiable characters that can be selected, dragged, and locked into their given path, before moving across that path on turn end. To do this, I created a script that when the character's "cursor" is dragged, it will periodically add points to a rendered line following the player's directions. The points are only added when the player has moved the cursor a predetermined distance so that the processor isn't adding new points to the line every frame. Then, on turn end, a path is passed the same points of the line to direct the characters across the line.

![Prototype in action](/assets/images/BlogPictures/Devlog1.3.gif){: .align-center}

Once the characters have all reached the end of their path, the previous path turns red to show what was done in the last turn, and to signal that the new turn has begun. Characters are then ready for the next turn, allowing for them to be moved within their range across the entire screen over the period of however many turns it takes to do so.

Code was handled in only two scripts, which were the Main Scene Controller, and the Player script (currently inaptly named DragLine.gd). The next step will be cleaning up the circle's interaction with the characters, and the few bugs found on button inputs and end of animation selection, both detailed on the Itch page where the game is hosted. Then, the exciting part, I will be adding hit points and a small handful of attacks to show where the direction of this project is heading in. Lastly, I will develop the prototype onto mobile for testing on local hardware, and I will share with you the progress throughout the weekend!

![Player scene from within the editor](/assets/images/BlogPictures/Devlog1.1.png){: .align-center}

If you want to look at the code and history thereof, it is available in a public [github repository][code-repo], and of course if you want to play it, click this shiny button!

[Play the game here!](https://playerpeter1231.itch.io/simulturn-tactics-prototype){: .btn .btn--warning}
{: .align-center}

![My notes from the day](/assets/images/BlogPictures/Devlog1.4.png)

[code-repo]: https://github.com/playerpeter1231/SimulTurn-Tactics