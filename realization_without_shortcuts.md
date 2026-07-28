# Realization Without Shortcuts: Infrastructure, Locality, and the Limits of Compression

## Abstract

A person can represent a journey as:

```text
home
->
work
```

But a vehicle cannot ordinarily realize that journey merely because its endpoints are named.

It requires a traversable route, a suitable vehicle, energy, control, and a sufficiently connected sequence of physical conditions between departure and arrival.

Likewise, a buyer can represent a transaction as:

```text
repeat order
->
package arrives
```

But the represented relation does not itself move matter, settle payment, cross borders, or deliver a package. Those results require an actual realization path.

This document develops a distinction between:

```text
representational compression
```

and:

```text
realization.
```

A representation may suppress arbitrarily many distinctions. Reality cannot suppress a condition that remains necessary for the outcome. A missing road segment, broken wire, unavailable vehicle, absent authorization, or unexecuted intermediate transformation may prevent the result even when the high-level description remains unchanged.

Infrastructure therefore should not primarily be understood as compressed reality. It is maintained realizability: organized physical, informational, institutional, and control conditions that make certain transformations possible.

The central claim is:

> A high-level description may omit intermediate distinctions, but a successful outcome still requires a sufficiently connected path of admissible realizing transitions.

A second claim follows:

> Infrastructure does not abolish the intermediate work of reality. It constructs, stabilizes, redirects, distributes, and reuses the conditions under which that work can occur.

A third claim concerns bounded agents:

> Boundedness explains why agents use coarse representations. It does not by itself explain why coarse representations are reliable, why large organizations arise, or why desired outcomes remain realizable.

The framework developed here distinguishes:

```text
omission in a description
from
absence in reality
```

```text
causal reorganization
from
causal elimination
```

```text
geometric smoothness
from
physical connectivity
```

```text
stored capability
from
current activation
```

```text
reduced agent effort
from
reduced total realization
```

and:

```text
local invocation
from
the maintained path that makes invocation effective.
```

---

## 1. The Road-Segment Test

Suppose a person lives at location \(A\) and works at location \(B\).

At home there is a short road segment.

At work there is another short road segment.

Representationally, one may write:

```text
A
->
B
```

But two disconnected endpoint segments do not ordinarily permit a wheeled vehicle to travel from one to the other.

A traversable realization requires something more like:

```text
A
->
locally supported motion
->
continued support
->
continued controllability
->
B
```

If a sufficiently disruptive gap appears in the route, the vehicle may stop, become stuck, fall, or require a different mode of transport.

The high-level intention remains:

```text
drive from A to B
```

The physical possibility has changed.

This gives a simple test:

> If an allegedly compressed-away element can be removed while the representation remains unchanged but the outcome becomes impossible, then that element was omitted from the representation, not eliminated from realization.

The road-segment example is therefore not merely an illustration of hidden complexity.

It reveals a structural distinction between:

```text
the endpoints named by an agent
```

and:

```text
the connected conditions required by the world.
```

---

## 2. Boundedness Is Not Yet an Explanation

A bounded agent has finite:

```text
attention
memory
observation
computation time
energy
skill
control bandwidth
```

This explains why an agent cannot actively represent every intermediate transition.

It does not explain why:

```text
a coarse description remains reliable
```

or why:

```text
a much larger organization exists
```

or why:

```text
the desired outcome is physically reachable.
```

Boundedness creates pressure toward selective representation.

It does not automatically generate:

```text
roads
vehicles
ports
protocols
warehouses
currencies
standards
repair systems
```

Nor does it imply that any arbitrary chain can be hidden without consequence.

A bounded agent can represent:

```text
A
->
B
```

whether or not \(B\) is reachable from \(A\).

Therefore:

> Boundedness explains the demand for abstraction, but not the truth of an abstraction.

The truth of the abstraction depends on the organization of the realizing world.

---

## 3. What Can Actually Be Compressed?

The word `compression` can refer to several different things.

They should be separated.

### Representational compression

A description suppresses distinctions:

```text
unlock car
start engine
leave driveway
follow route
park
```

becomes:

```text
drive to work
```

The realization has not been shortened by the sentence.

Only the active description has changed.

### Decision compression

Repeated decisions are replaced by a reusable rule:

