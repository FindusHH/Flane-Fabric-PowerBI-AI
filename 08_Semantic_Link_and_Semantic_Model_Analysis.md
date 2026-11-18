# 8. Semantic Link and Semantic Model Analysis

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [8.1 Semantic Link and SemPy: Concepts and Packages](#81-semantic-link-and-sempy-concepts-and-packages)
- [8.2 Semantic Link Overview and Sample Notebooks](#82-semantic-link-overview-and-sample-notebooks)
- [8.3 Explore a Semantic Model and Evaluate Measures](#83-explore-a-semantic-model-and-evaluate-measures)
- [8.4 Analyze Relationships and Validate Data](#84-analyze-relationships-and-validate-data)
- [8.5 Analyze Models with Ready-made Notebooks and Semantic Link Labs](#85-analyze-models-with-ready-made-notebooks-and-semantic-link-labs)
- [8.6 Manage the Semantic Model Lifecycle](#86-manage-the-semantic-model-lifecycle)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://github.com/microsoft/fabric-samples/blob/main/features-samples/semantic-link/Semantic%20Link%20all-in-one%20demo.ipynb" target="_blank" rel="noopener noreferrer">Explore Semantic Link in an all-in-one notebook</a> | [8.3 Explore a Semantic Model and Evaluate Measures](#83-explore-a-semantic-model-and-evaluate-measures) | Explore a sample semantic model, evaluate measures, run DAX, and examine data quality. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures" target="_blank" rel="noopener noreferrer">Extract and calculate Power BI measures</a> | [8.3 Explore a Semantic Model and Evaluate Measures](#83-explore-a-semantic-model-and-evaluate-measures) | List and evaluate measures from a sample semantic model using SemPy. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies" target="_blank" rel="noopener noreferrer">Analyze functional dependencies</a> | [8.4 Analyze Relationships and Validate Data](#84-analyze-relationships-and-validate-data) | Test dependencies between columns and identify data-quality issues using SemPy. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships" target="_blank" rel="noopener noreferrer">Discover semantic model relationships</a> | [8.4 Analyze Relationships and Validate Data](#84-analyze-relationships-and-validate-data) | Discover relationships between tables and check for relationship violations. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection" target="_blank" rel="noopener noreferrer">Discover relationships in the Synthea dataset</a> | [8.4 Analyze Relationships and Validate Data](#84-analyze-relationships-and-validate-data) | Detect and visualize relationships in sample data. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations" target="_blank" rel="noopener noreferrer">Validate data with SemPy and Great Expectations</a> | [8.4 Analyze Relationships and Validate Data](#84-analyze-relationships-and-validate-data) | Validate semantic model data using SemPy and Great Expectations earlier than version 1.0. |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/21b-manage-semantic-model-lifecycle.html" target="_blank" rel="noopener noreferrer">Manage the semantic model lifecycle</a> | [8.6 Manage the Semantic Model Lifecycle](#86-manage-the-semantic-model-lifecycle) | Validate a model with SemPy, fix missing relationships, and promote the validated solution through Development and Production stages (approximately 45 minutes). |

**Teaching note:** Begin with the concepts and overview, then use an end-to-end notebook and select focused exercises for measures, relationships, and data quality. Use the lifecycle lab for a broader **Validate → Fix → Deploy** workflow that includes a deployment pipeline. The ready-made model-analysis notebooks and Semantic Link Labs examples offer additional practical paths.

## 8.1 Semantic Link and SemPy: Concepts and Packages

**Semantic Link** is the Microsoft Fabric capability that connects Power BI semantic models with Fabric data science. It makes both model data and semantic information—such as measures, relationships, data categories, and hierarchies—available in data-science workflows. Semantic Link is supported in Microsoft Fabric.

Semantic Link provides access through two paths:

- **SemPy (Python/pandas):** the Python library for working with semantic models and their metadata in notebooks. Its `FabricDataFrame` extends pandas with semantic metadata and lineage.
- **Spark native connector:** provides access from the Spark ecosystem, including PySpark, Spark SQL, R, and Scala.

The PyPI package names describe how the Python components are distributed:

| Package | Purpose |
| --- | --- |
| [`semantic-link-sempy`](https://pypi.org/project/semantic-link-sempy/) | The core SemPy package, including the `sempy` Python modules and Fabric semantic-model functionality. |
| [`semantic-link`](https://pypi.org/project/semantic-link/) | A convenience meta-package that installs the Semantic Link packages together, including `semantic-link-sempy` and optional semantic-function packages. |

In supported Fabric runtimes, Semantic Link is preinstalled. Install or update packages only when needed for a different environment, a newer version, or specific dependency requirements. If only the core SemPy functionality is required, installing `semantic-link-sempy` individually can avoid adding optional package dependencies.

**Semantic Link Labs** is a separate open-source library, distributed as [`semantic-link-labs`](https://pypi.org/project/semantic-link-labs/) and imported as `sempy_labs`. It builds on SemPy with additional model-management and analysis utilities; it is not the same package as either `semantic-link-sempy` or the `semantic-link` meta-package.

## 8.2 Semantic Link Overview and Sample Notebooks

- **Semantic link** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/semantic-link-overview" target="_blank" rel="noopener noreferrer">What is semantic link?</a> — **Overview/reference:** explains how semantic link connects Power BI semantic models with Fabric data science and notebooks.

> **Key resource: Semantic Link sample notebooks**
>
> [Semantic link samples](https://github.com/microsoft/fabric-samples/tree/main/docs-samples/data-science/semantic-link-samples) — **Sample notebook collection:** find and download notebooks accompanying the Semantic Link tutorials below. The repository itself is not a step-by-step guide.

## 8.3 Explore a Semantic Model and Evaluate Measures

- ⭐ **Explore Semantic Link in an all-in-one notebook** — <a href="https://github.com/microsoft/fabric-samples/blob/main/features-samples/semantic-link/Semantic%20Link%20all-in-one%20demo.ipynb" target="_blank" rel="noopener noreferrer">Semantic Link all-in-one demo</a> — **Hands-on notebook tutorial:** set up the Retail Analysis sample, explore and query its semantic model, evaluate measures, run DAX, and examine data quality. Requires a Fabric workspace; some examples also require a lakehouse.

- ⭐ **Extract and calculate Power BI measures** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures" target="_blank" rel="noopener noreferrer">Calculate Power BI measures from a Jupyter notebook</a> — **Hands-on notebook tutorial:** list and evaluate measures from a sample semantic model using SemPy.

## 8.4 Analyze Relationships and Validate Data

- ⭐ **Analyze functional dependencies** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies" target="_blank" rel="noopener noreferrer">Analyze functional dependencies in a semantic model</a> — **Hands-on notebook tutorial:** use SemPy and a sample model to test dependencies between columns and identify data-quality issues.

- ⭐ **Discover semantic model relationships** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships" target="_blank" rel="noopener noreferrer">Discover relationships in a semantic model using semantic link</a> — **Hands-on notebook tutorial:** discover relationships between tables and check for relationship violations using SemPy.

- ⭐ **Discover relationships in the Synthea dataset** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection" target="_blank" rel="noopener noreferrer">Discover relationships in the Synthea dataset</a> — **Hands-on notebook tutorial:** detect and visualize relationships in sample data, from a small example to a larger set of tables.

- ⭐ **Validate data with SemPy and Great Expectations** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations" target="_blank" rel="noopener noreferrer">Validate data using SemPy and Great Expectations</a> — **Hands-on notebook tutorial:** configure expectations and validate data from a Power BI semantic model. The tutorial uses Great Expectations versions earlier than 1.0.

## 8.5 Analyze Models with Ready-made Notebooks and Semantic Link Labs

- **Use notebooks with a semantic model** — <a href="https://learn.microsoft.com/en-us/power-bi/transform-model/service-notebooks" target="_blank" rel="noopener noreferrer">Use notebooks with a semantic model</a> — **Practical guide:** open ready-made notebooks from a semantic model to run best-practice and memory analysis. Requires suitable workspace access, model permissions, and Fabric capacity.

- **Semantic Link Labs code examples** — [Code Examples](https://github.com/microsoft/semantic-link-labs/wiki/Code-Examples) — **Practical code examples:** use Python notebook snippets for tasks such as model best-practice analysis and memory analysis.

## 8.6 Manage the Semantic Model Lifecycle

- ⭐ **Manage the semantic model lifecycle** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/21b-manage-semantic-model-lifecycle.html" target="_blank" rel="noopener noreferrer">Manage the semantic model lifecycle</a> — **Hands-on lab (approximately 45 minutes):** create sample data, inspect a semantic model and validate data quality with SemPy, fix missing relationships through a read/write TOM connection, then promote the validated solution from Development to Production using a deployment pipeline. Requires Fabric capacity; both pipeline workspaces must be on Fabric or Premium capacity. Review the lab's license and workspace requirements before starting. Related learning path: <a href="https://learn.microsoft.com/en-us/training/modules/manage-semantic-model-lifecycle/" target="_blank" rel="noopener noreferrer">Manage the semantic model development lifecycle</a>.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
