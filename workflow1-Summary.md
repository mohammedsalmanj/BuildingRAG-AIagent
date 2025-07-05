Workflow 1: Analysis-RAG – Turning PDF into Searchable Brain
This is the indexing phase. Think of this like "training the AI assistant with Nike’s report."

1. Manual Trigger
Node Name: When clicking ‘Execute workflow’
Why: You want to run this only when you want to ingest a new PDF.

2. Google Drive - Download File
Purpose: Downloads the Nike report PDF from your Google Drive.

You gave it the file ID of the Nike report

Auth is handled via your connected Google Drive credentials

3. Recursive Character Text Splitter
Why: PDFs are too big to embed all at once.
What it does: Breaks the PDF into chunks (like pages or paragraphs).

Think of it like cutting a textbook into pages so the AI can understand each page.

4. Default Data Loader
Why: It converts the chunks into a format n8n + LangChain understands
Think: It’s a translator between split pages and AI embeddings.

5. OpenAI Embeddings
What it does: Converts each chunk of text into a vector (numbers AI can search).

Like turning a sentence into GPS coordinates in idea-space.

6. Pinecone Vector Store
Purpose: Stores the embeddings in a fast searchable database.

Index name: reportsales

Namespace: Nike

Now your Nike report is in a vector database, ready to be searched with questions.