# OMVA-000 — Philosophy and Design Principles

**Status:** Draft 0.1 — Request for Comment
**Not a validated vehicle safety standard.**

## 1. Executive Concept

OMVA proposes a different way to think about the automobile: not as a
tightly integrated product that becomes increasingly expensive to repair as
it ages, but as a durable platform built around standardized, replaceable
modules.

The design objective is not to make a vehicle that never fails. The
objective is to make failures predictable, serviceable, inexpensive, and
minimally disruptive. A failed module should be removable from the vehicle
quickly, replaced with a known-good module, and rebuilt later on a
workbench or at a remanufacturing center.

## 2. Scope and Non-Goals

**In scope:**
- Interface standards (mechanical, electrical, data, diagnostic) that let
  independently manufactured modules interoperate.
- Machine-readable specification formats so tooling can check compatibility.
- A vehicle-health / predictive-maintenance data architecture built on top
  of those interfaces.

**Explicitly out of scope, at this stage:**
- Designing, certifying, or building an actual roadgoing vehicle.
- Defining final dimensions, tolerances, or load ratings for any interface.
  Every number in this repo is a placeholder pending real engineering
  analysis.
- Solving regulatory type-approval. OMVA can describe what a module-level
  certification regime *could* look like, but it cannot grant certification,
  and no vehicle should be built to this standard and treated as compliant
  with FMVSS, UNECE, or any other regulatory framework without independent
  validation.

This distinction matters: OMVA is trying to be a *starting reference point*
for people with the resources to do the real engineering, not a shortcut
around that engineering.

## 3. Why This Doesn't Already Exist

Worth stating plainly, because it's the honest answer to "why hasn't a
major automaker done this": the primary obstacles are not mechanical, they
are legal and structural.

- **Liability.** A vehicle manufacturer is strictly liable for the vehicle
  as an integrated system. If a third-party module built to an open
  interface standard fails and causes injury, there is currently no
  established legal framework analogous to "the module conformed to
  OMVA-130" as a liability shield. Any real-world path forward has to solve
  this, not route around it — likely through some combination of
  module-level certification (closer to how aftermarket trailer hitches or
  child car seats are certified independently) and clear allocation of
  liability to the module manufacturer rather than the chassis
  manufacturer.
- **Crash structure.** Engine bays, suspension mounting points, and similar
  attachment zones are not just brackets — they are tuned load paths for
  crash energy management. A genuinely swappable interface at these points
  has to reliably transfer crash loads the same way across independently
  manufactured modules, accounting for tolerance stacking between suppliers
  who never coordinate directly. This is a harder problem than the
  connector and coupling geometry, and it is the part of this framework
  most in need of real structural-engineering scrutiny.
- **Business incentive.** Proprietary parts and service are a revenue
  stream automakers have no commercial reason to give up voluntarily. This
  framework assumes the pressure to open up will come from outside the
  incumbent industry — right-to-repair regulation, independent module
  manufacturers, universities, and distributed/additive manufacturing
  communities — not from within it.

Prior partial attempts worth knowing about, so this framework can build on
them rather than repeat them: OBD-II already standardizes read access to
vehicle diagnostics (the "open access" principle below is partly already
law in some jurisdictions). This idea has been tried before, and it's
important to be honest about exactly how it failed rather than pretend
OMVA is starting from nothing. The clearest precedent is OSVehicle's
**Tabby** (launched 2013, Italy/Shenzhen): a genuinely open chassis
released under a CC BY-SA license, assembled in under 45 minutes,
configurable as a 2-seat or 4-seat vehicle with a swappable ICE, hybrid,
or electric drivetrain in the same frame — real, citable prior art for the
power/energy-storage split in §4. What happened to it afterward is the
more important lesson, and it's worth being specific rather than vague
about the difference: the 2017 successor, Tabby EVO, sells for $12,000 for
the platform alone (or $17,500 with a modest 12.8 kWh battery pack), sold
by OSVehicle (rebranded Open Motors) as a single-vendor R&D product aimed
at funded startups developing *new* EVs faster — not at repairing vehicles
people already own, and not as an interface other independent
manufacturers can build competing, compatible modules against. In plain
terms: a company bought the open idea, closed it, and effectively shelved
it as a mass-market open standard — and nothing has happened with open
modular vehicles in the twelve years since, precisely because of that.
"Open specifications, one vendor selling the hardware" is not the same
claim as "open standard, many manufacturers building interoperable
parts," and Tabby's trajectory is the clearest evidence available that the
former doesn't become the latter on its own — it becomes a commercial
product instead, and then it stalls, because a single company's roadmap
and funding cycle is now the whole ecosystem's ceiling. §5 below is
OMVA's answer to why that specific failure shouldn't repeat here. Various
other EV "skateboard" platforms (REE Automotive, Canoo) have explored
pieces of the same modularity, generally without achieving a genuinely
open, multi-manufacturer interface standard either.

