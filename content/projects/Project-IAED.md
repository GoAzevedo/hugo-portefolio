---
title: "C Project: Introduction to Algorithms and Data Structures"
date: 2023-04-22T23:16:00+07:00
slug: c-introduction-algorithms-data-structures
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

# Project 1 statement - IAED 2019/20

## 1. Introduction

The goal of this project is to develop, in the C language, a logistics system. Interaction with the program should occur through a set of lines composed of a letter (command) and a number of arguments dependent on the command to be executed. The possible commands are listed in the table below and indicate the operations to be performed.

| Command | Action                                                                      |
| :-----: | :-------------------------------------------------------------------------- |
|  **a**  | adds a new product to the system                                            |
|  **q**  | adds stock to an existing product in the system                             |
|  **N**  | creates a new order                                                         |
|  **A**  | adds a product to an order                                                  |
|  **r**  | removes stock from an existing product                                      |
|  **R**  | removes a product from an order                                             |
|  **C**  | calculates the cost of an order                                             |
|  **p**  | changes the price of an existing product in the system                      |
|  **E**  | returns the description and quantity of a product in a given order          |
|  **m**  | returns the ID of the order in which a given product occurs most frequently |
|  **l**  | lists all products in the system in ascending order of price                |
|  **L**  | lists all products in an order in alphabetical order of description         |
|  **x**  | ends the program                                                            |

## 2. Problem Specification

The goal of the project is to have a logistics system that allows the management of product stocks and orders.

There are several products that can be added to orders.

Each **product** is characterized by:

- an identifier (an integer in the interval [0, 9,999])
- a description (a non-empty string with a maximum of 63 characters)
- its price (an integer greater than 0)
- its weight (an integer greater than 0)
- its quantity in stock (an integer greater than or equal to 0)

An **order** is a set of products.

The restrictions on the problem are as follows:

- The product identifiers are unique.
- It can be assumed that there will be at most 10,000 different products.
- The products are numbered from 0 to 9,999 and sequentially by their introduction order.
- It can be assumed that all products created with the `a` command will be distinct.
- It can be assumed that there will be at most 500 orders.
- Orders are numbered from 0 to 499 and sequentially by their introduction order.
- Each order may weigh a maximum of 200 units of weight.
- Only products that exist in the required quantity in stock can be added to orders.

It can be assumed that all input provided will respect the indicated types. For example, a product will never be added whose price is a string, a negative value, or zero.

## 3. Input Data

The program should read the input data from the command line and terminal.

During program execution, instructions must be read from the terminal (standard input) in the form of a set of lines initiated by a character, which is called a command, followed by a number of information dependent on the command to be executed. The command and each of the pieces of information are separated by the `':'` character.

Here is the markdown showcase of the project:

# Product Management System

This program is a product management system, which allows for the creation, management and calculation of orders, as well as stock management of different products.

## 1. How to run the program

The program should be run using a command line interface. Once the program is running, it will read commands from standard input. The available commands are listed below.

## 2. Commands

During the execution of the program, instructions should be read from the terminal (standard input) in the form of a set of lines initiated by a character, which is referred to as the command character, followed by a number of command-specific information separated by `':'`.

The available commands are:

- **a** - adds a new product to the system
  - Input format: `a description:price:weight:quantity`
  - Output format: `New product <idp>.` where `<idp>` is the identifier of the created product.
- **q** - adds stock to an existing product in the system
  - Input format: `q idp:quantity`
  - Output format: NONE (except for errors)
  - Errors:
    - `It is impossible to add product <idp> to stock. Product does not exist.` if there is no product created with that identifier.
- **N** - creates a new order
  - Input format: `N`
  - Output format: `New order <ide>.` where `<ide>` is the identifier of the created order.
