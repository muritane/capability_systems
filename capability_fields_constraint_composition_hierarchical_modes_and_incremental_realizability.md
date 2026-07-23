# Capability Fields, Constraint Composition, Hierarchical Modes, and Incremental Realizability

## Abstract

A capability is rarely available everywhere, continuously, independently, and without support.

A worker may be present but unable to work because:

```text
the workspace is full
the air is unsafe
the lighting is insufficient
the required machine is occupied
the material is absent
the task is undefined
the worker is fatigued
the relevant authorization is missing
```

A machine may be installed but unable to operate because:

```text
electricity is unavailable
temperature is outside tolerance
pressure is insufficient
maintenance is overdue
a qualified operator is absent
an upstream material flow has stopped
```

A high-level capability model must therefore represent more than a dependency list.

It must represent where, when, under which mode, at what rate, with what uncertainty, and through which shared interaction region a dependency can be satisfied.

This document proposes a field-oriented extension of capability systems.

The central objects are:

```text
typed fields
field operators
hierarchical modes
occupancy and interaction regions
dependency closures
self-closed feedback subsystems
incremental recomputation
parallel evaluation
```

A field assigns a value, interval, distribution, state, or relation over a declared domain such as:

```text
space
time
population
authority
resource class
organizational role
representation
```

Examples include:

\[
W(x,t)
\]

for worker occupancy,

\[
E(x,t)
\]

for electrical capacity,

\[
L(x,t)
\]

for lighting,

and:

\[
D(x,t)
\]

for task demand.

Operators do not all behave like addition.

They may:

```text
sum
restrict
intersect
mask
reserve
allocate
transport
delay
convolve
saturate
select
project
aggregate
propagate
solve a fixed point
```

Hierarchical statecharts select which fields, constraints, and operators are active in each qualitative mode.

A worker in:

```text
off_shift
```

does not expose the same capabilities or requirements as a worker in:

```text
working
```

A machine in:

```text
failed
```

does not participate in the same dependency closure as one in:

```text
operational
```

Time is not reduced to a uniform sequence of arbitrary slots.

The system may partition a horizon into intervals whose boundaries are introduced only when a relevant field, mode, requirement, or operator changes materially.

Space is not decorative metadata.

Workers, robots, tools, machines, air, light, and tasks occupy or apply to typed spatial regions.

Tutor-student interaction becomes possible only when their interaction fields overlap through a suitable communication medium.

Workspace capacity becomes a spatial occupancy constraint rather than one global integer.

Cyclic dependencies are grouped into self-closed subsystems.

For example:

```text
worker occupancy
->
heat generation
->
ventilation demand
->
electricity demand
->
available cooling
->
permitted worker occupancy
```

cannot be evaluated as a simple acyclic pipeline.

The cycle must be solved as a mutually consistent subsystem and may expose one higher-level result such as:

```text
SafeWorkspaceCapacity
```

while preserving internal explanation paths.

Because fields and operators form an explicit dependency graph, independent regions can be evaluated in parallel.

When a new field is introduced later—such as a holiday calendar, a yearly health distribution, or photovoltaic generation—only its transitive dependents need to be invalidated and recomputed.

The resulting architecture resembles a combination of:

```text
statecharts
geographic information systems
reactive spreadsheets
build systems
multimedia compositors
constraint solvers
dataflow runtimes
reliability models
```

without being reducible to any one of them.

Its design target is:

> A capability compositor that can accept new typed fields, derive local and global realizability margins, hide stable internal closures behind inspectable interfaces, and reject impossible configurations before committing to detailed execution.

---

## 1. Starting Point

Suppose the desired capability is:

```text
paint shirts
```

A flat capability list might contain:

```text
worker
paint
shirt
room
```

This is insufficient.

The actual capability depends on relations such as:

```text
the worker is present
the worker is allowed to perform the task
the worker can reach the shirt
the worker and shirt occupy a compatible workspace
the paint is compatible with the shirt material
the room is sufficiently ventilated
the lighting supports visual inspection
the required throughput is achievable
the worker can recover, leave, or remain safely
the organization can replace depleted materials
```

The question is not merely:

```text
Does each required object exist?
```

It is:

```text
Do the required capability fields overlap
with sufficient margin
over the relevant space,
time,
population,
resource,
and authority domains?
```

This changes the representation.

A dependency graph remains necessary.

But each node and edge must become conditional on where and when its relation is realizable.

---

## 2. From Tracks to Fields

A timeline editor contains tracks.

An audio track may contain amplitude over time.

A subtitle track contains text cues over time.

A video track contains spatial images over time.

The track metaphor is useful because it suggests:

```text
layering
alignment
visibility
coverage
synchronization
overlap
masking
```

But a capability model usually requires more than one-dimensional tracks.

A worker may move through rooms.

A machine occupies a footprint.

Lighting varies across the floor.

Noise varies by location.

A holiday applies to a jurisdiction.

An authorization applies to a role and scope.

A health distribution applies to a population and time range.

The more general object is therefore a field:

\[
F:D\to V
\]

where:

```text
D = declared domain
V = declared value type
```

The domain may include several coordinates:

\[
D
=
X
\times
T
\times
P
\times
R
\times
A
\]

where:

```text
X = spatial domain
T = temporal domain
P = population or provider domain
R = resource or role domain
A = authority or applicability domain
```

A timeline track is then a field whose domain happens to be primarily temporal.

---

## 3. A Minimal Field Schema

A field may be represented as:

\[
F=
(D_F,V_F,U_F,S_F,Q_F,P_F,C_F,E_F)
\]

where:

```text
DF = domain
VF = value type
UF = units or semantic quantity
SF = support region where the field is defined
QF = uncertainty or confidence representation
PF = provenance and observation history
CF = declared composition contracts
EF = evaluation realization
```

For example:

```yaml
field:
  id: room_3_worker_capacity

domain:
  space: building.room_3
  time: 2026-01-01/2026-12-31
  role: production_worker

value:
  type: nonnegative_capacity
  unit: workers

resolution:
  space: room
  time: 15m

uncertainty:
  representation: interval

provides:
  - maximum_compatible_occupancy

depends_on:
  - usable_floor_area
  - evacuation_capacity
  - ventilation_capacity
  - task_layout
```

A field is not only stored data.

It may be:

```text
observed
declared
derived
estimated
predicted
simulated
bounded
unknown
```

The model should preserve this distinction.

---

