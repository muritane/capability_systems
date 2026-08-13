# From World Constraints to Endogenous Mobility Frontiers: Feasible Graphs, Capability Composition, and Reality-Coupled Search

## Abstract

A mobility planner does not choose routes from all imaginable movements.

It acts from:

```text
a real current location
a real capability state
a real access state
a real legal environment
a real transport network
a real budget
a real time horizon
```

The physical and institutional world determines which transitions exist.

The agent's current state determines which of those transitions are usable.

This suggests a distinction between:

\[
G_{\text{world}}
\]

the graph of mobility transitions represented as existing in the world, and:

\[
G_{\text{feasible},t}
\]

the subset currently executable by a particular agent.

A driver's license does not create roads.

A car-rental subscription does not create roads either.

But together with vehicle availability, payment capability, jurisdictional validity, and other prerequisites, they may unlock a large family of transitions already present in the world model.

Thus:

\[
\boxed{
\text{world possibility}
\neq
\text{agent feasibility}
}
\]

and:

\[
\boxed{
\text{capability-changing action}
=
\text{action that changes which world transitions become feasible later}
}
\]

This produces a concrete interpretation of endogenous frontier expansion.

The system is not merely searching for the best route through a fixed graph.

It is sometimes deciding whether to change:

```text
licenses
subscriptions
vehicle access
skills
location
infrastructure
representation
legal compatibility
resource availability
```

so that a different feasible graph becomes available later.

Mobility is therefore a useful domain for explicit constraint modeling because physical reality, infrastructure, law, and agent capability impose hard limits that search cannot simply optimize away.

---

## 1. Mobility Begins From a Real Current State

Let:

\[
S_t
\]

be the current mobility state.

It may contain:

```text
current location
current time
available money
owned vehicles
borrowable vehicles
rental memberships
public-transport subscriptions
tickets
licenses
visas
physical mobility constraints
battery or fuel state
parking access
charging access
known routes
current reservations
```

The system does not begin from:

\[
S^\*,
\]

the state it would prefer to already have.

It begins from the mobility state that actually exists.

Thus:

\[
\boxed{
\text{desired mobility}
\neq
\text{currently executable mobility}
}
\]

---

## 2. The World Graph and the Agent Graph Are Different

Let:

\[
G_{\text{world}}=(V,E)
\]

represent mobility transitions believed to exist in the world.

Nodes may represent:

```text
places
stations
ports
airports
road intersections
parking locations
charging locations
border crossings
```

Edges may represent:

```text
walking
cycling
driving
rail
bus
tram
ferry
flight
car sharing
ride hailing
scooter travel
```

But an agent cannot necessarily use every edge.

Therefore define:

\[
G_{\text{feasible},t}
\subseteq
G_{\text{world}}.
\]

The feasible graph is agent-conditioned.

---

## 3. An Edge Should Carry Constraints

A mobility edge should not merely say:

```text
A connects to B.
```

It should carry applicability conditions.

Write:

\[
e=
(
u,
v,
m,
C_e
),
\]

where:

\[
m
\]

is the mobility mode and:

\[
C_e
\]

is the constraint set.

For a road edge, constraints may include:

```text
vehicle class
maximum vehicle weight
maximum height
maximum width
directionality
speed restrictions
toll requirements
road closure state
seasonal availability
emission-zone requirements
permit requirements
border rules
```

For a ferry edge:

```text
schedule
vehicle acceptance
weight limits
reservation requirements
ticket availability
operating season
port compatibility
```

For rail:

```text
departure time
ticket validity
service disruption
bicycle carriage
reservation
class restrictions
```

The edge exists physically or institutionally.

Whether it is executable is a separate question.

---

## 4. Explicit Constraint State

Let:

\[
C_t
\]

be the active constraint state.

A simple formulation is:

\[
C_t
=
C(
S_t,
K_t,
R_t,
J_t,
E_t
),
\]

where:

\[
K_t
\]

is capability state,

\[
R_t
\]

is resource and access state,

\[
J_t
\]

is jurisdictional state,

and:

\[
E_t
\]

is environmental state.

Then:

\[
\boxed{
A_t^{\text{feasible}}
=
\{a\in A_t\mid C_t(a)=\text{true}\}
}
\]

The purpose of explicit constraint modeling is to make feasibility inspectable rather than burying it inside an opaque action generator.

---

## 5. Transition Feasibility Is Conjunctive

A proposed transition:

\[
S_t
\xrightarrow{a}
S_{t+1}
\]

may require several independent conditions.

For example:

\[
a=\text{drive rental car from A to B}.
\]

Its feasibility may require:

\[
\begin{aligned}
&\text{valid driving license}\\
\land\;&\text{rental membership}\\
\land\;&\text{eligible payment method}\\
\land\;&\text{vehicle available}\\
\land\;&\text{license accepted in jurisdiction}\\
\land\;&\text{road permits vehicle class}\\
\land\;&\text{fuel or battery sufficient}\\
\land\;&\text{rental policy allows trip}\\
\land\;&\text{destination permits return or parking}.
\end{aligned}
\]

Thus:

\[
\boxed{
\operatorname{Feasible}
(
S_t\xrightarrow{a}S_{t+1}
)
\iff
\bigwedge_i c_i(S_t,a,S_{t+1})
}
\]

This is stronger than assigning a route a poor score.

An infeasible transition should normally be excluded from ordinary route search.

---

## 6. Hard Constraints and Soft Costs Should Be Separated

Some properties determine feasibility.

Others determine desirability.

Examples of hard constraints:

```text
no valid license
road physically closed
vehicle too heavy for bridge
border entry prohibited
no ferry service
battery range insufficient with no charging path
```

Examples of soft costs:

```text
high toll
long travel time
uncomfortable transfer
parking difficulty
fuel expense
expected delay
```

Thus route planning should distinguish:

\[
\text{feasibility}
\]

from:

\[
\text{valuation}.
\]

A useful ordering is:

\[
\boxed{
\text{world model}
\rightarrow
\text{constraint filtering}
\rightarrow
\text{feasible graph}
\rightarrow
\text{search}
\rightarrow
\text{valuation}
}
\]

Search should not be expected to repair impossible world assumptions.

---

## 7. A Driver's License Is a Capability, Not a Vehicle

Let:

\[
k_{\text{drive}}
\]

represent the legal and practical capability to drive a relevant vehicle class.

Acquiring a driver's license may perform:

\[
K_t
\rightarrow
K_{t+1}.
\]

It does not necessarily provide a vehicle.

Thus:

\[
\text{can drive}
\neq
\text{has car access}.
\]

A useful mobility state should distinguish:

```text
skill
legal authorization
vehicle ownership
vehicle access
service membership
payment access
```

These variables combine.

---

## 8. A Rental Subscription Is an Access Capability

Suppose:

\[
k_{\text{drive}}=1
\]

but:

\[
r_{\text{vehicle-access}}=0.
\]

The agent can legally drive but cannot currently instantiate a driving transition.

Now add:

\[
r_{\text{rental-membership}}=1.
\]

If vehicles are available under acceptable conditions, an entire class of actions may become executable.

Thus:

\[
\text{license}
+
\text{rental access}
\]

can behave like a composite mobility capability.

---

## 9. Capability Composition Unlocks Action Families

A useful formulation is:

\[
K_t^{\text{effective}}
=
\operatorname{Compose}
(
K_t,
R_t,
J_t,
E_t
).
\]

For car mobility:

\[
\begin{aligned}
K_{\text{car-effective}}
=
&\text{license}\\
+&\text{vehicle access}\\
+&\text{payment compatibility}\\
+&\text{jurisdictional compatibility}\\
+&\text{route compatibility}.
\end{aligned}
\]

This can unlock:

\[
A_{\text{car}}
\subseteq
A_{t+1}^{\text{feasible}}.
\]

The strategic value may therefore lie in the composition, not in any single component viewed independently.

---

## 10. Effective Access Is More Important Than Ownership

Ownership is only one access mechanism.

A mobility planner may obtain effective access through:

```text
ownership
rental
subscription
borrowing
shared mobility
employer-provided vehicle
taxi
ride hailing
public transport
on-demand services
```

Thus:

\[
\boxed{
\text{ownership}
\neq
\text{mobility capability}
}
\]

The more general variable is:

\[
\operatorname{Access}(m,t),
\]

the effective ability to instantiate mobility mode \(m\) at time \(t\).

---

## 11. Search Happens Over the Feasible Projection

The world model may contain many transitions unavailable to the agent.

Define a projection:

\[
\Pi(
G_{\text{world}},
S_t,
K_t,
R_t,
J_t,
E_t
)
=
G_{\text{feasible},t}.
\]

Then ordinary route search operates on:

\[
G_{\text{feasible},t}.
\]

This makes clear that two agents at the same location may have different mobility graphs.

One may have:

```text
walking
rail
car
ferry
```

available.

Another may have only:

```text
walking
rail
```

The physical world is shared.

Operational reachability is not.

---

## 12. Reachability Is Agent-Relative

Let:

\[
\mathcal R_H(S_t,K_t,R_t)
\]

be the set of destinations or mobility states reachable within horizon \(H\).

Then:

\[
\mathcal R_H^{(1)}
\neq
\mathcal R_H^{(2)}
\]

for two agents who differ in:

```text
license
budget
vehicle access
visa
mobility skill
subscription
location
time availability
```

Thus geographical distance alone is not mobility distance.

A nearby destination may be operationally inaccessible.

A distant destination may be cheaply reachable by rail or flight.

---

## 13. Mobility Distance Is Constraint-Conditioned

Define:

\[
D(x\mid S_t,K_t,R_t,J_t,E_t)
\]

as the effective distance to destination \(x\).

This may include:

```text
travel time
monetary cost
transfer count
legal friction
schedule latency
booking latency
reliability
walking burden
charging burden
border friction
risk
```

A capability-changing action may produce:

\[
D_{t+1}(x_i)
<
D_t(x_i)
\]

for many destinations simultaneously.

This is why reusable mobility capabilities can have high option value.

---

## 14. A License Can Compress the Mobility Geometry

Suppose acquiring a driver's license unlocks access to rental cars.

The immediate action may have no destination value.

But afterward:

\[
D(x_i\mid K_{t+1})
<
D(x_i\mid K_t)
\]

for a broad family of \(x_i\).

The license therefore changes the geometry of future mobility.

This is a direct instance of capability-changing preparedness.

---

## 15. A Vehicle Purchase Is Not the Same Kind of Expansion

Buying a vehicle can change:

```text
availability
departure flexibility
range
cargo capacity
time independence
route choice
```

But it also introduces:

```text
purchase cost
insurance
maintenance
repair risk
parking dependency
fuel or charging dependency
depreciation
inspection obligations
```

Thus:

\[
\boxed{
\text{frontier expansion}
\neq
\text{constraint elimination}
}
\]

A new capability can remove some constraints while creating others.

---

## 16. Expansion Changes the Constraint System

A capability-changing action can be modeled as:

\[
C_t
\rightarrow
C_{t+1}.
\]

For example:

```text
before:
licensed_to_drive = false

after:
licensed_to_drive = true
```

This may cause a large family of edges to pass feasibility filtering.

Likewise:

```text
before:
rental_membership = false

after:
rental_membership = true
```

may activate vehicle-access transitions.

Thus endogenous frontier expansion can be interpreted as:

\[
\boxed{
\text{selective transformation of the constraints that generate the feasible graph}
}
\]

---

## 17. Physical Constraints Remain External

Not every constraint is agent-changeable.

A missing bridge remains missing.

A flooded road remains flooded.

A ferry schedule remains external unless the agent controls the ferry.

Thus it is useful to distinguish:

\[
C_t
=
C_t^{\text{agent}}
\cup
C_t^{\text{world}}.
\]

Agent-side constraints may include:

```text
license
budget
subscription
skill
vehicle ownership
visa
```

World-side constraints may include:

```text
roads
bridges
closures
ferry routes
rail infrastructure
weather
jurisdictional rules
service schedules
```

Capability expansion normally modifies only part of the total constraint state.

---

## 18. The Five-Ton Bridge Example

Suppose a bridge edge exists:

\[
A
\xrightarrow{\text{bridge}}
B.
\]

Its constraint set includes:

\[
\text{vehicle weight}\le5\text{ t}.
\]

For a 3-ton vehicle:

\[
c_{\text{weight}}=\text{true}.
\]

For a 7-ton vehicle:

\[
c_{\text{weight}}=\text{false}.
\]

The bridge remains part of:

\[
G_{\text{world}}.
\]

But it is excluded from the heavy vehicle's:

\[
G_{\text{feasible},t}.
\]

A route planner that ignores this distinction may produce a physically connected but operationally invalid route.

---

## 19. The Ferry Example

Suppose there is no bridge between two regions.

Then:

\[
A\xrightarrow{\text{road}}B
\]

may not exist at all.

But:

\[
A\xrightarrow{\text{ferry}}B
\]

may exist.

Its feasibility could depend on:

```text
vehicle class
weight
departure schedule
ticket availability
port opening time
reservation
weather
```

For a heavy vehicle, the ferry may be the only feasible transition.

Thus:

\[
\boxed{
\text{shortest geometric path}
\neq
\text{shortest feasible mobility path}
}
\]

---

## 20. Reality-Coupled Maps Are Constraint Databases

A navigation system is useful because it attempts to maintain a representation of real transition structure.

Its model may include:

```text
roads
turn restrictions
vehicle classes
weight limits
height limits
ferries
public transport
temporary closures
border rules
traffic
charging infrastructure
walking paths
cycling paths
```

The value of the map is not merely visual.

It is a continuously revised approximation of:

\[
G_{\text{world}}
\]

