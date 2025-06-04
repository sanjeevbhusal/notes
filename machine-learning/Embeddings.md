

Embeddings are numerical representation of a text. It is basically conversion of natural human language to numbers that is easier to understand for machines. When a sentence's embeddings is generated, the generated numbers also capture the semantic meaning of the sentence. This helps the LLM compare different texts to see how similar they are.

Step 1: Generate Embeddings from a text.
Eg: Text is "My name is Sanjeev Bhusal. ". The generated embeddings might look like [-12.3, 3.4, 5.6]
Step 2: Ask the llm a question. 
Eg: Question is "What is my name".  Generate embeddings of this question. The embeddings might looks like [-9, 2, 0.8]. 
Step 3: Compare the embeddings.
Eg: Pass both embeddings to a LLM and ask it to answer the question. The LLM will be able to understand the semantic meaning of both text and question and return a meaningful answer. This comparison is done using similarity metrics such as COSINE SIMILARITY, DOT PRODUCT etc. 

![[Pasted image 20250604135229.png]]


Embeddings is generated using Embeddings Model. These models are specifically designed to generate embeddings from text. You can find various open source models or providers like OpenAI also provide embeddings model. 

Embeddings model embed documents and query text differently. documents is the context i.e. the data upon which further searches will be made and query is the actual asked question. 

**Search algorithms**

You can think of each embedding as a set of coordinates. Eg: [10].  This coordinates represent the meaning of its corresponding text. text that are similar to each other will have similar or close to coordinates value. 

The comparison for how close 2 embeddings are with each other can be done via various algorithms. 

- **Cosine Similarity**: Measures the cosine of the angle between two vectors.
- **Euclidean Distance**: Measures the straight-line distance between two points.
- **Dot Product**: Measures the projection of one vector onto another.

you should choose the metric based upon the model used. For Eg: OpenAI suggests using Cosine Similarity when dealing with their models. 

Read more: https://python.langchain.com/docs/concepts/embedding_models/