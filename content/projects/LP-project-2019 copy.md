---
title: "Puzzle Solving Algorithm"
date: 2023-04-22T23:15:00+07:00
slug: puzzle-solving-algorithm
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

## Puzzle Solving Algorithm

### Initialization

The first step in solving a puzzle consists of initialization. In some cases, this step is sufficient to solve the puzzle. To initialize a puzzle, follow these steps:

### 1.

Get an ordered list whose elements are lists with the letters of each word. For example, for the puzzle in Fig. 1, this list would be `[[a,m,e,n,o],[a,t,o],[d,a,o],[d,i,a],[d,r,a,m,a], [m,a,e],[m,a,n,d,e],[s,e,d,e],[s,o,a,r]]`.

### 2.

Get a list with the available spaces in the grid to which words can be assigned. Consider that a space has at least three positions. The list must be ordered to present the spaces from the first to the last row, from left to right, followed by the spaces from the first to the last column, and from top to bottom. For example, for the puzzle in Fig. 1, this list would be `[[P11, P12, P13], [P15, P16, P17, P18], [P23, P24, P25], [P35, a, P37], [P41, P42, P43, P44, P45], [P11, P21, P31, P41, P51], [P13, P23, P33, P43, P53], [P15, P25, P35, P45], [P17, P27, P37]]`.

### 3. Get the list of possible words for each space. This list will be referred to as the list of possible words from now on. A word `Pal` is possible for a space `Esp` if:

- `Pal` and `Esp` have the same length.
- `Pal` respects the letters already assigned to elements of `Esp`. For example, the word "ato" is not possible for the space `[P35, a, P37]`.
- The placement of `Pal` in `Esp` does not make it impossible to fill other spaces with positions in common with `Esp`. For example, the word "ato" is not possible for the space `[P11, P12, P13]`, because position P13 would be filled with "o", this position is the first of the space `[P13, P23, P33, P43, P53]`, and there is no five-letter word starting with "o".

The result of this step consists of a list in which each element is a list of 2 elements: a space and the (ordered) list of possible words for that space. For example, for the puzzle in Fig. 1, the list of possible words would be `[[P11, P12, P13], [[d, i, a]]], [[P15, P16, P17, P18], [[s, e, d, e], [s, o, a, r]]], [[P23, P24, P25], [[a, t, o], [m, a, e]]], [[P35, a, P37], [[d, a, o]]], [[P41, P42, P43, P44, P45], [[m, a, n, d, e]]], [[P11, P21, P31, P41, P51], [[d, r, a, m, a], [m, a, n, d, e]]], [P13, P23, P33, P43, P53], [[a, m, e, n, o]]