## 4. AI as the Democratizing Layer

The reason this is worth trying again now, and not just a repeat of
Tabby's attempt, is that the tooling available to an individual designer
has changed. Tabby in 2013 was open blueprints — you still needed real
mechanical engineering skill to design a new compliant part from scratch.
The published OMVA interface specifications (mechanical envelopes, guide
geometry, electrical pin-outs, data protocols — see OMVA-100 and the
OMVA-200 series) function like a published API: fixed inputs and outputs,
with the internal implementation left open. With AI-assisted design tools,
an individual engineer, a small shop, or a home hobbyist can design,
simulate, and validate a new module against that published interface
without needing an automaker's engineering department behind them —
plug-in solutions, in the literal sense. This doesn't remove the need for
real validation before anything safety-critical ships (OMVA-000 §8 still
governs that), but it moves the *starting point* for who can attempt to
build a compliant part from "a company with an R&D budget" to "anyone with
the spec and access to AI-assisted design tools." That shift, more than
any single technical decision in this document, is what makes trying this
again in 2026 different from trying it again in 2013.

## 5. Governance: Structurally Uncapturable, Not Just Intentionally Open

Tabby didn't fail because anyone acted in bad faith. It failed because
nothing structurally prevented a single company's commercial incentives
from becoming the whole project's ceiling once ownership sat in one place.
"We intend to stay open" is not a defense against that; a foundation with
no owner, a license with teeth, and a mark nobody can privatize are. This
governance model isn't about keeping any particular kind of company out —
a small independent shop and a large Tier 1 supplier should both be able
to build modules to the open interface, and having large manufacturers
participate is a *win* for parts availability, not a threat. What has to
be structurally impossible is any single entity — corporate, nonprofit, or
individual — coming to own the standard itself the way OSVehicle owned
Tabby.

- **A foundation, not a company or a person, holds the standard.** Modeled
  on how the Linux Foundation holds Linux: a nonprofit whose charter is
  legally bound to keep the specification open cannot be acquired, sold,
  or quietly folded into a product line the way a company can. Even if
  every individual involved today walked away, the standard itself
  wouldn't move with them.
- **Strong copyleft licensing does the enforcement work, not litigation.**
  CERN-OHL-S (already the recommended hardware license in this repo)
  legally requires that anything built on OMVA's hardware designs stays
  open — a derivative can't be closed off and resold as proprietary. This
  is the actual mechanism that prevents a Tabby-style enclosure; it
  doesn't rely on anyone suing anyone.
- **A certification mark, kept separate from the specification itself.**
  Anyone can build to the open interface — that's the entire point — but
  only conformance-tested implementations may call themselves
  "OMVA-Certified." Enforcing a trademark against misuse is cheap and fast
  compared to patent litigation, and a foundation with even a handful of
  active members can do it.
- **A patent non-assertion pool among contributors**, on the model of the
  Open Invention Network that protects Linux. Contributors agree upfront
  not to use patents against the ecosystem or each other — this closes
  off the specific risk of someone inside the community later trying to
  enclose a piece of it from within.

Together, these are the difference between "we hope this stays open" and
"this cannot be un-opened without every one of these structures failing at
once." That's the actual, buildable answer to what happened to Tabby.

## 6. Power Conversion vs. Energy Storage Are Separate Interfaces

Earlier drafts of this framework treated "power module" as a single slot
that an engine, a motor, or a battery would each occupy. That's wrong for
any vehicle that is a genuine hybrid, which needs both a power-conversion
device (engine and/or motor) and an energy-storage device (battery) present
at once — they aren't alternatives, they're two different interfaces that
happen to both be empty in some configurations and both filled in others.

OMVA therefore separates:

- **OMVA-110, Power Module** — the conversion device: ICE, electric drive
  unit, or combined hybrid unit.
