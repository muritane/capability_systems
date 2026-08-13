# From Legacy State to Endogenous Frontier Expansion: Self-Migration, Bootstrapping, and Capability-Changing Preparedness

## Abstract

A bounded system does not choose its next state from all imaginable states.

It acts from the state it already has.

That state determines:

```text
what it can represent
what it can observe
what it can retrieve
what it can understand
what it can build
what it can change
what it can learn next
what transitions it can afford
```

This creates a stronger problem than ordinary preparedness.

Earlier preparedness can be written as:

\[
\text{known possible state}
\rightarrow
\text{make that state more ready}.
\]

But some actions do more than move a known state closer.

They change the system's future capability set.

They may introduce:

```text
new distinctions
new tools
new methods
new interfaces
new measurement procedures
new abstractions
new transition operators
new reachable states
```

This paper calls that process **capability-changing preparedness**.

A related interpretation is **endogenous frontier expansion**.

The central constraint is:

\[
\boxed{
\text{the system of tomorrow can be reached only through operations available to the system of today}
}
\]

unless an external intervention changes the transition structure.

This makes legacy state unavoidable.

A running system is not designed repeatedly from a blank slate.

It is the result of a path:

\[
S_0
\rightarrow
S_1
\rightarrow
\cdots
\rightarrow
S_t.
\]

Each state inherits dependencies from earlier states while enabling only some next transitions.

Thus:

\[
\boxed{
\text{best imaginable state}
\neq
\text{best reachable next state}
}
\]

and:

\[
\boxed{
\text{current inadequacy}
\neq
\text{permission to reason from a hypothetical future capability}
}
\]

The same structure appears in:

```text
software migration
organizational change
education
human learning
semantic revision
methodology adoption
tool acquisition
scientific instrumentation
institutional reform
AI capability development
```

The resulting control problem is not merely:

```text
What should be ready?
```

It is also:

```text
Which present actions should be taken
because they expand what can become ready later?
```

This extends preparedness from allocation over a fixed possibility set to management of a possibility set that can itself change.

---

## 1. The Current State Comes First

A transition system begins from:

\[
S_t.
\]

It does not begin from:

\[
S^\*,
\]

the state one would prefer to already have.

The currently available action set is:

\[
A_t=A(S_t).
\]

A transition has the form:

\[
S_t
\xrightarrow{a_t\in A(S_t)}
S_{t+1}.
\]

This apparently trivial constraint has strong consequences.

A system cannot directly execute an operation that requires capabilities it does not yet possess.

Thus:

\[
\boxed{
\text{desired operation}
\not\Rightarrow
\text{currently executable operation}
}
\]

---

## 2. Improvement Is Path-Constrained

Suppose the desired state is:

\[
S^\*.
\]

The naive improvement problem asks:

```text
What should the final system look like?
```

The operational problem asks:

```text
What transition can be executed now
that moves the current system toward states
from which better transitions become possible?
```

Thus the relevant structure is:

\[
S_t
\rightarrow
S_{t+1}
\rightarrow
S_{t+2}
\rightarrow
\cdots
\rightarrow
S^\*.
\]

The intermediate states matter.

Some may be temporary.

Some may be inferior to the final state.

Some may exist only to unlock later transitions.

---

## 3. The Best Next State Need Not Be the Best State

Let:

\[
U(S)
\]

be the utility of state \(S\).

A locally available transition may produce:

\[
U(S_{t+1})<U(S^\*).
\]

That does not make the transition irrational.

If:

\[
S^\*\notin \operatorname{Reach}_1(S_t),
\]

then direct comparison with \(S^\*\) is operationally irrelevant.

A more useful objective is:

\[
a_t^\*
=
\arg\max_{a\in A(S_t)}
V(
\operatorname{Reach}_{H}(F(S_t,a))
),
\]

where:

\[
\operatorname{Reach}_{H}(S)
\]

is the set of states reachable from \(S\) within horizon \(H\).

The action can be valuable because it improves the future reachable set.

---

## 4. A Ladder Must Be Built From Inside the Pit

Consider the informal case:

```text
current state:
    in a pit

desired state:
    outside the pit
```

The instruction:

```text
be outside the pit
```

does not define an executable transition.

The useful questions are:

```text
What materials are available?
What actions are possible from here?
Can a foothold be made?
Can a tool be constructed?
Can external help be requested?
Can an intermediate platform be reached?
```

The problem is not solved by describing the target more accurately.

It is solved by finding a realizable transition path.

Thus:

\[
\boxed{
\text{target specification}
\neq
\text{migration procedure}
}
\]

---

## 5. Legacy Is a State Property

A legacy system can be described as:

\[
S_t
=
F(
S_{t-1},
a_{t-1},
\text{history}
).
\]

Its current shape may include:

```text
old interfaces
historical data formats
obsolete assumptions
compatibility layers
organizational habits
trained users
deployment procedures
measurement conventions
contractual dependencies
```

These are not necessarily evidence of irrationality.

They are inherited state.

The system exists in its current form partly because earlier transitions made that form reachable.

---

## 6. Legacy Is Not Merely Oldness

A system can be old without being difficult to change.

A system can be recent and already deeply locked in.

The stronger variable is:

\[
D(S)
=
\text{dependency structure induced by }S.
\]

A useful approximation is:

\[
\operatorname{LegacyPressure}(S)
=
f(
\text{dependency count},
\text{coupling},
\text{switching cost},
\text{retraining cost},
\text{migration latency},
\text{irreversibility}
).
\]

Thus:

\[
\boxed{
\text{legacy}
\approx
\text{historically accumulated transition constraint}
}
\]

rather than simply age.

---

## 7. A Running System Is Necessarily Historical

A functioning system has survived a sequence of prior states.

Therefore:

\[
S_t
\]

contains traces of:

\[
S_0,\ldots,S_{t-1}.
\]

These traces may appear as:

```text
interfaces
defaults
naming conventions
schemas
organizational roles
data
skills
habits
assumptions
physical infrastructure
```

Complete independence from history would normally require replacing the system rather than evolving it.

But replacement itself must still be performed by some current system.

History cannot be removed merely by declaring it irrelevant.

---

## 8. Greenfield Is Usually Local

