---
layout: post
author: Mordecai
title: "Infrastructure Languages and Kubernetes"
categories: post
---

In the fantastic *Sorting Things Out*, Bowker & Star[^1] talk about information
infrastructure, in the case of the first part of the book, the ICD-10. The main
point of the ICD, they argue, is to create a common reference and classification
of disease, a recognised taxonomy and nomenclature that can be used to
communicate and think about diseases in a standardised and consistent way. A
reference to the ICD code of pneumonia will describe pneumonia wherever the ICD
is used. Therefore, a doctor trying to communicate that a patient is definitely
suffering from pneumonia will use the ICD code to describe what's going on, and
this, in turn, makes other doctors more likely to use ICD codes as well. The
entire point of the book is that this is not a neutral act. In assigning names
and taxonomy, various cans of complex, socio-technical issues are
opened. The classifications we use shape our actions and thoughts.[^2]

Concretely, the language constructed from such infrastructure is oriented around
handling the objects of the domain, and hopefully also solving the problems of
and in the domain. The ICD is designed as a classification rather than a
nomenclature,[^3] where related diseases are grouped closely together. A doctor
trying to figure out _which_ respiratory disease is afflicting their patient
only needs to look through a narrow sub-tree of the ICD.

The problems start arriving once you look at the sacrifices required to make a
classification _useful_ in practice: Statistically
irrelevant diseases have to be omitted,[^4] and similar-but-distinct rare diseases
are grouped. If this is not done, the ICD becomes too "heavy" to use and
communicate with. Information is always necessarily dropped to make a map of the
land.[^5]

Now, information infrastructure is everywhere, we use such infrastructure daily
and at every turn. A consistent theme in Susan Leigh Star's work on
infrastructure is that it tends to vanish from sight: We use it, but we're not
aware of the effort that goes into constructing and maintaining such
infrastructure.[^11] Tech and software are no different but slightly more amusing in
how blatant the irony is: nobody wants to think about the effort that goes into
maintaining and creating things like the Linux kernel, CPUs, cURL, USB drivers,
and so on, yet they are still used every day to provide... more infrastructure
to people who don't want to think about the effort it takes to provide them with
a convenient way to order pants from the internet.

The *perspective* from which the information infrastructure is built matters,
because it informs what dimensions are first to the chopping block when an
abstraction is created. The ICD came about as a mortuary rate table, so the
question was "how many distinct deaths can be attributed to this code?". Niche
diseases with few statistical cases were dropped or grouped, whereas things like
"respiratory illness", accounting for a great chunk of cases, were split up
further. Of note is that relatively little of that is based on treatment
options, or severity, only on the statistics.

Yet, despite its origins as a mortuary statistical device, it found adoption in
hospitals and with doctors needing to communicate, in brief, what someone was
afflicted with. The ICD simply worked well enough to use directly, there was no
need to adapt it to local use, or change it, or even create a new abstraction
suited perfectly to the context. It worked. So it was used. The information
dropped almost certainly caused and causes a bunch of pain for practitioners,
but it was still, by far, the best choice for the job.

The ICD is a bit like Kubernetes, in the sense that it may have had a narrow,
intended use case once, but it has since spread into other domains due to
*usefulness*. It was designed to distribute containers of usually-stateless
services over machines. However, it also worked just well enough for other
things (like running databases, ETL pipelines, *et cetera*), so
practitioners that were already using it for running stateless
services over many computers started using it for those secondary targets, as it
was easier to bodge the task into Kubernetes than it was to stand
up an entire secondary piece of infrastructure that would allow you to run ETL
pipelines in not-Kubernetes.

So the practitioners started creating supplemental infrastructure that would
ease the pains in using Kubernetes for the thing that was previously hacked in.
Deployment services that were run in CI that ended up just calling `kubectl
apply -f` became ArgoCD watching repositories. People realised that re-using
bits of YAML was useful, and we ended up saddled with Helm.[^6]

We're at a point where Kubernetes does most things a SaaS company needs well
enough in some capacity. Given a hosted Kubernetes cluster, I could easily find
a way to run all of the information infrastructure that company would need. It
would be a bad-to-mediocre-to-fine choice for many of them, but I would not have
to try very hard.[^8] With this, Kubernetes has become the topmost layer of
infrastructure for a great deal of people, the thing they look at, the thing
they interact with, the thing they need to debug when things break. Not AWS, not
a VM, not a rack server, but `kubectl`.

Infrastructure vanishes from sight when it works. Kubernetes may be run atop
AWS, and AWS may break separately from Kubernetes and may have many more
features and services than Kubernetes can offer, but unless AWS breaks, that is
not something ever contended with by the average all-in-Kubernetes practitioner.
Kubernetes forms its own infrastructure language, with its own answers to common
problems, with its own practitioner community that uses those answers.

