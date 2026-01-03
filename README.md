# LangGraph – Complete Notes (Detailed, Practical, Production-Ready)

## What is LangGraph?

LangGraph is a framework built on top of LangChain that enables the creation of **stateful, graph-based workflows** for Large Language Model (LLM) applications. It allows developers to model complex AI systems using **nodes, edges, and shared state**, making it possible to build agents that can reason, loop, retry, branch, and collaborate.

LangGraph is designed for **agentic AI systems** where linear chains are not sufficient.

---

## Why LangGraph Exists

Traditional LLM applications often follow a linear flow:
Prompt → LLM → Output

This approach fails when applications require:
- Decision-making
- Validation and retries
- Multiple agents
- Long-running workflows
- Stateful reasoning

LangGraph solves this by introducing **explicit control flow and state management**.

---

## LangChain vs LangGraph

### LangChain
- Builds LLM-powered capabilities
- Provides prompts, chains, tools, retrievers, memory
- Best for simple and semi-complex pipelines

### LangGraph
- Controls execution logic
- Handles loops, conditions, retries
- Manages shared state across steps
- Enables multi-agent systems

**LangChain defines what can be done.  
LangGraph defines how it is done.**

---

## Core Concepts

## State

State is a shared data structure that flows through the entire graph.  
It is the memory of the system.

- Defined using `TypedDict`
- Passed to every node
- Updated incrementally
- Enables persistence and traceability

Example:
```python
from typing import TypedDict, List

class AgentState(TypedDict):
    user_input: str
    messages: List[str]
    result: str
    approved: bool
