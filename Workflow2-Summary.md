Workflow 2: My Workflow – Chat with the Brain
This is where you set up an AI Agent that can chat with users, ask Pinecone for answers, and respond clearly.

1. Chat Trigger
Why: This node waits for a user to send a message to the bot.

“Hey bot, how did Nike perform in APAC?”
2. AI Agent
What: This is the brain that coordinates tools, memory, models.
Think of it like Jarvis (Iron Man's assistant) deciding what to do with the question.
3. OpenAI Chat Model
Why: Gives the AI its language powers.
Model: gpt-4o

It helps the agent speak fluently and think clearly.

4. Simple Memory
Why: Keeps last few interactions.
Setting: 5 context windows
So if a user says “what about Europe?”, the bot remembers previous question context.
Vector Store Tool
This is the most important tool.

Named: "database"
Description: "Use this tool to search content from the vector store"
Think of it like Jarvis having access to Nike's entire report in memory.
It connects:

To Pinecone Vector Store (already populated by Workflow 1)

Uses OpenAI Embeddings to convert questions to vector format
Uses OpenAI Chat Model to convert answers into human language
6. Pinecone Vector Store
Same one from Workflow 1 (reused):
Index: reportsales
Namespace: Nike
This is where the knowledge lives.


Final Result 
Workflow:
User asks: "Top regions by revenue growth?"
ChatTrigger passes it to AI Agent

Agent thinks: “Hmm... this needs the database tool”

It uses the Vector Store Tool
Converts question to vector (embedding)

Searches Pinecone
Gets best matching chunks from Nike PDF

Sends those chunks to OpenAI Chat Model1

Final answer is crafted and returned to user
