---
title: "Assembly Galaxy of Pulsars"
date: 2023-04-19T23:15:00+07:00
slug: assembly-project-spaceship-game
category: projects
summary:
description:
cover:
  image:
  alt:
  caption:
  relative: true
showtoc: true
draft: false
---

## Project Description:

### 1 - Objectives:

This project aims to exercise the fundamentals of the Computer Architecture field, namely programming in assembly language, peripherals, and interrupts. The objective of this project is to develop a simulation game of a rover defending planet X, which must obtain energy from good meteors and destroy bad meteors, which are nothing more than robot ships sent to invade the planet. The interface consists of a screen, a keyboard for game control, and a set of displays to show the rover's energy.

### 2 - Specifications

The MediaCenter module of the simulator has various multimedia capabilities, allowing for defining background images, playing sounds and videos, multiple image planes constructed pixel by pixel, a front scenario for billboards, etc. Laboratory script 4 provides more details on this module. By clicking on some of the keys, the keyboard allows the game's command (start, pause, and stop) to be made, as well as controlling the rover's position. The displays allow the current energy of the rover to be displayed, which varies over time.

Each game state (initial, playing, paused, terminated, etc.) should have a different background image or video or a billboard (front scenario, an image with transparent letters and background), to give a visual indication of the game's state. The figure on the previous page illustrates a possible entry scenario, in which the user must press the C key to start the game. It can also be a video, with the letters superimposed by means of a front scenario (with a transparent background).

### Generic idea

- The rover is at the bottom of the screen (surface of the planet) and can only move (by keys) to the left and right.
- Meteors come from far away from the top of the screen, so when they appear, they are just a gray pixel. These meteors descend vertically and increase in size as they approach the rover. In the second size (2 x 2 pixels), they are still distant and gray and indistinct, but from then on, they change shape and color depending on whether they are good meteors (green) or bad meteors (enemy ships, red), as illustrated in the following figure;
- The rover's goal is to destroy enemy ships (by firing a missile) to defend the planet and obtain energy from good meteors (allowing them to collide with it).
- The collision of a missile with a meteor (good or enemy ship) implies its destruction and that of the meteor, with an explosion effect. Note that the missile has limited range (thus cannot hit distant meteors).
- Undestroyed enemy ships and unused good meteors are lost in the bottom of the screen. Whenever an enemy ship is destroyed, a good meteor collides with the rover or any of them is lost at the bottom, a new one is born at the top, with the type (good meteor or enemy ship) chosen in a pseudo-random way (25% good meteor, 75% enemy ship).
- The rover has an initial energy (100%). That energy is spent over time, just by the fact that the rover is running. Firing a missile spends additional energy. However, colliding with a good meteor and destroying an enemy ship increases that energy.
- The game ends if an enemy ship collides with the rover or if the energy reaches zero. The game's objective is, therefore, to keep the rover running for as long as possible, obtaining energy from good meteors and destroyed ships and avoiding colliding with an enemy ship.
- The player must have the option to pause the game, as well as resume after pausing, terminate the game at any time, and start a new game after the previous one ends