```text
if route is open and destination unchanged
then follow stored route
```

The agent performs fewer fresh deliberations.

### Control compression

A controller accepts a high-level target and handles lower-level corrections:

```text
maintain speed
```

instead of:

```text
continuously calculate every actuator adjustment
```

The lower-level control remains physically realized.

### Organizational reuse

Prior work is embedded in:

```text
roads
machines
standards
software
training
contracts
```

Later users invoke the result without reconstructing it.

### Amortization

A costly structure is constructed once and used many times.

The cost per invocation may fall even when the total structure is large.

### Parallelization

Many realizing transitions occur simultaneously across different components.

The elapsed time seen by one user may fall without eliminating the work.

### Causal reorganization

A realization path is replaced by a different one:

```text
manual excavation
```

may become:

```text
mechanized excavation
```

The new path may require different materials, machines, control, and energy.

None of these necessarily implies:

```text
reality itself became smaller.
```

They imply that distinctions, decisions, costs, control, time, or repeated construction were redistributed.

---

## 4. Omission Is Not Elimination

Consider a realized chain:

\[
x_0
\xrightarrow{T_1}
x_1
\xrightarrow{T_2}
\cdots
\xrightarrow{T_n}
x_n.
\]

An observer may write:

\[
x_0 \Rightarrow x_n.
\]

This notation may be adequate for a selected purpose.

But it does not follow that:

\[
x_1,\ldots,x_{n-1}
\]

ceased to exist or ceased to matter.

The compressed arrow can mean:

> There exists an accepted realization path from \(x_0\) to \(x_n\), and the current observer is not representing its internal distinctions.

It should not mean:

> The outcome occurs without any realizing transitions.

The first is abstraction.

The second is a claim of ontological discontinuity.

They are not interchangeable.

---

## 5. The Realization-Path Requirement

Let a system have:

```text
states
admissible local transitions
disturbances
constraints
```

A desired outcome \(g\) is reachable from initial state \(x\) only if there exists some admissible path:

\[
x=x_0
\to x_1
\to \cdots
\to x_n=g.
\]

For continuous models, this may be represented as a trajectory:

\[
\gamma:[t_0,t_1]\to \mathcal{S},
\]

where \(\mathcal{S}\) is a state space and the evolution of \(\gamma\) satisfies the relevant physical constraints.

The important claim is not that every path must be geometrically smooth.

It is:

> The outcome requires a connected sequence of admissible realizing states or events.

The chain may contain:

```text
discrete switches
impacts
phase transitions
vehicle transfers
software state changes
institutional authorizations
waiting periods
```

It need not resemble a smooth line.

But it cannot contain an unexplained gap at which the required state simply appears without any realizing process.

---

## 6. Geometric Continuity, Smoothness, and Causal Connectivity

Several distinct ideas are often grouped under the word `continuity`.

### Geometric adjacency

A body moves through neighboring regions of space rather than disappearing at one location and appearing at another.

### Temporal persistence

A system continues through intermediate times, even when little observable action occurs.

### Smoothness

A mathematical trajectory changes without abrupt corners, jumps, or discontinuities in selected derivatives.

### Causal connectivity

Later states depend on earlier states through admissible realizing interactions.

These are not identical.

A road can contain:

```text
sharp turns
surface changes
intersections
movable bridges
ferries
elevators
```

without being globally smooth.

A vehicle journey can also include discrete mode changes:

```text
car
->
ferry
->
car
```

The realization remains connected because each transfer supplies a compatible next condition.

Thus the road example does not establish a universal smoothness requirement.

It establishes a compatibility and connectivity requirement.

The relevant question is not:

> Is the route mathematically smooth everywhere?

It is:

> At every required transition, is there a physically admissible way for the journey to continue?

---

## 7. Can Road Segments Be Skipped?

Yes, but only by replacing the missing support with another realization mechanism.

Examples include:

```text
jumping a small gap
crossing by bridge
using a ferry
flying over the gap
laying a temporary surface
switching to a vehicle with different capabilities
```

In each case, the road segment is not simply ignored.

The required function is supplied differently.

The relevant function may be:

```text
support weight
maintain traction
preserve controllability
bridge elevation difference
cross an obstacle
```

A missing road segment matters only insofar as some required function is no longer realized.

