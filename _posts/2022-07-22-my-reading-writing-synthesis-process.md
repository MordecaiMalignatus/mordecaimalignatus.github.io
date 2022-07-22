---
layout: post
author: Mordecai
title: "My Reading/Writing/Synthesis Process"
categories: post
---

In a conversation with [David](https://twitter.com/drmaciver), the aspect of
precisely *how* I read books came up, in that it seems that I am relatively
uncommonly thorough in how I read the books I do, and that a lot of them have a
reputation for being either dense or boring.

The process below is how I read a very specific type of book, namely the very
dense academic non-fiction book. These are books that grapple with dense or
abstract topics, that are frequently dry and relatively boring, but that I find
tremendously worthwile to read. Some examples of these books are: _Behind Human
Error_ from Woods, Johannesen, Cook & Sarter, _Sorting Things Out_ from Bowker &
Star[^2], _Power In The System_ from Luhmann, _Tyranny Of Metrics_ from Muller.

Notedly, this is not for fiction, things read for general fun and amusement, or
fluff. This is a process that is optimised for *learning*, and if you find that
fun, fantastic. I am relatively sparse in which books I apply this process to,
and will often read lighter books with a much lighter process that boils down
to "scribble some stuff down and maybe read it later". For many lighter books,
that is plenty. Some of those books are, for example, _The Master Switch_
from Wu, _The Scout Mindset_ from Galef, or _Against The Grain_ from Scott.

## Goals and Non-Goals.

First, let's talk about the goals of this process. This is an unusually involved
process, and so it has specific goals. They are, quite simply:

1. Make my brain engage with the book in front of my face. This is what the
   dialogue is for. Being forced to rephrase, reformulate and argue with the
   points the author makes prevents my brain from slipping clean off the letters
   in front of my eyes.
2. Understanding and retention. I am terrible at "reading" a book very quickly
   and forgetting 98% of it. Most people report having 10% retention of books
   and a vague "index", ie getting a memory association that may not tell them
   what they are directly looking for, but tells them where to find it. I will
   wholesale forget books if I don't engage with them deeply.
3. Writing. This entire process is oriented around writing, around forcing vague
   and abstract concepts into linearised words that force me to actually think
   about what I *mean* instead of what I'm gesturing at. Sometimes the writing
   is even for others to read, because selfishly, I like talking about the
   things I find interesting.

Conversely, there's also non-goals, or things that I actively avoid optimising
for. If they happen, cool, if they don't, also cool.

1. Speed. I read terribly slowly. Some books take months for me to get through,
   reading 30-60 minutes per day. I have spent 2 months on a single 250 page
   book, and I'm currently on track to spend another 2 months on a 320 page
   book. I very much do not care about the speed. I am much more interested in
   digesting and dealing with the contents.
2. Ability to consider books by themselves. This is not something to *review*
   books on their own merits. This process is to pluck interesting insights out
   of them, and leave the rest behind. I will have *opinions* on the books I
   read, but not for their own, stand-alone merits. Instead the opinion will be
   formed by how many pieces it fits together inside the larger context of
   "books I have read".

## The Process itself.

To lay out the process, here's the simple version:

1. Read with a notebook and pen in hand, take notes of the points of the book,
   always paraphrasing, never quoting. Write plentifully and freely, treat it as
   a sort of dialogue with the author(s). Rebut their points, rephrase their
   arguments, insult them for overlooking something. Read for 30-60 minutes at a
   time.
2. Add a bookmark to the block of notes. I tend to use one mark per half-page of
   notes or so, with the average reading session taking three. This is purely
   for granularity. I use a single tin of [Book
   Darts](https://www.bookdarts.com/), which simultaneously doubles as my WIP
   limit. Can't have more outstanding note blocks than bookmarks.
3. As part of "reading time" (I tend to split mine halfways between actual
   reading, and reprocessing, with a bias towards reading), go over your marked
   notes, and rephrase/reconstruct them into a third medium. This can be a
   personal wiki, flat pages, pieces of paper, whatever works for you. The
   second transformation is the important bit. I use a custom tool for this[^1].
   Once you have transferred a block of notes from second to third form, remove
   the bookmark.
4. After transferring and transforming the second form (the initial,
   written-while-reading dialogue with the authors) to the third location, you
   will notice many sparked connections and ideas between what was already in
   the third location and those you newly entered. Write those out, too, taking
   care to develop coherent reasoning and noting where things collide.
   Contradictions are valuable here, contradictions means that something
   interesting is afoot. It's important to note that this writing is strictly
   [*internal*](on-internal-writing), and
   therefore you should employ all the shorthand you have access to.

Eventually, you will have more than enough things jumping at you that make you
think "I should write something more refined about this", and then you have a
free essay by taking all of your third-form writing, and just needing to polish
it slightly.

A important but unmentioned element is the delay between 2 and 3. Since I use a
tin of book darts for this, and most of them are typically in use, there's
about 2-4 weeks between writing the nodes and transferring them for a second
time. In the beginning I saw this as a bug, and that the delay ought to be as
small as possible, but over time it's become clearer to me that this acts as a
sort of spaced repetition: The delay between writing the dialogue and then
transforming them again makes the material stick better in your mind, especially
if you were generous in your notes and had quite a dialogue. I would recommend
at least one week delay. I think 4 weeks as I have right now is too long, and I
need to remove some book darts from the tin because of this.

A note on the fourth step: as your structure builds, the fourth step will take
up more and more of your time, as you notice more and more things to connect,
tie together, and write about. This is by design. Once it reaches a sufficient
maturity you can, in theory, decouple steps 3 and 4, though I've found that I
don't create sufficient internal connections and have a weaker grasp on the
domain. Therefore, I keep them together.

## Origins of the process

Originally this came from Adler's classic *How To Read A Book*, where he pleads
to never read without a pen in hand, but does not actually give any instructions
as to *what to write*. I winged it until I found something that worked for me,
which is exactly this, before I then smashed it into Luhmann's own process of
cultivating a third form in something external and persistent.

## Details Of Some Steps

### The Notebook Notes.

They look like this, forgive the hard-to-read handwriting:

![notebook based paper notes about Sorting Things
Out.](../assets/paper-notes.jpeg)

Bullet points, arguing with the authors, trying to figure out what they were
trying to get at. You can also see that I read 12 pages in 30 minutes.

### The Custom Tool

It's named [`org-kasten`](https://github.com/mordecaimalignatus/org-kasten).
It's an Emacs/`org-mode` based implementation of a fairly traditional
Zettelkasten, based closely on Luhmann's original design. It features a tree
structure, easy traversal of said tree structure, arbitrary one-directional
links, rapid editing, and a sense of place.

This is my persistent structure of destination, and the network effects can't be
underestimated. My rather small structure counts 1200 files, and I already have
way, way more topics that I could potentially write about than interest or time
for writing. Writing, however, feels good, and so every now and then I pick a
particularly interesting strand from the structure and write about it.

---

[^1]: Because of course I do.

[^2]: I currently can't shut up about this thing, it is so, so very good, and
    you should read it.
