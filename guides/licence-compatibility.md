# Understanding Licence Compatibility

Both re-users and publishers of open data often need to understand whether the licenses that are applied to datasets are "compatible". For example:

* Can some data published with License X be combined with some additional data published under License Y?
* What license(s) could be applied to a derived or aggregated dataset?
* Are there provisions associated with a license that inhibit or constrain the creation and publication of derivations?

This document gathers together pointers and discussion on existing work in this area, with the intention of providing some help/insight for both data publishers and re-users.

**Note**: This document has not been created by a legal expert and its contents should not be taken as legal guidance. When in doubt, consult the terms of the specific licenses that apply to the datasets you are using. Legal input/review is welcomed.

## What is Compatibility?

It can be hard to define compatibility as there are often nuances to to take into account.

The Creative Commons (CC) [define licenses as compatible](http://creativecommons.org/compatiblelicenses) when:

> ...they, at a minimum, contain terms that have the same purpose, meaning and effect as the key license elements of a particular Creative Commons license and when a license explicitly permits the relicensing of derivatives of works made available under that license under a particular Creative Commons license.

However to date the Creative Commons have not approved any licenses as being compatible.

This article on [copyleft and license compatibility](http://opensource.com/law/11/9/mpl-20-copyleft-and-license-compatibility) provides some good background, noting that:

> "compatible" generally means "one-way" compatibility, where code from a more permissive license can be used as part of a project whose overall license is more restrictive, but not vice versa

The fuller definition of compatibility given in that document is worth reviewing:

> To be slightly more precise, one can say that permissive License P is one-way compatible with restrictive License R when:

> * Anyone who complies with all requirements of License R would also comply with all requirements of License P.
> * Everything permitted by License P is also permitted by License R.

> In other words, License P and License R are compatible if, as long as you play by the more restrictive rules set by License R, you'll also be playing by the rules set by the more permissive License P

However compatibility might be of a limited nature. For example the GNU Free Documentation License was revised to make it compatible with the CC-BY-SA license, for a limited period for specific types of publication. This was to enable [the re-licensing of Wikipedia under a Creative Commons license](http://en.wikipedia.org/wiki/GNU_Free_Documentation_License#Compatibility_with_Creative_Commons_licensing_terms).

## Use Cases

There are several related use cases that are behind most discussions of compatibility:

* _License Alignment_ -- The authors of open licenses may want to ensure that data or content published under a specific license can be remixed with other sources. Aligning the terms of a license can help ensure this. For example the recently published [Open Government License 2.0](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) declares that it has been aligned with the CC-BY and ODbL licenses
* _License Selection_ -- publishers of open data want to understand how licenses align in order to ensure that re-users have the greatest amount of freedom, or to ensure that certain types of usage are restricted
* _Re-licensing_ -- a publisher may wish to switch to an alternative, but compatible license, e.g. as Wikimedia Foundation did with the Wikipedia content.
* _Publication of Derivative Works_ -- creators of derived works need to understand how their derivatives (or adaptations or aggregates) can be licensed and distributed. There are some additional nuances here depending on how the derivative is created.

It is worth noting that some open licenses explicitly restrict the right to sub-license a work, e.g. it is not possible to take a dataset published under a Creative Commons license and then distribute the same dataset under a different license. The original license always applies to the original work.

Compatibility is most relevant when considering re-publication of data, e.g. as a derivative. Using data purely for personal use or internally within an organisation doesn't raise issues of compatibility: your re-use just need to obey the terms of the original license, e.g. attribution or non-commercial clauses.

When you are distributing a derived work, e.g. a derived dataset or aggregation, then there are additional considerations: the license that can be applied to the derivative may be constrained by the license(s) that are applied to the original data. Obviously some licenses may preclude the creation of derivatives altogether.

## License Attribute Matrix

The most important step towards understanding compatibility in more detail is to understand the basic provisions of each license.

The [Creative Commons Rights Expression Language](http://creativecommons.org/ns) defines some basic facets of licenses, covering Permissions, Requirements and Prohibitions. As the CC licenses are already described using these facets, which are also common to many other licenses, it is possible to put together a matrix that identifies which facets apply to which licenses.

**[Table 1](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=0&output=html)** summarises how a number of licenses can be classified based on these facets.

There are several things to note here:

* The _Share Alike_ requirement requires that derived data is published under the same terms or compatible terms as the original. This means that some forms of remix are prohibited unless license terms are compatible.
* The _Derivative Works_ prohibition limits re-users from distributing any form of derivative work at all. Although aggregations in which the original is preserved may still be allowed.

When it comes to publishing derivatives there are, broadly, two different scenarios to consider: publishing a simple derivative based on a single source, or publishing a remix of several datasets.

These scenarios are covered in the following sections.

## Simple Derivative Matrix

In this scenario a re-user is taking a single source dataset which is then adapated, transformed, or edited in some form in order to create a new dataset. The input is a single dataset and some effort from the re-user. The output is one or more new datasets. 

The re-user needs to only understand the terms of a single license and their own desire to publish their work openly.

**[Table 2](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=1&output=html)** -- provides a matrix that indicates permitted licenses that can be used for this type of derivative.

In Table 2 each cell provides a Yes or No answer as to whether this license could be used to license the derivative work.

Note: Table 2 has been adapted from [this original matrix created by Kaitlin Thaney](http://www.slideshare.net/kaythaney/data-sharing-social-and-normative-iswc/49) but has been updated to include additional licenses.

Unsurprisingly, those licenses with the most permissions and least requirements and prohibitions, provide the most flexibility for re-users to decide how to license their work.

## Remixed Dataset Matrix

In this scenario multiple datasets are combined to create a new derived dataset. For example the data might be combined and linked to create a new aggregate dataset. Because the source datasets might use different licenses, then a re-user may need to obey multiple terms. In some cases these might be incompatible. 

For example its not possible to create remixes that use sources published under the CC-BY-SA and CC-BY-NC-SA licenses: a re-user can't obey the requirements of both licenses as the non-commercial clause isn't compatible.

**[Table 3](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=2&output=html)** -- provides a matrix that indicates the "minimum" license that can be applied to the derivative.

For example:

* There are no restrictions on publishing remixes that use only public domain (CC0, PDDL) sources
* Whereas, if a public domain (CC0, PDDL) source is combined with a CC-BY-SA source, then the derivative must also be published under a CC-BY-SA license or one which also includes requirements for attribution and sharealike.
* Additionally, works licensed under the Open Data Commons Open Database License (ODbL) cannot be used in combination with works licensed under the CC-BY-NC license: the non-commercial prohibition on the CC-BY-NC license is at odds with the sharealike provision of the ODbL license

Note: Table 3 is partly derived from this [original comparison](http://wiki.creativecommons.org/Wiki/cc_license_compatibility) published by the Creative Commons. The original has been extended to include additional licenses.

## Further Work

Some additional work needs to be undertaken to explore some of these issues further. For example the matrices need further review by experts.

The matrices could also be used to create tools, like this [CC License Compatibility Wizard](http://www.web2rights.com/OERIPRSupport/creativecommons/), to help both publishers and re-users to understand the impacts of particular licensing conditions.

It is important that this work addresses all licenses that re-users are likely to encounter, e.g from the Creative Commons, Open Data Commons and various government licensing agencies.
