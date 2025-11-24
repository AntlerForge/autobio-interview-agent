# Generic Blueprint: Building Local File-Backed Custom LLM Agents in Cursor
### A domain-agnostic reference for reusable custom agents

## 1. What This Pattern Is
A method for building persistent, file-backed, restartable custom LLM agents inside Cursor using:

- A saved boot prompt (defines behaviour)
- A structured project directory (defines memory & logic)
- Full file I/O
- Clear modes
- Reusable schemas/templates
- Stateless chat + stateful disk → persistent agent

Use cases include research assistants, analysts, planning agents, code-generation systems, domain-specific experts, and any multi-step agent that needs memory.

## 2. Core Principles (Domain-Neutral)
- The first message in Cursor is the system prompt.
- The system prompt must be stored on disk.
- All persistent memory lives in files.
- The agent must be instructed to read & obey files.
- Use a clean project directory.
- Use clear modes.
- A loader prompt makes re-init trivial.

## 3. Boot Prompt (Generic Template)
(Contents abbreviated here for brevity in this preview; full detail in prior message.)

## 4. system_prompt.md — Generic Behaviour Layer
Defines roles, modes, behaviour logic; domain-agnostic.

## 5. How New Projects Use This Blueprint
1. Copy folder template
2. Copy generic boot prompt
3. Add project-specific roles to system_prompt.md
4. Define templates in prompts/templates
5. Define schemas in config/schema.json
6. Load via new Cursor chat
7. Agent initialises from files

## 6. Summary
- Boot Prompt loads system
- system_prompt.md defines behaviour
- config defines structure
- data stores memory
- Cursor executes
- Reload via loader prompt