Therefore the stronger principle is not:

> Every centimeter of road is necessary.

It is:

> Every necessary enabling function must be realized by some admissible structure or process.

One realization substrate may substitute for another.

The requirement for realization does not disappear.

---

## 8. Infrastructure as Maintained Reachability

Infrastructure changes which states are reachable at acceptable cost, time, risk, and control burden.

A road does not merely describe a connection.

It modifies the physical environment so that a class of vehicle trajectories becomes possible.

A bridge modifies reachability across a river.

A power grid modifies the reachable operating states of machines.

A legal identity system modifies the reachable institutional actions of a recognized person.

A software protocol modifies the set of compatible communications between systems.

Infrastructure can therefore be defined as:

> Maintained organization that preserves a class of admissible realization paths.

This definition includes:

```text
physical structures
stored energy
control systems
standards
records
permissions
trained roles
repair processes
```

Infrastructure is not merely a hidden middle.

It is part of the world that makes the endpoint relation true.

---

## 9. Construction Does Not Compress Reality

Suppose travel from \(A\) to \(B\) is initially difficult.

A road is constructed.

The traveler later experiences:

```text
less effort
less route finding
less uncertainty
shorter travel time
```

But the road required:

```text
surveying
excavation
material production
transport
paving
drainage
signage
maintenance
```

The world did not become smaller.

Additional organized structure was added.

The later journey became easier because earlier work was preserved.

This suggests:

> Many apparent compressions are transfers of effort from present invocation to prior construction and ongoing maintenance.

The low local cost of use may conceal a large stock of accumulated organization.

---

## 10. The Difference Between a Shortcut and a New Path

A shortcut is often described as if intermediate reality were bypassed.

But a physical shortcut is ordinarily a newly available realization path.

A tunnel shortens a route by constructing a different traversable path.

A bridge avoids a detour by creating new support across a gap.

An aircraft crosses terrain by using aerodynamic lift rather than continuous ground support.

A radio link avoids a cable along a selected route but still requires:

```text
transmission
propagation
reception
energy
compatible equipment
```

A shortcut therefore does not mean:

```text
no middle
```

It means:

```text
a different middle.
```

The path may be shorter according to:

```text
distance
time
energy
number of decisions
number of institutional handoffs
```

But it remains a realized path.

---

## 11. Delayed Activation Is Still Continuous Realization

Consider a timed explosive placed during excavation.

The desired pattern is:

```text
prepare now
->
activate later
```

The temporal gap is not an absence of realization.

During the delay, relevant physical state persists:

```text
material remains placed
stored energy remains available
the timing mechanism evolves
the arming state is preserved
environmental conditions continue to act
```

At the selected time, the mechanism changes state and initiates a rapid process.

The delay therefore illustrates:

> Inactivity at the level of human attention is not inactivity at the level of physical realization.

A maintained latent capability can bridge long periods without continuous human intervention.

The bomb is not causally absent during the delay.

It is physically present in a state whose future transition remains enabled.

---

## 12. Stored Capability and Activated Path

A road network exists before a particular journey.

A logistics network exists before a particular purchase.

A machine exists before a particular command.

These structures represent stored capability.

When an agent acts, only part of that capability may be activated.

Let:

```text
G = maintained capability graph
x = current state
u = invocation or control input
P(x,u) = activated realization path
```

Then:

\[
P(x,u)\subseteq G.
\]

The invocation does not construct the entire graph.

It selects and activates a path within an already organized possibility structure.

This explains how a small instruction can have a large effect without containing a complete description of the effect.

The causal capacity resides largely in the maintained system.

The input selects among its possibilities.

---

## 13. Reasons Do Not Supply Missing Physics

A person may have the reason:

```text
I need to reach work.
```

That reason can alter behavior.

It may cause the person to enter a vehicle and follow a route.

But the reason does not itself:

```text
support the wheels
provide fuel
create traction
bridge gaps
move air
maintain the vehicle
```

Reasons can select and initiate realization paths.

They do not replace the conditions those paths require.

Therefore:

> The causal reach of a reason depends on the organized capacities available to receive it.

A command becomes effective because it enters a system already capable of expanding the command into physical transitions.

---

## 14. Interface Truth

A high-level interface may expose:

```text
drive to work
```

or:

```text
repeat order
```

