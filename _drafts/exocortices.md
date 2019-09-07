---
title: Exocortices
author: Mordecai
layout: post
tags: organization exocortex
---

At some point, everyone who deals with knowledge for a living in some form, will
stumble into the problem that they forget more than they really want to, and
rack their brains trying to remember what insight they had a week ago while
reading that one paper they found in some reference section.

I tried to stop the continuous forgetting of information that I would need
later, but it turns out that typically information is not the part you end up
missing - You can always search for facts - but insight is something you dearly
miss. . Serialising insight is a lot harder than just noting down facts, and
thus also less often done. We can make this process a little easier by
constraining the audience: Making something understandable to everyone is
intensely difficult, as any teacher will tell you. Making yourself understand
something in the future that you already understood in the past is doable. If we
then take this idea a little further, and rely on our ability to re-understand
something from material we left behind for ourselves, we can then forgo trying
to keep it in our heads. (It will remain in our heads, due to spaced repetition
when revisiting the material, but we no longer have to concern ourselves with
keeping it there.) With all that newfound mental space we gain from no longer
having to strain to remember the details of how our ideas relate to ideas that
we read about, and the consequence of synthesising the two, we can turn to the
thing we set out to do: Gain more insight into our fields of interest.

What I'll set out below are some of the things I found while assembling a
mechanism for writing and consuming such memory-aiding material. I went through
four iterations of such mechanisms, a personal wiki in Gollum, a set of
semantically-named markdown files in a folder in Dropbox, a pile of index cards
with nothing digital about them, and now, a set of numerically titled `org-mode`
files in a folder in Dropbox.  This is the first iteration that is sticking in
my habits and my mind insteda of becoming a graveyard for thoughts, so I thought
I'd write up what I found.

At last, a request for help: I know of the existence of the field of
metacognition, but I know not where to start. If you know of resources related
to this, or that you think I'd be interested in based on this post, please do
let me know via one of the means listed in the footer.

## The concept for an Exocortex

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

(Thanks to Elly for coming up with the term 'exocortex'. It's a far better
one than I could have come up with.)

## Upsides and downsides of an exocortex

So why should you do this to yourself, why take the responsiblity for thinking
and fermenting thought away from your head, and entrust it to a system imposed
on text? Well, there are a bunch of reasons why you would **not** want to do
that.

The most impactful downside to having and relying on an exocortex is, put
simply, you're screwed when it's not there. It's a structure you come to rely on
heavily, for thinking and composing ideas, and that makes it hard to work if it
isn't present. This, originally, was the reason for writing my version of a
plain-text-based exocortex. I forgot my index card based original structure on
the way to the library and, well, had to go back home, grab it, and go back to
the library before I was actually able to do the thinking I originally
wanted. The same problem, but more severe happens when you lose it, it will take
a long time to reconstruct, if you ever fully do.

I 'fixed' (worked around, rather) this by moving to a digital version that uses
a series of plain text files in a synched file folder (Dropbox or Syncthing,
whatever you already have set up), which makes sure I don't forget it. It does
come with the (smaller) downside of not being able to use it without a computer
that is appropriately setup.

The biggest upside to adopting an exocortex for thinking, to me, is being
"forced" to write down any idea I consider worthwhile. This forces you to put
your idea and insight into words, and write it out in such a manner that you
will be able to understand it later. This will often make you realize what the
holes in your idea are, where you have to go look for other ideas that will plug
this hole, and why an argument may simply not be valid. In a way, the difficulty
of serialzing insight is what helps us here. (The effect of "being forced to
explain what you think makes you realize if you actually understand something"
is also popularly known as the Feynmann Effect.)

This also makes your thinking interruptible. If you write down every idea and
insight about said ideas you have, an interruption will not break down grand
mental castles of insight that you will need to painfully reconstruct. This is,
to put it mildly, incredibly valuable in the open-plan offices that are the norm
today. I dislike being interrupted as much as the next person in flow, but since
it's a reality of the modern office life, we might as well build systems to
mitigate the impact they have. The ability to just put down your work, and go do
something that is important elsewhere is an amazing capability in modern
offices. There is also, of course, a wonderful [Hamming
quote](https://gist.github.com/b3d44ed936ce863f2232145d85019d01) for this.

Thinking-by-writing is, in my opinion, an underutilized tools for finding
logical holes early, forcing yourself to put your thoughts into words at all
times is a very simple tool to be able to share your thoughts, get feedback on
them faster, and makes you see the holes in your logic as soon as you come back
from lunch, glance at your notes and realise why your planned approach won't
work before you're halfway through implementing it.

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

## Inspiration and Attribution

To the people who have been around this particular block will notice I'm not
proposing anything new here, nor am I proclaiming to do so. This concept is
based on the Zettelkasten proposed in Ahrens' book *How To Take Smart Notes*,
which itself takes principles and ideas chiefly from German sociologist Niklas
Luhmann, but also from authors who utilized a similar techniques like Vladimir
Nabokov.

For technological translations of this methodology that was originally based on
index cards, see [The Archive](https://zettelkasten.de/the-archive/). This is
the most faithful digital translation of the Zettelkasten method. I wrote an
Emacs based alternative for myself, `org-kasten.el`, based on my experiences and
shortcomings found when using a purely paper-based workflow.

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