With this, Kubernetes stops being a purely technical or technological choice, and
instead also becomes a social choice. Running your infrastructure on Kubernetes
first and foremost is now also about primarily choosing your hiring pool. What
skills do you want engineers you hire to have? Do you think you'll get a better
average candidate by choosing to run AWS-first or Kubernetes-first? What about
hiring pool size, compensation, especially versus the cost of the infrastructure?

This is why I think that "oh you don't need Kubernetes for this, it's overkill"
or "you should not choose Kubernetes for running your 10-requests-per-day
proof-of-concept for your startup" miss the point, these days. That may have
been a sufficient and complete critique when Kubernetes started out, but it most
definitely is no longer, and has not been for a while now. It's not just about
running your tiny proof-of-concept, but also about choosing your infrastructure
language, and your community of practitioners.

Looking down on people for 'only knowing Kubernetes' may have been somewhat
justified (personally I *don't want* to look down on anyone) when Kubernetes
only solved a narrow slice of infrastructure problems, but those times have
indeed also passed us by for years now. People who only know infrastructure
through the lens of Kubernetes can still solve all the business problems an
average shop may face, they just do it through the lens of Kubernetes.

The options may be worse than non-Kubernetes alternatives in some facet or
another, but that is the same issue faced when AWS first became its own
infrastructure language, and people talked about the things that should never be
run on AWS and only ever be in a data centre. If the solution is acceptable, it
will not be optimised, it vanishes from sight *because it works*. What is
considered 'acceptable' may shift and prompt re-engineering, especially under
cost pressure.[^9]

Very frequently, when "inefficient" or "bad" solutions or "terrible hacks" start
becoming common industry practice, it's not that people all of a sudden lost
their collective minds about how to solve infrastructure problems, it's that
non-technical reasons have won out over technical concerns. Social pressures
include things like the need to be seen as 'cool' and 'current', and I think we
have all seen an executive forcing a technically-stupid decision for marketing
reasons a million times. The same social pressures happen inside of communities
of practitioners as well, just less drastically, and less visibly. A shift like
that is a sign that a piece of infrastructure that used to be a solution in a
broader domain has become an infrastructure language unto itself.[^10]

---

[^1]: The subtitle is "Classification and its Consequences" and that title right
    there is when I originally stopped reading the marketing copy and just
    bought the book. It lives up to it, too. It's fantastic, if a little dry.
    Highly recommended. I've also not been able to get it out of my head since.
    I have also not been able to stop talking about it, either.

[^2]: While this is *similar* to Sapir-Whorf, I think it's distinct: Languages
    evolve, but classifications are explicitly constructed towards a purpose.
    Also, classifications and taxonomies are domain-specific, while the ICD may
    pose thorny ethical issues in the realm of disease and the medical field, it
    has no opinions over, say, what does and does not belong in kimchi.
    (Arguably, it has the opinion that it shouldn't contain botulism.)

[^3]: Bowker & Star distinguish classifications from nomenclatures in that
    nomenclatures make no claim to anything other than providing common names
    for things, whereas classifications take causation and relatedness on board:
    A disease with numerical code J18.9 (pneumonia) is related in some way to
    numerically close codes. In this case, J09-J18 refer to influenza and
    pneumonia diseases, J00-J99 as a whole refer to respiratory diseases.

[^4]: Except for the ones that would be a public health danger, a single case
    of, say, malaria is _very_ worth knowing about. Where to make these
    exceptions? Now we're in the fun discussions about politics, influence, and
    weight of opinion.

[^5]: When those simplifications and statistically-irrelevant cases then run
    over _people_, the fun begins: Just because a taxonomy has to have clear
    boundaries to work does not mean that people and reality obey that same
    restriction.

[^6]: God, I *hate* Helm. I realise that text templating is useful and all, but
    Helm manages to be the single most unpleasant and awful programming language
    (since it has logic constructs and repetition) and also packaging format at
    the same time.

[^8]: The [CNCF Landscape](https://landscape.cncf.io/) is an omnipresent,
    self-writing joke here.

[^9]: See here the repatriation to data centres for compute heavy-loads from
    companies like Dropbox or Adobe, who purchased hardware again for some
    workloads as it was too expensive to run on AWS exclusively.

[^10]: And frequently I wish it would not be so, but that hasn't stopped any of
    them yet.

[^11]: This notably does not mean that it becomes any less *influential*. For a
    treatise on the political influence of infrastructure, Keller Easterling's
    _Extrastatecraft_ is a fantastic read.
