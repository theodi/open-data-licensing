# Publisher Guide to the Open Data Rights Statement Vocabulary

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. A clear statement of rights can ensure that data re-users fully understand the potential for re-use of a dataset, whether it is suitable for their purposes, and any obligations that may incur through using the data.

This guide describes how to publish machine-readable rights statements using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/open-data-licensing/). The guide includes a number of worked examples that illustrate how to use the vocabulary to publish a variety of different rights statements using a number of different serializations.

A separate document, the [Re-users Guide to the Open Data Rights Statement Vocabulary](), provides advice on how to process and use these rights statements within applications.

## Vocabulary Overview

There are three key concepts required to understand the Open Data Rights Statement (ODRS) Vocabulary: _Datasets_, _Rights Statements_ and _Licenses_.

The vocabulary deliberates avoids providing a single definition of a dataset, this allows it to be freely used alongside other vocabularies and in a variety of data publishing contexts. However for the purposes of this document, the [Data Catalog Vocabulary](http://www.w3.org/TR/vocab-dcat/#class-dataset) (DCAT) provides a useful working [definition of a dataset](http://www.w3.org/TR/vocab-dcat/#class-dataset):

>A collection of data, published or curated by a single source, and available for access or download in one or more formats.

On intended use of the ODRS vocabulary is to provide a more detailed description of the rights associated with a Dataset described using the DCAT vocabulary.

A _Dataset_ is usually associated with a _License_. The ODRS vocabulary uses a broad definition of license which is intended to cover any legal document that describe re-use rights up to an including a complete waiver of rights (e.g. a public domain dedication):

>A legal document that describes the legal terms for re-use of some information. A license might apply to either content or data. It might also be a waiver document that indicates that the owner waives all rights they may have over the information.

The ODRS vocabulary does not provide a machine-readable description of licensing terms. The Creative Commons vocabulary (ccRel) provides the necessary terms for describing this aspect of licensing. ODRS is instead focused on describing _Rights Statements_ which are used to describe the application of a _License_ to a _Dataset_.

In some juristictions, particularly the EU, a dataset might actually have several licenses associated with it:

* A Dataset License, e.g. the Open Database License, that covers reuse of the dataset
* A Content License, e.g. the Open Database Content License, that covers re-use of the contents of a dataset

A _Rights Statement_ is a resource that amongst other things, describes the relationship between a _Dataset_ and its _Licenses_. A statement of rights will typically include some or all of the following information:

* A reference to a Dataset License
* A reference to a Content License (where applicable)
* Notices, e.g. copyright notices, that should be preserved by re-users
* Guidance on a means of attributing the source of the data, e.g. when re-used in an application
* Pointers to further information, e.g. further guidance on re-use or details on how to acquire additional rights

The description of a License, such as the UK Open Government License, remains unchanged no matter how it is used or applied by an organisation. It is the Rights Statement that captures the context of its re-use by an organisation, including descriptions of relevant notices, attribution guidance and other relevant relationships.

A Rights Statement might apply to an individual Dataset. But it could equally be applied to several Datasets, e.g. if an organization publishes data under a consistent set of rights.

### Attribution versus Citation

Publishers often want to be acknowledged for producing and publishing data. Data re-users often need to refer to their data sources. There are two related, but relatively distinct use cases:

* Attribution -- giving credit to the creator and/or maintainer of a dataset
* Citation -- linking to a source dataset that has been used in some analysis or is a component of an aggregated dataset

Many communities have existing norms around both attribution and citation. Many licenses allow publishers to require attribution when a dataset is re-used, but it can be unclear how this should be achieved.

Citation usually involves linking to the individual dataset, or version of a dataset, that has been used. Citation use cases are already well supported by existing dataset metadata vocabularies, as they typically cover titles, versioning information (including publication dates), dataset URLs, download locations, etc.

ODRS provides two terms to support attribution use cases, where the goal is to typically acknowledge the dataset creator by name, often with a link to either the dataset homepage or a specific attribution or acknowledgement page

* `attributionText` -- the name to be used when attributing the creator of some data. This might differ from the name of the organization that published the data. E.g "Ministry of Justice", or "Wikipedia Community"
* `attributionURL` -- the URL to be used when building an attribution link. The expectation is that the link text will be the `attributionName`.

We encourage publishers to keep attribution text as short as possible, recognising that their data may get re-used in a wide variety of locations. The ability to provide a specific destination page for attribution links makes it easier to avoid "attribution stacking" that can make attribution and re-use difficult.

The ODRS vocabularly also includes a `copyrightNotice` term that can be used to capture specific copyright statements that should be preserved by re-users.

Both attribution and citation are expected to be community norms. Publishers should recognise that community norms around formlinking to sources is likely to vary across communities, e.g. between web application developers and scientific researchers. The goal for machine-readable metadata is to ensure that the data required to support these use cases is easily accessible to re-users without the need to read detailed attribution guidelines. 

## Worked Examples

The following sections provide examples of using the ODRS vocabularly in a variety of ways. The initial examples which introduce the core terms all use the Turtle RDF serialization, although later examples include illustrations that use JSON-LD, RDFa, and other formats.

The github project that supports this vocabularly includes some [additional standalone examples](https://github.com/theodi/open-data-licensing/tree/master/examples).

For clarity many of the examples below omit prefix definitions from RDF terms. The full set of prefixes used in the examples is given below:

	TODO: prefixes

### Single License

The following example illustrates how to associate a rights statement with a DCAT dataset:

	:example1
		a dcat:Dataset ;
		dct:title "Court Cases Dataset" ;
		dct:rights :example1-rights-statement;
		dct:license <http://reference.data.gov.uk/id/open-government-licence>.

	:example1-rights-statement
		a odrs:RightsStatement;
		rdfs:label "Rights relating to re-use of the Court Cases Dataset" ;
		odrs:dataLicense <http://reference.data.gov.uk/id/open-government-licence> ;
		odrs:attributionText "Ministry of Justice" ;
		odrs:attributionURL <https://www.gov.uk/government/organisations/ministry-of-justice>
	   
The rights statement is associated with its dataset using the Dublin Core `dct:rights` relationship. The Rights Statement for the dataset has a label and several properties from the ODRS vocabulary. The `odrs:dataLicense` property indicates which license covers the re-use of the dataset, in this case it refers to the UK [Open Government License](http://www.nationalarchives.gov.uk/doc/open-government-licence/). As part of the rights statement, the publisher of the dataset has provided the text and URL that re-users can use to attribute the publisher.

In addition to the `dct:rights` property the dataset has also been directly associated with the Open Government License via the Dublin Core `dct:license` property. This property is already in relatively common use for relating datasets with their licenses and it is recommended that publishers include it for compatibility with existing applications. However, as the next example shows, a Rights Statement allows for greater clarity when associating a dataset with both a data and a content license.

### Multiple Licenses

In some circumstances there are different rights that relate to a dataset (or database) as a whole, and the contents of that database. The following example illustrates how to relate a dataset to multiple licenses one for the data domain and one for the content domain:

	:example2
		a dcat:Dataset ;
		dct:title "Open Products" ;
		dct:rights :example2-rights-statement;
		dct:license <http://opendatacommons.org/licenses/odbl/1.0/>.

	:example2-rights-statement
		a odrs:RightsStatement;
		rdfs:label "Rights relating to re-use of the Open Products Dataset" ;
		odrs:dataLicense <http://opendatacommons.org/licenses/odbl/1.0/> ;
		odrs:contentLicense <http://opendatacommons.org/licenses/dbcl/1.0/> ;
		odrs:attributionText "the Open Products community" ;
		odrs:attributionURL <http://example.org/open-products>

The two licenses are distinguished through the use of the `odrs:dataLicense` and `odrs:contentLicense` properties. In this example the properties refer to the [Open Database License](http://opendatacommons.org/licenses/odbl/) and the [Open Database Content License](http://opendatacommons.org/licenses/dbcl/). In other scenarios the content of a database might be licensed under a Creative Commons License.

### Copyright Notices

The following example illustrates how to include a copyright notice as part of a Rights Statement. For example a dataset or its contents might be licensed under a Creative Commons license, but the publisher still retains their copyright in the content. Creative Commons licenses indicate that re-users should retain any notices that are provided by a publisher.

The ODRS vocabulary captures copyright information separately to attribution text, making it easier for applications to extract and display the relevant information.

The following example illustrates how the Ordnance Survey Open Data might have been described using the ODRS vocabulary:

	<http://data.ordnancesurvey.co.uk/id/data/os-linked-data> 
		rdf:type void:Dataset ;
		dct:title "Ordnance Survey Linked Data" ;
		dct:license <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf> ;
		dct:rights 	:example3-rights-statement;

	:example3-rights-statement
		a odil:RightsStatement;
		odil:dataLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odil:contentLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odil:copyrightNotice "Contains Ordnance Survey data © Crown copyright and database right 2013. Contains Royal Mail data © Royal Mail copyright and database right 2013. Contains National Statistics data © Crown copyright and database right 2013." ;
		odil:attributionText "Ordnance Survey";
		odil:attributionURL "http://ordnancesurvey.co.uk".

The Rights Statement includes a `odil:copyrightNotice` property in addition to the attribution properties used in previous examples. An application might choose to display the copyright notice differently to the attribution text, e.g. including it in a general copyright notice section of the application website.

### Rights Statements in RDFa

	TODO: DIODD example

### Rights Statements in JSON-LD

	TODO: DIODD example in JSON-LD

### Rights Statements in simple JSON

	{
		"rights": {
			"dataLicense": "...",
			"contentLicense": "...",
			"copyrightNotice": "...",
			"attributionText": "...",
			"attributionURL": "..."
		}
	}

Or, alternatively, referencing an external definition, in which case the value of the rights key is a simple literal not a property

	{
		"rights": "...url..."
	}

### Rights Statements in XML

TODO: Namespaced XML, using ODRS vocabulary

### Rights Statements in HTTP API Responses

	Link: <http://opendatacommons.org/licenses/odbl/>; rel="license", 
	<http://example.org/rights-statement/1>; rel="http://purl.org/dc/terms/rights",