and its constraint metadata.

---

## 21. Map Accuracy Is Operational, Not Merely Descriptive

An inaccurate map can create false feasibility.

For example:

```text
bridge marked open when closed
road marked unrestricted when weight-limited
ferry omitted
charging station marked available when removed
pedestrian path represented as driveable
```

Thus representation quality affects reachable-state estimation.

Write:

\[
\hat G_{\text{world},t}
\]

for the represented world graph.

Then:

\[
\hat G_{\text{world},t}
\neq
G_{\text{world},t}
\]

creates planning error.

The planner therefore requires both:

```text
world-state updates
representation updates
```

---

## 22. Mobility Has Representational Expansion Too

Some changes require updating values inside known fields.

For example:

```text
road_status:
    open -> closed
```

This is a state update.

Other changes may require new distinctions.

For example:

```text
new vehicle category
new permit class
new low-emission rule
new shared-mobility mode
new charging constraint
new autonomous vehicle restriction
```

Then the representation may need:

\[
L_t
\rightarrow
L_{t+1}.
\]

This is representational expansion.

---

## 23. A New Mobility Mode Can Require New Rules

Suppose the current representation knows:

```text
walk
bike
car
bus
rail
```

A new mobility mode becomes relevant.

It may require new variables such as:

```text
where it may operate
maximum speed
parking rules
age requirements
license requirements
helmet requirements
sidewalk legality
road legality
charging rules
rental zone
geofencing
```

The open-world problem is not merely adding one more route option.

The system may need to expand the ontology required to represent the option correctly.

---

## 24. Open-World Mobility

Let:

\[
M_t
\]

be the currently represented set of mobility modes.

A future useful mode may satisfy:

\[
m\notin M_t.
\]

The planner cannot assign ordinary route value to \(m\) if \(m\) is not yet represented.

Thus mobility planning can contain both:

### Known-space uncertainty

```text
Which currently known mode is best?
```

and:

### State-space uncertainty

```text
Is an important mobility mode, rule, capability,
or transition type missing from the representation?
```

These are different problems.

---

## 25. New Rules Can Reveal Missing Variables

Suppose vehicle weight was previously irrelevant to local route planning.

Then a new restriction appears:

```text
vehicles over 5 tonnes prohibited
```

If the mobility schema has no vehicle-weight field, the planner cannot enforce the rule correctly.

Thus:

\[
\boxed{
\text{new world constraint}
\rightarrow
\text{possible representational expansion}
}
\]

A constraint system is only as good as the distinctions available to express constraints.

---

## 26. Exploitation, Exploration, and Expansion

Mobility actions divide naturally into three classes.

### Exploitation

Use current mobility capabilities.

Examples:

```text
take the usual train
drive the available car
walk
cycle
use the current transit pass
```

### Exploration

Search or gather information within the current capability space.

Examples:

```text
compare routes
check delays
compare bus and train
inspect parking
check rental availability
test commute times
```

### Expansion

Change the future mobility capability or access space.

Examples:

```text
get a driver's license
buy a bicycle
buy a car
join a car-sharing service
obtain a transit subscription
get a visa
move closer to a station
install a charger
learn to ride a motorcycle
```

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

---

## 27. Expansion Can Be More Valuable Than a Better Route

Suppose the current commute problem is expensive.

One option is:

```text
find a slightly better train connection
```

Another is:

```text
obtain a capability that unlocks many alternative commutes
```

The first improves:

\[
\text{one path}.
\]

The second may improve:

\[
\text{a family of future paths}.
\]

Thus:

\[
\boxed{
\text{route optimization}
\neq
\text{mobility-system optimization}
}
\]

---

## 28. Mobility Capabilities Have Option Value

Let:

\[
a_e
\]

be a mobility-enabling action.

Its immediate reward may be small:

\[
R_{\text{now}}(a_e)\approx0.
\]

But suppose:

\[
A_{t+1}^{\text{feasible}}
=
A_t^{\text{feasible}}
\cup
\Delta A.
\]

Then:

\[
V_{\text{option}}(a_e)
=
V(
A_{t+1}^{\text{feasible}}
)
-
V(
A_t^{\text{feasible}}
).
\]

Examples include:

```text
driver's license
annual rail pass
rental membership
bicycle ownership
passport
visa
charger installation
```

Their value should not be judged only by the first trip after acquisition.

---

## 29. Mobility Expansion Has Maintenance Debt

A capability can require continuing support.

Examples:

### Car

```text
insurance
maintenance
parking
fuel
charging
repairs
inspection
registration
```

### Bicycle

```text
storage
maintenance
weather equipment
theft protection
```

### Public-transport subscription

