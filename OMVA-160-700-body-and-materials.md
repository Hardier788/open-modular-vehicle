# OMVA-160 / OMVA-700 — Body Shell Interface and Materials Circularity

**Status:** Draft 0.1 — placeholder for domain review
**Not a validated vehicle safety standard.**

## 1. Structural Safety Cell vs. Replaceable Exterior Shell (OMVA-160)

An earlier draft of this section proposed a fully non-structural body
shell bolted to a chassis that alone carries all crash loads. That's not
defensible: modern vehicles deliberately use the passenger cell, A/B/C
pillars, roof rails, rockers, doors, and even bonded stationary glass as
part of the crash load path. Bonded windshields in particular contribute
measurably to body stiffness and help transfer roof-crush loads —
automotive structural repair guidance treats bonded glass as a structural
element, not decoration. Making the chassis carry 100% of crash loads alone
would mean substantially over-building it, which fights the "long-life,
lightweight-enough-to-be-viable" goal in OMVA-000's core principles.

OMVA-160 instead splits the vehicle into two zones with different
lifecycles:

- **Structural safety cell** (long-life, permanent, part of the
  certified crash structure): occupant cell, roof rails, A/B/C pillars,
  rockers, and the primary crash-load path. This is where certification
  burden concentrates, and it is *not* intended to be swapped or
  independently designed the way propulsion or corner modules are.
- **Replaceable exterior shell** (independently designable, swappable):
  fenders, hood, fascias, door skins, quarter skins, deck lid, trim,
  aerodynamic panels, and lighting assemblies. These sit outside the crash
  load path, which is what makes them genuinely open to independent
  design.

This still delivers the thing that makes the concept fun — a different
body style on the same vehicle years later — without the previous
version's implicit claim that the whole exterior can be replaced without
touching anything crash-relevant. The engineered safety cell stays with the
vehicle for its full service life; the exterior skin doesn't have to.

Open questions for a real OMVA-160 draft:
- Exact boundary between safety-cell structure and replaceable skin for a
  given vehicle class (this will vary — a rollover-rated pillar is safety
  cell; a fender is shell, but where exactly the line falls at the A-pillar
  base needs real structural analysis, not a guess)
- Mounting interface between exterior shell panels and the safety cell
- Pedestrian-safety and aerodynamic/NVH baseline requirements for
  independently designed shell panels so they don't compromise
  range/efficiency/comfort even though they aren't crash-structural

## 2. Materials and End-of-Life Circularity (OMVA-700 family, new)

Not present in the original draft — added because closed-loop material
recovery is a first-order design goal, not an afterthought. The governing
requirement, rather than assuming every material recycles the same way:

> Components shall identify material composition and an approved
> end-of-life recovery pathway.

Recovery pathways differ by material and need their own spec entries:

- **Aluminum, steel, copper** → remelt / reclaim via established metal
  recycling streams.
- **Non-safety-critical thermoplastics** (interior trim, HVAC ducting, body
  panels): mechanical recycling (grind and reprocess) using identifiable,
  sorted plastics. Requires material-ID marking on parts so end-of-life
  sorting is automatic, not manual.
- **Laminated safety glass (windshields):** NOT a simple grind-and-remelt
  case. Windshields are two glass layers bonded to a PVB (polyvinyl
  butyral) interlayer specifically so they don't shatter in a crash.
  Recovery requires de-lamination — mechanically separating glass from PVB
  — before either stream can be reprocessed. This is commercially proven;
  industrial processes exist today that mechanically separate windshield
  glass from PVB with both resulting streams suitable for reuse or
  remanufacturing (the glass into cullet, the PVB into applications like
  sound-dampening interlayers or carpet padding). It's a distinct process
  step OMVA needs to specify, not an assumption that "windshield = glass =
  remeltable."
- **Battery systems**: refurbish / repurpose / recycle, following
  ISO/CD 18006-2 ("Battery information — Part 2: dismantling, safe repair,
  re-use and preparation for repurposing") rather than an OMVA-invented
  process — see OMVA-000 §5.
- **Electronics**: component- and material-level recovery, consistent with
  existing e-waste recovery practice.
- **Structural/safety-critical materials** (chassis, corner-module
  castings, safety-cell structure): recyclability is desirable but must
  never compromise material traceability or certified-process requirements
  (see OMVA-000 core principle: "Safety remains deterministic"). A
  recycled input stream is fine; an untraceable one is not, for anything in
  the crash-load path.

## 3. Predictive Replacement, Not Just Predictive Detection

Extends OMVA-600 (Vehicle Health Architecture): the health system's output
isn't only a warning — it can trigger a module going out for rebuild
*before* failure, using the same swap-and-rebuild-on-a-bench flow OMVA-000
describes for reactive replacement. The rebuilt/refurbished module then
re-enters the supply pool. This turns the health-monitoring architecture
into a closed loop with the module-exchange architecture, rather than two
separate systems — worth stating explicitly in OMVA-600 rather than leaving
implicit.