The interface is trustworthy only if the hidden realization remains available under relevant conditions.

Let an interface promise:

\[
I:x\rightharpoonup G.
\]

This should be interpreted as:

> Given accepted requirements and operating conditions, invocation from state \(x\) is supported by at least one maintained admissible path to an outcome in \(G\).

The interface does not prove that the path will always succeed.

It claims that the path exists with sufficient reliability for the intended use.

When a road collapses, a payment system fails, or a vehicle becomes unavailable, the interface may remain linguistically meaningful while becoming physically or institutionally false.

---

## 15. The Correspondence Between Representation and Reality

A coarse representation can correspond accurately to reality even when it omits most internal distinctions.

The representation:

```text
A reaches B
```

may be true if:

```text
there exists a realized admissible path from A to B.
```

Its truth does not require every intermediate state to appear as a separate symbol.

But its truth does require the relevant relation to be realized.

This gives a distinction between:

```text
symbolic sparsity
```

and:

```text
ontological sparsity.
```

A statement can be symbolically sparse while referring to a causally dense realization.

The sparsity of the statement is not evidence that the world itself skipped the intermediate work.

---

## 16. Reality Is Not Compressed by Being Correctly Described

Suppose the statement:

```text
the package arrived
```

is true.

The truthmaker may include:

```text
physical movement
sorting
custody changes
address recognition
energy use
human or machine control
```

The statement does not need to list these.

But the truth of the statement depends on some realized history that makes arrival the case.

A correct high-level representation therefore does not violate reality.

It abstracts over the realization while preserving the relation relevant to the statement.

The more precise formulation is:

> Representations can be compressed because truth can be invariant under omission of distinctions irrelevant to the selected claim.

Reality itself need not be compressed for the representation to be accurate.

---

## 17. Query-Relative Adequacy

Let:

```text
R = detailed realization model
M = coarse model
Q = selected query
```

The coarse model is adequate when:

\[
Q(M)\approx Q(R)
\]

within an accepted tolerance.

For the query:

```text
Can I reach work by 09:00?
```

many molecular and mechanical details may be irrelevant.

For the query:

```text
Why did the wheel become stuck at this point?
```

surface geometry, material strength, tire shape, and load may become relevant.

The world has not changed between the queries.

The required represented distinctions have.

Thus:

> Compression is primarily query-relative at the level of representation, not absolute at the level of realization.

---

## 18. Failure as a Realizability Test

Failures reveal which hidden conditions were genuinely load-bearing.

A road gap tests whether another supporting path exists.

A broken wire tests whether current can be routed elsewhere.

A failed authorization tests whether another institutional path can satisfy the same requirement.

A delayed package tests which local commitment failed to transition.

Failure therefore distinguishes:

```text
details that were merely omitted
```

from:

```text
conditions whose absence breaks reachability.
```

This gives a practical rule:

> To test whether a component is realizationally necessary, remove or perturb it and examine whether an admissible substitute path remains.

Necessity is relative to the available alternatives, not merely to one familiar implementation.

---

## 19. Substitution and Functional Equivalence

A road segment may be replaced by a bridge.

A human operator may be replaced by a controller.

A paper credential may be replaced by a digital credential.

A local warehouse may be replaced by a distant warehouse with faster transport.

These substitutions show that the necessity of one component does not imply the necessity of its exact form.

What remains necessary is a function within the realization:

```text
support
transport
identify
authorize
store
transform
control
```

Let component \(c_1\) and component \(c_2\) be functionally equivalent for a selected envelope when:

\[
F(c_1,\Theta)\approx F(c_2,\Theta).
\]

Then one may substitute for the other under conditions \(\Theta\).

This is not elimination of realization.

It is replacement of one realizing mechanism by another.

---

## 20. Locality and the Physical World

The road example invites a stronger question:

> Must every physical realization be locally connected in spacetime?

The framework itself should not answer this purely by definition.

That is partly an empirical question for physics.

However, ordinary infrastructure, transport, computation, and communication all rely on processes whose effects are propagated through physical interactions and persisting states.

Even apparently remote coordination requires some realizing substrate:

```text
fields
signals
matter
stored state
shared prior interaction
classical records
```

