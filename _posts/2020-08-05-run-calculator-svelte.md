---
slug: run-calculator-svelte
layout: post
date: 2020-08-05
title: "Run Calculator - Svelte"
description: "Another lap"
categories: css svelte

image: https://runcalculator.flanny.app/img/social/share-card.png
github: https://github.com/pjflanagan/runcalculator
website: https://runcalculator.flanny.app
---

During COVID I was regularly watching [Fireship.io](https://www.youtube.com/c/Fireship) on YouTube. Fireship shares out basic tutorials on web frameworks in way that makes it easy to get excited over trying them. After watching one on [Svelte](https://svelte.dev/), I decided I'd revisit an old favorite.

In the most up to date version of `runcalculator`, I got the app to be where I always wanted it to be: as an installable app (thanks PWA's). The changes in this version included:

- Installable as a PWA
- Animations where I always felt they should have gone
- Sizing for various screens
- Making the website keyboard friendly, so users don't have to use the mouse 
- The ability to share what you've entered into the calculator just by copying the URL

![Version 3](/assets/posts/2020/run-calculator/v3.png)

## Thoughts on Svelte

I experimented with a very lightweight framework called Svelte and realized that I don't prefer it, but found it interesting. 

### Pros

Svelte feels like a return back to early web development, before Webpack and React. I like how Svelte allows you to bind variables, a feature I miss from when I used Angular. I also like the syntax for component props.

{% highlight svelte %}
<Component {prop1} bind:value={prop2} />
{% endhighlight %}

### Cons

But the rest of `.svelte` file syntax I can't say the same for:

- I don't miss adding `<style>` and `<script>` tags, and greatly prefer importing modules
- I don't like being required to name my files as the their component name
- I kinda like `{#if}{:else}` and `{#each}` blocks, but not as much as conditional rendering and `.map()`
- I couldn't stand state updates with `$: variableName`, many times it didn't seem to fire and I couldn't tell why

I understand what they were going for by having these files feel like simple little html pages, but the result feels very loose, like the variables are just floating around. It's very different from the sense of security that using Immutable variables in React affords.

Because Svelte is new, there are not a whole lot of packages available for it, so when developing you are kinda on your own. But it's also exciting that Svelte is new. It'll be exciting to see what happens to Svelte in later versions. I did enjoy using it for this project, and might use it again for other simple projects in the future.
