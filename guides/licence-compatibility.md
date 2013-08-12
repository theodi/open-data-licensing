# Licence Compatibility

Both re-users and publishers of open data often need to understand whether the licenses that are applied to datasets are "compatible". For example:

* Can some data published with Licence X be combined with some additional data published under Licence Y?
* What license(s) could be applied to a derived or aggregated dataset?
* Are there provisions associated with a licence that inhibit or constrain the creation and publication of derivations?

This document gathers together pointers and discussion on existing work in this area, with the intention of providing some help/insight for both data publishers and re-users.

**Note**: This document has not been created by a legal expert and its contents should not be taken as legal guidance. When in doubt, consult the terms of the specific licenses that apply to the datasets you are using. Legal input/review is welcomed.

This document is intended to provide guidance and discussion on mixing together data that may be published under different licences. It does not provide a general background on data licences or choosing and applying licences. The Open Data Institute have produced two guide that provide useful background reading for this document:

* [Publisher's Guide to Open Data Licensing](http://theodi.org/guide/publishers-guide-open-data-licensing) -- the sections "What Do You Own", and "What Are Open Licenses" are particularly relevant
* [Reuser's Guide to Open Data Licensing](http://theodi.org/guide/reusers-guide-open-data-licensing) -- the section "What Can't You Do" is relevant to the process of creating and using licensed data.

## What is Compatibility?

It can be hard to define compatibility as there are often nuances to to take into account.

The Creative Commons (CC) [define licenses as compatible](http://creativecommons.org/compatiblelicenses) when:

> ...they, at a minimum, contain terms that have the same purpose, meaning and effect as the key license elements of a particular Creative Commons license and when a license explicitly permits the relicensing of derivatives of works made available under that license under a particular Creative Commons license.

However to date the Creative Commons have not yet [officially approved](http://creativecommons.org/compatiblelicenses) any licenses as being compatible.

This article on [copyleft and license compatibility](http://opensource.com/law/11/9/mpl-20-copyleft-and-license-compatibility) provides some good background, noting that:

> "compatible" generally means "one-way" compatibility, where code from a more permissive license can be used as part of a project whose overall license is more restrictive, but not vice versa

The fuller definition of compatibility given in that document is worth reviewing:

> To be slightly more precise, one can say that permissive License P is one-way compatible with restrictive License R when:

> * Anyone who complies with all requirements of License R would also comply with all requirements of License P.
> * Everything permitted by License P is also permitted by License R.

> In other words, License P and License R are compatible if, as long as you play by the more restrictive rules set by License R, you'll also be playing by the rules set by the more permissive License P

However compatibility might be of a limited nature. For example the GNU Free Documentation Licence was revised to make it compatible with the CC-BY-SA license, for a limited period for specific types of publication. This was to enable [the re-licensing of Wikipedia under a Creative Commons license](http://en.wikipedia.org/wiki/GNU_Free_Documentation_License#Compatibility_with_Creative_Commons_licensing_terms).

Within the Creative Commons suite of licenses the stance to [compatibility has changed over time](http://wiki.creativecommons.org/License_Versions#Compatible_licenses_may_be_used_for_adaptations_of_works_originally_offered_under_CC_ShareAlike_licenses). For example the 1.0 ShareAlike licences required that the exact same licence was used for adaptations. In the 2.x series of licences the wording was changed to make the licences forwards compatible: an adaptation could use a later version of the same licence. With the CC-BY-SA 3.0 licence the Creative Commons [broadened this definition further](http://wiki.creativecommons.org/Version_3#BY-SA_.E2.80.94_Compatibility_Structure_Introduced)
 to allow the Creative Commons to identify a range of compatible licences, although as noted this has not yet happened. (It is possible that the Creative Commons might identify the [Open Government License 2.0](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) as being compatible as it has been aligned with CC-BY 4.0).

## Who Defines Compatibility?

While this document attempts to provide some guidance on compatibility between licences a clear definition on licence compatibility can come from one of two places:

* The Licence Author -- as noted above, the Creative Commons are intending to publish a list of compatible licences; the [Open Government License 2.0](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) explicitly identifies several compatible licences
* The Publisher -- a publisher can release data under more than one licence or document which licences they consider to be compatible with their goals to publish and share data. The [Open Database Licence](http://opendatacommons.org/licenses/odbl/1.0/) states that publishers can designate a proxy who will determine whether licences are compatible

Ultimately while a legal perspective can be taken on whether the terms of two licences are compatible, it is the publisher who will have the final decision as they retain rights in their data.

## Compatibility Use Cases

There are several related use cases that relate to questions around licence compatibility:

* _Licence Alignment_ -- The authors of open licenses may want to ensure that data or content published under a specific licence can be remixed with other sources. Aligning the terms of a licence can help ensure this. For example the recently published [Open Government Licence 2.0](http://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/) declares that it has been aligned with the CC-BY and ODbL licenses
* _Licence Selection_ -- publishers of open data want to understand how licenses align in order to ensure that re-users have the greatest amount of freedom, or to ensure that certain types of usage are restricted
* _Re-licensing_ -- a publisher may wish to switch to an alternative, but compatible license, e.g. as Wikimedia Foundation did with the Wikipedia content.
* _Publication of Derivative Works_ -- creators of derived works need to understand how their derivatives (or adaptations or aggregates) can be licensed and distributed. There are some additional nuances here depending on how the derivative is created.

It is worth noting that some open licenses explicitly restrict the right to sub-license a work, e.g. it is not possible to take a dataset published under a Creative Commons licence and then distribute the same dataset under a different licence. The original licence always applies to the original work.

Compatibility is most relevant when considering distribution of data, e.g. as a derivative. When using data purely for personal use or internally within an organisation issues of compatibility are rarely relevant: your re-use just needs to obey the terms of the original license, e.g. attribution or non-commercial clauses.

When you are distributing a derived work, e.g. a derived dataset or aggregation, then there are additional considerations: the licence that can be applied to the derivative may be constrained by the license(s) that are applied to the original data. Obviously some licenses may preclude the creation of derivatives altogether.

## Licence Attribute Matrix

The most important step towards understanding compatibility in more detail is to understand the basic provisions of each license.

The [Creative Commons Rights Expression Language](http://creativecommons.org/ns) defines some basic facets of licenses, covering Permissions, Requirements and Prohibitions. As the CC licenses are already described using these facets, which are also common to many other licenses, it is possible to put together a matrix that identifies which facets apply to which licenses.

**[Table 1](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=0&output=html)** summarises how a number of licenses can be classified based on these facets.

There are several things to note here:

* The _Share Alike_ requirement requires that derived data is published under the same or compatible terms as the original. This places limits on how remixes can be distributed, i.e. only under compatible terms.
* The _Derivative Works_ prohibition limits re-users from distributing *any* form of derivative work at all. Even if those derivatives are not distributed. However it is still possible to include the database in a collection in which the original is preserved.

When it comes to publishing derivatives there are, broadly, two different scenarios to consider: 

1. publishing a simple derivative based on a single source, and
2. publishing a remix of several datasets. 

These scenarios are covered in the following sections.

Once a derivative has been created, then it too can be the source of additional derivation. Derivation is a process that can be repeated either by the original publisher (e.g. mixing in additional further datasets) or by third-parties (e.g to create new derivatives).

## Simple Derivative Matrix

In this scenario a re-user is taking a single source dataset which is then adapted, transformed, or edited in some form in order to create a new dataset. The input is a single dataset and some effort from the re-user. The output is one or more new datasets. 

The re-user needs to only understand the terms of a single licence and their own desire to publish their work openly.

**[Table 2](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=1&output=html)** -- provides a matrix that indicates permitted licenses that can be used for this type of derivative.

In Table 2 each cell provides a Yes or No answer as to whether this licence could be used to license the derivative work.

Note: Table 2 has been adapted from [this original matrix created by Kaitlin Thaney](http://www.slideshare.net/kaythaney/data-sharing-social-and-normative-iswc/49) but has been updated to include additional licenses.

Unsurprisingly, those licenses with the most permissions and least requirements and prohibitions, provide the most flexibility for re-users to decide how to licence their work.

## Remixed Dataset Matrix

In this scenario multiple datasets are combined to create a new derived dataset. For example the data might be combined and linked to create a new aggregate dataset. Because the source datasets might use different licenses, then a re-user may need to obey multiple terms. In some cases these might be incompatible. 

For example its not possible to mix together one dataset published under CC-BY-SA with another dataset published under CC-BY-NC-SA. A re-user can't obey the requirement of the CC-BY-SA licence to republish derived data under the CC-BY-SA and the requirement of the CC-BY-NC-SA licence to republish derived data under CC-BY-NC-SA.

**[Table 3](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=2&output=html)** -- provides a matrix that indicates the "minimum" licence that can be applied to the derivative.

For example:

* There are no restrictions on publishing remixes that use only public domain (CC0, PDDL) sources
* Whereas, if a public domain (CC0, PDDL) source is combined with a CC-BY-SA source, then the derivative must also be published under a CC-BY-SA licence or one which also includes requirements for attribution and sharealike.
* Additionally, works licensed under the Open Data Commons Open Database Licence (ODbL) cannot be used in combination with works licensed under the CC-BY-NC license: the non-commercial prohibition on the CC-BY-NC licence is at odds with the sharealike provision of the ODbL license

Note: Table 3 is partly derived from this [original comparison](http://wiki.creativecommons.org/Wiki/cc_license_compatibility) published by the Creative Commons. The original has been extended to include additional licenses.

## Database Rights and Creative Commons Licences

For the purposes of providing a simple overview, [Table 2](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=1&output=html) and [Table 3](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=2&output=html) largely treats the various licences as being interchangeable based on their key provisions (e.g. their prohibitions, permissions, etc). However in practice there are some additional issues to consider.

In the European Union data publishers may have both copyright and database rights over a database. Database rights are often referred to as 'Sui Generis' Database Rights (SGDRs). However [SGDRs are not covered by the unported Creative Commons 3.0 licences](http://wiki.creativecommons.org/Data#What_are_sui_generis_database_rights.3F). But are covered by some versions of the ported (jurisdiction specific) licences. This means that these licences cannot be used to license database rights and so are not suitable for fully licensing all types of data re-use in the EU. The Open Data Commons licences do cover these additional rights.

The Creative Commons are currently drafting the CC 4.0 licences. This currently includes [a change of approach to database rights](http://wiki.creativecommons.org/4.0/Sui_generis_database_rights). This suggests that thes CC 4.0 licences can be used to licence database rights in the EU. For example [the draft of the CC-BY 4.0 licence](http://mirrors.creativecommons.org/drafts/by_4.0d3.html) explicitly references and addresses re-use under database rights.

Ultimately then, when considering compatibility re-users will need to consider not just which licences are being combined, but also:

* The specific version of the licence that was applied to a dataset -- different versions may use different legal provisions that impact terms of use, including compatibility
* Whether the licence applies to all re-uses -- e.g. does it only cover re-uses that are covered by copyright, or does it also address database rights?
* Whether the licence is being applied to the database or its contents -- different licences may be used to licence a database and its contents

This creates additional complexity but it is hoped that the basic compatibility matrices defined here provide publishers and re-users with a useful starting point for assessing compatibility.

## Further Work

Additional work needs to be undertaken to explore these issues further. For example the matrices need further review by experts.

The matrices could also be used to create tools, like the [CC License Compatibility Wizard](http://www.web2rights.com/OERIPRSupport/creativecommons/), to help both publishers and re-users to understand the impacts of particular licensing conditions.

It is important that this work addresses all licences that re-users are likely to encounter, e.g from the Creative Commons, Open Data Commons and various government licensing agencies. While convergence on common licenses will hopefully continue, re-users are likely to be operating in a "mixed economy" for some time.

## Summary of Tables

* **[Table 1](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=0&output=html)** -- summarises key facets of common open licenses
* **[Table 2](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=1&output=html)** -- indicates which licences can be used when publishing simple single-source derivatives
* **[Table 3](https://docs.google.com/spreadsheet/pub?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&single=true&gid=2&output=html)** -- provides a matrix that indicates the "minimum" licence that can be applied when publishing derivatives created from 2 or more datasets

The tables are held in a single Google spreadsheet. You can [comment directly on the spreadsheet](https://docs.google.com/spreadsheet/ccc?key=0AiswT8ko8hb4dEJ6VVhYamlNMWo5WHpSV3IzVzAtZkE&usp=sharing) to make comments or highlight issues.


