# Publisher Guide to the Open Data Rights Statement Vocabulary

This guide illustrates how to publish machine-readable rights statements using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/open-data-licensing/) (ODRS). 

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. A clear statement of rights can ensure that data re-users fully understand the potential for re-use of a dataset, whether it is suitable for their purposes, and any obligations that may incur through using the data.

This guide provides and introduction to the ODRS vocabulary, and includes a number of worked examples that illustrate how to use the vocabulary to publish rights metadata in a number of different ways.

A separate companion document, the [Re-users Guide to the Open Data Rights Statement Vocabulary](), offers some additional advice on how to process and use rights statements within applications.

## Overview of the ODRS Vocabulary

The ODRS vocabularly is based around describing the relationships between three types of resource: _Datasets_, _Rights Statements_ and _Licences_. Each of these are introduced in the following sections.

### Datasets

There are many different definitions of the term "dataset": different communities define the term very differently. The ODRS vocabulary deliberates avoids adopting a single definition in order to allow it to be used in a number of different ways.

For the purposes of this document, the [Data Catalog Vocabulary](http://www.w3.org/TR/vocab-dcat/#class-dataset) (DCAT) provides a useful working [definition of a dataset](http://www.w3.org/TR/vocab-dcat/#class-dataset):

>A collection of data, published or curated by a single source, and available for access or download in one or more formats.

One intended use of the ODRS vocabulary is to provide a more detailed description of the rights associated with a Dataset described using the DCAT vocabulary, as well as other Linked Data vocabularies such as [VoiD](http://www.w3.org/TR/void/). However it can also be used to help describe datasets published in other ways, as well as data exposed via web APIs.

As a data publisher you should ensure that all of your datasets are associated with rights information to ensure re-users can be clear on how the data can be used. Clearly labelled rights are an important part of sustainable Open Data publishing.

### Licences

A _Dataset_ is usually associated with a _Licence_. The ODRS vocabulary uses a broad definition of licence which is intended to cover any legal document which describes the re-use rights that apply to some information, including a complete waiver of rights (e.g. a public domain dedication).

The ODRS vocabulary does not provide a machine-readable description of licensing terms. The [Creative Commons vocabulary](http://creativecommons.org/ns) (ccRel) already provides the terms required for describing the broad classes of permissions, requirements and prohibitions that are commonly described in legal licences.

As a data publisher, if you are not using a standard licence, such as the [Open Database License](http://opendatacommons.org/licenses/odbl/) then you are encouraged to publish additional machine-readable data about your licence, using the ccRel vocabulary. A worked example of this is shown later in the document.

Rather than describing licences, the ODRS vocabularly instead focuses on describing _Rights Statements_. A Rights Statement is the application of a a _Licence_ to a _Dataset_.

In some juristictions, particularly the EU, a dataset might actually have several licences associated with it:

* A Dataset Licence, e.g. the Open Database Licence, that covers re-use of the dataset
* A Content Licence, e.g. the Open Database Content Licence, that covers re-use of the contents of a dataset

### Rights Statements

A _Rights Statement_ is a resource that describes the relationship between a _Dataset_ and its _Licence(s)_. It is also used to describe additional contextual information that applies to the re-use of a dataset. 

For example a statement of rights may typically include some or all of the following information:

* A reference to a Dataset Licence
* A reference to a Content Licence (if, and where applicable)
* Notices, e.g. copyright notices, that should be preserved by re-users
* Guidance on a means of attributing the source of the data, e.g. when re-used in an application
* Pointers to further information, e.g. further guidance on re-use or details on how to acquire additional rights

The description of a Licence, such as the [UK Open Government Licence](http://www.nationalarchives.gov.uk/doc/open-government-licence/), remains unchanged no matter how it is used by an organisation when publishing data. It is the Rights Statement that captures the context of the use of a licence to support the publication of a dataset, including descriptions of relevant notices, attribution guidance and other relevant relationships.

A Rights Statement might apply to an individual Dataset. But it could equally be applied to several Datasets. If your organization publishes data under a consistent set of rights, then you need only publish a single machine-readable rights statement which can then be associated with all of your datasets. However if rights vary across datasets, then each dataset should have its own rights statement.

### Attribution Requirements: Attribution versus Citation

Publishers often want to be acknowledged for the effort involved in producing and publishing Open Data. Data re-users often need to refer to their data sources. There are two related, but relatively distinct use cases where these needs are important:

* _Attribution_ -- giving credit to the creator and/or maintainer of a dataset
* _Citation_ -- linking to a source dataset that has been used in some analysis, or the components of an aggregated dataset

Many licences allow publishers to require attribution when a dataset is re-used, but it can be unclear how this should be achieved. Norms for dataset citation also vary. E.g. the research community have well-defined conventions for citing datasets in research papers that describe some research or analysis.

Citation usually involves clearly identifying the specific dataset, or version of a dataset, that has been used. Citation helps to identify the provenance of data, allowing others to potentially recreate some analysis or discover interesting datasets. The citation use case is already well supported by existing dataset metadata vocabularies. A citation typically includes a link or reference to a dataset that includes its title, versioning information (including publication dates), the dataset homepage, and perhaps download locations for specific distribtions. Vocabularies like DCAT and Dublin Core already support publication of this type of metadata.

Attribution is typically less formal. The goal is usually to acknowledge the dataset creator by name, often with a link to either the dataset homepage or a specific attribution or acknowledgement page. 

The ODRS vocabulary provides two terms to support publishing in describing means of attribution:

* `attributionText` -- the name to be used when attributing the creator of some data. This might differ from the name of the organization that published the data. For example it might be a single organization "_Ministry of Justice_" or it could refer to a group of contributors "_Wikipedia Community_". By specifying the attribution text you are clearly indicating to data re-users how you wish to be acknowledged.
* `attributionURL` -- this is the URL to be used when building an attribution link. The expectation is that the link text displayed to a user will be the value of the `attributionText` property. As a data publisher this provides you with the ability to request attribution to a specific web page. While this might be the dataset homepage, or a link to your organization homepage, it may also be a link to a dedicated attribution page. This is particularly useful if you must also acknowledge your data sources.

Publishers should keep attribution text as short as possible, recognising that their data may get re-used in a wide variety of locations. The ability to provide a specific destination page for attribution links makes it easier to avoid "attribution stacking" issues which can make attribution and re-use difficult.

The ODRS vocabulary deliberately doesn't describe how to format attributions or citations, e.g. on a web page. Data might be consumed in a number of different ways and displayed on a number of different devices (if at all). Publishers should recognise that styles of attribution and citation will vary between communities and be flexible on their expectations for how this information is displayed. A scientific researcher citing some data in an academic paper will follow (and be bound by) different styles of attribution and citation than a web developer building a mobile application.

The goal of the ODRS vocabulary, and for machine-readable dataset metadata in general, is to ensure that the data required to support these various use cases is easily accessible to re-users without the need to read detailed attribution guidelines.

### Publishing Copyright Notices

Copyright notices are another important item of metadata to publish as part of a rights statement. These notices must typically be preserved by re-users, particularly if they are re-publishing the data for downstream use.

The ODRS vocabulary includes two terms for capturing copyright notice information:

* The simplest is the `copyrightNotice` term which allows a short copyright notice to be directly included in the rights statement metadata.
* The `copyrightStatement` term can be used to link to a specific web page that provides a fuller statement of the copyright that relates to a dataset covered by an individual rights statement. This can be useful where the statement might need to recognise a number of different sources.

## Using the ODRS Vocabulary

The ODRS vocabulary is intended to be used to publish machine-readable metadata in a variety of formats. The vocabulary has been formally defined using RDFS and OWL, allowing it to be directly used as a means of publishing Linked Data and RDFa. However the vocabulary can also be viewed as a simple conceptual framework that can be used to guide the publication of data in other ways, e.g in simple JSON or XML formats.

The following sections provide details on using the vocabulary:

* to publish Rights Statements as Linked Data, using formats like Turtle and JSON-LD
* to embed Rights Statements as metadata into web pages using RDFa; and 
* how to add links to rights statements to web APIs

The examples in the Linked Data sections introduce the core terms in the vocabulary, while the later examples focus on details of specific data formats.

The github project that supports this vocabulary includes some [additional standalone examples](https://github.com/theodi/open-data-licensing/tree/master/examples) that can be used a further reference.

### Publishing Rights Statements in Linked Data

The following examples all use the [Turtle](http://www.w3.org/TR/turtle/) RDF syntax. For clarity the prefix definitions have been omitted from individual examples. You should assume that the following set of prefixes are defined:

    @prefix cc: <http://creativecommons.org/ns#> .
    @prefix dcat: <http://www.w3.org/ns/dcat#> .
    @prefix dct: <http://purl.org/dc/terms/> .
    @prefix odrs: <http://schema.theodi.org/odrs#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

#### Defining a Rights Statement with a single Licence

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
		odrs:attributionURL <https://www.gov.uk/government/organisations/ministry-of-justice>.
	   
The rights statement is associated with its dataset using the Dublin Core `dct:rights` relationship. The rights are described using an `odrs:RightsStatement` resource which has several important properties:

* A human-readable label specified using `rdfs:label`. This could also be supplemented with, e.g. a `dct:description` property to provide a summary of the rights
* A `odrs:dataLicense` property which specifies which licence covers the re-use of the associated dataset. In this example it refers to the UK [Open Government Licence](http://www.nationalarchives.gov.uk/doc/open-government-licence/). 
* The preferred form of attribution is described using the `odrs:attributionText` and `odrs:attributionURL` properties

In addition to the `dct:rights` property the example also includes a `dct:license` property that directly associates the dataset with its licence. The `dct:license` property is already in relatively common use for this purpose and it is recommended that publishers include it for compatibility with existing applications. 

Where the `dct:license` property is included it is recommended that this is used to refer to the same data licence that is referenced from the `odrs:dataLicense` property.

#### Defining a Rights Statement with multiple Licences

In some circumstances there are different rights that relate to a dataset (or database) as a whole, and the contents of that database. The ODRS vocabulary allows multiple licences to be associated with a dataset, allowing these data and content licensed to be clearly defined.

The following example dataset is associated with a Rights Statement that has both the `odrs:dataLicense` and `odrs:contentLicense` properties. 

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
		odrs:attributionURL <http://example.org/open-products>.

In this example the licence properties refer to the [Open Database Licence](http://opendatacommons.org/licenses/odbl/) and the [Open Database Content License](http://opendatacommons.org/licenses/dbcl/). While those licences might often be used together, an alternative licence could be applied to the copyrightable part of a dataset. For example a publisher might prefer to use a Creative Commons Licence.

The ability to clearly distinguish between these different types of licences is an important part of the ODRS vocabulary.

Publishers should only create rights statements that include at most one data licence and one content licence. For example a Rights Statement should not have multiple data licences. 

Some open licences can be used to license both data and content, so a single licence can be used to cover all aspects of re-use. However it is recommended that publishers still include both of the ODRS licence properties, even if they refer to the same licence resource.

#### Including Copyright Notices and User Guidelines

The description of a Rights Statement can be enriched by including further metadata, including copyright notices. For example while a dataset or its contents might be licensed under a Creative Commons licence, the publisher still retains their copyright in the content. Creative Commons licences indicate that re-users should retain any notices that are provided by a publisher.

The ODRS vocabulary captures copyright information separately to attribution text, making it easier for applications to extract and display the relevant information.

The following example illustrates how the Ordnance Survey Open Data might have been described using the ODRS vocabulary:

	<http://data.ordnancesurvey.co.uk/id/data/os-linked-data> 
		rdf:type void:Dataset ;
		dct:title "Ordnance Survey Linked Data" ;
		dct:license <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf> ;
		dct:rights 	:example3-rights-statement;

	:example3-rights-statement
		a odrs:RightsStatement;
		odrs:dataLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:contentLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:copyrightNotice "Contains Ordnance Survey data © Crown copyright and database right 2013. 
        Contains Royal Mail data © Royal Mail copyright and database right 2013. 
        Contains National Statistics data © Crown copyright and database right 2013." ;
		odrs:attributionText "Ordnance Survey";
		odrs:attributionURL <http://ordnancesurvey.co.uk>.

The Rights Statement includes a `odrs:copyrightNotice` property in addition to the attribution properties used in the previous examples. An application might choose to display the copyright notice differently to the attribution text, e.g. including it in a general copyright notice section of the application website.

In some cases it may be more suitable to provide a link to a copyright statement, e.g. if the text of the copyright notice is lengthy or subject to change. In this case the `odrs:copyrightStatement` property can be used instead. The following rights statement illustrates use of this property:

	:example3-rights-statement
		a odrs:RightsStatement;
		odrs:dataLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:contentLicense <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licence/docs/licence.pdf>;
		odrs:copyrightStatement <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licensing.html> ;
        odrs:reuserGuidelines <http://www.ordnancesurvey.co.uk/oswebsite/opendata/licensing.html> ;
		odrs:attributionText "Ordnance Survey";
		odrs:attributionURL <http://ordnancesurvey.co.uk>.

This revised example also includes the `odrs:reuserGuidelines` property which can be used to provide a link to further documentation for data re-users. These guidelines might be an FAQ or other user guide that provides a useful overview of the rights statement. In this example the same web page contains both user guidance and a copyright statement.

#### Combining the ODRS and ccREL vocabularies

Wherever possible, publishers are encouraged to use an "off-the-shelf" Open Data licence, but in some circumstances a custom licence might be required. The Creative Commons have created a vocabulary that supports the publishing of a machine-readable description of the key facets of a data or content licence.

The following example illustrates how to combine [the Creative Commons vocabulary](http://creativecommons.org/ns) with ODRS:

	:example4
		a dcat:Dataset ;
		dct:title "Dataset with Custom License" ;
		dct:rights :example4-rights-statement ;
		dct:license :example4-license .

	:example4-rights-statement
		a odrs:RightsStatement ;
        rdfs:label "Rights Statement referencing our custom license" ;
		odrs:dataLicense :example4-license .

	:example4-license
        a odrs:License, cc:License;
        rdfs:label "Custom Data License";
        cc:legalcode <http://example.org/legal/custom-license> ;
        cc:permits cc:DerivativeWorks, cc:Distribtion, cc:Reproduction ;
        cc:requires cc:Notice , cc:ShareAlike .
        
The above example includes a rights statement that refers to a custom licence. The licence is described using terms from the Creative Commons vocabulary including a link to its legal definition and a series of permissions and requirements. This particular licence is a variation of the CC-BY licence: it permits the creation of derivative works, distribution and reproduction of the data and the re-user must include all copyright notices and license derivatives using similar terms; but there is no _legal_ requirement to include attribution.

#### Publishing Rights Statements in JSON-LD

[JSON-LD](http://json-ld.org/) is a light-weight data format for publishing Linked Data as JSON. It is straight-forward to publish Rights Statements that conform to the ODRS vocabulary using JSON-LD.

The following example shows how to combine the description of a dataset and its rights into a single JSON-LD document. The `@context` section defines the prefixes for the properties used elsewhere in the JSON document.

    {
        "@context": {
            "dcat": "http://www.w3.org/ns/dcat#",
            "dct": "http://purl.org/dc/terms/",
            "odrs": "http://schema.theodi.org/odrs#",
            "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#"
        },
        "@id": "http://gov.example.org/dataset/finances",
        "@type": "dcat:Dataset",
        "dct:title": "Example Finances Dataset",
        "dct:license": {
            "@id": "http://reference.data.gov.uk/id/open-government-licence",
            "dct:title": "UK Open Government Licence (OGL)"
        },
        "dct:rights": {
            "rdfs:label": "Rights Statement",
            "@id": "http://gov.example.org/dataset/finances#rights",
            "odrs:copyrightNotice": "Contains public sector information licensed under the OGL v1.0",
            "odrs:attributionText": "Example Department",
            "odrs:attributionURL": {
                "@id": "http://gov.example.org/dataset/finances"
            },
            "odrs:contentLicense": {
                "@id": "http://reference.data.gov.uk/id/open-government-licence"
            },
            "odrs:dataLicense": {
                "@id": "http://reference.data.gov.uk/id/open-government-licence"
                }
        }
    }

### Publishing Rights Statements in Web Pages using RDFa

ODRS metadata can easily be embedded into a web page using [RDFa](http://www.w3.org/TR/xhtml-rdfa-primer/). The following example illustrates how to 
add a multi-licence rights statement as part of describing a DCAT dataset. The [complete example file](https://github.com/theodi/open-data-licensing/blob/master/examples/simple-rdfa-example.html) is included in the supporting github project.

Firstly, the prefixes need to be added to the HTML element in the document:

    <html prefix="dct: http://purl.org/dc/terms/
                  rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
                  dcat: http://www.w3.org/ns/dcat#
			      odrs: http://schema.theodi.org/odrs#">


Then the description of the dataset and the rights statement can be added to the document. The outer `div` element identifies the DCAT dataset and defines its `dct:title`. The `dct:rights` and `dct:license` properties are then used to refer to its Rights Statement and data licence. The rights statement references multiple licences, a copyright notice and a suggested method of attribution:

    <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/finances">
         <h1 property="dct:title">Example Finances Dataset</h1>                      
           <div property="dct:rights" resource="#rights">
             <div resource="#rights">
                 <h2 property="rdfs:label">Rights Statement</h2>
                 <ul>
                     <li>Data Licence: <a href="http://reference.data.gov.uk/id/open-government-licence" 
                                       property="odrs:dataLicense">UK Open Government Licence (OGL)</a>
                     </li>
                     <li>Content Licence: <a href="http://reference.data.gov.uk/id/open-government-licence" 
                                       property="odrs:contentLicense">UK Open Government Licence (OGL)</a>
                     </li>
                 </ul>
                 <p>
                 When re-using this data please preserve the following copyright notice: 
                 "<span property="odrs:copyrightNotice">Contains public sector information licensed 
                   under the Open Government Licence v1.0</span>".
                 </p>

                 <p>
                 If you would like to attribute your use of this dataset, please use a link 
                 similar to the following: 
                 <a href="http://gov.example.org/dataset/finances" 
                    property="odrs:attributionURL">
                     <span property="odrs:attributionText">Example Department</span>
                 </a>.
                 </p>
             </div>
                 
         </div>

         <div property="dct:license" 
              resource="http://reference.data.gov.uk/id/open-government-licence">
             <a href="http://reference.data.gov.uk/id/open-government-licence">
             <span property="dct:title">UK Open Government Licence (OGL)</span>
             </a>
         </div>

         <!-- additional markup with further description of dataset -->
     </div>

The equivalent metadata in Turtle is given below:

    @prefix dcat: <http://www.w3.org/ns/dcat#> .
    @prefix dct: <http://purl.org/dc/terms/> .
    @prefix odrs: <http://schema.theodi.org/odrs#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

    <http://gov.example.org/dataset/finances> a dcat:Dataset;
        dct:license <http://reference.data.gov.uk/id/open-government-licence>;
        dct:rights <#rights>;
        dct:title "Example Finances Dataset" .

    <#rights> rdfs:label "Rights Statement";
        odrs:attributionText "Example Department";
        odrs:attributionURL <http://gov.example.org/dataset/finances>;
        odrs:contentLicense <http://reference.data.gov.uk/id/open-government-licence>;
        odrs:copyrightNotice "Contains public sector information licensed under the Open Government Licence v1.0";
        odrs:dataLicense <http://reference.data.gov.uk/id/open-government-licence> .

    <http://reference.data.gov.uk/id/open-government-licence> dct:title "UK Open Government Licence (OGL)" .

In this case both the dataset and its right statement are described in the same page, but the rights statement might be described in a separate web page, allowing it to be referenced by more than one dataset.

### Publishing Rights Statements for Web APIs

As well as raw data downloads, datasets may also be published via a web API, allowing users to query and extract portions of the data as they need it. The data exposed via the API should also be associated with a clear rights statement. Rather than burying this information in API documentation or the terms of use of a service it can be referenced directly from the results of an API request.

One simple approach to this is to include a link to a machine-readable rights statement that is published elsewhere on a site, e.g. as RDFa annotations in the API documentation. The `Link` HTTP header defined by [RFC5988](http://tools.ietf.org/html/rfc5988) can be used to add links to API responses without the need to change the response formats, avoiding any potential impacts on existing users.

For example an HTTP GET to the fictitious `http://api.example.org/search` API might return the following response:

    HTTP/1.1 200 OK
    Cache-Control: max-age=86400, must-revalidate
    Content-Type: application/json
    Date: Mon, 17 Jun 2013 13:45:45
	Link: <http://opendatacommons.org/licenses/odbl/>; rel="license", 
	      <http://api.example.org/docs/rights>; rel="http://purl.org/dc/terms/rights",
    Server: Apache/2.2.3 (CentOS)
    Vary: Accept
    Content-Length: 12345
 
    { ...some JSON data... }

The HTTP response includes a `Link` header that defines two links for this HTTP response. The first uses the standard `license` relation to refer to the data licence associated with the data included in the response. In addition a custom link relation is also included to refer to a rights statement that provides a fuller description of the re-use rights associated with the data. The custom relation uses the URI of the `dct:rights` property which we have used elsewhere in the document.

Link relations can also be used directly in API responses. Some standard formats, like Atom, already allow for additional links to be added to a document. Other formats might need further customisation.