## 4. Field Values Need Not Be Scalars

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
capability manifest
```

Examples include:

\[
A_i(t)\in[0,1]
\]

for the probability that worker \(i\) is present,

\[
C(x,t)\in[0,\infty)
\]

for workspace capacity,

\[
T(x,t)\in\mathbb R
\]

for temperature,

and:

\[
M(x,t)\subseteq\mathcal U
\]

for the set of currently executable operators.

A health field might return a distribution over possible functional states rather than one score.

A permission field might return a set of authorized operations.

A task field might return a structured specification.

The field system must therefore be typed.

---

## 5. Field Identity Is Not Display Name

Two fields may share a label while referring to different objects.

For example:

```text
availability
```

may mean:

```text
physical presence
contractual availability
attention availability
machine uptime
inventory availability
network reachability
```

A field identity should preserve:

```text
semantic quantity
domain
unit
scope
provider population
version
provenance
```

The expression:

```text
worker availability
```

is not enough to determine whether the field refers to:

```text
probability of arriving
probability of remaining
expected productive capacity
legal schedulability
current observed presence
```

Composition requires the intended relation to be explicit.

---

## 6. Operators Over Fields

Let:

\[
\Phi:
(F_1,\ldots,F_n)
\rightharpoonup
G
\]

be a field operator.

The operator declares:

```text
accepted field types
domain alignment rules
unit requirements
composition semantics
uncertainty propagation
failure conditions
output field type
```

For example:

\[
\operatorname{CapacityMargin}(C,R)
=
C-R
\]

may compare supply capacity \(C\) with required capacity \(R\).

But subtraction is only valid when:

```text
the quantities are commensurable
the domains have been aligned
the units match
the interpretations of capacity agree
```

A field operator is therefore not just a numerical function.

It is a typed relation between structured fields.

---

## 7. Restriction Is a First-Class Operator

Many important fields do not produce more capability.

They restrict the region in which another capability is admissible.

Let:

\[
\operatorname{Restrict}(F,R)
\]

return the part of field \(F\) supported inside admissible region \(R\).

Examples include:

```text
worker presence
restricted by
legal working hours
```

```text
machine throughput
restricted by
electricity availability
```

```text
room occupancy
restricted by
safe ventilation capacity
```

```text
task execution
restricted by
authority
```

The restriction operator is central because constraints usually shrink feasible regions.

A capability system that includes only productive transformations will systematically underrepresent:

```text
safety
space
authorization
compatibility
maintenance
environmental tolerance
```

---

## 8. Major Field Composition Operators

Different relations require different operators.

### Additive aggregation

For divisible independent capacities:

\[
C(t)=\sum_i C_i(t)
\]

### Bottleneck composition

For serial requirements:

\[
C(t)=\min_i C_i(t)
\]

### Conjunctive support

For boolean admissibility:

\[
A(t)=\bigwedge_i A_i(t)
\]

### Probabilistic conjunction

Under justified independence:

\[
P(A\cap B)=P(A)P(B)
\]

### Redundant support

When any provider is sufficient:

\[
P(A\cup B)
=
1-(1-P(A))(1-P(B))
\]

under justified independence.

### Spatial intersection

\[
S_{\text{joint}}(t)
=
S_1(t)\cap S_2(t)
\]

### Masking

\[
F_{\text{visible}}
=
\operatorname{Mask}(F,M)
\]

### Saturation

\[
C_{\text{usable}}
=
\min(C,C_{\max})
\]

### Convolution

\[
y(t)
=
\int k(t-\tau)x(\tau)d\tau
\]

for history-dependent response.

### Reservation

\[
C_{\text{remaining}}
=
C_{\text{available}}
-
C_{\text{reserved}}
\]

### Allocation

\[
\operatorname{Allocate}(C,D,\pi)
\]

distributes capacity \(C\) across demands \(D\) according to policy \(\pi\).

### Transport

\[
F_{t+\Delta}
=
\operatorname{Transport}(F_t,v,\Delta)
\]

moves matter, energy, people, or information through a domain.

### Projection

\[
G
=
\operatorname{Project}_{D'}(F)
\]

forgets selected dimensions in a controlled way.

No single superposition rule can replace this algebra.

---

## 9. Linear Superposition Is One Special Case

Ordinary superposition assumes that:

\[
\Phi(F_1+F_2)
=
\Phi(F_1)+\Phi(F_2)
\]

for the relevant operator \(\Phi\).

This is powerful for linear systems.

But many capability relations are nonlinear.

Examples include:

```text
a room becomes unsafe after an occupancy threshold
a worker cannot perform two exclusive tasks simultaneously
a machine saturates at its maximum rate
a shared supervisor becomes a bottleneck
a battery cannot provide negative stored energy
a permission is either sufficient or not
```

The field system should therefore treat linearity as a declared property rather than a default assumption.

---

## 10. Space Is a Literal Domain of Capability

A workspace should not be represented only as:

```text
room available = true
```

It may be represented as a spatial field:

\[
S_{\text{worker}}(x,t)
\]

that declares where workers may occupy space.

A worker occupancy field may be:

\[
W_i(x,t)
\]

and total occupancy:

\[
W(x,t)
=
\sum_i W_i(x,t)
\]

A spatial capacity constraint becomes:

\[
W(x,t)
\le
S_{\text{worker}}(x,t)
\]

for every relevant \(x\) and \(t\).

This is stronger than checking:

```text
number of workers <= room capacity
```

because it can represent:

```text
narrow passages
blocked exits
localized hazards
machine footprints
required clearance
crowding near one station
```

Space is not merely one number attached to a track.

It is part of the track's domain.

---

## 11. Typed Space

Not every physical region is suitable for every occupant.

Examples include:

```text
human standing space
forklift operating space
robot arm sweep volume
clean-room space
storage space
evacuation path
acoustic communication region
wireless coverage region
```

A field should therefore declare its spatial type.

For example:

```yaml
occupies:
  - human_workspace

requires_clearance:
  - emergency_egress
  - machine_safety_envelope

may_overlap:
  - illumination_field
  - breathable_air_field

may_not_overlap:
  - robot_high_speed_zone
```

Typed spatial composition prevents a system from satisfying a worker-space requirement with arbitrary geometric volume.

---

## 12. Shared Space Creates Interaction Possibility

Two providers may both exist without being able to interact.

Let:

\[
S_A(t)
\]

and:

\[
S_B(t)
\]

be their spatial support regions.

Direct interaction requires at least:

\[
S_A(t)\cap S_B(t)\neq\varnothing
\]

or the existence of a mediator connecting them.

For a tutor and student:

```text
same physical room
```

may support direct speech.

But remote teaching may instead require:

```text
tutor microphone
network connection
student speakers
shared language
shared temporal interval
```

Thus interaction capability is:

\[
\operatorname{Interact}(A,B)
\]

only when a suitable interaction channel creates an admissible overlap in a declared interaction frame.

---

## 13. Shared Time Creates a Common Temporal Frame

Shared spatial support is not enough.

The tutor and student must also overlap in time:

\[
T_A\cap T_B\neq\varnothing
\]

The effective interaction region becomes:

\[
I_{A,B}
=
(S_A\cap S_B)
\times
(T_A\cap T_B)
\]

possibly extended by:

```text
language compatibility
attention
communication bandwidth
authority
task context
```

A common timeline therefore supplies a global temporal analysis frame.

But each field may still use different temporal resolution.

---

## 14. Different Fields Have Different Time Resolutions

Examples include:

```text
public holiday:
one value per jurisdiction per day

