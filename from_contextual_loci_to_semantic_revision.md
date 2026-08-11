# From Contextual Loci to Semantic Revision: Reference Frames, Correspondence, Invalidation, and the Foundations of Rule Discovery

## Abstract

A semantic bootstrapping system should be careful not to hide domain structure inside its supposed primitives.

Terms such as:

```text
input
output
observation
intervention
mutation
state
value
change
ordering
```

already encode substantial semantic commitments.

An input is an input relative to a boundary.

An output is an output relative to a boundary.

A voltage is a value relative to a reference.

A pixel location is comparable across images only relative to a correspondence between coordinate systems.

A numerical comparison is meaningful only relative to a domain, representation, unit, scale, ordering, and often bounds.

A change is identifiable only after some locus or identity has been preserved across contexts.

An observation is not absence of interaction; it is an interaction whose role is primarily epistemic relative to some higher-level target.

A control is not necessarily an intrinsic property of a variable; it may be a discovered asymmetric relation in which variation at one locus reliably constrains or selects variation elsewhere.

This suggests a deeper bootstrapping architecture.

Instead of beginning from a vocabulary such as:

```text
observe(x)
mutate(x)
set_input(x, v)
read_output(y)
```

begin from a weaker question:

```text
Under what context can descriptions be associated with loci,
which associations can be compared across contexts,
which claims depend on those associations,
and what changes require those claims to be reconsidered?
```

The central proposal is:

\[
\boxed{
\text{semantic discovery begins with contextual association and revision,}
\\
\text{not with pre-classified inputs, outputs, observations, and actions}
}
\]

A useful system therefore maintains not only propositions about a world, but the contextual structure that makes those propositions meaningful:

```text
loci
reference frames
assignment domains
correspondences
comparison contracts
dependencies
validity conditions
invalidation events
ordered evidence contexts
```

From this substrate, higher-level notions such as state, motion, control, observation, intervention, causation, and input/output roles can be synthesized when sufficient evidence supports them.

The result is a semantic bootloader whose deepest responsibility is not merely discovering facts.

It discovers and maintains the conditions under which facts can be stated, compared, reused, and invalidated.

---

## 1. The Primitive Vocabulary May Already Be Too Semantic

Suppose a proposed minimal semantic bootstrapper begins with:

```text
SetInput(x, value)
ObserveOutput(y)
DetectChange(z)
```

This appears minimal.

It is not.

Each term contains hidden structure.

`SetInput(x, value)` assumes:

```text
x is identifiable
x has a state-like quantity
that quantity has a domain
one value can replace another
the operation is directed toward x
x has the role "input"
the operation can be distinguished from ordinary environmental evolution
```

`ObserveOutput(y)` assumes:

```text
y is identifiable
y exposes something measurable
y belongs on the "output" side of some boundary
observation can be separated from intervention
an observer exists as a meaningful role
```

`DetectChange(z)` assumes:

```text
z at one context corresponds to z at another context
the descriptions are comparable
some ordering connects the contexts
the difference is meaningful in the relevant domain
```

Thus a supposed primitive operation may already contain much of the semantic structure the system is intended to discover.

A deeper bootstrapping system should therefore distinguish:

```text
operational primitives
```

from:

```text
semantic interpretations of those operations
```

The first may be unavoidable.

The second should be earned whenever possible.

---

## 2. A Locus May Be More Fundamental Than a Value

A raw value does not say what it describes.

Consider:

```text
3
```

This could mean:

```text
three objects
3 volts
3 metres
state identifier 3
third array index
three seconds
class label 3
file descriptor 3
probability encoded on an arbitrary scale
```

The value alone carries almost no usable semantics.

A stronger primitive is an **assignment to a locus under a context**.

Conceptually:

```yaml
assignment:
  locus: x
  context: C
  domain: D
  value: v
```

or formally:

\[
A(x,C,D)=v.
\]

The important object is not merely \(v\).

It is the structured association:

\[
(x,C,D,v).
\]

This suggests:

\[
\boxed{
\text{values are meaningful only through contextual assignment}
}
\]

---

## 3. What Is a Locus?

A locus should not initially be understood only as a physical coordinate.

A locus is any stable-enough referential position to which descriptions can be attached.

Examples include:

```text
a circuit node
an image coordinate
a memory address
a register field
a variable binding
a filesystem path
a process
a tracked object
a package identity
a region in a scene
a timestamped sensor channel
a proposition slot in a structured artifact
```

The important property is not physicality.

It is referential reuse.

A system must be able to ask:

```text
Is this description about the same locus as that description?
```

or, more cautiously:

```text
Under which correspondence should these two loci be treated as related?
```

The second question is more general.

Identity itself may be contextual and inferred.

---

## 4. Context Is Not Metadata Attached After the Fact

Context is often treated as auxiliary metadata.

For semantic bootstrapping, it is constitutive.

An assignment may be meaningful only relative to:

```text
reference frame
unit system
coordinate system
clock
device identity
calibration
schema
encoding
observer boundary
software version
environment configuration
```

Therefore:

\[
\operatorname{Claim}(P)
\]

should often be understood more precisely as:

\[
\operatorname{Claim}(P \mid C).
\]

The context \(C\) is part of what licenses the claim.

This is the same structural issue whether the claim is:

```text
this node is at 3 V
```

or:

```text
this executable exposes subcommand launch
```

In both cases, the proposition is meaningful only under an identity and reference context.

---

## 5. Voltage Shows Why Reference Is Fundamental

Voltage is a useful example because the apparent scalar hides a relational quantity.

A voltage associated with a point is ordinarily a potential difference relative to a reference:

\[
V(x;r)=\phi(x)-\phi(r).
\]

The statement:

```text
x = 3 V
```

therefore suppresses:

```text
which x?
relative to which reference r?
under which measurement convention?
under which calibration?
with which units?
at which relevant context?
```

Ground is usually not an absolute universal zero.

It is a selected reference structure from which other assignments are interpreted.

Thus:

```text
zero
```

may itself be a contextual construction.

The semantic lesson is broader:

> A numerical assignment can depend on a reference relation that must remain valid for the assignment to be reused.

If the reference changes, previously cached comparisons may become stale even if the recorded numerals do not change.

---

## 6. Comparison Requires a Comparison Contract

Two descriptions should not be compared merely because they have representable values.

A useful architecture may require an explicit comparison contract:

