# Local Trending-Shop Audit

[English](README.md) | [简体中文](README.zh-CN.md)

> Inventory the trending shops in a city or district and produce a three-part deliverable: an Excel ledger, a Word report and an interactive HTML ranking.

## What this is

This is not a list of shop names pulled from one search. Lists like that are cheap and unreliable, and the moment someone asks "are they still open?" the whole thing collapses.

What it produces instead is an auditable ranking: every score traces back to a source link you can click. Where a fact could not be confirmed, it is marked as unconfirmed rather than invented.

## Why we open-sourced it

We did this a few times for local projects and it kept being useful — opening a category, choosing a location, evaluating a market. Each time we rebuilt the same pipeline, so we stopped rebuilding it.

This is a research methodology rather than a company asset: the sources are public, the scoring model is a documented weighting, and the output format is generic. Nothing about it belongs to us.

## What it does

- **Four parallel research tracks.** Different source types are searched separately and their findings reconciled, instead of one search standing in for the whole picture.
- **Five-dimension weighted index.** The scoring model is documented, and every point is traceable to evidence rather than assigned by impression.
- **Incremental expansion.** A `data2.py` hook plus rule-based auto-scoring lets you grow a batch without redoing the first one.
- **Two routes to business-registration data**, used to check whether a shop still legally exists rather than relying on a listing that may be years old.
- **One script, three outputs.** The Excel ledger, Word report and HTML ranking all come from a single run, so the numbers cannot drift apart between formats.
- **A fallback verification path.** When browser automation is unavailable, a minimal Node DOM check keeps verification possible.

## Requirements

Python 3 · Node (optional, for the fallback verification path)

## Installation

```bash
git clone https://github.com/<your-username>/local-wanghong-audit.git
```

Then place the folder into your agent skills directory:

| OS | Path |
|---|---|
| Windows | `C:\Users\<you>\.workbuddy\skills\local-wanghong-audit\` |
| macOS / Linux | `~/.workbuddy/skills/local-wanghong-audit/` |

There is no build step. Restart the session and it takes effect.

## How to use

State the area and what you want:

- "Inventory the trending shops in <area>"
- "Give me a ranking, and mark which ones have closed"
- "Split them into chains and independent shops"

Before starting, the skill asks for four scoping parameters, because "trending" means different things depending on the answer.

## Files

```
└── SKILL.md
```

## Notes and limits

1. **Unconfirmed is a valid answer.** The methodology prefers marking a fact unknown over filling it in plausibly. Expect some cells to say so.
2. **Index scores are relative, not absolute.** A score of 80 means "high within this batch", not "80 out of 100 in general".
3. **Listing platforms go stale.** Opening hours, closure and even existence can be years out of date. Registration data is the reason the second route exists.
4. **The scoping questions are not optional.** Skipping them produces a ranking that answers the wrong question.

## License

MIT
