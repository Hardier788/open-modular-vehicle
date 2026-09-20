# Licensing

This repo mixes two kinds of content, and they need different licenses. Pick
the actual license text from the official sources below and drop the full
text into `LICENSE-DOCS` and `LICENSE-HARDWARE` before publishing — don't
just link to this file as the license, GitHub and most institutions want the
literal license text in the repo root.

## Specification documents and prose (`specifications/`, `README.md`, etc.)

Recommended: **CC BY 4.0** (Creative Commons Attribution 4.0)
- Official text: https://creativecommons.org/licenses/by/4.0/legalcode
- Why: it's the standard choice for open standards documents (W3C, IETF-adjacent
  projects, most open hardware philosophy docs use it). Anyone can copy,
  modify, and redistribute, including commercially, as long as they credit
  the origin. That's what you want — maximum reach, no gatekeeping.

## Reference hardware designs and schemas (`reference-designs/`, `schemas/`)

Recommended: **CERN-OHL-S v2** (CERN Open Hardware Licence — Strongly Reciprocal)
- Official text: https://ohwr.org/cern_ohl_s_v2.txt
- Why: it's purpose-built for open hardware (unlike CC licenses, which
  don't handle patent/manufacturing rights well) and the "strongly
  reciprocal" variant means derivative hardware designs must stay open too —
  which matters here, since the entire point is preventing re-enclosure by a
  single manufacturer.

## Code (conformance tests, schema validators, tooling)

Recommended: **Apache 2.0**
- Official text: https://www.apache.org/licenses/LICENSE-2.0
- Why: includes an explicit patent grant, which matters more for code than
  for documents, and is broadly trusted by companies and universities alike
  (lowers the barrier for a university lab or a corporate advanced-concepts
  team to actually touch this).

## Action needed before publishing

1. Copy the three license texts above into `LICENSE-DOCS`, `LICENSE-HARDWARE`,
   and `LICENSE-CODE`.
2. Reference them from this file and from each top-level directory's own
   short README if you add one.
3. If you ever want a lawyer to sanity-check one thing before publishing,
   make it this — license choice is the one part of this repo with real
   legal teeth.
