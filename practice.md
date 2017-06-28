## Practicing our open source policy

This document is meant to give specific team guidance on [open sourcing](policy.md) at GSA into practice.

* GSA releases software into the [international public domain](#public-domain).
* All team members should feel empowered to contribute back to outside open source projects.
* We [develop our software in the open](#working-in-public), while also [protecting sensitive information](#protecting-sensitive-information).

GSA team members should work with the presumption that all of their code will be public, throughout and after development.

Before deciding to delay or withhold the release of source code, consult with the team and be prepared to publicly document this exception.

### Implementation guidance to support OMB-16-21

[Implementation guidance](https://open.gsa.gov/oss-implementation/) supporting [M-16-21](https://sourcecode.cio.gov/) is located on GSA's open government platform [open.gsa.gov](https://open.gsa.gov/).  In particular, teams that produce custom code, either developed by a federal employee or contractor, are to include it in the [code.json file](https://open.gsa.gov/code.json) and consider how to open source it if not already done.

To assist with open sourcing the code, use this repo's [open source checklist](https://github.com/GSA/open-source-policy/blob/master/open_source_checklist.md).  This checklist will continue to be refined as we progress through open sourcing.

### Public domain

[By law](http://www.law.cornell.edu/uscode/text/17/105), works of the United States government are not copyrightable in the US, and so are public domain. But by default, US government works **are** copyrightable internationally, and so GSA intentionally waives this copyright abroad using [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

There are potentially other cases where copyright is involved: where contractors produce the work, or where work was otherwise originally performed not in the capacity of a US government employee.

To the extent GSA has the rights to do so, GSA will normalize the copyright status of its work product under CC0.

### Contributing back to outside projects

GSA staff are encouraged to contribute back any modifications or improvements they make to open source software projects outside GSA -- whether government or non-government -- in the course of their work. When GSA staff begin modifications to outside work, they should plan with eventual upstream contribution in mind.

In terms of licensing: as works of the government, employee contributions are public domain in the United States, regardless of the outside project's contribution agreement. This does not change the overall license status of the outside project.

As [the Free Software Foundation says](https://www.gnu.org/licenses/gpl-faq.html#GPLUSGovAdd) about government-contributed improvements to GPL software:

> Yes. If the improvements are written by US government employees in the course of their employment, then the improvements are in the public domain. However, the improved version, as a whole, is still covered by the GNU GPL. There is no problem in this situation.


#### How to license GSA repos

When creating a repo, add a [LICENSE.md](LICENSE.md) and [CONTRIBUTING.md](CONTRIBUTING.md) file, and add/edit the [README.md template](README_TEMPLATE.md).

The preceding links are to our standard boilerplate for each of those, so you can just copy and paste them. In some cases, you may need to customize them for your use -- for example, if you've forked a project that originated from outside the government.

You may wish make the following shell aliases

```bash
alias insert-license="curl -sO https://raw.githubusercontent.com/GSA/open-source-policy/master/LICENSE.md"
alias insert-contrib="curl -sO https://raw.githubusercontent.com/GSA/open-source-policy/master/CONTRIBUTING.md"
alias GSA-init="insert-license && insert-contrib && echo 'Licensed.'"
```

You can then initialize a new GSA repository's license information with:

```bash
GSA-init
```

Want to take it even further and create the repo at the same time?

```bash
alias create-repo="mkdir \!* && cd \!* && git init ."
alias create-readme="curl -s https://raw.githubusercontent.com/GSA/open-source-policy/master/README_TEMPLATE.md -o README.md"
alias create-GSA-repo="create-repo \!* && GSA-init && create-readme && sed 's/[Repo Name]/$(/usr/bin/basename $(pwd))/' README.md && git add . && git commit -m 'initial commit'"
```

Then create a repo and license it with:

```bash
create-GSA-repo new-project-name
```

Even if you don't create a repo, it's recommended to use [this README.md template](README_TEMPLATE.md) that sums up what's going on.

### Accepting contributions from the public

Any GSA project can (and should!) accept open source contributions from the public.

Projects can **encourage public contributions** by:

* Creating open issues where public help would be especially welcome.
* Labeling those issues with `help wanted` so people can scan issues quickly and [services](http://www.codeforamerica.org/geeks/civicissues) can aggregate volunteer opportunities.
* Asking for contributions, in the README and in other public writing about the project.
* Providing solid documentation for any project setup process.
* Being super nice when communicating with volunteers.

As [described above](#public-domain), GSA projects are dedicated to the international public domain wherever possible. In this situation, contributors must agree to release their contributions into the international public domain. Projects can inform contributors of this agreement by copying the [`CONTRIBUTING.md`](CONTRIBUTING.md) file from this repo into new project repos, and copying the ["Public domain" section of this repo's README](README.md#public-domain) into the new project's README.

When an GSA project has a non-standard license status (e.g. it's a fork of a previously licensed project, or is a module/plugin for a GPL project), then that project needs to figure out an appropriate contributing agreement.

### Working in public

GSA believes in [working in public](https://18f.gsa.gov/2014/07/31/working-in-public-from-day-1/). It creates a healthier working environment, a more collaborative process, and just better software.

All GSA team members are expected to make new source code repositories public from the time of creation. This means we often publish drafts in our repos that may change substantially. If you're interested in learning more about the contents of a repo, email cto@gsa.gov and we'll direct you to the right person or team.

### Protecting sensitive information

As part of responsibly working in the open, GSA team members are expected to protect information that needs to be protected. We already receive training and guidance about information we can’t publish for [ethical](https://www.oge.gov/web/oge.nsf/Topics), [legal](https://handbook.18f.gov/intro-to-18f-infrastructure/), and [security](https://insite.gsa.gov/portal/content/627226) reasons — this section is a reminder about sensitive information (formally called “[controlled unclassified information](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-171.pdf)”) to carefully protect when working with our open source projects. Sensitive information can include code, configuration, content, or documentation. (We have [approved options for sharing sensitive information](https://handbook.18f.gov/sensitive-information/).)

If GSA team members aren't sure whether they should make something public, they should ask a person on our CTO Digital Service team for advice _first_. (Ask through cto@gsa.gov)

If GSA team members inadvertently come into the possession of classified information (Secret, Top Secret, etc.), they should immediately report it to the supervisor and agency CISO.

Sensitive information we need to protect includes, but is not limited to:

* Information an attacker could plausibly use to help them compromise any system (including a prototype/development system). Examples:
    * **Secret keys:** Passwords, passcodes, access codes, access tokens, API keys, TLS keys, SSH keys, OAuth secrets, or any other “secret keys” that protect access to something.
    * **Undisclosed vulnerabilities:** If we know of a security problem or potential security problem with our code that isn’t already publicly-known (such as a vulnerability that can’t be found with a publicly-available open source scanning tool run on the public-facing system), we shouldn’t write publicly about it until we fix it.
* Nonpublic information in general about vulnerabilities, including attribution/source information (such as how and when we learned about a vulnerability, if the disclosure to us was not public).
* We may wish to withhold some non-GSA IP addresses. If something looks like an IP address, ask GSA IT security before publishing that info.
* Personally Identifiable Information (PII). Here’s [OMB's definition and GSA's policy](http://www.gsa.gov/portal/content/104256). 18F also has [guidance for systems involving PII](https://pages.18f.gov/before-you-ship/security/pii/).
* Some kinds of procurement and acquisition information, which may include non-public cost or pricing data, contract information, trade secrets, indirect costs, and direct labor rates.
* Emergency procedures, such as evacuation plans.

There are more categories of controlled unclassified information to protect; those are just the kinds that we work with most often. [Here’s the complete list.](https://www.archives.gov/cui/registry)

### Managing GSA resources

GSA intends to produce great software for the American people. That means not just rushing through projects to get them working as fast as possible, but managing [technical debt](https://en.wikipedia.org/wiki/Technical_debt) with an eye towards usability and reusability.

If a refactoring or feature makes the tool easier for GSA to use in its work, and the teammate doing it is otherwise meeting their duties, then that's time well spent for GSA and the taxpayer.

Open source projects can &mdash; and hopefully do! &mdash; get use and uptake from outside GSA.

When creating new open source projects:

* If you're creating a repo because it's primarily for your GSA work, and the work you perform in it is primarily to benefit GSA, start the repo's life in the GSA organization.
* If you're creating a repo for personal use, this is okay and hopefully will result in useable code for the agency as well.  You may use the GitHub/GSA organization but should most likely use your personal GitHub accont.  Use your discretion and consider our internal ethics policies.
* If you're creating a repo and plan to make it private for all or some of it's life, you should consult cto@gsa.gov and the GitHub manager to discuss applicability and cost.  This is a **strongly discouraged** path to open source or to code management/development in general.

As people open issues and request features continue to exercise professional judgment about how to spend GSA time.

### Deprecating a repository

When a repository is no longer useful, it should be deprecated. This may be because the work has been incorporated into another repository, the project is unmaintained and out-of-date, or some other reason.

In order to preserve repository metadata like pull request discussions and issues, the repository should not be deleted or made private. Instead, a prominent deprecation notice should be added. This notice should include the project's status as deprecated, a reason for the deprecation, and (if applicable) a link to the repository where work is continuing.

The deprecation notice should be added to the top of the project's `README`, and the description field should be changed to reflect the project's status as deprecated.
