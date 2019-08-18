# Org-kasten.el: An exocortex implementation

_I describe what an exocortex is in the previous post. I split these for reasons
of length and topics, between an idea and its implementation_

This is, for now, the result of a really long yak shave that had me try 4
different iterations of an exocortex until I arrived at this, and this seems to
work for me.

This is a small set of functions and a minor mode on top of `org-mode`, togehter
with a specific file format and directory layout.

The layout is simple: One folder to ser

## Why Emacs as base?

- Org-mode is 80% there, only missing some features related to navigation and
  creation of new files.
- Emacs is very amenable to hacking tools on top of it.
- I spend a lot of time in Emacs, it would make sense for my
  knowledge-management tool to also be based on Emacs.
- Emacs is very old, very stable, and very unlikely to go away any time soon. It
  is also subject to a little bit of a renaissance recently.
- The downsides of emacs are also just that: There aren't that many users of
  emacs, constraining the usefulness of the tool provided
  significantly. However, I hope that I can convince

## My personal workflow as an example

- Read a book you want to learn from.
- Take notes on paper, never quoting but always paraphrasing the author
- Later, but ideally within 24 hours, write references for the kasten, filtering
  your paper notes to the ones that are relevant for the conversation inside the
  kasten.
- After each reference file, navigate to the cluster that you are targeting, and
  see how the newly created reference relates to the notes you already
  have. does it create a disagreement between ideas you already have stored? If
  so, that usually points to an insight not yet had.
- As you navigate around the kasten to make connections between ideas as they
  occur to you, new ideas will be sparked, that extend the kasten further and
  may even be able to resolve some disagreements in the kasten that you had
  before.
- This entire system is geared towards writing, the end product is text that you
  can share. The act of writing is crucial, the system will not come together
  without you also putting ideas together in text. It's the critical last step
  where you find missing links, holes in your arguments that sound good in
  isolation, and citations that are missing. The whole point of this system is
  to enable your writing, and if you do not use it to write at least directed at
  yourself, you will have holes in your ideas and no opportunity to actually
  notice them being that. This is, for the record, also why I'm writing this
  post. It's the last step in checking whether or not my ideas are sound (to
  me), or if I just have gibberish for notes.

## Installation

- [Github Repo](https://github.com/MordecaiMalignatus/org-kasten)
- Currently you have to install it by adding it to your load path.
- `use-package` declaration:

```lisp
(use-package org-kasten
  :bind (("C-# C-#" . #'org-kasten-open-index))
  :config
  (setq org-kasten-home "~/Dropbox/Perceptron/")
  (add-hook 'org-mode-hook 'org-kasten-mode))
```

- Disclaimer: software still in development, more things hardcoded than I want
  there to be, help appreciated, bugs appreciated. First elisp project.
