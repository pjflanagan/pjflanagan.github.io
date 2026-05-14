---
slug: bell-revisited
layout: post
date: 2026-04-06
title: Bell
description: A REST scripting language
categories: tool
image: https://pjflanagan.github.io/bell/bell-card.png
github: https://github.com/pjflanagan/bell
website: https://flanny.app/bell
---

I still dislike Postman. Heavy GUI tools for API testing always feel like they're fighting against the developer's workflow. You have to click through menus, manage collections in a proprietary format, and it's a nightmare to version control. 

And now, with the ubiquity of AI chat bots, developers want their coding agents to be able to handle all aspects of their projects. That means more documentation, configs, and resources living in your codebase.

I wanted something that:
- was simple
- readable
- could live and run in VSCode
- was free
- wasn't plagued by cloud features and strange organization patterns

To achieve these goals, I decided to make a programming language specialized for making HTTP requests. Simple script files can live in your codebase, alongside your project.
For here, you and your coding assistant can easily read and edit it in your editor, run it from your terminal or a VSCode extension, and collaborate on it with git.

> Cleaner than Postman. Clearer than cUrl.

## The Idea

I first started [ideating on Bell](/blog/2024/bell-ideation/) back in 2024. The idea was to create a Domain Specific Language (DSL) that was as readable as a cURL command but as powerful as a full testing suite. 

Now, with AI to help me with the more complex parts of the parser and runtime, I've brought that proof-of-concept to life.

## How it Works

Bell scripts are simple `.bel` files. You define your endpoint, headers, and body using a clean, declarative syntax.

```bell
url "https://api.example.com/v1/login"

body {
  "username": "admin",
  "password": "{env.ADMIN_PASSWORD}"
}

POST
```

That's it!

## Building the Monorepo

In this MVP phase, it was important to build a little bit of every aspect of what this language could be. That meant in a monorepo we created:
- a `core` package for `bell-lang`
- a `vscode` package for the VSCode extension
- a `docs` app that serves the website explaining bell
- a `test-app` app for local testing 

## Plans

I plan to start using Bell to test all my side projects. While there a certainly bugs and imperfections, I feel with time, and perhaps support from other devs, Bell can become a viable option for testing APIs. Maybe then, I'll try bringing with me to work.
