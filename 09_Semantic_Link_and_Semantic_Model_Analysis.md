# 9. Semantic Link and Semantic Model Analysis

[Back to agenda](./Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [9.1 Semantic Link Overview and Sample Notebooks](#91-semantic-link-overview-and-sample-notebooks)
- [9.2 Explore a Semantic Model and Evaluate Measures](#92-explore-a-semantic-model-and-evaluate-measures)
- [9.3 Analyze Relationships and Validate Data](#93-analyze-relationships-and-validate-data)
- [9.4 Analyze Models with Ready-made Notebooks and Semantic Link Labs](#94-analyze-models-with-ready-made-notebooks-and-semantic-link-labs)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Teaching note:** Begin with the overview and an end-to-end notebook, then select focused exercises for measures, relationships, and data quality. The ready-made model-analysis notebooks and Semantic Link Labs examples offer additional practical paths.

## 9.1 Semantic Link Overview and Sample Notebooks

- **Semantic link** — [What is semantic link?](https://learn.microsoft.com/en-us/fabric/data-science/semantic-link-overview) — **Overview/reference:** explains how semantic link connects Power BI semantic models with Fabric data science and notebooks.

- **Semantic link sample notebooks** — [Semantic link samples](https://github.com/microsoft/fabric-samples/tree/main/docs-samples/data-science/semantic-link-samples) — **Sample notebook collection:** download the notebooks accompanying the semantic link tutorials below; the repository itself is not a step-by-step guide.

## 9.2 Explore a Semantic Model and Evaluate Measures

- 🛠️ **Explore Semantic Link in an all-in-one notebook** — [Semantic Link all-in-one demo](https://github.com/microsoft/fabric-samples/blob/main/features-samples/semantic-link/Semantic%20Link%20all-in-one%20demo.ipynb) — **Hands-on notebook tutorial:** set up the Retail Analysis sample, explore and query its semantic model, evaluate measures, run DAX, and examine data quality. Requires a Fabric workspace; some examples also require a lakehouse.

- 🛠️ **Extract and calculate Power BI measures** — [Calculate Power BI measures from a Jupyter notebook](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures) — **Hands-on notebook tutorial:** list and evaluate measures from a sample semantic model using SemPy.

## 9.3 Analyze Relationships and Validate Data

- 🛠️ **Analyze functional dependencies** — [Analyze functional dependencies in a semantic model](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies) — **Hands-on notebook tutorial:** use SemPy and a sample model to test dependencies between columns and identify data-quality issues.

- 🛠️ **Discover semantic model relationships** — [Discover relationships in a semantic model using semantic link](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships) — **Hands-on notebook tutorial:** discover relationships between tables and check for relationship violations using SemPy.

- 🛠️ **Discover relationships in the Synthea dataset** — [Discover relationships in the Synthea dataset](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection) — **Hands-on notebook tutorial:** detect and visualize relationships in sample data, from a small example to a larger set of tables.

- 🛠️ **Validate data with SemPy and Great Expectations** — [Validate data using SemPy and Great Expectations](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations) — **Hands-on notebook tutorial:** configure expectations and validate data from a Power BI semantic model. The tutorial uses Great Expectations versions earlier than 1.0.

## 9.4 Analyze Models with Ready-made Notebooks and Semantic Link Labs

- **Use notebooks with a semantic model** — [Use notebooks with a semantic model](https://learn.microsoft.com/power-bi/transform-model/service-notebooks) — **Practical guide:** open ready-made notebooks from a semantic model to run best-practice and memory analysis. Requires suitable workspace access, model permissions, and Fabric capacity.

- **Semantic Link Labs code examples** — [Code Examples](https://github.com/microsoft/semantic-link-labs/wiki/Code-Examples) — **Practical code examples:** use Python notebook snippets for tasks such as model best-practice analysis and memory analysis.

[Back to contents](#chapter-contents)

[Back to agenda](./Agenda%20with%20Tutorials.md)
