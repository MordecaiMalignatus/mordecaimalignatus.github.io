---
title: Exocortices
author: Mordecai
layout: post
tags: organization exocortex
---

# What they are and their implementations.

At some point, everyone who deals with knowledge for a living in some form, will
stumble into the problem that they forget more than they really want to, and
rack their brains trying to remember what insight they had a week ago while
reading that one paper they found in some reference section.


- This is the fourth iteration of this idea, after each previous one was
  scrapped for not working and not actually assisting my thought process.
- This is looking like the first time it's sticking and working out correctly,
  so I thought I'd write about it.

## The concept for an Exocortex

- Thanks to Elly for the name.
- An exocortex is any structure authored by one person for the sole sake of aiding
  their thought process. Any such structure must be actively and heavily used in
  order to maintain its usefulness.
- It is meant to be an idea storage device, not a fact storage -- it is a text
  aid for your mind to remember ideas. You can store facts along side it, but I
  found them to distract and to be better kept in another archive, usually one
  sorted by problems.
- The ideas in an exocortex are not meant to be shared - you still can, but the
  primary audience is the person who wrote them, and I would not expect any of
  mine to be as useful to anyone else as they are to myself.

### Upsides and downsides of an exocortex

There are plenty of reasons not to use one, of course:

- It makes you dependent on your cortex being present for writing and for using
  it. This is a much bigger problem if you keep your cortex in index card form,
  and the original reason why I translated it to use plain text instead.
- You will be struggling if it somehow is lost, as a lot of thought is
  externalised to the cortex. This makes you quite dependent on having it
  there.

Upsides:

- My workaround to those two is to keep my exocortex in the most universal of
  formats: plain text in a synced folder.
- Writing about your ideas makes them a lot less liable to simply disappear on
  you. If you write down the ideas you have, your thinking also becomes
  interruptible -- you are less dependent on having long stretches of quiet time
  to achieve insight.
  - This is doubly valuable in today's environment of open-plan offices

#### Hamming

>I notice that if you have the door to your office closed, you get
more work done today and tomorrow, and you are more productive than most. But 10
years later somehow you don't know quite know what problems are worth working
on; all the hard work you do is sort of tangential in importance. He who works
with the door open gets all kinds of interruptions, but he also occasionally
gets clues as to what the world is and what might be important. Now I cannot
prove the cause and effect sequence because you might say, ``The closed door is
symbolic of a closed mind.'' I don't know. But I can say there is a pretty good
correlation between those who work with the doors open and those who ultimately
do important things, although people who work with doors closed often work
harder. Somehow they seem to work on slightly the wrong thing - not much, but
enough that they miss fame.

(from ["You and Your
Research"](https://www.cs.virginia.edu/~robins/YouAndYourResearch.html))

 - This effect is not unique or dependent on an exocortex but merely on
    thinking-by-writing, which you can implement without adopting an exocortex.

## Why personal wikis fail

One effect I have noticed in trying to implement this for myself is that
Wiki-like implementations (I have previously tried DocuWiki and Gollum, before
abandoning the approach) always eventually found themselves unused, vastly out
of date, or having duplicated, conflicting information everywhere. I'm
attributing this to a few things, like reliability, interface and fragility, but
most centrally, the average size of a page, or node in the graph.

I have a theory that you can maintain either one very large page, where you
gather all of your information/ideas/notes in one file and use text search,
structural parsers and file-internal links to navigate (see: the `notes.md`
files I know a lot of people to have), or you can maintain a bunch of tiny pages
and use tooling for navigation and structure (see: my `org-kasten.el`). I do not
have any evidence for this past musing over failed attempts of myself, though.

Wikis on the other hand encourage a medium sized collection of medium-sized
pages, where you are encouraged to put further context with an idea. Navigation is
comparatively clunky, as you have to hunt for the links in the text. Pages
usually contain clusters of ideas which sometimes are actual clusters (where
every idea is related to all others on the page) and sometimes they are
insight-chains: A relates to B which is basically like C and can be likened to
D, but A and D have nothing to do with each other. Insight chains are part of
the reason I have found wikis to fail - it becomes very hard to ever find D
again when you have an idea that relates to D, as page it is contained in (A) is
only tangentially related to D.

Wikis are excellent if you have a larger community and people that will refactor
inconsistencies and create categories, links, and portals. The du jour example,
Wikipedia, is one of the most wonderful creations of the modern age. But you are
just one person, trying to remember what a Monoid was and how it relates to a
Semigroup. You have limited capability to fix inconstencies and perform wiki
maintenance, and so you eventually don't. The cruft accumulates, the wiki
becomes unused, the knowledge in it, lost.

## Inspiration

- How to take smart notes and the works of Luhmann.
- I am not really inventing anything new here, I'm just providing an alternative
  tool to transport Luhmann's and Ahrend's ideas to files. For other
  translations, see [The Archive](https://zettelkasten.de/the-archive/), which
  is another translation of roughly the same method. My method diverged a little
  as I developed it, which makes The Archive the more faithful translation, as
  far as I am able to tell.

## The simplest structure that could still work

- Very small nodes require tooling to reduce friction, else your pages will
  become larger again. The index card was the initial medium for a reason, it
  kept node size small by design.
- Small nodes enable page-centric links, rather than explicit links in the
  text - as long as one page represents one idea, the links to each page
  directly relate to said idea, enabling much easier navigation -- nothing has
  to be found in the text to follow.
- Sorting by topic/semantic grouping is actively harmful as the clustering is
  context-dependent.
  - Example: If you are looking for similarities across topics rather than at
    the problems in one topic, a clustering by-topic will hurt more than it
    helps, you have to fight the hierarchical structure to find your
    similarities. If you have loosely linked nodes, that kind of similarity is
    just another link.
  - This leads to an "exocortex maximalist" usage -- every idea that I want to
    remember/think about later goes into the kasten. If they are not what I
    want, the idea will still be there, just be traversed less and gradually
    forgotten for its lack of links. This is the ideal case.
- Sharp distinction between your ideas (notes) and other people's ideas
  (references) as they relate to your thoughts.
- System geared towards writing: References mean you have citations for your
  claims from your own reading.

## About this post.

This post, predictably, was written with my exocortex as main source of
arguments, points, references and mistakes. I would go as far as to
say that I did not do a lot of thinking for this post, the main points simply
fell out of traversing the exocortex for what I considered relevant, then
I drafted prose to connect the dots, and edited.
