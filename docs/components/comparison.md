---
layout: page
title: Comparison between these integration [TODO]
permalink: /components/comparison/
parent: Third party integration
order: 10
---


# Which type of integration I should choose?

## Polymer3

It's discouraged to use Polymer3 for a new component.
The Polymer team doesn't update Polymer and it's less and less used.
In my opinion, it's rather complicated to learn.
I would only use it if you already have components in Polymer and you already know Polymer.
That's the less future proof solution.

## Vanilla Javascript

It's a good option for JavaScript library that:
- doesn't work well with shadow dom
- enhance other components (For example, a tooltip or sortable layout (that brings reordering on *anything*).)
- does not contain html template

That's the best future proof solution since your code should work for a long time.

## Lit

It's a good option if:
- you are building a component without dependencies
- your component contains html that requires update

Lit is light and very powerful. For simple component, it's easy to learn.

The new version of Lit contains all the documentation in TypeScript and JavaScript. Vaadin's examples is written in TypeScript.
I would recommend TypeScript since it helps to write code easier to read, maintain and refactor.



