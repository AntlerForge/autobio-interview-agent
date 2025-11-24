# Design Decisions

This file records key design choices for the autobiographical interview system.

## 2025-11-22 – Initial setup

- Chosen architecture:
  - File-backed interview system in this repo.
  - Separate roles for interviewer, event extractor, and biographer.
- Data model:
  - Individual “events” stored as JSON objects following `config/interview_schema.json`.
  - All events merged into `data/autobiography/autobio_timeline.json`.
- Output:
  - Primary narrative stored in `data/autobiography/autobio_draft_v01.md`.
- Purpose:
  - Personal autobiography and learning exercise for a future “retiring experts” system.