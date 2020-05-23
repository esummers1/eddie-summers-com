---
date: 2017-08-18T16:00:00+00:00
title: "Agricultural Capitalism Simulator"
summary: "Agricultural Capitalism Simulator (ACS) is a tongue-in-cheek command-line farming business simulator. The player is given some money and a field, and told to make the greatest amount of profit possible in the allotted number of years."
categories: ["Projects"]
splash: "/images/acs.jpg"
---

![Agricultural Capitalism Simulator](/images/acs.jpg "Agricultural Capitalism Simulator")

Agricultural Capitalism Simulator (ACS) is a tongue-in-cheek command-line farming business simulator. The player is given some money and a field, and told to make the greatest amount of profit possible in the allotted number of years. Different crops have different ideal weather conditions, and different fields (which the player can purchase) have different qualities. The weather is generated each game year, producing a certain yield in each field according to its planted crop's characteristics.

There is also an AI mode, in which a basic evolutionary algorithm with a small set of weightings (probability to plant each crop, and aggressiveness when purchasing new land) optimizes those weightings for high scores. The best strategies from each checkpoint generation will be printed to the player at the terminal.

ACS was originally [written in Java](https://github.com/esummers1/agricultural-capitalism-simulator); I later [ported it to Python](https://github.com/esummers1/agricultural-capitalism-simulator-py), to practise the language.
