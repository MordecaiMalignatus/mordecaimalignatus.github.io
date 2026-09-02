---
layout: post
author: Mordecai
title: "My Paper Filing System"
categories: post, fates
---

"How do I organise paper" seems to be a perpetual, vexing question of people
roughly my age, with them being digital enough to see the allure of not dealing
with paper, but realistic enough to know that they live in Germany, with paper
being more of an inescapable truth than something they can dodge.

The go-to solution among my nerdier friends seems to be
[Paperless](https://docs.paperless-ngx.com/), which is a document indexing
solution that does OCR, digital organisation, and has some features based around
automation. I... do not want to operate more persistent software. I have dodged
having a homelab for a while now[^1], and I don't really want to maintain
integral computer infrastructure for my personal life.

The other end that seems to be the common solution among my friends is "chuck
all of the paper I need to keep into a box. When I need a document, look through
the box." This is... pragmatic, and easy, but it does not fulfill my retrieval
needs of needing to be able to tell whether or not I have a document at all. I
relatively frequently find myself needing to check for possession without
needing the document itself, which this strategy just fails.

## My System

I ended up settling on the simplest system I could think of that works: A flat
text file, and some classic German binders with clear plastic sleeves. The file
looks like this:

```org
* File Archive III
- 076: [2023-02-27 Mon] State Farm annual 401k Savings Plan statement 2022-2023
- 077: [2023-02-27 Mon] Student Loans monthly statement.
- 078: [2023-03-14 Tue] Fidget Cube Drawing
- 079: [2023-03-17 Fri] Dentist bill, professional tooth cleaning on [2023-03-01 Wed]
- 080: [2023-03-20 Mon] iFixit stickers
- 081: [2023-04-03 Mon] Doc's note, burn-out illness [2023-04-03 Mon]--[2023-04-15 Sat]
```

A basic incrementing counter, a date of when the document was received or when
it was added to the file, and a brief description of what's inside.

This is complemented by a number of binders, with numbers on paper inserted into
the sleeves with the document in question, looks like this:

![./assets/binder-system.jpeg][A picture of a binder with several clear
plastic sleeves housing documents, with a number on a piece of scrap paper
inserted on the front.]


The straight-forward case is retrieval: Open the text file, search for some
keywords, find the file you need, open the binder it's filed under, then
retrieve the document you need.

Insert is the similarly simple: Take a sleeve, open the text file, add a new
line, increment the counter, add it to the binder with a piece of paper with the
number.

It's, I think, the simplest handling-documents system that can work, and it has
next to no overhead assuming that you have access to a computer in the same
place you hold your files. You could also store the text file in a service that
you can access on your phone, I personally just hold it as an `.org` file inside
my legally-distinct-Dropbox.

---

[^1]: Though that one will get me sooner than later, with "I run a bare Plex
    binary on my desktop tower" not being the best experience for anyone.