- **OMVA-115, Energy Storage Module** — the storage device: 12/48V system,
  traction battery, or future storage technology.

The same two interfaces, differently populated, describe every propulsion
architecture:

| Configuration | Power module (OMVA-110) | Energy storage (OMVA-115) |
|---|---|---|
| ICE | Combustion engine | Small 12/48V system only |
| Hybrid | ICE + motor/generator | Small traction battery |
| Plug-in hybrid | ICE + motor/generator | Medium traction battery |
| Battery electric | Electric drive unit | Large traction battery |

This is closer to the original computer-rack analogy than a single
"propulsion slot" was: a server rack has a power-supply bay and a separate
drive bay, and different machines populate each bay differently. OMVA
should show the *same chassis* in these four configurations side by side —
that communicates the architecture faster than prose can.

## 7. Relationship to Existing Standards Work

OMVA should defer to and cross-reference existing standards rather than
re-deriving battery-swap and battery-service practice from scratch:

- **IEC 62840-1:2025** — "Electric vehicle battery swap system — Part 1:
  General and guidance" is already a published International Standard
  covering general requirements and interoperability guidance for battery
  swap systems. This is the most mature existing reference for OMVA-115's
  swap-interface work and should be the starting citation, not a
  from-scratch design.
- **ISO/AWI TR 25656** — "Electrically propelled road vehicles — Battery
  swap" is under development at ISO/TC 22/SC 37/WG 8. As of this draft it
  is at the Approved Work Item stage (drafting underway, not yet a
  Committee Draft) — worth tracking, not yet citable as settled guidance.
- **ISO/CD 18006-2** — "Battery information — Part 2: dismantling, safe
  repair, re-use and preparation for repurposing of EV modules and battery
  packs" is further along, at Committee Draft stage. Its scope — design and
  assembly techniques that facilitate maintenance, repair, re-use, and
  repurposing — overlaps directly with OMVA's serviceability and
  circularity goals (OMVA-500 series, OMVA-700) and should be the primary
  reference for the energy-storage module's rebuild/repurpose pathway
  rather than OMVA inventing its own.

Real-world precedent for fast, standardized physical module exchange
already exists at production scale: NIO's Power Swap Station 4.0 completes
an automated battery swap in 144 seconds, and the network passed 100
million cumulative swaps in February 2026. Worth being precise about what
that does and doesn't prove, though: NIO's stations serve NIO's own
sub-brands (Onvo, Firefly) plus a growing list of automakers (Changan,
Geely, SAIC-GM, XPeng, and others) who each negotiated bilateral technical
partnerships to interoperate with NIO's proprietary interface. It's strong
evidence that automated, fast, cross-manufacturer physical module exchange
is commercially and mechanically viable at scale — it is not evidence that
an *open, publicly governed* interface standard (any manufacturer can build
to it unilaterally, without a bilateral deal) yet exists anywhere in the
industry. That open-governance gap is precisely what OMVA is proposing to
fill.

## 8. Core Principles

- **Long-life platform.** The chassis and primary structural architecture
  should be designed for decades of service, while shorter-life subsystems
  are replaceable.
- **Standardize interfaces, not implementations.** Define mounting datums,
  envelopes, electrical interfaces, fluid couplings, communications,
  diagnostics, and safety behavior without dictating exactly how every
  manufacturer builds the internal component.
- **Repair by substitution.** Vehicle downtime is minimized by exchanging
  modules rather than performing long invasive repairs in the vehicle.
- **Open access.** Diagnostic information, interface specifications,
  service data, and module identification should be accessible to the
  vehicle owner and independent repairers.
- **Machine-readable specifications.** Every specification should exist in
  both human-readable and machine-readable form so software and AI systems
  can automatically evaluate compatibility and conformance.
- **Condition-aware operation.** The vehicle should continuously monitor
  its own systems, detect degradation, estimate remaining useful life, and
  schedule maintenance before failure.
- **Backward and forward compatibility.** A future engine, motor, battery,
  suspension, or controller should be able to fit an older vehicle when it
  conforms to the defined interface class.
- **Safety remains deterministic.** AI can predict and diagnose, but
  safety-critical functions require validated engineering limits,
  independent safety logic, and physical testing. AI is not the final
  engineering authority on any safety-critical value in this framework.
