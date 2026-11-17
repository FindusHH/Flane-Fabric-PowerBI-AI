# 6. Fabric IQ and Ontology

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [6.1 Fabric IQ Overview](#61-fabric-iq-overview)
- [6.2 Create and Populate an Ontology](#62-create-and-populate-an-ontology)
- [6.3 Explore and Visualize Ontology Data](#63-explore-and-visualize-ontology-data)

**Key Microsoft Learn references**

- [What Is Ontology (Preview)?](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview)
- [Generate Ontology (Preview) from Semantic Models](https://learn.microsoft.com/en-us/fabric/iq/ontology/how-to-generate-from-semantic-models)
- [Agent Integration Options for Ontology (Preview)](https://learn.microsoft.com/en-us/fabric/iq/ontology/concepts-agent-integration)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ [Create a Fabric ontology](https://learn.microsoft.com/en-us/fabric/iq/ontology/tutorial-0-introduction) | [6.2 Create and Populate an Ontology](#62-create-and-populate-an-ontology) | Prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. |
| ⭐ [Build a healthcare ontology manually](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html) | [6.2 Create and Populate an Ontology](#62-create-and-populate-an-ontology) | Build and populate a healthcare ontology using the new experience (approximately 40 minutes). |
| ⭐ [Generate an ontology from a semantic model](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html) | [6.2 Create and Populate an Ontology](#62-create-and-populate-an-ontology) | Generate a healthcare ontology from a semantic model and add time-series bindings (approximately 45 minutes). |
| ⭐ [Visualize healthcare ontology data](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html) | [6.3 Explore and Visualize Ontology Data](#63-explore-and-visualize-ontology-data) | Use a separate setup notebook to explore and visualize an ontology in the older experience (approximately 30 minutes). |

**Teaching note:** Start with the Fabric IQ overview, then choose an ontology creation path. The visualization lab uses an older ontology experience and its own setup notebook; it is not a direct continuation of the newer-experience labs.

## 6.1 Fabric IQ Overview

- **Fabric IQ** — [What is Fabric IQ?](https://learn.microsoft.com/en-us/fabric/iq/overview) — **Overview/reference:** introduces Fabric IQ and its components; it is not a build tutorial.

## 6.2 Create and Populate an Ontology

- ⭐ **Create a Fabric ontology** — [Ontology tutorial: Introduction and environment setup](https://learn.microsoft.com/en-us/fabric/iq/ontology/tutorial-0-introduction) — **Hands-on tutorial series (preview):** prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. Requires Fabric capacity and enabled tenant settings.

- ⭐ **Build a healthcare ontology manually** — [Create an ontology with Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html) — **Hands-on lab (preview, approximately 40 minutes):** create entity types, properties, keys, and relationships, then bind hospital reference data from a lakehouse and sample time-series readings from an eventhouse. Uses the new ontology experience; paid or trial Fabric capacity and enabled ontology tenant settings are required.

- ⭐ **Generate an ontology from a semantic model** — [Build an ontology from a semantic model in Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html) — **Hands-on lab (preview, approximately 45 minutes):** build a healthcare semantic model, generate ontology entities and relationships, and add eventhouse time-series bindings. Uses the new ontology experience; requires paid or trial Fabric capacity, enabled tenant settings, and Read and Build permissions on the semantic model.

## 6.3 Explore and Visualize Ontology Data

- ⭐ **Visualize healthcare ontology data** — [Visualize ontology data with Microsoft Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** use a setup notebook to create the sample ontology, then explore entity instances, relationship graphs, property charts, time-series data, and the Query builder. Requires paid or trial Fabric capacity and enabled ontology tenant settings. Uses the older ontology experience rather than the new experience used in labs 23 and 24.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