- **A** - adds a product to an order. If the product already exists in the order, the new quantity is added to the existing one.
  - Input format: `A ide:idp:quantity`
  - Output format: NONE (except for errors)
  - Errors:
    - `It is impossible to add product <idp> to order <ide>. Order does not exist.` if there is no order created with that identifier.
    - `It is impossible to add product <idp> to order <ide>. Product does not exist.` if there is no product created with that identifier.
    - `It is impossible to add product <idp> to order <ide>. Insufficient stock quantity.` if there is not enough stock of the product to fulfill the order.
    - `It is impossible to add product <idp> to order <ide>. Order weight exceeds the maximum of 200.` if adding that product exceeds the maximum weight allowed per order.
- **r** - removes stock from an existing product
  - Input format: `r idp:quantity`
  - Output format: NONE (except for errors)
  - Errors:
    - `It is impossible to remove stock from product <idp>. Product does not exist.` if there is no product created with that identifier.
    - `It is impossible to remove <quantity> units of product <idp> from stock. Insufficient quantity.` if the remaining quantity after the removal would be negative.
- **R** - removes a product from an order

  - Input format: `R ide:idp`
  - Output format: NONE (except for errors)
  - Errors:
    - `It is impossible to remove product <idp> from order <ide>. Order does not exist.` if there is no order created with that identifier.
    - `It is impossible to remove product <idp> from order <ide>. Product does not exist.` if there is no product created with that identifier.

- **C** - calculate the cost of an order
  - Input format: `C ide`
  - Output format: `Order <ide> cost <total>.` where `<total>` is the total cost of order `<ide>`
  - Errors:
    - `Unable to calculate cost of order <ide>. Order does not exist.` in case there is no order created with that identifier
- **p** - change the price of an existing product in the system
  - Input format: `p idp:price`
  - Output format: NOTHING (except error)
  - Errors:
    - `Unable to change price of product <idp>. Product does not exist.` in case there is no product created with that identifier
- **E** - list the description and quantity of a product in an order
  - Input format: `E ide:idp`
  - Output format: `<desc> <qtd>.` where `<desc>` is the description of product `<idp>` and `<qtd>` is the quantity of that product in order `<ide>`
  - Errors:
    - `Unable to list order <ide>. Order does not exist.` in case there is no order created with that identifier
    - `Unable to list product <idp>. Product does not exist.` in case there is no product created with that identifier
- **m** - list the order with the highest quantity of a given product. If there are 2 or more orders in this situation, the order with the smallest `id` should be printed.
  - Input format: `m idp`
  - Output format:
    - `Maximum product <idp> <ide> <qtd>.` where `<ide>` is the order number where `<idp>` occurs most frequently, being that quantity `<qtd>`
    - Nothing should be listed if product `<idp>` does not occur in any order, or if there are no orders.
  - Errors:
    - `Unable to list maximum of product <idp>. Product does not exist.` in case there is no product created with that identifier
- **l** - list all products in the system in ascending order of price. If there are 2 or more products with the same price, they should be printed in ascending order of product `id`

  - Input format: `l`
  - Output format: A block in the format below, and where the products are listed in ascending order of price

        Products
        * <desc1> <price1> <qtd1 in stock>
        * <desc2> <price2> <qtd2 in stock>
        ...
        * <descn> <pricen> <qtdn in stock>

  - Errors: Not applicable

- **L** - list all products in an order in alphabetical order of description

  - Input format: `L <oid>`
  - Output format: A block in the format below, and where the products are listed in alphabetical order of description

        Order <oid>
        * <desc1> <price1> <qtd1 in oid>
        * <desc2> <price2> <qtd2 in oid>
        ...
        * <descn> <pricen> <qtdn in oid>

  - Errors:
    - `Unable to list order <oid>. Order does not exist.` if there is no order created with that identifier

- **x** - terminates the program
  - Input format: `x`
  - Output format: NOTHING

## 4. Output Data

The program should write the answers to the commands presented in the standard input to the standard output. The answers are also lines of text formatted as defined earlier in this statement. Pay attention to the number of spaces between elements of your output, as well as the absence of spaces and the periods at the end of each line. Try to scrupulously respect the indications given.
