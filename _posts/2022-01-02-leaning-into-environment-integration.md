---
layout: post
author: Mordecai
title: "Leaning into Environment Integration"
categories: post, tech
---

A relatively common piece of advice, or rather an attitude, to encounter with
older developers and sysadmins that have Seen Some Stuff is the insistence on
using no or very little editor configuration, instead relying on stock,
unconfigured `vim`, Sublime Text, and `bash` or maybe `zsh` if they feel
adventurous. The common reason for this is that getting used to customisations
might end you up in a situation where you don't have access to this
customisation and then have to make do with the unconfigured version, such as
having to jump on a host that you haven't seen before and having to debug an
issue.

This sort of cultural influence has in part, I believe, discouraged people from
customising their tools or building environments for themselves, instead relying
on things that are mostly interchangeable, easily assembled, or low-impact: They
might have a VS Code configuration that puts together plugins and a colour
scheme, but it will stop there.

The other reason is that people might not see it as worthwhile, or that it is a
distraction from what they could be doing otherwise: making stuff that they see
as more useful, or things that they could be paid for. In that model, futzing
with your environment is a distraction, something that yields no progress
towards your goals, but definitely sucking up time and brain juice.

There's one culture that tends to stand against this, – Emacs – where people
still heavily invest into their environment and making it appropriate for them.
The downside of this is that Emacs is very much so a "build your own editor with
lisp" toolkit, rather than being out-of-the-box usable in modern times. For
example, VS Code is well-usable with the installation of a few recommended
plugins, and IntelliJ does not need any customisation to be usable at all. Vim
is great at text editing even without changing a thing even if it understands
nothing semantic about your code whatsoever, stock IntelliJ has a pretty deep
understanding of what your code is doing and what types are where, even if its
text editing can be generously described as basic. Without tinkering and
building your environment, Emacs is bad at both.

This barrier is such that despite using Emacs for most of anything that involves
text, I'm unable to recommend it to others that ask. The tragedy is that this
barrier is the very thing that taught me about what I call "Environment
Integration", or building an environment where your intentions have very low
cost to be translated to action.

### Environment Integration

