# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

This is not a software codebase. It is a **brand automation intelligence system** for **PBD London** — a luxury streetwear brand ("Pressure Builds Diamonds"). The repo acts as persistent memory, creative infrastructure, and operational context for AI-assisted content and video production.

The primary workflow automates cinematic video generation using **Seedance 2.0 via Higgsfield**, with Claude handling prompt engineering, variable population, and output logging to Obsidian.

---

## Required Read Order Before Any Output

Per `agents/claude-code-instructions.md`, always read in this order before generating any creative output:

1. `ARCHITECTURE.md` — modular system structure and planned folder hierarchy
2. `SYSTEM/operating-rules.md` — quality rules, automation logic, agent behaviour
3. `CREATIVE-DIRECTION.md` — master brand identity (PBD London, full visual/voice/audience context)
4. `brand-voice.md` — communication tone, writing rules, platform voice adaptation
5. `Visual language md` — composition, typography, colour, garment, and cinematic rules
6. Relevant workflow or prompt file (e.g. `workflows/video-pipeline.md`, `prompts/seedance-base-prompt.md`)

---

## Architecture

The system follows **one file = one responsibility**. Do not mix concerns across files.

| Path | Purpose |
|------|---------|
| `CREATIVE-DIRECTION.md` | Master brand identity — stable, rarely changes |
| `brand-voice.md` | Communication style for all written outputs |
| `Visual language md` | Visual composition and design rules |
| `SYSTEM/operating-rules.md` | Operational intelligence, quality gates, agent rules |
| `ARCHITECTURE.md` | Folder structure plan and system philosophy |
| `agents/claude-code-instructions.md` | Claude's operating instructions within this repo |
| `prompts/seedance-base-prompt.md` | Modular Seedance 2.0 video prompt with `{{VARIABLE}}` placeholders |
| `prompts/caption-prompt.md` | Modular caption generation system with `{{VARIABLE}}` placeholders |
| `workflows/video-pipeline.md` | 10-stage pipeline: Brief → Context Analysis → Variables → Prompt → Validate → Submit → Review → Select → Export → Log |

**Planned but not yet created:** `/brand`, `/cinematics`, `/content`, `/commerce`, `/strategy` sub-directories per `ARCHITECTURE.md`.

---

## Prompt Variable System

Both prompt files use `{{VARIABLE_NAME}}` placeholders. When building prompts:

1. Load the base prompt file
2. Populate each `{{VARIABLE}}` with concise, cinematic, emotionally precise wording
3. Preserve the modular structure — do not flatten into prose
4. Validate emotional consistency against brand direction
5. Remove duplicated wording

**Disallowed variable language:** `epic`, `insane`, `futuristic`, `mind blowing`, `viral`, `luxury drip`, `alpha`, `boss energy`

---

## File Conventions

- File names: `kebab-case.md`
- Place files only in their correct directory (`prompts/`, `workflows/`, `agents/`, etc.)
- Before creating any new file, scan related directories to avoid duplication — update existing files instead

---

## Video Pipeline Summary (10 Stages)

`workflows/video-pipeline.md` defines the full workflow:

1. **Brief Intake** — campaign name, product focus, scene + emotional direction, output type
2. **Campaign Context Analysis** — validate brief against brand files
3. **Variable Population** — fill campaign, visual, subject, and technical variables
4. **Prompt Construction** — load `seedance-base-prompt.md`, inject variables
5. **Seedance Prompt Validation** — pre-generation QC checklist
6. **Higgsfield Submission** — submit prompt into Seedance 2.0
7. **Output Review** — review against cinematic quality, brand alignment, emotional weight
8. **Asset Selection** — approve or reject
9. **Export & Naming** — format: `YYYYMMDD-campaign-scene-version` (e.g. `20260522-pressure-season-rooftop-v01`)
10. **Obsidian Logging** — log campaign name, date, prompt version, approved/failed outputs, asset paths

---

## Core Creative Rules (When Uncertain)

- Choose restraint over noise
- Choose premium minimalism over complexity
- Choose emotional realism over artificial aesthetics
- Choose cinematic storytelling over spectacle
- Fashion-house presentation takes priority over hype culture

If an output feels generic, repetitive, structurally messy, or emotionally weak — stop and reassess.
