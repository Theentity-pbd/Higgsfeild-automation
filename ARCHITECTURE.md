# Architecture

This repository is a modular brand automation system for PBD London. Each folder has a single responsibility.

## Folder Map

| Folder | Purpose |
|--------|---------|
| `brand/` | Core brand identity — typography, colour system, audience psychology |
| `cinematics/` | Visual direction — camera language, lighting, motion, editing, shot composition |
| `content/` | Content frameworks — TikTok, Instagram, captions, hooks, emotional triggers |
| `commerce/` | Commerce systems — product launch, Shopify, conversion (planned) |
| `strategy/` | Business intelligence — positioning, growth, monetisation (planned) |
| `prompts/` | Prompt templates with `{{VARIABLE}}` systems for Seedance and captions |
| `workflows/` | Process definitions — the 10-stage video pipeline |
| `agents/` | Agent operating instructions and behaviour rules |
| `SYSTEM/` | Operational intelligence — rules, automations, campaign log, integration docs |

## Root Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Claude Code operating instructions for this repo |
| `CREATIVE-DIRECTION.md` | Master brand identity — stable, rarely changes |
| `brand-voice.md` | Communication tone and writing rules |
| `visual-language.md` | Visual composition and design rules |
| `ARCHITECTURE.md` | This file |

## Structure Principle

One file = one responsibility.

Do not mix unrelated systems across files. Brand voice does not belong in commerce files. Cinematic direction does not belong in SEO files. Keep each file modular, clearly named, and easy to retrieve from.

Core identity files (`CREATIVE-DIRECTION.md`, `brand-voice.md`, `visual-language.md`) remain stable at root level. Sub-systems evolve independently inside their folders.