The idea here is very much from Emacs, where over time, as you grow more
proficient in elisp and understanding how everything works, you begin to build
small snippets of elisp in order to plug together the nuts and bolts given to
you to build something more effective. This gives, effectively, trains users to
become elisp developers and build more and more things to help themselves. The
top-end for environment integration here is hard to butt into on accident, given
that it's less of an editor and more of an old-school [lisp
machine](https://en.wikipedia.org/wiki/Lisp_machine) that happens to have
graphic output attached.

Environment Integration is having a low barrier from intent ("I want to run this
code") to action ("The code is running in my shell"). For the most common
intents, nearly every setup has this, like re-running unit tests, compilations,
running the resulting binary. This does not need a particularly high degree of
tooling or customisation, this is the bottom line that is the standard and
minimum barrier to entry of any text editing tool. Some people demonstrate the
lack of customisation required, for example, Gary Bernhardt's [Destroy All Software
screencasts](https://www.destroyallsoftware.com)[^3]. In nearly-stock vim, Gary
is quicker, more direct, and plain faster in translating his intents to action
than everyone else I know. This is owed to his deep expertise with vim, and
knowing how to make use of its facilties very well.

The next step up is rarer: Tools for, for example, dealing with version control.
Many of my coworkers drop to the `git` CLI in a shell to interact with it,
despite that being a notoriously poor experience. The cause here is not that
there are no tools, but that the tools are perceived as bad: While I know many
people using Jetbrains' IDEs, the amount of people that use the `git` integration
rather than dropping to the `git` CLI in the intergrated terminal I can count on
one hand. Usually it is perceived as janky, slow, incomplete, or otherwise bad
in a way that does not save on time or brain juice in dealing with `git`.[^1]

I think these boil down to the same problem: The `git` interface might be
perfectly competent, complete, and relatively easy to use with some training,
but for most people, it does not beat using the CLI.

*Why* it doesn't beat the CLI has many reasons that are not necessarily that the
UI for it is bad, or that it's too slow:

* People have no practice with it because they assume it won't be worth the
  effort in learning it, as most `git` UIs are not good, so why would this one
  be different? (TortoiseGit and Sourcetree in particular are... worse than the
  CLI.)
* People have no practice with it because they don't want to invest in learning
  the tool.

This, again, may have a few reasons that can be unrelated to the tool itself:

* People don't want to lose their expertise between tools, while they will
  be using `git` for the considerable future, they might not be using this
  editor and so any expertise accumulated on this tool that is specific to
    this editor would "go to waste" once they switch.
* People don't think getting better at using `git` is a goal worth
  pursuing: After all, their job is write software, not use `git`. The
  marginal time savings getting better at using `git` would bring are
  pushed into not being worth the effort by the prospect of just writing
  more code instead.[^4]

Yet, getting good at using `git` yields large return on time-investment in one
crucial metric: The amount of thought you have to invest. Being low-skilled at
`git` (knowing about basic commits, pushes, cloning and branching and doing the
more complex actions in the GitHub interface) is fine, right up until a merge
conflict happens and you pull up Google to figure out how to resolve this.[^11]

Having to think hard about how to deal with this problem throws you out of the
previous problem you were trying to solve: Everything came to a halt and you
pulled up google to acquire a skill ad-hoc and without any further integration
into your skillset. Eventually though, through repetition, you won't have to do
that anymore, and your `git` skill grows.

On the other side of that coin, putting some effort into learning how to get
good at `git`[^5], this interruption disappears: Doing the thing you intended
(create a pull-request to address the bug earlier today) happens without
interruption (or, more truthfully, with much fewer interruptions that are either
Very Interesting™ or more easily resolved)

Once you do understand it and have some skill, you can begin to
customize/integrate for *your intent*. This means, in this case, having hotkeys
for pulling/fetching/rebasing from `git`. Having the `gh` CLI setup so creating a
pull-request is quick and painless. More and more interruptions disappear from
your life once you put some effort into acquiring expertise about the things you
have to deal with on a daily basis.[^6]


### Leaning into it

So what if we were to lean into this? To lean into the idea that our machines as
developers are nuts and bolts given to us to make into something useful and
practical, to actively and consciously integrate our environment, for us.

There's a couple of points that immediately come to mind as to why it's a bad
idea:

1. Your integration is specific to you, it won't translate inside your team.
   Given how collaborative software development is, this seems like a thorny
   issue.
2. Adding complexity (in forms of integration) to the process of software
   development seems like an *even worse idea*, given how many things we have to
   juggle to get anything done.
3. Building tools that depend or integrate with our environment might break or
   become unusuable when our environment changes. With the average job tenure in
   Software being somewhere [between 2 and 3
   years](https://www.inc.com/business-insider/tech-companies-employee-turnover-average-tenure-silicon-valley.html),
   the environment will change frequently and it seems bad to integrate with
   things we know will not stay in the same place.

For the first point, this is entirely correct, and hard to avoid, but relatively
easy to mitigate. We already work with non-standardized environments and
communicate via artefacts (code, pull requests, documents) that are outputs of
our environment that can be produced many ways. Until your integration produces
artefacts that you expect people in your team to understand, you're relatively
clear of this issue. The other problem falling into the same corner is *magic
tooling*: When your tooling produces useful effects that you rely on, but you
have no idea how that happens. I find this only to be the case when I steal
integrations from others wholesale and integrate them, without understanding how
they work and why.[^7]

Secondly, adding complexity: In the worst case, this is what happens, and it
frequently does, especially in the teething stages of integrations. But the core
idea of environment integration is to build tooling based on your existing
process model. The idea is to take *out* complexity from processes by removing
the parts it can go wrong, while preserving the intent to an action. Less CLI
command flags to remember, less order of process to remember. However, if a
piece of integration is so brittle that it causes more harm than good, removing
it is absolutely the correct thing to do.

Third, yes, things will break. However, most parts inside of companies these
days are broadly similar: There's a `git` host or forge like GitHub, there's
likely to be a form of YAML based CI pipeline, there's ideally some form of
infrastructure-as-code. Due to the way market competition works, most of these
tools have a relatively similar shape, and therefore it's relatively simple to
replace one semantic component with another that is shaped similarly, even if
you have to change some parts of your integration.

I am deeply convinced that we are sorely underinvesting in our tools. As
software developers we have the incredibly unique situation shared only by,
maybe, at most, carpenters and gardeners. We can look at the tools we're working
with, and decide that we want to change them, to make them better for our
purpose. We can decide to make things that work for our way of thinking and
working.[^8]


### The Software Engineer's Toolchest.

A car mechanic brings their toolbox to the shop they work at. This can often be
an entire ordeal, given that toolboxes can weigh in excess of 2500kg, and they
are everything but portable. There's an entire niche industry around the secure
hauling of these very important toolboxes. They are the tools of the trade,
quite literally the thing they earn their money with.

However, when software developers talk about toolchests, they talk about
primarily *knowledge and expertise*, and maybe some dotfiles they keep on
GitHub. The rest is knowledge of their go-to solutions to problems they are
faced with, like programming languages, development techniques, and common
problems.

I see the lack expansive, honed, carefully crafted toolchests on the end of most
software developers as a massive missed opportunity and potential to become so
much more effective.

### What If We Are Our Own Bank?

What tipped me into this direction was reading about the heavily-integrated and
widely-divergent [Python environment present in large US
banks.](https://calpaterson.com/bank-python.html). Some of these integrations,
like trivially globally-available task-graph execution, to all storage being
done in global overlays are things that I personally did not even conceive of
before reading about it. It makes *absolutely perfect sense* in the environment
that this grew in: A bank that wants to enable as many people as it can to be
effective writing number-crunching python as possible. To go for the
mostly-semantic level of "run this script with this data", stripping or
abstracting away hosts, deployments, everything that requires heavy lifting of
knowledge to get right.

The heavy downside is that for the developers inside these very different,
heaviy integrated environments, the work with this environment means nothing
without the context of working at the bank mentioned. All your domain expertise,
all your tricks and knowledge goes *poof* when you leave the bank. Investing
heavily in becoming good in this is a dead end, because it won't find re-use.

But what if we instead integrated our *own* processes and environment to this
level? The seeds of it exist, with dotfiles and editor configuration. I just
don't think it has been taken anywhere near its potential.

If we do this solely for our own processes, we can eliminate the biggest problem
the bank python environment faces: Namely, that the environment will stay
constant, because the environment is our personal workspace that we take with us
between the companies we move between. Once that is eliminated, we can then
invest heavily in any process where you communicate via artefacts, rather than
by having others be part of the process.

But what are those processes that involve just us? For example, anything that
produces an artefact, or consumes them. That means templates, snippets and
text-expansion blocks. But it also means how we debug, or notice errors. How we
read logs and metrics[^10], and notice outliers. [Hillel Wayne has an excellent
essay](https://buttondown.email/hillelwayne/archive/syntax-highlighting-is-a-waste-of-an-information/)
about how differently we could be using syntax highlighting to add semantic
information.[^9]

Crafting, honing, refining your toolchest is a compounding investment. Being
able to worry about less and less problems, and having to accept less and less
interruptions from wanting to execute on intent means that you become faster and
faster, and encounter less frustration. I have, for example, not once stressed
about moving or editing commits in `git` since acquiring some inside knowledge
and getting comfortable with Magit.

Creating your own tools, the scripts and applications that carry us from
declaring our intent to the result being achieved also comes with the free
benefit of them being completely malleable to your needs in specific, rather
than the need of the general developer audience. Few applications that come from
GitHub will provide the knobs required to make it just right for you, or have a
good/any/sufficient API to integrate with what you need it to. I am in fact
directly encouraging you to reinvent the wheel here, as it will either teach you
quickly why the insufficient tool is that way, or you walk away with something
that's just right for you.


### It's Not Just For Work

However, even if all the examples and concepts so far have referenced working as
a software developer, that is merely one of the domains applicable. The skill of
being able to write software to support our own processes is just the most
pronounced in this domain, but holds just as true everywhere else in life. Write
a tool to keep your recipes for cooking and baking, write a script that reminds
you to connect with your old friends. Write a generator that creates football
tournament brackets. Your toolbox will grow, and you will be able to apply bits
and pieces in entirely unrelated domains and situations.

Over time, your toolchest will accumulate solutions, patterns, documentation,
cheatsheets, tricks, and libraries that then make it much easier to solve new
problems you will encounter in the future. You will be able to have more
abstract intents carried through to your desired result, as you know what's
under the hood and what it's doing. You can worry less and less about technical
execution and think more and more about *what's a good idea to do now*.

In a different wording: I encourage you to invest in acquiring expertise in the
domain of your own processes, of how *you* work, and what works best for your
work. Build the things that help, tinker with them until you no longer worry
about them. Accumulate a toolbox that you can then apply to any new problem you
encounter. Human performance is a force to be reckoned with if properly taught,
utilised and given feedback, and figuring out how you work and what you struggle
with so you can compensate is the most profitable investment you can make in
yourself.

I see this ability to create your own tools as a skill on a similar level of
learning how to do project management well: It may be a specific job, but it is
also partially literally everywhere else. It will empower you to solve things
faster, more effectively and more thoroughly than you would otherwise be able
to. Consider reinventing a wheel in order to see if you might find one that
works better for you.

<!-- Footnotes. -->

[^1]: Emacs[^2] is the home of the sole better-than-CLI `git` interface that I
    know: [magit](https://magit.vc/), which makes very few, but very good
    assumptions and decisions for how the user wants to interact with `git`, while
    always keeping the escape hatch (`git` CLI) in the top-level bindings.
    (hitting `!` in the Magit buffer opens a `git` CLI prompt.)

[^2]: There's a pattern here, I think. :)

[^3]: Gary Bernhardt's screencasts are **very good** and have probably taught me
    more about programming than nearly any other person in tech. He is a very
    good teacher, and I encourage you to pay for DAS, and also to try out his
    other project, [Execute Program](https://www.executeprogram.com/). He cares
    about pedagogy, being a good teacher, and fast feedback loops, and nobody
    else seems to do so. The difference between someone caring about these
    things and not is hard to communicate in its immensity.

[^4]: It should go without saying that I disagree with this statment extremely
    deeply, but it remains a position I encounter relatively frequently.

[^5]: There's plenty of resources, but particularly effective at *understanding*
    how `git` works and what it wants from you was Alex Chan's *fantastic* notes
    on [The Plumber's Guide To
    Git](https://alexwlchan.net/a-plumbers-guide-to-git/) (links to the
    individual parts are the bottom), and the excellent interactive teaching
    tool with a very descriptive URL:
    [learngitbranching.js.org](https://learngitbranching.js.org/)

[^6]: I'm in a slightly unusual situation here: Due to the way my brain is
    shaped and thinks (ADHD), I have a very low tolerance for these
    interruptions, my brain "RAM", so to speak, the parts where I can freely
    stop and resume trains of thought is tiny, and so any derailment in the
    current one requires me to then pick up the pieces of the exploded old
    thought, slowing down the process *tremendously*.

[^7]: This is more of a problem as it might at first seem: Literally any piece
    of software that is part of the modern toolkit is this, just to varying
    degrees. The people using mostly infrastructure tooling encounter this
    problem with terraform, webdevs with webpack. Both of them are sometimes
    utterly confusing, and very complex pieces of software. The complexity makes
    it hard to maintain a working process model for them, and makes it harder to
    integrate them effectively.

[^8]: I've been exploring this somewhat myself, with [prior
    posts](https://rambling.malignat.us/2021-11-22/software-as-brain-prosthesis).
    However, this is a journey I still feel like I'm only now beginning.

[^9]: I also see Hillel's journey into Formal Methods as an extension of this
    integration: Investing in tools that allow us to go quicker from intent (A
    distributed system that works) to solution (A system design free of
    deadlocks and all sorts of distributed systems tomfoolery). That's mostly
    just my interpretation, though.

[^10]: Another illustration of how under-invested these sort of tools are is the
    comparison of using DataDog for logs and metrics and using Honeycomb. Anyone
    that has used Honeycomb and DataDog both that I've talked to has expressed
    eternal frustration of trying to get sensible answers from DataDog and
    working around its constraints all the time.

[^11]: This is an imperfect but illustrative example, a friend points out that a
    lot of these specific issues with git (forgetting commands, etc) are solved
    by installing/using fuzzy history matching in your shell, which requires
    zero training or time investment past being aware it exists. I concede his
    point, this is an important step between the two ends of flailing wildly and
    having a working, integrated solution for yourself.
