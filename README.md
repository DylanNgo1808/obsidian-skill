# Obsidian KnowledgeBase Skill

A Claude Code skill that saves, searches, and manages content in an Obsidian vault.

## Overview

This skill turns your AI assistant into a knowledge management partner. It can save notes, clip articles, journal, queue content for later, and search your entire vault — all through natural language.

## Architecture

```
KnowledgeBase/
├── SKILL.md              # Skill entry point & workflow routing
└── Workflows/
    ├── Save.md           # Save notes, ideas, learnings, resources
    ├── Search.md         # Find existing vault content
    ├── DailyJournal.md   # Journal entries & weekly review
    ├── DailyNote.md      # Daily aggregation of all saved content
    └── WatchLater.md     # URL queue for future processing
```

## Vault Structure

The skill organizes content into these directories (configurable):

| Directory | Purpose |
|-----------|---------|
| `1. Inbox/` | Quick captures, unsorted items, watch-later queue |
| `2. Notes/Reference/` | Factual notes, references |
| `2. Notes/Learning/` | Lessons, tutorials, TIL |
| `2. Notes/Ideas/` | Brainstorms, concepts, hypotheses |
| `2. Notes/Conversations/` | Chat summaries, meeting notes |
| `3. Projects/` | Project-specific notes |
| `4. Journal/` | Daily journal entries, weekly reviews |
| `5. Resources/Clippings/` | Web clippings, article saves |
| `7. Daily Notes/` | Auto-generated daily aggregation |

## Quick Start

1. Copy `CONFIG.example.md` and set your vault path
2. Place the skill files in your Claude Code skills directory
3. Say "save this note about..." or "search my vault for..."

## Configuration

See [CONFIG.example.md](./CONFIG.example.md) for all configurable values.

## Workflows

| Workflow | Triggers | What It Does |
|----------|----------|-------------|
| **Save** | "save this", "clip this", "note this down" | Routes content to the right vault folder with tags and metadata |
| **Search** | "search vault", "find notes about..." | Full-text, tag, title, date, or type search |
| **DailyJournal** | "journal entry", "weekly review" | Timestamped journal entries, one file per day |
| **DailyNote** | "what did I save today" | Auto-aggregated index of everything saved on a given day |
| **WatchLater** | "watch later", "read later", "show queue" | URL queue with type hints, processing tracking |

## File Format

Every saved note uses Obsidian-compatible markdown with YAML frontmatter:

```markdown
---
title: "Note Title"
date: 2026-03-12
type: learning
tags:
  - tag1
  - tag2
source: "conversation"
connections:
  related: ["[[2026-03-10-related-note]]"]
  status: connected
---

# Note Title

Content body in clean markdown.

## Connections

**Related:** [[2026-03-10-related-note]]
```

## Features

- **Auto content-type routing** — detects note type from your intent
- **Smart tagging** — generates 2-5 relevant tags automatically
- **Vault connections** — discovers and links to related existing notes via wikilinks
- **Daily note updates** — every save is logged in the daily note
- **Watch Later integration** — queued URLs auto-link when processed
- **Sources Index** — chronological index of all consumed content
- **Duplicate detection** — warns if URL already saved

## Guides

- [Use Cases](./USE-CASES.md) — Common scenarios and examples
- [Usage Guide / Hướng dẫn sử dụng](./USAGE-GUIDE.md) — Detailed guide (Vietnamese)
