# ArKG data documentation

On this site, you can download the latest version of the ArKG dataset and find some preliminary documentation (under development). At the bottom, you can find and download the different versions of the dataset. Next, we briefly present some technical details of the graph representation.

The ArKG knowledge graph is modeled as an RDF graph, a format for describing graph data. Data is stored as triples:

> (subject, predicate, object)

where *subject* and *object* are nodes in the graph data, and *predicate* is a label that gives a meaning to the connection between both. In ArKG, each date data item is a node, connected to other data items (such as locations, dates, materials, etc.) through triples. Therefore, the predicates state the *type* of the connection between different data items.

The following namespaces and prefixes are used in ArKG:

| Prefix | Namespace URI | Description |
| :------- | :------- | :------- |
| **`rdf:`** | <http://www.w3.org/1999/02/22-rdf-syntax-ns#> | RDF syntax vocabulary. |
| **`rdfs:`** | <http://www.w3.org/2000/01/rdf-schema#> | RDF Schema vocabulary. |
| **`wd:`** | <http://www.wikidata.org/entity/> | Wikidata entities. |
| **`wdt:`** | <http://www.wikidata.org/prop/direct/> | Wikidata direct properties. |
| **`arkgp:`** | <https://arkg.cl/property/> | ArKG custom properties (predicates). |
| **`arkgd:`** | <https://arkg.cl/datings/> | ArKG dates. Each date is identified as `arkgd:D000001`, `arkgd:D000002`, etc. |
| **`arkgs:`** | <https://arkg.cl/sites/> | ArKG archaeological sites. Each site is identified as `arkgs:S000001`, `arkgs:S000002`, etc. |
| **`:`** | <https://arkg.cl/> | ArKG classes (e.g., `:ArchSite`) and controlled vocabulary values (e.g., materials such as `:Charcoal`). |

The following classes are used in ArKG:

| Class | Description |
| :------- | :------- |
| **`:Fechado`** | A radiometric date (one dated sample). |
| **`:ArchSite`** | An archaeological site. |
| **`:GeographicalEntity`** | A geographic entity of the political-administrative hierarchy (e.g., commune, province, region, country). Extended variant only. |

The following table describes each predicate currently supported/used in ArKG. Predicates marked as *Extended variant only* are not present in the Pure variant of the dataset:

| Predicate | Description |
| :------- | :------- |
| **`rdf:type`** | Class or category to which the resource belongs. |
| **`rdfs:label`** | Readable label associated with the resource's URI. |
| **`wdt:P186`** *(made from material)* | The type of sample analyzed (e.g, bone, wood, shell,etc.)|
| **`wdt:P9047`** *(archaeological site of)* | Name of the archaeological site where the archaeological date was discovered. |
| **`wdt:P1343`** *(described by source)* | Bibliographic source or publication where the archaeological date is reported.|
| **`wdt:P585`** *(point in time)* | Date when the analysis of the archaeological date was performed.|
| **`wdt:P131`** *(is located in)* | The item is located on the territory of the following administrative entity. *Extended variant only.*|
| **`wdt:P17`** *(country)* | Sovereign state that this item is in. *Extended variant only.*|
| **`arkgp:site_name`** | Name of the archaeological site. It has the same value as `rdfs:label`.|
| **`arkgp:lab_code`** | Laboratory code of the date, as reported in the source. Codes are not guaranteed to be unique: some dates share a code or have none ("-").|
| **`arkgp:dating_method`** | Dating method used, can be **wd:Q173412** (radiocarbon dating) or **wd:Q2727388** (thermoluminescence dating).|
| **`arkgp:14C_age`** | Uncalibrated radiocarbon age expressed in years BP.|
| **`arkgp:14C_type`** | Type of radiocarbon measurement, can be **wd:Q530255** (AMS) or **wd:Q80354132** (conventional).|
| **`arkgp:TL_Age_AC_DC`** | Age obtained through **Thermoluminescence** (**TL**), expressed in BC/AD years.|
| **`arkgp:TL_Age_BP`** | Age obtained through **Thermoluminescence** (**TL**), expressed in years BP, i.e., years before the reference year given by `arkgp:reference_year`.|
| **`arkgp:reference_year`** | Reference year ("present") from which the BP age of the date is counted. It is 1950 for all radiocarbon dates, and the reference year of the measurement for thermoluminescence dates, when reported in the source.|
| **`arkgp:x`** , **`arkgp:y`** | Geographic coordinates of the site in decimal degrees (longitude and latitude, respectively).|
| **`arkgp:sd`** | Standard deviation associated with the age measurement.|
| **`arkgp:delta13C`** | Measure of the proportion of stable carbon isotopes.|
| **`arkgp:sample_type_info`** | Information about the type of sample analyzed.|
| **`arkgp:age_info`** | Additional information about the archaeological age.|
