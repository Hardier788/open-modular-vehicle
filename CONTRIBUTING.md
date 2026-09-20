# Contributing to OMVA

This is a Draft 0.1 concept framework, not a finished standard. It needs
criticism more than it needs new content right now.

## Most useful contributions, in order of value

1. **"This is wrong, and here's why"** — especially on anything
   safety-critical, structural, or regulatory. If you're an automotive
   engineer and section 4 (power module) is naive about crash-load paths,
   say so specifically. That's worth more than a whole new spec section.
2. **Prior art pointers** — if something in here already exists (OBD-II,
   ISO standards, an existing open-hardware vehicle project), link it so
   OMVA can reference or defer to it instead of reinventing it.
3. **Domain-specific spec drafts** — taking one placeholder from the
   specification family (see `specifications/OMVA-000-philosophy.md`) and
   writing a real first draft, if it's your area of expertise.
4. **Machine-readable schemas** — turning the YAML examples in the spec
   into actual validated JSON Schema / YAML Schema files in `schemas/`.

## What NOT to do

- Don't treat any interface dimension, connector spec, or tolerance in this
  repo as final. Everything is a placeholder until validated by qualified
  engineering analysis and testing.
- Don't submit safety-critical claims without evidence. "Deterministic
  safety, AI-assisted diagnosis" (see OMVA-000 §Safety Posture) is a hard
  requirement of this project, not a suggestion.

## How

Open an issue for discussion before a large PR. For small corrections
(typos, broken links, formatting), a PR directly is fine.