```yaml
comparison_contract:
  left_domain: ...
  right_domain: ...
  correspondence: ...
  frame_relation: ...
  unit_relation: ...
  normalization: ...
  ordering: ...
```

Then:

\[
\operatorname{Compare}(a,b)
\]

is admissible only when:

\[
\operatorname{Comparable}(a,b,C).
\]

A possible rule is:

\[
\operatorname{SameDomain}(a,b)
\land
\operatorname{FrameCompatible}(a,b)
\land
\operatorname{Correspond}(a,b)
\rightarrow
\operatorname{Comparable}(a,b).
\]

The exact premises are domain-dependent.

The architectural point is that **comparison itself has semantic prerequisites**.

---

## 7. Equal Shapes Do Not Make Images Comparable

Suppose two image-like arrays have shape:

```python
(1024, 1024, 3)
```

A numerical library can establish:

```text
same rank
same extents
compatible element type
```

It cannot thereby establish:

```text
pixel [i,j] refers to the same ray
both arrays use the same camera
both use the same lens model
both are spatially registered
both use the same channel semantics
both use the same normalization
both refer to the same time
both depict the same scene region
```

Therefore:

```python
A == B
```

may be syntactically defined while semantically meaningless for the target.

The stronger structure is:

```text
array compatibility
AND
coordinate correspondence
AND
semantic channel compatibility
AND
required registration
→ target-relevant comparability
```

A semantic bootstrapper should discover or demand those prerequisites rather than silently assuming them.

---

## 8. Correspondence Comes Before Change

To say that something changed requires a correspondence across contexts.

Suppose contexts \(C_1\) and \(C_2\) contain assignments:

\[
A(x_1,C_1)=v_1
\]

and:

\[
A(x_2,C_2)=v_2.
\]

The statement:

\[
v_1 \neq v_2
\]

is not sufficient to establish that **one thing changed**.

The system also needs something like:

\[
\operatorname{Correspond}(x_1,x_2,C_1,C_2).
\]

Only then can it construct:

\[
\operatorname{Changed}(x,C_1,C_2).
\]

Thus:

\[
\boxed{
\text{change is difference under an admitted correspondence}
}
\]

This makes object tracking, variable identity, file identity, executable digests, and schema identity instances of the same deeper problem.

---

## 9. Identity Can Be a Candidate Rule

The system should not necessarily assume perfect persistence of objects.

Instead it may maintain hypotheses such as:

```text
track_17 in frame t
corresponds to
track_19 in frame t+1
```

with evidence:

```text
spatial continuity
appearance similarity
motion consistency
shared identifier
structural continuity
```

Likewise in software:

```text
/path/to/tool at time t
```

may or may not be the same semantic object as:

```text
/path/to/tool at time t+1
```

A path alone may be insufficient.

Identity can depend on:

```text
digest
version
provider set
configuration
environment
runtime state
```

Therefore even identity may belong to the candidate-and-validation lifecycle.

---

## 10. Numerical Ordering Is Not Universal Ordering

A symbol such as:

\[
<
\]

looks primitive because mathematics provides familiar ordered domains.

But a semantic system must know which ordering is intended.

Examples:

```text
1 < 2
    numerical order

a.txt < b.txt
    perhaps lexical order

event A < event B
    perhaps temporal precedence

claim A < claim B
    perhaps information ordering

state A < state B
    perhaps reachability or preference
```

Therefore ordering should generally be contextual:

\[
\operatorname{Order}_C(a,b).
\]

The system should not infer an ordering merely from representational encodings.

An enum value `2` is not necessarily greater than enum value `1` in any target-relevant sense.

---

## 11. Counting Also Requires a Boundary

Even counting is not semantically free.

To say:

```text
there are 3 objects
```

requires some answer to:

```text
which things count as objects?
which region is being counted?
which time/context is relevant?
when are two observations the same object rather than two objects?
which classes are included?
what constitutes one unit?
```

Thus cardinality requires a collection boundary and an equivalence or identity discipline.

Conceptually:

\[
\operatorname{Count}(S/{\sim_C})=n
\]

where the context determines both the candidate collection \(S\) and the equivalence relation under which occurrences are treated as the same or distinct.

This matters for semantic discovery because apparent numerical primitives often depend on earlier structural commitments.

---

## 12. Input and Output Are Relative Roles

A node is not intrinsically an input or output in every context.

The same signal can be:

```text
output of component A
input to component B
observation channel for controller C
control signal relative to actuator D
evidence source relative to a semantic bootstrapper
```

Therefore:

```text
Input(x)
```

is generally weaker than:

```text
InputRelativeTo(x, boundary, interaction)
```

or:

```text
Role(x, INPUT, system=S, context=C)
```

Similarly:

```text
Output(y)
```

should usually be relational.

This removes a hidden agent-centric assumption from the primitive ontology.

---

## 13. Observation Is Input to an Observer

Observation is often described as if it were absence of input.

That is misleading.

An observation requires some coupling through which a condition elsewhere influences the observing system.

From the observer boundary:

\[
\text{observed condition}
\rightarrow
\text{observer state}
\]

is itself an input-like relation.

Physical observation may also perturb the observed system.

Therefore three claims should remain distinct:

```text
no intentional control was applied
no target-relevant perturbation occurred
no physical interaction occurred
```

The third is generally too strong for physical measurement.

A semantic architecture should therefore classify observation not as "no interaction" but as an interaction whose intended role is primarily knowledge acquisition and whose perturbation is bounded relative to the target.

---

## 14. Intervention Is Also a Relative Interpretation

To say:

```text
we set the transistor low
```

already presupposes:

```text
an agent
an identified transistor or terminal
a state domain
an intended operation
a direction of influence
a meaningful low region
a before/after relation
```

A weaker record may be:

```text
condition at locus X differed across contexts
condition at locus Y subsequently differed
```

Repeated evidence may later justify stronger roles:

```text
X is controllable
Y is responsive to X
X functions as an input relative to boundary B
Y functions as an output relative to boundary B
```

Thus intervention can itself be a semantic conclusion rather than an unquestioned primitive.

---

## 15. Control Can Be Discovered as Asymmetric Influence

A useful derived concept is **control-like influence**.

Suppose variation at locus \(x\) consistently changes the reachable assignments of locus \(y\), while the reverse relation is not observed under the same context.

