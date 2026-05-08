---
layout: post
author: Mordecai
title: "The LLM Flood, As Seen From The Trenches"
categories: post
---

The influence and omnipresence of LLMs and LLM-based technology has accounted
for, on the lower end, 40% of what I see on what I'd call "the papers" for
people working in software in some capacity, sites like Lobste.rs, The Accursed
Orange Website, various Bluesky/Mastodon ecosystems. It feels impossible to
discern which parts of it are genuine excitement and discussion, and which are
puff-pieces, what part of it is skepticism at extra-ordinairy claims and what is
unwillingness to engage with a subject and finding reasons to dismiss it.

Well, I try to be a reasonable person, so as ~~mandates~~ strong encouragements
from corporate rolled in, issued from on-high, my work life began to be changed
by LLMs and related technology, whether I wanted that to happen or not. So,
let's talk about my personal, very specific point of view on LLMs and their
effects on software, engineering, and corporate culture.

First, it would be helpful to outline where I am standing, from where I am
casting this view. I work as a nebulously labeled "DevOps Engineer" in central
Europe, at a medium-sized company I would describe in this case as "solidly an
internet-based company, but boring", a solid C in terms of 'coolness' and
technological maturity. I say "nebulously labeled", because in practice it means
"tending to infrastructure", whatever that may be, and it's better defined as
"everything that does not belong to some product team". This generally involves
AWS and AWS-based infrastructure, mostly EC2 machines and EKS clusters.

So, now, from this perspective, what's the impact the ~~coerced~~ strongly
encouraged[^1] adoption of LLMs for software engineering as I have seen it?

## Impacts On Myself For The Work I Do

Adopting some form of LLM tooling has made some things easier, particularly the
writing of better-than-bash scripts for operations purposes and the writing of
CRUD APIs to glue together various tools that do not naturally come glued
together. This means that I can offload the reading of various API documentation
sites that may or may not be accurate, and focus on what I want to accomplish,
which I'll call an improvement.

I do not use LLMs for purposes of writing human-oriented documents, because it
takes longer to finagle the beige prose of LLMs into something good than it does
to write it myself, and it is much less fun. This is coupled with a lot of
people I respect growing increasingly allergic and disparaging (myself included
in this) to LLM-generated prose.

I have also derived great benefits from the research mode on various LLMs that
allow me to obtain answers to questions of knowledge that is available easily,
but usually not indexed in the way I want to ask the question. What I mean by
that is that I will ask a question 'backwards' from the way it's usually
categorized and presented in the literature, and previously I would have to
manually invert my question to obtain these answers. These days, I do not. This
is also an improvement.

On the downsides, the amount of text on the internet generated via LLMs these
days makes it hard to find worthwhile sources of information, all while tacitly
encouraging the use of LLMs to read that information. Needlessly verbose prose
can be summed up by an LLM just fine, even if I prefer to simply not read it at
all. Discerning which text is worth reading is now an important skill, and I
can't help but wish it was not so.

## Impacts On My Team

Most prominent is the effect of code being submitted and merged that is only
roughly understood. This *usually* the case without LLMs, but at least there,
somebody wrote it, with some intentions and towards some restrictions to solve a
problem. This is not the case with LLMs. It means that if I ask the submitter of
the code "Why did you write it this way?", I will not get an answer that may
hint towards a specific opinion or understanding, I will get "this was the
output and it seems alright", at best. This is annoying, because this was the
hook of some of the better discussions about implicit understandings in my
coworkers I had. This non-understanding of nuance on the side of the LLM is also
the cause of many subtle bugs I've seen, things that would not happen this way
if written without an LLM. This is considerations like "there's an ETL-based
loadspike at 3am so it there should be some sort of minimum duration for the
alert so it doesn't trigger every night at precisely 3am for 5 minutes". This is
something that LLMs account for in any consistent manner. They do *sometimes*,
when they look at the data, but this again then means that there is no real
intention or understanding of the patterns in the change.

The "this was the output and it seemed alright" answer has also made the quality
of submitted code drop, at least in my context. People do not want to fight the
LLM to output code in a different style or that is more to local idioms and
style, and so they accept what the machine spits out, so long as it works. In
general, the thinner-spread the team in question is, the more it will drop
relative quality, at least in my experience, as people prioritize getting things
done over doing them well, because they need to not drown *now*.

