---
layout: post
author: Mordecai
title: "Software As Brain Prosthesis"
date: Mon, 22 Nov 2021 08:40:08 +0100
categories: post
---

I learned programming after I figured out that a chief obstacle to me doing
something I wanted to do was how janky it was to do. First I used spreadsheets,
then I picked up Python after I got frustrated with spreadsheets not being very
good with letting me do dynamic input. I started writing small tools for myself,
tiny, one-off specialised tools and scripts that had no audience but myself. The
common thread was compensating for something I thought I should be able to do,
but was not.

Programming, in that way, had become a way I could mitigate my brain's blind
spots. I have a bit of a different-than-normal (as far as I can tell, anyways)
relationship to my head, with the PTSD and the ADHD and all, where it's more of
a dialogue. What do we need to have in order to do the thing, and why are we not
there? How can we bridge that gap?

I think this is something that people (especially programmers) don't commonly
appreciate: The most helpful part is to be able to help yourself. To construct
prostheses for your mind. To help things that may not be running as smoothly as
they could. A lot of things in my life run through an unflattering, janky,
pipes-and-duct-tape setup of custom scripts, tools, inputs, triggers and sinks
that keep my life running.

I want to show some of the janky things I've built for myself, in the
probably-vain hopes somebody gets Ideas™ and starts helping themselves. As
such, a short tour of the things that keep me running.

## Spending Queue (sq)

The [Spending Queue](https://github.com/MordecaiMalignatus/spending-queue) is a
small CLI application that looks like this in your terminal:

```
~ sq
Currently available free budget: $22.24
The next item in the queue is Moka Induction Pot (4 cups) for $33.58
```

It takes a budget (money per time), and a list of stuff you want to buy. It
prorates the budget over time and tells you when you can buy the next
thing. That's all it does.

This is very useful for me, because I forget to do nice things for myself. The
README has a bit more information, but it's very much because I'm bad at doing
nice things for myself. Having a nice thing come in once a week or two brings me
an outsized amount of joy, for a little bit of book-keeping and 100€ per month.

## Work Music

[This is essentially a
`Rakefile`](https://github.com/MordecaiMalignatus/work-music) that I use for
managing the music I listen to when trying to focus. It keeps a small database
of Youtube links, downloads them, rips the audio tracks from the videos, and
then gives you a small interface to pick one or play one at random.

I tend to like DJ sets, I tend to like electronic music. Listening to things on
Youtube is okay, but janky and does not work when I'm places without
internet. So, I just rip them instead. Curating this list and finding new mixes
is a little spark of joy as well. The curious can glance at the `dl_store.csv`
file to see what powers my daily work life.

## Checklist Stepper (cls)

A [rather new addition](https://github.com/MordecaiMalignatus/checklists), `cls`
is something I've wanted to build for a while. It is, like basically everything
else on this list, incredibly simple: It takes a bunch of lines of text, and
turns them into a checklist.

It's probably easiest to demonstrate:

<video width="100%" controls src="{{ '/assets/cls-demo.webm' | relative_url }}" type="video/webm"></video>


I essentially use this to keep myself on track in linear, boring processes. I
can forget at which point I was in a process and not have it matter. I can
remember to do the boring stuff like make tea and brush my teeth even before any
medication kicks in. Its simplicity also means that I can have a bunch of these
up in `tmux` or something and keep my head on straight while coordinating
parallel processes. Its simplicity also means that I can generate the steps as
output of some other script and use `cls` in the vein of `fzf` and other "nuts
and bolts" tools.

## OmniFocus, Hammerspoon, Emacs and the rest.

A lot of other things are held togehter by a combination of those three
things. OmniFocus essentially runs my life and I have accepted that that means
I'm buying apple devices forever.

Emacs is fantastic because it follows the exact sort of, "if you need it to work
differently, you can make that happen" ethos that has pushed me to learn how to
program in the first place. I cannot, in good conscience, recommend others learn
it though. It is archaic, difficult and hard to make friends with. Once you do
that though, lots of wonderful stuff happens. I've also written a bunch of
software for it that I use in similar capacities as the rest of this
list. ([org-kasten](https://github.com/MordecaiMalignatus/org-kasten), my
knowledge base implementation I use for writing, and
[cheatsheets.el](https://github.com/MordecaiMalignatus/cheatsheets.el), a really
simple package to remember and look up language-specific things.)

Hammerspoon is just a really neat utility that makes macOS a bit more
customizable and bridges some UX gaps.

I use a lot of `rake` in my daily work, not for anything it was originally built
for but because it gives me a CLI without much work and I can use real functions
in it. It doesn't compose great and it has a bunch of issues, but it ships with
every Macbook and lets me forget complex commands.

To wrap up, writing your own custom tooling to fix your specific brain is
something that brings me outsized joy in programming. It allows me to compensate
for the parts my brain is bad at without creating other deficiencies. The nice
part is that over the years, you will accumulate a toolbox that you can re-use,
reconfigure and then apply again to solve a different problem. Your solutions
are specific to you, and being able to make your own when nothing else fits your
needs is the ability I'm the most proud of having.