Quantum entanglement is sometimes invoked as an apparent exception because spatially separated measurements can exhibit correlations not reproducible by ordinary local hidden-variable models.

But such correlations should not casually be treated as a usable jump that transports arbitrary matter, energy, or controllable information from \(A\) to \(B\) without a preparation history or communication structure.

The conservative claim is therefore:

> No known infrastructure permits an agent to omit every realizing connection between separated physical outcomes.

A future physical theory might revise what counts as a connection.

It would not make realization unnecessary.

---

## 21. Why Distinguish Causal and Geometric Connectivity?

People distinguish causal from geometric connectivity because a causal dependency need not be represented in the geometry relevant to a particular observer.

For example:

```text
payment authorization
->
warehouse release
```

is a causal and institutional dependency.

Its geometric realization may pass through many devices and locations that the warehouse system does not model.

Similarly:

```text
software call
->
remote service response
```

is represented as one dependency while being physically realized through distributed hardware.

The distinction is therefore useful at the level of models.

But at the level of physical realization, causal dependencies still require some admissible physical history.

So the distinction should be formulated carefully:

```text
causal connectivity
=
which state depends on which prior state
```

```text
geometric or spacetime realization
=
how that dependency is physically carried
```

The first can be modeled without displaying the second.

The second cannot be assumed absent merely because it is omitted.

---

## 22. No Magic-Jump Principle

The road example suggests a minimal principle:

> An outcome cannot be explained by naming its initial and final states while leaving the realizing transition entirely absent.

This may be called the No Magic-Jump Principle.

It does not require one specific ontology.

It requires only that successful transformation be grounded in some admissible process.

A proposed explanation fails when it says, in effect:

```text
A
->
B
```

while providing no account of:

```text
what carried state
what supplied energy
what preserved identity
what constrained the transition
what made B reachable from A
```

The principle is methodological as well as metaphysical.

It prevents a symbol from being mistaken for the process it denotes.

---

## 23. A Possible Conservation Principle

It may be tempting to say that realization complexity is conserved.

That claim is too strong without a defined measure.

A better provisional principle is:

> Necessary realizing functions cannot simply be discarded; they must be performed, avoided by changing the goal, or replaced by an alternative mechanism.

The associated burdens may be:

```text
shifted into prior construction
spread across many users
performed in parallel
automated
stored in physical structure
transferred to another organization
reduced by a better path
```

But when an outcome still requires a function, some system must realize it.

This is closer to conservation of obligation than conservation of a scalar quantity.

---

## 24. Realization Debt

A representation may promise more than the current infrastructure can realize.

For example:

```text
instant delivery
universal access
seamless interoperability
fully autonomous operation
```

These descriptions create realization obligations.

If the necessary paths do not yet exist, the difference may be called realization debt:

```text
promised relation
-
maintained reachable relation
```

Realization debt can be hidden temporarily by:

```text
manual intervention
exception handling
subsidy
fragile workarounds
unreported failures
```

But it reappears under scale, disturbance, or inspection.

This concept distinguishes genuine infrastructure from aspirational interface language.

---

## 25. Infrastructure as Accumulated Realization Work

A mature infrastructure contains preserved results of earlier work:

```text
surveyed routes
constructed surfaces
verified standards
trained operators
stored records
reserve capacity
repair knowledge
```

The current user does not repeat this work.

But the work remains materially or institutionally embodied.

Infrastructure is therefore:

> Accumulated realization work maintained in a reusable form.

This explains why invocation can be locally cheap while capability remains globally expensive.

The user pays only part of the causal and historical cost at the moment of use.

---

## 26. The Bounded Agent Reinterpreted

The bounded agent is still important, but its role changes.

The agent does not cause infrastructure to exist merely by being bounded.

Rather:

```text
boundedness
->
need for selective representation
```

while:

```text
recurring goals
+
available energy and materials
+
coordination
+
learning
+
maintenance
->
infrastructure
```

The agent can then use a small representation because the environment has been reorganized to support it.

The relationship is:

```text
bounded agent
+
coarse intention
+
maintained realization substrate
->
reachable outcome
```

Boundedness explains the interface scale.

Infrastructure explains the reliability of acting through that interface.

---

## 27. Organizations Larger Than Agents

A vastly larger organization does not follow logically from boundedness alone.

Additional conditions are required:

