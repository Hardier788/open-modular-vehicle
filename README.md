# Open Modular Vehicle Architecture (OMVA)

**Status:** Draft 0.1 — Request for Comment
**Concept initiated by:** Rocky Hardie, with AI-assisted drafting
**License:** See [LICENSE.md](LICENSE.md)

## What this is

OMVA is a proposed open standard for automobile interfaces — mechanical, electrical,
data, and diagnostic — so that major vehicle subsystems (power module, suspension
corners, etc.) can be designed, manufactured, diagnosed, and replaced independently
of any single vehicle maker, the way USB, PCIe, and ATX let independent companies
build interoperable computer components.

The goal is not to design a car. It's to design the sockets a car plugs into, so
that repair, upgrade, and long-term serviceability stop being controlled by a
single manufacturer's parts monopoly.

## What this is not

- **Not a certified safety standard.** Nothing here has been validated by
  qualified engineering analysis, physical testing, or a regulatory body.
  Treat every number and interface definition as a *starting proposal*, not
  an approved spec.
- **Not a finished product or a company.** This is a published concept
  framework, released for engineers, researchers, universities, and the
  right-to-repair / open-hardware community to critique, fork, and build on.
- **Not a claim that this is easy.** The hardest problems here are not
  mechanical — they're liability, certification, and crash-structure
  integration. See `specifications/OMVA-000-philosophy.md` for an explicit
  discussion of why this doesn't already exist.

## Why publish this at all

Every open interface standard that succeeded (USB, PCIe, HTTP) started as a
document with no hardware behind it, put in front of the people who could
eventually build the hardware. This repo is that document. If it's useful to
you — as a researcher, a student project, an automaker's advanced-concepts
group, a right-to-repair organization, or someone smarter than the person
who started it — take it and run.

This has been tried once before. OSVehicle's Tabby (2013) was a genuinely
open modular vehicle chassis — then it got bought up, turned into a
$12,000+ single-vendor commercial product, and nothing has happened with
open modular vehicles since. See `specifications/OMVA-000-philosophy.md`
§3–§5 for the full story and for OMVA's actual structural answer to it
(a foundation that can't be sold, copyleft licensing with real teeth, a
certification mark, a patent non-assertion pool) — not a promise to stay
open, but a design that can't be un-opened without every one of those
pieces failing at once.

## Structure

```
specifications/   The numbered OMVA-### spec documents (human-readable)
schemas/           Machine-readable schemas (YAML/JSON) for manifests and APIs
reference-designs/ Non-normative example implementations
tests/conformance/ Conformance test stubs
CONTRIBUTING.md    How to propose changes
```

## Current state

Only `OMVA-000` (philosophy and scope) is drafted in detail. Everything else
listed in OMVA-000's specification family table is a placeholder waiting for
someone with the right domain expertise — mechanical, electrical,
automotive-cybersecurity, regulatory — to take it on.

## How to engage

Open an issue or PR. If you're a domain expert in any one area (suspension
design, automotive networking, functional safety / ISO 26262, materials,
regulatory certification), your critique of the relevant OMVA-### section is
more valuable right now than new material — this needs to survive contact
with people who actually know where it's wrong.