```text
subscription cost
regional coverage limits
renewal
```

### Driver's license

```text
renewal
jurisdictional recognition
medical requirements in some contexts
```

Thus:

\[
\operatorname{Value}(a)
=
V_{\text{current}}
+
V_{\text{reachability}}
-
C_{\text{acquire}}
-
C_{\text{maintain}}
-
R.
\]

---

## 30. Reachability Quality Matters More Than Reachability Count

A car may make thousands of places theoretically reachable.

That does not mean all of those options are valuable.

New reachability can include:

```text
high-cost routes
dangerous routes
parking-constrained destinations
traffic-heavy routes
maintenance exposure
legal complexity
```

Therefore:

\[
|\mathcal R_{t+1}|
>
|\mathcal R_t|
\]

does not imply:

\[
V(\mathcal R_{t+1})
>
V(\mathcal R_t).
\]

Useful mobility expansion should be value-weighted.

---

## 31. Reliability Pressure Can Trigger Structural Search

Suppose a train commute repeatedly fails because of:

```text
delays
cancellations
missed connections
crowding
schedule instability
```

The first response need not be:

```text
buy a car
```

Instead repeated failures can create:

\[
P_{\text{mobility}}.
\]

When pressure rises, the controller may investigate:

```text
different departure times
different rail routes
bus alternatives
cycling
car sharing
private car
remote work
job-location change
residential relocation
```

The structural question is:

```text
Is the current mobility architecture still adequate?
```

---

## 32. Mobility Expansion Should Use Hysteresis

The system should not redesign mobility after one late train.

Nor should it wait until the current arrangement becomes intolerable.

Define:

\[
\theta_{\text{explore}}
\]

for beginning structural investigation and:

\[
\theta_{\text{commit}}
\]

for adopting a substantial mobility change.

Then:

```text
observe repeated failure
↓
investigate alternatives
↓
simulate or test
↓
compare total costs
↓
commit only when evidence is strong enough
```

This reduces oscillation between mobility strategies.

---

## 33. Trial Access Is Speculative Mobility Expansion

Many mobility capabilities can be tested before full commitment.

Examples:

```text
rent a car before buying one
use car sharing for a month
trial a transit subscription
borrow an e-bike
test a commute at actual rush hour
use a temporary parking arrangement
```

This creates a speculative state:

\[
S_{t+1}^{S}.
\]

If evidence is favorable:

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

This reduces the risk of irreversible mobility commitments.

---

## 34. Relocation Is a Graph-Rewriting Action

Moving home does more than change one route.

It changes the starting node for many future journeys.

Thus:

\[
S_t^{\text{location}}
\rightarrow
S_{t+1}^{\text{location}}
\]

can alter:

```text
commute distance
station access
airport access
cycling feasibility
car dependence
parking pressure
regional ticket compatibility
cross-border friction
```

Relocation is therefore a high-impact frontier-changing action.

---

## 35. Job Location Is Also Part of the Mobility System

A commute problem can be attacked from either side.

One may change:

```text
vehicle
route
departure time
home location
work location
remote-work frequency
```

Thus mobility optimization should not assume destinations are fixed.

A job change or workplace-location change may produce greater long-run mobility value than optimizing transportation technology.

This generalizes the control problem from:

```text
How do I move from A to B?
```

to:

```text
Which parts of the recurring mobility system should remain fixed?
```

---

## 36. The Agent Can Change Nodes, Edges, or Eligibility

Different mobility actions alter different parts of the system.

### Change node

```text
move home
move workplace
change parking location
```

### Change edge availability

```text
obtain ferry ticket
gain rental access
join car sharing
```

### Change eligibility

```text
get license
get visa
obtain permit
```

### Change edge cost

```text
buy transit subscription
install home charger
move near station
```

### Change representation

```text
add new vehicle class
add new restriction type
add new mode
```

This provides a more precise vocabulary for frontier expansion.

---

## 37. Constraint Removal and Constraint Satisfaction Are Different

Some actions remove a constraint from the system.

Others merely satisfy it.

For example:

```text
license requirement exists
```

The agent normally does not remove the legal requirement.

Instead the agent obtains:

```text
valid license
```

so the requirement becomes satisfied.

Thus:

\[
\boxed{
\text{constraint transformation}
\neq
\text{constraint deletion}
}
\]

This matters when reasoning about agency.

The world may remain unchanged while the agent becomes compatible with it.

---

## 38. Compatibility Is a Central Mobility Variable

A capability has value only when it couples to the environment.

A driver's license valid only in one jurisdiction may not unlock driving elsewhere.

A charging connector incompatible with available chargers limits an EV.

