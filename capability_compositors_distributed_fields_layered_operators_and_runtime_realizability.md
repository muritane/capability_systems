# Capability Compositors: Distributed Fields, Layered Operators, and the Runtime Construction of Realizability

## Abstract

Many systems are described as if they act directly on isolated objects.

A compiler acts on a program.

A scheduler acts on processes.

A logic gate acts on bits.

A shop acts on customers and products.

A chemical reaction acts on molecules.

A physical law acts on particles or fields.

These descriptions are useful, but they suppress an important intermediate structure.

The systems normally act through typed, distributed state over some declared domain.

A compiler resolves names, propagates types, tracks liveness, estimates aliasing, and transforms intermediate representations over program locations.

A scheduler evaluates readiness, priority, deadlines, affinity, resource demand, and dependency state over addressable processes.

A digital gate exposes logic level, timing, fan-out, power, and noise margins over circuit terminals and components, while lower semiconductor organization realizes those effective quantities.

A store maintains inventory, price, demand, accessibility, checkout load, replenishment, authority, and payment relations over products, customers, locations, and time.

Chemistry organizes possible transitions through molecular structure, bond relations, concentrations, potentials, geometry, and environmental conditions.

Physics often represents distributed quantities directly as fields over spacetime or configuration space.

This suggests a general architecture:

> Many practical systems compute over typed fields defined on addressable domains, apply operators that compose or transform those fields, and realize transitions through layered physical or organizational implementations.

The claim is not that every system should be reduced to one universal scalar field.

Nor is it that effective software objects are unreal because their implementations ultimately involve electrical or material transitions.

The claim is that object identity, addressability, distributed state, operator applicability, and realized transition should be separated.

A process identifier is not the process state.

A memory index is not the value stored there.

A product identifier is not inventory.

An atom label is not a bond.

A coordinate is not a physical field value.

The address identifies a position, entity, region, relation, or configuration in a domain.

A field assigns typed values or relations over that domain.

An operator declares how admissible inputs may be transformed.

A transition is an actual change produced through some realized implementation.

Composition connects compatible outputs and inputs, including across abstraction layers.

From these distinctions, many apparently separate concepts become derived:

```text
capability
=
a reachable or supportable transition region
```

```text
mode
=
a qualitative selector over active fields and operators
```

```text
provider
=
an organization or domain region satisfying an interface
```

```text
closure
=
a mutually dependent composition solved as a fixed point
```

```text
margin
=
derived slack between support and requirement fields
```

```text
layer
=
a stable interface boundary that suppresses internal realization detail
```

```text
invocation
=
an addressed request to resolve and exercise some operator or capability
```

The resulting runtime can be divided into three complementary organizations:

```text
capability resolver
=
resolve the invocation, types, providers, and dependency closure
```

```text
capability compositor
=
align domains, activate modes, compose fields, solve closures,
and compute realizability and viability margins
```

```text
navigator or guidance system
=
select locally executable transitions from the composed capability frontier,
observe outcomes, and revise the model
```

The central proposal is:

> A capability compositor is a typed reactive runtime that constructs higher-order realizability fields from distributed state, explicit operators, hierarchical modes, solved dependency closures, and evidence-indexed interfaces.

It does not replace compilers, schedulers, control systems, physical models, chemical models, stores, or planning systems.

It identifies a shared architectural pattern through which their effective state, constraints, interfaces, and transition possibilities can be composed without collapsing their distinct levels of explanation.

---

## 1. Starting Point

Consider the statement:

```text
the compiler acts on memory indices
```

This can be true at one level.

A compiler implementation reads and writes memory.

Its symbols, graphs, instructions, and analyses are represented through addressable storage.

But the compiler is usually not specified as:

```text
change electron configuration at physical memory location 872193
```

It is specified through structures such as:

```text
token
syntax node
symbol
type
basic block
instruction
control-flow edge
data-flow fact
register candidate
memory effect
```

The memory address is part of the realization.

The compiler's effective semantics operate over a higher-level represented domain.

Likewise:

```text
the scheduler acts on process IDs
```

is incomplete.

The PID supplies an addressable handle.

Scheduling depends on fields such as:

```text
ready state
priority
deadline
CPU demand
affinity
fairness debt
blocking relation
memory pressure
I/O state
security class
```

The scheduler does not choose the numerically smallest PID merely because the PID exists.

It evaluates distributed state associated with addressable processes.

The first distinction is therefore:

```text
address
!=
state
```

and:

```text
carrier
!=
effective domain
```

---

## 2. Addressability Before Field Evaluation

A field requires some way to distinguish where its values apply.

The domain may contain:

```text
spatial coordinates
time intervals
memory locations
instructions
processes
customers
products
machines
atoms
molecules
bonds
roles
permissions
states
interfaces
configurations
```

Let:

\[
D
\]

be a domain of distinguishable positions, entities, regions, or configurations.

An address function may provide a stable handle:

\[
\operatorname{Addr}:D\to I
\]

where \(I\) is an identifier space.

Examples include:

```text
virtual address
process identifier
SKU
customer account
ROS topic name
atom index
mesh coordinate
database key
symbol name
```

An address does not need to contain the state of the addressed entity.

It only needs to locate or distinguish it sufficiently for the current organization.

Thus:

> Addressability provides coordinates for organization; it does not determine the organized values attached to those coordinates.

---

## 3. Domain Is Broader Than Physical Space

The word `field` often suggests a function over physical space.

That is one important case.

But the relevant domain may instead be:

```text
program locations
process population
product catalog
organizational roles
network endpoints
state-machine modes
molecular configurations
possible plans
authority classes
```

A field may therefore be written generally as:

\[
F:D\rightharpoonup V
\]

where:

```text
D = declared domain
V = typed value space
```

The partial arrow indicates that the field may only be defined over a support region:

\[
\operatorname{supp}(F)\subseteq D.
\]

Examples include:

