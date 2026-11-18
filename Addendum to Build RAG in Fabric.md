# Addendum to Build RAG in Fabric

This addendum accompanies Microsoft's <a href="https://learn.microsoft.com/en-us/fabric/data-science/quickstart-building-retrieval-augmented-generation" target="_blank" rel="noopener noreferrer">Build retrieval-augmented generation in Microsoft Fabric</a> tutorial. It summarizes account and tenant requirements, setup considerations, and code caveats to review before running the notebook.

## Do Fabric and Azure AI Search need the same account or tenant?

**Not for the authentication flow shown in this tutorial.** Fabric and Azure AI Search do not have to use the same user account, Azure subscription, or Microsoft Entra tenant for the notebook's key-based Search connection to work.

The notebook uses two separate connections:

| Connection | Authentication |
| --- | --- |
| Fabric notebook to Fabric's built-in AI endpoint | The Fabric identity and the built-in Fabric client |
| Fabric notebook to Azure AI Search | The Search endpoint and an Azure AI Search API key |

The notebook passes the Search key through `AzureKeyCredential` to create or query the index. Microsoft documents that a Search request using key authentication is authorized by the key and the service's key-authentication setting, rather than by the caller's Fabric identity. This means the accounts can be separate in this specific setup. Microsoft doesn't state a blanket cross-tenant guarantee for every network and organizational configuration, so verify your own tenant policies and service access.

If you replace the API key with Microsoft Entra ID or managed identity, this tutorial no longer applies unchanged. Configure the identity and least-privilege Azure AI Search roles: **Search Service Contributor** for index management, **Search Index Data Contributor** for uploads, and **Search Index Data Reader** for queries. Cross-tenant identity and role assignment need to be planned separately; they are not automatically solved by using the same notebook.

References: <a href="https://learn.microsoft.com/en-us/azure/search/search-security-api-keys" target="_blank" rel="noopener noreferrer">Azure AI Search API keys</a> · <a href="https://learn.microsoft.com/en-us/azure/search/search-security-rbac" target="_blank" rel="noopener noreferrer">Role-based access control for Azure AI Search</a>.

## Prerequisites and account setup

- **Fabric capacity:** The tutorial lists F64. The current general AI Functions documentation lists paid capacity F2 or higher, or a P capacity. Those requirements do not match exactly. For a class or production-style run, use the tutorial's stated F64 requirement unless you have tested and confirmed a smaller capacity is supported for the complete notebook in your environment. A Fabric user license alone does not provide capacity.
- **Tenant settings and region:** An administrator might need to enable Copilot and other Azure OpenAI-powered Fabric features. Depending on the Fabric and capacity locations, a cross-geo data-processing setting might also be required. Confirm both before the session.
- **Lakehouse and environment:** Attach a lakehouse to the notebook. The tutorial uses the accompanying `environment.yaml`; create, save, and publish the Fabric environment, then select it before running the import and setup cells. The current SynapseML guide specifies Fabric Runtime 1.3 or later.
- **Separate AI and Search costs:** The built-in Fabric AI endpoint avoids creating a separate Azure OpenAI resource or managing its API key for this example. However, Spark execution and AI calls consume Fabric capacity. Azure AI Search is a separate Azure resource with its own tier, limits, and possible costs.

References: <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/overview#prerequisites" target="_blank" rel="noopener noreferrer">AI Functions prerequisites</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-python-sdk#use-the-built-in-openai-compatible-clients" target="_blank" rel="noopener noreferrer">Built-in Fabric OpenAI-compatible clients</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-synapse-ml" target="_blank" rel="noopener noreferrer">Use Azure OpenAI in Fabric with SynapseML</a>.

## Azure AI Search access and networking

The tutorial creates or updates an index and uploads documents, so its API-key approach needs an **admin key**. A query key is read-only and is not sufficient for the indexing steps. The Search service must also allow API-key authentication. Keep the admin key out of shared notebooks, source control, and output cells; use an approved secret-management approach for a shared or persistent solution.

Network access is separate from authentication. A valid key cannot connect through a blocked firewall. Requests originate from the Fabric notebook's Spark environment, not from the learner's browser, so allowing only the learner's home or office IP might not allow the notebook's requests. For private networking, Fabric managed private endpoints can be used with supported sources, but the endpoint and approval workflow are additional setup beyond this tutorial. Azure AI Search private endpoints require Basic or higher; they aren't available on the Free tier.

