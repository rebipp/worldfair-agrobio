---
jupytext:
  formats: md:myst
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

(intro-pids)=
# Persistent Unique Identifiers

Persistent Unique Identifiers refer to specific codes or labels assigned to digital objects, data sets, publications, or entities in a manner that ensures their uniqueness and longevity throughout their lifecycle, regardless of changes in location, format, or ownership.

These identifiers are designed to be persistent, meaning they remain unchanged and continue to point to the same digital object even if it undergoes modifications, moves across different systems or repositories, or evolves over time. The persistence of these identifiers is crucial in maintaining traceability, ensuring reliable referencing, and enabling the retrieval of digital objects across various platforms and domains.

PUIDs serve as digital fingerprints or keys that enable unambiguous identification and access to specific digital entities. They play a vital role in data management, facilitating the discoverability, accessibility, interoperability, and reusability of digital information—aligning with the FAIR principles (Findable, Accessible, Interoperable, and Reusable) in data management.

Common examples of Persistent Unique Identifiers include DOI (Digital Object Identifier) for scholarly articles, ORCID iD for researchers, ISBN for books, and other standardized codes specifically designed to uniquely identify and persistently reference digital objects within their respective domains.

## Minting identifiers

The fundamental principle is that identifiers must be distinct, establishing an exclusive link between each "identifier" and the corresponding entity.

In isolated systems that operate independently, the likelihood of identifier collision is null. However, within such closed environments, distinct systems may generate local identifiers that, despite being identical, reference entirely separate entities. In fact, this happens all the time.

These identifiers are denoted as `locally unique` due to their exclusivity within their respective systems. However, their uniqueness is not guaranteed when compared across all existing systems, thereby lacking `global uniqueness`.

## Producing globally unique identifiers

Creating `globally unique identifiers` involves generating codes or labels that are guaranteed to be `distinct across different systems, locations, or contexts worldwide`. 

Several approaches ensure the generation of such identifiers.

### UUID based identifiers

Universally Unique Identifiers (UUID) are standardized identifiers generated using specific algorithms to ensure their uniqueness across diverse systems. UUIDs follow specific patterns and are highly unlikely to be duplicated, even when generated independently in separate locations.

The probability of a **collision** (two UUIDs being the same) for randomly generated UUIDs is extremely low, bordering on statistically negligible due to the vast number of possible UUID combinations.

UUIDs are `128-bit numbers`, allowing for a theoretical total of `2^128 (approximately 3.4 x 10^38)` unique combinations. Generating this enormous number of unique identifiers means the probability of two UUIDs being identical is exceptionally remote, even when generating UUIDs at an incredibly high rate.

For context, generating one billion UUIDs per second would take over 100 billion years to exhaust the potential space of unique UUIDs. This demonstrates the minuscule likelihood of collision when using properly generated UUIDs.

