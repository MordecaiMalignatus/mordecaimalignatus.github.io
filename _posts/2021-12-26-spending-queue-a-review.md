---
layout: post
author: Mordecai
title: "Spending Queue: A Review"
date: Sun, 26 Dec 2021 17:31:39 +0100
categories: post
---

A while back, I wrote about my idea for [a simple spending
queue](/2020/06/18/decoupling-purchasing-and-joy) that I then went and
implemented. You can find the current implementation that I use every day
[here](https://github.com/MordecaiMalignatus/spending-queue), it's a small
terminal application we'll look at closer in a bit, but first:

## Review of the effect.

I honestly did not think that it would make much difference, but it absolutely
does. It has made me happier, noticably so. It avoids serveral pitfalls that I
have fallen into before:

- I set aside a separate budget for this in specific, but without proration or
  keeping of a list. The money accumulates forever because I never have any
  nudge to spend it on things.
- I keep a list, but no proration happens. Every end of month I buy the stuff
  from the list based on the budget available. This is better, but it still
  batches things in a way that feels like a financial maintenance chore: I do my
  budget, I buy the things.

This way, these small things are spaced out over time, and I get little
irregularly sized nice things. They're not grand luxuries (see list below), but
the fact that it is explicitly a small splurge for me makes it better. That's
all there is to it.

## The Mechanism.

You set aside a fixed amount of money per certain time interval (personally,
mine is set to $50 per 30 days). Then you add some stuff that you want to have,
but always feel a faint niggling of guilt for, something that it's something you
don't strictly need and could do without. Then you wait. The status is displayed
when you call `sq status`. Since that's something I have to explicitly do, I
have a block in my shell `rc` that calls this whenever a TTY is launching a new
shell.

About halfways through, I implemented a feature that kept track of the things I
bought with this method, so here's about half of my list since I started keeping
track of this in earnest:

```
 Name                        | Cost   | Purchased
-----------------------------+--------+---------------------------------
 A4 Leuchtturm Notebook      | $27.50 |
 Hardspace Shipbreaker       | $25.00 |
 The Power Broker            | $18.99 |
 Peugeot Pepper Mill         | $35.50 |
 Pyrex Measuring Jugs        | $31.54 |
 Moka Induction Pot (4 cups) | $33.58 |
 Cake Stand                  | $12.90 |
 Parker Jotter               | $5.73  |
 Scalpel                     | $9.99  |
 Wuesthof Vegetable Knife    | $79.00 | Sun, 26 Dec 2021 17:07:41 +0100
 Visa's FAN                  | $10.00 | Sun, 26 Dec 2021 17:14:31 +0100
```

*Note: Another bug ate the purchase dates, but between the rate ($50/mo) and the
amounts listed, you can figure out the spacing.*

Once the accumulated balance ticks over the pricepoint for the next item, `sq`
will display that you can buy the next thing. `sq buy` opens the purchasing page
you saved when entering the item, lets you buy the thing, then asks if the price
still matched. The item is bought as marked, and the process begins anew.

## The secondary effect.

The more notable bit of this experiement succeeding so resoundingly is that it
has given me insight into two more things, namely: I can build things I can't
find already existing, and I have agency over these things, and how they
intersect with my life.

Running a small experiment like this that directly tinkered with how I relate to
life makes me feel more confident in my agency over how I interact with life. I
consider this, the building of tools that shift your interaction with the world,
a skill that I intend to hone, and get _better_ at. Earlier today I had [an
insight](https://twitter.com/m_malignatus/status/1475063733256916993) with how
many things are skills, even/especially if they are not commonly practiced. I
think this falls _exactly_ into this niche. Building things that tinker with
your interaction with the world is an extremely valuable skill that I don't
think is on many people's minds -- and I fully intend to become good at it.

I can only encourage you to do similar things: Your interaction with the world
could be different, and you could make it easy enough to interact that way that
it supersedes the default way with something that feels better.