A project may be called:

```text
greenfield
```

while still depending on:

```text
existing programming languages
existing hardware
existing operating systems
existing organizations
existing funding
existing knowledge
existing legal systems
existing people
existing terminology
```

So even a clean implementation is embedded in inherited infrastructure.

The boundary of the reset is local.

It is not ontological.

---

## 9. The Action Set Is State-Dependent

The action set should therefore be written:

\[
A(S_t),
\]

not merely:

\[
A.
\]

A database without replication capability cannot instantly execute:

```text
migrate with zero-downtime cross-region replication
```

unless the required mechanisms already exist or are first introduced.

Likewise, a person cannot immediately apply an advanced method whose prerequisites are not operationally available.

Thus:

\[
A(S_t)
\neq
A(S_{t+1}).
\]

A transition can change not only the system state but the future action vocabulary.

---

## 10. Capability-Changing Actions

Ordinary actions change state:

\[
S_t\rightarrow S_{t+1}.
\]

Capability-changing actions also modify:

\[
A(S_t)\rightarrow A(S_{t+1}).
\]

Examples include:

```text
installing a compiler
learning algebra
adding observability
creating a new measurement procedure
introducing version control
building a migration adapter
learning a new language
adding a schema field
acquiring a sensor
creating a rollback mechanism
```

These actions have second-order value.

They do something now.

They also change what can be done later.

---

## 11. Preparedness Over a Fixed State Space Is Incomplete

Ordinary preparedness may assume a set:

\[
X=\{x_1,\ldots,x_n\}
\]

of potentially useful states.

The controller chooses:

```text
what to retain
what to prefetch
what to validate
what to keep nearby
what to reconstruct
```

But this assumes the candidate set is already available.

A stronger problem permits:

\[
X_t\rightarrow X_{t+1}.
\]

The future state inventory itself can change.

---

## 12. Endogenous Frontier Expansion

Let:

\[
X_t
\]

be the set of states the system can currently represent as candidates.

Let:

\[
A_t
\]

be the set of operations it can currently execute.

Then a capability-changing action may produce:

\[
(X_t,A_t)
\rightarrow
(X_{t+1},A_{t+1})
\]

with:

\[
X_t\subset X_{t+1}
\]

or:

\[
A_t\subset A_{t+1}.
\]

This is **endogenous frontier expansion**.

The system does not merely move toward an existing frontier.

It changes the frontier-generating space.

---

## 13. Three Kinds of Preparation

A useful decomposition is:

### State preparation

```text
Make a known state more ready.
```

For example:

```text
cache a document
stock an item
load a model
prepare a plan
```

### Exploratory preparation

```text
Reduce uncertainty over known possibilities.
```

For example:

```text
measure
investigate
compare
test
search
```

### Capability-changing preparation

```text
Change the representation or action system
so new possibilities become expressible or reachable.
```

For example:

```text
learn a method
build a tool
add a type
introduce a protocol
create a new measurement basis
```

These are related but not identical.

---

## 14. Filling a Field Is Not Creating a Field

Suppose the current schema is:

```text
candidate:
    cpp_level
    python_level
    linux_level
    ros_level
```

New evidence may change:

```text
cpp_level:
    medium -> high
```

This is a state update.

But suppose an important capability is:

```text
rapid reconstruction of unfamiliar systems
```

and no field exists for it.

Then the system faces a different operation:

\[
D_t\rightarrow D_{t+1}.
\]

This is representational expansion.

Preparedness must therefore distinguish:

\[
\boxed{
\text{prepare a value}
\neq
\text{prepare the capacity to represent a new variable}
}
\]

---

## 15. Learning Can Change the Coordinate System

Learning is often described as:

\[
\text{unknown}
\rightarrow
\text{known}.
\]

But some learning instead performs:

\[
L_t\rightarrow L_{t+1},
\]

where \(L_t\) is the current representational system.

A new concept can introduce:

```text
a variable
a relation
a decomposition
a measurement
a comparison class
a transformation
a causal mechanism
```

Afterward, observations that previously looked identical may become distinguishable.

Thus:

\[
\boxed{
\text{learning can increase representational resolution}
}
\]

---

## 16. Learning Can Change the Action System

Learning may also change:

\[
A_t\rightarrow A_{t+1}.
\]

Before learning a method, the system may be unable to perform some operation.

After learning it, that operation becomes available.

Thus learning can alter:

```text
what can be represented
what can be predicted
what can be built
what can be repaired
what can be tested
what can be communicated
```

This gives learning option value beyond immediate task performance.

---

## 17. Education Is Not Only Information Transfer

A school does not merely transmit a list of propositions.

It also installs:

```text
symbol systems
conceptual distinctions
procedures
measurement conventions
problem decompositions
disciplinary boundaries
methods of proof
ways of asking questions
```

Therefore education partially shapes:

\[
L_t
\]

and:

\[
A_t.
\]

A student inherits a large representational infrastructure before being capable of evaluating that infrastructure.

---

## 18. Bootstrapping Requires Temporary Dependence

A learner cannot evaluate every primitive before using it.

To evaluate a representational system, the learner already needs some representational system.

Thus:

\[
\boxed{
\text{representation precedes full representational critique}
}
\]

operationally.

This does not imply that inherited categories are permanently correct.

It means they can function as scaffolding.

---

## 19. Scaffolding Is Not Ontology

A child may learn:

```text
letter
word
sentence
number
animal
country
city
history
physics
```

These categories permit early coordination and learning.

Their usefulness does not imply:

\[
\text{instructional decomposition}
=
\text{final ontology}.
\]

A scaffold can be necessary for development while remaining revisable later.

Thus:

\[
\boxed{
\text{bootstrapping interface}
\neq
\text{metaphysically privileged structure}
}
\]

---

## 20. Educational Inertia Is a Network Effect

Suppose a representation \(L\) is shared by:

```text
teachers
students
textbooks
tests
databases
institutions
employers
professional communities
```

Then the cost of replacing \(L\) is distributed.