\[
L:\operatorname{Instruction}\to\mathcal P(\operatorname{Variable})
\]

for variable liveness,

\[
R:\operatorname{Process}\to\{\text{ready},\text{blocked},\text{running}\}
\]

for scheduler state,

\[
I:\operatorname{Product}\times\operatorname{Store}\times\operatorname{Time}
\to
\mathbb N
\]

for inventory,

and:

\[
B:\operatorname{Atom}\times\operatorname{Atom}\to\operatorname{BondState}
\]

for a bond relation.

The domain need not be continuous.

It may be:

```text
continuous
discrete
graph-structured
relational
hierarchical
hybrid
configuration-valued
```

---

## 4. A Field Is Not Necessarily Fundamental Physics

Calling a distributed quantity a field does not claim that it is a fundamental physical field.

A compiler liveness field is not proposed as a new force of nature.

A customer-demand field is not a material substance.

A permission field is not a microscopic particle distribution.

These are effective organizational fields.

They summarize stable task-relevant distinctions over declared domains.

The relation is:

```text
physical realization
        supports
effective organization
        exposes
task-relevant field
```

A high-level field remains real as an operative representation or constraint when it is realized by some carrier and participates in actual computation or coordination.

Thus:

> A field may be substrate-general without being substrate-free.

---

## 5. Layers Do Not Remove Realization

A NAND gate may be analyzed through:

```text
electron and hole motion
electromagnetic potential
semiconductor junction behavior
transistor current
terminal voltage
logic level
Boolean function
```

These are not competing claims about one exclusive level.

They are layered descriptions connected by realization relations and interface contracts.

At the logic layer:

\[
\operatorname{NAND}:\{0,1\}^2\to\{0,1\}.
\]

At a circuit layer, acceptable voltage intervals realize the logical values.

At a device layer, transistor organization realizes the voltage transformation.

At a material layer, charge-carrier and field dynamics realize transistor behavior.

The logic operator does not directly mention every electron.

Its validity depends on the lower layers preserving the logic contract.

The important relation is:

```text
lower-level transition organization
        realizes
higher-level operator contract
```

not:

```text
higher-level description
        replaces
lower-level reality
```

---

## 6. Effective Fields Compress Lower-Level Organization

A higher-level field often compresses many lower-level states.

For example:

```text
gate_output = HIGH
```

suppresses:

```text
exact carrier distribution
thermal fluctuation
microscopic timing variation
material defects
electromagnetic coupling
```

The compression is valid only within a declared tolerance.

Likewise:

```text
process = READY
```

suppresses:

```text
kernel data structures
interrupt state
cache contents
memory mappings
device queues
```

and:

```text
product_available = true
```

may suppress:

```text
shelf position
warehouse stock
staff access
checkout status
reservation state
payment compatibility
```

Abstraction therefore creates effective fields by preserving distinctions relevant to a selected interface.

---

## 7. The Minimal Primitive Kernel

A useful reduced kernel can begin with five primary notions:

```text
Domain
Field
Operator
Transition
Composition
```

A sixth notion may be included explicitly:

```text
Realization relation
```

to connect layers.

These notions answer different questions.

### Domain

```text
Where, over what, or among which configurations are distinctions made?
```

### Field

```text
What typed state, quantity, uncertainty, set, or relation is assigned there?
```

### Operator

```text
Which transformation is admissible, under what conditions, and with what contract?
```

### Transition

```text
What actual change occurred between configurations?
```

### Composition

```text
How are compatible fields and operators connected into a larger organization?
```

### Realization relation

```text
Which lower-level organization carries or implements the higher-level contract?
```

The purpose of reduction is not to deny useful concepts.

It is to distinguish foundational concepts from convenient derived structures.

---

## 8. Configuration Can Be Derived From Fields

A configuration need not be an additional primitive.

For a collection of fields:

\[
\mathcal F=\{F_1,\ldots,F_n\},
\]

a configuration at index or time \(t\) may be represented as a compatible assignment:

\[
c_t=
\left(
F_1|_t,
F_2|_t,
\ldots,
F_n|_t
\right).
\]

The configuration may include:

```text
physical state
represented state
resource state
authority state
active mode
uncertainty
current commitments
```

A transition changes one or more assignments while preserving declared invariants.

Thus:

```text
configuration
=
a jointly interpreted field assignment
```

rather than an unexplained container separate from the field system.

---

## 9. Fields and Relations

Not every useful field returns a scalar.

A field may return:

```text
boolean
number
interval
probability
distribution
vector
tensor
set
state
relation
graph neighborhood
capability manifest
operator family
```

For example:

\[
A:\operatorname{Instruction}\to\mathcal P(\operatorname{MemoryRegion})
\]

may return possible alias regions.

A chemical field may return a local concentration vector.

A capability field may return a set of executable operators:

\[
C:D\to\mathcal P(\mathcal U).
\]

A compatibility field may be relational:

\[
K:D_1\times D_2\to\{\text{compatible},\text{incompatible},\text{unknown}\}.
\]

This avoids forcing heterogeneous organization into one universal number.

---

## 10. Objects May Be Stable Regions in Field Organization

The framework does not require eliminating objects.

An object can be treated as a stable, addressable organization across transitions.

Let:

\[
I(c_t,c_{t+\Delta t})
\]

be an identity or continuity criterion.

An object persists when enough relevant organization satisfies \(I\) despite lower-level change.

Examples include:

```text
one process across context switches
one customer across store visits
one product type across inventory movements
one molecule across thermal motion
one software module across recompilation
```

Objects remain useful because they provide:

```text
addressability
continuity
responsibility
localization
history
interface stability
```

The field view supplements object models by representing distributed properties and relations that cannot be adequately attached to one isolated object.

---

## 11. Operator Is Not Field

A field answers:

```text
what is assigned where?
```

An operator answers:

```text
how may assignments or configurations change?
```

Let:

\[
u:A\rightharpoonup B
\]