Then the system may construct a candidate:

\[
\operatorname{ControlLike}(x,y,C).
\]

A possible interpretation is:

> variation at \(x\) reliably constrains or selects states of \(y\) under context \(C\).

This need not immediately imply philosophical causation.

It is a target-useful structural asymmetry.

The system can then synthesize higher-level roles:

```text
control
input
command
actuator drive
gating signal
parameter
```

when the relevant domain semantics support them.

---

## 16. Propagation May Be More Primitive Than Global Input/Output

In a distributed physical or computational structure, there may be no single privileged global input/output boundary.

Instead there may be local relations:

```text
A influences B
B influences C
C constrains D
```

or:

\[
A \leadsto B \leadsto C \leadsto D.
\]

What appears globally as:

```text
input → output
```

may simply be a projection over a larger propagation graph.

Therefore the bootloader may prefer local relations such as:

```text
Adjacent
Coupled
Influences
Constrains
PropagatesTo
ReachableFrom
```

and derive global roles only relative to a selected boundary.

This is especially important when boundaries themselves are target-relative.

---

## 17. A NAND Gate Is Already an Abstraction Boundary

A NAND gate is often treated as nearly primitive.

But even:

\[
\operatorname{NAND}(a,b)
\]

assumes:

```text
two loci have been classified as inputs
one locus has been classified as output
continuous physical values have been partitioned into logical classes
logical 0 and logical 1 have been defined
sampling conditions have been chosen
transient behavior has been abstracted away
voltage references are established
```

Thus a NAND truth table is not a raw physical description.

It is a high-quality semantic compression boundary.

This does not make it less useful.

It makes clear what has already been bootstrapped.

---

## 18. The Transistor Exposes the Abstraction Stack

At a lower level, a transistor may be described through relations among terminal potentials, currents, geometry, temperature, and time.

At a higher level it may support a binary abstraction:

```text
control region low
→ channel state class A

control region high
→ channel state class B
```

At a still higher level, several devices may realize a logical gate.

The stack may look like:

```text
physical field / charge relations
↓
terminal measurements relative to references
↓
operating-region classifications
↓
binary signal classes
↓
gate relation
↓
combinational circuit
↓
stateful circuit
↓
instruction behavior
↓
software contract
↓
application semantics
```

Each arrow is a potential semantic bootstrapping boundary.

The framework should therefore support not only discovering facts *within* a level, but discovering valid abstraction mappings *between* levels.

---

## 19. A Semantic Compression Point Is Also an Abstraction Contract

A schema, gate abstraction, coordinate transform, type declaration, interface, or protocol can all act as semantic compression points.

Their common structure is:

```text
large lower-level possibility space
↓
validated abstraction mapping
↓
smaller target-useful semantic space
```

For example:

```text
continuous voltage traces
↓
validated logic-level thresholds
↓
Boolean signal
```

or:

```text
pixel intensities under calibrated camera geometry
↓
validated correspondence model
↓
world-relative feature position
```

or:

```text
implementation details
↓
declared callable contract
↓
planner-usable operation
```

The critical object may therefore be not merely a rule, but a **validated abstraction relation**.

---

## 20. Assignments Should Carry Their Context Dependencies

A semantic assignment should record what makes it valid.

For example:

```yaml
assignment:
  proposition:
    Voltage(node_x, 3.0)

  context:
    reference_node: ground_A
    unit: volt
    calibration: meter_calibration_17
    sample_context: c_1042

  depends_on:
    - SameReferenceFrame(ground_A)
    - CalibrationValid(meter_calibration_17)
    - NodeIdentityStable(node_x)
```

Or for vision:

```yaml
assignment:
  proposition:
    At(object_42, region_r)

  context:
    camera: camera_2
    calibration: K17
    frame: world_frame_8
    image: frame_991

  depends_on:
    - TrackIdentity(object_42)
    - CalibrationValid(K17)
    - TransformValid(camera_2, world_frame_8)
```

A claim is therefore also a dependency object.

---

## 21. Invalidation Is More Fundamental Than Motion Detection

A system may appear to care about moving things.

But movement is often important only because it threatens previously admitted semantic claims.

Suppose the system currently relies on:

\[
\operatorname{At}(O,x),
\]

\[
\operatorname{Distance}(O,R,d),
\]

\[
\operatorname{Occludes}(O,P),
\]

and:

\[
\operatorname{CollisionFree}(trajectory).
\]

Evidence of movement may invalidate all four.

Thus the useful event is not necessarily:

```text
MOVEMENT DETECTED
```

but:

```text
DEPENDENCIES OF ACTIVE CLAIMS MAY NO LONGER HOLD
```

This suggests:

\[
\boxed{
\text{attention can be understood as prioritizing potential semantic invalidation}
}
\]

Motion is one high-value invalidation signal among many.

---

## 22. Many Non-Motion Events Have the Same Structure

The same architecture handles:

```text
reference voltage changed
→ invalidate voltage assignments

camera calibration changed
→ invalidate image-to-world correspondences

clock synchronization changed
→ invalidate temporal comparisons

object identity became uncertain
→ invalidate tracked-object claims

schema changed
→ invalidate field interpretations

executable digest changed
→ invalidate command semantics

plugin set changed
→ invalidate available-operation claims

unit convention changed
→ invalidate numerical comparisons
```

The common pattern is:

\[
D \text{ changes}
\rightarrow
\operatorname{InvalidateDependents}(D).
\]

This is broader and more useful than treating every change class separately.

---

## 23. Stale Does Not Mean False

When a dependency changes, a claim need not become false.

It may simply stop being justified for reuse.

Therefore the epistemic state should distinguish:

```text
SUPPORTED
CONTRADICTED
STALE
UNKNOWN
```

For example:

```text
camera calibration changed
```

should not automatically imply:

```text
ObjectAt(O, x) is false
```

It may imply only:

```text
previous evidence no longer establishes ObjectAt(O, x)
```

This distinction is essential for safe semantic revision.

---

## 24. Context Change Is an Evidence-Validity Event

The software-level rule:

```text
artifact identity changed
→ cached semantic contract becomes stale
```

can be generalized into:

```text
context dependency changed
→ claims derived under that dependency require reconsideration
```

Let a claim \(P\) have dependency set:

\[
\operatorname{Deps}(P)=\{d_1,\ldots,d_n\}.
\]

Then:

\[
\exists d_i:\operatorname{Invalidated}(d_i)
\rightarrow
\operatorname{Stale}(P).
\]

This turns semantic maintenance into dependency-directed truth maintenance.

---

## 25. History Is a Sequence of Evidence Contexts

A history need not initially be represented as a rich physical theory of time.

It can begin as ordered evidence contexts:

\[
C_0,C_1,C_2,\ldots
\]

with a primitive or observed successor relation:

\[
\operatorname{Next}(C_i,C_{i+1}).
\]

From this relation, the system can construct:

```text
previous
next
before
after
changed since
still supported
became stale
became contradicted
```

when the required ordering properties hold.

Temporal semantics can therefore grow from contextual ordering rather than being assumed in full.

---

## 26. Ordering Can Be Extended by Backtracking Through Contexts

Suppose a claim is supported at \(C_t\) but fails validation at \(C_{t+k}\).

The system may walk backward through prior contexts to identify the earliest relevant dependency transition:

```text
current contradiction
↓
inspect provenance of claim
↓
identify dependencies
↓
walk previous contexts
↓
find last context in which dependencies were valid
↓
locate transition that invalidated reuse
```

This yields richer temporal concepts such as:

```text
valid until
changed at
first contradicted after
stable across interval
re-established at
```

Thus ordering becomes operationally useful through revision and provenance.

---

## 27. Frames Are Not Merely Images

A frame can be generalized as an evidence context.

An image frame is one example.

A frame may contain:

```text
raw observations
current assignments
reference identities
coordinate transforms
calibrations
active object correspondences
admitted claims
uncertain claims
```

Conceptually:

```yaml
context_frame:
  id: C_t
  predecessor: C_t_minus_1
  observations: ...
  assignments: ...
  references: ...
  correspondences: ...
  admitted_claims: ...
  invalidations: ...
```

The frame becomes a semantic snapshot, not merely a sensor sample.

---

## 28. Semantic Attention Can Be Dependency-Directed

A naive perception or discovery system may compare everything against everything.

That scales poorly.

A dependency-aware system can ask:

```text
Which newly changed assignments participate in dependencies of currently useful claims?
```

Then attention can be prioritized by:

```text
number of active claims potentially invalidated
importance of those claims to current targets
uncertainty of correspondence
cost of revalidation
risk of acting on stale semantics
```

A possible priority function is:

\[
\operatorname{Priority}(e)
=
\operatorname{ExpectedInvalidationImpact}(e)
-
\operatorname{RecheckCost}(e).
\]

This makes attention target-relative and semantic rather than merely perceptual.

---

## 29. Motion Is a Derived High-Impact Pattern

Motion can be reconstructed as:

```text
corresponding locus/object across ordered contexts
AND
spatial assignment differs
```

or:

\[
\operatorname{Motion}(O,C_i,C_j)
\leftarrow
\operatorname{Correspond}(O_i,O_j)
\land
\operatorname{Position}(O_i,C_i)=x_i
\land
\operatorname{Position}(O_j,C_j)=x_j
\land
x_i\neq x_j.
\]

This shows that motion is already a composite semantic relation.

Its importance comes from what it tends to invalidate, not necessarily from being foundational.

---

## 30. Mutability Can Also Be Derived

Instead of treating:

```text
Mutable(x)
```

as primitive, the system may discover repeated admissible transitions among assignments to a corresponding locus.

For example:

\[
A(x,C_1)=v_1,
\]

\[
A(x,C_2)=v_2,
\]

\[
v_1\neq v_2,
\]

with correspondence and ordering sufficient to support:

\[
\operatorname{Transition}(x,v_1,v_2,C_1,C_2).
\]

From a family of such transitions it may synthesize:

\[
\operatorname{Mutable}(x,D,C).
\]

Mutability is then a discovered capability of a locus under some context and domain.

---

## 31. Known Mutability Does Not Require Known Consequences

A system may establish:

```text
locus x can occupy multiple states
```

without knowing:

```text
what changing x causes elsewhere
```

These are different semantic claims.

For example:

```text
KNOWN:
    Mutable(x)
    ReachableValue(x, v1)
    ReachableValue(x, v2)

UNKNOWN:
    DownstreamEffect(x, ...)
    Reversibility(x)
    SafetyImpact(x)
```

This is not a defect.

It is correct partial semantics.

---

## 32. Unobservable Consequences Are Still Semantically Possible

Suppose the system can alter a locus but has no observation path to downstream consequences.

It may know:

\[
\operatorname{TransitionPossible}(x,v_1,v_2)
\]

while leaving:

\[
\operatorname{Consequences}(x,v_1\rightarrow v_2)
\]

unknown.

The correct result is not:

```text
there are no consequences
```

but:

```text
no represented evidence route establishes the consequences
```

This is another instance of open-world semantic reasoning.

---

## 33. The Observer Should Not Be Privileged Ontologically

A semantic bootstrapping system is itself part of some interaction graph.

It receives influences from some loci and produces influences toward others.

Calling one direction "observation" and another "action" is useful for planning, but these roles are relative to the system boundary and target.

At a lower structural level:

```text
A influences bootstrapper
bootstrapper state changes
bootstrapper influences B
```

At a higher semantic level:

```text
observe A
reason
act on B
```

The higher description is valuable.

It should not be confused with a fundamental asymmetry in the underlying interaction structure.

---

## 34. Knowledge Effects and World Effects Can Be Reinterpreted Relationally

A goal-directed architecture often distinguishes:

```text
KNOWLEDGE effect
WORLD effect
BOTH
```

That distinction remains useful, but it is target-relative.

An operation classified as `KNOWLEDGE` means primarily:

```text
its intended planner-relevant consequence is a change in admitted semantic state
```

not:

```text
nothing physical changed
```

Likewise a `WORLD` effect may produce observations incidentally.

This gives a cleaner interpretation:

```text
KNOWLEDGE
    semantic-state consequence is primary

WORLD
    target-world consequence is primary

BOTH
    both are planner-relevant
```

The categories classify purpose and modeled consequence, not metaphysical purity.

---

## 35. Reference Frames Are Semantic Reservoirs

The earlier idea of semantic reservoirs can be extended.

Useful semantics may exist not only in:

```text
schemas
registries
metadata
reflection
tests
source
```

but also in structures that establish comparability:

