# Design Decisions – Autobiographical Interview Agent

This file records key design choices for the autobiographical interview system.

## 2025-11-22 – Initial local project structure

- **Architecture**
  - File-backed interview system under `autobio-interview-agent/`.
  - No external databases or services; everything is stored as Markdown/JSON.
  - Clear separation between prompts, config, data, and notes.

- **Roles**
  - Distinct conceptual roles for:
    - Interviewer (live conversation),
    - Event Extractor (mapping transcript → events),
    - Biographer (timeline + narrative),
    - Light-weight System Designer (maintaining prompts/schemas).

- **Data model**
  - Individual “events” stored as JSON objects following `config/interview_schema.json`.
  - All events merged into `data/autobiography/autobio_timeline.json`.
  - One pair of files per session:
    - `session_YYYYMMDD_HHMM_raw.md`
    - `session_YYYYMMDD_HHMM_structured.json`

- **Autobiography output**
  - Primary narrative stored in `data/autobiography/autobio_draft_v01.md`.
  - Structure and tone guided by `prompts/biography_outline_template.md`.

- **Future-proofing for “retiring experts”**
  - Life stages and domains are designed so they can later be swapped for:
    - Roles/systems,
    - Incidents/failures/successes,
    - Organisational contexts.

## 2025-11-22 – Session settings baseline

- **Session control parameters**
  - `default_session_length_minutes`: 45
  - `max_questions_per_session`: 15
  - `target_events_per_session`: 3
  - `allow_mid_session_summarise`: true
  - `max_followups_per_story`: 4
  - `recap_required`: true

- **Rationale**
  - Start with a comfortably long but not exhausting session length.
  - Prioritise **depth over breadth**: aim for a few well-developed stories.
  - Make recap mandatory to reinforce structure and aid later event extraction.

<!-- TODO: Add a section once the first real session has been run, capturing observations about pacing, question style, and emotional load. -->



