# Workflow Definition: Claude News Briefing

## Overview

| Field | Value |
|-------|-------|
| **Workflow Name** | Claude News Briefing |
| **Description** | Search the web for the latest news on Claude, Claude Code, and Claude Cowork, summarize findings as bullet points with links, and save to a markdown file |
| **Outcome** | A markdown file with a concise, linked summary of the latest Claude news |
| **Trigger** | On-demand |
| **Type** | Research & Reporting |
| **Business Objective** | Stay current on Claude product developments with minimal effort |
| **Current Owner(s)** | James Gray |

## Steps

### Step 1: Search for news
- **Action:** Query the web for news about Claude, Claude Code, and Claude Cowork from the last 3 days
- **Input:** Search queries (Claude, Claude Code, Claude Cowork) + 3-day time window
- **Output:** Raw search results with URLs and snippets

### Step 2: Summarize with links
- **Action:** Distill search results into bullet points with source URLs
- **Input:** Raw search results from Step 1
- **Output:** Formatted bullet-point summary with hyperlinks

### Step 3: Save to file
- **Action:** Write the formatted summary to a markdown file
- **Input:** Formatted summary from Step 2
- **Output:** Markdown file saved to disk

## Sequence

Step 1 → Step 2 → Step 3 (strictly sequential)

## Prerequisites

- Access to web search (WebSearch / WebFetch tools)
- File system write access for saving the output
