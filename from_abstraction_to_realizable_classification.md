# From Abstraction to Realizable Classification: Dependency, Coherence, Perturbation, and the Physical Cost of Stable Meaning

## Abstract

An abstraction is often described as a way of ignoring detail.

That description is incomplete.

A useful abstraction does not make lower-level detail disappear. It classifies many physically different states, trajectories, or organizations as equivalent relative to a selected architecture, task, or horizon.

The success of that classification depends on the lower-level world continuing to behave in ways that preserve the distinction.

A logical bit is not independent of charge, voltage, material structure, timing, temperature, noise, or radiation merely because an application refers only to `0` and `1`.

A virtual address is not independent of page tables, translation hardware, physical memory, kernel state, and processor execution merely because software does not name a physical memory cell directly.

A bank credit is not independent of ledgers, obligations, settlement systems, institutions, identity, law, computation, and material infrastructure merely because it is not a pile of currency.

A road is not independent of gravity, friction, molecular bonding, drainage, weather, thermal expansion, and maintenance merely because traffic engineering treats it as a route between locations.

The abstraction works only while the lower-level organization continues to realize the distinctions that the abstraction requires.

This yields the central sequence:

\[
\boxed{
\begin{aligned}
&\text{continuing lawful evolution}\\
&\rightarrow \text{recurring physical regularities}\\
&\rightarrow \text{physically realizable classifications}\\
&\rightarrow \text{equivalence classes and higher-level states}\\
&\rightarrow \text{architecture-relative operations and meanings}\\
&\rightarrow \text{perturbation, drift, detection, repair, or failure}.
\end{aligned}
}
\]

The framework developed here makes five related claims.

First:

> An abstraction is not the removal of physical dependence. It is the selective suppression of distinctions whose consequences remain negligible for a specified purpose.

Second:

> Every realized classification depends on the lower-level dynamics preserving its relevant class boundaries over a sufficient horizon.

Third:

> An organizer does not stand outside dependency. Every mechanism that classifies, isolates, repairs, or controls another organization is itself physically instantiated and dependency-bound.

Fourth:

> Robustness is often achieved not by eliminating dependency, but by introducing additional organized dependencies that detect, absorb, redirect, or repair perturbation.

Fifth:

> Small lower-level changes can acquire large higher-level significance when an architecture concentrates extensive semantic consequence into a narrow physical distinction.

A single deposited charge may become a bit flip.

A bit flip may reverse a sign.

A reversed sign may alter a control decision.

A control decision may redirect an entire process.

Nothing has escaped physical law.

The higher-level architecture has amplified a physically small distinction because its classification rules assign that distinction consequential meaning.

The central proposal is therefore:

\[
\boxed{
\text{An abstraction is a physically sustained classification of continuing variation.}
}
\]

And the practical principle is:

\[
\boxed{
\text{Ignoring a distinction is safe only while the realized architecture keeps that distinction inconsequential.}
}
\]

---

## 1. Abstraction Does Not Remove Reality

Suppose a system classifies a range of physical states as logical `0`.

It may ignore the exact positions, energies, and histories of individual particles.

But those particles do not cease to possess charge, momentum, energy, location, or interaction capacity.

The abstraction does not erase them.

It introduces a higher-level equivalence relation:

\[
x\sim_A y
\iff
\pi_A(x)=\pi_A(y),
\]

where \(\pi_A\) is a projection associated with architecture \(A\).

The statement

\[
\pi_A(x)=\pi_A(y)
\]

does not imply

\[
x=y.
\]

It means only that the architecture treats the relevant difference as insignificant for a selected purpose.

Thus:

```text
physical difference
not consequential under projection A
→ same higher-level classification
```

The lower-level difference remains physically present.

Its consequences are merely suppressed, absorbed, delayed, or rendered irrelevant within the operating region of the architecture.

---

## 2. Classification Is Not Arbitrary Realization

Mathematically, one may define almost any partition of a state space.

Physically, not every partition is stably realizable.

Suppose a designer declares:

```text
all voltages from 0.0 V to 0.8 V = logical 0
all voltages from 2.0 V to 3.3 V = logical 1
```

The declaration alone does not make the classification reliable.

Its realization depends on:

```text
transistor transfer characteristics
noise margins
supply stability
temperature
material integrity
timing
fan-out
manufacturing variation
radiation environment
```

A classification becomes operationally meaningful only when lower-level dynamics preserve its boundaries sufficiently well.

Let \(B_0\) and \(B_1\) be two physical regions representing logical states.

A useful digital architecture requires more than their formal definition.

It requires that relevant transformations satisfy something like:

\[
x\in B_a
\Longrightarrow
F(x)\in B_{f(a)}
\]

for sufficiently many admissible \(x\), disturbances, and trajectories.

The abstraction is therefore not merely selected.

It is realized.

---

## 3. Realizable Classification

A classification is realizable when a physical organization makes it possible to:

```text
identify classes
preserve class separation
transform members predictably
recover from bounded deviation
expose class membership through an interface
```

Let:

\[
\pi_A:X\rightarrow S_A\cup\{\bot\}
\]

map lower-level states into higher-level states \(S_A\), with \(\bot\) representing invalid, indeterminate, or unrealized states.

A realization region may be written:

\[
R_A=\{x\in X:\pi_A(x)\neq\bot\}.
\]

The architecture is realized only while physical trajectories remain sufficiently compatible with this map.

A disturbance need not destroy matter in order to destroy a classification.

It may merely move a state from one class to another, or into the invalid region:

\[
x\in B_0
\rightarrow
x'\in B_1,
\]

or:

\[
x\in B_0
\rightarrow
x'\in B_\bot.
\]

At the physical level, lawful interaction continues.

At the architectural level, a bit has flipped or become unreadable.

---

## 4. Classification Strength

Not all classifications are equally robust.

A classification is strong relative to a disturbance class when many lower-level variations fail to change the higher-level result.

Let \(D\) be a set of disturbances.

A simple robustness condition is:

\[
\pi_A(d(x))=\pi_A(x)
\]

for relevant \(x\in R_A\) and \(d\in D\).

The larger the disturbance set under which this equality continues to hold, the stronger the classification is relative to that disturbance model.

Classification strength may depend on:

```text
margin between classes
restorative dynamics
redundancy
detection capacity
repair capacity
temporal horizon
resource availability
```

A bit stored for one nanosecond under laboratory conditions may be robust.