worker attendance:
minutes or hours

worker fatigue:
minutes to hours

photovoltaic production:
seconds to minutes

building temperature:
seconds to minutes

robot control:
milliseconds

component aging:
days to years
```

The system must not silently assume that a coarse field proves a fine-grained requirement.

For example:

```text
daily average electricity supply
```

cannot establish:

```text
uninterrupted millisecond-level voltage stability
```

The result should be:

```text
unknown at required resolution
```

rather than:

```text
satisfied
```

---

## 15. Resampling Is an Explicit Operator

Temporal and spatial alignment require operators such as:

```text
interpolate
aggregate
integrate
sample
hold-last-value
project-to-region
convert-time-zone
convert-coordinate-frame
```

Let:

\[
R_{\Delta t}(F)
\]

resample field \(F\) at temporal resolution \(\Delta t\).

The resampling contract should state:

```text
whether values are averages or point samples
whether interpolation is valid
whether peaks may be hidden
whether uncertainty increases
whether conservation is preserved
```

Without this metadata, aligned curves may appear compatible while concealing important violations.

---

## 16. Events Are Boundaries, Not Necessarily Primitive Semantics

An event may be represented as:

```text
worker arrives
machine fails
holiday begins
battery reaches threshold
```

But each can also appear as a change in a field.

A worker arrival time \(\tau\) induces:

\[
A(t)
=
\begin{cases}
0,&t<\tau\\
1,&t\ge\tau
\end{cases}
\]

If arrival time is uncertain, the field may instead be a cumulative distribution.

Events remain computationally useful because they identify boundaries at which evaluation must change.

Thus:

```text
field semantics
+
event-indexed execution
```

is often preferable to choosing one representation exclusively.

---

## 17. Adaptive Temporal Partitioning

A horizon need not be divided into uniform slots.

Let:

\[
T
=
[t_0,t_1)\cup[t_1,t_2)\cup\cdots\cup[t_{n-1},t_n)
\]

where boundaries are introduced when:

```text
a mode changes
a field definition changes
a threshold is crossed
a reservation begins or ends
a provider appears or disappears
a requirement changes
uncertainty requires refinement
```

Within an interval, selected field relations may remain stable enough for direct evaluation.

This resembles a statechart evaluated over piecewise-stable temporal regions.

But the regions are derived from relevant changes rather than imposed uniformly.

---

## 18. Hierarchical Modes

Fields describe quantities.

Modes describe qualitative organizations.

A worker may occupy one of the modes:

```text
unavailable
available
working
on_break
sick
commuting
```

A machine may occupy:

```text
off
starting
operational
degraded
failed
under_repair
```

A hierarchical mode system avoids one enormous flat state space.

For example:

```text
Worker
├── unavailable
│   ├── off_shift
│   ├── holiday
│   ├── sick
│   └── inaccessible
└── available
    ├── idle
    ├── working
    │   ├── nominal
    │   ├── fatigued
    │   └── assisted
    └── on_break
```

Each state may declare:

```text
active requirements
provided capabilities
resource consumption
field bindings
allowed transitions
entry conditions
exit conditions
```

---

## 19. Parallel State Regions

One object may have several partially independent state dimensions.

For a worker:

```text
schedule state
health state
location state
attention state
authorization state
task state
```

Representing every combination as one flat state creates combinatorial explosion.

Parallel state regions allow:

```text
schedule = working_hours
health = mildly_fatigued
location = room_3
authorization = paint_line
task = shirt_batch_12
```

The effective capability is derived by composing the active regions.

This preserves structure while avoiding a distinct named state for every possible combination.

---

## 20. Modes Select Active Field Relations

A mode does not merely label the object.

It selects which operators and dependencies are active.

For example:

```text
worker.state = working
```

may activate:

```text
requires workspace
requires safe environment
requires task input
requires tools
consumes attention
consumes supervision
produces task throughput
```

Whereas:

```text
worker.state = on_break
```

may activate:

```text
requires break region
requires safe environment
consumes occupancy
produces recovery
does not produce task throughput
```

A machine in:

```text
failed
```

may cease to consume production material while beginning to require:

```text
diagnosis
repair space
technician time
spare parts
```

Modes therefore switch dependency subgraphs.

---

## 21. Statecharts and Fields Should Remain Distinct

Statecharts answer:

```text
Which qualitative mode is active?
Which transitions are allowed?
```

Fields answer:

```text
How much?
Where?
When?
With what uncertainty?
```

Operators answer:

```text
How do these states and quantities constrain or derive one another?
```

The separation can be summarized as:

```text
statecharts
=
mode selection
```

```text
fields
=
distributed values and relations
```

```text
operators
=
composition semantics
```

Collapsing all three into one representation makes the model harder to type, evaluate, and explain.

---

## 22. Availability Curves

Human availability should not usually be one deterministic interval.

Let:

\[
A_i(t)
=
P(\text{worker }i\text{ is present at }t)
\]

A scheduled start time may produce a rising availability curve because arrivals vary.

A scheduled end may produce a falling curve.

But productive capacity also depends on other fields:

\[
C_i(t)
=
\Phi(
A_i(t),
H_i(t),
F_i(t),
D_i(t),
S_i(t),
E_i(t)
)
\]

where:

```text
Hi = health state
Fi = fatigue
Di = distraction or attention availability
Si = skill-adjusted capacity
Ei = environmental compatibility
```

The operator \(\Phi\) must be declared.

Simple multiplication may be a rough approximation, not a universal law.

---

## 23. Fatigue Is History-Dependent

Fatigue is not generally a function of the current workload alone.

A simple model may use:

\[
F(t)
=
F_0
-
\int_0^t
k(t-\tau)W(\tau)d\tau
+
\int_0^t
r(t-\tau)B(\tau)d\tau
\]

where:

```text
W = workload history
B = break or recovery history
k = fatigue response kernel
r = recovery kernel
```

This is one example of convolution-like composition.

Other models may use:

```text
differential equations
state transitions
empirical lookup tables
learned response models
```

The field architecture does not require one fatigue theory.

It requires the selected theory to expose its domain, assumptions, and output contract.

---

## 24. Population Fields and Individual Fields

A yearly health distribution may apply to a population:

\[
P(H\mid
\text{age},
\text{region},
\text{season},
\text{occupation})
\]

An individual worker field may combine:

```text
population prior
individual history
current observation
workload
known conditions
```

The system should distinguish:

```text
population expectation
individual prediction
current observation
organizational planning reserve
```

A population tendency must not be treated as a known fact about a particular person.

At the same time, population distributions are useful for estimating:

```text
expected absence
required reserve staffing
correlated seasonal illness
replacement demand
uncertainty bands
```

---

## 25. Correlation Prevents Naive Multiplication

Suppose ten workers each have an independent probability \(p\) of absence.

A binomial model may be appropriate.

But seasonal infection, transport disruption, or a building hazard can create correlated absence.

Then:

\[
P(A_1,\ldots,A_n)
\neq
\prod_i P(A_i)
\]

The field model should support:

```text
shared latent causes
joint distributions
scenario fields
correlation groups
common-mode failure
```

Otherwise aggregation will overestimate redundancy.

---

## 26. Holiday Fields

A holiday field might be:

\[
H(r,t)
\]

where \(r\) is a jurisdiction or employment domain.

But the holiday field should not directly set every worker's availability to zero.

It should feed an interpretation operator:

```text
HolidayField
        ↓
