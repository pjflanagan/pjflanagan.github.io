---
slug: price-matchers
layout: post
date: 2026-05-21
title: Price Matchers
description: Daily Amazon Price Guessing Game
categories: game live
image: https://pricematchers.flanny.app/share-card.png
github: 
website: https://pricematchers.flanny.app
---

I've been building a little daily game called **Price Matchers**. Inspired by Price is Right, I figured I could bring a price guessing game to the world using real Amazon products. 

Here's how it came together.

## The Goals

I've built games, including daily games (see OhWord!?), before. I also enjoy playing daily games quite a bit (my favorites are ___, ___, and __). Something that these games all have that OhWord!? does not have is a true finished state.

The games I enjoy most are puzzles meant to be solved. You answer a question and are either right or wrong and maybe you are judged for how right or wrong. In OhWord!? you are given a task meant to be completed, but it's never done.
User's are never wrong or rewarded for obscure knowledge or quick thinking. It's part of the reason that I don't even play OhWord!? that often myself.

I wanted to make a new game, with set puzzles (like how the NYT Crossword is curated), that had a true end state.

> Main Goal: Create a fun daily game with a **solveable** puzzle

I also wanted to see if I could generate some profit from it. With the game idea already being very product oriented, I felt there were a few opportunities to generate revenue:

