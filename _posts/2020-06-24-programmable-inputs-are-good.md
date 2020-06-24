---
layout: post
author: Mordecai
title: "Programmable Inputs Are Good"
date: Wed, 24 Jun 2020 15:01:42 -0500
categories: notebook
---

Yesterday, I flashed my keyboard with some new firmware. Now, holding the `a`
key acts as Meta/Win/Cmd signal. I did this because my keyboard had no easy
acces to said modifier on the left side of my keyboard, making me rely on the
right side a lot more than I wanted to. I own an excellent
[Ergodox-EZ](https://ergodox-ez.com/), and while the mechanical parts are nice,
the main benefits are 1) the ergonomics of it, and 2) the keyboard itself
running [QMK](https://docs.qmk.fm/#/), a firmware for keyboards usually utilised
by the hobbyists that are soldering and building their own keyboards from
scratch. The graphic configuration tool supplied with the Ergodox is the cherry
on top.

This reminded me of [a good thread on
Twitter](https://twitter.com/hillelogram/status/1252729449084145666) (by Hillel
Wayne) about why modal editing is good: Because it frees most of the keys that
are taken for inserting letters, and turns them into a hundred arbitrarily
programmable buttons instead. He also acknowledges vim itself falls a little
short of that goal, as you're stuck with the seven-or-so modes it ships with.

QMK, also, can turn a keyboard into a hundred buttons, not by creating modality
in software, but by implementing them in the keyboard, and thus having the modes
where you so want, no matter what the software underneath may conceptualise as a
normal keyboard. The most important insight here is not how precisely you
achieve having a hundred buttons, but that it's *possible*. You can do the same
with AHK, or Hammerspoon, or running Emacs for everything. QMK customisation
means that I can rely on it being there for all machines I can plug my keyboard
into in some form. I guess what I'm saying is, the next keyboard, should this
Ergodox die, is going to run QMK in one form or another.

The biggest issue, by far, is actually creating the actions that happen when
those 100 buttons are pressed. This takes significant time and
effort. Sometimes, someone already did it for certain domains (the main one that
comes to mind is the amazing [Magit](https://magit.vc/), which turns your
keyboard into a hundred buttons for `git`), but usually, you'll be on your
own. Then it's about thinking really hard what precisely is needed. I'm not too
sure what I'd do with a hundred buttons for writing notebook entries, but I'm
slowly writing bindings for the tasks I usually need, like spellchecking,
previewing, commit/build/push, and so on.

PS: Rixx' [notebook aggregator](https://notebooks.rixx.de/) is wonderful and has
me contemplating writing a specialised, hard-coded version of RSass for just the
combined feed. Will publish if it becomes a thing.