References: <a href="https://learn.microsoft.com/en-us/azure/search/search-security-api-keys#types-of-keys" target="_blank" rel="noopener noreferrer">Azure AI Search key types</a> · <a href="https://learn.microsoft.com/en-us/azure/search/service-configure-firewall" target="_blank" rel="noopener noreferrer">Configure Search firewall rules</a> · <a href="https://learn.microsoft.com/en-us/azure/search/service-create-private-endpoint" target="_blank" rel="noopener noreferrer">Create a Search private endpoint</a> · <a href="https://learn.microsoft.com/en-us/fabric/security/security-managed-private-endpoints-overview" target="_blank" rel="noopener noreferrer">Fabric managed private endpoints</a>.

## Search tier, model, and data considerations

- The tutorial suggests the Search Free tier for its small sample, and describes its limits as three indexes and 50 MB. Current Azure service limits state that only one Free Search service can be created per Azure subscription. In a shared training subscription, the free service may already be in use. A free Search tier does not make Spark or Fabric AI usage free.
- The example uses `text-embedding-ada-002` and defines the index vector field with 1,536 dimensions. If you choose a different embedding model, verify its dimension and use the same compatible model for both document and query embeddings. When changing models, re-embed the documents and recreate or migrate the index as needed; matching dimensions alone do not make two embedding spaces compatible.
- The sample data comes from the CMU Question/Answer dataset. Review the dataset's included license and citation information if you reuse or redistribute it.

References: <a href="https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity" target="_blank" rel="noopener noreferrer">Azure AI Search limits and quotas</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/ai-services-overview#consumption-rate" target="_blank" rel="noopener noreferrer">Fabric AI services consumption rates</a>.

## Code caveats to review

These are observations about the tutorial's published example code. Test any changes in your own Fabric workspace and Search service.

1. **The data-load cell overwrites a table.** It writes the sample data using `mode("overwrite")`. Use an isolated training lakehouse and check for existing data before running it.
2. **The sample IDs are not durable business keys.** `monotonically_increasing_id()` is convenient for a demonstration but is not a stable identifier across changed input, partitioning, or reruns. Repeated indexing can leave stale documents or create a different set of IDs. For repeatable ingestion, derive document IDs from stable source identifiers and define how to update or delete old records.
3. **The upload UDF issues an HTTP request per row.** The example does not show explicit timeouts or retry/backoff handling. Spark transformations are lazy, so repeated actions or retries can cause the work to run again. For larger datasets, use controlled batching and inspect each document's result in the Search response. An HTTP 200 response alone doesn't prove every document in an indexing request succeeded.
4. **The `filter` argument is not applied.** The sample `vector_search` function accepts a `filter` parameter, but the shown call to `SearchClient.search` does not pass it. Add and test the filter explicitly before relying on it for scoping results.
5. **A semantic configuration does not itself run semantic ranking.** The index setup defines semantic settings, while the demonstrated retrieval call performs vector search. Treat vector retrieval and semantic reranking as distinct features.
6. **The Chat Completions example is not the only current option.** The tutorial's generation function calls `openai_client.chat.completions.create`. Microsoft recommends the Responses API for new text-generation applications, while documenting that Chat Completions remains supported. Modernize only after testing the installed runtime and client; the built-in Fabric client supports both. For Responses, the Fabric endpoint does not support `store=True` or `previous_response_id`.

References: <a href="https://learn.microsoft.com/en-us/azure/search/search-how-to-load-search-index" target="_blank" rel="noopener noreferrer">Load data into a Search index</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-python-sdk#responses-api" target="_blank" rel="noopener noreferrer">Responses API in Fabric</a> · <a href="https://learn.microsoft.com/en-us/azure/search/semantic-search-overview" target="_blank" rel="noopener noreferrer">Semantic ranking in Azure AI Search</a>.

## Suggested workshop sequence

1. Confirm Fabric capacity, administrator settings, region, notebook runtime, lakehouse, and environment.
2. Provision or identify an Azure AI Search service. Confirm the selected tier, API-key setting, available index quota, and network access from Fabric.
3. Store the Search admin key using the training environment's approved secret-handling method.
4. Test a small number of chunks first: create the index, generate embeddings, upload documents, and query the index.
5. Review upload errors and retrieved content before running the complete sample. Monitor Fabric capacity usage and Azure Search limits.
6. After the exercise, remove temporary keys and delete resources or indexes that are no longer needed, according to the organization's retention policy.

For the original agenda entry, see [Chapter 11: Retrieval-Augmented Generation](./11_Retrieval_Augmented_Generation_RAG.md).
