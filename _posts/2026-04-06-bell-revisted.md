---
layout: post
date: 2026-04-06
title: Bell
description: A REST scripting language
categories: tool
image: /assets/posts/2024/bell.png
github: https://github.com/pjflanagan/bell
website: https://flanny.app/bell
---

I still dislike Postman. 

Heavy GUI tools for API testing always feel like they're fighting against the developer's workflow. You have to click through menus, manage collections in a proprietary format, and it's a nightmare to version control. 

I wanted something that felt like a programming language, but was specialized for one thing: making HTTP requests and asserting on the responses.

## The Idea

I first started [ideating on Bell](/blog/2024/bell-ideation/) back in 2024. The goal was to create a Domain Specific Language (DSL) that was as readable as a cURL command but as powerful as a full testing suite. 

Now, with the help of AI to help me with the more complex parts of the parser and runtime, I've brought that idea to life.

## How it Works

Bell scripts are simple `.bell` files. You define your endpoint, headers, and body using a clean, declarative syntax.

```bell
POST https://api.example.com/v1/login
Content-Type: application/json

{
  "username": "admin",
  "password": "{{env.ADMIN_PASSWORD}}"
}

EXPECT status 200
EXPECT json.token EXISTS
```

One of the most powerful features of Bell is its environment variable handling. You can define variables in a `.env` file or pass them in via the CLI, making it easy to switch between local, staging, and production environments without changing your test scripts.

## Why use Bell?

1. **Version Control**: Because scripts are just text files, they live in your Git repo alongside your code.
2. **CI/CD Integration**: The Bell CLI is a single binary that can be dropped into any pipeline to verify your API health on every deploy.
3. **Speed**: No GUI to load. Just run `bell test login.bell` and see your results instantly.
4. **Readability**: The syntax is designed to be understood by anyone, not just the person who wrote it.

I've been using Bell to test all my recent projects, and it's already saved me hours of clicking through Postman collections. It's fast, it's light, and it just works.
