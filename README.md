

# Build a RAG API with FastAPI


---

---


In this project, I will demonstrate on how to build a RAG API from scratch. I are doing this project to learn how ollama works ,how to build an API and run it locally.


### Key tools and concepts

The key tools I used include Ollama models, ChromaDB, Fast API. Key concepts I learnt include 
Perform RAG (Retrieval-Augmented Generation) both manually and with code.
Create a personal knowledge base using ChromaDB and vector embeddings.
Build a REST API with FastAPI that implements a full RAG pipeline.
 Use nomic-embed-text for semantic search and qwen2.5:0.5b for AI response generation.
 Extend the API into a multi-user AI directory with dynamic document ingestion.

### Challenges and wins

This project took me approximately 2 days because i was taking a lot of gaps inbetween to finish it , but honestly it wouldnt have taken me more than 3 hours to complete this if i was fully dedicated to this project

---

## Performing RAG Manually

In this step, I'm going to be seeing RAG in action by dowloading ollama and then set up a Virtual Environment for the python project that we are going to do. RAG stands for Retrieval Augmented Generation 



### Understanding the three parts of RAG

I performed RAG manually by doing three parts, The three parts are 
Retrieval - You found the relevant text (some personal info).
Augmentation - You added that text to the prompt.
Generation - The AI used that context to generate an accurate answer.

### Comparing the two AI models

The key difference between the two is that Nomic-embedded text is used purely in searching purpose, uses vector-based searching technique, while qwen2.5:0.5b is a chat model that generates responses 

---

## Building a Personal Knowledge Base

In this step, I'm going to write a personal profile document, in Python that will be converted to embeddings by Ollama's nodic embedding model, then store it in Chroma DB. 


### Creating the profile document

I included information about myself in the profile.txt file. This will allow the AI to refer to the text file and answer me to questions based on the file  

### How semantic search finds relevant chunks

When I ask a question, ChromaDB has the vector value stored , the asked question also turns into a vector and then ChromaDB trys to find the chunks whose vectors are closest , this is the implementation of semantic search , finds the content with the closest meaning.

---

## Creating the RAG API with FastAPI

In this step, I'm going to build an API that brings the full RAG pipeline together. When someone sends a question to your API, it will automatically retrieve context, augment the prompt, and generate a grounded answer. I will test the API with Swagger UI



### How the /ask endpoint works

When a question comes in, my endpoint these are the three steps of RAG that i performed manually in Step 1. When someone sends a question, it retrieves the 2 most relevant chunks from ChromaDB, augments the prompt by combining those chunks with the question, and generates a grounded answer using qwen2.5:0.5b. The response includes the context that was used so you can verify the AI's sources.

### Testing with Swagger UI

I tested my API by asking... The AI answered with telling what my name was, it displayed in a JSON format. The context used was the profile.txt file that i had written earlier.

---

## Extending to a Multi-User AI Directory

In this project extension, I'm adding multi-user support because almost all real world RAG systems have mutiple user support and this will enable me to learn more on dynamic document ingestion, metadata filtering in vector databases, and basic multi-tenancy patterns.  Multi-tenancy is where a single instance of a software application serves multiple user / tenant.   
Each tenant shares the same application and database but their seperate data remains safe and isolated. 


### Adding the POST /documents endpoint

In this project extension, I added a POST endpoint that accepts the data of the specific user in the request body of the specific user. Metadata filtering allows us to sift through the specific user's details and generate an answer according to the input they have given.  In detail , metadata filtering options that allow you to refine your searches beyond just semantic similarity. While embeddings help find documents based on meaning, metadata filtering lets you narrow down those results based on specific attributes or properties of your data.


### Verifying multi-user filtering

In this project extension, I tested multi-user queries by adding a post request to the main.py code. The filter works with the technique called meta data filtering 

---

## Wrapping Up

I did this project today to learn how to work with APIs and RAG Pipelines.

---

---
