# Baseline Workflow Prompt: Claude News Briefing

## Purpose

Search the web for the latest news on Claude, Claude Code, and Claude Cowork from the last 3 days, summarize the findings as bullet points with source links, and save the results to a markdown file.

**When to use:** Whenever you want a quick catch-up on recent Claude product news and developments.

**Outcome:** A markdown file with a concise, linked news summary ready to read.

---

## Instructions

Run the following steps in order:

### Step 1: Search for news (AI)

Search the web for news and announcements from the **last 3 days** on each of the following topics. Run a separate search for each:

1. **"Anthropic Claude" news** — product updates, announcements, releases
2. **"Claude Code" news** — features, updates, tutorials, announcements
3. **"Claude Cowork" news** — features, updates, announcements

For each search, collect:
- Article title
- Source URL
- Publication date (if available)
- A brief snippet or key point from the article

Aim for 5-10 relevant results across all three topics. Skip duplicate articles that appear in multiple searches.

### Step 2: Summarize with links (AI)

Organize and summarize the search results into a clean, scannable format:

1. Group findings by topic: **Claude**, **Claude Code**, **Claude Cowork**
2. For each item, write a **one-sentence summary** of the key news
3. Include the **source link** as a markdown hyperlink after each bullet
4. Order items within each group by publication date (most recent first)
5. If no results were found for a topic, note "No news found in the last 3 days" under that heading

### Step 3: Save to file (AI)

Write the formatted summary to a markdown file at `outputs/claude-news-briefing-YYYY-MM-DD.md`, using today's date in the filename.

The file should follow this structure:

```markdown
# Claude News Briefing — YYYY-MM-DD

## Claude

- Summary of news item — [Source Title](URL)
- Summary of news item — [Source Title](URL)

## Claude Code

- Summary of news item — [Source Title](URL)

## Claude Cowork

- Summary of news item — [Source Title](URL)

---

*Generated on YYYY-MM-DD. Covers the last 3 days of news.*
```

---

## Input Requirements

No manual input needed. The prompt is self-contained — just run it.

The only variable is **today's date**, which the model determines automatically.

---

## Context Requirements

None. No files to attach or pre-load. All data is gathered at runtime via web search.

---

## Output Format

A single markdown file: `outputs/claude-news-briefing-YYYY-MM-DD.md`

Contents:
- Bullet-point summaries grouped by topic (Claude, Claude Code, Claude Cowork)
- Each bullet includes a one-sentence summary and a hyperlinked source
- Date-stamped filename and footer

---

## Where to Run

**Recommendation: Normal chat**

**Reasoning:**
- This workflow runs on-demand, not on a fixed schedule
- Zero context files are needed — everything is gathered at runtime
- No conversation memory across runs is required
- The prompt is fully self-contained

Simply paste this prompt into a new Claude chat (or Claude Code session) with web search access and let it run.

---

## Recommended Implementation Order

### Tier 1: Quick wins (start here)
- **Step 3 — Save to file:** Deterministic file write with a clear template. This is the simplest part and works out of the box with the prompt instructions above.

### Tier 2: High-value semi-autonomous steps
- **Step 2 — Summarize with links:** AI handles the summarization. If you find the output quality varies, you can add an optional review gate — pause after summarization and ask for confirmation before saving.

### Tier 3: Complex steps
- **Step 1 — Search for news:** Depends on WebSearch/WebFetch tool access. If running in Claude Code, these tools are available natively. If running in Claude.ai chat, web search must be enabled. This step is the most likely failure point — if searches return no results, the workflow has nothing to summarize.
