+++
title = "Getting Started With Claude Code"
description = "Practical techniques to get the most out of Claude Code as an agentic coding assistant."
draft = false
date = "2025-02-02"
author = "Camilo Macías"
tags = ["ai", "claude", "agentic-ai", "developer-tools"]
categories = ["AI Engineering"]
+++

Claude Code is an agentic coding assistant that runs directly in your terminal. Unlike chat-based interfaces, it operates as a CLI tool that can read your files, run commands, and edit code autonomously. This post covers the techniques I've found most effective after integrating it into my daily workflow.

## Why a Terminal-Based Agent Matters

Most AI coding assistants operate through a chat window or an IDE sidebar. Claude Code takes a different approach: it runs as a subprocess in your terminal with direct access to your project files, git history, and shell environment.

This means it can:

- Read and edit files across your entire codebase
- Run tests and check their output
- Execute git commands
- Chain multiple operations together autonomously

For AI engineers working on multi-file projects — agentic systems, RAG pipelines, deployment configs — this is a significant advantage over copy-pasting code into a chat window.

## Technique 1: Give Context, Not Just Instructions

The most common mistake is treating Claude Code like an autocomplete tool. Instead of:

```text
"Fix the bug in my RAG pipeline"
```

Provide structured context:

```text
"The retrieval step in src/rag/retriever.py is returning empty results
when the query contains special characters. The vector store is
ChromaDB. Check the query preprocessing in the embed_query function."
```

The more precise your description of the problem, the fewer iterations the agent needs.

## Technique 2: Use Plan Mode for Architectural Changes

When working on tasks that touch multiple files — like adding a new agent to a LangGraph workflow — start with plan mode. This tells Claude Code to analyze the codebase and propose an approach before writing any code.

This is particularly useful when:

- Adding new nodes or edges to an existing agent graph
- Refactoring shared utilities across modules
- Modifying API contracts that affect multiple services

Reviewing a plan before execution prevents wasted effort and keeps the architecture coherent.

## Technique 3: Let the Agent Iterate on Tests

One of Claude Code's strengths is its ability to run commands and react to their output. A productive pattern:

1. Write or describe the feature you need
2. Point Claude Code at your test suite
3. Let it run tests, read failures, and fix issues in a loop

```bash
# Example: asking Claude Code to fix failing tests
claude "Run pytest tests/test_retriever.py and fix any failures"
```

This loop — run, read, fix — is where agentic coding assistants outperform chat-based ones.

## Technique 4: Scope Your Requests

Claude Code works best with well-scoped requests. Instead of asking it to "build a RAG system," break the work into steps:

1. "Set up the document loader for PDF ingestion"
2. "Implement the chunking strategy with overlap"
3. "Add the vector store integration with ChromaDB"
4. "Write the retrieval chain with reranking"

Each step gives the agent a clear objective and makes it easier to review the output.

## When Not to Use It

Agentic coding tools are not a replacement for understanding your own system. I avoid using Claude Code for:

- **Security-critical code** without careful review
- **Architectural decisions** that require deep domain context
- **Performance-sensitive loops** where you need to reason about memory and CPU at a low level

The tool accelerates execution, not judgment.

## Final Thoughts

Claude Code fits naturally into an AI engineer's workflow because it operates at the same level we do — in the terminal, across files, with access to the full project context. The key is learning to communicate with it effectively: provide context, scope your requests, and let it iterate.
