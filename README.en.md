# api-with-docs

[中文](README.md) | **English**

Writes client-facing API docs, field notes, and Apifox descriptions. It does not write business-process docs or translate implementation into prose.

## Use with grill-with-docs

This skill **depends on** `grill-with-docs` (install that skill first) to align **domain terms** and keep the project `CONTEXT.md`.

Without grill-with-docs there is no stable glossary. The model will still coin names, narrate code as “business”, and invent “because”. Results drop sharply. Install and use grill first, then `/api-with-docs`.

## What it does

The reader is the App / frontend / other caller. Each endpoint (fields: same shape, shorter) has three blocks only:

1. **How to use** — purpose first; then only the call constraints the caller must know.
2. **How to pass params** — mappings the schema does not show. Do not copy the parameter table.
3. **Notes** — one rule per bullet. Split by workflow state / business scenario only when outcomes differ. Write “this endpoint does not do X” only when another endpoint is easy to confuse with this one.

See [examples.md](examples.md). Glossary: [CONTEXT.md](CONTEXT.md). Rules: [SKILL.md](SKILL.md).

## What it does not do

- No coined names. Pair existing terms as `中文(\`code\`)`. If there is no Chinese name, keep the identifier and mark **待确认**.
- No speculation, no invented “because”, no summarizing backend call chains as business.
- Does not edit a product repo’s glossary (grill-with-docs does).
- Do not run `/chinese-ai-humanizer` on this copy.

## Install

Read https://github.com/anlondon/api-with-docs and install this skill.