```text
coordinate frames
unit systems
calibration models
clock synchronization
identity maps
alignment transforms
normalization conventions
schema mappings
encoding tables
```

These artifacts do not merely provide facts.

They provide **conditions under which other facts can be meaningfully compared**.

Call them **contextual semantic reservoirs**.

---

## 36. Correspondence Mechanisms Are Semantic Compression Points

A correspondence mechanism may explain large families of comparisons.

Examples include:

```text
camera calibration + pose transform
    maps image loci to world-relative rays

schema migration map
    maps fields across versions

symbol table
    maps names to entities

memory map
    maps addresses to device regions

clock transform
    maps timestamps across domains

unit conversion
    maps measurements across unit systems
```

Instead of manually authoring every pairwise correspondence, the system can discover and validate the mapping mechanism.

This is exactly the same compression strategy used for registries, factories, and generators.

---

## 37. Contextual Rules Can Generate Ordinary Rules

Suppose the system validates a transform:

\[
T_{A\rightarrow B}.
\]

Then many pairwise location relations can be generated lazily:

\[
x_B=T_{A\rightarrow B}(x_A).
\]

Likewise, a validated unit relation:

\[
f:Celsius\rightarrow Fahrenheit
\]

supports many value conversions without separately authoring each value relation.

Thus semantic bootstrapping should search not only for behavioral generators but for **comparison generators**.

---

## 38. Context Should Be Part of Rule Applicability

A rule should not merely state:

\[
P\rightarrow Q.
\]

It may need:

\[
(P \land C)\rightarrow Q
\]

where \(C\) includes the semantic conditions under which the proposition domains are interpretable.

For example:

```text
SameCoordinateFrame(A, B)
AND
SameObjectIdentity(O_A, O_B)
AND
Position(O_A) != Position(O_B)
→ PositionChanged(O)
```

Without the contextual premises, the rule may be syntactically valid but semantically unsound.

---

## 39. The Context Graph and the Rule Graph Are Coupled

A useful architecture may therefore maintain at least two coupled graphs:

```text
SEMANTIC RULE GRAPH
    propositions and derivations

CONTEXT DEPENDENCY GRAPH
    frames, references, identities, mappings, and invalidators
```

A rule derivation may point into the context graph:

```text
claim P
    depends on frame F
    depends on identity I
    depends on transform T
    depends on calibration K
```

A change in \(K\) can then invalidate \(P\) and all downstream claims without recomputing unrelated semantics.

---

## 40. Re-Elaboration Is a General Truth-Maintenance Operation

When a contextual dependency becomes stale:

```text
invalidate dependent claims
↓
identify currently active targets that use them
↓
reopen only affected proof branches
↓
seek new evidence or correspondence
↓
revalidate
↓
readmit claims if justified
```

This is not limited to software version changes.

It applies equally to:

```text
moving objects
changing references
sensor recalibration
schema drift
network topology changes
identity uncertainty
unit changes
configuration changes
```

Thus re-elaboration becomes a universal response to context drift.

---

## 41. History Becomes a Provenance Structure, Not Just a Log

A conventional history records events.

A semantic history should additionally record:

```text
which claims were supported
which evidence supported them
which contexts licensed comparison
which dependencies were active
which invalidations occurred
which rules were reopened
which correspondences were revised
```

Then a question such as:

```text
Why is this no longer believed?
```

can be answered structurally:

```text
claim P
↓
depended on transform T
↓
T was valid through context C17
↓
calibration K changed at C18
↓
T became stale
↓
P was invalidated
↓
new evidence has not yet re-established P
```

This makes temporal explanations proof-carrying.

---

## 42. Temporal Stability Can Become a Discovered Property

If a claim repeatedly survives context transitions without invalidation, the system may learn a stability model.

For example:

```text
wall geometry
    usually stable across many image frames

tracked pedestrian position
    frequently invalidated

camera calibration
    stable until explicit reconfiguration

CLI grammar
    stable until executable/provider identity changes
```

This can improve scheduling.

Stable dependencies can be checked less often.

Volatile dependencies can be monitored more aggressively.

Thus history can teach the system not merely what was true, but **which semantics tend to require reconsideration under which context transitions**.

---

## 43. Attention Can Be Learned From Invalidation History

Suppose event class \(E\) frequently invalidates high-value claims.

The system may learn:

\[
E
\rightarrow
\text{high expected semantic impact}.
\]

Examples:

```text
large optical-flow region
→ likely spatial claim invalidation

package upgrade event
→ likely software-semantic invalidation

reference-clock loss
→ likely timestamp-comparison invalidation

calibration-file change
→ likely geometry invalidation
```

Attention policies can then be learned from prior invalidation structure rather than hand-authored salience rules.

---

## 44. The Primitive Kernel May Be a Contextual Association Kernel

A deeper minimal kernel might avoid domain terms such as:

```text
file
CPU
sensor
input
output
mutable
observable
```

and instead expose operations closer to:

```text
identify candidate locus
associate description with locus under context
record evidence
propose correspondence across contexts
check comparison compatibility
record dependency
order contexts when justified
invalidate dependent claims
reopen derivations
```

Even this vocabulary is not metaphysically primitive.

It is an engineering hypothesis about a small useful meta-ontology.

The research question becomes:

> How small can this contextual association kernel be while still allowing richer semantic roles to be discovered rather than pre-authored?

---

## 45. A Compact Formalization

Let:

\[
\mathcal L
\]

be known or hypothesized loci.

Let:

\[
\mathcal K
\]

be contexts.

Let:

\[
\mathcal A
\]

be contextual assignments.

An assignment may be written:

\[
a=(\ell,k,d,v)
\]

where:

```text
ℓ
    locus

k
    context

d
    assignment domain / interpretation

v
    represented value or description
```

Let:

\[
\Gamma
\]

be contextual correspondence relations.

Let:

\[
\mathcal C
\]

be admitted claims.

Let:

\[
\operatorname{Deps}(c)
\]

return the contextual dependencies of claim \(c\).

Let:

\[
\prec
\]

be an admitted ordering over contexts when available.

Then semantic maintenance contains at least two operations:

\[
\operatorname{Derive}(\mathcal A,\Gamma,\mathcal C)
\rightarrow
\widetilde{\mathcal C}
\]

and:

\[
\operatorname{Invalidate}(\Delta \mathcal K,\Delta \Gamma)
\rightarrow
\mathcal C_{stale}.
\]

