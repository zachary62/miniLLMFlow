---
layout: default
title: "Home"
nav_order: 1
---

# Mini LLM Flow

A 100-line minimalist LLM framework for agents, task decomposition, RAG, etc.

<div align="center">
  <img src="/assets/minillmflow.jpg" width="400"/>
</div>

## Core Abstraction

We model the LLM workflow as a **Nested Flow**:
- Each **Node** handles a simple LLM task.
- Nodes are chained together to form a **Flow** for more complex tasks.
- One Node can be chained to multiple Nodes based on **Actions**.
- A Flow can be treated as a Node for **Nested Flows**.
- Both Nodes and Flows can be **Batched** for data-intensive tasks.
- Nodes and Flows can be **Async**.

- [Node](./node.md)
- [Flow](./flow.md)
- [Communication](./communication.md)
- [Batch](./batch.md)
- [Async](./async.md)

## Paradigm Implementation

- Task Decomposition
- Agent
- Map Reduce
- RAG
- Structured Output

## Example Use Cases

TODO