A transit pass may cover one region but not another.

A rental membership may have no vehicles nearby.

Thus:

\[
\text{nominal capability}
\neq
\text{effective capability}.
\]

A useful approximation is:

\[
V_{\text{effective}}
=
f(
\text{capability},
\text{access},
\text{compatibility},
\text{availability},
\text{latency}
).
\]

---

## 39. Mobility Is a Constraint-Satisfaction Problem Before It Is an Optimization Problem

A route system should first answer:

```text
What is possible?
```

Then:

```text
What is preferable?
```

This suggests:

\[
\boxed{
\text{constraint satisfaction}
\rightarrow
\text{search}
\rightarrow
\text{optimization}
}
\]

rather than:

\[
\text{generate arbitrary possibilities}
\rightarrow
\text{score them}
\]

The first architecture can exclude nonsense earlier.

---

## 40. But Constraints Can Themselves Become Search Targets

Ordinary routing searches over currently feasible actions.

Endogenous mobility management also searches over:

```text
which constraint can be satisfied?
which capability can be acquired?
which access mechanism can be added?
which location can be changed?
which dependency can be removed?
```

Thus the higher-level search space contains actions that modify the lower-level feasible graph.

Formally:

\[
\boxed{
\text{search over routes}
\subset
\text{search over mobility architectures}
}
\]

---

## 41. Two-Level Search

A useful architecture has two coupled planners.

### Level 1: route planner

Given:

\[
G_{\text{feasible},t},
\]

find a good path for current demand.

### Level 2: frontier planner

Given repeated demand, failures, cost, and predicted future needs, consider actions that modify:

\[
G_{\text{feasible},t+1}.
\]

Examples:

```text
get license
buy vehicle
join rental service
move house
change job location
obtain visa
install charger
```

The lower layer moves through the graph.

The higher layer selectively changes which graph the lower layer will receive later.

---

## 42. Search Can Be Directed by Blocking Constraints

Suppose no feasible route satisfies a demand.

Instead of searching randomly for new capabilities, inspect the failed constraints.

For example:

```text
destination unreachable by transit
car route exists
blocked by no license
blocked by no vehicle
```

This exposes a minimal capability gap.

The controller can then ask:

```text
Which blocking constraint is cheapest or most valuable to satisfy?
```

This can make frontier expansion computationally tractable.

---

## 43. Constraint Provenance Matters

A useful system should know why an action is infeasible.

For example:

```text
edge: bridge_A_B
status: infeasible
reason:
    vehicle_weight = 7.0 t
    maximum_allowed = 5.0 t
source:
    jurisdiction rule
valid_from:
    ...
```

Without provenance, infeasibility becomes opaque.

With provenance, the system can distinguish:

```text
temporary closure
permanent infrastructure limit
agent capability gap
unknown data
legal restriction
representation failure
```

Each suggests a different response.

---

## 44. Unknown Constraint State Should Not Be Treated as False or True

Reality models are incomplete.

Suppose the planner does not know whether a road permits a particular vehicle class.

Then:

\[
c_i=\text{unknown}
\]

should remain distinct from:

\[
c_i=\text{true}
\]

and:

\[
c_i=\text{false}.
\]

Thus constraints may be three-valued:

\[
c_i\in
\{
\text{true},
\text{false},
\text{unknown}
\}.
\]

Unknown constraints create exploration pressure.

---

## 45. Exploration Can Target Constraint Resolution

If a promising route is blocked by:

```text
unknown ferry vehicle limit
```

the next valuable action may be:

```text
check ferry operator rules
```

not:

```text
buy a different vehicle
```

Thus exploration reduces uncertainty about the current graph.

Expansion changes the graph or agent compatibility.

This preserves the distinction:

\[
\text{explore}
\neq
\text{expand}.
\]

---

## 46. Dynamic World State Requires Continuous Reprojection

Mobility constraints change over time.

Examples:

```text
road closures
construction
new traffic rules
rail disruptions
weather
ferry cancellation
charging outages
new low-emission zones
new border rules
new shared-mobility services
```

Therefore:

\[
G_{\text{feasible},t}
\]

must be recomputed when either:

```text
the world changes
```

or:

```text
the agent changes.
```

The same agent can have different feasible graphs at different times without acquiring any new capability.

---

## 47. A Reality-Coupled Planner Must Separate Three Update Types

### World update

```text
bridge closed
train canceled
new ferry line
```

### Agent update

```text
license acquired
budget changed
vehicle purchased
subscription activated
```

### Representation update

```text
new vehicle class added
new rule type added
new mode introduced
```

These correspond roughly to changes in:

\[
S_t,
K_t,R_t,
L_t.
\]