EmploymentCalendarOperator
        ↓
WorkerSchedulability
```

The operator may depend on:

```text
contract
role
jurisdiction
emergency exemption
collective agreement
personal leave
```

This keeps public-calendar facts separate from employment semantics.

---

## 27. Photovoltaic Fields

Let:

\[
G(x,t)
\]

represent incident solar irradiance over a roof.

A photovoltaic conversion operator may derive:

\[
P_{\mathrm{PV}}(t)
=
\int_{\text{roof}}
G(x,t)
\eta(x,t)
dA
\]

subject to:

```text
panel orientation
shading
temperature
inverter limit
dirt
snow
degradation
maintenance state
```

The derived electricity field may then participate in:

\[
M_{\mathrm{electric}}(t)
=
P_{\mathrm{grid}}(t)
+
P_{\mathrm{PV}}(t)
+
P_{\mathrm{battery}}(t)
-
D_{\mathrm{building}}(t)
\]

Downstream capabilities consume the electricity margin through a stable interface.

They do not need to know how the electricity was produced.

---

## 28. Stable Interfaces Permit Late Extension

Suppose the initial electricity model contains only:

```text
grid supply
```

Later, photovoltaic generation is added.

If consumers depend on:

```text
AvailableElectricalPower
```

rather than directly on:

```text
GridSupply
```

the new provider can be integrated without rewriting every consumer.

Likewise:

```text
WorkerSchedulability
```

may later incorporate holidays without changing every production capability.

The architectural principle is:

> New fields should usually enter through stable typed interfaces rather than creating direct dependencies on every downstream capability.

---

## 29. Dependency Graphs Over Fields and Operators

Let:

\[
G=(V,E)
\]

where vertices include:

```text
source fields
derived fields
mode selectors
operators
composite capability fields
```

An edge:

\[
u\to v
\]

means that evaluating \(v\) may depend on \(u\).

This graph supports:

```text
dependency closure
topological evaluation
parallel scheduling
incremental invalidation
explanation
cycle detection
```

The graph is not only a visualization.

It is an execution and maintenance structure.

---

## 30. Parallel Evaluation

Independent source and derived fields may be evaluated concurrently.

For example:

```text
holiday field       ┐
health field        │
weather field       │
solar field         ├── parallel
machine health      │
inventory field     │
workspace geometry  ┘
```

Synchronization occurs only when an operator requires several results:

```text
WorkerCapability =
Compose(
    worker schedule,
    health,
    workspace,
    environment,
    tools,
    task demand
)
```

A scheduler may evaluate dependency layers in parallel:

```text
source fields
      ↓
local derived fields
      ↓
composite subsystem fields
      ↓
mission capability fields
```

This resembles a reactive dataflow runtime.

---

## 31. Incremental Recalculation

When a field changes, the whole world should not be recomputed.

For a changed node \(v\), define:

\[
\operatorname{Affected}(v)
=
\{u\mid v\leadsto u\}
\]

Only transitive dependents need invalidation.

Adding a holiday field may affect:

```text
worker schedulability
team capacity
production capability
delivery forecast
```

It should not invalidate:

```text
building geometry
paint chemistry
robot arm dimensions
```

unless an explicit dependency exists.

Incremental recomputation turns late model extension into a manageable operation.

---

## 32. Provenance and Dependency Versioning

A derived field should record:

```text
which source field versions were used
which operator version was used
which assumptions were active
which resolution was used
when the result was computed
```

This permits:

```text
cache reuse
reproducibility
targeted invalidation
comparison across model revisions
explanation of changed outcomes
```

Without provenance, an incremental system may reuse stale results while appearing consistent.

---

## 33. Hidden Composite Fields

A global model can become unusable if every low-level field is displayed continuously.

Related fields should be encapsulated.

For example:

```text
oxygen
carbon dioxide
temperature
humidity
air velocity
particulate matter
chemical exposure
```

may derive:

```text
HumanHabitableEnvironment
```

or:

```text
WorkerEnvironmentMargin
```

Downstream consumers use the composite interface.

The internal fields remain available for diagnosis.

Thus:

```text
hidden by default
!=
discarded
```

A composite field is a maintained abstraction over a lower-level dependency organization.

---

## 34. Abstraction as Controlled Hiding

A composite field should declare what it preserves and what it forgets.

For example:

```text
WorkerEnvironmentMargin
```

may preserve:

```text
minimum safety margin
violated requirements
confidence
spatial support
temporal support
```

while hiding:

```text
raw sensor channels
intermediate calibration values
low-level atmospheric equations
```

The abstraction is safe only when downstream questions do not require the forgotten distinctions.

A request for:

```text
general worker occupancy
```

may accept the composite.

A request for:

```text
chemical exposure diagnosis
```

may require expansion into lower-level fields.

---

## 35. Self-Closed Dependency Subsystems

Some dependency regions contain cycles.

For example:

```text
worker occupancy
    ↓
heat generation
    ↓
room temperature
    ↓
ventilation demand
    ↓
electricity demand
    ↓
available cooling
    ↓
