Autobiographical Interview Agent
================================

This project is a **file-backed autobiographical interview system** for Tony.  
It is designed both as a personal autobiography tool and as a **learning rig** for a future
“retiring experts’ knowledge capture” system.

## Goals

- **Interview** Tony conversationally about his life.
- **Store** each interview session on disk (raw transcript + structured events).
- **Analyse** all sessions into a merged life-events timeline.
- **Generate and refine** a written autobiography from that timeline.

All behaviour and data are defined in this repository via **Markdown**, **JSON**, and other
human-readable formats. There is deliberately **no external database** or complex framework.

## Project layout

- `prompts/`
  - `system_prompt.md` – Core behaviour of the interviewer, event-extractor, and biographer.
  - `interview_question_templates.md` – Libraries of question patterns by phase/topic.
  - `biography_outline_template.md` – Template for structuring the written autobiography.

- `config/`
  - `interview_schema.json` – JSON schema for a single “life event” or “story”.
  - `session_settings.json` – Settings for session length, number of questions, etc.

- `data/`
  - `sessions/`
    - One Markdown file per interview session (raw transcript).
    - One JSON file per interview session (structured events).
  - `autobiography/`
    - `autobio_timeline.json` – Merged and deduplicated life events from all sessions.
    - `autobio_draft_v01.md` – Current assembled autobiography draft.

- `notes/`
  - `design_decisions.md` – Running log of design choices and rationales.
  - `backlog.md` – TODOs, ideas, and future enhancements.

## Modes of operation

The system is intended to support four conversational “modes”:

1. **INTERVIEW mode**
   - Conduct a live interview with Tony using the prompts and settings.
   - Maintain a clear session structure (warm-up → focus → deep dives → reflection → recap).
   - Save:
     - `data/sessions/session_YYYYMMDD_HHMM_raw.md`
     - `data/sessions/session_YYYYMMDD_HHMM_structured.json`

2. **ANALYSIS mode**
   - Read all `data/sessions/*_structured.json`.
   - Merge events into `data/autobiography/autobio_timeline.json`, deduplicating and refining.
   - Use the outline template + timeline to generate or update `autobio_draft_v01.md`.

3. **REVIEW/EDIT mode**
   - Work with Tony to refine `autobio_draft_v01.md`.
   - Propagate important factual corrections back into `autobio_timeline.json`.

4. **MAINTENANCE/DESIGN mode**
   - Improve question templates, schemas, and workflows.
   - Record design decisions and backlog items under `notes/`.

## File-backed contract

- **Source of truth**:
  - Prompts and behaviour live in `prompts/`.
  - Schemas and settings live in `config/`.
  - Session data and autobiography live in `data/`.
- All updates should:
  - Be written back to disk.
  - Be explained briefly in `notes/design_decisions.md` where they represent a real design choice.

## Getting started

1. Decide which mode to use:
   - INTERVIEW – start a new interview session.
   - ANALYSIS – process existing sessions into the timeline and draft.
   - MAINTENANCE/DESIGN – tweak the system itself.
2. Use the files in `prompts/` and `config/` as the controlling configuration for the assistant.
3. Keep iterating on the design as you learn what works for Tony.

<!-- TODO: Add examples of a full session (raw + structured) and a sample timeline snippet. -->


