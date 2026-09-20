# OMVA-100 — Mechanical Interface Architecture

**Status:** Draft 0.1 — placeholder for domain review
**Not a validated vehicle safety standard.**

## 1. Purpose

Defines the shared mechanical alignment and mating architecture that every
OMVA module family (OMVA-110 power, OMVA-115 energy storage, OMVA-130/140
corners, OMVA-150 steering) uses to physically locate and secure itself to
the chassis, so that alignment strategy is specified once, here, instead of
reinvented per module.

## 2. Self-Aligning Guide System

Every module interface uses a mechanical alignment system before any
electrical, fluid, or data connection is permitted to engage, based on
guide-pin/bushing practice already proven in high-precision manufacturing
tooling (injection mold guide pins and bushings solve an identical
alignment problem, at similar or tighter tolerances, over very large
numbers of repeated mating cycles — actual mold service life varies too
much by tooling class, materials, maintenance, and load to put a specific
figure like "millions" in a standards document; OMVA should define its own
validated requirement rather than borrow an implied number from a
different industry, e.g.:

```text
OMVA Docking Class D3 (illustrative — not a validated requirement)
Minimum validation:        25,000 mating cycles
Allowable locator wear:    < X μm
Maximum positional
  degradation:              < Y mm
```

- **Guide pins lead, and mate first.** The mechanical guide system fully
  aligns and seats the module before any functional connector engages.
  Where electrical safety requires it, protective-ground and interlock
  contacts may additionally use first-mate/last-break contact geometry —
  but that term describes electrical contact sequencing specifically, not
  the mechanical guide system as a whole, and this document shouldn't
  conflate the two.
- **Two identical round locating pins overconstrain the interface.**
  Standard fixture-design logic, not a detail to skip: two tightly-fitted
  round pins fight each other under manufacturing tolerance, chassis
  distortion, thermal expansion, coating thickness, or ordinary wear — the
  second pin binds instead of locating. The correct architecture separates
  the six degrees of freedom instead of forcing two pins to jointly resolve
  all of them:
  - **Primary locator** — round tapered pin, fixes X/Y position.
  - **Secondary locator** — diamond pin (or a relieved/slotted pin), fixes
    rotation while deliberately allowing tolerance along one axis, so it
    can't fight the primary locator.
  - **Datum surface** — hardened seating pads, fix Z position and angular
    attitude.
  - **Locking system** — cam, wedge, or captive fastener, applies preload
    only after alignment is complete.
  This is the classic round-pin-plus-diamond-pin scheme from precision
  fixturing, and it's what lets the interface constrain all six degrees of
  freedom without fighting itself.
- **Hardened, replaceable locator cartridges — not a bushing pressed
  straight into the chassis.** A steel bushing pressed directly into an
  aluminum chassis structure, exposed to water, road salt, humidity, and
  thermal cycling, is a galvanic-corrosion problem waiting to happen if the
  long-life chassis platform uses aluminum (a real possibility given the
  weight goals in OMVA-000). The fix is a small replaceable cartridge at
  each locating point — corrosion isolation layer, hardened bushing, datum
  surface, and a wear indicator — pressed into a structural mounting boss.
  A technician replaces the whole precision cartridge as a unit, which is a
  cleaner service operation than replacing a bare bushing and solves the
  corrosion problem at the same time.
- **Orientation-proofing (poka-yoke) by design, not by label.** The
  primary/secondary locator asymmetry described above doing double duty:
  spacing and diameter are chosen so incorrect orientation is physically
  impossible to mate, not merely discouraged by a sticker or a manual.
  This matters most where reversed or rotated installation would be a
  safety issue rather than a simple malfunction (corner modules and
  steering interfaces in particular — see OMVA-130/140/150).
- **Tapered leads.** Guide pin tips are conical/tapered, not flat, so
  minor approach misalignment self-corrects during insertion rather than
  binding or requiring the installer (human or robotic) to achieve
  near-perfect alignment before contact.

## 3. Docking Sequence

Five physical zones, in order, cover the full mate operation from approach
to verified connection. This sequence is worth treating as a named
principle in its own right — it's what "self-aligning" actually consists
of, staged so nothing delicate is ever asked to do a job it isn't built
for:

**Support → Capture → Align → Seat → Lock → Connect → Verify**

1. **Load support.** The module's weight is carried by rails, rollers, or
   a lift cart/robot at all times — never by the alignment pins. A 300 kg
   power cassette should never be hanging from its guide pins, even
   momentarily.
2. **Coarse capture.** Funnel-shaped lead-in geometry gets the module
   roughly located (on the order of ±10–20 mm) as it's pushed or driven
   toward the bay. Nothing precision-fitted is anywhere near contact yet.
3. **Precision alignment.** The hardened round and diamond locators
   (§2) engage and progressively resolve the remaining misalignment down
   to final seating tolerance. The exact progression and final tolerance
   are engineering questions for a later draft, not values to assume here.
4. **Structural seating.** The module reaches the datum pads, which — not
   the guide pins — define final location and carry operational loads.
   Guide pins align; datum surfaces carry load. Cams, wedges, or captive
   bolts then apply preload.
5. **Utility mating.** Only now do HV power, LV power, network (CAN/
   Ethernet), coolant, refrigerant, hydraulic, fuel, and exhaust
   connections mate, followed by a software verification pass confirming
   the module is correctly seated and identified before it's released to
   service.

## 4. Same Interface for Humans and Robots

Good self-alignment is what keeps this architecture from becoming
dependent on robotic vision systems — a human pushing a module cart
through guide rails and a robot arm or AGV doing the same motion both go
through the identical sequence in §3: support, capture, align, seat, lock,
connect, verify. The robot does not get a privileged or different
interface. This is a hard requirement, not a nicety — an interface that
only self-aligns reliably under robotic vision guidance quietly becomes an
interface that only works in someone's proprietary automated service
network, which defeats the manual-operable baseline principle in OMVA-000
as surely as never solving self-alignment at all would.

## 5. Interface-Level Health Monitoring

Because every docking interface is now a defined, instrumentable assembly
(locator cartridge, datum pads, lock, connectors), it can report its own
condition through the same vehicle-health architecture that monitors
propulsion and corner modules (OMVA-600 series) — swap-cycle count,
locator wear, lock preload, connector cycle count, alignment offset from
nominal. This extends predictive maintenance to the interface itself, not
just the modules it connects.

## 6. Why This Matters for Both Service Tiers

This directly supports the manual-operable baseline principle in OMVA-000:
a self-aligning, orientation-proofed guide system is what makes a hand-tool
swap by an independent technician actually reliable — without it, "repair
by substitution" depends on either expert-level manual precision or
robotic vision-guided alignment, which would quietly push all real-world
servicing toward automated bays (see OMVA-000 §"Manual-operable baseline").
Good guide-pin design is therefore not a manufacturing nicety — it's a
prerequisite for the framework's cottage-industry and independent-repair
goals to actually work outside a robotic service center.

## 7. Future Decomposition

OMVA-100 stays the umbrella document. As the technical detail in each area
matures, it should split into focused sub-documents rather than growing
one file indefinitely:

| ID | Title |
|---|---|
| OMVA-101 | Datum & Coordinate System |
| OMVA-102 | Module Envelope Classes |
| OMVA-103 | Structural Load Interfaces |
| OMVA-104 | Guide Rails & Coarse Capture |
| OMVA-105 | Precision Docking & Alignment |
| OMVA-106 | Module Locking & Preload |
| OMVA-107 | Utility Blind-Mate Interfaces |
| OMVA-108 | Service Handling Equipment |
| OMVA-109 | Mechanical Conformance Testing |

## 8. Open Questions for a Real Draft

- Pin/bushing material spec (hardened tool steel grade, surface treatment)
  and expected service-cycle life before locator cartridge replacement
- Standard pin diameter/spacing classes per module weight and precision
  class (a corner module's alignment tolerance needs are different from a
  low-voltage electronics cassette's)
- Corrosion isolation material and method for the locator cartridge on an
  aluminum chassis

## 9. The Central Technical Challenge

Worth stating plainly, because it's what separates this from a modular-car
sketch and makes it an actual standard: if one company builds a chassis in
one country and an independent company builds a power module in another
country, years apart, having never coordinated with each other, they still
have to mate — to the tolerances in §3, with zero adjustment at
install time. That tolerance-stack problem across independently
manufactured, independently toleranced parts is harder than any single
number in this document, and it's the open question a real engineering
draft has to answer before anything here is buildable.
