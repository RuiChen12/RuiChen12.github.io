---
layout: essay
type: essay
title: "Building with Patterns: Why Good Websites Are Like Good Cities"
# All dates must be YYYY-MM-DD format!
date: 2025-4-24
published: true
labels:
  - Software enginnering
  - Front-End
---

<img width="300px" class="rounded float-start pe-4" src="../img/Website.jpg">

## How Design Patterns Made My Code Feel Like a City

Imagine you are visiting a new city. You notice it’s easy to find your way around. The sidewalks look the same everywhere, the streetlights are always at the corners, and there are parks in every neighborhood. No matter where you go, you can always see signs that help you get back to the main square. The city feels comfortable and organized. Why? Because the city designers followed some good ideas about how to build things, and they use these same ideas everywhere. They don’t make up new rules for every street—they reuse what already works.

I think design patterns in coding are just like these smart ideas for building cities. They are not rules you must follow; they aren’t just step-by-step recipes. Instead, they are simple solutions that can help you fix common problems, so your code is easier to read, change, and reuse—just like a good city is easy to live in.

When I started making websites, everything felt messy. I would copy and paste the same navigation bar into all my pages. If I wanted to add a link, I had to change it everywhere, and sometimes I would forget a page. My website felt like a city with random roads and dead ends.

Later, I learned to use reusable components. It was like discovering building blocks that I could use anywhere. In React and Next.js, I made parts like buttons and navbars into their own little pieces. Now, whenever I needed a button or a navbar, I just dropped in my component. If I wanted to change the look, I only had to do it once, and all my pages were updated. This is called the Composite Pattern—it means you can build small parts and big parts in the same way, just like building a city out of houses, parks, and streets.

But cities also have a hierarchy—some places are important and always show up, like the main roads. On my website, the navigation bar is like one of those main roads. No matter which page you go to, the navbar is always there, helping you go back or move around. To do this, I learned about something called the Template Pattern (or global layout). I made a layout component that wraps all my pages, so every page has the same structure, but the content in the middle can change. This made my website feel more like a real city, with familiar paths and clear directions.

Using these patterns made my code so much easier to manage. If I wanted to add something new, like a notification icon or a footer, I just put it in the layout, and every page got it right away. If I needed to update a button, I did it in one place and every button changed.

In the end, I learned that design patterns aren’t about following strict rules—they’re about making your code cleaner and your work easier. Just like good city planning helps people feel comfortable and not get lost, good design patterns help your code be simple, organized, and fun to use.


This essay was written with assistance from ChatGPT, which was used to refine wording, improve clarity, and structure the content.....
