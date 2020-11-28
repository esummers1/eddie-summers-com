---
date: 2020-07-13T10:00:00+00:00
title: "Herding Cats"
summary: "Herding Cats is a game about the chaos of managing a busy cattery, developed over 48 hours for the GMTK Game Jam 2020."
categories: ["Projects"]
splash: "/images/herding-cats.png"
---

[Herding Cats](https://github.com/esummers1/gmtk-game-jam-2020) is a browser game created for the [GMTK Game Jam 2020](https://itch.io/jam/gmtk-2020), a 48-hour game-making hackathon. I worked on this game as part of Team Cat Herders. The theme this year was "Out of Control", so we decided that literally herding cats would be a fun idea.

[You can play the game here](https://danjb1.itch.io/herding-cats)! Please turn your sound on.

The idea of the game is that the player runs a cattery, where owners drop their cats off for short stays. The player takes on way more business than they can handle, which is a problem because the pen from which owners will collect their cats is small, and the cats are prone to escaping. Cats will avoid  the player and the player's trusty dog, which can be summoned to the player's location with a whistle. They must be herded into the pen to be picked up on time.

As cats approach their pickup time (shown in the bar at the top), coloured exclamation marks will appear over their heads. The player gains money (points) for each cat delivered on time, as well as a star (life) for delivering several cats in a row. If a cat is not ready for pickup by the time its avatar reaches the end of the bar, the player loses a star. If the star rating reaches zero, the game will end.

Since the theme was "Out of Control", the game is intended to be difficult and overwhelming. It usually feels as if the player is *almost* on top of herding all the cats, but this can change quickly.

Herding Cats runs natively in the browser. We used PixiJS for our rendering engine; luckily its latest versions support TypeScript, which we used for all our logic. The game engine itself was custom and used a component-based architecture to manage the entities' behaviour. Most of the assets we used were created by the team.
