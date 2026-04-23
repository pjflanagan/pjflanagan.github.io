---
layout: post
date: 2025-09-27
title: Study Mandarin
description: A lightweight Traditional Chinese study site
categories: web live
image: https://www.flanny.app/study-mandarin/src/img/banner.png
github: https://github.com/pjflanagan/study-mandarin
website: https://flanny.app/study-mandarin
---

I've created other mandarin study tools for myself before. The problem I've faced with them is that I get too invested in building them and don't spend as much time using them.

Programming has been an important part of my study journey. Not enough tools out there teach Traditional characters, so writing a program to convert Simplified to Traditional has been very helpful for me. It's also nice to be able to bring flashcards I've made anywhere with me on my phone.

To balance both the usefulness of a custom website and limit my time actually creating that website, I resolved to under-engineer it. No backend, no accounts, no Chrome integrations, no PWA. Just jQuery and HTML.

The site I've come up with is a collection of pages meant to keep me on track
- A home page with my daily tasks, study suggestions, links to external tools
- A flashcard page I can bring anywhere that has various sets
- A Zhuyin trainer
- A tool for showing character by character pronunciation to help while reading

Other tools and useful things
- Google Translate and Pinyin Conversion integration so writing flashcards is just copying characters
- A PDF generator for printable flashcards
- It's very easy to ask an LLM to generate flashcards for a CSV in VSCode

## Why Traditional Characters

Most Mandarin learning resources focus on Simplified Chinese, which is used in mainland China. Taiwan uses Traditional characters, which are more complex but also more visually meaningful — many characters retain the pictographic or ideographic logic they were built from. <!-- AMAZON: Textbooks: Integrated Chinese or A Course in Contemporary Chinese (Taiwan) --> I'm learning Traditional because I spend time in Taiwan, so most off-the-shelf tools weren't quite right for me. <!-- AMAZON: Writing Practice: Water-tracing cloth for character practice -->

Writing a converter from Simplified to Traditional was one of the first things I built. It's not perfect, but for flashcard generation it works well enough. 

## Zhuyin

Most Western learners use Pinyin (romanization) to learn pronunciation. Taiwan uses Zhuyin, a phonetic system made of 37 symbols that map to sounds in Mandarin. <!-- AMAZON: Zhuyin Keyboards: Silicone keyboard covers with Zhuyin/Bopomofo --> Learning Zhuyin is extra work upfront, but it pays off because it's how Taiwanese dictionaries, children's books, and phone keyboards are organized.

The Zhuyin trainer is a simple drill: a random character is selected and only the Zhuyin pronunciation is shown. Clicking reveal shows the character, but more importantly, the romanization.

## Keeping It Simple on Purpose

The deliberate choice to avoid a backend has held up well. The flashcard sets are plain CSV files. Adding new vocabulary is a matter of adding rows. There's no database to manage, no auth system to maintain, no server bills. The whole thing lives in a GitHub repo and deploys for free.

The one thing I'd add eventually is offline support — a PWA cache so I can drill flashcards on the subway without a connection.