```text
recurring demand
specialization
coordination benefits
stored state
standardization
energy surplus
material capacity
maintenance
institutional persistence
```

Large organizations emerge when distributed cooperation or mechanization can preserve realization paths that isolated agents cannot maintain alone.

Thus:

> Boundedness makes delegation useful, but repeated realizability problems make maintained organization valuable.

This is a causal and historical account, not a deduction from finitude.

---

## 28. Reorganization Without Ontological Compression

Infrastructure can radically change a realization path.

A mountain journey may change from:

```text
walk around mountain
```

to:

```text
drive through tunnel
```

A calculation may change from:

```text
manual symbolic work
```

to:

```text
electronic computation
```

A message may change from:

```text
physical courier
```

to:

```text
electromagnetic transmission
```

These changes may reduce:

```text
elapsed time
human effort
error rate
marginal cost
```

Yet they often increase:

```text
capital structure
energy dependence
technical specialization
maintenance burden
```

The resulting organization may be more efficient for a selected objective while being more complex in total.

Therefore:

> Reorganization can reduce one measured burden without constituting absolute compression of reality.

---

## 29. When Is `Compression` Still a Useful Word?

The term remains useful if its target is stated explicitly.

Reasonable uses include:

```text
compression of description
compression of active decision depth
compression of user-visible control
compression of repeated coordination
compression of elapsed time through parallelism
compression of marginal effort through reuse
```

The term becomes misleading when it implies:

```text
necessary physical realization vanished
```

or:

```text
a symbol performs the work of the process it denotes.
```

A disciplined framework should therefore always ask:

> What exactly is being compressed, relative to which observer, objective, metric, and time horizon?

---

## 30. A Realizability-Oriented Formal Model

Let:

```text
A = invoking agent
x = initial state
G = desired outcome set
U = available agent inputs
S = system state space
R = admissible transition relation
I = maintained infrastructure
Θ = operating conditions
```

Infrastructure modifies the available transition relation:

\[
R_I \subseteq S\times S.
\]

An outcome \(g\in G\) is realizable from \(x\) under infrastructure \(I\) when there exists a path:

\[
x=x_0,
 x_1,
 \ldots,
 x_n=g
\]

such that:

\[
(x_i,x_{i+1})\in R_I
\]

for every required transition.

The agent need not represent the full path.

The agent may use an interface:

\[
J_I:x\rightharpoonup G.
\]

The interface is warranted only if the maintained system makes the relevant path sufficiently available:

\[
\operatorname{AvailablePath}(x,G,R_I,\Theta).
\]

Representational compression is therefore a relation between:

```text
the detailed path
```

and:

```text
the agent's model of reachability.
```

It is not an erasure of \(R_I\).

---

## 31. Smoothness Is Not the Fundamental Constraint

The road intuition may suggest that realization must be smooth.

But many successful processes contain discontinuities in a selected description:

```text
relay switches
chemical ignition
gear changes
contract signatures
phase transitions
packet handoffs
```

The more fundamental constraint is admissibility.

A transition may be abrupt yet physically realized.

A path may be piecewise continuous, discrete, stochastic, or hybrid.

What matters is that each transition is licensed by the relevant dynamics and available structures.

Thus:

> Reality need not be smooth in every representation, but it must not rely on an ungrounded transition.

---

## 32. Hybrid Realization Chains

Modern infrastructure combines several kinds of transitions:

```text
physical
informational
institutional
human
algorithmic
```

For example:

```text
button press
->
digital message
->
payment authorization
->
warehouse instruction
->
physical transport
->
legal border crossing
->
delivery
```

Some arrows describe physical propagation.

Others describe state changes whose realization includes recognized rules, records, and authorized roles.

A complete account must avoid two errors:

```text
reducing institutional transitions to mere words
```

and:

```text
treating institutional recognition as independent of physical implementation.
```

Institutional facts have causal consequences because they are maintained through physical records, trained agents, enforcement structures, and coordinated expectations.

They are not geometric road segments.

But they still require realizing organization.

---

## 33. Maintained Continuity

A realization path may exist now and fail later.

Roads erode.

Machines wear.

Records drift.

Authorities change.

Standards become incompatible.

Therefore infrastructure must preserve more than initial construction.

It must preserve continuity across time.

