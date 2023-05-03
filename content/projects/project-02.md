---
title: "Pathfinding in a Maze: A Python Project"
date: 2023-04-21T23:15:00+07:00
slug: Python Project
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

# The Maze

In this first project of Programming Fundamentals, students will develop functions that allow implementing a program to simulate the movement of a unit through a 2D maze containing obstacles and other units. This unit always moves to an adjacent space to get closer to one of the remaining reachable units in the maze.

## 1 Movement in a maze

### 1.1 The maze and units

The maze is a rectangular structure of size Nx × Ny, where Nx is the maximum size of the x-axis and Ny is the maximum size of the y-axis. Each position (x, y) in the maze is indexed from the origin position (0, 0), which corresponds to the upper left corner of the maze. In a maze, all positions on the outer boundary are walls, meaning they cannot be occupied. The remaining positions can either be walls or corridors. Corridors (or empty spaces) are positions that can be occupied by units that move through the maze. Each unit occupies only one position in the maze at each point in time. The order of reading positions in the maze is always from left to right and top to bottom.

### 1.2 Unit movement rules

The movement of a unit is calculated by applying the following rules:

• A unit moves by taking steps. A step is defined as a single movement made to an adjacent position. The set of positions adjacent to a unit is defined as the positions immediately above, below, to the right, or to the left of it. Units cannot pass through walls or other units.

• To choose the next position of a given unit, start by identifying the set of possible target positions, which are the adjacent positions free of each of the remaining units. If the unit is already adjacent to another unit, it remains stationary.

• Next, determine the path of minimum number of steps from the unit to the target position. The target position is the one (among the possible target positions) that is at the minimum number of steps away. If more than one target position is at the same distance (a tie), choose one of them arbitrarily

### 1.3 Search for the path with a minimum number of steps

There are several algorithms that allow solving the problem of finding the path with a minimum number of steps between two positions in a maze. One possible approach is Lee's algorithm1, which is based on Breadth-First Search (BFS)2, an algorithm for traversing or searching in graphs.

The BFS algorithm is based on ensuring the exploration, or visit, first of all reachable positions with the same number of steps before moving on to explore positions reachable with a greater number of steps. To do this, it uses a linear data structure known as a queue where the new positions to be explored are added at the end of the queue. We call this structure the exploration queue.

Initially, the exploration queue contains only the initial position. Next, the algorithm cyclically processes the positions found in the exploration queue, always removing the position that is in the first position until the termination condition is reached (for example, the removed position is the destination) or until the exploration queue is empty (in this case, the termination condition could not be reached). For each position in the exploration queue, the processing cycle begins by checking if the position has already been visited. If so, the position is removed from the queue and the next position is processed. If not, the position is explored and marked as visited. To make this possible, it is necessary to store the visited positions in a structure called visited positions.
The exploration of a position consists of adding to the exploration queue the adjacent empty positions. In order to be able to recover the path when we reach the destination position, it is necessary to store the sequence of adjacent positions that led us to each explored position.

In this first FP project, the objective is to find the path with the minimum number of steps from a given position to one of the possible objective positions, according to the tie-breaking and movement rules described in the previous section. The BFS algorithm ensures that the first visited position that corresponds to one of the possible objective positions is reached in a minimum number of steps. On the other hand, to ensure that the tie-breaking rules in the choice of the next position and the objective position are met, it is sufficient to add the positions to the exploration queue in the appropriate order (from lowest to highest reading order) during the exploration phase. The corresponding pseudocode is described in Algorithm 1.

## 2 Work to be done

The objective of the first project is to write a program in Python, corresponding to the functions described in this section, that allows moving a unit in a maze as described above. To do this, you should define the set of requested functions, as well as eventually some additional auxiliary functions.

### 2.1 Representation of the maze and units

Consider that a maze is internally represented (i.e., in your program) by a tuple with Nx tuples, each of them containing Ny integer values. The integer values represent each position in the maze and can take values of 1 or 0 depending on whether the position corresponds to a wall or not.

Also, consider that the positions occupied by the units present in a maze are internally represented by a set of positions corresponding to a tuple of positions. A position is internally represented as a tuple of two integers corresponding to the first value representing the position on the x-axis and the second value representing the position on the y-axis.
