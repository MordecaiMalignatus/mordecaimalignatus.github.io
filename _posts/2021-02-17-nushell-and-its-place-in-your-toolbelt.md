---
layout: post
author: Mordecai
title: "Nushell And Its Place In Your Toolbelt"
date: Wed, 17 Feb 2021 08:06:17 +0100
categories: post
---

[Nushell](https://www.nushell.sh/) is something I found recently, and have come to appreciate. Here's,
briefly, why I think it deserves a place in your toolbelt, even if it may not
become your login/default shell of choice.

## Object streams instead of text streams

The big conceit of `nu` is that it adopts PowerShell-like structured object
flows in pipelines, instead of relying on unix-style conventionally-formatted
text streams. Since none of the shell-stalwarts like the GNU `coreutils` support
these, they also wrote a fitting set of commands to execute on this
paradigm. And what a success this is.

To be explicit, this is the one point why I think you should have `nu` installed
even if you use another shell for your daily work.

To showcase this feature a bit, for work reasons I had to delve into log-files
and check of sometimes, user IDs were unset, since it propagated all the way
into some reports and we were asked about. Now, I could write a script for this,
I `grep` the logs after crafting an expression that would fit `null` user IDs,
I could check by hand. Or I could fire up `nu` and run this:

![An example of nushell, running "open 12:00:00_12:59:59_S1.json --raw | from
json -o | select jsonPayload.user.user_id  | uniq -c" and getting back a table
of numbers, with one row displaying
nulls."](../assets/nushell-pipelines-example.png)

And there were my unset null values, 52 of them.

Now, I could do this with `jq`, which is a wonderful tool that should not go
without mention, solving this problem precisely. But it solves it for _JSON_,
while the above pipeline would also work if my files were in YAML (yes there's
`yq`, but the syntax is different from `jq`, which is maddening), TOML, XML,
CSV or anything reasonably popular that can be made to fit a table
structure.

That's why I think it deserves at least a place in your toolbelt,
because it takes those tools and integrates them into a scriptable and
generalised language, rather than having to implement that entirely _inside_
`jq`. Which leads to...


## Scripting: Less footguns than Bash, more ad-hoc than Python

If you're like me and you detest using `bash` for scripts because of its myriad
issues and footguns, you'll often find yourself writing verbose one-off scripts
in something like Python to avoid them. This is always annoying, because what
could be a few lines in bash is inevitably _more_ in Python.

Nushell solves this problem very well for me, because they provide a level of
abstraction in between: A typed(!) bash-like scripting language with sensible
syntax, and Rust-like errors(!!). For those that have never seen this style of
error before, here's what a type error looks like in `nu`:

![Type error in nushell, trying to compare a string with a number, displaying
exactly where the error ocurred and what the differing types
are.](../assets/nushell-type-error.png)

Functions can take typed arguments. Functions have helptext. Pipelines tell you
where a type error originated. There's a lot to love about `nu`'s scripting
capabilities, and it occupies a really nice spot where digging out Python is
just annoying and `bash` remains full of footguns you don't want to think
about.

However, for cooperation with team members, servers, and so on you will still be
stuck with python/bash since it's unlikely that people even know of `nu`, much
less have it installed. But for those cases, this article might help :)

## Human-oriented

It's very clear that the authors of `nushell` care about the user experience and
thus have done what they can to make it a welcoming, and so a lot of small
features are included solely oriented towards the user experience, even more so
than `fish`.

My favorite little thing is that invalid subcommands flash red. That means, that
rather than type a command and hope the flag is the one you remembered, you can
type and if the subcommand/flag/argument is not known to `nu`, it will be
highlighted in red.[^1]

There's another nifty little thing that's an improvement on `pushd`/`popd`, the
concept of "shells" (which, to me, is a bit of a terrible name). They have a
wonderful explanation [here](https://www.nushell.sh/book/shells_in_shells.html),
to which I will just link.

The [documentation](https://www.nushell.sh/book/) is pretty great in general,
the parts of it that are there. A lot better than you would expect from an
early-stage project, and I like it a lot. They also have a
[cookbook](https://www.nushell.sh/cookbook/) for common uses, which displays
some of the cool stuff `nu` can do.


## A word of caution

Nushell is still early days. A lot of things are janky. It is however a very
active project, and if you've been looking for a project to contribute to,
everyone seems to be friendly and welcoming. This, however, means that things
will break, change, and otherwise inconvenience you. In my experience it's been
pretty stable and good, but it is easy to tell that a lot of edges still need to
be smoothed.

All in all, I'm happy to have found it, and it makes a nice addition to my
toolset. Perhaps you should consider that as well.

[^1]: This sadly only works for the commands and functions known to nushell, not
    the ones existing independently, like `git`.
