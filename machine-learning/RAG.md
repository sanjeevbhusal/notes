
Creating a RAG application has few major steps involved. 
1) Indexing: In this step, we take embeddings of a document (or any other data source) and store it in some sort of vector database. 
2) Retrieval: In this step, we retrieve those stored documents from the database that match the user's query. 
3) Generation: In this step, we create a prompt using the retrieved documents and user query and send it to a LLM. LLM then generates a response. 


**Indexing**
A Document can have tens of thousands of words. We cannot send all of the document to the LLM due to:
- models' context window: models have a fixed context window. We cannot exceed it.
- unnecessary information: If we supply unnecessary information to a model, a model might get confused and produce inaccurate result. 

So, it is important that we first break the document into smaller chunks and only send the relevant chunks to the model. A common strategy is to split the document into multiple small chunks (eg: 1000 characters per chunk) and only send 3 chunks to the model. These 3 chunks should be the one that has the highest possibility of containing answer to the asked question. 

In order to find the best 3 chunks, we can use similarity search. We take the embedding of the question and compare it with the embeddings generated from the documents. We then take the best 3 matches. 

You can use this strategy to recommend similar articles in a blog post as well. 

In summary indexing contains 3 main steps:
- Loading: Load the document from a data source
- Splitting: Split the document into smaller chunks. 
- Storing: Take the embeddings of the documents and store it in some sort of vector storage.

![[Pasted image 20250604144657.png]]

**Retrieving**
When the user sends a search query, retrieve relevant documents (document split). For this, generate query embedding and perform a similarity search. 

**Generate**
Craft a prompt combining users query, relevant documents and additional instructions and send the prompt to a LLM. 

![[Pasted image 20250604145429.png]]