- **Manual-operable baseline.** Every module interface must be serviceable
  with hand tools by a trained independent technician within a reasonable
  time, full stop — robotic and automated service infrastructure (fast
  vision-guided swap bays, AGV-assisted module handling) is an optional
  accelerant for speed, precision, and scale, never a prerequisite for
  basic repairability. This is what keeps "repair by substitution" open to
  a driveway mechanic or a small independent shop and not just whoever owns
  an automated bay — the cottage-industry goal in OMVA-000 §1 only survives
  if this stays a hard requirement, not an aspiration.

## 9. Design for Low Mean Time to Repair

OMVA should explicitly optimize Mean Time to Repair (MTTR), not just Mean
Time Between Failures (MTBF). A component can be reliable and still create
unacceptable ownership cost if reaching it requires disassembling half the
vehicle.

## 10. Proposed OMVA Specification Family

Everything below OMVA-000 is currently a placeholder. If you have relevant
domain expertise, picking one of these up is the most useful contribution
you can make — see CONTRIBUTING.md.

| ID | Title |
|---|---|
| OMVA-000 | Philosophy and Design Principles (this document) |
| OMVA-001 | Terminology |
| OMVA-002 | Versioning and Compatibility |
| OMVA-003 | Module Identification and Manifest |
| OMVA-004 | Governance and Anti-Capture Model (foundation structure, licensing, certification mark, patent pool) |
| OMVA-100 | Mechanical Interface Architecture |
| OMVA-110 | Power Module Interface (ICE / motor / hybrid drive — power *conversion*) |
| OMVA-115 | Energy Storage Module Interface (battery / future storage — power *storage*) |
| OMVA-120 | Transmission / Drive Interface |
| OMVA-125 | Thermal Interface (cooling/heating loops shared across modules) |
| OMVA-130 | Front Corner Module |
| OMVA-140 | Rear Corner Module |
| OMVA-150 | Steering Interface |
| OMVA-160 | Body Shell Interface (structural safety cell + replaceable exterior shell) |
| OMVA-200 | Low-Voltage Electrical Architecture |
| OMVA-210 | Vehicle Communications Network |
| OMVA-220 | Module Discovery Protocol |
| OMVA-230 | Diagnostic Interface |
| OMVA-240 | Software / API Architecture |
| OMVA-250 | Software Update Architecture |
| OMVA-300 | Cooling / Fluid Interfaces |
| OMVA-310 | Fuel Interface |
| OMVA-320 | Brake Hydraulic Interface |
| OMVA-400 | Safety Architecture |
| OMVA-410 | Cybersecurity |
| OMVA-420 | Functional Safety |
| OMVA-500 | Serviceability Requirements |
| OMVA-510 | Module Replacement Procedures |
| OMVA-520 | Diagnostic Requirements |
| OMVA-600 | Vehicle Health Architecture |
| OMVA-610 | Sensor and Signal Requirements |
| OMVA-620 | Baseline / Machine Fingerprinting |
| OMVA-630 | Anomaly Detection |
| OMVA-640 | Fault Classification |
| OMVA-650 | Remaining Useful Life Estimation |
| OMVA-660 | Maintenance Planning |
| OMVA-670 | Vehicle Health API |
| OMVA-680 | Fleet Learning and Model Updates |
| OMVA-690 | Predictive-Maintenance Conformance Testing |

## 11. Practical Development Path

A new roadgoing automobile creates major regulatory, certification, crash,
emissions, cybersecurity, warranty, and liability burdens. This framework is
therefore meant to be developed in stages that don't require building or
certifying a vehicle:

1. Publish the architecture and RFC specifications.
2. Build software schemas, health APIs, and conformance tools.
3. Develop bench demonstrators of module discovery, diagnostics, and
   predictive maintenance.
4. Build a power-module or corner-module physical demonstrator.
5. Prove fast replacement and automatic module identification.
6. Demonstrate predictive maintenance with real vibration, acoustic, and
   electrical data.
7. Prototype in a lower-complexity vehicle class or experimental platform
   before attempting a fully certified passenger automobile.
8. Iterate the standard through public engineering review and measured
   test data.

## 12. The Central Proposition

OMVA combines two ideas that reinforce each other: modularity makes the
automobile easier and cheaper to repair, while AI makes failures less
surprising. The vehicle becomes a durable open platform whose components
can evolve over time rather than a tightly integrated object that must be
discarded when repair becomes uneconomic.
