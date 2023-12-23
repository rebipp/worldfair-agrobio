(data-std)=
# Data Standardization

## FAIR Principles Met

```{admonition} FAIR PRINCIPLE I1
:class: interoperable
(Meta)data use a formal, accessible, shared, and broadly applicable language for knowledge representation
```

```{admonition} FAIR PRINCIPLE I2
:class: interoperable
(Meta)data use vocabularies that follow the FAIR principles
```

```{admonition} FAIR PRINCIPLE I3
:class: interoperable
(Meta)data include qualified references to other (meta)data
```

## Introduction

Data standardization is the process of transforming data into a common format or structure to ensure consistency, comparability, and compatibility across different datasets or systems. It involves cleaning, formatting, and organizing data to adhere to predefined norms or guidelines, making it easier to analyze, integrate, and share information effectively.

In the biodiversity domain the [Biodiversity Information Standards](https://tdwg.org) (TDWG) is a non-profit organization and a community dedicated to developing biodiversity information standards. The TDWG is involved in developing, ratifying and promoting standards and guidelines for the recording and exchange of data about organisms; and acting as a forum for discussing all aspects of biodiversity information management through meetings, online discussions, and publications. A list of all standards in TDWG auspicius can be found at: [https://www.tdwg.org/standards/](https://www.tdwg.org/standards/).

Among the TDWG standards, the [Darwin Core standard](https://dwc.tdwg.org) is widely used to document occurrence data.
> It includes a glossary of terms (in other contexts these might be called properties, elements, fields, columns, attributes, or concepts) intended to facilitate the sharing of information about biological diversity by providing identifiers, labels, and definitions. Darwin Core is primarily based on taxa, their occurrence in nature as documented by observations, specimens, samples, and related information.

Despite it has been initially defined for occurrence data, it has been used for documeting other kinds of data, such as biotic interactions. Due its flexibility and capability to be extended it has been used within other vocabularies and ontologies.


## Biotic interactions and the Darwin Core standard

The Darwin Core (DwC) provides many different terms for documenting biotic interactions (e.g. `associatedTaxa`, `associatedOccurrences`, `ResourceRelatinship`). However, we recommend the usage of the schema proposed in {cite:t}`salim2022`, which is based on the Darwin Core `Event` and `ResourceRelationship` classes for represeting biotic interactions. Accordiing to the authors the proposed schema:
>recognizes the importance of context-dependent information, which drives biotic interaction in nature {cite}`Hoeksema2010,Butterfield2013,Chamberlain2014,Maron2014,Hoeksema2015,Frederickson2017`.

The schema for biotic interactions has its grounds in the *co-action* definition proposed by {cite:t}`haskell1949clarification`, futher refined by {cite:t}`Lidicker1979` for biotic interactions, and more recent, the biotic interactions model of *interaction events* introduced by {cite:t}`Gomez2023`.

Instances of DwC `Event` class serve as representations of interaction events. These instances capture essential information about the interactions, such as temporal data and sampling details. Additionally, geographic information can be included in the event using terms from the DwC `Location` class. The interacting organisms or taxa are represented by their respective instances of the DwC `Occurrence` and DwC `Taxon` classes. These classes serve as the basis of documenting data about individual organisms or species involved in the interactions. By linking these instances to an instance of `Event` the data schema enables the representation of a pairwise interaction. It is common that biotic interactions are sampled with a particular interest in organisms’ traits and the effects and outcomes of the interactions in which they participate. In DwC it is possible to include these data using the `MeasurementOrFact` class, but more complex representations can be achieved using extensions like the [Extended Measurement or Fact](https://rs.gbif.org/extension/obis/extended_measurement_or_fact.xml) {cite}`Pooter2017` developed by [Ocean Biodiversity Information System (OBIS)](https://obis.org/), or the [Ecological Trait-data Standard Vocabulary](https://github.com/EcologicalTraitData/ETS) {cite}`Schneider2019a`. The eMoF is particularly useful when using the Darwin Core-Archive format because it addresses the limitations of the star-schema in representing one-to-many relationships. Instances of `MeasurementOrFact` class, or its extensions, can be associated with instances of the `Event` class to represent interaction effects and outcomes. Similarly, these measurements or facts cat also be linked to instances of the `Occurrence` class, representing the traits of specific organisms or effects of the interaction on an individual organism or group of organisms. See {numref}`biotic-interaction-schema` for a graphical representation of the data schema.

```{figure} ../../images/data-model-ppi.png
---
name: biotic-interaction-schema
---
Data schema for represeting biotic interactions using Darwin Core. Only the `identifiers` and `relationshipType` are shown.
```

## The Plant-Pollinator Interactions Vocabulary (PPI)

The Darwin Core standard does not aim to cover all use cases and specificities of biodiversity data. However, it can be used with other vocabularies to enrich data annotation and standardization of data elements which do not have correspoding concepts defined by the DwC.

However, it is common that organisms' traits and interaction outcomes and effects data to be present in biotic interaction datasets. In addition, these data elements should be also standardized and it can be achived by the adoption of community-specificic vocabularies. In this case the [REBIPP Plant-Pollinator Interaction Vocabulary](https://ppi.rebipp.org.br) (PPI) provides additional terms to the stadardization of plant-animal interactions datasets.

The PPI vocabulary is recommended to be used within the Darwin Core `MeasurementOrFact` class as controlled vocabulary for the term `measurementType`. The PPI vocabulary also defines [controlled vocabularies](https://ppi.rebipp.org.br/cv/) for some its terms, and then, the terms in the controlled vocabularies should be used as values for the `measurementValue` term of the DwC `MeasurementOrFact` class.

## Other vocabularies, thesauri and ontologies

## Tools

Data standardization can be a complex and time consuming process, for that reason many tools have been created to facilitate this task. Bellow is a list a some tools which can help with data standardization:

- [REBIPP Plant-Pollinator Interactions Dataset Template](https://docs.google.com/spreadsheets/d/1z2mvs6Bm7fE5IhxPRVbh1ieEfKsVKeIiK_mitPqvPJw/copy): a Google Sheet template with controlled vocabularies for terms from DwC and PPI. In the template each row represents an interaction between a plant and an animal. Columns from the spreadsheet can be removed if they are not needed, but the inclusion of new columns is not RECOMMENDED.

- [GloBI dataset template](https://github.com/globalbioticinteractions/template-dataset): a simplified dataset template to make data available through [Global Biotic Interactions](http://globalbioticinteractions.org/).

```{admonition} Attention
:class: danger
REBIPP and GloBI template only simplify the process of data standardization. However, data transformation from original format to one of these templates **IS NOT SUFFICIENT** to consider data as standardized. The templates act as intermediate representation between original data and the standardized data which REBIPP Database and GloBI will generate when publishing the datasets. We call these template as **PUBLISHING MODELS**, which differ from the **DATA MODELS** as shown in {numref}`biotic-interaction-schema`
```


## References

```{bibliography}
:filter: docname in docnames
```