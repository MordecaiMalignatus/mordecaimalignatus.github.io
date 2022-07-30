---
layout: post
author: Mordecai
title: "Infrastructure \"Languages\""
categories: post
---

I'm currently reading the fantastic *Sorting Things Out* from Bowker & Star[^1],
and it talks about information infrastructure, in the case of the first part of
the book, the ICD-10. The main point of the ICD, they argue, is to create a
common langugage of disease, a recognised taxonomy and nomenclature that can be
used to communicate and think about diseases in a standardised and consistent
way. A reference to the ICD code of pneumonia will describe pneumonia wherever
the ICD is used. Therefore, a doctor trying to communicate that a patient is
definitely suffering from pneumonia will use the ICD code to describe what's
going on, and this, in turn, makes other doctors more likely to use ICD codes in
turn. The entire point of the book is that this is not a neutral act. In
assigning names, taxonomy and nomenclature, the can of complex, socio-technical
issues is opened. The classifications we use shape our actions, and thoughts.

As I turned this over in my head, an old quote from Dijkstra popped into my
head: "The purpose of abstraction is not to be vague, but to create a new
semantic level in which one can be absolutely precise." Specifically, I think
that information infrastructure forms languages used to communicate, and on the
basis of those classifications, semantic levels and understandings form.[^2]

Now, information infrastructure is widespread, we use such infrastructure daily
and at every turn. A consistent theme in Susan Leigh Star's work on
infrastructure is that it tends to vanish from sight: We use it, but we're not
aware of the effort that goes into constructing and maintaining such
infrastructure. Tech and software are no different but slightly more
funny: nobody wants to think about the effort that goes into maintaining and
creating things like the Linux kernel, CPUs, LetsEncrypt, and so on, yet they
are still used every day to provide... other infrastructure to people who don't
want to think about the effort it takes to provide them with a convenient way to
order pants from the internet.

Concretely, the language constructed from such infrastructure is oriented around
helping the solving the problems of and in the domain. The ICD is designed as a
classification rather than a nomenclature[^3], where related diseases are
grouped closely together. A doctor trying to figure out _which_ respiratory
disease is afflicting their patient only needs to look through a narrow subtree
of the ICD.

The problems start arriving once you look at the necessary sacrifices that have
to be made to make a classification _useful_ in practice: Statistically
irrelevant diseases have to be omitted[^4], similar-but-distinct rare diseases
are grouped. If this is not done, the ICD becomes too "heavy" to use and
communicate with. Information is always necessarily dropped to make a map of the
land.

- If people only have one language to solve their domain problems, they're going
  to golden-hammer it hard, even when it is technically a poor use of the tool
- If a sufficient number of people do this, the infrastructure, whether directly
  or by extension of its domain community, will provide tools to make the
  golden-hammering easier/better
- Each level of abstraction by necessity (cf "map is not territory") sheds some
  capabilities of what it abstracts over. If you are fluent in the less-abstract
  infrastructure/tool and can use it to solve problems, you can see the
  higher-abstraction infrastructure as a nice way to do some things, but you can
  see the gaps in what it doesn't do well. This is the role/position most people
  that continuously complain about people using k8s for stuff it's not good at
  (eg, running DB servers).
- However, if it solves most or all of your daily problems, then there's no
  reason to use the less-abstract infrastructure, as it just means more work to
  potentially do things you never need (this is the role of most people that
  crowbar k8s into everything)
- By means of infrastructure vanishing from consideration by design (see Star's
  work), the missing capabiities from the lower-abstraction infrastructure will
  eventually be backported to the higher-abstraction infrastructure, however
  badly and worse, and will enable people that are only fluent in the
  high-abstraction tool to solve their problems.
- The backporting is not seen as unnecessary/bad, because the community of the
  higher-abstraction tools is not necessarily familiar with the
  lower-abstraction tool already providing this functionality, and it would also
  mean having to learn an entirely new domain "language". In such, they badly
  integrate the things they need, solve their problem, and move on.
- People who have seen the strata of infrastructure move and shift know that at
  some point, the battle is lost and the critical mass of higher-abstraction
  "native speakers" is hit, at which point, all they can do to keep the problem
  solved reasonably well is to willingly adopt some parts of the
  higher-abstraction model of the world to ease integration and make the
  backport lessbad.
- once the language-community hits a certain size, the technical or objective
  merits of whatever infrastructure discussed start being dwarfed by the social
  aspects; the capability to shittily-back port things on short notice becomes
  the de-facto objective merit.

---

[^1]: The subtitle is "Classification and its Consequences" and that title right
    there is when I originally stopped reading the marketing copy and just
    bought the book. It lives up to it, too. It's fantastic, if a little dry.
    Highly recommended.
[^2]: While this is *similar* to Sapir-Whorf, I think it's distinct: Languages
    evolve, but classifications are explicitly constructed towards a purpose.
[^3]: Bowker & Star distinguish classifications from nomenclatures in that
    nomenclatures make no claim to anything other than providing common names
    for things, whereas classifications take causation and relatedness on board:
    A disease with numerical code J18.9 (pneunomia) is related in some way to
    numerically close codes. In this case, J9-J18 refer to influenza and
    pneunomia diseases, J0-J99 as a whole refer to respiratory diseases.
[^4]: Except for the ones that would be a public health danger, a single case
    of, say, malaria is _very_ worth knowing about. Where to make these
    exceptions? Now we're in the fun discussions about politics, influence, and
    weight of opinion.
