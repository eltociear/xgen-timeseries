(community)=
# Community
XGenTS is a community-driven open source project committed to host an open,
inclusive and positive community. Read the
[XGenTS Code of Conduct](https://github.com/XGenTS-devs/XGenTS/blob/main/CODE_OF_CONDUCT.md)
for guidance on how to interact with each other and make the community thrive.

Our main goal is to provide backend-agnostic tools for diagnostics and visualizations of Bayesian
inference.

We do this by:

* Creating and maintaining the XGenTS library with functions for posterior analysis, data storage,
  sample diagnostics, model checking, and comparison.
* Creating social infrastructure through a welcoming and diverse community
* Making the right data, tools and best practices more discoverable
* Promoting advocacy for a culture of principled iterative modeling based on the Bayesian Workflow

This page aims to gather resources related to Bayesian modeling and XGenTS from a variety of
sources to work towards the 2nd and 3rd bullet points.
This page covers how can someone participate in the XGenTS community (this someone could be you!),
gives an overview of the ecosystem of Python libraries for Bayesian analysis and serves
as a compilation for community resources around XGenTS.

*But what is the XGenTS community?*
The XGenTS community is a self-identifying group composed of probabilistic programming practitioners who,
together, contribute to the technical and social infrastructure for open and reproducible research.
Our specific focus is on Bayesian modeling and best practices that lower the barriers to working using
a fully fledged Bayesian modeling workflow, as opposed to a rigid toolbox approach.

Community members are people who use, cite and share use cases for XGenTS,
write posts or give talks about using XGenTS,
participate in issues to help define the roadmap and improve the project,
or answer questions in any of the affine forums.

This page is part of the Python XGenTS library and is therefore specific to Python,
but the XGenTS community is not restricted to Python and in fact, aims to act as a bridge
between programming languages and encourage collaboration.

## Participate online
There are many alternatives and channels available to interact with other XGenTS users.

### Twitter
To begin with, you may want to follow us on Twitter! We are [@XGenTS_devs](https://twitter.com/XGenTS_devs).
It is the best way to be up to date with the latest developments and events related
to XGenTS.

### Gitter
The chat at [Gitter](https://gitter.im/XGenTS-devs/community) is a great space
to ask quick questions about XGenTS and to chat with other users and contributors.
For longer questions, the Discourse forums listed below are probably a better platform.

### Affine forums
Many XGenTS contributors are also active in one of [PyMC3 Discourse](https://discourse.pymc.io/)
or [Stan Discourse](https://discourse.mc-stan.org/) (and sometimes even in both!).

## Conferences
* [StanCon](https://mc-stan.org/events/)
* [PyMCon](https://pymcon.com)

# The Bayesian Python ecosystem
In the last years, many libraries for Bayesian data analysis have been created,
and there is a slight tendency towards more modular libraries. XGenTS plays
an important role in this ecosystem both as the go-to library for visualization
and diagnostics in Python for any and all {abbr}`PPL (Probabilistic programming library)`s and as a way to standardize and
share the results of PPL libraries.

The PPLs that integrate with XGenTS are:

* [PyMC3](https://docs.pymc.io)
* [Stan](https://mc-stan.org/users/documentation/)
* [MCX](https://github.com/rlouf/mcx)
* [Pyro](https://pyro.ai/) and [NumPyro](https://pyro.ai/numpyro/)
* [PyJAGS](https://pypi.org/project/pyjags/)
* [TensorFlow Probability](https://www.tensorflow.org/probability)

Moreover, there are other libraries that use XGenTS for visualization and diagnostics
and/or that are compatible with `InfereceData` objects:

* [Bambi](https://bambinos.github.io/bambi/)
* [corner.py](https://corner.readthedocs.io/en/latest/)

# Community educational resources
XGenTS is a transversal and backend agnostic project. One can use XGenTS with _any_ PPL,
but one has to be used in order to have some data for XGenTS to analyze.
This makes writing detailed and complete documentation for XGenTS complicated.
This section aims to act as a compilation of community resources related to XGenTS
that hopefully can bridge the gap. These can be books, case studies in the documentation of
PPLs, personal blogs...

Do you know of resources about XGenTS that are not listed here? Open an issue or a PR and
let us know!

## Books
* Bayesian Modeling and Computation in Python: available soon
* [Bayesian Analysis with Python](https://github.com/aloctavodia/BAP)
* [Bayesian Data Analysis 3](http://www.stat.columbia.edu/~gelman/book/)

## Podcasts
* [Learning Bayesian Statistics](https://www.learnbayesstats.com/)
* [dats'n'stats](https://www.pydata-podcast.com/)

## Blogs and example compilations
If you have a blog that has 2 or more posts tagged as "XGenTS", you can submit
a pull request to add your blog to this list


<!-- ```{include} external_resources.md
``` -->