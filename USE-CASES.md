# Use Cases — KnowledgeBase Skill

Real-world scenarios for using the Obsidian KnowledgeBase skill.

---

## 1. Capture Meeting Notes on the Fly

**Scenario:** You just finished a team standup and want to save key decisions.

**How:**
```
"Save this as a conversation note — we decided to migrate from REST to GraphQL
for the product API. Timeline is Q2. Sarah owns the schema design, Tom handles
the gateway setup."
```

**Result:** Saved to `{{VAULT_PATH}}/2. Notes/Conversations/2026-03-12-rest-to-graphql-migration.md` with tags: `migration`, `graphql`, `api`, `team-decision`.

---

## 2. Build a Learning Log

**Scenario:** You learned something useful while debugging and want to remember it.

**How:**
```
"Save this learning — When using Prisma with PostgreSQL, always use
@db.Text instead of @db.VarChar for fields that might exceed 255 chars.
The default VarChar silently truncates."
```

**Result:** Saved to `{{VAULT_PATH}}/2. Notes/Learning/2026-03-12-prisma-text-vs-varchar.md` with tags: `prisma`, `postgresql`, `database`.

---

## 3. Queue Articles for Weekend Reading

**Scenario:** You find interesting articles during the week but don't have time to read them now.

**How:**
```
"Watch later: https://example.com/article-about-ai-agents"
"Read later: https://example.com/react-server-components-deep-dive"
```

**Later:**
```
"Show my queue"
```

**Result:** URLs added to the watch-later queue with auto-detected types. View your queue anytime with a simple command.

---

## 4. Daily Knowledge Review

**Scenario:** At end of day, you want to see everything you captured.

**How:**
```
"What did I save today?"
```

**Result:** Shows the daily note with links to all notes, journal entries, and resources saved that day — organized by type.

---

## 5. Search Across Your Entire Vault

**Scenario:** You remember saving something about "rate limiting" months ago but can't find it.

**How:**
```
"Search my vault for rate limiting"
```

**Or more specific:**
```
"Find all notes tagged with 'architecture'"
"Search for notes from last week about deployment"
```

**Result:** Returns matching notes with title, date, tags, and a content preview. Offers to open the full note.

---

## 6. Daily Journaling / Reflection

**Scenario:** You want to log thoughts, reflections, or daily progress.

**How:**
```
"Journal entry — Today was productive. Shipped the auth refactor,
got positive feedback from the team. Need to follow up on the
performance regression in the dashboard."
```

**Result:** Appended to today's journal file at `{{VAULT_PATH}}/4. Journal/2026-03-12.md` with a timestamp. Multiple entries per day are supported.

---

## 7. Clip Web Content for Reference

**Scenario:** You found a great blog post and want to save it to your vault.

**How:**
```
"Clip this article: https://example.com/scaling-postgres-tips"
```

**Result:** Fetches the article content, extracts key information, saves to `{{VAULT_PATH}}/5. Resources/Clippings/2026-03-12-scaling-postgres-tips.md` with source URL, tags, and a clean markdown version.

---

## 8. Weekly Review

**Scenario:** End of week, you want to reflect on progress and plan ahead.

**How:**
```
"Weekly review"
```

**Result:** Creates a weekly review file from your template at `{{VAULT_PATH}}/4. Journal/2026-03-12-weekly-review.md` with sections for wins, learnings, and next week's focus.

---

## 9. Quick Idea Capture

**Scenario:** A product idea hits you mid-conversation and you want to save it before you forget.

**How:**
```
"Save this idea — What if we built a Slack bot that summarizes
unread channels each morning using AI? Could save 30 min/day for
the whole team."
```

**Result:** Saved to `{{VAULT_PATH}}/2. Notes/Ideas/2026-03-12-slack-ai-morning-summary-bot.md` with tags: `product-idea`, `slack`, `ai`, `productivity`.

---

## 10. Process Watch Later Queue

**Scenario:** It's the weekend and you want to go through your saved articles.

**How:**
```
"Show my queue"
— pick an item —
"Process the first article from my queue"
```

**Result:** The article is fetched, extracted, saved as a proper vault note with tags and connections, and moved from Queue to Processed in the watch-later file.

---

## Team Workflow Examples

### Shared Knowledge Base

Team members can each run this skill against a **shared Obsidian vault** (e.g., via OneDrive, Dropbox, or Git) to build a collective knowledge base.

### Onboarding Documentation

New team members can use the skill to:
- Save learnings as they ramp up
- Search existing team notes for context
- Build a personal learning log linked to team resources

### Research Collection

During research phases, team members can:
- Queue articles and papers with "watch later"
- Process and extract key insights into structured notes
- Search across all team research by keyword or tag
