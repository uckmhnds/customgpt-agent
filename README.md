<p align="center">
  <img src="assets/logo.svg" alt="CustomGPT.ai" width="320">
</p>

<h1 align="center">CustomGPT Agent</h1>

<p align="center">
  <strong>An enterprise-grade AI agent powered by Claude and CustomGPT.ai</strong>
</p>

<p align="center">
  <a href="https://customgpt.ai"><img src="https://img.shields.io/badge/CustomGPT.ai-Platform-blue?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNMTIgMkM2LjQ4IDIgMiA2LjQ4IDIgMTJzNC40OCAxMCAxMCAxMCAxMC00LjQ4IDEwLTEwUzE3LjUyIDIgMTIgMnoiIGZpbGw9IndoaXRlIi8+PC9zdmc+" alt="CustomGPT.ai"></a>
  <a href="https://docs.anthropic.com/en/docs/agents-and-tools/claude-code/overview"><img src="https://img.shields.io/badge/Claude_Agent_SDK-Anthropic-blueviolet?style=for-the-badge" alt="Claude Agent SDK"></a>
  <a href="https://e2b.dev"><img src="https://img.shields.io/badge/Sandbox-E2B-orange?style=for-the-badge" alt="E2B Sandbox"></a>
  <a href="https://huggingface.co/spaces/gaia-benchmark/leaderboard"><img src="https://img.shields.io/badge/GAIA_Benchmark-HuggingFace-yellow?style=for-the-badge&logo=huggingface" alt="GAIA Benchmark"></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Orchestrator-Claude_Opus_4-blueviolet?style=flat-square" alt="Claude Opus 4">
  <img src="https://img.shields.io/badge/Specialists-Claude_Sonnet_4-blue?style=flat-square" alt="Claude Sonnet 4">
</p>

---

## Overview