Candidates are validated before admission.

Stale claims are reopened rather than silently treated as false.

---

## 46. Comparison Is a Derived Effect

Given assignments:

\[
a_1=(\ell_1,k_1,d_1,v_1)
\]

and:

\[
a_2=(\ell_2,k_2,d_2,v_2),
\]

comparison requires a derivation of:

\[
\operatorname{Comparable}(a_1,a_2).
\]

This may depend on:

```text
domain compatibility
reference compatibility
locus correspondence
unit conversion
alignment
normalization
ordering
```

Only then may an operator such as equality, distance, or ordering be applied.

This prevents representational convenience from being mistaken for semantic comparability.

---

## 47. Change Detection Is a Rule Over Correspondence

A generic candidate rule is:

\[
\operatorname{Correspond}(a_1,a_2)
\land
\operatorname{Comparable}(a_1,a_2)
\land
\neg\operatorname{Equivalent}(a_1,a_2)
\rightarrow
\operatorname{Changed}(a_1,a_2).
\]

But `Changed` should itself remain typed by domain.

Examples:

```text
position changed
schema changed
identity changed
reference changed
value changed
availability changed
```

Different changes invalidate different claim families.

---

## 48. Invalidation Rules Are High-Leverage Semantic Rules

A system should actively discover rules of the form:

\[
\Delta X
\rightarrow
\operatorname{Invalidate}(P_1,\ldots,P_n).
\]

Examples:

```text
reference frame identity changed
→ invalidate coordinates expressed in old frame

camera calibration changed
→ invalidate image/world projections

object correspondence rejected
→ invalidate cross-frame object claims

executable identity changed
→ invalidate extracted command grammar
```

These rules compress future semantic maintenance.

A validated invalidator can be more valuable than many individual factual claims.

---

## 49. The Semantic Frontier Can Be a Context Frontier

Sometimes a claim cannot be established because the object semantics are unknown.

Sometimes the object semantics are known but the comparison context is missing.

For example:

```text
CONTEXT FRONTIER

Target requires:
    ComparePosition(object_A_t1, object_A_t2)

Known:
    coordinates exist in both frames
    units are compatible

Unknown:
    whether object identities correspond
    transform between coordinate frames

Possible extensions:
    establish track correspondence
    recover frame transform
    obtain calibration
    ask human to identify correspondence
```

This is different from lacking a domain rule.

The architecture should distinguish semantic-frontier failures caused by missing contextual structure.

---

## 50. Semantic Discovery and Context Discovery Form One Loop

A deeper combined engine may behave as:

```text
target
↓
interpret using current semantic and contextual knowledge
↓
elaborate proof forest
↓
encounter semantic or comparison gap
↓
ask what locus / frame / domain / correspondence is missing
↓
discover contextual reservoir
↓
propose assignment or correspondence
↓
validate
↓
admit contextual relation
↓
resume semantic elaboration
↓
act / observe / inspect as target requires
↓
receive new evidence context
↓
check invalidators
↓
reopen affected claims
↓
re-elaborate
```

The system is therefore not merely learning rules.

It is learning the coordinate structure in which rules can remain meaningful.

---

## 51. A Minimal Example: Two Arrays Across Frames

Suppose contexts \(C_1\) and \(C_2\) contain arrays \(A\) and \(B\).

A naive system asks:

```python
np.array_equal(A, B)
```

A semantic bootstrapper instead asks:

```text
What does each axis denote?
What domain does each element inhabit?
Do the arrays share a coordinate frame?
If not, is there a transform?
Do positions correspond?
Do channel meanings correspond?
Do the contexts refer to comparable times or states?
```

Only after these obligations are discharged does elementwise comparison become a meaningful semantic operation.

If registration later changes, the comparison result may be invalidated without either raw array changing.

This demonstrates why context dependencies must be first-class.

---

## 52. A Minimal Example: Voltage at a Node

Suppose the system records:

```text
node X = 1.2 V
```

A richer representation is:

```yaml
locus: X
quantity: electric_potential_difference
reference: G
unit: V
value: 1.2
context: C1
```

