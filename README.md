# ODI Open Data Licensing

This project contains the source and documentation for the 
Open Data Rights Statement (ODRS) vocabulary.

The ODRS vocabulary is designed to support the publication of 
machine-readable "rights statements" that describe:

* Which license(s) apply to a dataset -- there may be several, covering both the data and the content
* The preferred means of attributing the dataset
* A copyright statement
* Pointers to additional documentation

The vocabulary builds on [previous work](https://github.com/theodi/open-data-licensing/wiki/Related-Work), particularly Dublin Core and the Creative Commons ccREL vocabulary.

The [wiki](https://github.com/theodi/open-data-licensing/wiki) has some background documentation

## Feedback

If you have feedback on the vocabularly please [submit an issue](https://github.com/theodi/schemas/issues) (or even a pull request). This will allow us to capture and organise issues, their discussion and resolution.

## Project Structure

The project is organised as follows:

* `schema` -- the original turtle source for the schema, and the markdown documentation and diagrams
* `examples` -- example uses of the vocabulary for different kinds of datasets and a variety of vocabularies
* `guides` -- markdown source for the publisher and re-user guides that describe how to publish and consume data using this vocabulary

## Publishing the vocabulary

Note: this might change in future.

Currently the actual schema documentation is generated using [dowl](https://github.com/ldodds/dowl) which is a Ruby command-line tool for generating simple documentation from RDFS and OWL schema.

The project `Rakefile` uses the tool to generate the documentation, 
which is then published to the [ODI schema project](https://github.com/theodi/schemas) for live hosting.

## Pointers

* [Related Work](https://github.com/theodi/open-data-licensing/wiki/Related-Work)
* [Design Rationale](https://github.com/theodi/open-data-licensing/wiki/Design-Rationale)
