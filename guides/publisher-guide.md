# Publisher Guide to the Open Data Rights Statement Vocabulary

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. A clear statement of rights can ensure that data re-users fully understand the potential for re-use of a dataset, whether it is suitable for their purposes, and any obligations that may incur through using the data.

This guide describes how to publish machine-readable rights statements using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/open-data-licensing/). The guide includes a number of worked examples that illustrate how to use the vocabulary to publish a variety of different rights statements using a number of different serializations.

A separate document, the [Re-users Guide to the Open Data Rights Statement Vocabulary](), provides advice on how to process and use these rights statements within applications.

## Overview of the ODRS Vocabulary

There are three key concepts required to understand the Open Data Rights Statement (ODRS) Vocabulary: _Datasets_, _Rights Statements_ and _Licences_.

While the ODRS vocabulary has been formally defined as a vocabulary using [OWL](http://www.w3.org/TR/owl2-overview/) its use is not limited to the publication of Linked Data or RDF. The vocabulary can also be viewed as a simple conceptual framework for understanding the relationships between datasets, licences and rights statements. This framework can be used to structure metadata that might be published in a number of different formats, e.g. using simple JSON based data formats or as an extension to an existing XML schema.

### Datasets

There are many different definitions of the term "dataset": different communities define the boundaries of a dataset very differently. The ODRS vocabulary deliberates avoids adopting a single definition in order to allow the terms it defines to be freel used alongside other vocabularies and in a variety of publishing use cases.

For the purposes of this document, the [Data Catalog Vocabulary](http://www.w3.org/TR/vocab-dcat/#class-dataset) (DCAT) provides a useful working [definition of a dataset](http://www.w3.org/TR/vocab-dcat/#class-dataset):

>A collection of data, published or curated by a single source, and available for access or download in one or more formats.

One intended use of the ODRS vocabulary is to provide a more detailed description of the rights associated with a Dataset described using the DCAT vocabulary, as well as other Linked Data vocabularies such as [VoiD](http://www.w3.org/TR/void/).

As a data publisher you must ensure that all of your datasets are associated with rights information to ensure re-users are clear on how the data can be used.

### Licences

A _Dataset_ is usually associated with a _Licence_. The ODRS vocabulary uses a broad definition of licence which is intended to cover any legal document that describe rights to re-use some information, including a complete waiver of rights (e.g. a public domain dedication).

The ODRS vocabulary does not provide a machine-readable description of licensing terms. The [Creative Commons vocabulary](http://creativecommons.org/ns) (ccRel) already provides the terms required for describing the broad classes of permissions, requirements and prohibitions that are commonly described in legal licences. 

If a publisher is not using a standard licence, like the [Open Database License](http://opendatacommons.org/licenses/odbl/) then they are encouraged to publish additional machine-readable data about their license, using the ccRel vocabulary. A worked example of this is shown later in the document.

Rather than describing licences, the ODRS vocabularly is instead focused on _Rights Statements_. A Rights Statement is the application of a a _Licence_ to a _Dataset_.

In some juristictions, particularly the EU, a dataset might actually have several licences associated with it:

* A Dataset Licence, e.g. the Open Database Licence, that covers re-use of the dataset
* A Content Licence, e.g. the Open Database Content Licence, that covers re-use of the contents of a dataset

### Rights Statements

A _Rights Statement_ is a resource that describes the relationship between a _Dataset_ and its _Licences_. Its also provides additional context that applies to the re-use of a dataset. A statement of rights will typically include some or all of the following information:

* A reference to a Dataset Licence
* A reference to a Content Licence (if, and where applicable)
* Notices, e.g. copyright notices, that should be preserved by re-users
* Guidance on a means of attributing the source of the data, e.g. when re-used in an application
* Pointers to further information, e.g. further guidance on re-use or details on how to acquire additional rights

The description of a Licence, such as the UK Open Government Licence, remains unchanged no matter how it is used or applied by an organisation. It is the Rights Statement that captures the context of the use of a organisation to support the publication of a dataset, including descriptions of relevant notices, attribution guidance and other relevant relationships.

A Rights Statement might apply to an individual Dataset. But it could equally be applied to several Datasets. If your organization publishes data under a consistent set of rights, then you need only publish a single machine-readable rights statement which can then be associated with all of your datasets. However if rights may vary across datasets, then each dataset should have its own rights statement.

### Attribution Requirements: Attribution versus Citation

Publishers often want to be acknowledged for producing and publishing data. Data re-users often need to refer to their data sources. There are two related, but relatively distinct use cases where these needs become important:

* _Attribution_ -- giving credit to the creator and/or maintainer of a dataset
* _Citation_ -- linking to a source dataset that has been used in some analysis, or the components of an aggregated dataset

Many communities have existing norms around both attribution and citation. Many licences allow publishers to require attribution when a dataset is re-used, but it can be unclear how this should be achieved.

Citation usually involves linking to the individual dataset or version of a dataset, that has been used. The citation use case is already well supported by existing dataset metadata vocabularies. A citation typically includes a link or reference to a dataset that includes its title, versioning information (including publication dates), the dataset homepage, and perhaps download locations for specific distribtions. Vocabularies like DCAT and Dublin Core already support publication of this type of metadata.

ODRS provides two terms to support attribution use cases. In this use case the goal is usually to acknowledge the dataset creator by name, often with a link to either the dataset homepage or a specific attribution or acknowledgement page.

* `attributionText` -- the name to be used when attributing the creator of some data. This might differ from the name of the organization that published the data. For example it might be a single organization "Ministry of Justice" or it could refer to a group of contributors "Wikipedia Community". By specifying the attribution text you are clearly indicating to data re-users how you wish to be acknowledged.
* `attributionURL` -- this is the URL to be used when building an attribution link. The expectation is that the link text displayed to a user will be the value of the `attributionText` property. As a data publisher this provides you with the ability to request attribution to a specific web page. While this might be the dataset homepage, or a link to your organization homepage, it may also be a link to a dedicated attribution page. This is particularly useful if you must also acknowledge your data sources.

We encourage publishers to keep attribution text as short as possible, recognising that their data may get re-used in a wide variety of locations. The ability to provide a specific destination page for attribution links makes it easier to avoid "attribution stacking" issues which can make attribution and re-use difficult.

Both attribution and citation are expected to be community norms and that the specific usage of those norms might vary between communities. Publishers should recognise that norms will likely vary, e.g. between web application developers and scientific researchers publishing analyses within academic journals. 

The goal for machine-readable metadata is to ensure that the data required to support these use cases is easily accessible to re-users without the need to read detailed attribution guidelines. 

### Publishing Copyright Notices

Copyright notices are another important item of metadata to publish as part of a rights statement. These notices must typically be preserved by re-users, particularly if they are re-publishing the data for downstream use.

The ODRS vocabularly includes two terms for capturing copyright notice information:

* The simplest is the `copyrightNotice` term which allows a short copyright notice to be directly included in the rights statement metadata.
* The `copyrightStatement` term can be used to link to a specific web page that provides a fuller statement of the copyright that relates to a dataset covered by an individual rights statement. This can be useful where the statement might need to recognise a number of different sources.

## Worked Examples

The following sections provide examples of using the ODRS vocabularly in a variety of ways. The initial examples which introduce the core terms all use the Turtle RDF serialization, although later examples include illustrations that use JSON-LD, RDFa, and other formats.

The github project that supports this vocabularly includes some [additional standalone examples](https://github.com/theodi/open-data-licensing/tree/master/examples).

For clarity many of the examples below omit prefix definitions from RDF terms. The full set of prefixes used in the examples is given below:

    @prefix dcat: &http://www.w3.org/ns/dcat#> .
    @prefix dct: &http://purl.org/dc/terms/> .
    @prefix odrs: &http://schema.theodi.org/odrs#> .
    @prefix rdfs: &http://www.w3.org/2000/01/rdf-schema#> .

### A Rights Statement with a single Licence

The following example illustrates how to associate a rights statement with a DCAT dataset:

	:example1
		a dcat:Dataset ;
		dct:title "Court Cases Dataset" ;
		dct:rights :example1-rights-statement;
		dct:license <http://reference.data.gov.uk/id/open-government-licence>.

	:example1-rights-statement
		a odrs:RightsStatement;
		rdfs:label "Rights relating to re-use of the Court Cases Dataset" ;
		odrs:dataLicence <http://reference.data.gov.uk/id/open-government-licence> ;
		odrs:attributionText "Ministry of Justice" ;
		odrs:attributionURL <https://www.gov.uk/government/organisations/ministry-of-justice>
	   
The rights statement is associated with its dataset using the Dublin Core `dct:rights` relationship. The Rights Statement for the dataset has several properties:

* A human-readable label, this could also be supplemented with, e.g. a `dct:description` property to provide a summary of the rights
* An `odrs:dataLicence` property indicates which licence covers the re-use of the associated dataset, in this case it refers to the UK [Open Government Licence](http://www.nationalarchives.gov.uk/doc/open-government-licence/). 
* The attribution text and URL that a re-use can use to acknowledge the source of the data

Note that in addition to the `dct:rights` property the example also includes a `dct:license` property that directly associates the dataset with its license. The `dct:license` property is already in relatively common use for relating datasets to their licences and it is recommended that publishers include it for compatibility with existing applications. 

However, as the next example shows, a Rights Statement allows for greater clarity when associating a dataset with multiple licences.

### A Rights Statement including multiple Licences

In some circumstances there are different rights that relate to a dataset (or database) as a whole, and the contents of that database. The following example illustrates how to relate a dataset to multiple licences one for the data domain and one for the content domain:

	:example2
		a dcat:Dataset ;
		dct:title "Open Products" ;
		dct:rights :example2-rights-statement;
		dct:license <http://opendatacommons.org/licenses/odbl/1.0/>.

	:example2-rights-statement
		a odrs:RightsStatement;
		rdfs:label "Rights relating to re-use of the Open Products Dataset" ;
		odrs:dataLicence <http://opendatacommons.org/licenses/odbl/1.0/> ;
		odrs:contentLicence <http://opendatacommons.org/licenses/dbcl/1.0/> ;
		odrs:attributionText "the Open Products community" ;
		odrs:attributionURL <http://example.org/open-products>

The two licences are distinguished through the use of the `odrs:dataLicence` and `odrs:contentLicence` properties. In this example the properties refer to the [Open Database Licence](http://opendatacommons.org/licenses/odbl/) and the [Open Database Content License](http://opendatacommons.org/licenses/dbcl/). 

While those licences might often be used together, an alternative licence could be applied to the copyrightable part of a dataset. For example a publisher might prefer to use a more common Creative Commons Licence. 

The ability to clearly distinguish between these different types of licences is an important part of the ODRS vocabulary.

### Including Copyright Notices and User Guidelines

The following example illustrates how to include a copyright notice as part of a Rights Statement. For example a dataset or its contents might be licensed under a Creative Commons licence, but the publisher still retains their copyright in the content. Creative Commons licences indicate that re-users should retain any notices that are provided by a publisher.

The ODRS vocabulary captures copyright information separately to attribution text, making it easier for applications to extract and display the relevant information.

The following example illustrates how the Ordnance Survey Open Data might have been described using the ODRS vocabulary:

	<http://data.ordnancesurvey.co.uk/id/data/os-linked-data> 
		rdf:type void:Dataset ;
		dct:title "Ordnance Survey Linked Data" ;
		dct:license <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf> ;
		dct:rights 	:example3-rights-statement;

	:example3-rights-statement
		a odrs:RightsStatement;
		odrs:dataLicence <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:contentLicence <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:copyrightNotice "Contains Ordnance Survey data © Crown copyright and database right 2013. Contains Royal Mail data © Royal Mail copyright and database right 2013. Contains National Statistics data © Crown copyright and database right 2013." ;
		odrs:attributionText "Ordnance Survey";
		odrs:attributionURL <http://ordnancesurvey.co.uk>.

The Rights Statement includes a `odrs:copyrightNotice` property in addition to the attribution properties used in previous examples. An application might choose to display the copyright notice differently to the attribution text, e.g. including it in a general copyright notice section of the application website.

In some cases it may be more suitable to provide a link to a copyright statement, e.g. if the text of the copyright notice is lengthy or subject to change. In this case the `odrs:copyrightStatement` property can be used instead. The following rights statement illustrates how to use this property:

	:example3-rights-statement
		a odrs:RightsStatement;
		odrs:dataLicence <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:contentLicence <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:copyrightStatement <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licensing.html> ;
        odrs:reuserGuidelines <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licensing.html> ;
		odrs:attributionText "Ordnance Survey";
		odrs:attributionURL <http://ordnancesurvey.co.uk>.

The revised example also includes the `odrs:reuserGuidelines` property which can be used to provide further documentation for data re-users. This might be an FAQ or other user guide that provides a useful human-readable overview of the rights statement. In this example the same web page contains both user guidance and a copyright statement.

### Publishing Rights Statements in RDFa

ODRS metadata can easily be embedded into a web page using [RDFa](http://www.w3.org/TR/xhtml-rdfa-primer/). The following example illustrates how to 
add a multi-licence rights statement as part of describing a DCAT dataset:

    TODO: include HTML from this gist: https://gist.github.com/ldodds/5750746

The equivalent metadata in Turtle is given below:

    @prefix dcat: &http://www.w3.org/ns/dcat#> .
    @prefix dct: &http://purl.org/dc/terms/> .
    @prefix odrs: &http://schema.theodi.org/odrs#> .
    @prefix rdfs: &http://www.w3.org/2000/01/rdf-schema#> .

    &http://gov.example.org/dataset/finances> a dcat:Dataset;
        dct:license &http://reference.data.gov.uk/id/open-government-licence>;
        dct:rights &https://dl.dropboxusercontent.com/u/2806337/diodd.html#rights>;
        dct:title "Example Finances Dataset" .

    &#rights> rdfs:label "Rights Statement";
        odrs:attributionText "Example Department";
        odrs:attributionURL &http://gov.example.org/dataset/finances>;
        odrs:contentLicence &http://reference.data.gov.uk/id/open-government-licence>;
        odrs:copyrightNotice "Contains public sector information licensed under the Open Government Licence v1.0";
        odrs:dataLicence &http://reference.data.gov.uk/id/open-government-licence> .

    &http://reference.data.gov.uk/id/open-government-licence> dct:title "UK Open Government Licence (OGL)" .

### Publishing Rights Statements in JSON-LD

[JSON-LD](http://json-ld.org/) supports publishing of Linked Data using JSON. The following example shows how the data shown in the previous example could be published as JSON-LD:

    {
      "@context": {
        "dcat": "http://www.w3.org/ns/dcat#",
        "dct": "http://purl.org/dc/terms/",
        "odrs": "http://schema.theodi.org/odrs#",
        "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#"
      },
      "@graph": [
        {
          "@id": "http://reference.data.gov.uk/id/open-government-licence",
          "dct:title": "UK Open Government Licence (OGL)"
        },
        {
          "@id": "http://gov.example.org/dataset/finances",
          "@type": "dcat:Dataset",
          "dct:license": {
            "@id": "http://reference.data.gov.uk/id/open-government-licence"
          },
          "dct:rights": {
            "@id": "#rights"
          },
          "dct:title": "Example Finances Dataset"
        },
        {
          "@id": "#rights",
          "odrs:attributionText": "Example Department",
          "odrs:attributionURL": {
            "@id": "http://gov.example.org/dataset/finances"
          },
          "odrs:contentLicence": {
            "@id": "http://reference.data.gov.uk/id/open-government-licence"
          },
          "odrs:copyrightNotice": "Contains public sector information licensed under the Open Government Licence v1.0",
          "odrs:dataLicence": {
            "@id": "http://reference.data.gov.uk/id/open-government-licence"
          },
          "rdfs:label": "Rights Statement"
        }
      ]
    }

### Rights Statements in simple JSON

	{
		"rights": {
			"dataLicence": "...",
			"contentLicence": "...",
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


