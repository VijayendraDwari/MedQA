# MedQA
 Medical question-answering (QA) system
 
## Overview
In this project, I have fine-tuned a language model on the MedPubQA dataset to build a medical question-answering (QA) system. The primary goal was to enable the model to provide accurate, detailed, and evidence-based answers to medical questions. The process involved several key steps, from data preparation to model fine-tuning and evaluation.

## **Core Tasks**

1. **Model Fine-Tuning**  
   We are finetuning and evaluating 
   - Llama3.1-8B
     
   for Medical QA system.The following methodology and frameworks were used


2. **RAG Implementation**  
This project demonstrates the implementation of a Retrieval-Augmented Generation (RAG) system using a LoRA-tuned Llama model and the PubMedQA dataset to answer medical questions concisely and accurately. The workflow combines a fine-tuned generative model with a retrieval pipeline to enhance the factual accuracy and relevance of responses.

**Key Components**
LoRA-Tuned Llama Model

We leverage a lightweight LoRA (Low-Rank Adaptation) fine-tuning method to efficiently adapt the Llama model for medical question answering tasks. This approach reduces memory overhead and allows inference on high-capacity models using 4-bit quantization.

**PubMedQA Dataset**

The PubMedQA dataset provides a rich source of medical question-answer pairs derived from PubMed abstracts. We extract and chunk the dataset's LONG_ANSWER fields to build a comprehensive knowledge base.

**FAISS Vector Store for Retrieval**

We use the FAISS library to create a vector store from the chunked documents. FAISS enables fast and efficient similarity-based retrieval of relevant context for a given query.

**RAG Pipeline**

The RAG system integrates:

- A retriever to fetch the top-k relevant chunks from the vector store.
- A custom prompt to guide the Llama model in generating context-aware and concise answers.
- A LangChain RetrievalQA chain to connect retrieval and generation seamlessly.
- Custom LLM with Stop Sequences and Sampling Controls

We implement a custom LangChain-compatible LoRAMedicalLLM class that allows:

- Control over sampling parameters like temperature, top-p, and top-k to reduce repetitive text.
- Stop sequences to truncate outputs when certain phrases (e.g., "Context:", "Question:") are encountered, minimizing prompt echoing. 

3. **Web App Integration**  
  Web App Integration: Medical QA System with Gradio
This project implements a web app for a Medical Question Answering (QA) System using Gradio. The app integrates a LoRA-tuned Llama model and a Retrieval-Augmented Generation (RAG) pipeline to deliver accurate and contextually grounded answers.

Features of the Web App:
User Query Input:

The user can input any medical question via a simple text box.

**Model-Generated Answer:**

The system generates a concise answer to the query using the LoRA-tuned Llama model.
Answers are informed by relevant medical documents retrieved from the PubMedQA dataset.

References to Retrieved Documents:

The app displays the sources of information used to generate the answer.
Each source is a document chunk retrieved using a FAISS vector store and similarity-based search.
Workflow:
Query Input:

The user enters a question in the Gradio interface.
Document Retrieval:

Relevant document chunks are retrieved using FAISS and sentence-transformer embeddings.
Answer Generation:

The RAG pipeline feeds the retrieved context into the model, which generates a concise, context-aware answer.
Display Results:

The app shows both the generated answer and the referenced sources for transparency.
Advantages:
User-Friendly Interface:
The Gradio app provides a straightforward and interactive way to query the system.

Transparency:
References to the source documents increase user trust in the generated answers.

Scalability:
The app can be shared via a public Gradio link for broader access or deployed on platforms like Hugging Face Spaces.

This demo highlights how advanced AI models can be integrated into accessible web applications to provide reliable, evidence-based medical answers. 

4. **Future work and Improvements:**
This is a demo and for POC purpose we have used Llama3.1-8B , in my experience the most suitable model for handling domain specific queries of this nature is Llama70 B, using a 70B model should improve this model to a deployment ready state in LIVE environment.
