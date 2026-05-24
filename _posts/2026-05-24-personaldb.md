---
layout: post
author: Mordecai
title: "A sketch of PersonalDB"
categories: post
---

PersonalDB[^1] is a little concept I've been throwing around in my head for
supporting some things around the endless text files people (or at least, me)
have lying around for notes, cheat sheets, references, plans, etc. It's a thing
I have kinda started building, but I need to come to grips with what exactly it
should be, hence this article.

In essence, the origin of the problem is that "a file" does not really lend
itself to a useful taxonomy for personal writing. You can make it so, by using
it as a vague categorization system, but you will inevitably run into the ruin
of all rigid categorizations, the edge cases that are two kinds of something.
For an illustrative example, I have two files, `cooking.org`, which houses my
cooking recipes, and `baking.org`, which houses my baking recipes. Smashed
cucumber salad? Clearly cooking. Cake? Clearly baking. Soda bread? Savory, but
baked, so clearly baking. Now, naan? It's bread, and all of the other bread is
with the baking, but it isn't baked but instead griddled, does that make it
cooking? It's a question I've answered by just adding the recipes to both files
to avoid the frustration of opening a file and then having to backtrack after
searching, but that now means drift if it were to change.[^2]

The solution would clearly be some sort of tagging system rather than a
taxonomy. Naan gets both tags, both searches find it, grand. This would be
solvable with `org-mode`, which supports tagging. But then I'm forced into
re-doing all the files and the structure, and eh... Tagging systems outside of
things like `org-mode` are just kind of... bad. They're usually just kind of
barely functioning, really old, or bring way more machinery to the table than I
want to for purposes of organizing some text files.

As I was thinking about this, I remembered columnar databases, and how they made
additional columns almost free, as well as entity component systems (ECS) that
kinda do similar things. Then I was thinking about how this is personal,
one-human scale infrastructure, and how that lets me do some things that would
never fly in many-humans infrastructure.

## The Idea Behind PersonalDB

The core idea is abstracting over "a text file". There is an entity, or a row,
with an ID. An entity can have any number of columns, which are key/value pairs,
but the default value is `null`. This makes any entity, if we squint a bit, a
sparse JSON object, when trimmed for `null` values.

Suppose now that we take all of our recipes of some variety, and turn them into
entities that looks like this:

```json
{
    "text": "Delicious, Buttery Naan\n // the text key contains the entirety of the original text file.",
    "cooking_recipe": true,
    "baking recipe": true
}
```

Given a big list of all entities, finding recipes is now very easy. Attaching
metadata is now very easy. I could include a column of `contains_gluten` at no
cost and filter against it when reviewing recipes for what to make if I have a
guest with celiac disease.

So far, so "why not just include these in the file and use `grep`?". To me, the
'big trick' of this is this: **This same DB could house all my documents, all my
text files, all ad-hoc structured entities I come up with for various reasons,
with no loss of functionality, and the same underlying model, and the same
tools.** Blog posts in this blog could be entities in the same DB, with the
recipe column values set to `null` and a `blog_post` column being set to `true`,
and it would not impact anything at all, but now I no longer really have to deal
with the file system taxonomy for something that to me is fundamentally the same
type of thing, a piece of personal or internal writing[^3].

Because this is also a very simple data structure, it would also allow me to use
it for ad-hoc storage of personal tooling, having access to the same
abstractions and the same data. Magic: The Gathering deck lists could be a
column tag, bibliography citations could be a column tag. It also enables notes
on just about everything that is stored here, just by adding a column. Accessing
this DB programmatically from a script or other application is trivial, and I
probably will write a few libraries just for that.

Inconsistency (what if something is tagged as a M:TG decklist but also as a
cooking recipe and it now has two 'types'?) does not really matter, because
there are no automated consumers of the DB. There's just me, and I'll see it
unexpectedly, and fix it. This gets a bit more dicey with automated processing
via scripts, but honestly, that doesn't really matter all that much to me.

## The Sketch Of A User Interface

The idea is that this is personal-scale software, so I can cut some corners I
would never get away with in other places. I'll use a CLI as illustration,
although the exact same interface can be implemented in many ways, since it is
quite simple at its core.

There are fundamentally four actions: `list`, `get`, `write`, and `delete`.

`list` is the search functionality. It accepts any number of predicates that run
against the collection of entities, for example: `list baking_recipe=true
text=~naan`. These predicates are fundamentally `AND` conjunctions, but `OR` is
possible as well: `list either(baking_recipe=true, cooking_recipe=true)`. The
predicate DSL will have some leeway for being pleasant to use, like `any` or
testing for non-null if no value is specified. `list` also returns the entity
ID.

`get` takes an entity ID, and assembles the full entity JSON object from there.
It returns a JSON object, with all non-null columns. Column order is disregarded
entirely. There is also an option to pretty-print the keys, and to transform the
raw JSON blob into readable text that doesn't have escaped whitespacing and newlines.

`write` takes a entity ID and a JSON object, and replaces what the entity with
the given entity ID with the object.[^4] If it contains a new column, a new
column is created on write.

`delete` deletes (or alternatively, tombstones) an entity. Columns are checked
for whether or not this was the last entity with such a column, and then deleted
if so.

## The Storage Engine Underneath

With this being a small columnar DB, the easy answer is to throw this to
Parquet, and move on with life, and chances aren't bad that I might just do
that.

An alternative I've been thinking about that preserves the plain-text origins of
this, is rooted in entity component systems, and that is to just turn each
column into a separate file, with the entity ID as the key in a big object:

```
/T/t/personaldb tree .
├── baking_recipe.json
├── cooking_recipe.json
└── text.json
```

Where then each file contains a sparse 'list' of column values:

```
/T/t/personaldb jq < text.json
{
  "21": "Delicious Buttery Naan\n...",
  "121": "Smashed Cucumber Salad\n..."
}
```

This makes the management and search of this outside of specialized tooling,
whereas Parquet would just be a pile of binary blobs that I can't do anything
with outside of the tooling.

## A Note On Maintenance

File systems for notes get messy quick, nobody wants to do the house keeping
when it's about doing something, or makings something. Part of the reason why I
like this idea so much is that it makes housekeeping very easy, because there
are now no longer any folders that are just forgotten in some dusty corner. The
same structure houses everything, and reading any note forces you to see all of
its set columns. If a column seems old or antiquated, it can be very easily
overhauled programmatically, or the column file outright deleted, and that is
that.

I think I'll spend some time in the next few days and weeks building something
like this, it seems fun and rewarding for just me.

---
[^1]: Or OmniDB, as I've been kicking it around in my head, but it sounds too
    grandiose for what it is, honestly.

[^2]: Obviously, this is barely a real issue. It's however the little paper cut
    that made me think about this topic, and then I clearly thought a little too
    much about it, and here we are.

[^3]: See [this
    post](https://rambling.malignat.us/2022-07-22/on-internal-writing) for what
    I call 'internal writing'.

[^4]: Chances are I will instead create a new entity and shift the entity ID,
    for "undo" support, given that writes are destructive.
