# RAG-Pipeline-1
Created the first RAG pipeline


RAG Pipeline - GCP

Steps Followed => 

Create a new Google account.

300$ credits received.

Enable Vertex AI APIs

Create a bucket in GCS.

Use Vertex AI Workbench [Instead can use DataProc cluster with Jupyter Lab as an installed application]
Create a jupyter notebook(use the type of machine with specific configurations) :  https://console.cloud.google.com/vertex-ai/workbench/managed?authuser=6&walkthrough_id=vertex_index&project=robust-habitat-439810-p4

Takes 7-8 minutes to bring the jupyter notebook up.

Created 2 notebooks:

embeddings_gen_and_vector_index_deployment.ipynb
In this notebook, the embeddings are created for the uploaded PDF’s statements and the embeddings file is uploaded to the GCS at the specified file path.
A vector search index is created with the uri of the embeddings file created in the earlier step.
A Matching index endpoint is created and deployed as well. 
Make sure to pass the below parameters in deploy_index function, otherwise deployment will not succeed.

 machine_type=machine_type,
                        min_replica_count=min_replica_count,
 max_replica_count=max_replica_count


perform_semantic_search_and_get_output.ipynb
Initialise the vector sector search index
Generate the embeddings for the user input.
Find nearest neighbours for the user input embeddings from the matching index endpoint.
Say, we got the IDs of 10 nearest neighbours.
Now, look up for these 10 UUIDs in the sentences.json file and get the 10 sentences for context creation
The paragraph 10 sentences is now referred to as the context.
Now we need to create a prompt, inject the above created context and invoke the model to get the response.


Reference tutorials followed : 

https://www.youtube.com/watch?v=wGbZSErgEvg&ab_channel=JanakiramMSV
https://www.youtube.com/watch?v=YlAWtEAJl9g&ab_channel=GoogleCloud
https://www.youtube.com/watch?v=LF7I6raAIL4&ab_channel=GoogleforDevelopers