permitted worker occupancy
```

This subgraph cannot be evaluated through simple topological order.

It forms a strongly connected component.

Let the internal field vector be:

\[
x=
(
O,T,V,E,C
)
\]

and the subsystem relation:

\[
x=F(x,u)
\]

where \(u\) contains external inputs.

The subsystem must find a consistent solution:

\[
x^\ast=F(x^\ast,u)
\]

or report why no acceptable solution exists.

---

## 36. Fixed-Point Outcomes

A self-closed subsystem may produce:

```text
one stable fixed point
multiple fixed points
an unstable fixed point
a periodic orbit
unbounded growth
no feasible solution
insufficient information
```

The external interface should not pretend these cases are equivalent.

For example:

```text
SafeWorkspaceCapacity = 18 workers
```

may be valid only for one stable operating region.

If 19 workers cause ventilation overload and temperature escalation, the boundary should be represented as a margin rather than a decorative limit.

---

## 37. Composite Closure Interfaces

A self-closed subsystem may expose:

```text
SafeWorkspaceCapacity(x,t)
EnvironmentMargin(x,t)
ExpectedElectricalReserve(t)
StableProductionRate(t)
```

These outputs summarize the internally solved organization.

But they should include explanation handles:

```text
active limiting constraint
sensitivity
stability class
internal assumptions
unresolved uncertainty
```

A resolver may then report:

```text
Painting capability unavailable.

Immediate cause:
safe workspace capacity = 12

Requested occupancy:
15

Limiting internal relation:
ventilation electricity demand exceeds available power
```

The higher-level model remains compact without becoming opaque.

---

## 38. Algebraic Loops Need Declared Solution Methods

Not every cyclic relation should be solved in the same way.

Possible methods include:

```text
direct algebraic solution
monotone fixed-point iteration
constraint propagation
linear programming
nonlinear optimization
differential equation integration
probabilistic inference
discrete search
simulation
```

The closure manifest should declare:

```text
solution method
convergence assumptions
tolerance
maximum iterations
stability test
failure result
```

A cycle is not automatically an error.

An undeclared cycle is.

---

## 39. Monotone Closures and Conservative Bounds

Some closures can be evaluated through monotone bounds.

Suppose increasing occupancy can only increase heat and ventilation demand.

Then an upper-bound iteration may repeatedly tighten the admissible occupancy.

A conservative solver may return:

```text
definitely feasible up to 14 workers
possibly feasible from 15 to 17
definitely infeasible above 17
```

This is often more useful than one falsely precise number.

The capability system should preserve:

```text
definite feasibility
conditional feasibility
definite infeasibility
unknown
```

---

## 40. Viability Margins as Derived Fields

Let:

\[
C(x,t)
\]

be available capability and:

\[
R(x,t)
\]

be required capability.

Define:

\[
M(x,t)=C(x,t)-R(x,t)
\]

The margin field identifies:

```text
surplus regions
fragile regions
violated regions
unknown regions
```

A global mission should not be summarized only by average margin.

A short local violation may determine failure.

Useful summaries include:

```text
minimum margin
duration below zero
spatial extent of violation
probability of violation
distance to limiting threshold
```

---

## 41. Capability Regions

A capability exists over the region:

\[
\mathcal V
=
\{
(x,t,c)
\mid
M(x,t,c)\ge0
\}
\]

where \(c\) may contain additional configuration dimensions.

Planning then becomes:

```text
find a path through viable regions
```

rather than:

```text
select a capability name
```

For a robot:

> Move into a region where grasping becomes executable.

For a worker:

> Enter a workspace and time interval where tools, safety, materials, and authority overlap.

For a production plan:

> Allocate tasks so that all required capability regions overlap with sufficient margin.

---

## 42. Guidance Through Capability Fields

A navigator need not guide only physical position.

It may guide a configured agent through capability space.

A guidance commitment may say:

```text
move worker to station 4
```

because station 4 lies inside the intersection of:

```text
available workspace
required lighting
tool access
material access
supervision coverage
```

The next commitment is selected relative to the current field configuration.

Thus:

```text
global target
        ↓
capability field analysis
        ↓
local viable region
        ↓
bounded guidance commitment
        ↓
observation
        ↓
field update
```

---

## 43. Multimedia Composition as an Analogy

A video compositor places several layers on a shared timeline and spatial canvas.

It checks:

```text
which layer is visible
which layer masks another
whether a subtitle cue overlaps speech
whether audio and video timestamps align
whether an overlay falls outside the frame
```

A capability compositor can use similar concepts:

```text
coverage
alignment
masking
priority
safe region
synchronization
missing interval
```

But capability layers additionally require:

```text
resource conservation
causal dependencies
typed occupancy
authority
maintenance
uncertainty
feedback
```

The analogy is useful for interface design, not a complete formal model.

---

## 44. Subtitle Coverage as a General Pattern

Let:

\[
S(t)
\]

represent speech activity and:

\[
C(t)
\]

represent caption coverage.

The uncovered region is:

\[
U(t)=S(t)\land\neg C(t)
\]

The same pattern applies to capabilities:

```text
task demand
and not
provider coverage
```

or:

```text
worker presence
and not
safe workspace
```

Automatic subtitle systems may use speech recognition, text alignment, and cue timing rather than checking every word manually.

Likewise, a capability system can automate coverage checks once fields share typed domains and alignment operators.

---

## 45. Occlusion and Interference

A capability may exist nominally but be blocked.

Examples include:

```text
a machine blocks an evacuation route
noise masks spoken instruction
one task reserves the only tool
one visual layer obscures safety information
electromagnetic interference degrades communication
```

The system should distinguish:

```text
resource interference
spatial occlusion
signal interference
semantic interference
authority conflict
schedule collision
```

Each requires a different operator.

The general pattern is:

\[
F_{\text{effective}}
=
\operatorname{ResolveInterference}
(
F_{\text{candidate}},
I_1,\ldots,I_n
)
\]

The interference operator must be typed to the relation.

---

## 46. Amplification and Annihilation

Some field interactions amplify capability.

Examples include:

```text
tutor and student co-presence
worker and tool co-location
battery and photovoltaic generation
parallel independent providers
```

Others annihilate it.

Examples include:

```text
missing shared language
incompatible connector
safety exclusion zone
single required dependency at zero
destructive signal interference
```

The field algebra should express whether an interaction is:

```text
additive
multiplicative
thresholded
synergistic
antagonistic
exclusive
cancelling
```

Names such as:

```text
amplification
annihilation
```

are useful at a high level, but the exact operator must preserve the domain semantics.

---

## 47. Rate Compatibility

A provider with maximum rate \(1\text{ Hz}\) cannot directly satisfy a non-bufferable \(20\text{ Hz}\) requirement.

Let:

\[
C_{\max}(t)=1
\]

and:

\[
R_{\min}(t)=20
\]

Then:

\[
M(t)=C_{\max}(t)-R_{\min}(t)<0
\]

Parallel replication helps only when:

```text
the work is partitionable
results may be aggregated
coordination cost is acceptable
shared resources do not bottleneck
latency requirements remain satisfied
```

Rate fields therefore need:

```text
throughput
latency
burst capacity
buffer semantics
partitionability
synchronization requirements
```

A single scalar frequency is not always sufficient.

---

## 48. Reliability and Lifecycle Fields

A component may provide capability now but not throughout the mission horizon.

A reliability field may be:

\[
R_i(t)
=
P(\text{component }i\text{ remains functional through }t)
\]

A maintenance field may represent:

```text
inspection availability
repair capacity
spare-part inventory
replacement lead time
retirement condition
```

The capability field should account for:

```text
failure
degradation
repair
replacement
common-mode risk
maintenance contention
```

A specification that omits maintenance may appear viable over one interval while failing over the intended horizon.

---

## 49. Replacement Is a Capability Dependency

Suppose a filter must be replaced every month.

The continuing ventilation capability depends on:

```text
replacement filter availability
technician availability
access to the unit
safe shutdown
waste disposal
restart verification
```

These are not external annotations.

They are part of the long-horizon capability closure.

The system may derive:

```text
expected replacement demand
reserve stock requirement
repair-team utilization
probability of capability interruption
```

---

## 50. Static Evaluation Before Simulation

A field-oriented resolver can reject many configurations without dynamic simulation.

Examples include:

```text
no spatial overlap
no temporal overlap
unit mismatch
rate lower than requirement
empty authority intersection
environmental tolerance intersection is empty
workspace capacity below occupancy
required field has no provider
maintenance closure is absent
```

Simulation should not be used to rediscover a contradiction that static field composition can prove.

The pipeline may be:

```text
type checking
        ↓
