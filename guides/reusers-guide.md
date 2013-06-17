# Re-users Guide to the Open Data Rights Statement Vocabulary

This guide discusses how to process machine-readable rights statements that have been published using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/odrs/) (ODRS). 

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. As a re-user of Open Data you should ensure that your usage conforms to those rights. This includes making efforts to ensure that you properly attribute your sources.

The [Publishers Guide to the Open Data Rights Statement Vocabulary](https://github.com/theodi/open-data-licensing/blob/master/guides/publisher-guide.md), provides an introduction to the ODRS vocabulary and includes a number of worked examples. You should read that guide to introduce the basic concepts behind the vocabulary.

The ODRS github project includes some [additional standalone examples](https://github.com/theodi/open-data-licensing/tree/master/examples) that can be used a further reference.

This guide provides some advice on how to use metadata published in the ODRS vocabulary within your applications to help simplify the process of attributing sources of data.

## Discovering Rights Statements

Publishers should be exposing structured metadata about their datasets using standard formats such as the [Data Catalog vocabulary](http://www.w3.org/TR/vocab-dcat/) (DCAT) or [VoID](http://www.w3.org/TR/void/). 

As described in [the publisher guide](https://github.com/theodi/open-data-licensing/blob/master/guides/publisher-guide.md) there are two standard properties that can be used to reference licensing and rights information:

* `dct:license` -- existing practice is for this property to refer to a license that applies to the dataset
* `dct:rights` -- this property can be used to refer to a `odrs:RightsStatement` resource that provides a fuller description of a Rights Statement.

In most cases these properties are the starting point for discovering machine-readable rights metadata.

A `odrs:RightsStatement` resource may have several properties that can be useful in your application:

* `odrs:copyrightNotice` and `odrs:copyrightStatement` properties respectively provide the text or a link to a copyright statement that applies to the dataset you are using. Some licences, including the Creative Commons licenses, require you to preserve copyright notices published by the data publisher. These properties allow you to include a short notice in your application or a link to a longer description. You might typically include this in a colophon page that describes your application
* the `attributionText` and `attributionURL` properties provide the necessary information for building an attribution link

The machine-readable description of Rights Statement might be included alongside a description of a dataset, e.g. as embedded metadata expressed using RDFa. However the rights statement might also be published separately, e.g. as a standalone web page or document that is referenced by several datasets.

Rights information can also be referenced directly from individual documents, e.g. using [the `atom:link` element](http://tools.ietf.org/html/rfc4287#page-21) or in an HTML `link` element. 

Web APIs might also include HTTP `Link` Headers, as defined by [RFC 5988](http://tools.ietf.org/html/rfc5988), that refer to rights information, e.g:

	Link: <http://opendatacommons.org/licenses/odbl/>; rel="license", 
	      <http://api.example.org/docs/rights>; rel="http://purl.org/dc/terms/rights"

In short, while the structure of a rights statement is defined by the ODRS vocabulary there are several different locations in which references to that metadata might be included, either alongside a description of the data or by reference. When processing the data in your application you should ensure to fetch (and cache) any additional resources.

## Attributing Datasets

The [publisher guide](https://github.com/theodi/open-data-licensing/blob/master/guides/publisher-guide.md) discusses attribution and citation. While closely related, there are two slightly different use cases:

* _Attribution_ -- giving credit to the creator and/or maintainer of a dataset in order to acknowledge that their contribution to your application
* _Citation_ -- linking to a source dataset that you have used in your application, or some analysis, or which are components of a large aggregated dataset that you might be distributing to others

Attribution is often a legal requirement that is included in Open Data licenses. This means that you must attribute your sources to stay within the terms of the license. In addition you may need to preserve any copyright notices that are provided by the publisher.

Citation is often more detailed than attribution. A clear provenance statement, e.g. a list of data sources, can help users trust your application or attempt to reproduce your analysis.

The ODRS includes properties that help you to build attribution links, find copyright statements and, as a component of additional dataset metadata, publish citations.

### Building Attribution Links

Attribution should be simple and straight-forward. Even when a data license does not require attribution, you should attempt to acknowledge your sources.

The simplest form of attribution is to include a simple link in your application. For example:

    Uses data supplied by <a href="http://example.org/attribution-link">Example Company</a>

The following steps suggest a simple algorithm for building an attribution link:

1. Find the text to use as the anchor of the link:
    1. If the publisher has provided an `odrs:attributionText` property then use its value, otherwise
    2. If the dataset references a publisher via a `dct:publisher` property then use the `foaf:name` of the publisher
    3. If the dataset has a title property (`dct:title`) then use that
2. Find the URL to use as the target of the link:
    1. If the publisher has provided an `odrs:attributionURL` property then use that URI, otherwise
    2. If the dataset references a publisher via a `dct:publisher` property then use its `foaf:homepage` property
    3. If the dataset has a `dcat:landingPage` property then use that, else
    4. Use the URI of the dataset

The approach given here is to use the preferred attribution text and URL provided by the publisher but fall back to using other dataset metadata if that is not available. A publisher may wish to direct attribution links to a particular target page to help track usage of their data (to justify ongoing publishing efforts) or to support attribution and acknowledgement of _their_ sources.

The approach is applicable to any number of different approaches for publishing data. However for applications that are consuming and displaying Linked Data the recommendation is to also include direct links to any resources mentioned in your application. For example applications that use the Ordnance Survey Linked Data should directly link to the relevant Ordnance Survey resources, e.g. [Bath](http://data.ordnancesurvey.co.uk/id/7000000000024979) where possible. 

However this kind of attribution is not always feasible, e.g. if a data view draws from dozens of different sources or if the UX of the application might be impacted. For this reason the recommendation is to always include the basic attribution link and add "deep links" on a best effort basis.

### Where To Display Links

Attribution links should be displayed as close as possible to where the data is being displayed:

* If your application uses a single primary dataset across the whole application, then include an attribution link in the footer of the application
* If your application uses several datasets, then consider displaying an attribution next to a logical grouping of data items. For example if you display an "infobox" that provides some additional metadata, then include an attribution link in the infobox
* If your application draws on many different datasets then add a [colophon](http://en.wikipedia.org/wiki/Colophon_(publishing)) page that attributes each of the datasets
* If your application consumes multiple datasets but doesn't display the results directly to users then you should still include attribution, e.g. in a colophon

Even when you application only uses one or a few datasets you may want to consider adding a colophon page that provides additional detail on the datasets you're using. This can be used to include copyright notices and perhaps a dataset citation.

## Citing Datasets

Citation is usually more detailed than attribution and is intended to help support your users in:

* Understanding precisely which datasets you are using -- you may be using and attributing several datasets from a single source
* Obtaining those datasets for themselves -- e.g. to recreate your analysis, build their own application, or to report issues with the data

Dataset citations should include an attribution link, as well as more detailed metadata including:

* The title of the dataset and a link to its homepage
* The version of the dataset being used. E.g. its `dct:issued` or `dct:modified` dates
* The name of the publisher
* A link to the specific [distribution](http://www.w3.org/TR/vocab-dcat/#class-distribution) used and the date it was obtained, if the distribution isn't versioned
* References to the Rights Statement that applies to the re-use of the data

The precise format of the link will depend on the needs of your application and users, as well as the detailed metadata available for the dataset.


