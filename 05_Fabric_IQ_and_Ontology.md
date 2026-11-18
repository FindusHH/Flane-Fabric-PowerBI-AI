# 5. Fabric IQ and Ontology

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [5.1 Fabric IQ Overview](#51-fabric-iq-overview)
- [5.2 Create and Populate an Ontology](#52-create-and-populate-an-ontology)
- [5.3 Explore and Visualize Ontology Data](#53-explore-and-visualize-ontology-data)

**Key Microsoft Learn references**

- <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/overview" target="_blank" rel="noopener noreferrer">What Is Ontology (Preview)?</a>
- <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/how-to-generate-from-semantic-models" target="_blank" rel="noopener noreferrer">Generate Ontology (Preview) from Semantic Models</a>
- <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/concepts-agent-integration" target="_blank" rel="noopener noreferrer">Agent Integration Options for Ontology (Preview)</a>

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/tutorial-0-introduction" target="_blank" rel="noopener noreferrer">Create a Fabric ontology</a> | [5.2 Create and Populate an Ontology](#52-create-and-populate-an-ontology) | Prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html" target="_blank" rel="noopener noreferrer">Build a healthcare ontology manually</a> | [5.2 Create and Populate an Ontology](#52-create-and-populate-an-ontology) | Build and populate a healthcare ontology using the new experience (approximately 40 minutes). |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html" target="_blank" rel="noopener noreferrer">Generate an ontology from a semantic model</a> | [5.2 Create and Populate an Ontology](#52-create-and-populate-an-ontology) | Generate a healthcare ontology from a semantic model and add time-series bindings (approximately 45 minutes). |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html" target="_blank" rel="noopener noreferrer">Visualize healthcare ontology data</a> | [5.3 Explore and Visualize Ontology Data](#53-explore-and-visualize-ontology-data) | Use a separate setup notebook to explore and visualize an ontology in the older experience (approximately 30 minutes). |

**Teaching note:** Start with the Fabric IQ overview, then choose an ontology creation path. The visualization lab uses an older ontology experience and its own setup notebook; it is not a direct continuation of the newer-experience labs.

## 5.1 Fabric IQ Overview

- **Fabric IQ** — <a href="https://learn.microsoft.com/en-us/fabric/iq/overview" target="_blank" rel="noopener noreferrer">What is Fabric IQ?</a> — **Overview/reference:** introduces Fabric IQ and its components; it is not a build tutorial.

## 5.2 Create and Populate an Ontology

- ⭐ **Create a Fabric ontology** — <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/tutorial-0-introduction" target="_blank" rel="noopener noreferrer">Ontology tutorial: Introduction and environment setup</a> — **Hands-on tutorial series (preview):** prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. Requires Fabric capacity and enabled tenant settings.

- ⭐ **Build a healthcare ontology manually** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html" target="_blank" rel="noopener noreferrer">Create an ontology with Fabric IQ</a> — **Hands-on lab (preview, approximately 40 minutes):** create entity types, properties, keys, and relationships, then bind hospital reference data from a lakehouse and sample time-series readings from an eventhouse. Uses the new ontology experience; paid or trial Fabric capacity and enabled ontology tenant settings are required.

- ⭐ **Generate an ontology from a semantic model** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html" target="_blank" rel="noopener noreferrer">Build an ontology from a semantic model in Fabric IQ</a> — **Hands-on lab (preview, approximately 45 minutes):** build a healthcare semantic model, generate ontology entities and relationships, and add eventhouse time-series bindings. Uses the new ontology experience; requires paid or trial Fabric capacity, enabled tenant settings, and Read and Build permissions on the semantic model.

## 5.3 Explore and Visualize Ontology Data

- ⭐ **Visualize healthcare ontology data** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html" target="_blank" rel="noopener noreferrer">Visualize ontology data with Microsoft Fabric IQ</a> — **Hands-on lab (preview, approximately 30 minutes):** use a setup notebook to create the sample ontology, then explore entity instances, relationship graphs, property charts, time-series data, and the Query builder. Requires paid or trial Fabric capacity and enabled ontology tenant settings. Uses the older ontology experience rather than the new experience used in labs 23 and 24.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