domain alignment
        ↓
dependency closure
        ↓
static bound propagation
        ↓
fixed-point subsystem solving
        ↓
temporal logic checking
        ↓
dynamic simulation where unresolved
```

---

## 51. Dynamic Evaluation Remains Necessary

Static fields do not eliminate all dynamic reasoning.

Dynamic evaluation may still be needed for:

```text
queue formation
path-dependent fatigue
repair contention
inventory depletion
feedback instability
correlated random failures
adaptive behavior
traffic
learning
strategic interaction
```

But many dynamic models can still expose their results as fields.

For example:

```text
queue simulation
        ↓
expected waiting-time field
```

or:

```text
Monte Carlo reliability model
        ↓
mission-availability distribution
```

Thus dynamic execution can be encapsulated behind field interfaces.

---

## 52. Temporal Logic Over Fields

A requirement may refer to entire intervals rather than one sample.

Examples include:

```text
oxygen remains above threshold throughout the shift
```

```text
every machine failure receives repair support within 30 minutes
```

```text
subtitle coverage exists throughout every speech interval
```

A temporal requirement can be evaluated over field traces.

The result should preferably include a robustness margin:

```text
satisfied by large margin
satisfied narrowly
violated briefly
violated persistently
unknown because resolution is insufficient
```

This connects logical checking with viability fields.

---

## 53. Adding a New Field

A newly introduced field should declare:

```text
identity
domain
value type
units
support region
resolution
uncertainty
providers
consumers or semantic interface
composition contracts
provenance
```

The system then asks:

```text
Which existing operators accept this field type?
Which stable interfaces may it provide?
Which downstream nodes depend on those interfaces?
Which cached results are invalid?
Which requirements remain unresolved?
```

Adding a field is structurally easy only when these contracts are explicit.

---

## 54. New Fields Should Not Affect Everything

A holiday field should affect:

```text
employment schedulability
building access schedules
service availability
```

It should not directly affect:

```text
paint viscosity
robot geometry
battery chemistry
```

A photovoltaic field should affect:

```text
electrical supply
battery charging
grid import
```

It should not directly modify worker skill.

Explicit typing and dependency edges prevent accidental global coupling.

---

## 55. Extension Report

After adding a field, the resolver should produce a report such as:

```text
Field added:
HolidayCalendar_DE

Matched interfaces:
- jurisdictional_nonworking_day
- building_access_calendar

Affected derived fields:
- worker_schedulability
- team_capacity
- production_forecast

Unresolved mappings:
- contractor holiday policy
- emergency staffing exemption

Unaffected subsystems:
- machine geometry
- material compatibility
- autonomous robot availability
```

This makes extension inspectable.

---

## 56. Explainability Through Dependency Slices

A user should be able to ask:

```text
Why is this capability red?
```

The resolver should return the smallest useful dependency slice.

For example:

```text
PaintShirts unavailable
because
QualifiedWorkerCapacity = 0

QualifiedWorkerCapacity = 0
because
WorkerSchedulability = 0

WorkerSchedulability = 0
because
HolidayCalendar_DE applies
and
no emergency staffing exemption is declared
```

A different query may expand the internal closure:

```text
Why is SafeWorkspaceCapacity only 12?
```

The system then reveals the ventilation-power feedback subsystem.

---

## 57. Minimal Blocking Sets

A capability may have several simultaneous failures.

The resolver should identify minimal blocking sets.

For example:

```text
{no worker}
```

may independently block production.

So may:

```text
{no electricity}
```

A combined set such as:

```text
{no worker, no electricity}
```

is not minimal if either member alone is sufficient to block the capability.

Minimal blocking sets help prioritize repair.

---

## 58. Sensitivity and Leverage

A field may have high downstream influence.

Changing one upstream field may alter many capabilities.

The system should calculate:

```text
downstream dependency count
margin sensitivity
repair leverage
common-mode risk
```

For example:

```text
AvailableElectricalPower
```

may be generatively central because it supports:

```text
lighting
ventilation
machines
computers
charging
communication
```

This does not imply that electrical supply is always the best intervention.

The current limiting constraint still matters.

---

## 59. Parallelism Has Coordination Costs

Parallel evaluation and parallel production are different.

The model may calculate health, weather, holidays, and geometry in parallel because their evaluations are independent.

But adding twenty workers does not automatically multiply production by twenty.

Production parallelism may be limited by:

```text
workspace
tools
supervision
material flow
coordination
quality inspection
shared exits
```

The same field algebra used for evaluation should expose these bottlenecks.

---

## 60. Caching and Materialized Composite Fields

Frequently used composite fields may be materialized.

Examples include:

```text
HumanHabitableEnvironment
SafeWorkspaceCapacity
AvailableElectricalPower
QualifiedWorkerCapacity
```

Caching reduces repeated evaluation.

But cached fields require:

```text
versioned dependencies
freshness thresholds
invalidations
confidence decay
```

A stale composite should not be treated as current merely because it exists.

---

## 61. Local and Global Views

A global view may show:

```text
yearly staffing margin
annual electricity balance
mission reliability
```

A local view may show:

```text
room 3 at 10:15
worker 27 at station 4
battery 2 during one charging cycle
```

The system should support projection between these scales.

A global average can hide a local failure.

A local anomaly may be irrelevant to the global capability if redundancy exists.

The projection operator should preserve the distinctions needed by the question.

---

## 62. A Capability-Compositor Interface

A possible user interface resembles a nonlinear editor.

```text
Scene:
Paint 100 shirts per day

