# Global Biodiversity Information Facility (GBIF)

The [Global Biodiversity Information Facility](https://gbif.org) is an international network and open-access data infrastructure that aims to facilitate free and open access to biodiversity data from around the world.

For data publishing GBIF provides a tool called [Integrate Publishing Toolkit](https://www.gbif.org/ipt) (IPT) which after installed into a GBIF network node, it can share biodiversity data stored in node's databases or dataset created by users who have access to the IPT web interface.

Biotic interactions data can be published in GBIF, even though GBIF is not indexing this kind of that at the moment. It means that, despite it is possible to find and access the published datasets, GBIF does not offer a search mechanism for biotic interactions. It does not fully accomplishes with the [FAIR Principle F4](findable-f4).

```{warning}
The approach described here is for a new version IPT not yet released for general use ([3.0-RC2-SNAPSHOT version](https://github.com/gbif/ipt/tree/ipt-3.0-RC1)).
```

## Creating a new resource in IPT for biotic interactions

After successful log in into a IPT installation access the IPT `Manage Resources` page and select `Create New` option to create a new resource (dataset). In the `Create New Resource` page you MUST provide a shortname for your dataset and choose the option `Darwin Core Interaction Package (Interaction DP)` option as resource `Type` ({numref}`ipt-new`).

```{figure} ../../images/ipt-new.png
---
name: ipt-new
---
Create a new `Darwin Core Interaction Package (Interaction DP)` in IPT
```

## Upload and mapping source data

For generating a Data Package you need to upload the text-delimited files generated from the [publishing model template](https://docs.google.com/spreadsheets/d/1tbJ3yN_zQNoihBbjKdyrx-xZVCSr1_PSTB1wSAr0jJQ). After all files have been upload the files MUST be mapped back to the corresponding files in the `Publishing Model` ({numref}`ipt-mapping`).

```{figure} ../../images/ipt-mapping.png
---
name: ipt-mapping
---
Set `Source Data` and `Data Mappings` in IPT for `Darwin Core Interaction Package (Interaction DP)`.
```

## Filling metadata

In IPT there are some basic metadata fields from EML that needs to be filled ({numref}`ipt-metadata`).

```{figure} ../../images/ipt-metadata.png
---
name: ipt-metadata
---
Basic metadata needs to be filled in IPT.
```

## Publishing

To publish the recently created/edited dataset you need to click in the `Publish` option as shown in {numref}`ipt-pub`.

```{figure} ../../images/ipt-pub.png
---
name: ipt-pub
---
Publishing a dataset in IPT
```

## Persistent Identifier

GBIF uses DOI as PID for datasets published on its registry. However, the DOI are not updated or changed when new versions of the dataset were created. The DOI always redirect to the latest version of the dataset. For example the DOI [https://doi.org/10.15468/kjbp3w](https://doi.org/10.15468/kjbp3w) redirects to the latest version of the datasets `Occurrences in Sinbiota`.
