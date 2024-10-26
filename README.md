# RAG-Pipeline-1
Created the first RAG pipeline

# Vertex AI Project

## Steps Followed :

1. **Create a new Google account.**
2. **Credits:** Received $300 in credits.
3. **Enable Vertex AI APIs.**
4. **Create a bucket in Google Cloud Storage (GCS).**
5. **Use Vertex AI Workbench:** 
   - Alternatively, you can use a DataProc cluster with Jupyter Lab as an installed application.
   - Create a Jupyter Notebook using a machine with specific configurations: 
     [Vertex AI Workbench](https://console.cloud.google.com/vertex-ai/workbench/managed?authuser=6&walkthrough_id=vertex_index&project=robust-habitat-439810-p4)

   > **Note:** It takes about 7-8 minutes to bring the Jupyter Notebook up.

## Notebooks Created

### 1. `embeddings_gen_and_vector_index_deployment.ipynb`

- This notebook generates embeddings for the statements in the uploaded PDFs.
- The embeddings file is uploaded to GCS at the specified file path.
- A vector search index is created using the URI of the embeddings file created in the previous step.
- A Matching Index Endpoint is created and deployed.

> **Important:** Make sure to pass the following parameters in the `deploy_index` function, or the deployment will not succeed:
   - `machine_type=machine_type`
   - `min_replica_count=min_replica_count`
   - `max_replica_count=max_replica_count`

### 2. `perform_semantic_search_and_get_output.ipynb`

- Initialize the vector search index.
- Generate embeddings for user input.
- Find nearest neighbors for the user input embeddings from the Matching Index Endpoint.
- For example, if you get the IDs of 10 nearest neighbors:
  - Look up these 10 UUIDs in the `sentences.json` file to retrieve the corresponding sentences for context creation.
- The retrieved 10 sentences are now referred to as the **context**.
- Create a prompt that injects the above-created context and invoke the model to get a response.

## Reference Tutorials Followed

- [Tutorial 1: Janakiram MSV](https://www.youtube.com/watch?v=wGbZSErgEvg&ab_channel=JanakiramMSV)
- [Tutorial 2: Google Cloud](https://www.youtube.com/watch?v=YlAWtEAJl9g&ab_channel=GoogleCloud)
- [Tutorial 3: Google for Developers](https://www.youtube.com/watch?v=LF7I6raAIL4&ab_channel=GoogleforDevelopers)
