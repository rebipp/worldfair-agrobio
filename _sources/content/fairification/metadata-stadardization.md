(metadata-std)=
# Metadata standardization

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

Metadata standards refer to established guidelines or specifications defining how metadata, which provides information about data, is structured, formatted, and described. These standards ensure consistency and interoperability in describing data elements, aiding in their organization, discovery, and management. They outline rules for creating, storing, and managing metadata to ensure uniformity and comprehension across different systems, making it easier to exchange, locate, and interpret various types of data.

There are different types of metadata which can overlap or complement each other, and their application depends on the specific needs of data management, retrieval, and usage within different contexts;

- **Descriptive Metadata**: this type describes the content and context of the data, providing information such as titles, abstracts, keywords, and summaries that help users understand what the data is about.

- **Structural Metadata**: it outlines how the components of a dataset are organized, including information about relationships, hierarchy, and sequence of data elements. Structural metadata might describe tables, fields, and their relationships.

- **Administrative Metadata**: it includes details about ownership, access rights, versioning, {term}`provenance` (data origin), creation and modification dates, and other aspects relevant to data governance and stewardship.

- **Technical Metadata**: this type encompasses technical details about the data, such as file formats, sizes, data types, encoding schemes, software used to create or modify the data, and technical specifications necessary for data processing or interpretation.

- **Rights Metadata**: Rights metadata contains information regarding intellectual property rights, licensing, restrictions, and permissions associated with the data, ensuring compliance with legal and ethical considerations.

(eml)=
## The Ecological Metadata Language

The [Ecological Metadata Language (EML)](https://eml.ecoinformatics.org/) {cite}`EML_2019`, offers a comprehensive vocabulary and a user-friendly XML markup syntax designed to document ecological data. Widely adopted within the earth and environmental sciences and increasingly utilized in various research fields, EML remains a community-driven standard. Its continual evolution caters to researchers seeking open documentation, preservation, and data sharing. EML comprises modules covering data package identification and citation, delineation of spatial, temporal, taxonomic, and thematic data extents, description of research methodologies, intricate data structure and content delineation, and precise data annotation using semantic vocabularies.

The EML project is an open source, community oriented project dedicated to providing a high-quality metadata specification for describing data relevant to diverse disciplines that involve observational research like ecology, earth, and environmental science.

It has been used by biodiversity community as metadata standard, including the [Global Biodiversity Information Facility (GBIF)](https://gbif.org) and [DataONE](https://dataone.org) (a network of data repositories).

The EML standard contains a large number of terms providing the elements to a rich description of datasets, their contents, structure and semantics. However, we can enumerate a minimum set of terms which MUST be present in the metadata of the biotic interactions datasets to meet the FAIR principles.

## The minimum set of terms for biotic interactions

In the metadata of biotic interactions datasets the following term MUST be present:

- `title`: a description of the resource that is being documented that is long enough to differentiate it from other similar resources.
- dataset `creators`:
    - `individualName`: the full name of the people who created this resource,
    - `organizationName`: the full name of the organizations who created this resource,
    - `electronicMailAddress`: the email addresses of the people who created this resource,
-  `keywordSet`: keyword information that describes the resource,
- license:
    - `licenseName`: the official name of a license that applies to the data and metadata described in this metadata record. The name should match the name of a well-known license from the SPDX license vocabulary or a similar persistent vocabulary,
    - `url`: the persistent URL for the license, typically a SPDX URL, or an official URL from another well-known license vocabulary.  Users should avoid using arbitrary URLs that are not the official URL for a license,

The following metadata elements are RECOMMENDED to be included in order to improve reusability of datasets:

```{admonition} FAIR PRINCIPLE F2
:class: findable
(Meta)data include qualified references to other (meta)data
```

- `abstract`: a brief overview of the resource,
- `intellectualRights`: intellectual property rights regarding usage and licensing of this resource,
- `geographicCoverage`: geographic coverage information.
- `temporalCoverage`: temporal coverage information,
- `taxonomicCoverage`: taxonomic coverage information,
- `methods`: documents the scientific methods used in the data collection or generation,
- `referencePublication`: a citation to an additional publication that serves as an important reference for a dataset,
- `literatureCited`: a citation to articles or products which were referenced in the dataset or its associated metadata.

## Tools

Generating EML files using XML or text editors can be complex and unproductive. For that reason, there are some tools which can help the creation of metadata description in EML:

- [ezEML](https://ezeml.edirepository.org/eml/about): a form-based online application designed to streamline the creation of metadata in the Ecological Metadata Language (EML).
- [EML](https://github.com/ropensci/eml): Ecological Metadata Language interface for R,
- [python-eml](https://github.com/pieterprovoost/python-eml): a Python package containing dataclasses for the Ecological Metadata Language (EML) standard.

## References

```{bibliography}
:filter: docname in docnames
```