The same bit stored for ten years in a radiation-rich environment may not be.

Robustness is therefore architecture-, disturbance-, and horizon-relative:

\[
\operatorname{Robust}(A,D,H).
\]

---

## 5. Every Ignored Difference Is a Conditional Irrelevance

When an architecture ignores a lower-level distinction, it does not declare that distinction nonexistent.

It declares, explicitly or implicitly:

> Variations along this dimension will not materially alter the higher-level result within the relevant operating region and horizon.

For example:

```text
exact electron positions
→ ignored by the application

exact physical RAM frame
→ ignored by a process using virtual memory

exact serial number of a banknote
→ ignored by an account balance

exact aggregate grain arrangement
→ ignored by a road map
```

Each ignored distinction is only conditionally irrelevant.

If enough charge moves, the bit changes.

If the page mapping changes, the virtual address resolves elsewhere.

If institutional settlement fails, the bank balance loses practical force.

If the road surface collapses, the route no longer supports passage.

Thus:

\[
\boxed{
\text{Abstraction suppresses consequences, not existence.}
}
\]

---

## 6. A Bit Depends on the Charges It Does Not Name

A program ordinarily does not identify individual electrons.

Nevertheless, its continued operation depends on physical charge distributions remaining inside the regions that realize its logical states.

This does not mean that every individual electron is equally critical.

One electron may be displaced without changing the logical classification.

Many microstates belong to the same bit class.

But the architecture still depends on the collective charge organization.

The relevant relation is not:

```text
application
→ one privileged electron
```

It is closer to:

```text
application state
→ logical bit pattern
→ stable voltage and charge regions
→ semiconductor behavior
→ interacting matter and fields
```

The application does not depend on tracking each particle.

It depends on the ensemble remaining within a class-preserving region.

This distinction is essential:

> Not every lower-level constituent must be individually identified for the higher-level organization to depend on their collective behavior.

---

## 7. Cosmic Radiation as a Classification Perturbation

Cosmic radiation matters because energetic particles can deposit charge or generate secondary particles in electronic material.

A sufficiently consequential perturbation may change the state of a storage element.

The physical sequence is approximately:

```text
energetic particle
→ interaction with material
→ local ionization or charge deposition
→ altered electrical state
→ threshold crossing
→ changed logical classification
```

Nothing about this event contradicts digital logic.

Digital logic is realized only within a region where ordinary physical variation remains class-preserving.

The radiation event may move the physical state across a class boundary.

Then:

```text
physical charge perturbation
→ architecture-relative bit flip
```

The phrase `bit flip` is already a higher-level interpretation of the physical event.

At the lower level, charges and fields changed.

At the logical level, `0` became `1` or `1` became `0`.

---

## 8. Small Physical Change, Large Semantic Change

Suppose an integer is represented in a fixed-width binary format.

A single bit may be interpreted as a sign bit.

Then:

```text
00000001
```

may represent a positive value, while:

```text
10000001
```

may represent a negative value under a selected encoding.

The physical difference may be localized to one storage element.

The semantic difference may be enormous.

The higher-level propagation may be:

```text
charge disturbance
→ bit flip
→ sign reversal
→ altered arithmetic
→ changed branch condition
→ changed control path
→ incorrect output or system failure
```

The first event is physically small relative to the entire machine.

The later consequence is large because the architecture has assigned high semantic significance to that physical distinction.

Thus:

\[
\boxed{
\text{Semantic magnitude need not track physical magnitude.}
}
\]

The architecture supplies the amplification path.

---

## 9. Meaning Is Concentrated into Narrow Physical Distinctions

A logical architecture compresses extensive semantic consequence into small physical differences.

A single bit may determine:

```text
sign
permission
branch direction
validity
ownership
pointer interpretation
transaction status
control mode
```

This concentration is useful because it allows efficient storage and control.

It also creates potential fragility.

A narrow physical distinction may support a broad higher-level consequence.

Formally, if many higher-level continuations depend on state component \(b\), then a small perturbation to the realization of \(b\) may alter a large region of reachable architecture-relative trajectories.

The significance does not reside in the particle alone.

It resides in the dependency organization through which the particle-level perturbation becomes a higher-level distinction.

---

## 10. Error Correction Adds Dependency

Without correction:

```text
physical perturbation
→ changed bit
→ changed program state
```

With error correction:

```text
physical perturbation
→ changed encoded bit
→ redundant relation violated
→ syndrome detected
→ correction applied
→ original logical state restored
```

The robust architecture contains more structure:

```text
additional bits
encoding relations
checking logic
decoding logic
repair procedures
timing assumptions
power and material requirements
```

Robustness was not achieved by making the system independent.

It was achieved by adding organized dependencies whose interactions preserve a selected classification.

Thus:

\[
\boxed{
\text{Robustness often increases structural dependency while reducing failure sensitivity.}
}
\]

This is not a contradiction.

The architecture becomes dependent on more components and relations, but less vulnerable to a selected class of disturbances.

---

## 11. More Dependency Can Mean Less Fragility

Dependency count and fragility are not equivalent.

A system with one realization path may be structurally simple but brittle.

A system with several coordinated realization paths may be structurally complex but resilient.

For example:

```text
single storage copy
→ one disturbance may destroy the state
```

while:

```text
multiple encoded copies
→ one disturbance may be detected and repaired
```

The second system has more dependencies:

```text
replicas
comparison rules
quorum rules
repair channels
synchronization
```

But those dependencies create alternative continuation paths.

The relevant question is therefore not:

> How many dependencies exist?

It is:

> How are dependencies organized relative to disturbance, repair, and continuation?

---

## 12. Redundancy Is Projection-Relative Equivalence

Two stores may both provide food.

Relative to the projection:

```text
can obtain sufficient food
```

they may be treated as redundant.

But the stores are not physically identical.

They may differ in:

```text
suppliers
location
inventory
staff
power source
transportation links
prices
legal ownership
weather exposure
```

Redundancy therefore means:

> Two or more realized dependency paths are sufficiently equivalent relative to a selected capability, disturbance model, and horizon.

It does not mean that one path is unreal or independent of physics.

Each path must itself exist.

Each path must itself be maintained.

A redundant alternative is not outside dependency.

It is another dependency organization capable of realizing the same higher-level classification.

---

## 13. Virtual Memory Is a Maintained Classification and Translation Structure

A virtual address is not a fictional address.

It is an address interpreted through an architecture-defined translation relation.

A simplified path is:

