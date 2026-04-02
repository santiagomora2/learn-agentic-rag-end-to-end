# Lesson 0: Foundations — Understanding RAG & Embeddings

## Learning Objectives

By the end of this lesson, you'll understand:
- What embeddings are (geometrically and conceptually)
- Why you can't just give Claude all your documents
- How vector databases work
- Why ChromaDB is good for learning

## What You'll Build

A working vector store with sample documents that you can query.

## Notebooks

1. **01_llm_basics.ipynb** — Meet the Claude API
   - Your first API call (with costs tracked)
   - Tokens: what they are, why they matter
   - Cost calculation (spoiler: very cheap)

2. **02_rag_theory.ipynb** — Why RAG Works
   - The RAG loop (query → retrieve → generate)
   - Why fine-tuning doesn't compare
   - Failure modes we'll solve later

3. **03_vector_stores.ipynb** — ChromaDB Hands-On
   - Build your first vector store
   - Query it
   - Understand what's happening under the hood

## Knowledge Check

Can you answer?
- "What does embedding mean?"
- "Why can't we just make the prompt longer?"
- "How do we choose which chunks to retrieve for a given query?"

If yes, move to Lesson 1!