Later the reference changes from \(G\) to \(G'\).

The numeral `1.2` may remain stored.

But the old proposition cannot safely be compared with a new measurement unless the relation between \(G\) and \(G'\) is known.

The important change is therefore not necessarily at locus \(X\).

It is in the contextual support of the assignment.

---

## 53. A Minimal Example: A Transistor Without Predefined Input/Output

Suppose three terminal loci are available:

\[
L_1,L_2,L_3.
\]

Initially the system need not know:

```text
gate
source
drain
input
output
control
```

It may discover contextual relations among assignments:

```text
variation at L1 correlates with changes in relation between L2 and L3
```

Repeated evidence may support:

\[
\operatorname{AsymmetricInfluence}(L_1,(L_2,L_3),C).
\]

Only after further semantic interpretation might this become:

```text
L1 functions as a control terminal
```

The architecture therefore distinguishes:

```text
observed structural relation
```

from:

```text
domain role assigned to that relation
```

---

## 54. A Minimal Example: From Device Relations to NAND

Suppose a circuit exposes several loci whose continuous assignments can be mapped under validated thresholds into two logical classes.

The system may first establish:

```text
LogicClass(x, LOW)
LogicClass(x, HIGH)
```

relative to:

```text
reference
threshold convention
sampling context
```

It can then discover a relation among three logical loci.

If the resulting relation matches:

\[
\neg(a\land b),
\]

then:

```text
NAND(a,b,out)
```

is a higher-level semantic contract.

The NAND rule is therefore not simply "observed from raw reality."

It depends on an already validated abstraction from physical assignments to logical classes.

---

## 55. Bootstrapping Can Move Both Upward and Downward

Semantic zoom need not be one-directional.

A target may initially use:

```text
NAND gate
```

as a relative primitive.

If validation fails, the system may reopen the abstraction:

```text
NAND
↓
logic thresholds
↓
terminal behavior
↓
reference voltages
↓
physical measurements
```

Conversely, repeated lower-level structure may justify synthesis upward:

```text
physical assignments
↓
logical classes
↓
gate semantics
↓
circuit semantics
```

Thus relative primitives are reopenable in both directions.

---

## 56. The Main Architectural Shift

The earlier semantic-bootstrapping architecture asks:

```text
What semantic structure can be discovered from the accessible environment?
```

The deeper version asks additionally:

```text
Under what context is that structure meaningful?
What establishes correspondence across contexts?
Which comparisons are licensed?
Which claims depend on those contextual relations?
What changes invalidate reuse?
```

The semantic object is no longer just:

```text
rule
```

but something closer to:

```text
rule
+ context
+ correspondence
+ evidence
+ dependency
+ invalidation conditions
```

---

## 57. The Highest-Leverage Cached Object May Be a Contextual Mapper

Earlier semantic bootstrapping suggests that a trusted extractor can be more valuable than hundreds of extracted rules.

The same logic applies to contextual structure.

A trusted mapping such as:

```text
camera frame → world frame
schema V1 → schema V2
clock A → clock B
unit system A → unit system B
logical threshold model → Boolean domain
```

can make enormous families of previously incomparable assignments comparable.

Thus another optimization objective appears:

\[
\text{maximize semantic comparability gained per validated mapping}
\]

This complements:

\[
\text{maximize reusable semantic leverage per validated extractor}.
\]

---

## 58. Failure Mode: Treating Representation Equality as Semantic Equality

Two representations may compare equal while referring to different things.

Examples:

```text
same numeric value under different units
same pixel index under different camera poses
same path after file replacement
same object label assigned to different tracked entities
same enum integer under different schemas
```

Therefore:

\[
\operatorname{RepresentationEqual}(a,b)
\not\Rightarrow
\operatorname{SemanticallyEquivalent}(a,b).
\]

A comparison contract is required.

---

## 59. Failure Mode: Treating Difference as Change

Likewise:

\[
a\neq b
\]

does not imply:

```text
something changed
```

unless the system establishes a correspondence under which \(a\) and \(b\) are descriptions of the same relevant locus or relation across contexts.

Without correspondence, difference may simply mean:

```text
two different things were measured
```

This is particularly important for perception and distributed systems.

---

## 60. Failure Mode: Treating Ground, Origin, or Zero as Universal

Reference conventions can become invisible because they are stable.

This creates brittle semantics.

Examples:

```text
voltage relative to implicit ground
position relative to implicit origin
time relative to implicit epoch
angle relative to implicit axis
index relative to implicit layout
```

A robust system should surface reference dependencies when they matter to comparison, validation, or invalidation.

---

## 61. Failure Mode: Treating Observation as Side-Effect Free

A system may classify an operation as observation-only while the operation changes:

```text
hardware state
cache state
process state
network traffic
measurement loading
observer state
```

The correct abstraction is not necessarily to reject the operation as observation.

It is to record:

```text
primary semantic purpose
relevant perturbations
accepted perturbation bounds
```

Observation is therefore an effect contract, not absence of effect.

---

## 62. Failure Mode: Treating Motion as Intrinsically Salient

A system that checks every moving pattern may waste effort.

The target-relevant question is:

```text
Which changes threaten claims currently used by the planner?
```

Some large visual motion may invalidate nothing important.

A tiny change in a calibration marker may invalidate an entire geometric model.

Semantic attention should therefore be dependency-aware.

---

## 63. Failure Mode: Recomputing Everything After Every Context Change

Once context dependencies are explicit, global recomputation is unnecessary.

The system can propagate invalidation through a dependency graph:

```text
changed dependency
↓
directly dependent claims
↓
downstream derived claims
↓
active target branches using those claims
```

Only affected semantic neighborhoods need to reopen.

This is the temporal counterpart of target-relative semantic discovery.

---

## 64. A Suggested Foundational Prototype

A first prototype for this deeper architecture should avoid CPUs, ROS, filesystems, and other rich semantic surfaces.

Use a deliberately small synthetic environment containing:

```text
several loci
several context frames
a few assignment domains
one or two reference transforms
one hidden correspondence change
one mutable relation
one derived high-level abstraction
```

For example:

```text
two image-like grids under changing alignment
```

or:

```text
three electrical-like loci under changing reference
```

The system should begin without concepts such as:

```text
motion
input
output
control
```

It should attempt to discover enough contextual rules to justify them only when needed.

---

## 65. Prototype Questions

Useful questions include:

```text
Can the system refuse invalid comparisons between structurally similar arrays?

Can it discover a reusable alignment or mapping contract?

Can it distinguish "different value" from "same locus changed"?

Can it invalidate claims when a reference changes even if raw values do not?

Can it derive a control-like asymmetric relation without prelabeling input/output?

Can it preserve mutability while leaving downstream consequences unknown?

Can it identify which historical context first invalidated a cached claim?

Can it reopen only the affected semantic subgraph?

Can it derive temporal notions such as stable-until or changed-since from ordered contexts?
```

These questions test the contextual foundation rather than a particular domain adapter.

---

## 66. Evaluation Metrics

Possible metrics include:

```text
number of primitive semantic roles assumed

number of higher-level roles derived rather than pre-authored

fraction of attempted comparisons correctly rejected as context-incompatible

false change-detection rate caused by broken correspondence

false semantic reuse rate after context change

fraction of stale claims correctly invalidated

fraction of unaffected claims preserved without recomputation

average dependency depth traversed per invalidation

number of pairwise comparisons replaced by reusable mapping contracts

semantic comparability gained per validated mapping

semantic leverage per contextual rule

number of target-relevant abstractions synthesized from lower-level relations

fraction of explanations that identify reference, correspondence, and invalidation provenance
```

A particularly important metric is:

```text
semantic reuse without contextual unsoundness
```

because the architecture is useful only if caching and abstraction do not silently erase the conditions under which claims were meaningful.

---

## 67. The Core May Become Smaller but More Relational

A foundational core may expose operations such as:

```text
locate
associate
contextualize
correspond
compare
order
depend
validate
admit
invalidate
reopen
explain
```

Higher-level providers may then introduce:

```text
observe
intervene
control
input
output
motion
state
mutable
cause
```

as derived or domain-scoped concepts.

This separation reduces the chance that the bootloader silently presupposes the semantics it is intended to discover.

---

## 68. Explanation Should Include the Comparison Context

A proof-carrying explanation should answer not only:

```text
Why do we believe P?
```

but also:

```text
What locus does P describe?
Under which reference frame?
Under which assignment domain?
What makes the compared objects correspond?
Which transform or normalization was used?
Which context ordered these observations?
What would invalidate the comparison?
Which later context last revalidated it?
```

For example:

```text
CLAIM
    ObjectMoved(track_42)

SUPPORTED BY
    position differs between C17 and C18

CORRESPONDENCE
    track_42(C17) ↔ track_42(C18)

REFERENCE
    world_frame_8

VALIDATED BY
    calibration K5
    transform T_camera_to_world

INVALIDATED BY
    track identity rejection
    calibration change
    transform change

LIMITATION
    establishes position change under current correspondence;
    does not establish intentional motion or cause
```

This makes contextual assumptions visible.

---

## 69. New Central Principles

### Context-Before-Value Principle

> A value should be interpreted as an assignment to a locus under a context, not as a free-standing semantic fact.

### Reference-Relativity Principle

> Quantities, coordinates, origins, zeros, and orderings may depend on reference structures whose validity must be preserved.

### Comparison-Contract Principle

> Representations may be compared semantically only after the relevant domains, references, correspondences, and transformations establish comparability.

### Correspondence-Before-Change Principle

> Difference becomes change only after the compared descriptions are linked by an admitted correspondence across contexts.

### Relative-Role Principle

> Input, output, observer, control, and intervention are roles relative to boundaries and interactions, not necessarily intrinsic properties of loci.

### Observation-As-Interaction Principle

> Observation is an interaction whose primary modeled purpose is epistemic; it should not be equated with absence of physical effect.

### Derived-Mutability Principle

> Mutability may be inferred from validated transitions among assignments rather than assumed as a primitive capability.

### Partial-Consequence Principle

> Knowing that a locus can change does not imply knowledge of the downstream consequences of that change.

### Invalidation-Attention Principle

> Prioritize new evidence according to its expected ability to invalidate claims relevant to active targets.

### Stale-Is-Not-False Principle

> A changed dependency invalidates reuse of a claim unless revalidated; it does not automatically establish the negation of that claim.

### Contextual-Reservoir Principle

> Coordinate maps, calibrations, unit systems, identity maps, and synchronization structures are semantic reservoirs because they establish the conditions under which other semantics can be compared.

### Mapping-Compression Principle

> Prefer reusable correspondence and transformation mechanisms over enumerating pairwise relations across contexts.

### Dependency-Directed-Re-Elaboration Principle

> When context changes, reopen only the semantic structure whose validity depends on the changed context.

### History-As-Provenance Principle

> Historical contexts should preserve not only observations but the semantic dependencies, correspondences, and invalidations that explain why claims remained valid or became stale.

### Ordering-From-Context Principle

> Temporal notions such as before, after, changed-since, and stable-until can be constructed from admitted ordering relations among evidence contexts.

---

## 70. A Revised Bootstrapping Stack

The resulting architecture can be summarized as:

```text
TARGET
↓
current semantic claims
↓
context dependencies of those claims
↓
required loci and assignments
↓
required comparison / correspondence contracts
↓
contextual semantic reservoirs
↓
validated mappings and relations
↓
admitted comparisons and candidate rules
↓
semantic elaboration
↓
action / inspection / interaction
↓
new evidence context
↓
context correspondence
↓
change / invalidation detection
↓
dependency-directed re-elaboration
↓
updated semantic claims
```

This is not merely a pipeline for discovering new rules.

It is a system for preserving the conditions under which rules remain meaningful.

---

## 71. The Foundational Research Question Changes Again

The earlier research question is:

> Can a small set of generic semantic discovery methods bootstrap enough correct target-relevant rules from an unfamiliar environment to support useful elaboration?

A deeper question now appears:

> Can the system bootstrap the contextual structure required to know when two descriptions are even comparable, when a difference counts as a change, and when a previously admitted semantic rule must be reopened?

And beneath that:

> Which semantic roles truly need to be primitive, and which can be synthesized from contextual association, correspondence, dependency, and revision?

This tests whether the bootloader is genuinely discovering semantics rather than hiding them in its initial vocabulary.

---

## 72. A More Aggressive Minimality Hypothesis

A strong experiment would begin without predefined concepts of:

```text
input
output
observer
intervention
motion
mutable state
control
```

and provide only enough machinery to represent:

```text
candidate loci
contextual assignments
candidate correspondences
evidence
context ordering
dependencies
validation
invalidation
```

Then test whether target-driven reasoning can synthesize useful higher-level roles.

For example:

```text
repeated asymmetric dependency
→ candidate control relation

corresponding spatial assignment changes across contexts
→ candidate motion relation

repeated reachable assignments at one locus
→ candidate mutability

influence entering a selected system boundary
→ candidate input role

influence leaving that boundary
→ candidate output role
```

The objective is not to prove that these concepts have one universally correct reduction.

It is to test how much useful semantic structure can be derived from a smaller relational substrate.

---

## 73. Conclusion

Semantic bootstrapping becomes more interesting when its own primitives are subjected to the same discipline it applies to domain rules.

A system should not assume that because a quantity is represented numerically it can be compared.

It should not assume that because two observations differ, one object changed.

It should not assume that a signal is intrinsically an input or output.

It should not assume that observation means absence of interaction.

It should not assume that zero, origin, ordering, identity, or temporal alignment are globally given.

Instead, semantic claims should be rooted in contextual structure:

```text
where is the description attached?
under which reference?
in which domain?
relative to which boundary?
what makes two assignments correspond?
what licenses their comparison?
which claims depend on that relation?
what would invalidate it?
```

This produces a deeper semantic bootloader.

It does not merely discover:

```text
what the environment means
```

It discovers:

```text
under which context descriptions become meaningful
how contexts correspond
which abstractions compress those correspondences
and when changing context requires semantic revision
```

The resulting architecture has a natural continuity from low-level physical measurement to high-level software reasoning:

```text
reference-relative physical assignment
↓
validated correspondence
↓
contextual comparison
↓
derived change / influence / control
↓
validated abstraction boundary
↓
semantic rule
↓
provenance and dependencies
↓
invalidation
↓
re-elaboration
```

The deepest reusable knowledge may therefore not be a catalogue of facts, or even only a catalogue of semantic extractors.

It may be a compact set of methods for discovering and maintaining **contextual invariants, correspondences, abstraction mappings, and invalidation structure**.

That is a plausible foundation from which richer notions such as observation, intervention, state, input, output, control, motion, and software behavior can be introduced only when the target and evidence actually require them.