```text
virtual address
→ virtual page number and offset
→ translation state
→ physical frame and offset
→ physical memory access
```

The page table is ordinarily stored in memory, while processor mechanisms such as the memory-management unit and translation caches participate in using it.

The virtual address is meaningful only because the system maintains relations among:

```text
process identity
address-space state
page-table entries
permissions
physical frames
translation hardware
kernel procedures
```

Virtual memory does not remove physical addresses.

It reorganizes them.

It allows many processes to use similarly shaped address spaces while mapping them onto different physical locations.

The abstraction depends on translation correctness, permission enforcement, memory availability, and lower-level hardware behavior.

---

## 14. Pages Are Operational Groupings, Not Fundamental Objects

A memory page groups many addresses into a unit of translation, protection, allocation, and transfer.

The page is not merely a convenient name.

It is a unit realized by architecture and operating-system rules.

Pages are useful because managing every byte through independent mapping metadata would generally be too expensive.

Grouping addresses reduces management cost.

But the grouping also introduces consequences:

```text
internal fragmentation
page-fault granularity
protection granularity
translation-cache behavior
copy-on-write behavior
replacement policy
```

The page therefore represents a tradeoff.

It suppresses some distinctions among addresses while making page-level distinctions consequential.

The abstraction is not arbitrary because hardware and software must jointly realize the grouping.

---

## 15. The Page Does Not Replace the Bytes

A page remains composed of addressable storage locations.

The page abstraction does not eliminate byte-level variation.

It classifies a range of addresses as sharing selected properties:

```text
mapping
permissions
residency state
ownership context
replacement status
```

A byte within the page may still change independently.

A fault may affect one part of the page.

A protection rule may apply to the entire page.

Thus two projections coexist:

```text
byte-level state
page-level management state
```

Neither projection fully replaces the other.

Each exposes different consequential distinctions.

---

## 16. Bank Credit Is a Realized Relational State

A bank credit is not a physical object stored in a box.

It is a maintained state within a network of obligations, records, identities, institutional rules, and settlement capacities.

A simplified dependency structure may include:

```text
account identity
ledger entries
bank liabilities
payment rules
legal recognition
settlement systems
institutional continuity
computational infrastructure
material infrastructure
```

The credit is neither imaginary nor independent of its realization.

It is real as an architecture-relative capability and obligation.

For example, it may enable:

```text
payment
withdrawal
transfer
collateralization
accounting recognition
```

If the supporting institutional and computational relations cease to hold, the credit does not remain as an isolated hidden substance.

The higher-level financial state is no longer realized in the same way.

---

## 17. A Higher-Level Entity May Be a Maintained Relation

Some entities are misleadingly described as objects that merely possess dependencies.

In many cases, the entity is better understood as a stabilized organization of relations.

Examples include:

```text
virtual address space
bank credit
legal contract
software process
institutional office
Git branch
network session
```

A virtual address space is constituted by maintained translation and protection relations.

A bank credit is constituted by maintained accounting and obligation relations.

A legal office is constituted by recognized authority, procedure, role, and institutional continuity.

Remove enough of the constitutive relation and there is no independent higher-level object remaining with some supports missing.

The object was the organized relation.

---

## 18. Language Is Not an Alphabet with Additions

An alphabet alone does not realize a language.

Language depends on organized relations among:

```text
phonetic distinctions
writing conventions
grammar
lexicon
pragmatics
shared histories
speakers and interpreters
learning and memory
social transmission
physical expression
```

Letters may be concatenated without producing a meaningful utterance.

A program may be assembled from valid characters while violating syntax, type rules, semantics, or execution requirements.

Thus:

```text
symbols
not sufficient for
language or program
```

The higher-level organization depends on relations among symbols, not merely their presence.

The same physical mark may mean different things under different architectures.

Meaning is realized through classification plus context plus transformation rules.

---

## 19. Operations Are Also Instantiated

A mechanism that repairs, classifies, isolates, or controls another mechanism is not outside the system of dependence.

For example, an error-correcting decoder depends on:

```text
physical gates
stored check bits
correct timing
available power
sound encoding rules
sufficient fault assumptions
```

A memory manager depends on:

```text
processor execution
kernel state
page-table integrity
interrupt handling
storage and memory
```

A bank auditor depends on:

```text
records
access rights
institutional authority
procedures
communication
human or computational interpretation
```

There is no dependency-free manager.

Every organizer is itself organized.

Every corrective operation is another realized trajectory.

---

## 20. There Is No External Platform of Pure Control

It is tempting to picture an architecture as standing above the physical system and directing it.

But the architecture is itself realized within continuing physical interaction.

A controller measures through physical channels.

It computes through physical transitions.

It acts through physical forces.

It stores goals through physical states.

It may fail through physical perturbation.

Thus:

\[
\boxed{
\text{Control is dependency-bound intervention from within the dependency structure.}
}
\]

The controller can reorganize available paths.

It cannot operate from outside lawful evolution.

---

## 21. The Recursive Dependency Principle

Suppose architecture \(A\) is maintained by organizer \(K\).

Then \(K\) is itself an architecture with a realization basis.

This produces a recursive pattern:

```text
higher-level state
→ maintained by organizer
→ organizer realized by lower-level states
→ lower-level states maintained by further regularities
```

The recursion does not imply an infinite sequence of identical explanatory levels.

It means that no higher-level mechanism becomes dependency-free merely because it organizes another level.

The relation may terminate analytically at a selected physical description, but not in an uninstantiated operation.

---

## 22. Dependency Is Not an Optional Attachment

A common picture begins with an independent object and then adds relations to it.

For many organized systems, this is misleading.

A process without executable state, memory relations, scheduling, and machine realization is not the same process in an isolated form.

A road without material continuity, geometry, support, friction, and accessibility is not a pure road stripped of dependencies.

A credit without ledger, obligation, identity, and institutional recognition is not a pure credit awaiting implementation.

The dependency structure is not merely attached to the realized entity.

It participates in making that entity the kind of entity it is.

---

## 23. Minimal Sufficiency and Robust Sufficiency

A minimally sufficient realization contains enough organized relation to produce a selected capability.

Let \(D_A\) be a dependency structure for architecture \(A\).

A subset \(D_{\min}\subseteq D_A\) is minimally sufficient relative to capability \(C\) when:

```text
D_min realizes C
and
removing any required element from D_min prevents C
```

But minimal sufficiency is not the same as desirable design.