Let \(R_I(t)\) be the available transition relation at time \(t\).

A capability remains maintained over horizon \(H\) when the required reachability relation stays within tolerance:

\[
\forall t\in H,
\quad
\operatorname{Reachable}_{R_I(t)}(x,G)
\]

or when deviations are detected and repaired before violating the required service envelope.

Infrastructure is therefore not a static object.

It is an ongoing achievement.

---

## 34. The Cost of Removing the Middle

Suppose one wishes to remove a road, warehouse, protocol, operator, or approval step.

Three possibilities exist.

### The function was unnecessary

The component can be removed without changing reachable outcomes.

Then it was redundant, obsolete, or incorrectly modeled as necessary.

### Another component already performs the function

The component can be removed because a substitute path exists.

Then the realization was reorganized, not eliminated.

### The function remains necessary and has no substitute

Removal breaks reachability.

The desired endpoint relation becomes false.

This gives a simple diagnostic:

> Removing the middle is legitimate only when the required realizing functions are unnecessary or supplied elsewhere.

---

## 35. Apparent Violations of Reality

A technology can appear to circumvent reality when it relocates costs or transitions outside the user's frame.

Examples include:

```text
cloud computing
wireless communication
instant payment
same-day delivery
autonomous control
```

The user sees:

```text
request
->
result
```

The hidden realization may include:

```text
data centers
radio infrastructure
settlement systems
inventory positioning
trained models
energy consumption
maintenance labor
```

The appearance of violation comes from a mismatch between:

```text
visible local action
```

and:

```text
distributed prior and current realization.
```

No physical law is circumvented.

The burden is displaced, organized, and concealed from the immediate interface.

---

## 36. Infrastructure and Freedom

Infrastructure can increase practical freedom by enlarging reachable outcomes.

Without roads, vehicles, communication, records, and institutions, an isolated agent's reachable set is small.

But infrastructure also introduces dependencies.

The relevant question is not:

```text
dependence or independence?
```

It is:

```text
which realization paths exist?
who controls them?
how fragile are they?
what substitutes remain?
which costs are hidden?
```

Freedom can therefore be understood partly as:

> Access to sufficiently robust and governable realization paths among valued states.

---

## 37. Pathological Abstraction

A high-level interface becomes pathological when it suppresses distinctions required for:

```text
safety
consent
risk evaluation
repair
accountability
governance
```

For example, an interface may say:

```text
available
```

while hiding:

```text
single-point dependency
unsafe operating conditions
unpriced external cost
unreliable maintenance
lack of recourse
```

The problem is not abstraction itself.

The problem is that the omitted distinctions remain decision-relevant.

Responsible abstraction therefore requires:

```text
ordinary simplicity
+
selective reopenability
+
truthful operating conditions
```

---

## 38. Revised Central Thesis

The framework can now be stated without claiming that reality itself is compressed.

> Bounded agents act through coarse representations. These representations become reliable when maintained infrastructure preserves sufficiently connected realization paths between the states named by the representation.

A second formulation is:

> Civilization does not primarily compress reality. It accumulates reusable organization that makes selected high-level relations true at manageable local cost.

A third formulation is:

> What becomes small is the agent's active description, decision burden, and invocation effort. What remains large is the realizing organization distributed across space, time, matter, energy, records, and other agents.

---

## 39. Central Principles

### Representational-Omission Principle

> A description may omit intermediate distinctions without implying that the corresponding realizing conditions are absent.

### Realization-Path Principle

> A reachable outcome requires a sufficiently connected sequence of admissible realizing states or events.

### No Magic-Jump Principle

> Naming an initial and final state does not explain or produce the transition between them.

### Functional-Substitution Principle

> A particular component may be removed only when its function is unnecessary or realized by an admissible substitute.

### Infrastructure-as-Reachability Principle

> Infrastructure is maintained organization that preserves classes of admissible paths among states.

### Prior-Work Principle

> Low-cost invocation often depends on work performed earlier and preserved in reusable structure.

### Activation Principle

> A small input can have large effects by selecting and activating a path within a maintained capability graph.

### Boundedness-Limitation Principle

> Boundedness explains selective representation but does not by itself explain reliability, reachability, or organizational scale.

### Reorganization Principle

> Technology can replace one realization path with another without eliminating the need for realization.

