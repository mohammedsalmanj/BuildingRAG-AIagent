### Workflow 1: Analysis-RAG
This is your indexing pipeline (for storing knowledge into Pinecone).


## Flow:
Manual Trigger: Starts workflow on button click

Google Drive (Download File): Downloads the Nike_Global_Sales_Narrative_Report.pdf

Recursive Character Text Splitter: Breaks PDF into chunks

Default Data Loader: Prepares data chunks

OpenAI Embeddings: Converts chunks into vector format

Pinecone Vector Store: Inserts embeddings into Pinecone under:

Index: reportsales

Namespace: Nike

Purpose: Turns your Nike PDF into searchable AI-readable chunks stored in Pinecone



### Workflow 2: My Workflow
This is your RAG agent (for querying the stored knowledge using chat).

## Flow:
Chat Trigger: Captures incoming user questions

AI Agent: Orchestrates the tools

OpenAI Chat Model: Provides natural language generation

Simple Memory: Tracks recent conversation turns (context)

Vector Store Tool: Registered as a “Tool” for the agent, described as:

"Use this tool to search content from the vector store"

OpenAI Embeddings + Pinecone Vector Store:

Enables the Vector Store Tool to:

Embed the user’s question

Search Pinecone’s reportsales index in Nike namespace

Return relevant chunks

OpenAI Chat Model1: (Inside the tool) generates answers based on retrieved chunks

Purpose: Let the user chat with the Nike PDF using real AI search.

## Summary of Relationship
## Component
### Workflow 1	Load PDF → Embed with OpenAI → Insert into Pinecone
### Workflow 2	Chat Agent → Retrieves from Pinecone → Answers via OpenAI




What difference it makes ?

Building “Nike Report AI Assistant”
Nike’s global leadership wants a way to ask questions directly to their sales reports, like:

“What region had the highest growth in Q2?”

“What’s the trend in Europe from 2021 to 2024?”

Rather than manually searching PDFs, they want to chat with the report. You’re the engineer making this magic happen using n8n + OpenAI + Pinecone.