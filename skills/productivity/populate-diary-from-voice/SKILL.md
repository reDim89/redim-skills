---
name: populate-diary-from-voice
description: Process voice recording transcriptions from Tana calendar days into structured Check-in entries with Mood, Energy, and Diary fields
---

# Skill: Populate Diary from Voice Transcriptions

Go through Tana calendar day nodes, find voice recording transcriptions, and populate Check-in (#check_in) entries with Mood, Energy, and Diary fields.

## Trigger
User asks to process voice recordings/transcriptions into diary entries, or requests to populate check-ins from voice notes.

## Workflow

### 1. Get Workspace and Tag Info
```
Workspace ID: h_s6rhVZZh
Check-in tag ID: rgaDKl-sF0

Field IDs:
- Diary: qmUf98CwPR (Content - multi-value for diary entries)
- Mood: RchdkGoKj6 (Number - 1-10)
- Energy: 2NYqoRR52e (Number - 1-10)
```

### 2. For Each Date in Range
1. Get the calendar day node using `get_or_create_calendar_node` with:
   - workspaceId: h_s6rhVZZh
   - granularity: day
   - date: YYYY-MM-DD format

2. Read the day node with `read_node` (maxDepth: 5) to find voice transcriptions

3. Voice transcriptions are typically:
   - Child nodes under the day node (not under existing Check-in)
   - Often start with "Чек-ин" or contain date/time markers
   - Contain "Настроение X, энергия Y" pattern in Russian (recordings are in Russian)
   - Multiple paragraphs of diary content

### 3. Extract Data from Transcription
Parse the transcription text for:
- **Mood**: Look for "Настроение X" or "настроение X" (X is a number 1-10)
- **Energy**: Look for "энергия X" or "Энергия X" (X is a number 1-10)
- **Diary**: All the diary content (can span multiple nodes/paragraphs) — preserve the original Russian text

### 4. Create Check-in Entry
Use `import_tana_paste` with the day node as parent:

```
- Check-in #[[^rgaDKl-sF0]]
  - [[^qmUf98CwPR]]::
    - [First diary paragraph]
    - [Second diary paragraph]
    - [etc.]
  - [[^RchdkGoKj6]]:: [mood number]
  - [[^2NYqoRR52e]]:: [energy number]
```

### 5. Cleanup: Trash Processed Voice Nodes
After successfully creating the Check-in entry, trash the source voice transcription nodes using `trash_node`:
- If the voice transcription nodes are grouped under a parent container (e.g., "Задачи на сегодня", "Чек-ин 3 марта"), trash the parent node — this removes all children too.
- If voice nodes are direct children of the day node, trash each individual voice node.
- This is a soft delete — nodes can be restored from Tana trash if needed.

### 6. Voice Transcription Patterns
Typical voice recording transcription structure (in Russian):
- Header: "Чек-ин [date], утро/вечер, [day of week]. Настроение X, энергия Y."
- Yesterday recap: "Вчера был..."
- Today status: "Сегодня..."
- Plans: "По планам/приоритетам сегодня..."

## Example Usage
User: "Process voice transcriptions for Jan 26-28"

1. Get day nodes for 2026-01-26, 2026-01-27, 2026-01-28
2. Read each day node to find transcription content
3. Extract mood/energy numbers and diary text
4. Create Check-in entries with properly formatted Tana Paste
5. Trash the processed voice transcription nodes

## Notes
- Skip days that already have Check-in entries with Diary content
- Voice transcriptions may be under task/planning headers, not at root of day
- Mood and energy are typically stated at the start of the transcription
- Diary content stays in Russian (matches the recording); only Tana node/field labels are in English
- Content should be cleaned up but preserve the original meaning
