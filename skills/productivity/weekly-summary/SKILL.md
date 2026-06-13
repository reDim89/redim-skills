---
name: weekly-summary
description: Generate a weekly reflection summary from daily Check-in entries and populate the Weekly outcomes node in Tana
---

# Skill: Weekly Summary

Generate a structured weekly reflection from daily Check-in (#check_in) entries, then populate the "Weekly outcomes" node in the corresponding Tana week with average Mood, Energy, and a Diary reflection.

## Trigger
User asks to generate a weekly summary, weekly reflection, or "weekly outcomes".

## Workflow

### 1. Constants
```
Workspace ID: h_s6rhVZZh
Check-in tag ID: rgaDKl-sF0

Field IDs:
- Diary: qmUf98CwPR (Content - multi-value for diary entries)
- Mood: RchdkGoKj6 (Number - 1-10)
- Energy: 2NYqoRR52e (Number - 1-10)
```

### 2. Determine Target Week
- Ask the user which week to summarize (default: current week, or last week if today is Mon/Tue)
- Get the week calendar node using `get_or_create_calendar_node` with granularity: "week" and a date from that week

### 3. Collect Daily Check-ins
1. Read the week node with `read_node` (maxDepth: 5) to see all day nodes and their children
2. For each day in the week, look for Check-in (#check_in) entries that have Mood, Energy, and Diary fields
3. Also collect any raw voice transcription nodes (child nodes containing "Настроение X, энергия Y" patterns in Russian) that haven't been processed into Check-ins yet
4. Record per day:
   - Date and day of week
   - Mood value (number)
   - Energy value (number)
   - Diary content (all diary paragraphs)

### 4. Check for Existing "Weekly outcomes"
- Search children of the week node for a node named "Weekly outcomes"
- If it already has Diary content filled in, warn the user and ask whether to overwrite or skip

### 5. Generate Weekly Reflection
Using the collected daily data, generate a reflection in the same language as the diary entries (typically Russian), following this structure:

```
Diary for dd/MM – dd/MM
0. Summary (2 sentences summarizing all entries)
1. Average energy for the week: X.X
2. Average mood for the week: X.X
3. Key wins (no more than 5)
4. Factors that most influenced energy
   -- For each factor, mention if it was a positive or negative influence
5. Factors that most influenced mood
   -- For each factor, mention if it was a positive or negative influence
```

**Generation rules:**
- Whenever referencing a record, use exact names, dates and key events. Example: instead of "Went for a walk" say "Walk with Marina and music (Sat, 1 Feb)" (or the Russian equivalent if the diary is in Russian)
- Keep answers concise but do not omit important details — the summary should feel like a talk with a real coach
- Think step by step: first reason about the data, then generate the reflection
- Calculate averages from all available mood/energy values across the week (round to 1 decimal)
- Round the averages to the nearest integer for the Mood and Energy field values
- Match the language of the diary entries (Russian in, Russian out) — only Tana node/field labels and the section headers below are in English

### 6. Create or Update "Weekly outcomes" in Tana
If no "Weekly outcomes" node exists yet, use `import_tana_paste` with the week node as parent:

```
- Weekly outcomes #[[^rgaDKl-sF0]]
  - [[^RchdkGoKj6]]:: [rounded average mood]
  - [[^2NYqoRR52e]]:: [rounded average energy]
  - [[^qmUf98CwPR]]::
    - [Summary paragraph]
    - **Key wins:**
      - [win 1]
      - [win 2]
      - ...
    - **Factors that most influenced energy:**
      - [factor 1 (positive/negative)]
      - ...
    - **Factors that most influenced mood:**
      - [factor 1 (positive/negative)]
      - ...
```

If "Weekly outcomes" already exists but has no Diary content, use `set_field_content` to set Mood and Energy, and `import_tana_paste` to add Diary children.

### 7. Present Summary to User
After writing to Tana, display the generated summary to the user in the chat for review.

## Example Usage
User: "Generate weekly summary" or "Weekly outcomes"

1. Ask which week (default: current)
2. Fetch week node → read all days → collect Check-in data
3. Calculate averages: Mood 7.2, Energy 7.0
4. Generate structured reflection with specific dates and events
5. Create "Weekly outcomes" node in the week with averages and diary

## Notes
- Days without Check-in entries are skipped in the averages (don't count as 0)
- If a day has multiple Check-in entries (morning + evening), include all mood/energy values in the average
- The reflection should reference specific events, people, and dates from the diary entries
- Structural labels (section headers, field names) are in English; diary body text stays in the user's diary language
