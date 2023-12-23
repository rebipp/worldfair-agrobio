(fair-principles)=
# The FAIR Principles

## Introduction

FAIR stands for Findable, Accessible, Interoperable, and Reusable, representing a paradigm shift in how data is managed, shared, and utilized across various domains.

**Findability** encapsulates the notion that data should be easily discoverable by both humans and machines. 

**Accessibility** ensures that once data is found, it can be accessed, be it through open or controlled means, ensuring inclusivity and transparency in data availability.

**Interoperability** focuses on the seamless interaction between different systems, enabling data exchange and integration across various platforms and domains. 

Lastly, **Reusability** emphasizes the importance of ensuring that once accessed, data can be effectively reused for various purposes, maximizing its value and potential.

These principles are not just theoretical concepts; they form a guiding framework, influencing data management practices, technological advancements, and policy implementations worldwide. By adhering to the FAIR principles, data becomes more than just information—it becomes a catalyst for innovation, collaboration, and informed decision-making.

## The FAIR Guiding Principles 

:::{dropdown} Findability
:open:
:color: danger
**To be Findable:**
(findable-f1)=
- F1. (meta)data are assigned a `globally unique and persistent identifier`
(findable-f2)=
- F2. data are described with `rich metadata` (defined by [R1 below](reusable-r1))
(findable-f3)=
- F3. metadata `clearly and explicitly include the identifier of the data it describes`
(findable-f4)=
- F4. (meta)data are registered or `indexed in a searchable resource`
:::


:::{dropdown} Accessibilityy
:open:
:color: warning
**To be Accessible:**
(accessiable-a1)=
- A1. (meta)data are retrievable by their identifier using a `standardized communications protocol`
    - A1.1 the protocol is `open, free, and universally implementable`
    - A1.2 the protocol allows for an `authentication and authorization procedure, where necessary`
(accessiable-a2)=
- A2. `metadata are accessible`, even when the data are no longer available
:::


:::{dropdown} Interoperability
:open:
:color: success
**To be Interoperable:**
(interoperable-i1)=
- I1. (meta)data use a `formal, accessible, shared, and broadly applicable language for knowledge representation`.
(interoperable-i2)=
- I2. (meta)data use `vocabularies that follow FAIR principles`
(interoperable-i3)=
- I3. (meta)data include `qualified references to other (meta)data`
:::

:::{dropdown} Reusability
:open:
:color: info
**To be Reusable:**
(reusable-r1)=
- R1. meta(data) are `richly described with a plurality of accurate and relevant attributes`
    - R1.1. (meta)data are released with a `clear and accessible data usage license`
    - R1.2. (meta)data are associated with detailed `provenance`
    - R1.3. (meta)data meet domain-relevant `community standards`
:::

```{figure} ../../images/fair-paper.png
---
name: fair-paper
target: https://doi.org/10.1038/sdata.2016.18
---
The FAIR Principles the cover pages for the FAIR principle articles as published in Scientific Data. [https://doi.org/10.1038/sdata.2016.18](https://doi.org/10.1038/sdata.2016.18), {cite}`fair2016`.
```

## Additional resources

- [GoFAIR](https://www.go-fair.org/): is a bottom-up, stakeholder-driven and self-governed initiative that aims to implement the FAIR data principles, making data Findable, Accessible, Interoperable and Reusable (FAIR)
- [The FAIR Cookbook for FAIR doers](https://faircookbook.elixir-europe.org/): An online, open and live resource for the Life Sciences with recipes that help you to make and keep data Findable, Accessible, Interoperable and Reusable; in one word FAIR.

## References

```{bibliography}
:filter: docname in docnames
```