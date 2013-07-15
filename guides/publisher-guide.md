# Publisher Guide to the Open Data Rights Statement Vocabulary

This guide illustrates how to publish machine-readable rights statements using the [Open Data Rights Statement vocabulary](http://schema.theodi.org/odrs/) (ODRS). 

Data published to the web should always be accompanied by machine-readable metadata that describes the dataset, its means of creation and, importantly, a statement of the rights that relate to potential re-use of the data. A clear statement of rights can ensure that data re-users fully understand the potential for re-use of a dataset, whether it is suitable for their purposes, and any obligations that may incur through using the data.

This guide provides an introduction to the ODRS vocabulary, and includes a number of worked examples that illustrate how to use the vocabulary to publish rights metadata in a number of different ways.

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
* Copyright notices, that should be referenced or displayed by re-users
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

* `attributionText` -- the text to be used when attributing the creator of some data. Typically this will just be the name of your organization, e.g. your company or government department. However it might also be a more general phrase. E.g. a crowd-sourced dataset might use `attributionText` of: "_Wikipedia Community_". You can use this property to specify the attribution text you would like data re-users to use. Without this, re-users will need to decide for themselves how to reference your organisation or dataset. The re-users guide includes some guidance on this.
* `attributionURL` -- this is the URL to be used when building an attribution link. The expectation is that the link text displayed to a user will be the value of the `attributionText` property. As a data publisher this provides you with the ability to request attribution to a specific web page. While this might be the dataset homepage, or a link to your organization homepage, it may also be a link to a dedicated attribution page. This is particularly useful if you must also acknowledge your data sources. The ability to provide a specific destination page for attribution links also makes it easier to avoid "attribution stacking" issues which can make attribution and re-use difficult.

Publishers should keep attribution text as short as possible, recognising that their data may get re-used in a wide variety of locations. The following are all good examples of attribution text:

* _My Organization_
* _Open Data, Ltd_
* _Crowd sourced data community_

The following examples are problematic:

* _Data sourced from My Organization dataset_
* _Contains data provided by My Organization. Copyright 2013._
* _This data covers records processed by MyOrg in the period XYZ to XYZ. Data is covered by Crown Copyright_

These examples remove any flexibility on behalf of the data re-user to format and structure links to your dataset in a manner that is in-line with their application. For example the text is either lengthy, difficult to link, or mixes together attribution text with copyright statements (see below). 

The ODRS vocabulary deliberately doesn't describe how to format attributions or citations, e.g. on a web page. Data might be consumed in a number of different ways and displayed on a number of different devices (if at all). Publishers should recognise that styles of attribution and citation will vary between communities and be flexible on their expectations for how this information is displayed. A scientific researcher citing some data in an academic paper will follow (and be bound by) different styles of attribution and citation than a web developer building a mobile application.

The goal of the ODRS vocabulary, and for machine-readable dataset metadata in general, is to ensure that the data required to support these various use cases is easily accessible to re-users without the need to read detailed attribution guidelines.

### Publishing Copyright Notices

Copyright notices are another important item of metadata that might usefully be added to a rights statement. Some open licenses, particularly those from the Creative Commons state that re-users should display any copyright notices provided by publishers.

If you hold copyright over some part of your dataset, you _may_ wish to publish a copyright notice for re-users. This can be useful as it will support re-users in displaying or referencing a copyright notice or preserving a notice when redistributing data, if this is required by your licenses.

The ODRS vocabulary includes several terms for capturing copyright notice information:

* `copyrightHolder` and `copyrightYear` -- allows the copyright holder to be named, along with the year from which the copyright is claim.
* `copyrightStatement` -- this property allows you specify a URL for the copyright statement. This can be used an alternative to the other properties, providing a link to a web page that describes the copyright status of the dataset and any relevant notices. A re-user would link to this page, rather than including your copyright notice. This can be useful if your copyright notices are lengthy, e.g. if you have to reference several sources.

Copyright notices are distinct from attribution text. Wikipedia provides some notes on the [technical requirements for copyright notices](http://en.wikipedia.org/wiki/Copyright_notice#Technical_requirements) and there is generally specific advice available from your national copyright agency. See for example [guidance from the UK Copyright Service](http://www.copyrightservice.co.uk/copyright/p03_copyright_notices) and [the US Copyright Office](http://www.copyright.gov/circs/circ03.pdf).

The general convention for copyright notices is that they consist of:

* The phrase "_Copyright_"
* and/or the copyright symbol
* The year of copyright
* The copyright owners name, or a well-known alias

E.g. "_Copyright © 2013. Example, Ltd_".

This format can be easily created from the `copyrightHolder` and `copyrightYear` properties, whilst also supporting other uses of that information.

Attribution text should be distinct from copyright notices. Attribution text should not contain a copyright symbol or the word "Copyright". It should instead be the name of the organisation or group whose work should be attributed. Separately and clearly marking up these different elements will provide more flexibility for re-users.

For example an `attributionText` of _Dept of Data_, a `copyrightHolder` of _Crown copyright_ and a `copyrightYear` of _2013_ could be combined in several ways, e.g.:

* To create a phrase to be added in a web page footer: _Uses data from Dept. of Data. © Crown copyright 2013_
* To build an attribution link for a data element on a page (_Data from Dept. of Data_), whilst the copyright statement is referenced in the footer of the page (_© Crown copyright 2013. Dept of Data_)
* The developer could create a simplified attribution statement that combined attribution text and copyright notices from  multiple sources, e.g. _Uses data from Dept. of Data and Ministry of Facts. © Crown copyright 2013_

## Using the ODRS Vocabulary

The ODRS vocabulary is intended to be used to publish machine-readable metadata in a variety of formats. The vocabulary has been formally defined using RDFS and OWL, allowing it to be directly used as a means of publishing Linked Data and RDFa. However the vocabulary can also be viewed as a simple conceptual framework that can be used to guide the publication of data in other ways, e.g in simple JSON or XML formats.

The following sections provide details on using the vocabulary:

* to publish Rights Statements as embedded metadata in web pages using RDFa
* to publish Rights Statements as Linked Data, using formats like Turtle and JSON-LD
* how to add links to rights statements to web APIs and existing formats

The examples in the first section on RDFa introduces the core terms in the vocabulary, while the later examples focus on details of specific data formats.

The github project that supports this vocabulary includes some [additional standalone examples](https://github.com/theodi/open-data-licensing/tree/master/examples) that can be used a further reference.

### Publishing Rights Statements in Web Pages using RDFa

ODRS metadata can easily be embedded into a web page using [RDFa](http://www.w3.org/TR/xhtml-rdfa-primer/). This makes it easy to enhance your dataset and API documentation with some machine-readable metadata.

The following sections show how to markup a rights statement using RDFa. Each example highlights a specific aspect of the vocabulary and is present as a simple HTML fragment. To be valid RDFa some prefixes must be declared in the document. Each of the examples can be added to the following page template to make a valid document:

    <html prefix="dct: http://purl.org/dc/terms/
                  rdf: http://www.w3.org/1999/02/22-rdf-syntax-ns#
                  dcat: http://www.w3.org/ns/dcat#
			      odrs: http://schema.theodi.org/odrs#">
        
        <body>
            <!-- Example HTML+RDFa Fragment -->
        </body>
    </html>

The complete set of example files can be found in [the example section]((https://github.com/theodi/open-data-licensing/blob/master/examples/) of the supporting github project.

#### Marking up a Rights Statement with a single license

A machine-readable description of a dataset can be published using the DCAT vocabulary. The following HTML fragment shows a very simple description of a dataset published as RDFa:

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <div property="dct:license" 
                 resource="http://reference.data.gov.uk/id/open-government-licence">
                <a href="http://reference.data.gov.uk/id/open-government-licence">
                    UK Open Government Licence (OGL)
                </a>
            </div>

            <!-- additional markup with further description of dataset -->
        </div> 

The outer `div` element identifies the dataset being described and assigns it a type of `dcat:Dataset`. The other nested elements define the title (`dct:title`) and license (`dct:license`) of the dataset. 

The `dct:license` property is already in relatively common use for associating a resource with its license, and it is recommended that publishers continue to use the property to ensure compatibility with existing applications. But using the ODRS vocabulary we can provide a richer description of the rights associated with a dataset.

The following HTML fragment illustrates the most basic use of the ODRS vocabulary. 

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <div property="dct:rights" resource="#rights" typeof="odrs:RightsStatement">
                <h2 property="rdfs:label">Rights Statement</h2>
                <p>Published under the 
                    <a href="http://reference.data.gov.uk/id/open-government-licence" 
                        property="odrs:dataLicense">UK Open Government Licence (OGL)
                    </a>
                </p>

                <p>If you would like to attribute your use of this dataset, 
                    please use a link similar to the following: 
                    <a href="http://gov.example.org/dataset/example" 
                        property="odrs:attributionURL">
                        <span property="odrs:attributionText">
                            Example Department
                        </span>
                    </a>.
                </p>
            </div>

            <div property="dct:license" 
                 resource="http://reference.data.gov.uk/id/open-government-licence">
                <a href="http://reference.data.gov.uk/id/open-government-licence">
                    UK Open Government Licence (OGL)
                </a>
            </div>

            <!-- additional markup with further description of dataset -->
        </div>  

The description of the dataset has been enhanced to include a rights statement resource. The rights statement is associated with the dataset using the Dublin Core `dct:rights` relationship. The rights statement resource has a type of `odrs:RightsStatement` and has been described usings several properties:

* An `rdfs:label` which provides a human-readable label for the rights. This could also be supplemented with, e.g. a `dct:description` property to provide an additional summary of the rights
* An `odrs:dataLicense` property which specifies the licence covers the re-use of the data. This property should be consistent with the `dct:license` property where both are provided. 
* The `odrs:attributionText` and `odrs:attributionURL` properties indicate how to attribute the dataset

#### Marking up a Rights Statement with multiple licenses

In some circumstances there are different rights that relate to a dataset (or database) as a whole, and the contents of that database. The ODRS vocabulary allows multiple licences to be associated with a dataset, allowing these data and content licenses to be clearly defined.

The following example dataset includes a Rights Statement that has both the `odrs:dataLicense` and `odrs:contentLicense` properties. 

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <div property="dct:rights" resource="#rights" typeof="odrs:RightsStatement">
                <h2 property="rdfs:label">Rights Statement</h2>
                <p>This dataset may be re-used according to the following licenses:</p>
                <ul>
                    <li>Data Licence: 
                        <a href="http://opendatacommons.org/licenses/odbl/1.0/">
                            property="odrs:dataLicense">Open Database License</a>
                    </li>
                    <li>Content Licence: 
                        <a href="http://opendatacommons.org/licenses/dbcl/1.0/" 
                            property="odrs:contentLicense">Open Database Content License</a>
                    </li>
                </ul>

                <p>If you would like to attribute your use of this dataset, 
                    please use a link similar to the following: 
                    <a href="http://gov.example.org/dataset/example" 
                        property="odrs:attributionURL">
                        <span property="odrs:attributionText">
                            Example Department
                        </span>
                    </a>.
                </p>
            </div>

            <div property="dct:license" 
                 resource="http://reference.data.gov.uk/id/open-government-licence">
                <a href="http://reference.data.gov.uk/id/open-government-licence">
                    UK Open Government Licence (OGL)
                </a>
            </div>

            <!-- additional markup with further description of dataset -->
        </div>        

In this example the licence properties refer to the [Open Database Licence](http://opendatacommons.org/licenses/odbl/) and the [Open Database Content License](http://opendatacommons.org/licenses/dbcl/). While those licences might often be used together, an alternative licence could be applied to the copyrightable part of a dataset. For example a publisher might prefer to use a Creative Commons Licence.

The ability to clearly distinguish between these different types of licences is an important part of the ODRS vocabulary. Notice that the `dct:license` property only refers to the data license. In the context of describing datasets, it is recommended that this property only ever be used to refer to a data license.

Publishers should only create rights statements that include at most one data or content license. A Rights Statement should not have multiple data licences or content licenses. 

Some open licences can be used to license both data and content, so a single licence may cover all aspects of re-use. However it is recommended that publishers still include both of the ODRS licence properties, even if they refer to the same licence resource.

#### Including Copyright Notices and User Guidelines

The description of a Rights Statement can be enriched by including further metadata, including copyright notices. For example while a dataset or its contents might be licensed under a Creative Commons licence, the publisher still retains their copyright in the content. Creative Commons licences indicate that re-users should retain any notices that are provided by a publisher.

The ODRS vocabulary captures copyright information separately to attribution text, making it easier for applications to extract and display the relevant information.

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <div property="dct:rights" resource="#rights" typeof="odrs:RightsStatement">
                <h2 property="rdfs:label">Rights Statement</h2>
                <p>Published under the 
                    <a href="http://reference.data.gov.uk/id/open-government-licence" 
                        property="odrs:dataLicense">UK Open Government Licence (OGL)
                    </a>
                </p>

                <p>When re-using or distributing this data please preserve the 
                   following copyright notice: "
                    © <span property="odrs:copyrightHolder">Crown copyright</span> 
                    <span property="odrs:copyrightYear">2013</span>.".
                </p>

                <p>If you would like to attribute your use of this dataset, 
                    please use a link similar to the following: 
                    <a href="http://gov.example.org/dataset/example" 
                        property="odrs:attributionURL">
                        <span property="odrs:attributionText">
                            Example Department
                        </span>
                    </a>.
                </p>
            </div>

            <div property="dct:license" 
                 resource="http://reference.data.gov.uk/id/open-government-licence">
                <a href="http://reference.data.gov.uk/id/open-government-licence">
                    UK Open Government Licence (OGL)
                </a>
            </div>

            <!-- additional markup with further description of dataset -->
        </div>        

The Rights Statement includes both the `odrs:copyrightHolder` and `odrs:copyrightYear` properties in addition to the attribution properties used in the previous examples. An application might choose to display the copyright notice differently to the attribution text, e.g. including it in a general copyright notice section of the application website or in a copyright statement document included in a re-distributed version of the dataset.

In some cases it may be more suitable to provide a link to a copyright statement, e.g. if the text of the copyright notice is lengthy or subject to change. In this case the `odrs:copyrightStatement` property can be used instead. The following rights statement illustrates use of this property:

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <div property="dct:rights" resource="#rights" typeof="odrs:RightsStatement">
                <h2 property="rdfs:label">Rights Statement</h2>
                <p>Published under the 
                    <a href="http://reference.data.gov.uk/id/open-government-licence" 
                        property="odrs:dataLicense">UK Open Government Licence (OGL)
                    </a>
                </p>

                <p>When re-using or distributing this data please provide a link to the 
                    <a href="http://gov.example.org/copyright"
                        property="odrs:copyrightStatement">copyright statement</a>.
                </p>

                <p>If you would like to attribute your use of this dataset, 
                    please use a link similar to the following: 
                    <a href="http://gov.example.org/dataset/example" 
                        property="odrs:attributionURL">
                        <span property="odrs:attributionText">
                            Example Department
                        </span>
                    </a>.
                </p>
                
                <p>For more information on re-using this dataset, please read the 
                  <a href="http://gov.example.org/reuser-guide"
                     property="odrs:reuserGuidelines">re-user guidelines</a>.
                </p>
                
            </div>

            <div property="dct:license" 
                 resource="http://reference.data.gov.uk/id/open-government-licence">
                <a href="http://reference.data.gov.uk/id/open-government-licence">
                    UK Open Government Licence (OGL)
                </a>
            </div>

            <!-- additional markup with further description of dataset -->
        </div>        

This revised example also includes the `odrs:reuserGuidelines` property which can be used to provide a link to further documentation for data re-users. These guidelines might be an FAQ or other user guide that provides a useful overview of the rights statement. In this example the same web page contains both user guidance and a copyright statement.

#### Publishing Standalone Rights Statements

In the previous examples a description of a dataset and its rights statement have been marked up in a single web page. If you are publishing only a single dataset then this will likely be sufficient. If your rights statements will vary across datasets, e.g. to include different licensing, copyright or attribution details, then you should use a per-dataset rights statement.

However if you are publishing several datasets under the same terms then it may be easier to publish a standard rights statement that applies to all of your datasets.

For example the following HTML includes a machine-readable rights statement that might be accessible from: `http://gov.example.org/rights`:

        <div typeof="odrs:RightsStatement" resource="http://gov.example.org/rights#rights">
            <h1 property="rdfs:label">Rights Statement for Re-use Of Our Open Data</h1>                      

            <p>All our data is published under the 
                 <a href="http://reference.data.gov.uk/id/open-government-licence" 
                    property="odrs:contentLicense">UK Open Government Licence (OGL)</a>
            </p>

            <p>If you would like to attribute your use of our data then, 
               please use a link similar to the following: 
                  <a href="http://gov.example.org/open-data" 
                     property="odrs:attributionURL">
                       <span property="odrs:attributionText">Example Department</span>
                  </a>.
            </p>
        </div>

This standard rights statement could then be referenced from dataset descriptions published elsewhere on your website:

        <div typeof="dcat:Dataset" resource="http://gov.example.org/dataset/example">
            <h1 property="dct:title">Example Dataset</h1>                      

            <p>This dataset is published under an open license. Read our 
                <a href="http://gov.example.org/rights#rights""
                    property="dct:rights">standard rights statement</a> for details.
            </p>            
        
            <!-- additional markup with further description of dataset -->
        </div>

### Publishing Rights Statements in Linked Data

The following examples all use the [Turtle](http://www.w3.org/TR/turtle/) RDF syntax. For clarity the prefix definitions have been omitted from individual examples. You should assume that the following set of prefixes are defined:

    @prefix cc: <http://creativecommons.org/ns#> .
    @prefix dcat: <http://www.w3.org/ns/dcat#> .
    @prefix dct: <http://purl.org/dc/terms/> .
    @prefix odrs: <http://schema.theodi.org/odrs#> .
    @prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
    @prefix : <http://example.org/data/> .

#### Defining a Rights Statement with a single Licence

The following example illustrates how to associate a rights statement with a DCAT dataset:

	:example1
		a dcat:Dataset ;
		dct:title "Example Dataset" ;
		dct:rights :example1-rights-statement;
		dct:license <http://reference.data.gov.uk/id/open-government-licence>.

	:example1-rights-statement
		a odrs:RightsStatement;
		rdfs:label "Rights relating to re-use of the Example Dataset" ;
		odrs:dataLicense <http://reference.data.gov.uk/id/open-government-licence> ;
		odrs:attributionText "Example " ;
		odrs:attributionURL <https://www.gov.uk/government/organisations/ministry-of-justice>.
	   
#### Defining a Rights Statement with multiple Licences

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

#### Including Copyright Notices and User Guidelines

The following example illustrates how add a copyright notice and a reference to a reuser guidelines:

    :example3
        a dcat:Dataset ;
        dct:title "Example Dataset" ;
        dct:rights :example3-rights-statement;
        dct:license <http://reference.data.gov.uk/id/open-government-licence>.

    :example3-rights-statement
        a odrs:RightsStatement;
        rdfs:label "Rights relating to re-use of the Example Dataset" ;
        odrs:copyrightHolder "Crown copyright";
        odrs:copyrightYear "2013";
        odrs:reuserGuidelines <http://gov.example.org/reuser-guide>;
        odrs:dataLicense <http://reference.data.gov.uk/id/open-government-licence> ;
        odrs:attributionText "Example Department" ;
        odrs:attributionURL <https://www.gov.uk/government/organisations/ministry-of-justice>.

#### Combining the ODRS and ccREL vocabularies

The ODRS vocabulary can be combined with the Creative Commons `ccREL` vocabulary to provide more detailed descriptions of custom data licenses. While publishers are encouraged to use an "off-the-shelf" license wherever possible, in the circumstances where a custom license is required then it would be useful to have a machine-readable description of the key facets of that license.

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
        
The above example includes a rights statement that refers to a custom licence. The licence is described using terms from the Creative Commons vocabulary including a link to its legal definition and a series of permissions and requirements. 

This particular licence is a variation of the CC-BY licence: it permits the creation of derivative works, distribution and reproduction of the data and the re-user must include all copyright notices and license derivatives using similar terms; but there is no _legal_ requirement to include attribution.

Like `ccREL` the [ODRL](http://www.w3.org/community/odrl/) vocabulary aims to provide more detailed expression of re-use policies and can be similarly combined with the ODRS vocabulary.

### Linking to Rights Statements from Web APIs

As well as raw data downloads, datasets may also be published via a web API, allowing users to query and extract portions of the data as they need it. The data exposed via the API should also be associated with a clear rights statement. Rather than burying this information in API documentation or the terms of use of a service it can be referenced directly from the results of an API request.

The simplest approach to this is to include a link from the API response to a rights statement published elsewhere, e.g. as RDFa annotations to existing API documentation. 

The `Link` HTTP header defined by [RFC5988](http://tools.ietf.org/html/rfc5988) can be used to add links to HTTP API responses without the need to change the body of the response. This avoids the need to change existing formats and potential impacts on users.

For example an HTTP GET request to the fictitious API available at `http://api.example.org/search` might return the following response:

    HTTP/1.1 200 OK
    Cache-Control: max-age=86400, must-revalidate
    Content-Type: application/json
    Date: Mon, 17 Jun 2013 13:45:45
	Link: <http://opendatacommons.org/licenses/odbl/>; rel="license", 
	      <http://api.example.org/docs/rights>; rel="http://purl.org/dc/terms/rights"
    Server: Apache/2.2.3 (CentOS)
    Vary: Accept
    Content-Length: 12345
 
    { ...some JSON data... }

The HTTP response includes a `Link` header that defines two links for this HTTP response. The first uses the standard `license` relation to refer to the data licence associated with the data included in the response. This relation is equivalent to the `dct:license` property used in the RDFa and Linked Data examples. Where included it should reference the data license for the API response.

A custom link relation is also included in the response. This relation uses the URI of the `dct:rights` relationship as the identifier for the relationship. Its value if a link to a separate machine-readable rights statement. An application might follow this link and extract RDFa from the resulting web page to determine the licenses, attribution requirements, etc associated with the API.

Link relations might also be used directly in API responses. Some standard formats define extensible link elements that could also be used to reference a rights statement. For example an Atom based API might include `atom:link` elements to reference a rights statement.

It is increasingly common for Web APIs to be based on JSON. The following section looks in more detail at publishing rights statements in JSON formats.

### Publishing Rights Statements in JSON

The following example shows a simple JSON object that describes a simple, standalone rights statement. 

        {
            "contentLicense": "http://reference.data.gov.uk/id/open-government-licence",
            "dataLicense": "http://reference.data.gov.uk/id/open-government-licence",
            "copyrightNotice": "Crown copyright",
            "copyrightYear": "2013",
            "attributionText": "Example Department",
            "attributionURL": "http://gov.example.org/dataset/example"
        }

This structure uses a trivial encoding of the ODRS vocabulary into JSON, with the object having keys that directly correspond to the properties defined by the ODRS vocabulary. 

To include a rights statement in a document that also, for example, describes a dataset, use a `rights` key as follows:

        {
            "title": "Example Dataset",
            "license": "http://reference.data.gov.uk/id/open-government-licence",
            "rights": {
                "contentLicense": "http://reference.data.gov.uk/id/open-government-licence",
                "dataLicense": "http://reference.data.gov.uk/id/open-government-licence",
                "copyrightNotice": "Crown copyright",
                "copyrightYear": "2013",
                "attributionText": "Example Department",
                "attributionURL": "http://gov.example.org/dataset/example"
            }
        }

#### Interpreting a JSON Rights Statement as JSON-LD and RDF

[JSON-LD](http://json-ld.org/) is a light-weight data format for publishing Linked Data as JSON. 

JSON-LD documents can be processed as JSON but also have a standard mapping to RDF. In addition to defining some conventions for encoding data in JSON documents, JSON-LD also defines a way to [allow simple JSON to be interpreted as JSON-LD](http://json-ld.org/spec/latest/json-ld/#interpreting-json-as-json-ld) and hence as RDF. This is achieved by interpreting the data using a JSON-LD context.

A JSON-LD context can be referenced from an HTTP `Link` header, allowing applications that wish to process the data as JSON-LD or as RDF to easily convert the data. For example a GET request to a standalone JSON document containing a rights statement could reference a JSON-LD context as follows:

    HTTP/1.1 200 OK
    Cache-Control: max-age=86400, must-revalidate
    Content-Type: application/json
    Date: Mon, 17 Jun 2013 13:45:45
	Link: <http://schema.theodi.org/odrs/odrs-jsonld.json>; 
          rel="http://www.w3.org/ns/json-ld#context"; type="application/ld+json"
    Server: Apache/2.2.3 (CentOS)
    Content-Length: 12345
 
    { ...the rights statement as JSON... }

The JSON-LD context available from `http://schema.theodi.org/odrs/odrs-jsonld.json` defines how JSON key-value pairs should be interpreted and mapped to the ODRS vocabulary. The complete JSON-LD context for the ODRS vocabulary is included below:

    {
        "@context": {
            "RightsStatement": "http://schema.theodi.org/odrs#RightsStatement",
            "License": "http://schema.theodi.org/odrs#License",
            "rights": {
                "@id": "http://purl.org/dc/terms/rights",
                "@type": "@id"
            },
            "license": {
                "@id": "http://purl.org/dc/terms/license",
                "@type": "@id"
            },
            "dataLicense": {
                "@id": "http://schema.theodi.org/odrs#dataLicense",
                "@type": "@id"
            },
            "contentLicense": {
                "@id": "http://schema.theodi.org/odrs#contentLicense",
                "@type": "@id"
            },
            "reuserGuidelines": {
                "@id": "http://schema.theodi.org/odrs#reuserGuidelines",
                "@type": "@id"
            },
            "attributionURL": {
                "@id": "http://schema.theodi.org/odrs#attributionURL",
                "@type": "@id"
            },
            "copyrightStatement": {
                "@id": "http://schema.theodi.org/odrs#copyrightStatement",
                "@type": "@id"
            },
            "copyrightHolder": "http://schema.theodi.org/odrs#copyrightHolder",
            "copyrightYear": "http://schema.theodi.org/odrs#copyrightYear",
            "attributionText": "http://schema.theodi.org/odrs#attributionText"
        }
    }

While this context is suitable for use with simple standalone rights statements, if your JSON documents include additional data, e.g. a dataset description, then you may need to include this context alongside your own definitions.

#### Publishing Rights Statements directly as JSON-LD

The following final example shows a single JSON-LD document that contains a description of a dataset and its associated rights statement. The example illustrates how to publish a rights statement directly as a JSON-LD document. In this instance the `@context` is simply used to declare some prefixes for properties used elsewhere in the document:

    {
        "@context": {
            "dcat": "http://www.w3.org/ns/dcat#",
            "dct": "http://purl.org/dc/terms/",
            "odrs": "http://schema.theodi.org/odrs#",
            "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#"
        },
        "@id": "http://gov.example.org/dataset/example",
        "@type": "dcat:Dataset",
        "dct:title": "Example Dataset",
        "dct:license": {
            "@id": "http://reference.data.gov.uk/id/open-government-licence",
            "dct:title": "UK Open Government Licence (OGL)"
        },
        "dct:rights": {
            "rdfs:label": "Rights Statement",
            "@id": "http://gov.example.org/dataset/example#rights",
            "odrs:copyrightHolder": "Crown copyright",
            "odrs:copyrightYear": "2013", 
            "odrs:attributionText": "Example Department",
            "odrs:attributionURL": {
                "@id": "http://gov.example.org/dataset/example"
            },
            "odrs:contentLicense": {
                "@id": "http://reference.data.gov.uk/id/open-government-licence"
            },
            "odrs:dataLicense": {
                "@id": "http://reference.data.gov.uk/id/open-government-licence"
            }
        }
    }