The [RFC4122 specifications](https://tools.ietf.org/html/rfc4122), published by the [Internet Engineering Task Force](https://www.ietf.org/) (IETF), outlines the structure, generation methods, and different variants of UUIDs. It provides guidelines for creating UUIDs to ensure uniqueness across across both space and time.

```{note} Note
Key facts about UUID:
- no `centralized authority` is required to administer them,
- `content independent`, UUIDs do not carry information or context about the content it identifies,
- geration can be `automated`,
- `non resolvable`
- completly `semantic free (opaque) identifier`
```

- Generation of UUID using `Python`:

```{code-cell} ipython3
import uuid
id = uuid.uuid4() 

print(id)
```

- Generation of UUID using `R`:
```R
library(uuid)
UUIDgenerate()
```
```R
[1] "a33252da-902c-4482-be8c-82bcc104230f"
```

- Generation of UUID using `uuidgen` in `Unix` systems:

```bash
uuidgen
A76A1029-0418-4706-B8D1-5A7E4948724B
```

```{hint}
Microsoft Excel, Google Sheet and MacOS Numbers do not have functions for generating UUIDs. But you can create you own function to generate UUIDs and reuse it over your spreadsheets.
See more in [Additional Resources](extra)
```

### Centralized Authority or Registry

Establishing a `centralized authority or registry` that assigns and manages unique identifiers across different entities or systems can ensure global uniqueness. Examples include entities like `ISBN` (International Standard Book Number) for books or `DOI` (Digital Object Identifier).


```{note} Note
Key facts about DOI:
- `centralized authority` is required to administer them,
- `content dependent`, DOIs are specifically assigned to individual digital objects or resources, linking directly to the content they identify,
- `resolvable` identifiers
```

### Content Hash Identifiers

Content Hash Identifiers (CHIs) are identifiers generated based on the content of a digital object rather than arbitrary or structured identifiers like UUIDs or DOIs. These identifiers are derived from the content itself through a hashing algorithm, producing a `unique identifier` that represents the `content's characteristics`. The hash function generates a fixed-length alphanumeric string based on the input content. Even a minor change in the content would result in a significantly different hash value.

{cite:t}`elliott2020` propose a method for creating cryptographic hashing using SHA256 algorithm to generate content-based identifiers that can reliably reference datasets.

```{note} Note
Key facts about CHIs:
- `no centralized authority` is required to administer them,
- `content dependent`,
- geration can be `automated`,
- `non resolvable`
```

- Generation in `Python`:

```{code-cell} iphyton
import hashlib

# encode it to bytes using UTF-8 encoding
message = "creating globally unique identifiers for FAIR data".encode()

# hash with SHA-2 (SHA-256 bits & SHA-512 bits long)
print("SHA-256:", hashlib.sha256(message).hexdigest())
```

- Generation in `R`:

```R
library(digest)
digest("creating globally unique identifiers for FAIR data", algo="sha256", serialize=FALSE, raw=TRUE)
```

```R
[1] "119c6fe9833bcdf315c380593197283d1bc343e73fc4dab0bddaee47491b0184"
```

- Generation of CHI using `sha256sum` in `Unix` systems:

```bash
echo -ne "creating globally unique identifiers for FAIR data" | sha256sum
119c6fe9833bcdf315c380593197283d1bc343e73fc4dab0bddaee47491b0184  -
```

- Generation of CHI for a dataset using `sha256sum`:
```bash
curl -L "https://docs.google.com/spreadsheets/d/1cJ0qX9ppqHoSyqFykwYJef-DFOzoutthBXjwKRY81T8/export?format=tsv&gid=776329546" | sha256sum
4d20e242ebfa3a09cafeb3f9a523b6d669b82d8a8ff9f5df63f53ea3fb220a6a  -
```

## Resolvable Identifiers

Now that we've delved into the technical aspects of creating identifiers that are globally persistent and unique, the next important topic to address is `enabling identifiers to be resolved`, which is also referred to as making them `dereferenceable`.

A `resolvable identifier` is one that can be used to **retrieve or access the digital object or resource it represents**. `When an identifier is resolvable, it means that using that identifier provides a means to` locate, access, or retrieve the associated digital content or information`.

For instance, a resolvable DOI (Digital Object Identifier) allows you to access the specific resource it identifies by entering it into a DOI resolver, which directs you to the dataset's location, typically on a repository.

Resolvability is a critical attribute of identifiers, especially in digital systems, as it ensures that using the identifier leads to the intended digital object or resource, allowing for seamless access, retrieval, or interaction with the identified content.

The globally unique identifiers created for the `web` rely on the Uniform Resource Locators (`URL`) and on the Hypertext Transfer Protocol (`HTTP(S)`) .

## Uniform Resource Locators (URLs)

Uniform Resource Locators (URLs) are addresses used to identify resources on the internet and specify their locations. They serve as the web's addressing system, providing a standardized way to access various resources such as web pages, files, images, videos, or any other content available on the internet.

The structure of `URL`, according to the [World Wide Web Consortium](https://www.w3.org/) (W3C) specification, is as follow:

```
URI = scheme:[//authority]path[?query][#fragment]
```

Where:
- `scheme`: specified the protocol used to access the resource. In the realm of FAIR data the most relevant protocols are `http` and `https`, representing the `Hypertext Transfer Protocol` and its secure counterpart, the `Hypertext Transfer Protocol Secure`.
- `authority`: according to the [IETF](https://www.ietf.org/) specifications, it presents the following format:
    - `authority = [userinfo@]host[:port]` where:
    - `host` corresponds to the `Internet Protocol` (IP) address or `hostname` (e.g. `www.example.com`) of a server hosting a resource
    - `userinfo` and `port` are optional and should be avoided in identifiers for data.
- `path`: denotes the specific location or file on the `host`. It directs client to the resource within the `host`'s directory structure,
- `query`: optional parameters that provide additional information to the `host`, often used in dynamic web pages to pass data or parameters. In the context resolvable identiers, query components should be avoided,
- `fragment`: an optional part that identifies a specific portion within the resource, commonly used in longer documents to navigate to a particular section.


## Generating Resolvable URLs

In FAIR data context, web resources require **uniqe**, **persistent**, and **resolvable** identifiers. To ensure persistence, these identifiers must adhere to the [RFC 3986 IETF standard](https://datatracker.ietf.org/doc/html/rfc3986) for URIs . This implies they must encompass the following components:

- `scheme`: `https`,
- an `authority`: `www.example.com`
- optionally a `path`: `/dataset-title`,
- a local identifier or `globally unique identifier` (such as UUID or hash)

**Examples**:

 - Resolvable Hash Content Identifier:
```
ADD A RESOLVABLE HASH CONTENT IDENTIFIER EXAMPLES
```

- Resolvable local identifier: 

[`https://arctos.database.museum/guid/MSB:Mamm:233627`](https://arctos.database.museum/guid/MSB:Mamm:233627)

- Resolvable globally identifier (UUID):
[`https://treatment.plazi.org/id/0000C505-BB5D-484C-76BE-9AB6999DEB23`](https://treatment.plazi.org/id/0000C505-BB5D-484C-76BE-9AB6999DEB23)

- DOI:

[`https://doi.org/10.5281/zenodo.6245874`](https://doi.org/10.5281/zenodo.6245874)

## Identifier resolution

## Conclusions

## References

```{bibliography}
:filter: docname in docnames
```