be an operator from admissible input organization \(A\) to output organization \(B\).

A richer operator declaration may include:

\[
u=
(A_u,B_u,P_u,Q_u,I_u,C_u,R_u)
\]

where:

```text
Au = input domain and type
Bu = output domain and type
Pu = applicability conditions
Qu = success contract
Iu = preserved invariants
Cu = cost and resource model
Ru = realization relation or implementation
```

Examples include:

```text
type propagation
register allocation
schedule selection
inventory reservation
bond formation
field integration
image blending
route selection
```

An operator may itself consume and produce fields.

---

## 12. Invocation Is Not Operator

The operator:

```text
compile
```

is not the invocation:

```text
compile(project_x, release_mode)
```

The invocation is not the execution trace.

The execution trace is not the realized result.

The distinction is:

```text
operator schema
        ->
invocation
        ->
resolution
        ->
execution
        ->
realized transition
        ->
observed result
```

An invocation supplies:

```text
addressed operator or capability
arguments
target
constraints
authority
horizon
quality requirement
```

Its operational meaning depends on the organization that resolves it.

---

## 13. Transition Is Not Operator

An operator describes a class of admissible transformations.

A transition is one actual occurrence.

Let:

\[
c
\xrightarrow{u(a)}
c'
\]

denote that invocation \(u(a)\) was realized as a transition from \(c\) to \(c'\).

The operator may exist without being invoked.

The invocation may be issued without being executable.

Execution may begin without completing.

A transition may occur through an automatic process without an explicit symbolic invocation.

Therefore:

```text
operator
!=
invocation
!=
execution
!=
transition token
```

---

## 14. Capability Can Be Derived

Capability need not be a separate primitive substance.

Let:

```text
O = organized system
c = current configuration
H = horizon
Theta = constraints and tolerances
```

Define:

\[
\operatorname{Reach}(O,c,H,\Theta)
\]

as the region of configurations reachable through supported transitions.

A capability for target region \(G\) exists when:

\[
\operatorname{Reach}(O,c,H,\Theta)\cap G\neq\varnothing.
\]

A distributed capability field may then report, over domain \(D\):

\[
\operatorname{CapField}_{G}(d)
=
\text{support, confidence, cost, or margin for reaching }G
\text{ from or through }d.
\]

Capability is therefore derived from:

```text
current fields
available operators
applicability
coupling
resources
time
uncertainty
target criteria
```

---

## 15. Capability Fields Do Not Replace All Other Fields

A capability field is a higher-order field.

It may depend on:

```text
resource fields
state fields
geometry fields
authority fields
reliability fields
demand fields
environment fields
provider fields
```

For example:

\[
C_{\text{checkout}}(s,t)
\]

may represent realizable checkout throughput at store \(s\) and time \(t\).

It may be derived from:

\[
\min
(
\text{staff capacity},
\text{terminal capacity},
\text{payment availability},
\text{queue accessibility},
\text{inventory release capacity}
).
\]

The capability field is not the only primitive field.

It is a composed view of whether a transition class can be supported.

---

## 16. The Compiler as a Field System

A compiler provides a useful non-spatial example.

Possible domains include:

```text
source position
syntax node
symbol
basic block
instruction
control-flow edge
memory region
type variable
machine register
```

Possible fields include:

```text
type assignment
scope membership
definition reachability
variable liveness
dominance
alias set
constant value
side-effect class
register pressure
instruction cost
```

Possible operators include:

```text
parse
resolve
infer
propagate
merge
restrict
rewrite
lower
allocate
schedule
emit
```

A compiler pass often computes a fixed point over a graph.

For liveness:

\[
\operatorname{LiveIn}(b)
=
\operatorname{Use}(b)
\cup
(
\operatorname{LiveOut}(b)
-
\operatorname{Def}(b)
)
\]

and:

\[
\operatorname{LiveOut}(b)
=
\bigcup_{s\in\operatorname{Succ}(b)}
\operatorname{LiveIn}(s).
\]

The compiler is therefore not merely an object transformer.

It is already a typed field compositor over program domains.

---

## 17. Memory Indices Are One Realization Coordinate

Compiler data must be stored somewhere.

A syntax node may occupy memory.

A control-flow graph may be encoded through pointers.

A type variable may be indexed in an array.

But memory indices answer:

```text
where is the representation stored?
```

The compiler analysis answers:

```text
what program relation does this representation carry?
```

The two may coincide operationally without being semantically identical.

A debugging tool may expose both:

```text
node id: 487
memory address: 0x7f...
source span: line 28
type: Vec<Float>
liveness: blocks 4-9
```

Each coordinate belongs to a different frame.

---

## 18. The Scheduler as a Field System

A scheduler's addressable domain may include processes, threads, cores, queues, and time.

Fields may include:

\[
R(p,t)
\]

for runnable state,

\[
P(p,t)
\]

for priority,

\[
D(p,t)
\]

for deadline slack,

\[
A(p,c,t)
\]

for affinity between process \(p\) and core \(c\),

and:

\[
L(c,t)
\]

for core load.

The scheduling operator selects assignments:

\[
S:
(\mathcal P,\mathcal C,\mathcal F_t)
\rightharpoonup
\operatorname{Assignment}.
\]

The PID is a handle into the process domain.

The scheduling decision is a composition over several fields and constraints.

---

## 19. A Store as a Coupled Field System

A store is not adequately described as a container of customer and product objects.

Its effective domains include:

```text
customer
product
shelf
warehouse
checkout
staff role
supplier
location
time
authority
payment channel
```

Fields may include:

```text
inventory
price
demand
reservation
shelf accessibility
customer density
staff availability
checkout load
replenishment rate
payment compatibility
loss risk
```

A purchase capability exists only where several fields overlap.

For customer \(c\), product \(p\), location \(x\), and time \(t\):

\[
C_{\text{purchase}}(c,p,x,t)
\]

may require:

```text
product present
customer able to access it
price accepted
payment supported
sale authorized
inventory not reserved elsewhere
checkout or transaction channel available
```

The realized sale also causes product, money, records, people, and responsibilities to transition.

---

## 20. Chemistry as Relational and Configuration Fields

Chemistry is not only a list of atoms.

Relevant domains include:

```text
atoms
atom pairs
molecules
spatial regions
reaction coordinates
electronic states
concentrations
temperature and pressure conditions
```

A bond can be represented as a relational field:

\[
B(a_i,a_j)
\]

over atom pairs.

A concentration field may be:

\[
C_k(x,t)
\]

for species \(k\).

A reaction operator may be applicable only when:

```text
reactants coexist
geometry is compatible
energy barriers can be crossed
catalysts are present
environmental conditions are suitable
conservation constraints are satisfied
```

The reaction schema is not the realized reaction token.

The bond relation is not the atom identifier.

The effective chemical layer is realized by lower physical organization while exposing stable chemical variables.

---

## 21. Physics and Fields

Physics supplies the clearest literal field examples.

A field may assign:

```text
scalar
vector
tensor
operator
probability amplitude
```

over spacetime or configuration space.

But even here, one should distinguish:

```text
field value
operator or law
boundary conditions
state
measurement
realized evolution
```

A differential equation does not itself cause the transition.

It specifies a relation among admissible state evolutions.

A realized physical system follows or instantiates the relevant dynamics under its conditions.

The capability-compositor framework does not claim to replace physical theory.

It uses the field/operator distinction as an architectural pattern that can also organize effective non-physical domains.

---

## 22. Graphics Compositors as a Direct Analogy

A graphics compositor receives:

```text
layers
masks
opacity fields
depth fields
transforms
clipping regions
blend modes
color spaces
timing
```

and produces a composed image or stream.

The final image is not obtained by indiscriminate addition.

Composition may involve:

```text
over
under
multiply
screen
mask
clip
transform
occlude
resample
filter
```

A capability compositor follows a similar architecture.

It receives:

```text
resource fields
provider fields
demand fields
authority fields
environment fields
mode selections
reliability fields
```

and applies explicit operators to produce:

```text
realizability
margin
blocking regions
provider assignments
guidance-relevant capability frontiers
```

The analogy is structural, not merely visual.

---

## 23. Compositor Systems Operate Across Layers

A graphics compositor may combine layers produced by different subsystems.

A window comes from one process.

A cursor comes from another.

A video frame may come from a decoder.

A subtitle layer may come from a timing system.

The compositor does not duplicate every implementation.

It receives stable surfaces and contracts.

Likewise, a capability compositor may combine:

```text
compiler analysis
scheduler state
robot availability
human authority
inventory
weather
power
network health
```

through interfaces.

Each source can remain internally complex while exposing a typed field or capability surface.

Thus:

> Composition across layers requires stable contracts, not one flattened implementation.

---

## 24. Layer Is a Derived Interface Boundary

A layer can be defined as an organizational region whose internal realization is hidden behind a stable interface.

Let:

```text
L = internal organization
Q = exposed contract
```

A layer is valid while:

\[
L\models Q
\]

under declared conditions.

Different internal realizations may satisfy the same contract.

Examples include:

```text
transistor network
        exposes
logic gate
```

```text
kernel structures
        expose
process abstraction
```

```text
compiler passes
        expose
object file
```

```text
warehouse and staff
        expose
available inventory
```

```text
resolver and providers
        expose
realizability report
```

Layering is therefore derived from abstraction, realization, and interface preservation.

---

## 25. Composition Is Typed Coupling

Two operators do not compose merely because they are placed next to each other.

Let:

\[
f:A\to B
\]

and:

\[
g:C\to D.
\]

Direct composition requires a compatible relation:

\[
B\preceq C
\]

or an explicit bridge:

\[
b:B\to C.
\]

Then:

\[
g\circ b\circ f:A\to D.
\]

The bridge may perform:

```text
type conversion
unit conversion
coordinate transformation
resampling
protocol translation
aggregation
projection
authorization
semantic interpretation
```

Many practical failures are missing bridges rather than missing components.

---

## 26. Domain Alignment Is a First-Class Operation

Fields may refer to different domains or resolutions.

Examples include:

```text
hourly staff schedule
minute-level checkout load
daily inventory report
per-event payment status
room-level occupancy
building-level power
customer-level demand
```

Before composition, the system must declare how the domains align.

Possible operators include:

```text
resample
project
interpolate
aggregate
join
transform
restrict
broadcast
```

Implicit alignment is a major source of hidden error.

A field compositor should therefore reject or expose unresolved domain mismatches.

---

## 27. Modes Are Selectors, Not Universal Primitives

A mode describes a qualitative configuration such as:

```text
compiler optimization level
process lifecycle state
store open or closed
machine operational or failed
robot autonomous or teleoperated
chemical phase
circuit power mode
```

A mode can be represented as a state-valued field:

\[
M:D\times T\to\mathcal S.
\]

The mode selects active operators, requirements, and interfaces.

Thus:

```text
mode
=
a selector over a field-operator subgraph
```

rather than a wholly separate ontology.

Statecharts remain useful for declaring legal mode transitions and hierarchy.

The compositor uses their active selections during evaluation.

---

## 28. Provider Is a Satisfied Interface Region

A provider need not be primitive.

Let an interface requirement be \(Q\).

A provider is an organization \(P\) such that:

\[
P\models Q
\]

under declared conditions.

A provider field may report where and when this is true:

\[
\operatorname{Provides}_Q(p,d,t)
\in
\{\text{yes},\text{no},\text{unknown},\text{degraded}\}.
\]

Examples include:

```text
camera stream provided by physical camera
camera stream provided by simulation
checkout provided by staffed terminal
checkout provided by self-service terminal
object pose provided by vision
object pose provided by human operator
```

Provider substitution becomes a typed interface-matching problem.

---

## 29. Dependency Graphs Are Derived Evaluation Structures

A dependency graph records which field outputs are required by which operators and derived fields.

Nodes may include:

```text
source field
derived field
operator
mode selector
closure interface
requirement
```

Edges may include:

```text
depends_on
restricts
provides
transforms
selects
observes
invalidates
```

The graph is not necessarily the fundamental ontology.

It is the runtime's evaluation representation.

It is derived from field declarations, operator contracts, and requested outputs.

---

## 30. Closures Are Composed Fixed Points

Some dependencies are cyclic.

For example:

```text
worker occupancy
        increases
heat generation
        increases
ventilation demand
        increases
electricity demand
        reduces
available cooling
        constrains
permitted worker occupancy
```

The cycle should not be treated as an accidental graph error.

It is a self-closed subsystem.

Let:

\[
x=F(x;\theta)
\]

represent its mutually dependent state.

The runtime must declare a solution method such as:

```text
least fixed point
greatest fixed point
numerical iteration
constraint solve
optimization
conservative bound
simulation
```

The solved subsystem may expose:

```text
SafeWorkspaceCapacity
```

while retaining internal explanation paths.

Thus:

```text
closure
=
a composed operator region with a declared fixed-point contract
```

---

## 31. Margin Is a Derived Field

Binary realizability hides fragility.

Let:

\[
S(d)
\]

be support and:

\[
R(d)
\]

be requirement.

A simple margin is:

\[
M(d)=S(d)-R(d).
\]

Interpretation:

```text
M > 0
=
supported with slack
```

```text
M = 0
=
at boundary
```

```text
M < 0
=
blocked
```

More complex margins may combine:

```text
capacity
time
risk
uncertainty
authority
reliability
recoverability
```

A margin is therefore not a primitive.

It is a derived comparison field relative to a declared requirement and evaluation criterion.

---

## 32. Realizability Is Not One Boolean

A realizability result may need several dimensions:

```text
structurally resolvable
provider available
resource sufficient
authorized
safe
reversible
reliable
within deadline
within cost
known with adequate confidence
```

A result may be:

```text
physical realization: blocked
simulation realization: available
remote-assisted realization: degraded
authority: absent
evidence freshness: low
```

The capability compositor should preserve these distinctions rather than collapse them into one truth value.

---

## 33. The Capability Resolver

The resolver begins from an invocation.

Its tasks include:

```text
resolve the addressed capability
check names and types
expand requirements
identify provider candidates
bind compatible interfaces
detect missing bridges
construct dependency closure
identify irreversible boundaries
produce static blockers
```

Conceptually:

\[
\operatorname{Resolve}(i,M,c)=r
\]

and:

\[
C^*(r)=\operatorname{Closure}(r,M,c).
\]

The resolver is similar to a compiler front end, linker, package manager, and preflight checker.

It does not need to perform the full field computation itself.

---

## 34. The Capability Compositor

The compositor receives the resolved dependency organization.

Its tasks include:

```text
bind fields to domains
align frames and resolutions
select active modes
instantiate operators
build the evaluation graph
identify independent regions
solve strongly connected closures
propagate uncertainty
compute capability fields
compute viability margins
materialize stable composites
produce explanation slices
```

Conceptually:

\[
\mathcal C
=
\operatorname{Compose}
(
\mathcal F,
\mathcal U,
\mathcal M,
\Theta
).
\]

The output is not necessarily one value.

It may be a family of fields, reports, and inspectable interfaces.

---

## 35. The Navigator

The navigator operates downstream of composition.

The compositor answers:

```text
what transitions appear realizable, where, when, and with what margin?
```

The navigator answers:

```text
which transition should be endorsed next?
```

A guidance commitment may contain:

```text
selected operator
arguments
frame
applicability
expected effect
completion condition
validity interval
cancellation rule
replanning condition
```

The navigator repeatedly selects from the current capability frontier as observations change.

---

## 36. Runtime Architecture

The complete architecture may be represented as:

```text
invocation
        ↓
resolver
        ↓
typed requirement and provider closure
        ↓
capability compositor
        ↓
aligned fields and active modes
        ↓
dependency graph and solved closures
        ↓
realizability and viability fields
        ↓
navigator or selector
        ↓
guidance commitment
        ↓
executor
        ↓
realized transition
        ↓
observation and verification
        ↓
incremental model revision
```

This is a runtime because it maintains changing state and recomputes consequences.

It is not only a static ontology.

---

## 37. Reactive Evaluation

Fields may change because:

```text
new observation arrives
mode changes
provider disappears
resource is consumed
time advances
authority changes
failure occurs
new field is installed
```

The runtime tracks dependency edges.

When field \(F\) changes, only its transitive dependents should be invalidated:

\[
\operatorname{Invalidate}(F)
=
\operatorname{Descendants}(F).
\]

Independent subgraphs may remain cached.

This resembles:

```text
reactive spreadsheets
build systems
incremental compilers
dataflow engines
materialized views
```

---

## 38. Parallel Evaluation

Independent field regions can be evaluated concurrently.

For example:

```text
inventory analysis
power analysis
staff analysis
network analysis
authority analysis
```

may proceed in parallel until a shared operator requires their results.

Closures require internal coordination.

Parallelism therefore follows the condensation graph of strongly connected components.

A practical runtime may:

```text
identify SCCs
solve each SCC internally
collapse it to one interface node
schedule the resulting DAG
cache stable outputs
```

---

## 39. Materialized Composite Fields

Repeatedly used composites can be promoted into stable interfaces.

Examples include:

```text
SafeWorkspaceCapacity
DeployableServiceCapacity
PurchasableInventory
SchedulableComputeCapacity
ReachableRobotRegion
ChemicallyAdmissibleReactionRegion
```

Materialization may store:

```text
current value
support region
provenance
dependency version
uncertainty
validity interval
explanation handle
```

The composite remains revisable when dependencies change.

---

## 40. Explanation Is a Dependency Slice

A user asking:

```text
Why is this capability unavailable?
```

does not need the entire global model.

The runtime can return a dependency slice containing:

```text
requested capability
active mode
relevant requirement
selected provider
blocking field
failed operator
uncertain assumption
minimal repair candidates
```

A minimal blocking set identifies the smallest known collection of unsatisfied relations whose repair would reopen a candidate realization.

---

## 41. Fields Over Fields and Operators Over Operators

Higher-order organization is possible.

A field may return operators:

\[
F_{\mathcal U}:D\to\mathcal P(\mathcal U).
\]

An operator may transform an operator library:

```text
optimization pass
training procedure
proof transformation
planner synthesis
interface generation
```

A compositor may also operate on compositor outputs.

For example:

```text
local machine capability fields
        compose into
workcell capability field
        composes into
factory capability field
        composes into
supply-network capability field
```

Each layer need not expose every lower-level detail.

It must expose enough contract, uncertainty, and provenance for valid higher-level composition.

---

## 42. Cross-Layer Composition Requires Restraint

A universal compositor that attempts to combine every physical and organizational variable at once will fail through:

```text
type ambiguity
resolution explosion
hidden frame mismatch
false precision
causal confusion
unmanageable dependency closure
loss of responsibility boundaries
```

The runtime should instead use declared interfaces.

A compiler capability compositor need not continuously simulate semiconductor physics.

A store capability compositor need not model every molecular motion of every customer.

A chemistry model need not infer institutional authority unless the target requires it.

The principle is:

> Evaluate at the highest layer whose contracts remain adequate, and descend only where uncertainty, failure, or the requested question requires additional realization detail.

---

## 43. Multiple Valid Domains May Describe One System

One realized system can support several useful domains.

A process may be indexed by:

```text
PID
thread
address space
container
user
service role
CPU core
time slice
```

A product may be indexed by:

```text
SKU
physical item
batch
shelf position
supplier
customer reservation
```

A molecule may be indexed by:

```text
atom graph
spatial geometry
electronic configuration
reaction coordinate
species count
```

No single domain is universally privileged for every query.

A field declaration must state its domain and available transformations to other domains.

---

## 44. The Danger of Treating Addresses as Explanations

An address can locate a failure without explaining it.

Examples:

```text
process 417 crashed
```

```text
instruction 892 is invalid
```

```text
SKU 103 is unavailable
```

```text
atom 12 changed state
```

These statements identify where a problem appears.

They do not necessarily identify:

```text
which dependency failed
which constraint was violated
which operator was inapplicable
which lower layer broke the contract
which replacement is available
```

The compositor must preserve causal and dependency relations in addition to identifiers.

---

## 45. The Danger of Treating Fields as Substances

The opposite error is to reify every useful field.

A demand field is a model of distributed demand under a chosen representation.

It is not an independent material fluid.

A type field is a compiler relation.

It is not a physical force.

A capability field is an operational estimate.

It is not an omniscient map of all possible futures.

Every field should declare:

```text
domain
value type
support
resolution
provenance
uncertainty
validity conditions
evaluation method
```

---

## 46. A Minimal Data Model

A practical implementation may begin with six primary object classes:

```text
Domain
Field
Operator
Interface
ModeSystem
Closure
```

### Domain

```text
identity
coordinate or addressing scheme
topology or relation structure
resolution
available transforms
```

### Field

```text
domain
value type
support
units or semantic kind
uncertainty
provenance
evaluation
```

### Operator

```text
input contracts
output contract
applicability
invariants
cost
failure modes
implementation
```

### Interface

```text
provided contract
required contract
compatibility relation
observational criterion
version
```

### ModeSystem

```text
states
hierarchy
parallel regions
transition rules
active subgraph selection
```

### Closure

```text
members
boundary inputs
boundary outputs
solution method
convergence or bound contract
explanation mapping
```

Other concepts can be represented as records or derived views.

---

## 47. Compilation Pipeline

A capability-compositor compiler may proceed through:

```text
1. Parse the invocation and target criterion.

2. Resolve names, capability types, and domain references.

3. Expand requirements and candidate provider interfaces.

4. Bind source fields and declared observations.

5. Check semantic types, units, and coordinate frames.

6. Insert explicit bridges for compatible domain transformations.

7. Select active hierarchical modes.

8. Construct the field-operator dependency graph.

9. Partition the graph into strongly connected components.

10. Assign solution methods to closures.

11. Schedule independent components for parallel evaluation.

12. Propagate values, uncertainty, cost, and provenance.

13. Compute capability, realizability, and viability fields.

14. Identify blocking regions and minimal repairs.

15. Materialize stable composite interfaces.

16. Generate guidance candidates only within supported regions.

17. Record outcomes and incrementally revise affected fields.
```

---

## 48. Example: Compiler Deployment

Suppose the invocation is:

```text
build and deploy service S
```

The resolver may identify:

```text
source repository
compiler toolchain
dependency versions
target architecture
credentials
deployment environment
rollback capability
```

The compositor may combine:

```text
source compatibility field
dependency satisfiability field
build-resource field
artifact integrity field
network field
authority field
target-capacity field
service-health field
```

Closures may arise between:

```text
resource selection
build parallelism
memory pressure
compile duration
deadline margin
```

The output may report:

```text
build realizability: available
deployment realizability: blocked
blocker: production credential absent
simulation deployment: available
rollback margin: adequate
```

---

## 49. Example: Process Scheduling

Suppose the target is:

```text
complete workload W before deadline T
```

Fields include:

```text
runnable processes
core availability
priority
deadline slack
affinity
memory bandwidth
thermal headroom
I/O dependency
```

Operators include:

```text
assign
preempt
migrate
throttle
reserve
```

A thermal closure may connect:

```text
core frequency
power
temperature
cooling
available frequency
```

The compositor computes a schedulable capacity field.

The scheduler then selects the next process-core assignment from that field.

---

## 50. Example: Store Purchase

Suppose the invocation is:

```text
buy product P now
```

The resolver identifies candidate stores, channels, and providers.

The compositor combines:

```text
inventory
reservation
store-open mode
customer access
price
payment compatibility
checkout capacity
delivery or transport capability
authority and age restrictions
```

The result may be:

```text
in-store purchase: available with low queue margin
pickup: blocked by reservation cutoff
delivery: available tomorrow
payment method A: unsupported
payment method B: available
```

The purchase token is realized only when the selected transition actually occurs.

---

## 51. Example: NAND Gate

At the Boolean layer:

```text
inputs
        ->
NAND
        ->
output
```

At the timing layer, the capability depends on:

```text
input voltage intervals
setup and hold conditions
propagation delay
fan-out
noise margin
power state
temperature
```

At lower layers, those fields are realized through circuit and material dynamics.

A logic-capability field may report whether the gate can reliably realize the NAND contract over a time interval.

The Boolean operator remains distinct from the physical transition trace.

---

## 52. Example: Chemical Reaction

Suppose the target is:

```text
produce compound Z
```

The resolver identifies candidate reaction schemas and required inputs.

The compositor combines:

```text
reactant availability
concentration
temperature
pressure
catalyst state
mixing
geometry
reaction-rate estimate
safety constraints
waste-handling capacity
```

The reaction network may contain feedback closures.

The output may be a feasible reaction region with yield, time, and safety margins.

The chemical operator does not replace the lower physical realization.

It exposes an effective transition contract.

---

## 53. Example: Layered Organization

Consider:

```text
factory output
```

It may be composed from:

```text
machine capability fields
worker capability fields
material-flow fields
power fields
maintenance fields
quality fields
authority fields
```

A factory field may then become an input to:

```text
warehouse capability
distribution capability
store availability
customer purchase capability
```

The hierarchy is:

```text
component
        ->
machine
        ->
workcell
        ->
factory
        ->
supply network
        ->
store
        ->
customer realization
```

Each level exposes a stable composite interface with declared uncertainty and validity.

---

## 54. Primitive Reduction Does Not Mean Microscopic Reduction

Two different reductions should be distinguished.

### Conceptual reduction

Reduce the number of formal categories by deriving notions such as capability, mode, provider, margin, and closure from a smaller kernel.

### Physical reduction

Explain a higher-level realization through lower-level physical organization.

The first improves the framework's formal economy.

The second concerns implementation and ontology.

One can conceptually reduce `provider` to interface satisfaction without simulating its microscopic realization.

One can treat a compiler type field as an effective field while acknowledging that its execution is physically instantiated.

Thus:

```text
fewer formal primitives
!=
one compulsory explanatory scale
```

---

## 55. Explanatory Pluralism

Different layers answer different questions.

A semiconductor model answers:

```text
Will this transistor network satisfy voltage and timing constraints?
```

A logic model answers:

```text
Which Boolean function is implemented?
```

A compiler model answers:

```text
Which program transformation preserves semantics?
```

A scheduler model answers:

```text
Which workload assignment satisfies policy and resource constraints?
```

A store model answers:

```text
Which purchase transitions are currently supportable?
```

The framework should preserve multiple valid explanatory levels connected by realization contracts.

---

## 56. Central Principles

### Principle 1: Address is not state

An identifier locates a domain element; it does not contain the fields associated with it.

### Principle 2: Domain is declared

Every field and operator must state the domain over which it is meaningful.

### Principle 3: Fields are typed assignments

A field may return quantities, sets, states, distributions, or relations.

### Principle 4: Effective fields need not be fundamental physical fields

They are valid when realized organization preserves their declared operational contract.

### Principle 5: Operator is not invocation

A reusable transformation schema differs from one addressed request.

### Principle 6: Invocation is not execution

A valid request may remain unresolved, blocked, unsafe, or unauthorized.

### Principle 7: Operator is not transition token

A transition is one realized occurrence under a particular configuration.

### Principle 8: Capability is derived from reachable transition support

It depends on fields, operators, coupling, resources, conditions, and targets.

### Principle 9: Modes select active subgraphs

They do not need to be treated as unrelated primitive substances.

### Principle 10: Providers satisfy interfaces

Provider identity is secondary to contract compatibility under declared conditions.

### Principle 11: Closures are solved compositions

Cyclic dependencies require explicit fixed-point or bounding semantics.

### Principle 12: Margins are derived comparison fields

They express slack, fragility, or deficit relative to requirements.

### Principle 13: Layers are interface boundaries

They hide internal realization while preserving inspectable contracts.

### Principle 14: Composition is typed coupling

Outputs and inputs compose only through compatible domains, types, frames, and bridges.

### Principle 15: The resolver, compositor, navigator, and executor have distinct roles

Resolution identifies candidate organization; composition computes the capability frontier; navigation selects a transition; execution changes the world.

### Principle 16: Runtime evidence revises future capability

Observed success, failure, and improvisation should update affected fields and dependencies.

### Principle 17: High-level evaluation should descend only when necessary

Adequate interfaces should prevent universal microscopic simulation.

### Principle 18: Explanatory level is question-relative

No single domain or layer is sufficient for every operational question.

---

## 57. Compact Formal Summary

Let:

```text
D = domain
V = typed value space
F = field
u = operator
i = invocation
c = configuration
eta = execution trace
Q = interface contract
O = organized system
G = target region
H = horizon
Theta = constraints and tolerances
```

### Domain-address relation

\[
\operatorname{Addr}:D\to I.
\]

### Field

\[
F:D\rightharpoonup V.
\]

### Support

\[
\operatorname{supp}(F)\subseteq D.
\]

### Operator

\[
u:A\rightharpoonup B.
\]

### Applicability

\[
\operatorname{Applicable}(u,c,\Theta).
\]

### Invocation resolution

\[
r=
\operatorname{Resolve}(i,M,c).
\]

### Realized transition

\[
c
\xrightarrow{u(a)}
c'.
\]

### Realization trace

\[
\operatorname{Exec}(O,u(a),c)=\eta.
\]

### Interface satisfaction

\[
P\models_{\Theta}Q.
\]

### Direct composition

\[
f:A\to B,
\qquad
g:B\to C
\quad\Rightarrow\quad
g\circ f:A\to C.
\]

### Bridge-mediated composition

\[
f:A\to B,
\qquad
b:B\to C,
\qquad
g:C\to E
\quad\Rightarrow\quad
g\circ b\circ f:A\to E.
\]

### Capability region

\[
\operatorname{Cap}(O,c,H,\Theta;G)
\iff
\operatorname{Reach}(O,c,H,\Theta)\cap G\neq\varnothing.
\]

### Capability field

\[
C_G(d)
=
\operatorname{SupportEstimate}
(
d,
G,
\mathcal F,
\mathcal U,
\Theta
).
\]

### Mode selection

\[
\mathcal G_{\text{active}}
=
\operatorname{Select}
(
\mathcal G,
M(c)
).
\]

### Closure

\[
x^*
=
F(x^*;\theta).
\]

### Margin

\[
M(d)=S(d)-R(d).
\]

### Incremental invalidation

\[
\operatorname{Invalidate}(F)
=
\operatorname{Descendants}(F).
\]

### Model revision

\[
M_{t+1}
=
U(M_t,\hat{\eta}_t,\eta_t,o_t).
\]

---

## 58. Minimal Prototype

A first prototype should remain narrow.

One useful domain is:

```text
ROS workspace
+
one robot or simulator
+
one operator
+
limited capability vocabulary
```

Primary domains:

```text
node
topic
action
device
operator
workspace
location
time
```

Fields:

```text
node health
topic availability
build state
battery
pose confidence
authorization
disk capacity
network state
```

Operators:

```text
build
launch
move
observe
record
stop
dock
```

Modes:

```text
simulation
physical
maintenance
teleoperation
autonomous
```

The prototype should demonstrate:

```text
typed invocation
provider resolution
domain alignment
dependency closure
one cyclic subsystem
margin computation
minimal blocking set
guidance commitment
observed outcome
incremental revision
```

The first goal is not unrestricted autonomy.

It is an inspectable runtime that makes the distinction between address, field, operator, transition, and realization visible.

---

## 59. Open Questions

### Domain identity

When should two domains be treated as the same domain under different addressing schemes?

### Field granularity

How should the runtime choose spatial, temporal, organizational, or graph resolution?

### Cross-layer validity

What evidence is sufficient to trust a higher-level interface without descending into its implementation?

### Operator equivalence

When do different implementations expose the same effective operator?

### Capability stability

How much repeatability is required before one successful transition supports a reusable capability claim?

### Closure semantics

Which fixed-point methods are safe for heterogeneous physical, software, and social dependencies?

### Uncertainty composition

How should correlated, stale, adversarial, or structurally incomplete evidence propagate?

### Responsibility

How should agency, authority, credit, and blame be assigned across composed organizations?

### Runtime scope

Which fields belong in one compositor, and which should remain behind remote interfaces?

### Discovery

How can repeated successful compositions be promoted into new operators or stable composite fields?

---

## 60. Design Target

The intended system should make it possible to declare:

```text
I want to realize target G.
```

and receive:

```text
which domain and frame the target uses
which capability interfaces are required
which providers appear compatible
which fields support or block the target
which modes are active
which closures must be solved
where realizability holds
how much margin remains
which assumptions are uncertain
which transition is locally executable next
which effects cross a commitment boundary
which observations would most improve the model
```

The system should not claim absolute knowledge.

It should expose:

```text
scope
conditions
uncertainty
provenance
resolution
validity interval
unmodeled dependencies
```

---

## 61. Central Claim

> Many systems that appear to manipulate isolated objects are more accurately understood as operating over typed, distributed state on addressable domains, through operators whose applicability and realization depend on layered organization.

A process ID, memory index, SKU, atom label, coordinate, or interface name provides an address.

A field supplies organized state over that addressable domain.

An operator specifies an admissible transformation.

An invocation requests one operator or capability.

A transition is the realized change.

A layer preserves a stable contract over lower-level organization.

A capability compositor aligns and combines these relations into an inspectable field of current realizability.

---

## 62. Conclusion

Capability fields do make strong use of a small primitive kernel, provided that the word `field` is not forced to absorb every other concept.

Fields are especially powerful because they represent distributed state across domains that may be spatial, temporal, relational, graph-structured, organizational, or configurational.

They reveal a common structure across:

```text
compiler analysis
process scheduling
digital logic
commerce
robotics
chemistry
physics
graphics composition
organizational coordination
```

But fields do not replace:

```text
operators
invocations
transitions
realization relations
interfaces
```

The clean architecture is not:

```text
everything is a field
```

It is:

```text
addressable domains
        carry
typed fields
        transformed by
operators
        requested through
invocations
        realized as
transitions
        connected across
interfaces and layers
        composed into
capability and viability fields
```

This reduced kernel permits many higher-level notions to remain available without becoming independent primitives.

Capability becomes a reachable transition region.

Mode becomes a selector.

Provider becomes interface satisfaction.

Closure becomes fixed-point composition.

Margin becomes derived slack.

Layer becomes a stable abstraction boundary.

The resulting capability compositor is not merely a metaphor.

It is a plausible runtime architecture:

```text
resolve
align
select
compose
solve
propagate
explain
guide
observe
revise
```

Its promise is not that every domain becomes identical.

Its promise is that heterogeneous domains can expose enough typed organization to be composed while preserving their distinct realization layers, explanatory roles, and responsibility boundaries.