A minimally sufficient structure may have no repair path.

A robustly sufficient structure may include:

```text
redundancy
monitoring
fallback
error correction
isolation
reconfiguration
maintenance
```

Thus:

\[
D_{\min}
\subseteq
D_{\mathrm{robust}}
\]

may hold relative to a selected disturbance class.

More structure may be required for continued realization under perturbation than for momentary realization under ideal conditions.

---

## 24. Robustness Is a Construction Requirement

One cannot obtain robustness merely by naming a system robust.

Robustness must be physically and organizationally constructed.

To remain robust against disturbance class \(D\), a system may require:

```text
extra energy
extra material
extra information
extra time
extra pathways
extra checking
extra control
```

The robustness property therefore has its own realization dependencies.

A system does not merely depend on components.

It may depend on arrangements among components that preserve capability under perturbation.

This supports the principle:

\[
\boxed{
\text{A property of an architecture is itself realization-dependent.}
}
\]

---

## 25. Similarity Is Purpose-Relative but Not Physically Empty

Humans may be treated as similar for one task and different for another.

For voting:

```text
one person
→ one vote
```

Body geometry may be irrelevant.

For shoe production:

```text
foot length
foot width
arch shape
pressure distribution
```

become consequential.

The person has not changed.

The projection has changed.

But the projection is not unconstrained.

A shoe must still fit an actual foot.

The class `size 42` works only because a range of foot geometries is sufficiently similar relative to the tolerances of the shoe.

Thus classification is purpose-relative without being detached from physical organization.

---

## 26. Material Substitution Reveals Hidden Dependencies

Suppose a conductor is described simply as a `wire`.

At one scale, copper and aluminium may both satisfy the classification.

At another scale, their differences may matter:

```text
conductivity
resistance per length
mass
thermal expansion
contact behavior
oxidation
mechanical strength
frequency response
```

A one-millimeter copper segment followed by aluminium followed by an arbitrary copper length may or may not realize the same higher-level capability.

The answer depends on:

```text
current
frequency
length
interfaces
temperature
mechanical loading
acceptable loss
```

The abstraction `wire` remains useful only while the ignored material differences remain within the operating tolerance of the selected architecture.

---

## 27. Roads Are Physical Organizations, Not Pure Routes

A map may represent a road as an edge between two locations.

That projection suppresses enormous physical detail.

But the road capability depends on:

```text
surface continuity
load-bearing structure
friction
drainage
geometry
visibility
maintenance
legal accessibility
weather conditions
```

Wind, rain, heat, ice, gravity, erosion, and chemical change affect the road because the road never ceased to be a physical organization.

The surprising question is not:

> Why does weather affect the road?

It is:

> Why did the road abstraction remain useful long enough that its physical dependencies became easy to forget?

Its usefulness came from the stability of the underlying organization.

---

## 28. A Car Drives on a Built Road Because Relations Align

A car does not move merely because an object named `road` exists.

Driving requires a coordinated relation among:

```text
vehicle geometry
wheel and tire behavior
surface geometry
friction
engine or motor output
steering
control
traffic rules
available path
```

The road is not the sole cause.

The car-road system supplies compatible constraints and affordances.

The higher-level capability `drive from A to B` is realized by a network of dependencies.

It is obvious that a car drives on a suitable road.

What is easily overlooked is that `suitable` compresses a large set of lower-level conditions.

---

## 29. The Accelerator Does Not Make Particles Obey

A particle accelerator organizes conditions under which selected particle trajectories become reachable, stable, measurable, and useful.

It may depend on:

```text
vacuum
magnetic fields
radio-frequency cavities
alignment
beam focusing
timing
cooling
control systems
measurement
```

The particle remains governed by physical regularities.

The accelerator does not exempt it from those regularities.

It exploits and coordinates them.

The useful beam trajectory is a realized class of physical continuations made accessible by the surrounding organization.

Thus:

```text
lawful particle motion
+
organized environmental conditions
→ selected stable trajectory class
```

---

## 30. Available Paths Are Physically Constructed

A charged particle may propagate along an available path only when the surrounding conditions make that continuation admissible.

A wire, waveguide, accelerator, transistor channel, road, or institutional procedure does not create motion from nothing.

It organizes the space of likely, permitted, or stable continuations.

The path is therefore neither purely abstract nor merely geometric.

It is a realized constraint structure.

A path may depend on:

```text
material continuity
field configuration
boundary conditions
energy availability
timing
control
```

Remove or alter enough of these conditions and the path ceases to support the same propagation.

---

## 31. Conservation Laws Apply at Every Realized Level

A road network, computer, ledger system, and language community do not stand outside physical conservation laws.

Their higher-level descriptions omit many physical quantities because those quantities are not normally needed for the selected task.

But the realizations still involve:

```text
energy transfer
momentum exchange
charge conservation
material transport
heat dissipation
```

It is therefore unsurprising that innovative higher-level systems remain physically constrained.

A software abstraction does not suspend thermodynamics.

A financial abstraction does not eliminate the need for material institutions and communication.

A transportation abstraction does not remove friction, weather, or gravity.

However, realization dependency should not be confused with a conservation law in the strict physical sense.

The analogy is structural:

> Higher-level organization cannot persist without some nonempty realization basis.

The exact realizing matter, energy distribution, or path may change.

The need for realization does not vanish.

---

## 32. Dependency Is Preserved Under Abstraction in a Limited Sense

Abstraction may hide, aggregate, redirect, or replace dependencies.

It does not produce an uninstantiated entity.

For example:

```text
physical address dependence
→ reorganized through virtual addressing

single-bit reliability
→ reorganized through error-correcting codes

individual cash handling
→ reorganized through bank credit

local route knowledge
→ reorganized through maps and road networks
```

One should not call this literal conservation in the Noetherian sense.

A more careful statement is:

\[
\boxed{
\text{Realization dependence survives abstraction, although its visible form changes.}
}
\]

The dependency graph may be compressed at one level and expanded at another.

---

## 33. The Abstraction Boundary Is a Consequence Filter

An abstraction boundary separates distinctions that are exposed from distinctions that are suppressed.

A process sees virtual addresses rather than raw memory wiring.

A customer sees an account balance rather than interbank settlement details.

A driver sees a route rather than the molecular structure of asphalt.

The boundary does not stop lower-level causation.

It filters which consequences normally propagate into higher-level representation.

When an unusual disturbance crosses the filter, the lower level becomes visible again:

