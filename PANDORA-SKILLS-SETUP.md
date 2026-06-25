# Pandora AI Archetype Skills — Setup Guide

Two Claude Code skills for creating and using research-grounded AI user archetypes across foodpanda, foodora, and Yemeksepeti.

| Skill | What it does |
|-------|-------------|
| `/pd-create-archetype` | Builds an AI archetype from real research files (transcripts, surveys, analytics) |
| `/pd-use-archetype` | Loads an archetype and lets you converse with it to stress-test designs, flows, and hypotheses |

---

## Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed
- Access to the [Pandora Research Repository](https://drive.google.com/drive/folders/1y8e3FPZaw83l64ZsSAHZU0C4AZ814wBY) on Google Drive
- Your Claude Code session connected to Google Drive (via MCP)

---

## Setup: Load the Skills into Your Terminal

### Option A — Clone this repo (recommended)

```bash
git clone https://github.com/ryanfoodpanda/ryanfoodpanda.git
cd ryanfoodpanda
claude
```

The skills in `.claude/commands/` are automatically available in any Claude Code session opened from this directory.

### Option B — Copy skills to your own project

If you want to use these skills inside your own project folder:

```bash
# From your project directory
mkdir -p .claude/commands

# Copy both skill files
curl -o .claude/commands/pd-create-archetype.md \
  https://raw.githubusercontent.com/ryanfoodpanda/ryanfoodpanda/main/.claude/commands/pd-create-archetype.md

curl -o .claude/commands/pd-use-archetype.md \
  https://raw.githubusercontent.com/ryanfoodpanda/ryanfoodpanda/main/.claude/commands/pd-use-archetype.md
```

Then open Claude Code from that directory:

```bash
claude
```

---

## Running the Skills

### Create an archetype

```
/pd-create-archetype
```

Claude will ask you for:
1. Brand (foodpanda / foodora / Yemeksepeti) and market
2. The user segment you're creating the archetype for
3. Your research files — paste the Google Drive folder link or upload files directly
   - Default folder: `https://drive.google.com/drive/folders/1y8e3FPZaw83l64ZsSAHZU0C4AZ814wBY`
   - Minimum: 5 user interview transcripts
   - Optional: surveys, analytics data, research decks

The skill generates a full archetype `.md` document including:
- Goals, pain points, behaviours, jobs-to-be-done
- Every insight tagged as `[EVIDENCE]` or `[ASSUMPTION]`
- Researcher names and study citations on every claim
- `⚠️ LOW CONFIDENCE` flags where evidence is thin
- Groundedness, Coverage, and Source Quality scores
- A Gold / Silver / Needs More Research confidence tier

Save the output as `[archetype-name]-[brand]-[market]-archetype.md` and store it in the Pandora Research Repository.

---

### Use an archetype

```
/pd-use-archetype
```

Claude will ask you to paste or link the archetype `.md` file. Once loaded, Claude embodies the archetype and you can ask it questions like:

- *"How would you react to this new feature?"*
- *"Walk me through how you'd complete this flow."*
- *"What would make you more likely to reorder?"*

Every response includes a confidence flag — `[EVIDENCE]`, `[ASSUMPTION]`, or `⚠️ LOW CONFIDENCE` — so you always know how much weight to place on the answer.

At the end of a session, ask for a **session summary** to see which insights were evidence-based vs. assumed, and what to validate with real users next.

---

## Quality Framework

Both skills apply the **Groundedness, Coverage, Source Quality** framework to every insight:

| Dimension | Question it answers |
|-----------|-------------------|
| **Groundedness** | Is this insight backed by actual evidence — quotes, data, observations? |
| **Coverage** | Did the synthesis capture all major themes, or over-index on one? |
| **Source Quality** | How much confidence should we place in the evidence? (Higher when repeated across qual + quant, recent ≤18 months) |

### Confidence Tiers

| Tier | Meaning |
|------|---------|
| 🥇 Gold | Strong evidence base. Qual + quant. Mostly recent. Use with confidence. |
| 🥈 Silver | Reasonable evidence base. Some gaps or single-method sources. Use, but validate key assumptions. |
| ⚠️ Needs More Research | Limited evidence. Treat as directional only. Run more research before acting on it. |

---

## Do's and Don'ts

**Do:**
- Use archetypes to stress-test designs, flows, and copy before going to real users
- Use archetypes to align teams on user context and priorities
- Use archetypes to generate hypotheses for further research
- Update archetypes over time as new research comes in

**Don't:**
- Use archetypes to validate strategies or concepts
- Treat archetype responses as direct user evidence
- Use for high-stakes decisions without real user validation
- Assume everything in a Silver or ⚠️ archetype is accurate

---

## Questions or Improvements

Reach out to **Ryan Lim** (ryan.lim@foodpanda.com) or open an issue in this repo.