Tracks / fields:
├── worker availability
├── worker health
├── workspace occupancy
├── lighting
├── ventilation
├── machine capacity
├── paint inventory
├── shirt inventory
├── electricity
├── maintenance
└── task demand
```

The interface may display:

```text
green regions:
requirements satisfied with margin

yellow regions:
conditional or fragile

red regions:
infeasible

gray regions:
unknown
```

Users may:

```text
expand a composite field
add a new provider
add a new constraint field
change resolution
inspect blocking sets
compare configurations
trace provenance
```

---

## 63. Compilation Pipeline

A practical compiler may proceed through:

```text
1. Parse desired capability.

2. Resolve capability and provider types.

3. Expand dependency closure.

4. Bind fields to declared domains.

5. Check units and semantic types.

6. Align spatial, temporal, and population frames.

7. Select active hierarchical modes.

8. Partition the horizon at relevant boundaries.

9. Build the field-operator dependency graph.

10. Identify strongly connected components.

11. Solve or bound self-closed subsystems.

12. Propagate capacity, uncertainty, and viability margins.

13. Detect missing coverage and minimal blocking sets.

14. Evaluate temporal requirements.

15. Estimate reliability and maintenance demand.

16. Generate detailed simulation only for unresolved dynamics.

17. Produce an inspectable realizability report.
```

---

## 64. Minimal Data Model

A minimal implementation may use five primary object classes:

```text
Field
Operator
ModeSystem
CapabilityRequirement
Closure
```

A field declares:

```text
domain
value type
resolution
uncertainty
provenance
```

An operator declares:

```text
accepted inputs
alignment rules
composition semantics
output type
failure conditions
```

A mode system declares:

```text
states
parallel regions
transitions
active dependencies
```

A capability requirement declares:

```text
target output
quality
rate
location
time horizon
population
reliability threshold
```

A closure declares:

```text
member fields
external inputs
external outputs
solution method
stability result
explanation interface
```

---

## 65. Example: Painting Shirts

Desired capability:

```text
paint 100 acceptable shirts per day
```

Required fields include:

```text
shirt supply
paint supply
design specification
worker capacity
workspace capacity
lighting
ventilation
drying capacity
quality inspection
electricity
maintenance
```

Spatial relations include:

```text
worker overlaps workstation
shirt overlaps manipulation region
paint overlaps transfer tool
drying region does not conflict with active painting region
evacuation paths remain clear
```

Temporal relations include:

```text
inputs arrive before consumption
painted shirts remain in drying region long enough
inspection follows drying
workers receive breaks
maintenance occurs before expected failure
```

The result may be:

```text
Nominal capacity:
112 shirts/day

Conservative capacity:
94 shirts/day

Requested:
100 shirts/day

Status:
conditionally feasible

Primary uncertainty:
worker absence correlation

Primary limiting subsystem:
ventilation-electricity-occupancy closure

