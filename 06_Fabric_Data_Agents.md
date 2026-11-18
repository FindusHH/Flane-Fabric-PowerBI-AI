# 6. Fabric Data Agents

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [6.1 Data Agent Concepts and Setup](#61-data-agent-concepts-and-setup)
- [6.2 Hands-on Data Agent Scenarios](#62-hands-on-data-agent-scenarios)
- [6.3 Ground a Data Agent in an Ontology](#63-ground-a-data-agent-in-an-ontology)
- [6.4 Integrate Data Agents with Copilot Studio and Foundry](#64-integrate-data-agents-with-copilot-studio-and-foundry)
- [6.5 Related Path: Connect AI Agents to Fabric through MCP](#65-related-path-connect-ai-agents-to-fabric-through-mcp)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-end-to-end-tutorial" target="_blank" rel="noopener noreferrer">Fabric Data Agent with AdventureWorks</a> | [6.2 Hands-on Data Agent Scenarios](#62-hands-on-data-agent-scenarios) | Populate a lakehouse with sample data, create a data agent, and ask questions. |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html" target="_blank" rel="noopener noreferrer">Chat with sales data using a Fabric Data Agent</a> | [6.2 Hands-on Data Agent Scenarios](#62-hands-on-data-agent-scenarios) | Create a sales warehouse and data agent, then explore how questions are translated into SQL (approximately 30 minutes). |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html" target="_blank" rel="noopener noreferrer">Build a healthcare Data Agent with an ontology</a> | [6.3 Ground a Data Agent in an Ontology](#63-ground-a-data-agent-in-an-ontology) | Set up a healthcare ontology and configure and test a data agent using the older ontology experience (approximately 30 minutes). |

**Teaching note:** Learn the agent basics, then select a lakehouse or warehouse exercise. Ontology grounding and external integrations are separate paths; the GraphQL MCP guide connects AI agents to Fabric but does not configure a Fabric Data Agent.

## 6.1 Data Agent Concepts and Setup

- **Data Agent concepts and fundamentals** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent" target="_blank" rel="noopener noreferrer">What is a Fabric data agent?</a> — **Overview/reference:** introduces Fabric Data Agent concepts and capabilities.

- **Fabric Data Agents** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/how-to-create-data-agent" target="_blank" rel="noopener noreferrer">Create a Fabric data agent</a> — **Step-by-step how-to:** create an agent, add data sources, select tables, and configure it. Requires paid Fabric capacity and accessible data.

## 6.2 Hands-on Data Agent Scenarios

- ⭐ **Fabric Data Agent with AdventureWorks** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-end-to-end-tutorial" target="_blank" rel="noopener noreferrer">Data agent example with the AdventureWorks dataset</a> — **Hands-on tutorial (preview):** populate a lakehouse with sample data, create an agent, and ask questions. Requires paid Fabric capacity and appropriate tenant settings.

- ⭐ **Chat with sales data using a Fabric Data Agent** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html" target="_blank" rel="noopener noreferrer">Chat with your data using Microsoft Fabric data agents</a> — **Hands-on lab (approximately 30 minutes):** create a sales warehouse and configure a data agent, then ask plain English questions and inspect how they are translated into SQL queries. Requires paid Fabric capacity; trial capacity is not supported.

## 6.3 Ground a Data Agent in an Ontology

- **Connect a Data Agent to an ontology** — <a href="https://learn.microsoft.com/en-us/fabric/iq/ontology/how-to-create-data-agent" target="_blank" rel="noopener noreferrer">Create a data agent grounded in an ontology</a> — **Step-by-step how-to (preview):** add an ontology as a data source and ask questions in natural language. Currently, ontologies bound to semantic models are not supported by this integration.

- ⭐ **Build a healthcare Data Agent with an ontology** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html" target="_blank" rel="noopener noreferrer">Build a Fabric data agent with an ontology</a> — **Hands-on lab (preview, approximately 30 minutes):** create the Lamna Healthcare ontology with a setup notebook, configure agent instructions, test natural language questions, and publish and share the agent. Requires paid Fabric capacity and appropriate tenant settings; trial capacity is not supported. Uses the older ontology experience, scheduled to retire on January 31, 2027; it is not a direct continuation of lab 24.

## 6.4 Integrate Data Agents with Copilot Studio and Foundry

- **Use a Data Agent in Copilot Studio** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio" target="_blank" rel="noopener noreferrer">Consume a Fabric data agent in Microsoft Copilot Studio</a> — **Integration guide:** consume a Fabric Data Agent from Copilot Studio.

- **Add a Data Agent as a Copilot Studio tool** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-microsoft-copilot-studio-tool" target="_blank" rel="noopener noreferrer">Add a Fabric data agent as a tool in Microsoft Copilot Studio</a> — **Integration guide:** configure a Fabric Data Agent as a tool in Copilot Studio.

- **Use a Data Agent with Microsoft Foundry** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry" target="_blank" rel="noopener noreferrer">Consume Fabric data agent from Microsoft Foundry Services</a> · <a href="https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/fabric" target="_blank" rel="noopener noreferrer">Fabric data agent as a tool in the Foundry Agent Service</a> — **Integration guides:** use Fabric Data Agents from Foundry and as an agent tool.

## 6.5 Related Path: Connect AI Agents to Fabric through MCP

- **Connect AI agents to Fabric through MCP** — <a href="https://learn.microsoft.com/en-us/fabric/data-engineering/api-graphql-local-model-context-protocol" target="_blank" rel="noopener noreferrer">Connect AI Agents to Fabric API for GraphQL with a local MCP server</a> — **Integration guide:** connect an AI agent to a Fabric GraphQL API using a local MCP server; this is separate from the Fabric Data Agent integrations above.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
