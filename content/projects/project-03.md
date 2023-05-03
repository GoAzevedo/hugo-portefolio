---
title: "Python Project: Technical Battle Simulator"
date: 2023-04-20T23:15:00+07:00
slug: python-technical-battle-simulator
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

# Technical Battle Simulator

The second project of Fundamentals of Programming involves writing a Python program for simulating battles between two armies consisting of units that move and attack within a 2D maze, which may contain obstacles.

## Simulation of Battles

### Maze, Units, and Armies

The maze is defined in the same way as in the first project, i.e., it is a rectangular structure with positions indexed from the upper left corner of the maze, with walls at the positions of the outer limit, where the remaining positions can correspond to walls or corridors. The corridors may or may not be occupied by units.

In this second project, each unit belongs to one of two possible armies. In addition to moving in the maze, units attack units from the opposing army. Each unit, in addition to its position in the maze and its army, is characterized by its life points and its attack strength.

The order of reading the positions of the maze is defined as in the first project: from left to right followed by top to bottom.

### Turn, Movement, and Attack of Units

The simulation of a battle consists of executing multiple battle turns until one of the two armies wins, i.e., until all units of an army have been eliminated, or until there are no more possible movements. In each battle turn, each unit - following the order of reading the maze - performs a movement and an attack.

The movement consists of a single step to an adjacent position following the unit movement rules described in the first project, with the only difference that only adjacent positions free of each of the enemy units (i.e., from the opposing army) are considered as possible target positions. As in the first project, a unit stays still if it is already adjacent to an enemy or if there is no reachable target position.

After completing a movement, if the unit is adjacent to at least one enemy unit, it then performs an attack. If there is more than one adjacent enemy unit, the attack target is the first one according to the map reading order.

The effect of an attack consists of subtracting the attacking unit's attack strength points from the attacked unit's life points. An attacked unit that runs out of life points is eliminated, ceasing to exist in the current battle turn as well as in subsequent turns.