Conflating them makes diagnosis harder.

---

## 48. Mobility Frontier Pressure

Define:

\[
P_{\text{frontier}}
\]

as pressure indicating that current mobility capabilities or representations are no longer sufficient.

Signals may include:

```text
repeated infeasible trips
repeated expensive workarounds
persistent delays
large time loss
high taxi expenditure
frequent rental need
unreachable valuable destinations
new regulation repeatedly causing failure
new mode repeatedly appearing outside the schema
```

This pressure can trigger either:

```text
exploration
```

or:

```text
expansion.
```

---

## 49. A Mobility Capability Prefetch Principle

\[
\boxed{
\textbf{Mobility Capability Prefetch Principle}
}
\]

> When a future class of valuable journeys is sufficiently probable, expensive or impossible to satisfy reactively, and enabled by a reusable mobility capability that can be acquired at acceptable current cost, begin acquiring that capability before the first critical blocking demand.

Examples:

```text
obtain a driver's license before a job requires regular remote-site travel
obtain a passport before likely international travel
learn to cycle before moving to a cycle-oriented city
join a rental service before recurring car access becomes urgent
```

---

## 50. A Feasible-Graph Principle

\[
\boxed{
\textbf{Feasible-Graph Principle}
}
\]

> Route search should operate over transitions that satisfy the currently known physical, legal, capability, access, resource, and temporal constraints of the agent and environment.

This prevents optimization from treating impossible transitions as merely expensive ones.

---

## 51. A Capability-Composition Principle

\[
\boxed{
\textbf{Capability-Composition Principle}
}
\]

> Effective mobility capability often arises from combinations of skills, permissions, access mechanisms, resources, and environmental compatibility rather than from any single possessed asset.

Thus:

\[
\text{license}
+
\text{rental access}
+
\text{available vehicle}
+
\text{legal compatibility}
\]

can unlock a mobility mode without ownership.

---

## 52. A Constraint-Transformation Principle

\[
\boxed{
\textbf{Constraint-Transformation Principle}
}
\]

> Capability-changing actions should be modeled partly by how they alter which constraints are satisfied, which constraints are relevant, and which transitions therefore enter or leave the feasible graph.

This provides an explicit computational interpretation of frontier expansion.

---

## 53. A Reality-Coupling Principle

\[
\boxed{
\textbf{Reality-Coupling Principle}
}
\]

> A mobility representation should be continuously revised so that represented transitions and constraints remain sufficiently aligned with physical infrastructure, operating services, legal rules, and observed environmental state.

A route planner is useful only insofar as its represented world remains operationally connected to reality.

---

## 54. An Open-World Mobility Principle

\[
\boxed{
\textbf{Open-World Mobility Principle}
}
\]

> The system should treat its current set of mobility modes, vehicle classes, constraint types, and transition rules as operationally usable but not structurally complete.

New mobility technologies, regulations, infrastructure, and service models may require both new values and new variables.

---

## 55. A Mobility Hysteresis Principle

\[
\boxed{
\textbf{Mobility Hysteresis Principle}
}
\]

> Repeated mobility failure should trigger structural investigation before it triggers irreversible commitment, with stronger evidence required for acquisition, relocation, or other high-cost frontier-changing actions.

This separates:

```text
notice
investigate
test
validate
commit
```

---

## 56. A Mobility Architecture Objective

Let:

\[
a
\]

be either a normal mobility action or a frontier-changing mobility action.

A schematic objective is:

\[
a_t^\*
=
\arg\max_{a\in A_t^{\text{candidate}}}
\left[
V_{\text{current}}(a)
+
V_{\text{future-reachability}}(a)
+
V_{\text{reliability}}(a)
-
C_{\text{acquire}}(a)
-
C_{\text{operate}}(a)
-
C_{\text{maintain}}(a)
-
R(a)
\right]
\]

subject to:

\[
\operatorname{Feasible}(a)
\]

for actions executed now.

Capability-changing actions may be valuable because they alter the feasible set used in later optimization.

---

## 57. A Compact Formal Model

Let:

\[
W_t
\]

be world state.

Let:

\[
L_t
\]

be the represented mobility world.

Let:

\[
S_t
\]

be agent operational state.

Let:

\[
K_t
\]

be capability state.

Let:

\[
R_t
\]

be access and resource state.

Let:

\[
J_t
\]

be jurisdictional state.

Let:

\[
C_t
=
C(W_t,L_t,S_t,K_t,R_t,J_t)
\]

be the constraint state.

Let:

\[
G_{\text{world},t}
=
G(W_t,L_t)
\]

be the represented world transition graph.

Then:

\[
\boxed{
G_{\text{feasible},t}
=
\Pi(
G_{\text{world},t},
C_t
)
}
\]

Ordinary mobility action chooses a path through:

\[
G_{\text{feasible},t}.
\]

A frontier-changing action modifies one or more of:

\[
(S_t,K_t,R_t,J_t,L_t)
\]

so that:

\[
G_{\text{feasible},t+1}
\neq
G_{\text{feasible},t}.
\]

This is endogenous mobility frontier expansion.

---

## 58. A Complete Control Loop

```text
CURRENT MOBILITY STATE
↓
where does the agent need to go?
↓
construct current constraint state
↓
project world graph into feasible graph
↓
is a satisfactory route available?
├── yes
│   ↓
│   search / compare / execute
│   ↓
│   observe cost, delay, reliability, failure
│
└── no
    ↓
    inspect blocking constraints
    ↓
    are constraints uncertain?
    ├── yes → explore / retrieve / verify
    └── no
        ↓
        is a reusable capability or access change available?
        ├── no → revise destination, timing, or external assumptions
        └── yes
            ↓
            estimate acquisition cost
            estimate future reachability gain
            estimate maintenance burden
            estimate compatibility
            ↓
            test provisionally where possible
            ↓
            acquire / subscribe / learn / relocate / migrate
            ↓
            recompute feasible graph

IN PARALLEL:
↓
observe repeated route failures
↓
observe new mobility modes and regulations
↓
detect missing variables or constraint types
↓
expand representation where justified
↓
preserve provenance and compatibility
↓
recompute future mobility frontier
```

---

## 59. Why Mobility Is a Useful Test Domain

Mobility is unusually useful for this framework because reality supplies hard counterexamples.

A planner cannot:

```text
drive across water because the path is geometrically short
use a bridge that does not exist
send a 7-ton vehicle across a 5-ton bridge
drive legally without required authorization
take a ferry that is not operating
use a vehicle whose range cannot reach the next charging point
```

These failures are not matters of preference.

They are failures of feasibility.

Thus mobility makes a general principle visible:

\[
\boxed{
\text{search is downstream of reality and constraint satisfaction}
}
\]

---

## 60. The Deeper Mobility Realism

A mobility system should treat the current world as real.

It should treat the current agent state as real.

It should treat legal, physical, and resource constraints as real.

But it should not treat the current feasible graph as final.

The useful posture is:

```text
represent the world as accurately as practical
make constraints explicit
search only currently feasible transitions
observe repeated blocking conditions
distinguish uncertainty from impossibility
acquire reusable capabilities when justified
test expensive expansions provisionally
recompute the feasible graph after change
expand the representation when the world introduces new distinctions
```

Thus:

\[
\boxed{
\text{current feasibility is binding}
}
\]

and simultaneously:

\[
\boxed{
\text{future feasibility can sometimes be changed}
}
\]

---

## 61. Conclusion

Mobility planning is not merely shortest-path search.

A bounded agent exists inside a physical, legal, economic, and technological environment.

The world supplies a transition structure.

The representation approximates that structure.

The agent's current state determines which transitions are usable.

Explicit constraints project:

\[
G_{\text{world}}
\]

into:

\[
G_{\text{feasible},t}.
\]

Ordinary mobility reasoning then asks:

```text
Which feasible route should be used now?
```

Exploration asks:

```text
Which uncertain route, cost, rule, or service state should be investigated?
```

Endogenous mobility frontier management adds:

```text
Which present action should be taken
because it will change which transitions,
destinations, or mobility modes become feasible later?
```

A driver's license can expand legal capability.

A rental subscription can expand vehicle access.

Their composition can unlock a broad class of car transitions without ownership.

A vehicle can expand route flexibility while adding maintenance constraints.

A relocation can rewrite the starting node for thousands of future journeys.

A new mobility technology or regulation can require representational expansion before it can be reasoned about correctly.

A map or navigation system therefore does more than store routes.

It attempts to remain coupled to reality by representing:

```text
real roads
real services
real vehicle classes
real restrictions
real schedules
real jurisdictions
real infrastructure
```

while remaining capable of adding new distinctions when reality changes.

The resulting architecture is:

\[
\boxed{
\text{world}
+
\text{world representation}
+
\text{agent state}
+
\text{explicit constraints}
\rightarrow
\text{feasible graph}
\rightarrow
\text{search}
}
\]

with the endogenous extension:

\[
\boxed{
\text{actions now}
\rightarrow
\text{change capability, access, location, or representation}
\rightarrow
\text{different feasible graph later}
}
\]

The system is therefore not merely choosing routes through a mobility network.

It is sometimes choosing which future mobility network will become operationally available to it.
