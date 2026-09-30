# Project 5: Research Agent

**Goal:** A multi-step agent that takes a topic, gathers sources, and writes a cited brief.

## Architecture (suggested)
```
Planner -> Searcher -> Reader -> Writer -> Reviewer
```
- **Planner**: breaks the topic into questions
- **Searcher**: uses a search tool or API you provide
- **Reader**: extracts key facts with source URLs
- **Writer**: drafts the brief using only extracted facts
- **Reviewer**: checks claims against sources and flags unsupported statements

## Requirements
- Every claim in the output links to a source
- Loop limits (max steps, max tokens) to control cost
- Logging of each step
- A small eval set: 5 topics with expected key points
- Web UI or CLI

## Milestones
1. Single-agent version that works end to end
2. Split into roles
3. Add the reviewer and measure hallucination rate on your eval set
4. Add cost and latency logging
5. Deploy or document how to run it

## Risks to handle
Prompt injection from web pages, outdated sources, and overconfident summaries.
