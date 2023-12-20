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

Instances of DwC `Event` class serve as representations of interaction events. These instances capture essential information about the interactions, such as temporal data and sampling details. Additionally, geographic information can be included in the event using terms from the DwC `Location` class. The interacting organisms or taxa are represented by their respective instances of the DwC `Occurrence` and DwC `Taxon` classes. These classes serve as the basis of documenting data about individual organisms or species involved in the interactions. By linking these instances to an instance of `Event` the data schema enables the representation of a pairwise interaction. It is common that biotic interactions are sampled with a particular interest in organisms’ traits and the effects and outcomes of the interactions in which they participate. In DwC it is possible to include these data using the `MeasurementOrFact` class, but more complex representations can be achieved using extensions like the [Extended Measurement or Fact](https://rs.gbif.org/extension/obis/extended_measurement_or_fact.xml) {cite}`Pooter2017` developed by [Ocean Biodiversity Information System (OBIS)](https://obis.org/), or the [Ecological Trait-data Standard Vocabulary](https://github.com/EcologicalTraitData/ETS) {cite}`Schneider2019a`. The eMoF is particularly useful when using the Darwin Core-Archive format because it addresses the limitations of the star-schema in representing one-to-many relationships. Instances of `MeasurementOrFact` class, or its extensions, can be associated with instances of the `Event` class to represent interaction effects and outcomes. Similarly, these measurements or facts cat also be linked to instances of the `Occurrence` class, representing the traits of specific organisms or effects of the interaction on an individual organism or group of organisms.

## References

```{bibliography}
```