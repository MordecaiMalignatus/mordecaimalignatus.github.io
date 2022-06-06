---
layout: post
author: Mordecai
title: "Dimensionality And The Unbearable Size Of Systems"
categories: post
---

Dan Luu's [excellent post about how things "look easy" to build][dan-luu] has
posed something of a vexing mystery to me: Why do people, whose entire
(well-paid) job it is to build complex systems, insist and opine that something
must be easy to build? To quote:

> [...] But in the comments on Alex's posts, multiple people respond and say that
> Lucene basically does the same thing Google does and that Lucene is poised to
> surpass Google's capabilities in the next few years. It's been long enough
> since then that we can look back and say that Lucene hasn't improved so much
> that Google is in danger from a startup that puts together a Lucene cluster.
> If anything, the cost of creating a viable competitor to Google search has
> gone up.

I believe I have a reasonable guess at why that is: The "depth" of a system is
hard to see, while the "width" is relatively plain.

To elaborate on what that actually means, let's look at the environment Google
exists in. The world at large, that meaning society, our planet, the
interdependences of the various individual systems, is unfathomably complex. Luu
brings up some of the stumbling points for someone trying to build a competitor
to Google's search: Latency, speed, various alphabets that aren't always the
same, indexing, making something easy to use even when that means being
inconsistent, and so on. We can reasonably say that for all intents and
purposes, environmental complexity of any system approaches infinity. For
everything we consider, there's additional corner cases to take into account,
things that could happen that would change the outcome, or make the system not
work as intended. The main reason we don't consider solar rays flipping bits in
our RAM as a top-level engineering concern is that, for _most_ (but, crucially,
not *all*) applications, it does not have enough impact to make the cut for
"being worth addressing".

Luhmann[^6] has given the only definition of "complexity" and "managing complexity"
that I've found to hold up. To summarise: Complexity is the amount of input
variables that you consider for deciding what you will do. Low-complexity
systems are narrow `if` statements, they look at one or two input variables and
decide the course of action. Of course, not much of the world is represented (or
able to be represented) in one or two input variables, and much of it has to go
unrepresented.

"Managing complexity" is then having input of a certain complexity and
*selecting* a sensible, reasoned action from it. The more complexity you have at
hand, the more "selectivity" you need. Humans, by themselves, don't have much of
this selectivity. We have trouble choosing what to eat for dinner. We have and
build systems because they allow us to increase our selectivity, and therefore
manage more complexity, and with it, deal with more of the world.

The larger the part of the world your system needs to handle, the bigger it
needs to be. While the main point of a system is that it *reduces* complexity
from the environment, that stays true for a surprisingly long time. Much like
engineers in Luu's essay, additional size in the system to handle more of the
world pays for itself for a surprisingly long time, but not indefinitely. A
system handling all and every edge and corner case is a map with scale 1:1, and
with it, a bit worse than useless. The benefit of systems comes from _choosing
to not handle_ some cases.

Let's call the "depth" of a system the proportional amount of the complexity the
system handles in a given domain. That means, how well does it actually do that,
how well does it deal with edge cases, how many of those does the system
address? Domains have varying depths, and so do systems. A system like Google's
search is a particularly deep system for a deep domain, text search.

In contrast, the "width" of a system is then how many problems it claims to help
with. Some domains are wide, like "efficiency", some are quite narrow, like
"text search".

For a lot of systems, a rule of thumb therefore holds: If you see a system that
is particularly wide without being also appropriately large organisationally, it
won't solve many of the problems of the domain. This is the "feature factory"
problem, where, because you can say your system addresses a domain, you qualify
for a binary test, but how *well* you address that domain is never tested.
Google's search is perhaps the inverse of that, where an extremely large set of
resources is allocated to present a single input box to the user.

The mystery starts to unravel a bit once realise that it's relatively easy to
gauge the width of a system when you're far away from it (i.e., not working on
the domain it claims to help with), but the depth is, for all intents and
purposes, impossible to gauge without having first-hand experience.

Additionally, there's a quite elementary rule regarding complex system, most succinctly
delivered by John Gall's _Systemantics_[^5]:

> A complex system designed from scratch never works and cannot be patched up to
> make it work. You have to start over, beginning with a working simple system.

You can't skip the stages where the system only handles a small slice of the
actual domain complexity. For every working complex system addressing a deep
domain, there will be others that are not yet quite as large, and therefore
handle less of the domain, than others. An example here would be DuckDuckGo, it
handles less of the domain of internet search, but works better for some cases.
(or otherwise it would not exist, and people would use the larger, existing
system instead.)

We can't actually gauge the size or complexity of a *system* without being
involved in it, and we can't gauge the depth of a *domain* without having worked
on it.[^3] But we do have proxy measures: Engineering headcount[^1], company
revenue[^2], interface design. With these proxy measures we can have a
reasonable guess at whether or not the system is going to solve the problems we
care about[^4], and with it, if we would be well-advised to use it. But this is
hard, very hard. Choosing "what system do I best use to solve my problem" is the
entire reason for companies like Gartner to exist. They're not often even close
to correct, but they provide _an answer_ and that's more than most people have.

Domains and problems may look easy, but then again no mountain looks _that big_
when far away, but you sure feel every meter of height when climbing it.

---

[^1]: My pet theory is that some companies, notably Coinbase, previously, Uber,
    and more recently, Fast (which prided itself on its hockey-stick growth...
    **_in headcount_**, shortly before imploding), realise that these are seen
    as proxy measures for how well the domain is addressed, when in reality,
    they're just grossly overstaffed. This way they pass an initial smell-test
    for "can this company do what they claim to do".

[^2]: You can accuse Salesforce of many things, but you can be certain that
    their product works for a great amount of the domain they deal with,
    otherwise they would not have the business they do. How *well* it works for
    those problems is a different matter, but it does address many of the hidden
    corner cases adequately.

[^3]: For a quick and good demonstration of this, read these articles:
    [patio11's "Falsehoods Programmers Believe About Names"][patio11], [qntm's
    "So you want to abolish time zones"][qntm], and this video of [Tom Scott
    going mad while explaining why programmers hate time zones and
    dates][tom-scott].

[^4]: People with prior domain experience are much, much quicker at assessing
    this. They know where the corner-cases are that are important, but won't
    seem that way without knowing the domain in detail. For one step further,
    read [this story from Joel Spolsky about his first Bill Gates review][joel],
    where Gates is assuaged by Spolsky pointing out precisely which corner cases
    it *doesn't* handle, something you'd never think to point out if you weren't
    intimately familiar with the domain.

[^5]: Which is an undying book, only getting more and more relevant, and never
    less. I highly recommend you give it a read.

[^6]: These days perhaps more famous for his Zettelkasten, he was also an
    incredible sociologist that I can't shut up about, because much of his
    writing explains so much in so few concepts.

[dan-luu]: https://danluu.com/sounds-easy/
[patio11]: https://www.kalzumeus.com/2010/06/17/falsehoods-programmers-believe-about-names/
[qntm]: https://qntm.org/abolish
[tom-scott]: https://www.youtube.com/watch?v=-5wpm-gesOY
[joel]: https://www.joelonsoftware.com/2006/06/16/my-first-billg-review/