- Use Amazon affiliate links
- Allow advertisers to list their products on the site
- Google AdSense (which I've already setup for this domain)

With these goals, I started building (it's 2026, so I really mean vibe coding).

## The Stack

Nothing exotic here, mostly chosen for zero cost and ease of use:

- **Next.js 15** (App Router) on **Vercel** free tier
- **Neon Postgres** (serverless, free tier) via **Drizzle ORM** (as per Claude's recommendation)
- No user accounts — scores live in `localStorage`
- No auth library — admin is protected by a single password in middleware

This was the first project that I asked Claude to start from scratch. I noticed that Claude likes Tailwind a lot. I cannot stand Tailwind, so I had to ask for a refactor.

Claude also recommended Neon and Drizzle, which I think is the right call for a project this size. It's typed, lightweight, and its migration system is simple enough to reason about without a runbook. The schema is around five tables: `puzzles`, `puzzle_slots`, `products`, `game_plays`, and some ancillary stuff. Drizzle configs also allow Claude to see all the db change history, which is great because I ask Claude to make all these changes anyway.

## The Gameplay and Name

The premise is simple: show someone an Amazon product, maybe they have something similar or maybe they've never heard of it, then ask them to guess the price. I called it "DealBusterz" (with the A->Z being an homage to Amazon's logo).

The format was:
- "Price Is Right" rules: guess as close as you can get without going over, if you're over: you're "Busted!"
- 3 products per puzzle, each gives you 15 seconds to make a guess
- only 1 guess per product

With a basic game created, it was time for some user feedback. I found that the game was too unforgiving. The game played too quickly, with the timer rushing you and only 1 guess. But the biggest thing was that the game didn't let you feel smart. After 1 guess, you were told close, far or busted. No knowledge is gained and then used.

I also felt that advertisers wouldn't like this for a few reasons:
- products would be shown for only 15 seconds at most
- players a punished for guessing too high, wouldn't they prefer people be pleasantly surprised by a good deal?

So I changed it up:
- You get three guesses per product. After the first, you get a proximity hint ("very close!" / "way off!"). After the second, you learn whether you moved in the right direction. Score is based on accuracy across all three products.
- No timer, take as long as you want
- No concept of busting, at the end you're either "Short" or "Overpaid"

This game was more fun, as you have time to correct your mistakes. There's a feeling of discovery.

With a new core mechanic, we needed a new name. I went with PriceMatcher$, because now the game is about matching price. I went with a fire theme.


<!-- 
A few mechanics I had to think carefully about:

**Scoring.** Score is accuracy-based, not binary. If you guess $47 on a $50 item, that's 94% — you get green. If you guess $20, that's 60% and you get orange. The score tiers run from 95% (phenomenal) down to 14% (brutal), and each tier has its own set of result headlines chosen randomly from a pool. It makes the end screen feel less canned.

**Multiple guesses.** You get three guesses per product. The first guess gives you a proximity hint. The second tells you better/worse. The third is your last shot. Originally I had just one guess, which made the game too punishing and too fast.

**The timer question.** There was a timer in the game at one point. I removed it. With a timer, players were anxious instead of engaged, and wrong guesses felt unfair. Without a timer, the game is about knowing prices, not about typing fast. One of those decisions that felt risky and immediately felt right.

**Share text.** The share output uses emoji rows to represent per-item accuracy, styled like a receipt. Players can paste it into any chat app and it reads cleanly.
-->


## Building the Admin Panel

And now for the behind the scenes part.

Early on I was creating puzzles by hand — writing database inserts directly. That's fine for a proof of concept, but it's not sustainable when you want to stay two weeks ahead of the calendar.

The admin is a proper internal tool. It has:

- A **dashboard** showing today's completions, the next schedule gap, a site version number, and a button to clear local storage so I can play again
- A **calendar** with drag-and-drop to move puzzles between dates
- A **puzzle editor** where you paste an Amazon link, click Fetch, and the app scrapes the product page for title, image, and live price
- A **products table** with filtering by status (unused / in-puzzle / played) and affiliate link presence
- A **stats page** with histograms of guess distributions, median delta, and per-product breakdowns

One useful pattern: the dashboard computes the "next gap" — the soonest date with fewer than 3 products scheduled. It's a small quality-of-life thing, but it means I open the admin, see "next gap: June 14 (13 days)", and know exactly what I need to do.

## Using AI to Generate Puzzle Content

<!-- TODO: talk about how I'm either curating scheduled posts or just reviewing a backlog of undated puzzles -->

Now for OhWord!? I auto generated puzzles randomly, like spilling tiles out of a Scrabble bag, and that was enough. But for this, a little more has to go into each. Puzzles need a theme and three different products. Puzzles themes should be relevant to the season and coming holidays. Products should be unique and reasonably priced. Since more thought has to go into these puzzles, I figured I should have AI make a backlog of them.

The product pool is built by scraping Amazon. But to scrape usefully, you need search queries — something like "stainless steel kitchen timer" or "outdoor motion sensor light". Coming up with 200+ of those by hand is tedious. So I didn't.

There's a prompt in `scripts/categories-prompt.txt` that asks Claude to generate 100 new product search queries, avoiding duplicates already in `scripts/categories.txt`. The prompt has two modes baked in: if you're running it in Claude Code (the CLI), it reads the existing file, avoids duplicates, and appends directly. If you're running it in claude.ai, it prints the queries for manual paste. The result is that growing the product pool is a one-command operation.

The seeder then takes those queries, fetches two products per query from Amazon, and inserts them into the database. A `--dry-run` flag lets you preview without writing anything. After seeding, the admin product page shows everything in a table where I can delete the weaker of each pair and mark affiliate links.

The pipeline looks like:

1. prompt
2. categories file
3. seeder script
4. admin curation
5. puzzle scheduling.

Each step is manual enough that I stay in control of quality, but automated enough that the bottleneck is curation time, not generation time.

## Monetization Plan

Here's the business model I'm building toward:

**Sponsored puzzle slots.** Amazon shop owners can pay to have their product featured in a daily puzzle. Every player that day sees the product — guaranteed views, no algorithms. After the puzzle airs, the advertiser gets an email with total views and a guess distribution (what did people *think* your product cost?). That guess data is genuinely valuable market research, not just vanity reach.

**Pricing model.** A flat processing fee plus a per-player rate based on recent daily active players. So if yesterday had 200 completions, an advertiser can see their estimated cost before submitting. The price is transparent and predictable, unlike CPM ad networks.

**Self-serve flow (planned).** Advertisers visit `/advertisers`, fill out a submission form with their Amazon URL and preferred air date, and put a card on file via Stripe (authorized but not captured). I review the submission in the admin, accept or reject, and the card is captured on the day the puzzle airs. If I reject it, the hold is released with no charge.

**Why this model and not banner ads?** Banner ads on a game like this would ruin it. The whole appeal is that you're looking at a product and thinking about its price. A sponsored product slot *is* the game mechanic — it's not a distraction, it's the content. That's a much cleaner value proposition for an advertiser than a leaderboard banner.

## What's Next

A few things I'm actively thinking about:

**Affiliate revenue.** Every product has an Amazon affiliate link. Right now those links appear on the end screen. The click-through rate is low because players are done with the game by the time they see them. Better placement might help.

**User stats persistence.** Scores are in localStorage, which means they vanish when you clear your browser. A lightweight account system — maybe just email + magic link — would let players see their streak and lifetime accuracy. I'm holding off until there's traffic worth retaining.

**Auto-fill from the affiliate API.** Right now I scrape Amazon product pages manually. The Amazon Product Advertising API would give structured data (title, image, price) without scraping. It requires a qualifying affiliate account gated on minimum traffic — a nice problem to have eventually.

**Data aggregation.** Storing anonymized guess data across all players builds an interesting dataset over time: what does the median person think a cast iron skillet costs? That's either a fun public stats page or, for advertisers, a compelling data product.