```text
cosmic ray
→ bit flip

page-table corruption
→ invalid memory behavior

settlement failure
→ unusable credit

flooding
→ impassable road
```

The abstraction appears to break because a previously suppressed distinction has become consequential.

---

## 34. Leakage Is Reappearance of a Suppressed Distinction

A leak may be understood as a lower-level distinction becoming visible across a boundary that was intended to suppress it.

Examples include:

```text
cache timing revealing secret-dependent behavior
physical charge perturbation changing logical state
host resources becoming visible inside a container
weather damage changing route availability
institutional failure changing the meaning of a bank balance
```

The lower-level interaction was always physically possible.

The architecture classified it as irrelevant, isolated, or controlled.

The leak occurs when that classification no longer holds.

---

## 35. Repair Restores Classification, Not the Past Microstate

Error correction does not ordinarily restore the exact prior physical microstate.

It restores a state belonging to the same higher-level equivalence class.

Suppose \(x\) realizes logical `0`, a disturbance produces \(x'\), and repair produces \(x''\).

Typically:

\[
x''\neq x,
\]

but:

\[
\pi_A(x'')=\pi_A(x)=0.
\]

Thus repair is an equivalence-restoring process.

It preserves higher-level identity without reconstructing every lower-level detail.

This is one reason equivalence classes are central to robustness.

---

## 36. Maintenance Is Continuous Re-Realization

Many organizations do not persist by remaining physically unchanged.

They persist through repeated replacement, repair, refresh, and reclassification.

Examples include:

```text
DRAM refresh
error scrubbing
road resurfacing
biological metabolism
software reconciliation
ledger settlement
language transmission
```

Persistence therefore need not mean material stasis.

It may mean continued membership in an architecture-relative equivalence class across changing lower-level realizations.

The organization persists because transitions repeatedly restore or preserve the required classification.

---

## 37. Failure Is Loss of Realizable Classification

A higher-level failure occurs when lower-level evolution no longer supports the selected classification, transformation, capability, or viability condition.

This may happen because:

```text
class boundaries are crossed
classification becomes ambiguous
translation becomes inconsistent
repair capacity is exceeded
critical relations disappear
semantic interpretation no longer matches physical state
```

Formally, failure may be represented as:

\[
\rho_A(\gamma)
\]

becoming undefined or invalid for a lower-level trajectory \(\gamma\).

Reality continues.

The architecture-relative interpretation loses validity or success.

---

## 38. The Classification Cascade

A single lower-level perturbation may cross several architectural levels.

For example:

```text
particle interaction
→ charge redistribution
→ memory-cell state change
→ bit flip
→ integer sign reversal
→ invalid arithmetic
→ changed control flow
→ service failure
→ institutional or economic consequence
```

Each arrow depends on a classification and interpretation layer.

The physical perturbation does not contain the later semantic consequence by itself.

The architecture supplies the dependency path through which the consequence is propagated and amplified.

---

## 39. Semantic Amplification

Semantic amplification occurs when a small change at one level alters a large set of higher-level reachable states.

Let \(x\) and \(x'\) be physically close under some lower-level metric, but suppose:

\[
\pi_A(x)\neq\pi_A(x').
\]

If the two classifications lead to highly divergent architecture-relative continuations, then a small lower-level difference has large semantic effect.

Examples include:

```text
sign bit
permission bit
branch condition
cryptographic key bit
transaction commit marker
routing flag
```

This is not mysterious.

It is an effect of architectural organization.

---

## 40. Abstraction Can Increase Consequence Concentration

Abstraction often allows large systems to depend on compact interfaces.

A compact interface is efficient because many details are hidden.

But it may also concentrate consequence into a small number of exposed distinctions.

For example:

```text
one API status
one permission bit
one page-table entry
one certificate
one deployment configuration
```

may govern extensive downstream behavior.

The abstraction reduces cognitive and operational complexity while potentially increasing the criticality of selected states.

This yields a tradeoff:

```text
fewer exposed distinctions
→ simpler coordination
but sometimes
→ greater consequence per distinction
```

---

## 41. Classification Debt

An architecture may rely on a classification whose lower-level support has become weaker than assumed.

Examples include:

```text
aging hardware still treated as reliable memory
weather-damaged road still treated as passable
stale account records still treated as authoritative
legacy software boundary still treated as secure
```

The higher-level system continues operating under a classification that is no longer sufficiently supported.

This may be called classification debt:

> Accumulated mismatch between the distinctions an architecture assumes and the distinctions its current realization can reliably maintain.

Maintenance, validation, and repair reduce classification debt.

---

## 42. Classification Strength Must Match Consequence Magnitude

If a distinction has large downstream consequence, the architecture may require correspondingly strong preservation, validation, or repair.

A transient display pixel and a cryptographic key bit do not have equal consequence.

A road marking and a bridge support do not have equal criticality.

A typo in an informal note and a sign error in a medical dosage do not require equal assurance.

Thus:

\[
\boxed{
\text{Required classification strength should scale with consequence, horizon, and disturbance exposure.}
}
\]

This is an engineering and institutional principle rather than a universal physical law.

---

## 43. Knowledge Does Not Create the Dependency

An engineer may be unaware that radiation can affect a storage device.

A driver may be unaware that drainage is failing beneath a road.

A customer may be unaware of the settlement relations supporting a bank balance.

The dependency remains.

Knowledge changes prediction and possible intervention.

It does not create the underlying realization relation.

Thus:

\[
\operatorname{Depends}(A,R)
\]

may hold whether or not any agent represents that dependence.

The sentence

> The dependency exists regardless of whether it is known.

therefore means more than hidden risk.

It means that realization relations are not generated by our descriptions of them.

---

## 44. Classification Does Not Create the Classified Dynamics

An architecture may call a range of voltages `0`.

That label does not create the voltages.

A bank may call a ledger entry `credit`.

That classification does not create the material infrastructure or social history that makes the credit usable.

A map may call a surface `road`.

That label does not create friction or structural support.

Classification selects and organizes significance.

It does not manufacture the lower-level regularities from nothing.

---

## 45. The World Constrains Useful Equivalence Relations

Many equivalence relations can be written.

Few support stable prediction, intervention, and continuation.

A useful equivalence relation must align sufficiently with actual dynamics.

If states grouped together evolve into radically different higher-level outcomes under ordinary conditions, the classification is weak or misleading.

A strong architecture-relative equivalence relation tends to satisfy approximate dynamical compatibility:

\[
x\sim_A y
\Longrightarrow
F_t(x)\sim_A F_t(y)
\]

for relevant times \(t\), transformations, and disturbances.

This need not hold universally.

It must hold well enough for the intended use.

---

## 46. Stable Meaning Is a Dynamical Achievement

Meaning is often treated as if it were attached to a symbol once and for all.

In realized systems, stable meaning depends on maintained relations among:

```text
symbol
encoding
context
history
consumer
rules of transformation
physical persistence
```

A sign bit means `negative` only within an encoding and operation architecture.

A page-table entry means `map this virtual page to this frame` only within a processor and operating-system architecture.

A ledger entry means `the bank owes this amount` only within an institutional architecture.

Meaning persists because the relevant interpretive and physical relations persist.

---

## 47. The Road, the Bit, and the Credit Share a Structure

The examples appear different:

```text
road
bit
virtual page
bank credit
language expression
```

But they share a common pattern:

```text
many lower-level states and relations
→ classified as one higher-level state or capability
→ preserved by recurring regularities and organized maintenance
→ exposed through a limited interface
→ vulnerable when suppressed distinctions become consequential
```

This commonality does not erase their differences.

It supplies a shared analytical form.

---

## 48. A General Model

Let:

- \(X\) be a lower-level state space,
- \(\Gamma\) be a set of admissible lower-level trajectories,
- \(A\) be a selected architecture,
- \(\pi_A:X\rightharpoonup S_A\) be a partial classification map,
- \(D\) be a disturbance class,
- \(H\) be a horizon,
- \(K_A\) be a set of maintenance, detection, control, or repair mechanisms.

Architecture \(A\) is realized over horizon \(H\) when relevant trajectories remain classifiable and the required transition relations among classes remain valid.

A disturbance \(d\in D\) is absorbed when:

\[
\pi_A(d(x))=\pi_A(x),
\]

or when repair \(k\in K_A\) restores equivalence:

\[
\pi_A(k(d(x)))=\pi_A(x).
\]

Failure occurs when neither direct preservation nor available repair maintains the selected classification or capability.

---

## 49. Direct Preservation and Repair Preservation

There are at least two ways an architecture can remain stable.

### Direct preservation

The disturbance remains inside the same equivalence class:

\[
\pi_A(d(x))=\pi_A(x).
\]

Example:

```text
small voltage noise
→ still logical 0
```

### Repair preservation

The disturbance changes the immediate classification, but a corrective process restores it:

\[
\pi_A(d(x))\neq\pi_A(x),
\]

while:

\[
\pi_A(k(d(x)))=\pi_A(x).
\]

Example:

```text
single-bit error
→ ECC detection
→ corrected codeword
→ same logical data
```

Both are forms of robustness.

The second explicitly depends on additional organized operations.

---

## 50. No Architecture Is Robust Against Everything

An ECC scheme may correct one bit and fail on many simultaneous errors.

A road may resist rain and fail under flooding or earthquake.

A bank may survive ordinary defaults and fail under systemic collapse.

A virtual-memory system may isolate processes and fail under kernel compromise or hardware fault.

Robustness is bounded:

\[
\operatorname{Robust}(A,D,H)
\]

never means robust against all physically possible disturbances over all horizons.

The disturbance model matters.

The repair budget matters.

The time horizon matters.

---

## 51. Dependency Exposure Is an Architectural Choice

An architecture may expose some dependencies and hide others.

Examples:

```text
assembly exposes registers
high-level languages hide most registers

physical memory exposes frames
virtual memory exposes process-relative addresses

bank settlement exposes institutional obligations
consumer banking exposes account balances

road engineering exposes material and load models
navigation exposes routes and travel times
```

Hiding a dependency does not remove it.

It changes who must manage it and through which interface it can become consequential.

---

## 52. Hidden Dependency Is Often Managed Dependency

A dependency may be hidden precisely because another layer is managing it.

A process need not know the physical frame because the operating system and processor manage translation.

An application need not know which memory cell was corrected because ECC hardware manages the perturbation.

A customer need not know each settlement step because financial institutions manage it.

The invisibility of a dependency is often evidence of successful organization, not absence.

When management fails, the hidden dependency becomes visible again.

---

## 53. Successful Abstraction Produces Forgetfulness

Stable abstractions are easy to treat as independent entities because their realization conditions rarely demand attention during ordinary use.

A road appears simply to be a road.

A file appears simply to contain data.

A bank balance appears simply to be money available.

A bit appears simply to be `0` or `1`.

The better the lower-level organization suppresses irrelevant variation, the easier it is to forget that the higher-level state is being physically and institutionally realized.

This forgetfulness is operationally useful.

It becomes dangerous when it turns into the belief that realization conditions no longer matter.

---

## 54. The Reappearance Principle

A hidden lower-level distinction reappears at a higher level when its effects cross the architecture's tolerance or repair boundary.

Examples include:

```text
radiation reappears as a bit flip
thermal drift reappears as timing failure
page corruption reappears as invalid memory access
weather reappears as road closure
institutional instability reappears as frozen credit
```

The lower-level factor was never absent.

It was merely nonconsequential under ordinary operating conditions.

---

## 55. The Non-Arbitrariness of Abstraction

An abstraction may be chosen for a task, but its successful realization is constrained by the world.

A classification is not useful merely because it is convenient.

It must be:

```text
observable enough
stable enough
transformable enough
repairable enough
predictive enough
```

for the selected purpose.

The architecture may choose which distinctions matter.

It cannot freely choose whether the lower-level dynamics will preserve them.

---

## 56. The Physical Cost of Stable Meaning

Stable higher-level meaning usually requires material and energetic support.

Examples include:

```text
power for memory retention
energy for error correction
material for redundant storage
bandwidth for replication
maintenance for roads
institutional labor for ledgers
education and communication for language continuity
```

Meaning is not reducible to energy expenditure, but its stable realization is not costless.

The architecture requires work, structure, and recurring regularity.

---

## 57. Classification and Causal Compression

An abstraction compresses many lower-level causal details into a smaller set of higher-level variables.

For example:

```text
billions of microphysical configurations
→ one logical bit

many physical frames and translations
→ one virtual address

many institutional operations
→ one account balance

many material details
→ one road segment
```

The compression is useful when the higher-level variable retains the causal information required for the task.

If important distinctions are compressed away, prediction or control fails.

Thus abstraction quality depends on preserving the right causal distinctions.

---

## 58. Classification Failure and Model Failure

Two different failures should be distinguished.

### Realization failure

The lower-level organization no longer realizes the intended class.

Example:

```text
stored 0 becomes stored 1
```

### Model failure

The classification remains physically stable, but the model omits a distinction required for the task.

Example:

```text
road classified as passable
but vehicle weight exceeds bridge capacity
```

In one case, the architecture leaves its operating region.

In the other, the selected abstraction was inadequate for the intervention.

Both show that ignored distinctions are only conditionally irrelevant.

---

## 59. The Dependency of Properties

A system does not only depend on components.

Its properties depend on organized relations among components.

For example:

```text
conductivity
robustness
security
solvency
passability
correctness
```

are not free-floating properties.

They are realized under conditions.

A road depends not merely on asphalt existing, but on the asphalt, support, geometry, drainage, and maintenance jointly realizing passability.

A memory system depends not merely on bits existing, but on storage, timing, access, correction, and interpretation jointly realizing reliable state.

---

## 60. Constraint Is the Shape of Reachable Continuation

A constraint need not be understood as an external prohibition.

It may be the realized structure that makes some continuations stable, some unstable, some inaccessible, and some repairable.

A road constrains vehicle motion into a path.

A memory encoding constrains valid codewords.

A page table constrains address translation.

A grammar constrains valid expressions.

A bank protocol constrains valid settlement transitions.

The constraint is physically or institutionally instantiated.

It shapes reachable higher-level continuation.

---

## 61. Dependency and Constraint Are Mutually Realized

A dependency may motivate a constraint.

But the constraint itself introduces dependencies.

For example:

```text
memory errors
→ motivate ECC
→ ECC introduces encoding and decoder dependencies
```

```text
address collision
→ motivates virtual memory isolation
→ virtual memory introduces translation dependencies
```

```text
payment uncertainty
→ motivates settlement rules
→ settlement rules introduce institutional dependencies
```

Thus organization does not move from dependency to dependency-free order.

It transforms one dependency structure into another.

---

## 62. Dependency Transformation

An architecture may transform dependency by:

```text
aggregation
translation
replication
isolation
serialization
encoding
monitoring
repair
replacement
```

These operations do not abolish realization dependence.

They change:

```text
which distinctions are exposed
which disturbances are tolerated
which paths are available
which failures propagate
which states count as equivalent
```

The practical objective is not dependency elimination.

It is dependency organization relative to selected consequences.

---

## 63. Classification Requires a Horizon

A state may be stable for one second and unstable for one year.

A road may be passable today and degraded next winter.

A bank may be solvent under ordinary withdrawals and not under a systemic run.

A memory cell may retain state long enough for one computation but not archival storage.

Therefore every claim of stable classification should be indexed by a horizon:

\[
\operatorname{StableClass}(A,H).
\]

Without a horizon, permanence may be falsely inferred from temporary reliability.

---

## 64. Classification Requires a Disturbance Model

A system cannot be judged robust without asking: robust against what?

Examples include:

```text
thermal noise
single-particle radiation events
power interruption
material fatigue
ordinary traffic load
institutional fraud
communication error
adversarial action
```

A design may be robust against one disturbance class and fragile against another.

The disturbance model defines which ignored differences are expected to remain irrelevant.

---

## 65. Architecture-Relative Criticality

A tiny component may be highly critical when many higher-level continuations depend on its classification.

Examples include:

```text
sign bit
page-table root
cryptographic key
bridge joint
settlement account
root certificate
```

Criticality depends on:

```text
semantic consequence
redundancy
repairability
propagation paths
horizon
```

Physical size does not determine architectural importance.

---

## 66. Classification-Aware Intervention

Before altering a realized system, ask:

```text
Which higher-level classes does this locus help realize?

Which lower-level distinctions are currently being ignored?

Which disturbances can make those distinctions consequential?

Which class boundaries are narrow?

Which correction mechanisms exist?

Which correction mechanisms are themselves dependencies?

Which semantic consequences are concentrated into this state?

Which alternative realization paths remain?
```

This extends dependency analysis into classification analysis.

---

## 67. Diagnostic Vocabulary

A classification-centered vocabulary may include:

```text
ABSTRACTION ESCAPE ERROR:
    a higher-level state is treated as if it had escaped the conditions that realize it

ARBITRARY CLASSIFICATION FALLACY:
    a mathematically definable partition is assumed to be physically stable or operationally useful

SUPPRESSED-DIFFERENCE BLINDNESS:
    ignored lower-level variation is treated as nonexistent rather than conditionally irrelevant

REALIZATION FORGETFULNESS:
    successful abstraction leads agents to overlook the infrastructure that preserves it

SEMANTIC MAGNIFICATION BLINDNESS:
    a small physical change is assumed to imply only a small higher-level consequence

DEPENDENCY-ELIMINATION CONFUSION:
    transformed or hidden dependency is mistaken for absent dependency

ROBUSTNESS-WITHOUT-CONSTRUCTION:
    robustness is attributed without identifying redundancy, margin, repair, or other realizing structure

EXTERNAL-ORGANIZER FALLACY:
    a controller or repair mechanism is treated as if it operated outside physical and organizational dependency

REDUNDANCY ABSOLUTISM:
    two paths are called redundant without specifying the capability, projection, disturbance class, and horizon

CLASSIFICATION-DEBT BLINDNESS:
    a weakening realization continues to be treated as supporting the same stable higher-level distinctions

MEANING-WITHOUT-MAINTENANCE:
    semantic identity is treated as independent of encoding, context, interpretation, and physical persistence

CONSERVATION-ANALOGY OVERREACH:
    realization dependence is treated as a literal conserved physical quantity rather than a structural requirement
```

---

## 68. Central Principles

### Realizable-Classification Principle

> A useful abstraction is a physically, computationally, socially, or institutionally realizable classification of lower-level variation.

### Suppressed-Difference Principle

> An abstraction does not eliminate lower-level distinctions; it suppresses their higher-level consequences within a selected operating region.

### Non-Arbitrariness Principle

> A classification may be selected by an architecture, but its stability is constrained by actual lower-level dynamics.

### Structural-Dependence Principle

> A higher-level state continues only while the relations required for its realization remain sufficiently effective.

### Recursive-Instantiation Principle

> Every organizer, controller, classifier, or repair mechanism is itself instantiated through further dependencies.

### No-External-Manager Principle

> There is no dependency-free standpoint from which realized dependencies are manipulated.

### Semantic-Amplification Principle

> A physically small perturbation may produce a large higher-level consequence when an architecture concentrates meaning into a narrow distinction.

### Robustness-Through-Organization Principle

> Robustness is often achieved by adding redundant, corrective, or alternative dependency paths rather than by eliminating dependency.

### Projection-Relative-Redundancy Principle

> Two realization paths are redundant only relative to a selected capability, projection, disturbance model, and horizon.

### Equivalence-Restoration Principle

> Repair usually restores higher-level equivalence rather than the exact prior microstate.

### Reappearance Principle

> A suppressed lower-level distinction becomes visible when its effects cross the architecture's tolerance or repair boundary.

### Classification-Strength Principle

> The reliability required of a classification depends on the consequence attached to misclassification, the expected disturbances, and the relevant horizon.

### Realization-Survival Principle

> Abstraction can reorganize, compress, or hide realization dependency, but it cannot produce an uninstantiated higher-level entity.

---

## 69. What This Framework Claims

The framework claims:

```text
that abstraction classifies lower-level variation rather than removing it

that useful equivalence classes must be sufficiently aligned with actual dynamics

that ignored distinctions remain physically present

that a bit depends on collective charge organization even when no individual electron is named

that cosmic radiation can become a logical error by pushing a physical state across an architectural class boundary

that a small physical perturbation can have a large semantic consequence

that error correction adds organized dependencies in order to reduce sensitivity to selected disturbances

that redundancy is equivalence among realized paths relative to a selected capability

that virtual memory reorganizes physical addressing through maintained translation relations

that bank credit is a realized relational state rather than a detached substance

that roads, languages, programs, and institutional states depend on structured relations rather than mere component presence

that operations which classify or repair other systems are themselves instantiated

that no organizer operates outside dependency

that robustness, security, passability, solvency, and correctness have realization requirements

that successful abstraction often causes realization conditions to be forgotten

that lower-level distinctions reappear when tolerance or repair boundaries are crossed

that abstraction is constrained by the classification strength required for its consequences
```

---

## 70. What This Framework Does Not Claim

The framework does not claim:

```text
that every individual particle is equally critical to every higher-level state

that every abstraction actively maintains its own boundaries

that all classifications are engineered

that physical realization alone determines higher-level meaning

that redundancy means physical identity

that more dependency always increases robustness

that more complexity is always preferable

that a bank credit is reducible to one ledger entry

that a virtual address exists inside one CPU component

that every small physical perturbation produces a large semantic consequence

that realization dependence is a literal conserved quantity

that all higher-level failures share one physical mechanism

that abstraction is invalid because it ignores detail

that exact microstate reconstruction is required for repair

that a useful model must include every lower-level distinction
```

---

## 71. Revised Foundational Sequence

The resulting sequence is:

\[
\boxed{
\begin{aligned}
&\text{continuing lawful interaction}\\
&\xrightarrow{\text{recurrence}}
\text{stable lower-level regularities}\\
&\xrightarrow{\text{projection}}
\text{candidate classifications}\\
&\xrightarrow{\text{dynamical compatibility}}
\text{realizable equivalence classes}\\
&\xrightarrow{\text{interface and interpretation}}
\text{higher-level states and meanings}\\
&\xrightarrow{\text{maintenance and repair}}
\text{persistent architecture-relative identity}\\
&\xrightarrow{\text{perturbation}}
\text{absorption, correction, reclassification, or failure}\\
&\xrightarrow{\text{propagation}}
\text{semantic amplification and downstream consequence}.
\end{aligned}
}
\]

---

## 72. Conclusion

An abstraction does not escape the world it abstracts.

A logical bit remains physically realized through charge, fields, material structure, timing, thresholds, and noise margins.

A virtual address remains realized through translation state, processor mechanisms, kernel organization, and physical memory.

A bank credit remains realized through ledgers, obligations, identity, settlement, institutional authority, and material infrastructure.

A road remains realized through geometry, support, friction, molecular organization, drainage, weather exposure, and maintenance.

These higher-level entities are not unreal.

They are real as organized classifications, capabilities, and relations.

Their reality is conditional on continued realization.

The abstraction succeeds because many lower-level differences remain inconsequential for the selected task.

That irrelevance is never absolute.

A cosmic particle may deposit enough charge to move a memory state across a logical boundary.

A single flipped bit may reverse a sign.

A reversed sign may redirect a control path.

A small physical event may therefore become a large semantic event.

The amplification is not contained in the particle alone.

It is supplied by the architecture that assigns consequence to the affected distinction.

Error correction reveals the complementary fact.

Robustness is not necessarily achieved by removing dependence.

It may require additional bits, additional gates, additional checking, additional timing assumptions, and additional repair paths.

More dependency can produce less fragility when dependency is organized into alternatives, margins, detection, and restoration.

There is no contradiction.

A minimally sufficient architecture may realize a capability once.

A robustly sufficient architecture must continue realizing it under a selected disturbance class and horizon.

The repair mechanism does not stand outside the system.

It is another physical organization with its own dependencies.

The page table, the ECC decoder, the bank ledger, the road-maintenance process, and the language interpreter are all instantiated operations.

There is no external manager free of the conditions it manages.

This gives a stronger interpretation to the statement:

> The dependency exists regardless of whether it is known.

The claim is not merely that some risks are hidden.

It is that realization relations do not wait for observers to identify them.

A classification succeeds only insofar as the world continues to sustain the distinctions it requires.

We may ignore individual charges, physical frames, settlement procedures, material grains, or pronunciation details.

But we can safely ignore them only while their variation remains inside the region where the higher-level classification is preserved.

The central lesson is therefore:

\[
\boxed{
\begin{aligned}
&\text{Abstraction does not remove dependence.}\\
&\text{It selects which differences may remain inconsequential.}\\
&\text{Realization keeps those differences within tolerable bounds.}\\
&\text{Robustness adds paths that preserve or restore classification.}\\
&\text{Failure occurs when a suppressed distinction becomes consequential.}
\end{aligned}
}
\]

The practical question is no longer merely:

> What does this abstraction hide?

It becomes:

> Which lower-level variations are being classified as equivalent; what physical, computational, social, or institutional regularities keep them equivalent; how strong must that classification be relative to its consequences; which disturbances can cross its boundaries; which added dependencies detect or repair those crossings; and what higher-level meanings will change when the classification is no longer sustained?