A locally superior representation \(L'\) may require translation across all of those interfaces.

Thus:

\[
U_{\text{deployed}}(L)
\]

depends not only on intrinsic adequacy but on sharedness.

This produces educational and institutional inertia without requiring irrationality.

---

## 21. The Alphabet Is Not the Main Lock-In

A stable alphabet can be highly useful.

The deeper issue is not that schools preserve the same letters.

The stronger lock-in may occur in higher-order distinctions such as:

```text
what counts as a subject
what counts as a skill
what counts as evidence
what counts as a profession
what counts as a valid measurement
what variables appear on an evaluation form
```

These distinctions feed downstream systems.

Once deployed, they become difficult to change.

---

## 22. Curriculum as a Dependency Graph

A curriculum can be approximated as:

\[
G=(V,E),
\]

where:

\[
V=\text{learning states}
\]

and:

\[
E=\text{prerequisite relations}.
\]

For example:

\[
d_1\rightarrow d_4,
\]

\[
d_2\rightarrow d_4,
\]

\[
d_4\rightarrow d_7.
\]

The control problem becomes:

```text
Which distinctions should become operational first
so later high-value distinctions become cheaply reachable?
```

Education is therefore partly readiness scheduling over a dependency graph.

---

## 23. A Textbook Is a Compressed Migration Path

A learner does not normally rediscover a field from first principles.

A mature field provides:

```text
notation
definitions
canonical examples
exercise order
standard decompositions
proof techniques
known failure modes
```

These form a precomputed path through a conceptual state space.

A textbook can therefore be interpreted as:

\[
\boxed{
\text{compressed transition guidance}
}
\]

from one representational state to another.

---

## 24. A Teacher Can Be an External Transition Operator

Let:

\[
e_t
\]

represent external intervention.

Then:

\[
S_{t+1}
=
F(S_t,a_t,e_t).
\]

A teacher, mentor, tool, institution, or collaborator may expose transitions that the learner would not have discovered efficiently alone.

External assistance can therefore change:

\[
\operatorname{Reach}(S_t).
\]

This is the formal analogue of someone lowering a ladder into the pit.

---

## 25. External Rescue Still Requires Compatibility

An external intervention is useful only if it can couple to the current system.

A ladder that cannot be reached does not solve the pit problem.

A proof written in an unknown notation may exist but remain operationally unavailable.

A tool may be powerful but unusable without prerequisites.

Thus:

\[
\boxed{
\text{external availability}
\neq
\text{effective accessibility}
}
\]

and:

\[
\text{intervention value}
=
f(
\text{capability},
\text{compatibility},
\text{access latency},
\text{assimilation cost}
).
\]

---

## 26. Possession Is Not Assimilation

A system may possess:

```text
a book
a software package
a research paper
a dataset
a tool
a new concept description
```

without being ready to use it.

The relevant distance may include:

```text
retrieval
installation
translation
training
validation
practice
integration
schema migration
```

Thus preparedness should include assimilation distance.

---

## 27. Methodologies Are State-Conditioned Too

A methodology is often presented as a prescription:

```text
Do X.
```

But adoption depends on current structure.

A method may assume:

```text
tests
version control
observability
modular interfaces
deployment automation
data quality
organizational authority
measurement discipline
```

If those prerequisites are absent, the method cannot be instantiated directly.

Therefore:

\[
\boxed{
\text{method recommendation}
\neq
\text{method reachability}
}
\]

---

## 28. Today's Methodology and Today's System Co-Evolve

Current systems often reflect methods that were available, affordable, and institutionally legible when major architectural decisions were made.

Later methodologies arise partly in response to limitations observed in systems produced under earlier methods.

Thus:

\[
\text{method}_t
\rightarrow
\text{systems}_{t+1}
\rightarrow
\text{observed failures}
\rightarrow
\text{method}_{t+1}.
\]

Methodologies and deployed systems can therefore appear temporally parallel.

The method of one period helps produce the systems whose difficulties motivate the next method.

---

## 29. Tomorrow's System Requires Today's Transition Work

Suppose a future architecture requires:

```text
clean interfaces
versioned schemas
observability
testability
reversible deployment
```

If the current system lacks these, the future architecture does not appear automatically.

Some of those enabling properties must be introduced now.

Thus:

\[
\boxed{
\text{the system of tomorrow is partly a product of preparedness work performed today}
}
\]

This is obvious operationally.

It is still easy to omit from abstract reasoning.

---

## 30. The Transition Itself Is Productive Work

Migration is often treated as overhead relative to the "real" system.

But if the desired system cannot be reached without migration, then migration is part of production.

Examples include:

```text
adding adapters
writing tests around legacy code
documenting hidden interfaces
introducing observability
creating schema transforms
training users
building rollback paths
```

These operations may deliver little immediate feature value.

Their value lies in changing future reachability.

---

## 31. Enabling Work Has Option Value

Let:

\[
a_e
\]

be an enabling action.

Its immediate reward may be:

\[
R_{\text{now}}(a_e)\approx 0.
\]

But it can expand future choices:

\[
A_{t+1}
=
A_t\cup\Delta A.
\]

Then its value includes:

\[
V_{\text{option}}(a_e)
=
V(A_{t+1})-V(A_t).
\]

Thus:

\[
\boxed{
\text{low immediate output}
\not\Rightarrow
\text{low strategic value}
}
\]

---

## 32. Some Preparation Is Preparation to Prepare

A system may perform an action whose purpose is not to satisfy demand directly.

Instead it reduces the future cost of preparation.

For example:

```text
learn the prerequisite
install the toolchain
build the index
define the schema
create the test harness
add the measurement point
establish the interface
```

This gives a hierarchy:

\[
\text{prepare}
\]

and:

\[
\text{prepare the capacity to prepare}.
\]

Recursive preparedness need not imply infinite regress.

It can stop when expected marginal value becomes low.

---

## 33. Frontier Distance Can Depend on Capability

Earlier readiness distance can be written:

\[
D_t(x).
\]

But \(D_t(x)\) is not necessarily fixed.

After capability-changing action \(a\):

\[
D_{t+1}(x)
<
D_t(x)
\]

for many states \(x\).

For example, a new tool may reduce the cost of an entire family of future operations.

Thus the system can invest in actions that compress the readiness geometry itself.

---

## 34. Capability Can Be a Distance Reducer

Let:

\[
K_t
\]

denote a capability state.

Then:

\[
D(x\mid K_t)
\]

is the distance to usable state \(x\).

A capability-changing action can produce:

\[
K_t\rightarrow K_{t+1}
\]

such that:

\[
D(x_i\mid K_{t+1})
<
D(x_i\mid K_t)
\]

for many \(x_i\).

This provides a formal interpretation of reusable expertise.

---

## 35. Expertise Is Prepared Compression of Future Work

An expert may not actively hold every answer.

Instead expertise may provide:

```text
fast reconstruction
good search priors
useful decompositions
known tools
diagnostic patterns
reliable shortcuts
error recognition
```

Thus expertise can reduce:

\[
L_{\text{ready}}(x)
\]

and:

\[
C_{\text{ready}}(x)
\]

across a broad set of future states.

Expertise is therefore not merely stored content.

It is altered transition economics.

---

## 36. Reusable Methods Are Infrastructure

A method that repeatedly lowers transition cost becomes infrastructure.

Examples include:

```text
algebraic notation
unit tests
version control
coordinate transforms
statistical estimation
debugging procedures
formal types
measurement protocols
```

The method has value not only when actively used.

It changes the cost surface of future tasks.

---

## 37. Open-World Preparedness

A warehouse may know its SKU catalog while remaining uncertain about demand.

A semantic or learning system faces a stronger problem.

It may be uncertain about:

```text
future demand
future states
future distinctions
future action types
future objectives
```

Thus:

\[
X_t
\]

may not enumerate all states that could later matter.

This is **open-world preparedness**.

---

## 38. Unknown Demand and Unknown State Space Are Different

Two uncertainty problems should be separated.

### Demand uncertainty

\[
x\in X
\]

is known, but:

\[
P(\operatorname{Need}(x))
\]

is uncertain.

### State-space uncertainty

A future useful state may satisfy:

\[
x\notin X_t.
\]

The first problem asks which known states to prepare.

The second asks how much resource to allocate toward discovering or enabling states not yet represented.

---

## 39. The Missing Frontier May Be Unnameable

A system can predict:

```text
I may need distinction d later.
```

only if \(d\) is already representable.

But some future failure may arise because the current representation lacks the relevant distinction entirely.

Then:

\[
P(\operatorname{Need}(d))
\]

cannot be estimated directly because \(d\) is not yet a variable.

This is a limit of ordinary prefetch.

---

## 40. Discovery Pressure Is Different From Prefetch Pressure

Prefetch asks:

```text
Which known distinction is likely to become blocking?
```

Discovery asks:

```text
Is there evidence that the current distinction set itself
is failing to preserve important structure?
```

Thus a semantic controller may need:

\[
P_{\text{prefetch}}
\]

and:

\[
P_{\text{expand}}.
\]

The second pressure targets the representation itself.

---

## 41. Expansion Signals

Possible signals of representational frontier failure include:

```text
repeated exceptions
manual overrides
unexplained residual structure
unstable categories
frequent context repair
persistent translation loss
new phenomena repeatedly forced into old fields
high disagreement despite shared evidence
```

These do not prove that the schema must change.

They increase the expected value of investigating alternatives.

---

## 42. Capability Expansion Should Remain Selective

A system cannot expand every possible representational frontier.

That would create:

```text
concept explosion
maintenance cost
fragmentation
poor interoperability
attention overload
migration debt
unstable reasoning
```

Therefore:

\[
\boxed{
\text{open world}
\neq
\text{unbounded elaboration}
}
\]

Capability-changing preparedness remains a resource-allocation problem.

---

## 43. A Rough Expansion Criterion

Let candidate capability-changing action \(a\) have:

\[
C(a)=\text{acquisition cost},
\]

\[
L(a)=\text{latency},
\]

\[
R(a)=\text{risk},
\]

\[
U(a)=\text{recoverability},
\]

and:

\[
\Delta\mathcal R(a)
=
\text{expected expansion of useful reachable states}.
\]

Then one may write schematically:

\[
K_{\text{expand}}(a)
\propto
\frac{
\operatorname{ExpectedFutureValue}(\Delta\mathcal R(a))
\cdot
U(a)
}{
C(a)+L(a)+\operatorname{MaintenanceDebt}(a)
}.
\]

This is not a universal law.

It identifies the relevant tradeoff.

---

## 44. Reachability Is More Useful Than Hypothetical Optimality

A design discussion often compares:

\[
S_t
\]

with:

\[
S^\*.
\]

But action selection should often compare candidate transition paths:

\[
\gamma_1,\gamma_2,\ldots,\gamma_n.
\]

A path has:

```text
cost
latency
risk
irreversibility
intermediate value
compatibility burden
capability gain
future option value
```

The best architecture on paper may be dominated by a less elegant path that can actually be executed safely.

---

## 45. Architecture Is a Trajectory, Not Only a Snapshot

Traditional architectural description often asks:

```text
What components exist?
How are they connected?
```

A migration-aware description additionally asks:

```text
How did this state become reachable?
What transitions remain possible?
Which interfaces are temporary?
Which dependencies block migration?
Which capabilities are being installed for later phases?
```

Thus architecture should sometimes include:

\[
\boxed{
\text{state}
+
\text{transition structure}
}
\]

rather than state alone.

---

## 46. A System Can Be Locally Worse and Globally Better

Suppose an intermediate migration state introduces:

```text
duplicate interfaces
temporary adapters
extra storage
parallel systems
translation layers
```

Locally this may look less elegant.

But if it permits:

```text
incremental migration
rollback
compatibility
measurement
validation
```

then the temporary complexity may increase global transition quality.

Thus:

\[
\boxed{
\text{intermediate redundancy can purchase safe reachability}
}
\]

---

## 47. Reversibility Changes the Reachable Set

A transition that cannot be undone may shrink future options.

A reversible transition preserves them.

Let:

\[
\operatorname{Options}(S)
\]

be the useful future branch set.

Then a highly irreversible action may produce:

\[
|\operatorname{Options}(S_{t+1})|
\ll
|\operatorname{Options}(S_t)|.
\]

A reversible action may permit experimentation while retaining return paths.

This explains why rollback has strategic value beyond error recovery.

---

## 48. Speculative Migration

A future architecture may be uncertain.

Instead of committing immediately, a system can construct:

\[
S_{t+1}^{S},
\]

a speculative state.

It may contain:

```text
a prototype
a shadow deployment
a provisional schema
an experimental curriculum
a candidate abstraction
a parallel measurement
```

If evidence supports it:

\[
S_{t+1}^{S}
\rightarrow
S_{t+1}^{C}.
\]

Otherwise:

\[
S_{t+1}^{S}
\rightarrow
\varnothing.
\]

This extends speculative semantic architecture to migration itself.

---

## 49. Parallel Representations Can Reduce Migration Risk

During representational change, old and new schemas may coexist:

\[
L_t
\parallel
L_{t+1}^{S}.
\]

The system can compare:

```text
predictive performance
decision quality
translation loss
operational cost
user compatibility
failure modes
```

before committing.

This is more robust than silently redefining the old schema in place.

---

## 50. Deprecation Is a Transition Operator

A legacy distinction need not disappear immediately.

It can move through states such as:

```text
active
discouraged
deprecated
translation-only
historical
removed
```

This preserves continuity while shifting future dependence.

Thus conceptual deprecation can be treated like software deprecation:

\[
L_t
\rightarrow
(L_t,L_{t+1})
\rightarrow
L_{t+1}.
\]

---

## 51. Migration Debt Accumulates When Transition Paths Are Deferred

A system may repeatedly postpone structural work.

Each new dependency can increase future migration cost.

Let:

\[
M_t
\]

be migration difficulty.

Then under continued coupling:

\[
M_{t+1}>M_t.
\]

This is distinct from representational debt.

Representational debt concerns mismatch between schema and reality.

Migration debt concerns the accumulated difficulty of moving away from the current state.

The two can reinforce each other.

---

## 52. Preparedness Can Target Migration Debt

Some work is valuable because it reduces:

\[
M_t.
\]

Examples include:

```text
documenting interfaces
isolating dependencies
adding tests
creating adapters
extracting modules
recording provenance
versioning schemas
adding reversible boundaries
```

This does not necessarily change the visible product immediately.

It makes future change cheaper.

---

## 53. Human Habits Can Be Migration Infrastructure

A person may prepare for future conceptual change by learning habits such as:

```text
checking assumptions
tracking provenance
distinguishing measurements from proxies
separating confidence from commitment
keeping alternative hypotheses
asking what would invalidate a claim
```

These habits do not provide specific future answers.

They reduce the cost of later representational revision.

They are capability-changing preparedness at the metareasoning level.

---

## 54. Reasoning Infrastructure Can Be Managed Explicitly

A representational system can maintain metadata such as:

```text
current schema
known domains
defaults
dependencies
invalidators
translation paths
confidence
version
migration candidates
unresolved residuals
```

This does not formalize all thought.

It makes some representational state operationally inspectable.

The objective is not complete symbolic transparency.

It is cheaper safe adaptation.

---

## 55. Reasoning Needs More Than Formalization

It would be too strong to say:

```text
all engineered systems are formal
while reasoning alone remains informal.
```

Engineered systems still contain:

```text
informal requirements
implicit assumptions
organizational conventions
legacy semantics
human interpretation
unknown failure modes
```

The more defensible claim is narrower:

\[
\boxed{
\text{artifact engineering has developed explicit migration disciplines}
\text{ that conceptual infrastructure often lacks}
}
\]

The opportunity is to transfer control principles, not to pretend all semantics can be compiled.

---

## 56. Semantic DevOps as a Structural Analogy

A mature operational discipline may:

```text
preserve working state
track dependencies
monitor invalidators
test changes
stage migrations
keep experiments provisional
observe failures
rollback unsafe changes
deprecate old interfaces
retain compatibility where valuable
```

A representational system faces structurally similar pressures.

Thus one can imagine a discipline of semantic operations:

```text
semantic versioning
schema observability
dependency tracking
staged ontology change
translation testing
provisional distinctions
rollback
deprecation
```

The analogy is useful when treated as control transfer rather than identity.

---

## 57. Self-Migration Is Metareasoning

Ordinary reasoning asks:

```text
What should I conclude?
```

Preparedness asks:

```text
What should I make ready?
```

Self-migration asks:

```text
What should I change about my current capabilities
so better future reasoning and action become reachable?
```

This is a metalevel decision.

It selects operations that modify the future decision system.

---

## 58. A General State Model

Let:

\[
S_t
\]

be operational state.

Let:

\[
L_t
\]

be representational state.

Let:

\[
K_t
\]

be capability state.

Let:

\[
A(S_t,L_t,K_t)
\]

be currently executable operations.

Let:

\[
E_t
\]

be external interventions.

Then:

\[
\boxed{
(S_{t+1},L_{t+1},K_{t+1})
=
F(
S_t,
L_t,
K_t,
a_t,
E_t
)
}
\]

with:

\[
a_t
\in
A(S_t,L_t,K_t).
\]

This makes current-state dependence explicit.

---

## 59. Reachable State Sets

Define:

\[
\mathcal R_H(S_t,L_t,K_t)
\]

as the set of states reachable within horizon \(H\).

A capability-changing action is valuable partly when:

\[
\mathcal R_H(
S_{t+1},
L_{t+1},
K_{t+1}
)
\]

contains high-value states absent from:

\[
\mathcal R_H(
S_t,
L_t,
K_t
).
\]

Thus action evaluation can include reachable-set expansion.

---

## 60. Reachability Has Quality, Not Only Size

A larger reachable set is not automatically better.

New states can introduce:

```text
danger
confusion
maintenance debt
coordination cost
irreversibility
security exposure
```

Therefore useful reachability should be weighted.

Let:

\[
V(\mathcal R)
\]

measure expected value over reachable states rather than cardinality.

Then:

\[
\Delta V_{\mathcal R}(a)
=
V(\mathcal R_{t+1})
-
V(\mathcal R_t).
\]

---

## 61. The Transition Graph Is Part of Preparedness

A preparedness graph contains:

```text
states as nodes
transitions as edges
```

with edge attributes such as:

\[
(
\text{cost},
\text{latency},
\text{risk},
\text{resource requirements}
).
\]

Capability-changing actions can modify the graph itself.

They may:

```text
add edges
remove edges
reduce edge cost
reduce latency
add nodes
change observability
change recoverability
```

This is more than moving through the graph.

It is graph editing while traversing it.

---

## 62. The System Is Both Traveler and Road Builder

This gives a compact analogy:

\[
\boxed{
\text{ordinary control}
=
\text{choose a path through a graph}
}
\]

while:

\[
\boxed{
\text{self-migration}
=
\text{choose a path while selectively changing the graph}
}
\]

The system consumes current resources both to move and to improve future movement.

This creates a direct competition between immediate progress and enabling work.

---

## 63. Exploitation, Exploration, and Expansion

A useful action taxonomy is:

### Exploitation

Use current capabilities to satisfy present demand.

### Exploration

Reduce uncertainty within the current representational and action space.

### Expansion

Change the representational or action space itself.

Thus:

\[
A_t
=
A_{\text{exploit}}
\cup
A_{\text{explore}}
\cup
A_{\text{expand}}.
\]

The optimal allocation depends on horizon, urgency, uncertainty, and option value.

---

## 64. Expansion Can Be Mistaken for Waste

Expansion work often produces delayed returns.

It can look like:

```text
overengineering
unnecessary learning
premature abstraction
tool building
infrastructure work
research without immediate output
```

Sometimes those criticisms are correct.

But immediate output is not the only objective.

The relevant question is:

\[
\text{Does the expansion reduce enough future cost or unlock enough future value?}
\]

---

## 65. Premature Expansion Is Also a Failure Mode

Capability expansion can be overdone.

A system may build:

```text
frameworks never used
ontologies too rich to maintain
tools without demand
abstractions before evidence
skills with low reuse
migration layers for hypothetical futures
```

This consumes current capacity and creates maintenance obligations.

Thus:

\[
\boxed{
\text{capability-changing preparedness}
\neq
\text{prepare every conceivable capability}
}
\]

---

## 66. Frontier Expansion Needs Hysteresis

The system should not redesign itself after every anomaly.

Nor should it wait until failure becomes catastrophic.

A useful policy may require:

\[
\theta_{\text{expand}}
\]

for beginning structural investigation and a stronger:

\[
\theta_{\text{commit}}
\]

for committing the new capability or representation.

This separates:

```text
notice pressure
explore alternative
prepare candidate
validate
commit
```

---

## 67. Learning Is a Speculative Investment

A learner rarely knows exactly which future tasks will occur.

Learning therefore has:

```text
acquisition cost
maintenance cost
forgetting
future reuse probability
transfer value
option value
```

Long-horizon learning is partly speculative.

Its success should not be judged by:

```text
Was every learned item later used directly?
```

but by:

```text
Did the capability reduce future stalls,
enable valuable options,
or compress later learning?
```

---

## 68. Prerequisites Create Compounding Preparedness

Suppose learning \(d_1\) makes \(d_2\) cheaper:

\[
C(d_2\mid d_1)
<
C(d_2).
\]

And \(d_2\) makes \(d_3\) cheaper.

Then:

\[
d_1\rightarrow d_2\rightarrow d_3
\]

creates compounding preparedness.

The value of \(d_1\) may therefore be poorly estimated by its direct use alone.

---

## 69. Foundational Knowledge Has High Fan-Out

In a dependency graph, some distinctions have many descendants.

Let:

\[
\operatorname{FanOut}(d)
\]

measure the number or value of later capabilities that depend on \(d\).

A high-fan-out distinction can have large option value even when immediate demand is low.

This provides one reason foundational education can be rational under uncertain futures.

---

## 70. But Foundations Can Become Fossils

High fan-out also creates lock-in.

Once many later structures depend on \(d\):

\[
C(\text{replace }d)
\uparrow.
\]

Thus the most useful foundations can become the hardest to revise.

This produces a structural tension:

\[
\boxed{
\text{foundation value}
\leftrightarrow
\text{foundation lock-in}
}
\]

A good architecture should preserve translation and migration paths around important foundations.

---

## 71. Education Faces the Same Preparedness Economy

Education cannot teach:

```text
everything
at full depth
to everyone
before any need appears.
```

It must allocate limited:

```text
time
attention
practice
instruction
feedback
memory
institutional capacity
```

across uncertain future needs.

Therefore education is partly an economics of preparedness.

But unlike ordinary inventory, it can also change the learner's future representational and action spaces.

---

## 72. A Curriculum Should Consider Reachability Gain

A curriculum objective might include:

\[
\operatorname{Value}(d)
=
\operatorname{ImmediateUse}(d)
+
\operatorname{FutureReuse}(d)
+
\operatorname{ReachabilityGain}(d)
-
\operatorname{AcquisitionCost}(d)
-
\operatorname{MaintenanceCost}(d).
\]

Here:

\[
\operatorname{ReachabilityGain}(d)
\]

captures how much learning \(d\) lowers the cost of later learning or action.

This differs from testing only whether \(d\) is directly useful.

---

## 73. Current Schemas Influence What Looks Worth Preparing

A deeper recursion appears when:

\[
L_t
\]

influences the estimated value of future capabilities.

Then:

\[
L_t
\rightarrow
\text{noticed opportunities}
\rightarrow
\text{preparation choices}
\rightarrow
L_{t+1}.
\]

If the current schema cannot represent opportunity \(x\), then the system may assign it no preparation value.

Not because \(x\) is worthless.

Because \(x\) is invisible under the current representation.

---

## 74. Preparedness Has an Observability Problem

A system can prepare only for pressures it can detect or anticipate.

Thus capability-changing preparedness requires signals that current preparedness estimates are themselves incomplete.

Possible meta-signals include:

```text
surprising transfer failures
persistent anomalies
unexplained learning difficulty
repeated need for new ad hoc concepts
large translation losses
tasks that become easy only after reframing
```

These are not direct descriptions of the missing future capability.

They are evidence that expansion may have value.

---

## 75. The Rescue Problem Is Really an Interface Problem

External help can reduce migration latency enormously.

But the intervention must connect to the current state.

Thus rescue can be modeled as constructing an interface:

\[
T_{\text{external}\rightarrow\text{current}}.
\]

Good teaching, tooling, documentation, and mentorship frequently provide such interfaces.

They translate advanced structure into a sequence the current system can absorb.

---

## 76. Mature Knowledge Systems Store Transition Paths

A mature discipline does not only store conclusions.

It often stores:

```text
introductory sequences
worked examples
debugging heuristics
proof templates
measurement standards
migration guides
compatibility tables
failure cases
```

These encode paths through difficult state transitions.

Civilization therefore accumulates not only knowledge states but **transition infrastructure**.

---

## 77. Culture Is Partly a Shared Capability Cache

A community can make expensive distinctions cheap for individuals by preserving them externally.

Examples include:

```text
language
notation
books
software
institutions
schools
standards
libraries
tools
ritualized procedures
```

The individual need not reconstruct every distinction from raw observation.

Shared infrastructure lowers reacquisition cost.

This is a social form of preparedness.

---

## 78. Shared Infrastructure Also Creates Shared Blind Spots

If a community reuses the same schemas, it gains coordination.

But it may repeatedly:

```text
ask the same kinds of questions
measure the same variables
teach the same categories
reward the same skills
store the same distinctions
```

This can suppress alternatives.

Thus:

\[
\text{shared preparedness}
\rightarrow
\text{shared efficiency}
\]

and potentially:

\[
\text{shared preparedness}
\rightarrow
\text{shared schema inertia}.
\]

---

## 79. The Goal Is Not Permanent Novelty

A system that continually replaces its own primitives would lose:

```text
comparability
interoperability
memory
coordination
reliability
reuse
```

Therefore:

\[
\boxed{
\text{self-migration}
\neq
\text{constant self-reinvention}
}
\]

The useful objective is stable operation with preserved capacity for structural change.

---

## 80. Stability Should Be Operational, Not Absolute

A representation, method, or architecture can be treated as fixed for current work while remaining revisable under sufficient pressure.

Thus:

\[
\boxed{
\text{use the current system as real infrastructure}
}
\]

and simultaneously:

\[
\boxed{
\text{do not confuse current infrastructure with the only possible infrastructure}
}
\]

This is the practical balance between continuity and adaptability.

---

## 81. The Current State Is Not an Excuse for Inertia

Path dependence explains why direct jumps are unavailable.

It does not justify refusing reachable improvements.

A system can ask:

```text
Which dependency can be removed?
Which interface can be isolated?
Which capability can be learned?
Which measurement can be added?
Which rollback path can be created?
Which future transition can be made cheaper?
```

The current state is the starting condition.

It is not the terminal argument.

---

## 82. The Future State Is Not an Excuse for Fantasy

Conversely, describing an ideal future architecture does not make it actionable.

A useful future specification should connect to:

```text
current capabilities
migration stages
resource budgets
intermediate states
compatibility requirements
validation
rollback
```

Otherwise:

\[
S^\*
\]

is a specification without a transition model.

---

## 83. Migration Planning Is Frontier Scheduling

At each time step, the system can allocate effort among:

```text
current execution
maintenance
repair
known future preparedness
exploration
capability expansion
migration
validation
rollback protection
```

These compete for resources.

Thus migration becomes another frontier in the preparedness economy.

---

## 84. Capability Frontiers

A general frontier set may include:

\[
F_t=
(
F_{\text{execution}},
F_{\text{retrieval}},
F_{\text{validation}},
F_{\text{maintenance}},
F_{\text{prediction}},
F_{\text{commit}},
F_{\text{migration}},
F_{\text{capability}}
).
\]

The capability frontier asks:

```text
Which currently unavailable operations or distinctions
should the system invest in making reachable?
```

The migration frontier asks:

```text
How far has the current system moved toward a replacement structure?
```

---

## 85. Capability Pressure

Define:

\[
P_{\text{capability}}
\]

as pressure created when valuable future continuation depends on abilities not currently available.

Possible causes include:

```text
repeated expensive manual work
high latency to reconstruct methods
important tasks blocked by missing tools
schema failures
new environmental demands
high-value opportunities outside current competence
```

Capability pressure competes with immediate execution pressure.

---

## 86. A Capability Prefetch Principle

A general principle is:

\[
\boxed{
\textbf{Capability Prefetch Principle}
}
\]

> When a future class of valuable tasks is sufficiently probable, expensive to enter reactively, and enabled by a reusable capability that can be acquired at acceptable current cost, begin acquiring that capability before the first blocking demand.

This extends semantic prefetch from distinctions to transition machinery.

---

## 87. An Endogenous Frontier Principle

\[
\boxed{
\textbf{Endogenous Frontier Principle}
}
\]

> A bounded adaptive system should allocate some resources not only to moving known states toward readiness, but also to actions that improve the value, size, accessibility, or observability of its future reachable state space when the expected option value exceeds acquisition and maintenance cost.

This is the central extension.

---

## 88. A Current-State Realism Principle

\[
\boxed{
\textbf{Current-State Realism Principle}
}
\]

> Evaluate improvement from operations available to the current system, not from capabilities that exist only in the target system.

This prevents hypothetical architecture from being mistaken for an executable migration plan.

---

## 89. A Bootstrap Interface Principle

\[
\boxed{
\textbf{Bootstrap Interface Principle}
}
\]

> Early representations and methods may be accepted as operational scaffolds before they can be fully evaluated, provided the system preserves later paths for critique, refinement, translation, or replacement.

This describes education, training, and early system construction without treating initial schemas as permanent ontology.

---

## 90. A Transition Infrastructure Principle

\[
\boxed{
\textbf{Transition Infrastructure Principle}
}
\]

> Systems should retain or construct low-cost paths between important representational and operational states when future change is sufficiently valuable.

Examples include:

```text
adapters
version maps
migration scripts
teaching sequences
conversion procedures
rollback checkpoints
compatibility layers
```

Transition infrastructure is preparedness for change itself.

---

## 91. A Reachability-Weighted Preparedness Principle

\[
\boxed{
\textbf{Reachability-Weighted Preparedness Principle}
}
\]

> Preparation value should include not only the expected future use of the prepared state, but also the value of later states and actions that become cheaper or newly reachable because of it.

This captures prerequisite, tooling, and foundational-learning effects.

---

## 92. A Non-Finality Principle

\[
\boxed{
\textbf{Non-Finality Principle}
}
\]

> Treat currently deployed representations and methods as operationally real but not structurally final.

This preserves the advantages of stable infrastructure without turning deployment history into ontology.

---

## 93. A Complete Control Loop

A capability-aware preparedness system can execute:

```text
CURRENT STATE
↓
what is demanded now?
↓
can current capability satisfy it?
├── yes
│   ↓
│   execute using current committed infrastructure
│
└── no
    ↓
    is required state already recoverable?
    ├── yes → retrieve / reactivate / revalidate
    └── no
        ↓
        is the problem missing information,
        missing capability,
        or missing representation?
        ↓
        choose local recovery or structural expansion
↓
observe cost / latency / outcome

IN PARALLEL:
↓
estimate future demand
↓
estimate likely expensive misses
↓
estimate capability gaps
↓
estimate reusable enabling actions
↓
compare immediate cost with future reachability gain
↓
spare suitable capacity?
├── no → preserve current operation
└── yes
    ↓
    learn / build / instrument / translate / migrate
    ↓
    keep risky structures provisional where possible
    ↓
    validate
    ↓
    commit, retain, deprecate, or rollback

ON STRUCTURAL PRESSURE:
↓
inspect repeated residuals and exceptions
↓
ask whether current variables remain sufficient
↓
prototype alternative representation
↓
preserve translation to existing infrastructure
↓
migrate only when expected decision and reachability gain
justify coordination and compatibility cost
```

---

## 94. A Compact Formal Architecture

Let:

\[
S_t
\]

be current operational state.

Let:

\[
L_t
\]

be current representational architecture.

Let:

\[
K_t
\]

be current capability state.

Let:

\[
B_t
\]

be resource budgets.

Let:

\[
D_t
\]

be current demand.

Let:

\[
\hat D_{t+1:t+H}
\]

be predicted demand.

Let:

\[
\mathcal R_H(S_t,L_t,K_t)
\]

be the useful reachable state set within horizon \(H\).

Let:

\[
A_t=A(S_t,L_t,K_t,B_t)
\]

be currently executable actions.

Then action selection may be written schematically as:

\[
a_t^\*
=
\arg\max_{a\in A_t}
\left[
V_{\text{current}}(a)
+
V_{\text{preparedness}}(a)
+
V_{\text{reachability}}(a)
-
C(a)
-
R(a)
-
M(a)
\right],
\]

where:

\[
V_{\text{current}}
\]

captures present target value,

\[
V_{\text{preparedness}}
\]

captures improved readiness for known future states,

\[
V_{\text{reachability}}
\]

captures value from changing future capabilities or state accessibility,

\[
C
\]

is acquisition cost,

\[
R
\]

is risk,

and:

\[
M
\]

is maintenance and migration burden.

Then:

\[
(S_{t+1},L_{t+1},K_{t+1})
=
F(
S_t,L_t,K_t,a_t,E_t
).
\]

The central difference from fixed-space preparedness is:

\[
\boxed{
\mathcal R_{t+1}
\text{ may differ structurally from }
\mathcal R_t
}
\]

because the system can change the space from which later actions are chosen.

---

## 95. Why This Sounds Obvious

The local rules are familiar:

```text
use what you have
learn prerequisites
prepare early when delay is costly
do not rewrite everything at once
keep rollback paths
migrate incrementally
preserve compatibility
invest in reusable tools
```

Each statement is ordinary.

The stronger claim is that they may be instances of one abstract control problem.

That problem combines:

\[
\boxed{
\begin{aligned}
&\text{bounded current state}\\
+&\text{state-dependent action sets}\\
+&\text{unequal transition cost and latency}\\
+&\text{uncertain future demand}\\
+&\text{path dependence}\\
+&\text{representational incompleteness}\\
+&\text{capability-changing actions}\\
\end{aligned}
\Rightarrow
\text{endogenous frontier management}.
}
\]

The novelty is not that one should prepare for the future.

It is that preparation can change the system that will confront the future.

---

## 96. The Deeper Realism

A system cannot operate from hypothetical capability.

It must use:

\[
S_t,
L_t,
K_t
\]

as they currently exist.

But treating the present as real does not require treating it as final.

The correct posture is:

```text
use current infrastructure
preserve current continuation
identify high-value future gaps
invest selectively in enabling transitions
keep uncertain changes reversible
expand capability before critical demand when justified
migrate dependencies gradually
retain paths back when possible
```

This is neither static conservatism nor unconstrained redesign.

It is transition-aware adaptation.

---

## 97. Conclusion

A bounded system inherits a current state.

That state carries:

```text
capabilities
schemas
dependencies
interfaces
skills
tools
historical commitments
transition constraints
```

It therefore cannot simply choose an ideal future architecture.

It must construct a path.

Ordinary preparedness asks:

```text
Which known future state should be made ready now?
```

Capability-changing preparedness adds:

```text
Which present action should be taken
because it will change what future states
can be represented, reached, prepared, or recovered?
```

This yields a stronger control problem:

\[
\boxed{
\text{not only allocate preparedness over possible futures}
}
\]

but:

\[
\boxed{
\text{allocate resources partly toward changing the space of possible futures}
}
\]

Education does this when foundational distinctions make later learning cheaper.

Tool building does it when a reusable capability lowers the transition cost of many later tasks.

Migration does it when current infrastructure is modified so a future architecture becomes reachable.

External assistance does it when a teacher, institution, document, or tool exposes a transition path unavailable to the isolated system.

Representational revision does it when a new distinction makes previously collapsed states separable.

The system is therefore not merely choosing where to move.

It is partly constructing the roads from which later movement will be possible.

The corresponding principle is:

\[
\boxed{
\textbf{Endogenous Frontier Management}
}
\]

\[
\boxed{
\begin{minipage}{0.88\linewidth}
A bounded adaptive system should operate from its current state while selectively investing in actions that improve the readiness, observability, recoverability, and reachability of valuable future states. Because some actions modify the system's own representational and operational capabilities, preparedness must include not only movement toward known frontiers but controlled expansion of the frontier space itself.
\end{minipage}
}
\]

The system of tomorrow cannot normally be invoked directly.

It must be made reachable by the system of today.
