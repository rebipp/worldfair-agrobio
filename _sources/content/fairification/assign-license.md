(license-assign)=
# License Assignment

## FAIR Principles Met

```{admonition} FAIR PRINCIPLE R1.1
:class: reusable
(Meta)data are released with a clear and accessible data usage license
```

## Why assigning a license is important?

Assigning licenses to datasets is fundamental in ensuring legal clarity, promoting reuse, enabling interoperability, enhancing accessibility, and supporting responsible data practices—key aspects within the FAIR principles.

Licenses provide legal clarity about how the data can be used. They define the terms under which the data can be accessed, modified, shared, and reused. This clarity is essential for users to understand what they are allowed to do with the dataset. A dataset with clear licensing encourages data reuse, since when users know the terms of use, they are more likely to confidently reuse the data in their own research, applications, or projects.

## Licensing and EML

In the [Ecological Metadata Language](eml) the term `licensed` is used to provide information about a dataset license. The EML term is meant to be highly structured to allow machine-interpretable licenses to be asserted for the dataset.  This is done by identifying a well-defined license or contract and providing the SPDX license key or the license URL, and the name of the license. Where possible, the name, URL, and SPDX key should match the values found in the official [SPDX license vocabulary](https://spdx.org/licenses/).  If the license is not found in SPDX, then other well-established URIs for licenses can be used, but avoid using arbitrary URIs that are not maintained for persistence.

Alternatively to the SPDX licenses, open licenses (which allows others to reuse another creator’s work as they wish) the EML `licensed` term can be used with definitions from the [OpenDefinition](https://opendefinition.org/licenses/), a documentation published by the [Open Knowledge Foundation (OKFN)](https://okfn.org). The advantage of using licenses from OpenDefinition is that for every open license it also provides machine readable versions of the licenses in JSON format.