---
id: utility_first_fundamental
title: utility_first_fundamental
sidebar_label: utility_first_fundamental
sidebar_position: 1
tags:
  - Tailwind CSS
  - Getting Started
  - Tailwind CSS Setup
  - Tailwind CSS Installation
  - Tailwind CSS Quickstart
description: This guide provides instructions on how to get started with Tailwind CSS, including installation and basic usage.
---

# Utility-First Fundamentals

Building complex components from a constrained set of primitive utilities.

## Overview

Traditionally, whenever you need to style something on the web, you write CSS.

Using a traditional approach where custom designs require custom CSS

```html
<div class="chat-notification">
  <div class="chat-notification-logo-wrapper">
    <img
      class="chat-notification-logo"
      src="/img/logo.svg"
      alt="ChitChat Logo" />
  </div>
  <div class="chat-notification-content">
    <h4 class="chat-notification-title">ChitChat</h4>
    <p class="chat-notification-message">You have a new message!</p>
  </div>
</div>

<style>
  .chat-notification {
    display: flex;
    align-items: center;
    max-width: 24rem;
    margin: 0 auto;
    padding: 1.5rem;
    border-radius: 0.5rem;
    background-color: #fff;
    box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
  }
  .chat-notification-logo-wrapper {
    flex-shrink: 0;
  }
  .chat-notification-logo {
    height: 3rem;
    width: 3rem;
  }
  .chat-notification-content {
    margin-left: 1.5rem;
  }
  .chat-notification-title {
    color: #1a202c;
    font-size: 1.25rem;
    line-height: 1.25;
  }
  .chat-notification-message {
    color: #718096;
    font-size: 1rem;
    line-height: 1.5;
  }
</style>
With Tailwind, you style elements by applying pre-existing classes directly in
your HTML. Using utility classes to build custom designs without writing CSS
ChitChat You have a new message!

<div
  class="p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg flex items-center space-x-4">
  <div class="shrink-0">
    <img class="h-12 w-12" src="/img/logo.svg" alt="ChitChat Logo" />
  </div>
  <div>
    <div class="text-xl font-medium text-black">ChitChat</div>
    <p class="text-slate-500">You have a new message!</p>
  </div>
</div>
```

In the example above, we’ve used:

1.  Tailwind’s flexbox and padding utilities (flex, shrink-0, and p-6) to control the overall card layout
2.  The max-width and margin utilities (max-w-sm and mx-auto) to constrain the card width and center it horizontally
3.  The background color, border radius, and box-shadow utilities (bg-white, rounded-xl, and shadow-lg) to style the card’s appearance
4.  The width and height utilities (w-12 and h-12) to size the logo image
5.  The space-between utilities (space-x-4) to handle the spacing between the logo and the text
6.  The font size, text color, and font-weight utilities (text-xl, text-black, font-medium, etc.) to style the card text
7.  This approach allows us to implement a completely custom component design without writing a single line of custom CSS.

Now I know what you’re thinking, “this is an atrocity, what a horrible mess!” and you’re right, it’s kind of ugly. In fact it’s just about impossible to think this is a good idea the first time you see it — you have to actually try it.

But once you’ve actually built something this way, you’ll quickly notice some really important benefits:

You aren’t wasting energy inventing class names. No more adding silly class names like sidebar-inner-wrapper just to be able to style something, and no more agonizing over the perfect abstract name for something that’s really just a flex container.

Your CSS stops growing. Using a traditional approach, your CSS files get bigger every time you add a new feature. With utilities, everything is reusable so you rarely need to write new CSS.

Making changes feels safer. CSS is global and you never know what you’re breaking when you make a change. Classes in your HTML are local, so you can change them without worrying about something else breaking.
When you realize how productive you can be working exclusively in HTML with predefined utility classes, working any other way will feel like torture.

​

### Why not just use inline styles?

A common reaction to this approach is wondering, “isn’t this just inline styles?” and in some ways it is — you’re applying styles directly to elements instead of assigning them a class name and then styling that class.

But using utility classes has a few important advantages over inline styles:

Designing with constraints. Using inline styles, every value is a magic number. With utilities, you’re choosing styles from a predefined design system, which makes it much easier to build visually consistent UIs.
Responsive design. You can’t use media queries in inline styles, but you can use Tailwind’s responsive utilities to build fully responsive interfaces easily.
Hover, focus, and other states. Inline styles can’t target states like hover or focus, but Tailwind’s state variants make it easy to style those states with utility classes.
This component is fully responsive and includes a button with hover and focus styles, and is built entirely with utility classes:

```html
<div
  class="py-8 px-8 max-w-sm mx-auto bg-white rounded-xl shadow-lg space-y-2 sm:py-4 sm:flex sm:items-center sm:space-y-0 sm:space-x-6">
  <img
    class="block mx-auto h-24 rounded-full sm:mx-0 sm:shrink-0"
    src="/img/erin-lindford.jpg"
    alt="Woman's Face" />
  <div class="text-center space-y-2 sm:text-left">
    <div class="space-y-0.5">
      <p class="text-lg text-black font-semibold">Erin Lindford</p>
      <p class="text-slate-500 font-medium">Product Engineer</p>
    </div>
    <button
      class="px-4 py-1 text-sm text-purple-600 font-semibold rounded-full border border-purple-200 hover:text-white hover:bg-purple-600 hover:border-transparent focus:outline-none focus:ring-2 focus:ring-purple-600 focus:ring-offset-2">
      Message
    </button>
  </div>
</div>
```

​

### Maintainability concerns

The biggest maintainability concern when using a utility-first approach is managing commonly repeated utility combinations.

This is easily solved by extracting components and partials, and using editor and language features like multi-cursor editing and simple loops.

<!-- PrimaryButton.vue -->

```html
<template>
  <button
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
    <slot />
  </button>
</template>
```

Aside from that, maintaining a utility-first CSS project turns out to be a lot easier than maintaining a large CSS codebase, simply because HTML is so much easier to maintain than CSS. Large companies like GitHub, Netflix, Heroku, Kickstarter, Twitch, Segment, and more are using this approach with great success.

If you’d like to hear about others’ experiences with this approach, check out the following resources:

By The Numbers: A Year and a Half with Atomic CSS by John Polacek
No, Utility Classes Aren’t the Same As Inline Styles by Sarah Dayan of Algolia
Diana Mounter on using utility classes at GitHub, a podcast interview
For even more, check out The Case for Atomic/Utility-First CSS, curated by John Polacek.