This also has a profound impact on new entrants to the industry, the people who
are currently doing the most learning of things they haven't internalized yet.
In my experience, junior engineers take to LLMs very frequently and very
intensely, because most of the time, being able to get an explanation *now*
rather than needing to wait for a coworker is immensely valuable for their
independence and ability to actually resolve problems, rather than being a net
drain on the throughput of the team. I don't think this is inherently a bad
thing, not at all. The issue comes with the self-discipline it takes to only get
an explanation, and not a solution. It is simple to go from "what does this
error mean?" to the imperative "fix the cause of this error", and that shortcuts
the learning process. Doubly so, if people start dropping the actual explanation
step, and go to the resolution directly.

The other impact I want to talk about is impact mitigation and resolution. When
things are *down*, people want to get things up and running again ASAP. More
than once have I seen people plug an error or a general description into an LLM
interface and give it more and more credentials until the LLM spit out something
that may or may not be related to the incident, and may or may not be a relevant
factor to the incident.[^5]

## Impacts On The Work Itself.

The "subtle bugs introduced by non-understanding of context" is an issue by
itself, but the increased speed means that the brains that do have the context
become saturated very quickly, unable to meaningfully pick apart the many
changes in a way that would allow for the catching of these subtle bugs.

A lot of noise is made in writings about review being the new bottleneck, but I
would argue that it always was. Reviews are, to me, not primarily a means of
catching bugs, but of spreading context. People who aim to automate the review
of changes with LLMs, to me, miss this point entirely. I read 80% of PRs posted
by my team, not because I'm required to do so for review purposes, but because I
want to understand what people are doing, how they are doing it, and what that
leads to. Working on a corpus of code collaboratively means sharing
understanding and context, and this is a dynamic disrupted by this.

The bigger problem is that writing code faster does not at all mean that you
accomplish your desired outcome faster, but now you have to justify additional
cost incurred. Or, somehow worse, you have to justify not adding additional
cost, even if it's the right thing to do if it would not at all help you
accomplish additional objectives.

## Social Impacts Of The Impacts On The Work Itself.

I have a hypothesis that LLMs have a much bigger benefit to you if you work
solo or with one other person on a team. The less understanding and context you
need to teach, the faster you can go with the LLM.

Because going fast is the thing that is rewarded most directly as an engineer,
it discourages collaboration. Collaboration means going slower, means spreading
context. That is not rewarded, see the age-old fight about Glue Work[^3]. The
introduction of LLMs has resulted in more PRs being submitted, but fewer than
ever being collaborated on, just an engineer and his LLM setup. Unless I
actively go out of my way to read PRs others submit, going against my own
incentives, it is easy to lose track of what people are doing around me, and to
understand it.

Many downsides of using LLMs for code generation can be mitigated by using
planning documents, sketching out architectures, discussing structure and
intentions. I had hoped that this would encourage people to do this, but it has
not. Instead people have simply tried to move past these things, generating them
with an LLM, rather than having any specific intention about it. To very little
of my surprise, this has not worked very well.

This also has interesting implications specifically on engineering managers that
came from the IC track, that long to build things again and not just wrangle
people and documents. It's been my experience that people in EM roles and
EM-adjacent roles have the most fun with LLMs, building things and not caring
about the code itself too much, so long as it does what they want. They are
usually not embedded in a team as a contributor, and this is not their primary
role. So they are building things, sometimes to address things they've seen be
problems in their role as EMs, sometimes just for fun for themselves.

It *becomes* an issue when they proffer these projects off to the teams they
manage, because of the structural power relationship. Rarely are these
applications or tools suitable as more than a proof-of-concept, because they
have not been built to any sort of standard that may be prevalent in the team,
but instead as a fun project at first, that then slowly morphed into a concrete
tool.

These things are unceremoniously bumped into production, because hey, it helps
with the problems, right? Having this is better than not having it? The
structural power relationship here does not help. Telling your boss that his fun
side project should be thrown out as a successful proof of concept is the right
thing to do, but it's also the frictionful thing to do. Particularly when you're
already not on the greatest of terms with your manager, accepting this as a
small concession is the smoothest path. But now you have a badly engineered
project in production, that will invariably have the long tail of bugs any
newly-in-production application has, coupled with the usually partially-unknown
and subpar code that comes from joyful experimentation with LLM-based
programming, and it quickly becomes a small albatross with a lot of touchy
politics and optics concerns.[^4]

## Larger-scale Structural/Social Concerns With LLM-based Programming

My concerns with this boil down to, essentially, Kernighan's Law:

> Everyone knows that debugging is twice as hard as writing a program in the
> first place. So if you’re as clever as you can be when you write it, how will
> you ever debug it?