**CustomGPT Agent** is a multi-agent AI system that combines [CustomGPT.ai](https://customgpt.ai)'s enterprise RAG platform with Claude's reasoning capabilities and secure sandboxed code execution. It is designed to solve complex, real-world tasks that require multi-step reasoning, web research, file analysis, and computation.

The agent was evaluated on the [GAIA Benchmark](https://huggingface.co/spaces/gaia-benchmark/leaderboard) (General AI Assistants), a challenging benchmark that tests AI systems on tasks requiring real-world tool use, multi-step reasoning, and web browsing — tasks that go far beyond simple question answering.

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                    ORCHESTRATOR (Claude Opus)                    │
│              Claude Opus 4 + Agent SDK                          │
│         Multi-agent coordination & reasoning                    │
└────────────┬──────────┬──────────┬──────────┬──────────────────┘
             │          │          │          │
     ┌───────▼──┐ ┌─────▼────┐ ┌──▼───────┐ ┌▼──────────┐
     │  LOOKUP  │ │COMPUTATION│ │  FILE    │ │  CRITIC   │
     │ (Sonnet) │ │ (Sonnet)  │ │(Sonnet)  │ │ (Sonnet)  │
     └───────┬──┘ └─────┬────┘ └──┬───────┘ └┬──────────┘
             │          │          │          │
     ┌───────▼──────────▼──────────▼──────────▼──────────┐
     │                  TOOL LAYER                        │
     ├────────────┬─────────────┬──────────────┐         │
     │ Web Search │ E2B Sandbox │ CustomGPT.ai │         │
     │ & Browse   │ (Python,    │ Knowledge    │         │
     │            │  Shell, FS) │ Base API     │         │
     └────────────┴─────────────┴──────────────┘         │
     └────────────────────────────────────────────────────┘
```

### Components

| Component | Technology | Role |
|-----------|-----------|------|
| **Orchestrator** | Claude Opus 4 via Claude Agent SDK | Task decomposition, routing, and final answer synthesis |
| **LOOKUP Specialist** | Claude Sonnet 4 + web search & browser | Web research, fact retrieval, page navigation |
| **COMPUTATION Specialist** | Claude Sonnet 4 + E2B sandbox | Python execution, mathematical calculations, data processing |
| **FILE ANALYSIS Specialist** | Claude Sonnet 4 + E2B sandbox | Document parsing (PDF, Excel, images), file manipulation |
| **CRITIC Verifier** | Claude Sonnet 4 (verification loop) | Answer validation, cross-checking, quality assurance |
| **E2B Sandbox** | Secure microVM | Isolated code execution, browser automation (Playwright) |

---

## Key Features

1. **Multi-Agent Architecture** — Specialized subagents (LOOKUP, COMPUTATION, FILE ANALYSIS, CRITIC) collaborate under a central orchestrator for divide-and-conquer problem solving

2. **Secure Sandboxed Execution** — All code runs in isolated E2B microVMs with Playwright browser automation, filesystem access, and Python/shell execution

3. **Enterprise RAG Integration** — CustomGPT.ai's 40+ API endpoints provide citation-backed knowledge retrieval from proprietary data sources

4. **Self-Verification Loop** — Built-in CRITIC agent validates answers before submission, catching errors and improving reliability

5. **Resilient Execution** — Automatic retry logic, sandbox recovery, and graceful degradation for long-running complex tasks

---

## How It Works

```
User Question
     │
     ▼
┌─────────────┐
│ Orchestrator │──── Analyzes question, determines strategy
└──────┬──────┘
       │
       ├──► LOOKUP: Search the web, browse pages, extract facts
       ├──► COMPUTATION: Write & execute Python code for calculations
       ├──► FILE ANALYSIS: Parse PDFs, spreadsheets, images
       └──► CustomGPT KB: Query enterprise knowledge base
              │
              ▼
       ┌────────────┐
       │   CRITIC    │──── Verify answer, cross-check sources
       └──────┬─────┘
              │
              ▼
        Final Answer (with reasoning trace)
```

---

## About CustomGPT.ai

<p align="center">
  <a href="https://customgpt.ai">
    <img src="assets/logo.svg" alt="CustomGPT.ai" width="240">
  </a>
</p>

[**CustomGPT.ai**](https://customgpt.ai) is an enterprise AI platform that enables businesses to build custom AI agents powered by their own data — with no hallucinations and full source citations.

**Key Capabilities:**
- **1,400+ data formats** — Ingest websites, documents, helpdesks, videos, and more
- **Anti-hallucination technology** — Third-party verified #1 for accuracy
- **92 languages** supported
- **40+ REST API endpoints** — Full programmatic access for agent integration
- **SOC-2 Type II & GDPR** compliant
- **Enterprise-grade security** — Data never used for LLM training

In this agent, CustomGPT.ai serves as the **knowledge base layer**, providing semantic search, ranked context retrieval, and citation-backed answers from proprietary enterprise data.

> *"Business AI for trusted answers — no hallucinations, no guessing."*

---

## Author

**[Dennis Yavuz](https://github.com/uckmhnds)**

---

## Acknowledgements

- [**Anthropic**](https://anthropic.com) — Claude Opus 4, Claude Sonnet 4, and Claude Agent SDK
- [**CustomGPT.ai**](https://customgpt.ai) — Enterprise RAG platform and knowledge base API
- [**E2B**](https://e2b.dev) — Secure sandboxed code execution
- [**GAIA Benchmark**](https://huggingface.co/papers/2311.12983) — General AI Assistants evaluation framework

---

## Citation

```bibtex
@misc{customgpt-agent-2026,
  title={CustomGPT Agent: Enterprise AI Agent with RAG-Augmented Multi-Agent Architecture},
  author={Dennis Yavuz},
  year={2026},
  url={https://github.com/uckmhnds/customgpt-agent}
}
```

---

<p align="center">
  <sub>Built with Claude Agent SDK and CustomGPT.ai</sub>
</p>
