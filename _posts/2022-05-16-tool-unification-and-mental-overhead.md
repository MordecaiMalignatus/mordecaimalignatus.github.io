---
layout: post
author: Mordecai
title: "Tool Unification & Mental Overhead"
categories: post
---

Recently, after many frustrations with kitchen timer devices, I caved and bought
a cheap, single-purpose tool: A digital display timer. It has six buttons,
manages two timers, and does nothing more than that. And I love it, it's
fantastic. I have a much easier time using it than futzing with my phone to
enter timers, deal with trying to see which ones belong to what, what I need to
pay attention to.

There's an interesting scale here, and let's stick with the "things that can
time kitchen tasks" for now. It roughly goes, "how much can your tool do besides
what you want to use it for?".

The simplest tool to use for this would be a dedicated hourglass for the
interval you want, you could buy a bunch of cheap ones for common durations and
use those in the kitchen, the simplest tool that could possibly fulfil your
criteria. The next level up would be the classic kitchen timer, a mechanical,
spring-wound timer from one to 60 minutes. You gain the feature of variable time
length, and lose some ease of use. You now have to invest more effort into using
the tool, winding it up to the right amount of force, and dealing with
potentially adjusting if you miss the initial target, something that can't
happen with the hourglass.

Next up the scale is what I bought, a single-task device that now has two
timers, visual indication (there's a flashing light for timers that are up),
keeps track of how much your current timer has overrun what you initially
wanted, and can repeat timers without additional input. The downside is that I
now have to contend with buttons, reading digital displays, and mode errors:
Depending on which timer the clock selects between, I might be changing the one
I didn't want to modify, so I have to check for that as well.

Next up the list is some form of portal computer, probably a phone, on the upper
end, a laptop. Here, you can do arguably whatever you want with the timers, in
terms of functionality. Schedule them, spawn them dynamically, use voice
controls, have them play Danger Zone once up, whatever.

The downside is that _you can do whatever you want_ with your timers now, and
that means you now have to choose. The space of potential actions has grown
exponentially, and that's a space you have to deal with if you want to time the
baking time of your cake. It increases the cognitive overhead in dealing with
the tool. This overhead is something we can usually afford, but certainly not
always.[^4]

Realistically, everyone will have arbitrary defaults they always go to,
regardless of what options they might have in theory. The default ringtone, at
default volumes, while adjusting the timer, the thing they actually care about.
But the larger amount of capability the chosen device has can negatively impede
you; for an arbitrary example, if you have a do-not-disturb mode enabled on your
phone because you don't want it to light up like a Christmas tree every time
someone sends you a message, it might now also muffle your kitchen timer[^6],
you miss it expiring, the cake will bake for too long and be dry, and everyone
will be sad. Nobody wants that.

A tool with less capability, has, consequently, also less potential for errors
like this. Nothing about my simple digital kitchen timer can accidentally be
configured to not alert once the timer expires. I can mute the noise, but it
will still blink a LED at me. My cake timer will not suppress phone call audio,
or music, when going off because it does not run on my phone and does not share
an audio channel with it.

But clearly, having a million kitchen timers for a million tasks is also bad.
The modern phone consolidated and unified roughly a billion (scientific guess)
individual doodads and gadgets, from an actual phone, to music players[^1], to
pieces of scrap paper used for notes, to tamagotchis.

Having _a tool_ with you that can help you with what you want to do is better than
having _no tool_ with you. It might not be the _best_ tool you could use, but it
will still be better than glancing at the clock, trying to maths out when you
need to pull out your cake, and then trying to not forget when exactly it was
and also not forgetting that you have a cake in the oven in the first place.
The individual, single task of timers in the kitchen was valued enough by me to
go back and buy a _better_ tool than the default choice for it, my phone.

If you have a lot of simple tools, you have to put in a certain amount of effort
_first_, in picking your tool, before you can go ahead and do the thing you
intended to do, whereas I can grab my phone and be pretty sure it will solve my
problem in some way, and I can figure it out when it comes to it.

A lot of tools are on scales like this, and it is, for the most part, absolutely
fine, as long as the problem gets solved. However, when tools that are easier to
use by default get used for things that have a really high floor to them being
_solved well_, we start getting into tricky territory.

The poster child for this is Tesla's big touch screen as the centre console,
rather than having one with tactile buttons, like the rest of car manufacturers.
It's sleek, it's pretty, it's elegant, it's endlessly malleable, it's easy to
update, and it also gifts nightmares to safety engineers for free in its spare
time. Even aside the fact that the display controlling a large chunk of your car
is buggy as hell[^2], it now means that you have introduced the same sort of
failure mode that we talked about above, where things entirely unrelated to the
task of timing cake baking times end up interfering with that.

That aside, this scale offers an interesting space for experimentation: If you
find yourself not wanting to use a certain tool for a certain purpose, part of
that aversion might be the cognitive interference/noise from being on the wrong
level of tool unification. It might be too simple and you now have to make a
guess as to what tool to grab for your task at hand, or it might be too unified,
and you now have to remember all the things that have nothing to do with your
task potentially interfering and correcting for that.

Simple, directed, custom tools are best for repeated actions and known domains,
things you know you will need to do time and time again. I'm a big fan of making
these specific, sharp tools sooner than later, because they remove cognitive
load as soon as I have identified the thing I need them to do. Complex, unified
tools are best for when you're not quite sure what you'll need yet[^5], or that the
tools required might change quickly. But if you're not quite sure where your
task falls yet, experiment with unification. It might remove some aversion from
activities you didn't know you had.[^3]

---
[^1]: Rest in Peace, iPod. You were my first fancy thing.

[^2]: For a recent example from just a few days ago, look at [Tesla recalling
    130,000
    cars](https://www.reuters.com/business/autos-transportation/tesla-recalls-130000-vehicles-us-touchscreen-display-malfunction-2022-05-10/)
    cars because the screen could bug out, and show a blank display. This is, as
    they say, not ideal.

[^3]: For example, I avoided setting timers for some stuff when cooking when
    exhausted, because it meant looking at my phone, which meant dealing with
    my message notifications.

[^4]: _Behind Human Error_ gives the example of an anaesthetic device in an
    operating theatre: It had too many buttons, too many ways of dealing with
    things, that the most common way it was used was with _as few of its
    features as possible_, because that made it comprehensible under the stress
    and pressure of the operating theatre.

[^5]: An example from a realm where "the simple tool" is of nightmarish
    complexity: [Field-programmable Gate Arrays
    (FPGAs)](https://en.wikipedia.org/wiki/Field-programmable_gate_array) are
    used to experiment with integrated circuits and CPUs, things that take
    months to make and iterate on because each individual example needs _an
    insane amount of resources_. I encourage you to read [this list of steps on
    how to make a modern
    CPU](https://en.wikipedia.org/wiki/Semiconductor_device_fabrication#List_of_steps)
    because it is fascinating, and also _holy shit we managed to to make this
    the basis of modern information processing_. But now also imagine needing to
    run through all of these steps when you aren't even sure yet of what you
    need. FPGAs are neat as hell.

[^6]: depending on OS, settings, etc, etc, you see that even in this, there's a
    problem here.