LLMs are much more frequently subtly wrong than they are overtly wrong. The
LLM-based falsities usually prey on something close to Gell-Mann Amnesia[^2]. If
you are already proficient in the thing you are using the LLM for, spotting the
subtle falsehoods will happen by means of expertise.

In my opinion, one of the most important skills to develop with LLMs is the
ability to discern the useful parts of the output. The output being fully
correct and useful happens so rarely that on an absolute evaluation, LLMs would
be close to useless. The part that makes them useful is that you can pick out
bits and pieces that are indeed very useful, and assemble your desired result
from those.

This is harder when you are not able to spot the subtle falsehoods, or know
little enough of the target domain that you have trouble picking apart the
useful parts of the output. However, this is where people are drawn to LLMs the
most - for things they do not feel like learning, where they want a throwaway
script or placeholder. Here, the subtle offness matters less, because all you
really care about is the output. This is fine and good, and would not pose a
problem if things that are intended to be throw-away have a habit of not staying
that way, fairly regularly, and then things start off built on sand, getting
worse from there.

In this, LLMs encourage not only the writing of code by means of an LLM, but
also the reading of it. Especially when you do not have the developed skills to
read the output code correctly or completely, as is the case for junior
engineers sometimes, mediating understanding with an LLM is tempting. This
undercuts the learning process significantly, if no active learning process is
taking place. This is a process that can be beneficial, in that it allows people
to understand code and documents they would previously have bounced off of
entirely. It can be made to work as a learning tool that is gradually discarded,
but that is actively inviting friction and difficulty into the process, that
people in new jobs in the current state of the tech industry will likely feel
hesitant about.

The main reason I am not concerned about this on an existential level is that
LLMs are quickly becomming a commodity that will be priced on a narrow margin
over hardware costs. Open-weights models like DeepSeek V4 having enough
usefulness while being able to be run by anyone with a bunch of GPUs and access
to cheap electricity, so LLMs as a *thing* in programming will not magically
vanish.

## A Note To Things Not Mentioned So Far

An issue I've sidestepped here is all of the ethical quandries LLMs have
inherently. They're built on, essentially, colonialising the internet commons at
large, and that is hard to ignore, even if I am on some level required to.
Thanks to ubiquitous LLM access and promotion, things that used to be abstractly
trustworthy (someone put in sufficent effort to write something) has now broken
down entirely, and the open internet that is accessible via search engines is
now essentially a landfill you have to look carefully at to extract valuable
information from.

Worse, it's a breakdown in the contract of the internet commons that is visible
to the people involved with the technology, but not the public at large,
although it is becoming more widely understood. I'm about as worried about the
larger social impacts of this as I am powerless to do much about it. "You can
now trust random writings on the internet even less than you did before" is not
an actionable statement. In this particular way, the dystopia is already here,
unevenly distributed.

---
[^1]: I should point out here that I am not inherently hostile to encouragements
    for tools, just that this particular push for LLM adoption comes 1. from
    on-high, and 2. therefore carries the flavour of structural power imbalance,
    the implied "or otherwise we find someone else" is impossible to ignore.

[^2]: “Briefly stated, the Gell-Mann Amnesia effect is as follows. You open the
    newspaper to an article on some subject you know well. In Murray's case,
    physics. In mine, show business. You read the article and see the journalist
    has absolutely no understanding of either the facts or the issues. Often,
    the article is so wrong it actually presents the story backward—reversing
    cause and effect. I call these the "wet streets cause rain" stories. Paper's
    full of them. In any case, you read with exasperation or amusement the
    multiple errors in a story, and then turn the page to national or
    international affairs, and read as if the rest of the newspaper was somehow
    more accurate about Palestine than the baloney you just read. You turn the
    page, and forget what you know.” ― Michael Crichton

[^3]: See the transcript of the (I think) original talk introducing the term:
    https://www.noidea.dog/glue

[^4]: At least in my context, this fun side project was latched onto by
    engineering executives, and then brandished about as "the first agentic
    teammate", meaning that we could not throw it out, no matter how badly we
    wanted to. So we've now started to do the long journey of turning a
    hacked-together, mostly vibe-coded application into a thing suitable for
    production, and it's not particularly great.

[^5]: This has led to this quote that to this day is the clearest depiction of
    panicked action from external pressures coupled with LLM-reliance I've seen:

    > Uh, guys, I think I fixed it, but I don't know if I can describe what I did.

    They did, in fact, not fix it. The incident was a misconfiguration of our VPN
    (Tailscale) that led to networking breakdowns, the "fix" they did was to add
    their laptop as a host to tailscale. They saw the connectivity restored, but
    they did not resolve anything close to the problem.
