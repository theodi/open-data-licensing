# Introduction

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. 

While legal requirements vary across juristictions, a statement of rights will typically include some or all of the following information:

* A reference to a license or waiver that relates to re-use of the dataset
* A reference to a license or waiver that relates to re-use of the contents of the dataset, e.g where that content is covered by copyright
* Notices, e.g. copyright notices, that should be preserved by re-users
* Guidance on a means of attributing the source of the data, e.g. when re-used in an application
* Pointers to further information, e.g. further guidance on re-use or details on how to acquire additional rights

The Open Data Rights Statement vocabulary is intended to support the publication of machine-readable rights statements. The vocabulary builds on related work from the Dublin Core and Creative Commons communities and is intended to complement ongoing efforts to improve the quality of machine-readable dataset metadata. It is expected that the vocabulary will be useful in a number of contexts, e.g. for Linked Data publishing ([DCAT](http://www.w3.org/TR/vocab-dcat/), [VoiD](http://www.w3.org/TR/void/)), dataset distribution ([Data Packages](http://www.dataprotocols.org/en/latest/data-packages.html)), as well as data published via web APIs.

The following sections of the document provide more background on the vocabulary, including references to relevant related work.

## Related Work

There are several existing vocabularies cover similar goals, but all have their limitations. The Open Data Rights Statement vocabulary builds on this earlier work to support clearer publication of rights information.

* [Dublin Core](http://dublincore.org/documents/dcmi-terms/) distinguishes between a license (`dct:License`) and a rights statement (`dct:RightsStatement`) and provides terms for relating a work to a machine-readable descriptions of these documents using the `dct:rights` and `dct:license` properties.
* The [Creative Commons vocabulary](http://creativecommons.org/ns) (ccRel) supports the publication of machine-readable descriptions of broad classes of requirements, permissions and prohibitions that are associated with licenses. It also includes some terms to support attribution.
* The [Waiver](http://vocab.org/waiver/terms/.html) vocabulary supports the association of public domain waivers and community norms with a dataset

These vocabularies provide some necessary foundations for publishing rights statements, but each has its own limitations

## Design Rationale

The key limitations with the existing vocabularies are:

* There is no recognition of the need to separately license a database and its contents. Even outside of the EU, it is entirely possible that the content of a database is covered by a separate license to its structure. Where required there should be unambiguous ways to link to more than one license or waiver
* An unclear distinction between descriptions of a re-usable license; a rights statement which might apply to several datasets, and the specific rights associated with an individual dataset. This leads to some confusion around how best to publish attribution requirements, copyright notices, etc.

The intention is that this vocabulary should allow data publisher to publish, as machine-readable metadata, the following information:

* A license or waiver that applies to the database/data being published
* A license or waiver that applies to the content of a database, where is needs to be separately recorded
* Copyright notices
* Guidance on attribution requirements
* Pointers to additional material, e.g. notes on usage of a license, additional terms, etc.

The approach taken here borrows from Dublin Core and introduces a "Rights Statement" as a resource that relates a dataset to one or more Licenses as well as providing additional context that relates to re-use of a dataset.

The description of a License, such as the UK Open Government License, remains unchanged no matter how it is used or applied by an organisation. It is the Rights Statement that captures this customisation and description of copyright, attribution and other relevant relationships.

A Rights Statement might apply to an individual Dataset. But it could equally be applied to several Datasets, e.g. if an organization has a common set of attribution requirements.

The vocabulary does not provide a definition of dataset. This is intentionally under-specified to support the use of the vocabulary in a number of ways. The existing [Dublin Core](http://dublincore.org/documents/dcmi-terms/) terms (`dct:rights` and `dct:license`) can be used to relate a dataset to a `odil:RightsStatement` or a license.

Similarly, this vocabulary intentionally does not attempt to support the machine-readable description of the terms of a specific license. This is already adequately covered by the [ccRel](http://creativecommons.org/ns) vocabulary.

## Schema Diagram

The following diagram shows the key resources, relationships and properties defined by this vocabulary.

![Schema diagram](diagram.png)