### Query-Relative Compression Principle

> Compression is meaningful only relative to a representation, observer, metric, query, and horizon.

### Maintained-Continuity Principle

> A reusable capability remains true only while the enabling path is monitored, repaired, and preserved through time.

### Realization-Debt Principle

> An interface that promises relations unsupported by maintained paths accumulates hidden obligations that reappear under failure or scale.

---

## 40. Central Statements

> Two endpoint road segments do not make a road.

> A high-level arrow is not a physical bridge.

> A gap can be skipped only by another mechanism that realizes the missing enabling function.

> Smoothness is not always required; admissible connectivity is.

> A delayed process remains physically realized through stored state and temporal evolution.

> Infrastructure is not compressed reality. It is maintained reachability.

> A shortcut is usually a different middle, not no middle.

> Boundedness creates the need for abstraction but does not make abstractions true.

> Reality can be reorganized, parallelized, amortized, and externally controlled without being symbolically erased.

> The local representation may be small because the realizing capacity already exists elsewhere.

> A reason can select a path but cannot supply missing support, energy, material, or authority.

> The truth of a compressed statement depends on a realization that may be far denser than the statement.

> What civilization accumulates is not freedom from reality, but reusable ways of satisfying it.

---

## 41. Research Questions

### Realizability metrics

How should the difficulty of a realization path be measured across energy, time, control, risk, and institutional complexity?

### Functional necessity

How can one distinguish a genuinely necessary function from a historically inherited implementation?

### Path substitution

When are two realization mechanisms equivalent enough to support the same interface?

### Hybrid chains

How should physical, computational, institutional, and human transitions be represented in one framework without collapsing their differences?

### Locality

Which parts of the Realization-Path Principle are logical requirements, and which depend on contingent physical laws of our universe?

### Smoothness

What mathematical structure best represents infrastructure paths that combine continuous motion, discrete switching, stochastic events, and institutional state changes?

### Realization debt

How can systems detect when an interface promises more than its maintained substrate can support?

### Prior construction

How should the causal and economic contribution of past infrastructure investment be allocated to present invocations?

### Maintenance

Which observations are sufficient to establish that a realization path remains available over a given horizon?

### Compression measures

Can representational, decision, control, temporal, and marginal-cost compression be measured separately?

### Reopenability

Which hidden distinctions must remain inspectable for diagnosis, safety, consent, and governance?

### Civilizational capability

Can social capability be characterized as the maintained set of reachable transformations available to ordinary agents within bounded local effort?

---

## 42. Conclusion

A person can represent a journey with two symbols:

```text
A
->
B
```

Reality does not become two symbols.

The journey succeeds only if there exists a realizable path connecting the initial and final states.

A road is one way of supplying such a path.

A bridge, ferry, aircraft, or tunnel may supply another.

A missing road segment can be omitted only when some substitute mechanism performs the function that the segment would otherwise provide.

This suggests that the central phenomenon is not the compression of reality.

It is the relation between:

```text
coarse representation
```

and:

```text
maintained realizability.
```

Bounded agents require coarse representations because they cannot represent or control every intermediate distinction.

But boundedness alone does not make the world traversable.

Traversability must be constructed.

Reachability must be maintained.

Compatible transitions must exist.

Energy, matter, information, authority, and control must be organized so that the intended path remains admissible.

Infrastructure performs this work.

It does not violate reality.

It invests in reality.

It adds surfaces, machines, records, standards, stored energy, trained roles, and repair processes so that selected transformations become repeatedly available.

The agent then experiences a small interface:

```text
drive
order
send
activate
```

The smallness of the instruction is not the smallness of the realization.

It reflects the prior existence of a capability that can interpret and expand the instruction.

The strongest formulation is therefore:

> Reality permits representational shortcuts because a statement need not enumerate every condition that makes it true. Reality does not permit realization shortcuts in the sense of obtaining an outcome while every necessary enabling function remains absent.

What appears to be compression is usually one or more of the following:

```text
omission from description
reuse of prior construction
redistribution of control
parallel execution
replacement by a better path
transfer of effort to maintenance
activation of stored capability
```

These are genuine achievements.

They can make action dramatically easier for a bounded agent.

But they do not turn endpoints into a path.

They make a path exist.
