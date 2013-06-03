# Re-users Guide to the Open Data Rights Statement Vocabulary

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. A clear statement of rights can ensure that data re-users fully understand the potential for re-use of a dataset, whether it is suitable for their purposes, and any obligations that may incur through using the data.

This guide provides some guidance on how to process machine-readable rights statements that have been published using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/open-data-licensing/).

A separate document, the [Publishers Guide to the Open Data Rights Statement Vocabulary](), provides advice on how to publish machine-readable rights statements as well as an overview of the vocabulary as a whole. This document focuses on how application developers should use and interpret such data.

## Discovering Rights Statements

Which properties to look for:

* `dct:rights` associated with dataset metadata. Make reference to ways to discover datasets
* `Link` header in API responses: useful for filtering data aggregation without commiting to terms, etc.

## Attribution vs Citation

* How to build attribution link, e.g. from `odrs:attributionName` and `odrs:attributionURL` properties
* How to build citations using more of the dataset metadata
* Suggestions as to how to display attributions
* Copyright notices: How to find them, suggestions on how to display them, e.g. as part of a terms of use on website, or colophon



