# Movie Recommendation System using RAG


This repository contains a Real-time Recommendation and Generation (RAG) application that leverages MongoDB, Pinecone, SentenceTransformer, and Google Generative AI to provide movie recommendations based on user queries.
## Table of Contents

- [Introduction](#introduction)
- [Architecture](#architecture)
- [Components](#components)
- [Setup and Installation](#setup-and-installation)
- [Applications](#applications)
- [Possible Queries](#possible-queries)
## Introduction
This application monitors a MongoDB collection for movie data changes, generates embeddings for movie plots using SentenceTransformer, stores these embeddings in Pinecone, and provides real-time recommendations based on user queries. The application also uses Google Generative AI via LangChain to generate responses based on the most relevant movie plots.

## Architecture:
![image](https://github.com/lasyaMundrathi/RAG-Retrieval-Augmented-Generation-/assets/98383338/3fcd35f9-db3a-4ef2-a676-c94fd13a9d5d)

### Components:
#### 1. MongoDB Database (moviedb and moviecollection):
   
  - Stores movie documents with fields like title, fullplot, etc.
  - Change streams monitor the collection for changes (insert, update, delete).

#### 2. Change Stream Cursor:

  - Listens to changes in MongoDB.
 - On insert or update, generates embeddings for the movie plot using SentenceTransformer.
  - On delete, removes the corresponding vector from Pinecone.
#### 3. SentenceTransformer (thenlper/gte-large):

  - Encodes movie plots into vector embeddings.
  - Used during both change stream processing and query processing.
     
#### 4. Pinecone Vector Database:

  - Stores vector embeddings of movie plots.
  - Allows for querying similar movie plots based on user input.
     
#### 5. Query Processing:

  - User query is encoded into an embedding.
  - Pinecone is queried to find the most similar movie plots.
  - Relevant movie data is fetched from MongoDB using the IDs returned by Pinecone.
  
#### 6. LangChain and Google Generative AI (gemini-pro):

  - Processes the combined information from similar movies.
  - Generates a response based on the movie plots to answer user queries.
## Setup and Installation
### Prerequisites
1. Python 3.8+
2. MongoDB Atlas Account
3. Pinecone Account
4. Google Cloud Account for Generative AI
## Possible Queries

The application can handle a wide range of queries related to movies. Some example queries include:

### Recommendation Queries

- "What is the best horror movie to watch and why?"
- "Can you suggest a good comedy movie?"
- "Which thriller movies should I watch?"

### Plot-related Queries

- "Tell me the plot of an action movie."
- "What is the storyline of a romantic movie?"
- "Describe a science fiction movie plot."

### Comparative Queries

- "Compare the plots of two drama movies."
- "How does the plot of a mystery movie differ from a thriller?"

### Thematic Queries

- "What movies have a theme of friendship?"
- "Can you recommend movies with a strong female lead?"
- "Suggest movies that are based on true stories."

## Applications

This code can be used in various applications, including but not limited to:

- **Movie Recommendation Systems**: Enhance existing recommendation systems by providing plot-based suggestions and detailed responses to user queries.
- **Chatbots**: Integrate with chatbots to offer real-time movie recommendations and plot descriptions based on user inputs.
- **Content Analysis**: Analyze movie content and themes for research or entertainment purposes.
- **Interactive Entertainment**: Develop interactive applications where users can explore movie recommendations and plots through natural language queries.
     
     
