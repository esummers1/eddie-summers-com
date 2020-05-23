---
date: 2018-05-16 16:00:00 +0000
title: "Orbit Simulator"
summary: "Orbit Simulator is a two-dimensional physics sandbox. It uses a high physics framerate (decoupled from the slower rendering framerate) to compute the orbits of moons, planets and stars using real-world figures at high time accelerations."
categories: ["Projects"]
splash: "/images/orbit-simulator.jpg"
---

![Orbit Simulator](/images/orbit-simulator.jpg "Orbit Simulator")

[Orbit Simulator](https://github.com/esummers1/orbit-simulator) is a two-dimensional physics sandbox. It uses a high physics framerate (decoupled from the slower rendering framerate) to compute the orbits of moons, planets and stars using real-world figures at high time accelerations.

The player can focus the camera on different objects in the simulation, adjust the display scale and time acceleration factor, and 'fire' new objects into the simulation. These new bodies will be created using the average path and velocity of the mouse-drag, meaning they appear seamlessly and intuitively. The other objects in the simulation will feel the gravitational effects of the new object immediately.

Objects that collide merge into a new object with the combined mass and volume of its parents; its colour will also be an average.

Orbit Simulator is written in Java and uses Swing for the UI. It can handle highly-accelerated simulation of dozens of bodies without slowdown, though dense objects such as black holes can cause weird behaviour when other objects pass very close.
