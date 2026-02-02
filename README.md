## Youtube_RAG
An AI-powered YouTube Content Synthesizer using RAG (Retrieval-Augmented Generation). Built with Streamlit, LangChain, and Gemini 2.0 to transform video transcripts into structured notes, important topics, and an interactive chatbot.
# VidSynth AI: YouTube Content Synthesizer
VidSynth AI is a sophisticated RAG-based application that allows users to "talk" to YouTube videos and extract high-quality summaries. By leveraging Gemini 2.0 Flash and Vector Databases (ChromaDB), it provides an intelligent way to consume video content efficiently.

# Key Features
1. Automated Note-Taking: Generates well-structured, bulleted notes from any video transcript.

2. Topic Extraction: Identifies and summarizes the 5 most important technical points from the video.

3. Interactive Chatbot: A RAG-powered interface to ask specific questions about the video content.

4. Multi-lingual Support: Automatically translates non-English transcripts for analysis.

# Tech Stack
1. Framework: Streamlit

2. Orchestration: LangChain

3. AI Models: Gemini 2.0 Flash (Chat) & Text-Embedding-004 (Embeddings)

4. Vector Store: ChromaDB

# Technical Challenges & Disclaimers
This project was developed as a technical challenge to implement RAG (Retrieval-Augmented Generation) on a cloud environment. Due to the nature of free-tier cloud hosting and external APIs, users should be aware of the following:

__1. YouTube Request Blocking (Proxy Integration)__

YouTube frequently blocks automated requests (transcription fetching) from cloud providers like Streamlit.

The Solution: I have integrated a Webshare Proxy Server to route requests through a rotating IP.

The Limitation: Since this uses a free-tier proxy, YouTube may still occasionally block the connection. If you see a "Fetching Transcript Error," it is likely due to the proxy being temporarily throttled by YouTube's security layers.

__2. Google Gemini API Quota (429 Errors)__

The "Chat with Video" feature requires significant API credits to create embeddings for the vector database.

The Limitation: Users may encounter a 429 RESOURCE_EXHAUSTED error. This is a provider-side quota limit of the Google Gemini Free Tier and not a bug in the source code.

Recommendation: The "Notes For You" feature uses fewer credits and is more likely to work consistently. For chatting, please use shorter videos (under 5 minutes).

# Performance Optimizations
To make this work on Streamlit Cloud, I implemented the following:

1. pysqlite3-binary: Used to override the system SQLite version, as Streamlit's default environment is often incompatible with the latest ChromaDB requirements.

2. Proxy Authentication: Configured youtube_transcript_api to use authenticated proxy headers to bypass IP-based blocks.