Repair options:
- add 6 kW electrical reserve
- reduce simultaneous occupancy by 2
- extend production window by 45 minutes
```

---

## 66. Example: Software Development

Desired capability:

```text
deliver a software feature
```

Fields may include:

```text
developer availability
language competence
repository access
build environment
test infrastructure
requirement clarity
review capacity
deployment authority
```

Spatial proximity may be optional if communication infrastructure exists.

But shared temporal and semantic regions remain necessary.

For example:

```text
developer and reviewer
```

need not occupy the same room.

They require overlap through:

```text
shared repository
compatible language
review protocol
available review window
```

The field system therefore generalizes spatial overlap into interaction-medium overlap.

---

## 67. Example: Tutor and Student

Desired capability:

```text
teach concept X
```

A direct physical configuration may require:

```text
tutor present
student present
shared room
audible speech
visible materials
shared language
attention
```

A remote configuration replaces shared room with:

```text
network
microphone
camera or shared display
software compatibility
```

The capability is realized by different field intersections.

The resolver should keep the abstract requirement:

```text
bidirectional instructional interaction
```

separate from one implementation.

---

## 68. Example: Photovoltaic Extension

Initial model:

```text
AvailableElectricalPower
provided by
GridSupply
```

Extension:

```text
PVGeneration
BatteryStorage
```

The resolver adds:

```text
solar irradiance field
panel conversion operator
battery state field
charge-discharge operator
inverter constraints
```

It then invalidates:

```text
AvailableElectricalPower
electrical margin
dependent capabilities
```

It does not recompute unrelated material or geometric fields.

The annual result may show:

```text
grid energy reduced
daytime margin increased
nighttime capability unchanged
battery replacement demand introduced
new inverter single point of failure
```

Extension may improve one margin while adding new maintenance dependencies.

---

## 69. Example: Holiday and Health Extension

Initial worker capacity:

\[
C_{\text{team}}(t)
=
\sum_i C_i(t)
\]

New fields:

```text
HolidayCalendar(region, time)
PopulationHealthDistribution(group, season)
IndividualHealthObservation(worker, time)
```

Derived worker capacity becomes dependent on:

```text
employment interpretation
population prior
individual evidence
correlation model
reserve staffing
```

The resolver may conclude:

```text
average yearly capacity remains sufficient
but
two winter weeks have unacceptable shortfall probability
```

This is more useful than one annual average.

---

## 70. Failure Modes

A field-oriented capability system can fail through:

```text
wrong field identity
unit mismatch
invalid resampling
false independence assumption
missing spatial type
unmodeled common cause
stale cached field
hidden unstable closure
incorrect mode selection
excessive abstraction
insufficient resolution
undeclared authority dependency
```

A visually smooth composited result may still be wrong if its operators are semantically invalid.

The model must therefore preserve validation and provenance.

---

## 71. The Danger of Universal Fields

A temptation is to create one universal field containing every property of everything.

This defeats modularity.

A useful field should expose a coherent relation for a declared class of questions.

Too much detail causes:

```text
expensive recomputation
unintelligible dependencies
accidental coupling
difficult validation
```

Too little detail causes:

```text
false feasibility
hidden local violations
unsupported projection
```

The appropriate field boundary is an architectural decision.

---

## 72. Promotion Into a Stable Composite

A group of fields and operators may be promoted into a stable composite when:

```text
it is reused frequently
its internal relation is validated
its interface is stable
its failure modes are known
its explanation path is preserved
its maintenance cost is justified
```

Examples include:

```text
HumanHabitableEnvironment
QualifiedWorkerCapacity
SafeWorkspaceCapacity
AvailableElectricalPower
```

Promotion is organizational compression.

It preserves a lower-level closure as a higher-level invocable field.

---

## 73. Open-World Extension

The model should assume that new relevant fields will be discovered later.

Examples include:

```text
new health evidence
new holiday rule
new energy provider
new safety regulation
new machine degradation mode
new communication channel
```

Open-world extension requires:

```text
stable interfaces
typed contracts
versioned dependencies
incremental invalidation
unknown as a first-class result
```

A closed-world assumption would interpret all absent fields as irrelevant.

That is too optimistic for long-lived capability systems.

---

## 74. Central Principles

### Principle 1

Capabilities are distributed over domains.

```text
capability
!=
global boolean
```

### Principle 2

Space and time are first-class coordinates.

```text
existence
without overlap
does not imply interaction
```

### Principle 3

Fields are typed.

```text
arbitrary air
!=
human-compatible workspace
```

### Principle 4

Operators declare composition semantics.

```text
all curves
cannot be safely added
```

### Principle 5

Restriction is as important as production.

```text
constraints define admissible regions
```

### Principle 6

Statecharts select qualitative dependency structures.

```text
mode
changes
which relations are active
```

### Principle 7

Cyclic dependencies form self-closed subsystems.

```text
feedback
requires
fixed-point or dynamic solution
```

### Principle 8

Stable closures may be hidden behind inspectable interfaces.

```text
abstraction
should reduce clutter
without destroying explanation
```

### Principle 9

Independent field regions should be evaluated in parallel.

```text
dependency structure
determines
safe concurrency
```

### Principle 10

Changes should trigger incremental recomputation.

```text
new field
->
transitive dependents
not
entire model
```

### Principle 11

Resolution mismatch produces uncertainty.

```text
coarse evidence
cannot prove
fine-grained requirement
```

### Principle 12

Maintenance and replacement belong inside long-horizon capability.

```text
production-only specification
is incomplete
```

---

## 75. Compact Formal Summary

Let:

\[
\mathcal F
\]

be a set of typed fields.

Each field:

\[
F_i:D_i\to V_i
\]

declares:

```text
domain
value type
units
resolution
uncertainty
provenance
```

Let:

\[
\mathcal O
\]

be a set of typed field operators.

Each operator:

\[
\Phi_j:
(F_{j1},\ldots,F_{jn})
\rightharpoonup
G_j
\]

declares:

```text
domain alignment
composition semantics
uncertainty propagation
failure conditions
```

Let:

\[
\mathcal S
\]

be a collection of hierarchical mode systems.

The active mode configuration at time \(t\):

\[
s(t)\in\mathcal S
\]

selects the active dependency and operator relations.

Let:

\[
G_s=(V_s,E_s)
\]

be the resulting dependency graph.

Its strongly connected components define closure candidates.

For an acyclic component, evaluate by dependency order.

For a cyclic component \(K\), solve:

\[
x_K^\ast
=
F_K(x_K^\ast,u_K)
\]

or return an explicit unresolved or unstable result.

For capability requirement \(R\), derive available capacity field \(C\) and margin:

\[
M=C-R
\]

The viability region is:

\[
\mathcal V
=
\{d\mid M(d)\ge0\}
\]

subject to:

```text
confidence
resolution
reliability
authority
maintenance
```

When source field \(F\) changes, invalidate only:

\[
\operatorname{Affected}(F)
=
\{G\mid F\leadsto G\}
\]

Independent components may be scheduled in parallel.

The final result is not only:

```text
realizable
or
not realizable
```

It is a structured report containing:

```text
viable regions
margins
unknown regions
blocking sets
limiting closures
sensitivity
provenance
repair alternatives
```

---

## 76. Open Questions

Important open questions include:

```text
How should semantic field types be standardized?

How should probability distributions compose when dependencies are partially known?

When should a cyclic subsystem be represented by a fixed point,
and when should it remain a dynamic model?

How should field resolution be selected automatically?

How should the system detect that a hidden composite has forgotten
a distinction needed by a new downstream question?

How should human capability distributions be represented
without turning population statistics into individual judgments?

How should interaction media be modeled uniformly across
physical co-location,
networks,
language,
and institutional procedures?

How should explanations select the smallest useful dependency slice?

How should uncertainty and stale evidence propagate through cached composites?

When should a frequently reused closure be promoted into a maintained primitive?

How should the model compare alternative configurations
whose feasibility regions differ in space,
time,
risk,
and maintenance burden?
```

---

## 77. Design Target

The target system is not merely:

```text
a simulator
```

or:

```text
a project planner
```

or:

```text
a statechart editor
```

It is a capability compositor and resolver.

It should permit a user to:

```text
declare a desired capability
select candidate providers
inspect recursive requirements
add new fields later
compose spatial and temporal constraints
represent human and machine distributions
solve hidden feedback closures
evaluate fields in parallel
recompute only affected regions
inspect why a capability is unavailable
compare repair or replacement options
estimate viability over a mission horizon
```

The interface may look like a layered media editor.

The internal organization is a typed dependency and closure system.

The key result is not a rendered picture.

It is a map of where, when, and under which configurations a desired transition is actually realizable.

---

## 78. Central Claim

> Capability should be represented as a typed, distributed, and time-dependent field produced by explicit composition, restriction, allocation, transport, and closure operators over provider, resource, environment, authority, and maintenance fields.

And:

> Hierarchical modes select which dependency organizations are active; spatial and temporal overlap determine possible interaction; self-closed feedback regions are solved as composite subsystems; and explicit dependency structure permits parallel evaluation, late field extension, incremental recomputation, and inspectable preflight realizability.

---

## 79. Conclusion

The progression is:

```text
capability name
        ↓
dependency graph
        ↓
typed fields over space, time, and configuration
        ↓
field composition and restriction operators
        ↓
hierarchical mode selection
        ↓
self-closed subsystem solving
        ↓
viability margins
        ↓
incremental and parallel evaluation
```

This framework preserves the useful intuition of layered timelines while extending it into literal spatial, temporal, population, authority, resource, and maintenance domains.

A worker is not simply available.

The worker is available over a field.

A room is not simply present.

It provides typed occupancy, environmental, and interaction regions.

A machine is not simply operational.

Its capability is restricted by power, maintenance, environment, task input, and operator support.

A new health distribution, holiday calendar, photovoltaic source, safety rule, or degradation model can be added later as another typed field.

The dependency graph determines what must change.

The closure structure determines what must be solved together.

The operator algebra determines how the fields interact.

The result is a model that can remain extensible without becoming flat, global, or opaque.

Its practical ambition is straightforward:

> Before attempting a complex organization, render its capability fields, expose the missing intersections, solve the self-dependent closures, and determine whether the desired capability is green anywhere that matters.
