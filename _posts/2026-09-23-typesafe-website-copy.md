---
slug: typesafe-website-copy
layout: post
date: 2026-09-23
title: Typesafe Interpolated Website Copy
description: A better dictionary for website text
categories: tutorial
image: /assets/posts/2026/typesafe-website-copy/interpolation-large.png
github: https://gist.github.com/pjflanagan/6062cb5a2e11579314a8df197e05d18d
website:
---

Websites are fundamentally about text. But dynamic websites can have very dynamic text. Managing an entire website worth of copy can be an undertaking. Catching a grammatical error isn't always as simple as `CMD+F`-ing it.

Consider this situation:

```tsx
export function Action({ isWhimsical, isPaypal, isPremium, isNow }) {
    const desireWord = isWhimsical ? "wish" : "want";
    const method = isPaypal ? 'your Paypal' : 'your card';

    const start = `If you do not ${desireWord} to pay`;

    return (
        <>
            <Button text={"Pay" + isNow ? 'now' : 'sometime later'} />
            <Asterisk>
                {start}
                {isPremium
                    ? `, close the window!`
                    : `, call ${isPaypal ? 'Paypal' : 'us'} to prevent charges to ${method}`
                }
            <Asterisk>
        </>
    );
}
```

There are things to go off of here, but this isn't good code. Imagine trying to change for a new situation.

> When strings live in the JSX, they become difficult to find, read, and edit.

It is usually better to have website copy live in one place, to make it easily trackable and changeable. We could make something like this:

```ts
export const Copy: Record<string, string> {
    'action.cta.pay_now': "Pay now",
    'action.cta.pay_later': "Pay sometime later",
    'action.asterisk.premium': "If you do not [[desire]] to pay, close the window!",
    'action.asterisk.basic.paypal': "If you do not [[desire]] to pay, call Paypal to prevent charges to your {aypal.",
    'action.asterisk.basic.card': "If you do not [[desire]] to pay, call us to prevent charges to your card.",
}
```

This allows us to easily read what each sentence says and check for grammar errors. There is more text to `CMD+F` here when we need to track down text. It also forces us to think about each situation we have unique text as a deliberate instance, rather than an amorphous sentence that can change shape. We can also still take advantage of interpolation if we would like to.

This is a good start, but it could be made better with typesafety. 

This tutorial will show you how to implement that.

## How to make a Typesafe Interpolated String Map

### 1. Create a map

Creating a map of keys to strings can be very useful. Let's make a map of keys to interpolated strings. We will be using `[[value]]` for our interpolation. (Note: The Github Gist uses curly brackets, but square cooperated better with Jekyll, this blog's framework).

```ts
// Copy.const.ts
// This file will hold all of our copy for our website

export const CopyMap = {
  'page.title': 'Your Cart',
  'page.subTitle': 'Welcome to your cart [[name]]',
  'recept.line': '[[itemName]]: $[[itemPriceInRoundDollars]]'
} as const;
// CopyMap must be `as const` so the keys can become a type
```

### 2. Create a util function

It can be even more useful if it is interpolated and typesafe. Let's make a util function for accessing our data.

```ts
// Copy.ts
import { CopyMap } from './Copy.const';
import { CopyArgs, CopyKey, InterpolationValue } from './Copy.types';

const PLACEHOLDER_PATTERN = /\[\[\s*([^}]+?)\s*\]\]/g;

// This is our util function that we will use to locate and interpolate website copy
export function getCopy<K extends CopyKey>(key: K, ...args: CopyArgs<K>): string {
    const copy: string = CopyMap[key];
    const [interpolationData] = args as [Record<string, InterpolationValue>?];

    if (!interpolationData) {
        return copy;
    }

    return copy.replace(PLACEHOLDER_PATTERN, (placeholder, name: string) => {
        const value = interpolationData[name];

        return value === undefined ? placeholder : String(value);
    });
}
```

### 3. Make types

Now, let's make it typesafe by creating a type for `CopyKey` and `CopyArgs`. This is the complicated part.

```ts
import { CopyMap } from './Copy.const';

// CopyKey is simple enough
export type CopyKey = keyof typeof CopyMap;


// CopyArgs requires us to observe the string itself

type TrimLeft<S extends string> = S extends ` ${infer Rest}` ? TrimLeft<Rest> : S;
type TrimRight<S extends string> = S extends `${infer Rest} ` ? TrimRight<Rest> : S;
type Trim<S extends string> = TrimRight<TrimLeft<S>>;

type Placeholders<S extends string> = S extends `${string}[[${infer Name]]}${infer Rest}`
    ? Trim<Name> | Placeholders<Rest>
    : never;

export type InterpolationKeys<K extends CopyKey> = Placeholders<(typeof CopyMap)[K]>;

export type InterpolationValue = string | number;

export type CopyInterpolation<K extends CopyKey> = Record<InterpolationKeys<K>, InterpolationValue>;

type LooseInterpolations = Record<string, InterpolationValue>;

type UnionToIntersection<U> = (U extends unknown ? (arg: U) => void : never) extends (
    arg: infer I
) => void
    ? I
    : never;

type IsAny<T> = 0 extends 1 & T ? true : false;

type IsSingleKey<K> = IsAny<K> extends true
    ? false
    : [K] extends [UnionToIntersection<K>]
    ? true
    : false;

export type CopyArgs<K extends CopyKey> = IsSingleKey<K> extends true
    ? [InterpolationKeys<K>] extends [never]
        ? []
        : [interpolationData: CopyInterpolation<K>]
    : [interpolationData?: LooseInterpolations];
```

### 4. Call it

Now let's see it in action. Call `getCopy` and see that it has type safety.

![Suggestions when calling getCopy for keys](/assets/posts/2026/typesafe-website-copy/key.png)

![Errors when calling getCopy with missing interpolations](/assets/posts/2026/typesafe-website-copy/interpolation.png)

### You're Done!

Now you can have typesafe interpolated strings across your site. 

On your own you'll have to decide how to name the keys. Usually something descending like `page.component.element.text.option` is good.

You might also want to consider making `getCopy` a per page util if `CopyMap` is getting too large. As for how you implement that, that's up to you.
