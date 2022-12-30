---
layout: post
author: Mordecai
title: "Diagnosis Problems and Decision Problems"
categories: post
---

A relatively large amount of trouble in figuring out how to solve a problem can
be avoided by not treating diagnosis problems as decision problems, and not
treating decision problems as diagnosis problems, even if they are generally
similar.

A *Diagnosis Problem* is something where a definite cause for the behaviour of a
system exists and is in fact causing that behaviour. The trouble is finding it,
and diagnosis is about doing so in a timely and, most importantly, correct manner.
Often times this is not a singular cause, but a set of only jointly sufficient
substates, where changing any of them makes the larger problem go away.

A *Decision Problem* is that you have an outcome you'd like to achieve, and many
ways of getting there. You have to pick one, because you can't do multiple
things at the same time without them getting into each other's way. The problem
is typically about which way *the best* way of getting there.

Generally speaking, you can convert one into the other, and various framings of
the same problem will generally exist, but the framing has significant impact on
how a solution is sought and found.

Confusing a decision problem for a diagnosis problem results in a lot of small
experiments to test the waters, and being confused when all of them cause a
reaction in the system, usually in the direction you intend to go. There aren't
a lot of "misses" in walking in an open field, and it can result in paralysis as
you try to figure out "the best way" to get to your destination, ignoring that
the outcome is signficantly more important than the understanding of every step
along the way. This is the lesser of the two complications.

On the other hand, confusing a diagnosis problem for a decision problem often
results in removing the larger-scale problem without understanding why it
occurred, leading to simple solutions that *work*, but misunderstand the
problem, the solution, and the situation. An crude, exaggerated example here
would be to buy a new car when your old one runs out of gas. The problem is most
definitely solved, you have a functioning vehicle again, but the solution is...
not ideal.

Of course, often times, "a solution that works" is all you really care about.
The entirety of why Erlang is very good at producing reliable applications is
*because* it doesn't much care about what went wrong in what way, it shrugs and
restarts that part of the application. "A working solution" is already a very
good thing, and not to be scoffed at.

Diagnosing the exact cause and method of the symptom is expensive. Shrugging and
discarding the information of the path to the problem is often the right thing
to do, cognitive resources are scarce and considerably more expensive than, say,
making computers do more work. But that stops at a point, most notably when
safety is involved. Here, figuring how and why the system at large works is no
longer optional, but deeply important. The nature of the symptom is one that
can't be allowed to recur, so understanding the nature of the problem, the
system, and the solution and their respective consequences is crucial.

This points to a larger friction in organisations and systems, where for some
people, a problem is a diagnosis problem, and for others, it's a decision
problem. A manager will not care *why* a service keeps going down, only that it
stops going down. An engineer will care a lot as to *why* it goes down, because
otherwise they will have to mitigate that problem over and over again, and that
is boring and expensive.

Figuring out who is invested in what part of the problem can save you a lot of
trouble.
