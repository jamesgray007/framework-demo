# AI Building Block Map: Claude News Briefing

## Scenario Summary

| Field | Value |
|-------|-------|
| **Workflow Name** | Claude News Briefing |
| **Description** | Search the web for the latest news on Claude, Claude Code, and Claude Cowork, summarize findings as bullet points with links, and save to a markdown file |
| **Outcome** | A markdown file with a concise, linked summary of the latest Claude news |
| **Trigger** | On-demand |
| **Type** | Research & Reporting |
| **Business Objective** | Stay current on Claude product developments with minimal effort |
| **Current Owner(s)** | James Gray |

## Step-by-Step Decomposition Table

| # | Step | Action | Type | Decision Points | Failure Mode | Data In | Data Out | Context Needed | AI Building Block(s) |
|---|------|--------|------|----------------|-------------|---------|----------|----------------|---------------------|
| 1 | Search for news | Query the web for Claude, Claude Code, and Cowork news from the last 3 days | AI-Autonomous | Which search queries to run; how many results to collect | No results found; irrelevant results returned | Search queries (Claude, Claude Code, Claude Cowork) | Raw search results with URLs and snippets | Current date for 3-day window | Prompt, MCP |
| 2 | Summarize with links | Distill search results into bullet points with source URLs | AI-Semi-Autonomous | What's newsworthy; how to group/order items; level of detail | Key news missed; broken or wrong links | Raw search results | Formatted bullet-point summary with hyperlinks | Search results from Step 1 | Prompt, Context |
| 3 | Save to file | Write the formatted summary to a markdown file | AI-Deterministic | File name and location | Write failure; overwrite existing file | Formatted summary | Markdown file on disk | Output directory path | Prompt |

## Autonomy Spectrum Summary

- **Human steps:** None (fully automated once triggered)
- **Deterministic AI steps:** Step 3 — Save to file
- **Semi-autonomous AI steps:** Step 2 — Summarize with links (optional review gate: user can review summary before saving)
- **Fully autonomous AI steps:** Step 1 — Search for news

## Step Sequence and Dependencies

- **Sequential:** Step 1 → Step 2 → Step 3
- **Parallel steps:** None
- **Critical path:** Step 1 (search) — if no results are found, the workflow has nothing to summarize
- **Dependency map:**
  - Step 2 depends on Step 1 (needs search results)
  - Step 3 depends on Step 2 (needs formatted summary)

## Prerequisites

- Access to web search (WebSearch / WebFetch tools or MCP)
- File system write access for saving the output markdown file
- Output directory exists (e.g., `outputs/`)

## Context Inventory

| Artifact | Type | Description | Used By Steps | Status | Format | Key Contents |
|----------|------|-------------|---------------|--------|--------|--------------|
| Search queries | Input | Three topic keywords: Claude, Claude Code, Claude Cowork | Step 1 | Required | Text | Topic names and 3-day time window |
| Raw search results | Intermediate | URLs, titles, and snippets from web search | Steps 1, 2 | Generated at runtime | Structured text | Links, headlines, publication dates |
| Formatted summary | Output | Bullet-point summary with hyperlinks | Steps 2, 3 | Generated at runtime | Markdown | News bullets grouped by topic with source links |

## Tools and Connectors Required

| Tool | Purpose | Used By Steps |
|------|---------|---------------|
| WebSearch | Run search queries for Claude news | Step 1 |
| WebFetch | Fetch and extract content from news articles | Step 1 |
| File System (Write) | Save the final markdown summary to disk | Step 3 |
