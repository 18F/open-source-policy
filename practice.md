## Practicing our open source policy

This document is meant to give specific team guidance on putting our [open source policy](policy.md) into practice.

* 18F releases software into the [international public domain](#public-domain).
* All team members should feel empowered to contribute back to outside open source projects.
* We [develop our software in the open](#working-in-public).
* There are [narrow, documented exceptions](#exceptions) where source code may be delayed or withheld.

18F team members should work with the strong presumption that all of their code will be public, throughout and after development.

Before deciding to delay or withhold the release of source code, you should consult with the team and be prepared to publicly document this exception.

### Public domain

[By law](http://www.law.cornell.edu/uscode/text/17/105), works of the United States government are not copyrightable in the US, and so are public domain. But by default, US government works **are** copyrightable internationally, and so 18F intentionally waives this copyright abroad using [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

There are potentially other cases where copyright is involved: where contractors produce the work, or where work was otherwise originally performed not in the capacity of a US government employee. To the extent 18F has the rights to do so, 18F will normalize the copyright status of its work product under CC0.

### Contributing back to outside projects

18F staff are encouraged to contribute back any modifications or improvements they make to open source software projects outside 18F -- whether government or non-government -- in the course of their work. When 18F staff begin modifications to outside work, they should plan with eventual upstream contribution in mind.

In terms of licensing: as works of the government, employee contributions are public domain in the United States, regardless of the outside project's contribution agreement. This does not change the overall license status of the outside project.

As [the Free Software Foundation says](https://www.gnu.org/licenses/gpl-faq.html#GPLUSGovAdd) about government-contributed improvements to GPL software:

> Yes. If the improvements are written by US government employees in the course of their employment, then the improvements are in the public domain. However, the improved version, as a whole, is still covered by the GNU GPL. There is no problem in this situation.

#### How to license 18F repos

When you create a repo, add a [LICENSE.md](LICENSE.md) and [CONTRIBUTING.md](CONTRIBUTING.md) file.

The preceding links are to our standard boilerplate for each of those, so you can just copy and paste them. In some cases, you may need to customize them for your use -- for example, if you've forked a project that originated from outside the government.

You may wish to add the following to your `.bashrc` or `.zshrc`:

```bash
alias insert-license="wget -q https://raw.githubusercontent.com/18F/open-source-policy/master/LICENSE.md"
alias insert-contrib="wget -q https://raw.githubusercontent.com/18F/open-source-policy/master/CONTRIBUTING.md"
alias 18f-init="insert-license && insert-contrib && echo 'Licensed.'"
```

You can then initialize a new 18F repository's license information with:

```bash
18f-init
```

### Working in public

18F believes in [working in public](https://18f.gsa.gov/2014/07/31/working-in-public-from-day-1/). It creates a healthier working environment, a more collaborative process, and just better software.

All 18F team members are expected to make new source code repositories public from the time of creation.


### Delays and exceptions

Our policy lists [3 classes of exceptions](https://github.com/18F/open-source-policy/blob/master/policy.md#exceptions) for which we will not release source code:

1. We don't have the rights to release the code.
2. The code's public release is restricted by a specific law or regulation (for example, arms control).
3. Some other "compelling interest" that is "rare [and] documented publicly", listed below.

There are a couple of categories of "compelling interests" where we may _temporarily_ delay open sourcing our work:

* **Before the ink is dry**. It's common for 18F to begin work on code before formally signing and completing an "inter-agency agreement" (IAA) with our partner. Generally speaking, until an IAA is signed the project has not formally begun, and we are not able to discuss a project publicly.

* **Brief experimentation**. This could be work that a team member wants to share with another team member before clearing through partner agency processes, or to "whiteboard" out an idea that they want to propose in a small group. This shouldn't last more than 10 business days, by which time the code should be made public or removed from 18F's version control systems.

#### Exceptions

18F currently has **no projects** for which we will not ever release the source code.

18F has one project where source code will be released at a later time:

* [US Citizenship & Immigration Services](http://www.uscis.gov/) - Project agreement pre-dated the creation of 18F's open source policy. 18F will work with USCIS to coordinate publication of source code as components are publicly released. Components based on existing open source projects will remain open throughout development.
