# Endogenous Feasible-Action Frontiers: Reality, Representation, Constraint Diagnosis, and Capability Acquisition

## Abstract

A bounded agent does not choose actions from everything that can be imagined.

It acts from:

```text
a real current state
inside a real external world
through an incomplete representation of that world
with finite capabilities
finite access
finite resources
finite time
and uncertain knowledge
```

This creates several distinct objects that should not be conflated.

There is:

\[
G_t^\*
\]

the transition structure that actually exists in the world,

\[
\hat G_t
\]

the transition structure represented by the agent,

and:

\[
G_{t}^{F}
\]

the represented subset of transitions currently judged executable by that agent.

Ordinary planning searches through:

\[
G_t^F.
\]

But a sufficiently capable bounded agent may also take actions that alter the future graph on which ordinary planning will operate.

It may:

```text
acquire a skill
obtain authorization
gain access to a resource
buy or rent equipment
change location
remove a dependency
increase compatibility
resolve an unknown constraint
improve its world representation
```

so that:

\[
G_{t+1}^{F}
\neq
G_t^{F}.
\]

This is endogenous feasible-action frontier change.

The central claim of this framework is:

\[
\boxed{
\text{an agent should sometimes plan not only over feasible actions,}
}
\]

but also:

\[
\boxed{
\text{over interventions that change its future feasible-action set.}
}
\]

The framework separates reality from representation, feasibility from desirability, epistemic uncertainty from stochastic availability, ordinary action from architectural intervention, and reachability count from demand-weighted option value.

A key computational mechanism is blocking-constraint diagnosis.

When a desired plan fails, the system need not search arbitrarily over all possible self-improvements.

Instead it can identify the constraints responsible for failure, generate interventions targeted at those constraints, simulate the resulting counterfactual feasible graphs, and acquire new capabilities only when their expected future value justifies their cost and maintenance burden.

Mobility provides an intuitive test domain, but the architecture applies more generally to bounded agents operating under physical, legal, technological, organizational, informational, or resource constraints.

---

## 1. The Core Distinction: Reality, Representation, and Feasibility

A planning system should distinguish at least three layers.

### 1.1 The actual world

Let:

\[
W_t^\*
\]

be the actual external world state at time \(t\).

This includes whatever facts determine which transitions really exist and under what conditions.

In mobility, this may include:

```text
roads
bridges
rail lines
operating ferries
weather
closures
vehicle restrictions
jurisdictional rules
service schedules
charging infrastructure
```

The agent does not possess \(W_t^\*\) directly.

It exists independently of the agent's beliefs.

---

### 1.2 The represented world

Let:

\[
L_t
\]

be the agent's current representation of the world.

From it the agent constructs:

\[
\hat G_t
=
G(L_t),
\]

the transition graph it currently believes or represents as available in the world.

Thus:

\[
\hat G_t
\neq
G_t^\*
\]

is possible.

Indeed, for a bounded system it is normal.

The representation may be:

```text
incomplete
stale
coarse
incorrect
missing a mode
missing a rule
missing a variable
uncertain about availability
```

The planner therefore acts on a model of reality, not reality itself.

---

### 1.3 The represented feasible graph

Let the agent's operational architecture state be:

\[
X_t
=
(S_t,K_t,R_t,J_t),
\]

where:

\[
S_t
\]

is current operational state,

\[
K_t
\]

is capability state,

\[
R_t
\]

is resource and access state,

and:

\[
J_t
\]

is compatibility, authorization, or jurisdictional state.

Then define the represented feasible graph:

\[
\boxed{
G_t^F
=
\Pi(
\hat G_t,
X_t,
C_t
)
}
\]

where:

\[
C_t
\]

is the currently represented constraint state.

The projection operator \(\Pi\) retains transitions judged executable under the agent's current state.

Thus:

\[
G_t^F
\subseteq
\hat G_t.
\]

---

## 2. The Agent Never Plans Directly on Reality

This distinction is operationally important.

An agent may believe:

```text
a bridge is open
a ferry accepts a vehicle class
a service operates tonight
a permit is valid
a charging station exists
```

while reality differs.

Thus it is useful to distinguish:

\[
G_t^{F,\*}
\]

the set of transitions actually executable in the real world,

from:

\[
G_t^F
\]

the set of transitions the agent currently judges executable.

Then planning error can arise from:

\[
G_t^F
\neq
G_t^{F,\*}.
\]

There are two broad failure directions.

### False feasibility

The agent includes a transition that is not actually executable.

For example:

```text
road believed open but closed
license believed valid but expired
vehicle believed compatible but rejected
resource believed available but depleted
```

### False infeasibility

The agent excludes a transition that is actually usable.

For example:

```text
unknown ferry route
unrepresented mobility service
outdated permit rule
unrecognized compatible payment mechanism
unmodeled capability combination
```

The first produces failed execution.

The second produces unnecessarily narrow behavior.

---

## 3. Search Is Downstream of Representation

Ordinary search algorithms can only operate over what is represented.

They cannot select:

\[
e\notin \hat G_t
\]

through ordinary graph search.

This creates an important distinction.

### Known-space uncertainty

The agent knows several alternatives but does not know which is best.

For example:

```text
train or bus?
route A or route B?
leave now or later?
rent or ride-share?
```

This is ordinary search and uncertainty within the represented space.

### State-space uncertainty

The agent may be missing:

```text
a transition
a mode
a capability
a constraint type
a compatibility relation
a useful intervention
```

This is not ordinary route uncertainty.

It is uncertainty about the structure of the planning space itself.

Thus:

\[
\boxed{
\text{uncertainty over values}
\neq
\text{uncertainty over represented possibilities}
}
\]

---

## 4. Feasibility and Desirability Must Be Separate

A transition may be undesirable yet feasible.

A different transition may be attractive but impossible.

These cases should not be represented merely as different scalar scores.

Let:

\[
\operatorname{Feasible}(a\mid X_t,C_t)
\]

be a feasibility predicate.

Then ordinary choice should be restricted to:

\[
A_t^F
=
\{
a\in A_t
\mid
\operatorname{Feasible}(a\mid X_t,C_t)
\}.
\]

Only after this projection should the planner compare values such as:

```text
time
money
comfort
risk
energy
reliability
latency
maintenance burden
```

A useful ordering is:

\[
\boxed{
\text{representation}
\rightarrow
\text{constraint evaluation}
\rightarrow
\text{feasible action space}
\rightarrow
\text{search}
\rightarrow
\text{valuation}
}
\]

This prevents optimization from being asked to repair impossible assumptions.

---

## 5. Constraint Predicates

A transition should carry conditions.

Write:

\[
e
=
(u,v,m,C_e),
\]

where:

\[
u
\]

and:

\[
v
\]

are states or locations,

\[
m
\]

is the transition mode,

and:

\[
C_e
=
\{c_1,\ldots,c_n\}
\]

is a set of applicability conditions.

A transition is feasible only if all required predicates are satisfied:

\[
\boxed{
\operatorname{Feasible}(e)
\iff
\bigwedge_{i=1}^{n} c_i
}
\]

for deterministic known constraints.

Examples include:

```text
authorized = true
resource available = true
vehicle weight <= limit
funds >= price
service operating = true
battery >= required energy
skill level >= required threshold
jurisdiction compatible = true
reservation exists = true
```

The point is not that every system should literally use Boolean predicates.

The point is that feasibility should be inspectable.

The system should know why a transition enters or leaves the feasible set.

---

## 6. Constraint Provenance

A useful constraint representation should preserve provenance.

For example:

```text
transition: bridge_A_B
constraint: vehicle_weight <= 5 t
observed_vehicle_weight: 7 t
status: violated
source: jurisdiction rule database
valid_from: ...
last_verified: ...
confidence: ...
```

This allows the planner to distinguish:

```text
permanent limitation
temporary limitation
agent capability gap
resource shortage
legal incompatibility
unknown data
representation defect
stochastic availability
```

These categories should trigger different responses.

Without provenance:

\[
\text{infeasible}
\]

is merely a dead end.

With provenance:

\[
\text{infeasible}
\rightarrow
\text{diagnosable cause}.
\]

---

## 7. Unknown Is Not False

A bounded agent often does not know whether a constraint holds.

Therefore:

\[
c_i
\in
\{
\text{true},
\text{false},
\text{unknown}
\}.
\]

The distinction matters.

Suppose:

```text
ferry accepts vehicle = unknown
```

The planner should not automatically convert this to:

```text
ferry accepts vehicle = false
```

nor:

```text
ferry accepts vehicle = true.
```

Instead the unknown constraint may create an information-gathering action:

```text
check ferry operator rules
```

Thus:

\[
\boxed{
\text{unknown feasibility}
\rightarrow
\text{possible exploration target}
}
\]

---

## 8. Epistemic Uncertainty and Stochastic Availability Are Different

Three-valued constraints are not sufficient for every uncertain situation.

Consider two cases.

### Epistemic uncertainty

The world has a definite rule, but the agent does not know it.

For example:

```text
Does the ferry accept motorcycles?
```

There is a factual answer.

The uncertainty is in the agent's information.

Let:

\[
P(c_i=\text{true}\mid I_t)
\]

represent belief about an unknown constraint given information \(I_t\).

An information-gathering action may reduce this uncertainty.

---

### Stochastic availability

The transition itself may be uncertain.

For example:

```text
the ferry operates with 0.85 probability under tomorrow's weather
```

or:

```text
a ride-hailing vehicle will be available with probability 0.7
```

Here the world does not contain a fixed currently unknown truth of the same kind.

Availability is genuinely stochastic.

Represent this as:

\[
P(e\text{ available at execution time}\mid I_t).
\]

Thus:

\[
\boxed{
\text{unknown truth}
\neq
\text{random future availability}
}
\]

The first can sometimes be resolved by information.

The second normally requires risk-sensitive planning.

---

## 9. Capabilities Are Not Assets

A capability should not be identified with ownership.

For mobility:

\[
\text{can drive}
\neq
\text{owns a car}.
\]

A planner should distinguish:

```text
skill
authorization
ownership
temporary access
service membership
payment capability
physical capacity
compatibility
availability
```

The relevant variable is often not:

\[
\operatorname{Owns}(x)
\]

but:

\[
\operatorname{EffectiveAccess}(m,t).
\]

A mobility mode may be instantiated through:

```text
ownership
rental
borrowing
subscription
shared access
employer provision
on-demand service
public infrastructure
```

This generalizes beyond mobility.

A bounded agent may be able to use a capability without owning the underlying resource.

---

## 10. Capability Composition

Many useful abilities are conjunctive.

Suppose:

\[
k_{\text{drive}}=1
\]

but:

\[
r_{\text{vehicle}}=0.
\]

The agent is authorized and skilled to drive but cannot instantiate a driving transition.

Suppose it then obtains:

\[
r_{\text{rental-access}}=1.
\]

If payment, local availability, vehicle compatibility, and jurisdictional validity also hold, a broad action family becomes feasible.

Thus effective capability is better represented as:

\[
\boxed{
K_t^{\text{eff}}
=
\operatorname{Compose}
(
K_t,
R_t,
J_t,
C_t
)
}
\]

rather than as a flat list of independently possessed abilities.

For a mode \(m\):

\[
K^{\text{eff}}(m)
=
f(
\text{skill},
\text{authorization},
\text{access},
\text{resources},
\text{compatibility},
\text{availability}
).
\]

This yields:

\[
\boxed{
\text{nominal capability}
\neq
\text{effective capability}
}
\]

---

## 11. Compatibility Is a First-Class Variable

A capability matters only when it couples correctly to the environment.

Examples:

```text
license valid in one jurisdiction but not another
charger connector incompatible with available infrastructure
software skill incompatible with required platform
transit pass valid in one zone but not another
payment account unsupported by a service
tool available but unusable with current interface
```

Therefore:

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

This is important because frontier expansion is often not about creating a new capability from zero.

It may instead involve making an existing capability compatible with the environment.

---

## 12. From Action Space to Architecture State

Ordinary planning assumes a fixed architecture and chooses an action.

Endogenous frontier reasoning permits actions that alter the architecture itself.

Let:

\[
X_t
=
(S_t,K_t,R_t,J_t,L_t)
\]

be the architecture state.

Here:

\[
S_t
\]

contains current operational facts,

\[
K_t
\]

contains skills and capabilities,

\[
R_t
\]

contains resources and access,

\[
J_t
\]

contains authorization and compatibility,

and:

\[
L_t
\]

contains the representation used to construct the planning space.

An ordinary action approximately takes the form:

\[
a:
S_t
\rightarrow
S_{t+1}
\]

while leaving most architectural variables fixed.

An architecture-changing action takes the more general form:

\[
\boxed{
a^E:
X_t
\rightarrow
X_{t+1}
}
\]

and therefore may induce:

\[
G_t^F
\rightarrow
G_{t+1}^F.
\]

---

## 13. Endogenous Feasible-Action Frontier Change

Define the feasible-action frontier at time \(t\) as the operational boundary induced by:

\[
G_t^F.
\]

A frontier-changing action is any action whose important value arises partly because it changes the structure, cost, reliability, or representation of future feasible action.

Thus:

\[
\boxed{
\text{frontier-changing action}
=
\text{action that changes future planning possibility}
}
\]

The change need not be a simple expansion in edge count.

That distinction is important.

---

## 14. Five Kinds of Frontier Transformation

The term expansion can hide several different mechanisms.

A more precise taxonomy distinguishes at least five.

### 14.1 Edge expansion

Previously infeasible transitions become feasible.

\[
E_{t+1}^F
\supset
E_t^F.
\]

Examples:

```text
obtain license
gain vehicle access
obtain visa
join service
acquire required tool
```

---

### 14.2 Cost compression

The same transitions remain feasible, but their effective cost falls.

\[
c_{t+1}(e)
<
c_t(e).
\]

Examples:

```text
buy transit subscription
install home charger
move closer to station
automate a recurring setup step
```

---

### 14.3 Node relocation

The agent changes where recurring planning begins.

\[
s_{t+1}
\neq
s_t.
\]

Examples:

```text
move home
move workplace
change warehouse
change server region
move inventory closer to demand
```

This can rewrite the geometry of thousands of later plans.

---

### 14.4 Eligibility or compatibility change

The external requirement remains, but the agent becomes compatible with it.

For example:

```text
license requirement remains
agent becomes licensed
```

Thus:

\[
\boxed{
\text{constraint satisfaction}
\neq
\text{constraint deletion}
}
\]

---

### 14.5 Representational refinement

The underlying world may remain unchanged, but the planning representation improves.

\[
L_t
\rightarrow
L_{t+1}.
\]

This can:

```text
add a missing transition
add a missing mode
add a new constraint variable
correct stale availability
split an overly coarse category
introduce a new compatibility relation
```

This is not physical expansion.

It is expansion or correction of what the agent can reason about.

---

## 15. Exploration and Expansion Must Remain Distinct

Suppose a route is blocked because ferry rules are unknown.

One possible action is:

```text
check ferry rules
```

This does not necessarily alter the world or agent capability.

It alters information.

This is exploration.

Suppose instead the route is blocked because a required permit is definitely absent.

The action:

```text
obtain permit
```

changes the agent's compatibility with the world.

This is expansion.

Thus:

\[
\boxed{
\text{exploration}
\neq
\text{frontier intervention}
}
\]

A useful action taxonomy is:

\[
A_t
=
A_{\text{exploit}}
\cup
A_{\text{explore}}
\cup
A_{\text{expand}}
\cup
A_{\text{represent}}
\]

where:

```text
exploit    = use current feasible actions
explore    = reduce uncertainty
expand     = change capability, access, eligibility, resource, or location
represent  = change the ontology or model used for planning
```

These classes may overlap in practice, but their primary effects differ.

---

## 16. Planning Failure Should Produce Explanation

Suppose the agent has a demand:

\[
d.
\]

Ordinary planning attempts to find:

\[
p\in G_t^F
\]

such that:

\[
p\models d.
\]

If no satisfactory plan exists, the system should not stop at:

```text
no route found
```

It should compute:

```text
which candidate plans nearly worked?
which predicates blocked them?
which constraints recur across alternatives?
which blockers are agent-changeable?
which blockers are uncertain?
which blockers are external and immutable?
```

Failure should therefore produce a structured diagnosis.

---

## 17. Blocking-Constraint Sets

Let a candidate plan \(p\) require constraint set:

\[
C(p)
=
\{c_1,\ldots,c_n\}.
\]

Define the violated set:

\[
B(p)
=
\{
c_i\in C(p)
\mid
c_i=\text{false}
\}.
\]

Define the unresolved set:

\[
U(p)
=
\{
c_i\in C(p)
\mid
c_i=\text{unknown}
\}.
\]

A plan fails deterministically when:

\[
B(p)\neq\varnothing.
\]

Instead of treating every failed plan as equivalent, the planner can inspect:

\[
B(p).
\]

For example:

```text
candidate: drive rental car
blocking constraints:
    license = false
    vehicle access = false
```

This exposes a capability gap.

---

## 18. Minimal Blocking Sets

Many candidate plans may fail for overlapping reasons.

The useful object is often not the full set of all violated constraints but a minimal blocking set.

Let:

\[
\mathcal B(d)
\]

be the family of constraint sets sufficient to block all satisfactory plans for demand \(d\).

A minimal blocking set:

\[
B_{\min}
\in
\mathcal B(d)
\]

contains no redundant blocker.

Intuitively:

```text
if these few constraints were changed,
at least one satisfactory plan could become feasible
```

This resembles a cut set in graph reasoning.

The planner can then focus architectural search on:

\[
B_{\min}
\]

rather than on every possible capability the agent could ever acquire.

---

## 19. The Constraint-Directed Expansion Principle

This yields a computational principle:

\[
\boxed{
\textbf{Constraint-Directed Expansion Principle}
}
\]

> When a valuable demand cannot be satisfied, search first over interventions on the constraints that directly block high-value candidate plans, rather than over arbitrary possible capability acquisitions.

The resulting process is:

```text
failed demand
↓
candidate near-feasible plans
↓
blocking constraints
↓
minimal blocking sets
↓
candidate interventions
↓
counterfactual feasible graphs
↓
value comparison
```

This converts unconstrained self-improvement into targeted structural search.

---

## 20. From Blocking Constraints to Capability Gaps

Suppose a task family requires:

\[
K_{\text{required}}
=
\{k_1,k_2,k_3,k_4\}.
\]

The agent currently has:

\[
K_t
=
\{k_1,k_2\}.
\]

Then:

\[
\Delta K
=
K_{\text{required}}
-
K_t
=
\{k_3,k_4\}.
\]

The planner need not ask:

```text
What could I become better at?
```

It can ask:

```text
Which missing capabilities directly explain the failure of valuable plans?
```

Thus:

\[
\boxed{
\text{failed plans can generate candidate self-improvements}
}
\]

This is a central mechanism for keeping endogenous capability acquisition bounded.

---

## 21. Interventions Over Constraints

Let:

\[
I(c)
\]

be the set of possible interventions that may change the status of blocking constraint \(c\).

For example:

```text
constraint: no vehicle access

interventions:
    rent vehicle
    join car sharing
    borrow vehicle
    buy vehicle
    use employer vehicle
```

or:

```text
constraint: no authorization

interventions:
    obtain license
    obtain permit
    obtain visa
    change jurisdiction
    choose different mode
```

Thus the planner can construct:

\[
A_{\text{expand}}(d)
=
\bigcup_{c\in B_{\min}(d)}
I(c).
\]

The frontier search space is generated from diagnosed failure.

---

## 22. Counterfactual Feasible Graphs

Every candidate frontier intervention can be evaluated by projection.

Suppose:

\[
a^E:
X_t
\rightarrow
X_t^{(a)}.
\]

Then construct:

\[
G^{F,(a)}
=
\Pi(
\hat G_t,
X_t^{(a)},
C_t^{(a)}
).
\]

This is the feasible graph the agent expects would become available if intervention \(a\) succeeded.

The system can compare:

\[
G_t^F
\]

with:

\[
G^{F,(a)}.
\]

But raw graph size is not sufficient.

The planner must ask what valuable future demands the difference actually helps satisfy.

---

## 23. Reachability Count Is Not Value

Suppose an intervention unlocks:

\[
10{,}000
\]

new transitions.

That may sound valuable.

But if those transitions lead only to:

```text
irrelevant destinations
expensive routes
unsafe routes
rarely demanded states
high-maintenance dependencies
```

their practical value may be small.

Thus:

\[
|G_{t+1}^F|
>
|G_t^F|
\]

does not imply:

\[
V(G_{t+1}^F)
>
V(G_t^F).
\]

This requires a demand model.

---

## 24. Future Demand Distribution

Let:

\[
D_{t:t+H}
\]

represent future demands over horizon \(H\).

The agent does not know them exactly.

Instead use:

\[
d
\sim
P(D_{t:t+H}).
\]

Examples in mobility:

```text
future commute
airport trip
remote worksite visit
family visit
emergency trip
international travel
shopping trip
weekend travel
```

The value of a capability depends on how it changes outcomes under likely future demands.

This converts abstract reachability into expected usefulness.

---

## 25. Demand-Weighted Option Value

Let:

\[
V^\*(d\mid X)
\]

be the value of the best feasible response to demand \(d\) under architecture state \(X\).

Then the gross future value of intervention \(a^E\) can be approximated by:

\[
V_{\text{gross}}(a^E)
=
\mathbb E_{d\sim P(D)}
\left[
V^\*(d\mid X_t^{(a)})
-
V^\*(d\mid X_t)
\right].
\]

Net intervention value is then:

\[
\boxed{
V_{\text{net}}(a^E)
=
V_{\text{gross}}(a^E)
-
C_{\text{acquire}}(a^E)
-
C_{\text{operate}}(a^E)
-
C_{\text{maintain}}(a^E)
-
R(a^E)
}
\]

where:

\[
R(a^E)
\]

collects relevant risk, irreversibility, uncertainty, or downside exposure.

This formalizes capability option value.

---

## 26. A Capability Is Valuable When It Helps Plausible Future Demands

A driver's license is not valuable merely because it activates road edges.

Its value depends on whether future demands are likely to benefit from those edges.

Similarly:

```text
a passport has little immediate value while unused
a compiler installed locally may have little immediate value
a professional certification may create no immediate task reward
a backup payment method may be unused most days
```

Yet each can have high expected future option value when:

```text
future blocking demands are plausible
reactive acquisition would be slow
the capability is reusable
maintenance cost is acceptable
```

Thus:

\[
\boxed{
\text{capability value is demand-conditioned}
}
\]

not merely topology-conditioned.

---

## 27. Capability Prefetch

Some capabilities should be acquired before they are urgently needed.

Define a future demand class:

\[
D^+.
\]

Suppose:

1. \(P(D^+)\) is sufficiently high,
2. reactive acquisition latency is large,
3. the demand is expensive or impossible without the capability,
4. the capability is reusable,
5. current acquisition cost is acceptable.

Then pre-acquisition may be rational.

\[
\boxed{
\textbf{Capability Prefetch Principle}
}
\]

> If a reusable capability is likely to unblock valuable future demands and cannot be acquired cheaply or quickly at the moment of need, begin acquisition before the first critical demand.

Examples:

```text
obtain license before recurring remote-site travel begins
obtain passport before likely international travel
learn a tool before a project reaches the dependent phase
establish backup infrastructure before expected peak load
join a service before recurring urgent access is likely
```

---

## 28. Acquisition Latency Matters

Two interventions with equal long-run value may differ because one can be obtained instantly and the other requires months.

Let:

\[
\tau_{\text{acquire}}(a)
\]

be acquisition latency.

Then an intervention may be valuable even before immediate demand exists if:

\[
\tau_{\text{acquire}}(a)
>
\tau_{\text{reaction-window}}.
\]

This yields a general principle:

\[
\boxed{
\text{slow-to-acquire capabilities should be considered earlier}
}
\]

because waiting for explicit demand can make acquisition useless for the first important event.

---

## 29. Maintenance Debt

Frontier expansion is not free.

A new capability may introduce persistent obligations.

For a car:

```text
insurance
maintenance
parking
fuel
inspection
registration
repair risk
```

For a professional certification:

```text
renewal
continuing education
fees
compliance burden
```

For software infrastructure:

```text
updates
security patches
monitoring
compatibility maintenance
operator knowledge
```

Therefore:

\[
\boxed{
\text{frontier expansion}
\neq
\text{constraint elimination}
}
\]

A new capability can remove some blockers while creating new dependencies.

---

## 30. Dependency Topology

A frontier intervention should therefore be evaluated not only by what it unlocks but also by what it makes the agent depend on.

Let:

\[
Dep(a)
\]

be the dependency set introduced by intervention \(a\).

Examples:

```text
car ownership
    → insurance
    → parking
    → maintenance
    → fuel or charging

cloud service
    → network access
    → subscription
    → provider availability
    → account credentials
```

Two interventions may unlock similar future actions while producing very different dependency topologies.

This should enter valuation.

---

## 31. Reversibility

Some frontier interventions are easy to test and reverse.

Others are expensive or difficult to undo.

Let:

\[
\rho(a)
\]

represent reversibility.

High-reversibility interventions include:

```text
renting
trial subscription
borrowing
temporary access
sandbox deployment
short-term relocation
```

Low-reversibility interventions include:

```text
large purchase
permanent relocation
career change
major infrastructure investment
long contractual commitment
```

When uncertainty is high, reversibility has option value.

---

## 32. Speculative Frontier States

A planner can use provisional architecture states.

Let:

\[
X_{t+1}^{S}
\]

be a speculative state produced by a reversible trial.

For example:

```text
rent a car before buying one
borrow an e-bike before purchasing
trial a service before annual subscription
simulate a new workflow before organizational rollout
```

Then:

\[
X_t
\rightarrow
X_{t+1}^{S}
\]

allows evidence collection.

If results are favorable:

\[
X_{t+1}^{S}
\rightarrow
X_{t+1}^{C}
\]

where \(C\) is committed.

Otherwise:

\[
X_{t+1}^{S}
\rightarrow
X_t
\]

or another architecture.

This reduces irreversible mistakes.

---

## 33. Hysteresis

A frontier planner should not restructure itself after every isolated failure.

Nor should it ignore persistent architectural mismatch.

Define:

\[
P_t
\]

as frontier pressure.

Pressure may rise from:

```text
repeated infeasible demands
repeated expensive workarounds
persistent reliability failure
high recurring latency
frequent emergency access
repeated use of temporary substitutes
large opportunity loss
new rules repeatedly causing incompatibility
```

Define two thresholds:

\[
\theta_{\text{explore}}
\]

and:

\[
\theta_{\text{commit}},
\]

with:

\[
\theta_{\text{commit}}
>
\theta_{\text{explore}}.
\]

Then:

```text
low pressure
    → continue ordinary operation

moderate repeated pressure
    → investigate alternatives

high validated pressure
    → commit to structural change
```

This prevents oscillation.

---

## 34. The Frontier-Pressure Principle

\[
\boxed{
\textbf{Frontier-Pressure Principle}
}
\]

> Repeated failures, costly workarounds, or recurring blocked demands should increase pressure for architectural investigation, but substantial capability acquisition should require stronger evidence than merely beginning exploration.

This separates:

```text
notice
investigate
test
validate
commit
```

---

## 35. Representation Can Also Be a Bottleneck

An agent may possess a capability but fail to use it because the representation does not express the relevant distinction.

Suppose a system represents vehicles only as:

```text
car
truck
```

A new regulation distinguishes:

```text
combustion
hybrid
battery electric
hydrogen
```

If the schema cannot represent propulsion type, the constraint cannot be applied correctly.

Thus:

\[
\boxed{
\text{new world distinction}
\rightarrow
\text{possible representational expansion}
}
\]

A bounded agent must therefore treat its ontology as operationally useful but not complete.

---

## 36. Representation Updates Are Not World Updates

Three update types should be kept separate.

### World update

Reality changes.

```text
bridge closes
service launches
rule changes
resource disappears
weather changes
```

### Agent update

The agent changes.

```text
license acquired
budget changes
equipment purchased
skill learned
subscription activated
```

### Representation update

The model changes.

```text
new rule type added
new mode represented
incorrect edge removed
constraint variable introduced
compatibility relation added
```

These may produce similar changes in \(G_t^F\), but their causes differ.

Conflating them harms diagnosis.

---

## 37. Reality-Coupled Planning

The planner should repeatedly compare represented predictions with observed outcomes.

A useful loop is:

```text
represent
predict
act
observe
compare
revise
```

The goal is not perfect representation.

That is generally impossible.

The goal is sufficient operational coupling between:

\[
\hat G_t
\]

and:

\[
G_t^\*
\]

for the decisions that matter.

Thus:

\[
\boxed{
\textbf{Reality-Coupling Principle}
}
\]

> Planning representations should be revised when prediction errors, new evidence, or new distinctions materially affect feasibility, cost, or future frontier decisions.

---

## 38. Two-Level Planning

A practical architecture can use two coupled planners.

### Level 1: operational planner

Given:

\[
G_t^F,
\]

find a good action or path for current demand.

Its question is:

```text
What should I do with the capabilities I currently have?
```

### Level 2: frontier planner

Given:

```text
repeated demands
failures
blocking constraints
future demand forecasts
acquisition costs
maintenance burden
```

consider interventions that alter future planning conditions.

Its question is:

```text
What should I change now so that better actions become feasible later?
```

Thus:

\[
\boxed{
\text{search over actions}
\subset
\text{search over agent architectures}
}
\]

---

## 39. The Frontier Planner Should Not Run Everywhere

Architectural reasoning is expensive.

It should be triggered selectively.

Candidate triggers include:

```text
no satisfactory current plan
repeated use of costly fallback
persistent blocking constraint
forecasted high-value future demand
large acquisition latency
large reliability gap
new external rule
new technology or mode
large discrepancy between predicted and observed feasibility
```

This keeps the higher-level search sparse.

---

## 40. Candidate Generation by Causal Relevance

The frontier planner should prefer interventions causally connected to failure.

Suppose the current demand fails because:

```text
train route unavailable
car route exists
license missing
vehicle access missing
```

The relevant interventions include:

```text
obtain license
obtain vehicle access
find a non-car route
change destination or timing
```

Irrelevant interventions include arbitrary capabilities unrelated to those blockers.

Thus:

\[
\boxed{
\text{structural search should be causally anchored}
}
\]

This is stronger than generic self-improvement.

---

## 41. Counterfactual Architecture Evaluation

For each candidate intervention \(a\):

1. construct counterfactual architecture state,

\[
X_t^{(a)};
\]

2. recompute feasible graph,

\[
G_t^{F,(a)};
\]

3. evaluate future demands,

\[
d\sim P(D);
\]

4. compare expected value against acquisition and maintenance cost.

Formally:

\[
a^\*
=
\arg\max_{a\in A_{\text{frontier}}}
\left[
\mathbb E_d
V^\*(d\mid X_t^{(a)})
-
C_{\text{total}}(a)
\right].
\]

The current architecture can be represented as a null intervention:

\[
a_0=\text{do nothing}.
\]

Thus frontier change must beat continued operation.

---

## 42. Robustness Value

Some capabilities are valuable even if they rarely improve the nominal best plan.

They may improve resilience.

Suppose the normal commute is rail.

A car-sharing membership may almost never be the cheapest first choice.

But it may be valuable under:

```text
rail cancellation
late-night emergency
medical need
weather disruption
unexpected remote-site trip
```

Thus intervention value should include:

\[
V_{\text{robustness}}.
\]

A general objective may contain:

\[
V_{\text{expected}}
+
V_{\text{robustness}}
+
V_{\text{option}}
-
C_{\text{total}}.
\]

---

## 43. Rare but Severe Demands

Expected value alone may underweight low-probability catastrophic blockers.

Suppose:

```text
probability of emergency need = low
cost of being unable to respond = extremely high
```

Then risk-sensitive terms may matter.

One possibility is:

\[
V(a)
=
\mathbb E[U]
-
\lambda \operatorname{Risk}(U)
-
C(a).
\]

Another is to impose hard preparedness constraints:

\[
P(\text{critical demand satisfiable})
\ge
1-\epsilon.
\]

The correct form depends on the domain.

The general point is:

\[
\boxed{
\text{frontier value may include preparedness, not only average utility}
}
\]

---

## 44. Capability Portfolios

Capabilities interact.

A license may have little value without vehicle access.

Vehicle access may have little value without payment compatibility.

A passport may have little value for a trip without a visa.

Thus the value function may be non-additive.

For capabilities \(k_1\) and \(k_2\):

\[
V(k_1+k_2)
\neq
V(k_1)+V(k_2).
\]

Indeed:

\[
V(k_1+k_2)
>
V(k_1)+V(k_2)
\]

may occur through complementarity.

This makes capability acquisition a portfolio problem.

The planner should sometimes evaluate bundles.

---

## 45. Minimal Enabling Bundles

Given a blocked action family, define a minimal enabling bundle:

\[
B_E
=
\{k_1,\ldots,k_n\}
\]

such that:

\[
G^F(X_t+B_E)
\]

contains a desired transition family, while no strict subset of \(B_E\) does.

For car rental:

```text
license
payment capability
rental eligibility
vehicle availability
jurisdiction compatibility
```

may jointly form an enabling bundle.

This prevents the planner from overvaluing one component in isolation.

---

## 46. Bottleneck Dominance

If a capability bundle is conjunctive, one missing component can dominate value.

Suppose:

\[
K_{\text{effective}}
=
k_1\land k_2\land k_3.
\]

If:

\[
k_3=0,
\]

then increasing the quality of \(k_1\) may provide no immediate frontier gain.

This suggests:

\[
\boxed{
\text{in conjunctive systems, remove bottlenecks before optimizing non-bottlenecks}
}
\]

unless the improved component has value elsewhere.

Blocking-constraint diagnosis naturally exposes this structure.

---

## 47. Frontier Compression

Not all rational structural changes expand the action space.

Sometimes the agent should deliberately reduce it.

Examples:

```text
sell a rarely used vehicle
cancel an expensive service
remove fragile infrastructure
standardize tools
reduce unsupported modes
drop a jurisdiction with high compliance cost
```

Thus a more general term than expansion is:

\[
\text{frontier management}.
\]

The objective is not maximal breadth.

It is useful, reliable, maintainable capability.

Therefore:

\[
\boxed{
\text{optimal frontier}
\neq
\text{largest frontier}
}
\]

---

## 48. Capability Abandonment

Let a maintained capability \(k\) have:

\[
V_{\text{future}}(k)
<
C_{\text{maintain}}(k).
\]

Then abandonment can be rational.

This produces:

\[
G_{t+1}^F
\subset
G_t^F
\]

while improving total value.

A complete frontier framework should therefore permit:

```text
acquire
retain
upgrade
downgrade
replace
abandon
```

rather than assuming monotonic expansion.

---

## 49. Frontier Substitution

Two capabilities may provide overlapping reachability.

For example:

```text
private car
car sharing
ride hailing
strong rail access
```

may partially substitute for one another.

Thus the planner should evaluate marginal rather than gross value.

If capability \(k_1\) already exists:

\[
\Delta V(k_2\mid k_1)
\]

may be much smaller than:

\[
V(k_2\mid \varnothing).
\]

This matters for avoiding redundant capability portfolios.

---

## 50. Frontier Diversity and Correlated Failure

Capabilities that appear redundant under normal conditions may fail differently.

For example:

```text
rail
private car
bicycle
```

have different dependencies.

Rail may depend on service operation.

Cars may depend on fuel, roads, parking, and traffic.

Bicycles may depend on weather, physical ability, and safe infrastructure.

A diversified frontier can therefore improve resilience if failure modes are weakly correlated.

This introduces:

\[
V_{\text{diversity}}
\]

as a possible architectural value component.

---

## 51. Mobility Example: License Plus Rental Access

Suppose the agent currently has:

```text
walking
rail
bus
```

but no car mobility.

A valuable future demand appears repeatedly:

```text
reach remote sites outside transit coverage
```

Candidate car plans are blocked by:

```text
license = false
vehicle access = false
```

The frontier planner identifies:

\[
B_{\min}
=
\{
\text{license},
\text{vehicle access}
\}.
\]

Candidate interventions include:

```text
obtain license
join car-sharing service
join rental service
buy car
```

The planner may discover that:

```text
license + rental membership
```

unlocks most of the valuable future demand at much lower maintenance cost than ownership.

Thus the correct architectural unit is the enabling bundle.

---

## 52. Mobility Example: Relocation

Suppose a person repeatedly spends:

```text
90 minutes commuting
high monthly transit cost
large transfer risk
```

Ordinary route optimization may find only small improvements.

The frontier planner can consider:

```text
move home
change work location
increase remote work
change parking location
```

Relocation changes the start node:

\[
s_t
\rightarrow
s_{t+1}
\]

and therefore alters many future shortest paths simultaneously.

This is not merely a better route.

It is a graph-geometric intervention.

---

## 53. Mobility Example: Unknown Ferry Constraint

Suppose a desirable route uses a ferry.

The planner knows:

```text
ferry exists
departure time known
ticket price known
vehicle weight limit unknown
```

Then:

\[
c_{\text{weight}}=\text{unknown}.
\]

The correct next action may be:

```text
retrieve operator rule
```

rather than:

```text
buy a lighter vehicle.
```

Information gathering should precede capability acquisition when the blocker may disappear under better knowledge.

---

## 54. Mobility Example: Stochastic Service

Suppose the ferry accepts the vehicle, but severe weather may cancel service.

Then:

\[
P(\text{service available})=0.6.
\]

This is not an unknown rule.

It is stochastic availability.

The planner should compare:

```text
expected delay
fallback options
cost of failure
alternative routes
```

and may prefer a robust architecture with another mobility mode.

---

## 55. Generalization Beyond Mobility

The same structure appears in many domains.

### Computing

```text
world:
    available APIs
    networks
    machines
    software ecosystems

agent:
    credentials
    libraries
    compute
    permissions
    skills

frontier action:
    install dependency
    request permission
    provision compute
    learn API
    add connector
```

### Organizations

```text
world:
    regulations
    vendors
    markets
    institutions

agent:
    staff skills
    contracts
    licenses
    budget
    internal processes

frontier action:
    hire
    certify
    partner
    reorganize
    acquire tool
```

### Personal finance

```text
world:
    markets
    banking rails
    regulations
    products

agent:
    accounts
    credit
    liquidity
    identity documents
    tax status

frontier action:
    open account
    build emergency reserve
    obtain required documentation
```

The domain changes.

The architecture remains.

---

## 56. General Form of a Bounded-Agent Planning State

Let:

\[
W_t^\*
\]

be actual world state.

Let:

\[
L_t
\]

be represented world state.

Let:

\[
X_t
=
(S_t,K_t,R_t,J_t)
\]

be the agent's operational architecture.

Let:

\[
\hat G_t
=
G(L_t)
\]

be the represented transition graph.

Let:

\[
C_t
=
C(L_t,X_t)
\]

be represented constraint state.

Then:

\[
\boxed{
G_t^F
=
\Pi(
\hat G_t,
C_t
)
}
\]

is the represented feasible graph.

Ordinary planning selects:

\[
a_t
\in
G_t^F.
\]

Frontier planning selects an intervention:

\[
a_t^E:
(X_t,L_t)
\rightarrow
(X_{t+1},L_{t+1})
\]

because of its effect on later feasible planning.

---

## 57. A Unified Frontier Objective

A schematic objective is:

\[
\boxed{
a_t^\*
=
\arg\max_{a\in A_t^{\text{candidate}}}
\left[
V_{\text{current}}(a)
+
V_{\text{future-demand}}(a)
+
V_{\text{option}}(a)
+
V_{\text{robustness}}(a)
+
V_{\text{information}}(a)
-
C_{\text{acquire}}(a)
-
C_{\text{operate}}(a)
-
C_{\text{maintain}}(a)
-
C_{\text{dependency}}(a)
-
R(a)
\right]
}
\]

subject to:

\[
\operatorname{Feasible}(a)
\]

for actions executed now.

Different action classes emphasize different terms.

An exploratory action may have large:

\[
V_{\text{information}}.
\]

A capability acquisition may have large:

\[
V_{\text{future-demand}}
+
V_{\text{option}}.
\]

A robust backup capability may have large:

\[
V_{\text{robustness}}.
\]

A maintenance-heavy asset may have large:

\[
C_{\text{maintain}}
+
C_{\text{dependency}}.
\]

---

## 58. Demand-Conditioned Reachability

Define:

\[
\mathcal R_H(X_t)
\]

as the set of states reachable within horizon \(H\).

A purely topological frontier value might depend on:

\[
|\mathcal R_H|.
\]

A demand-conditioned frontier instead weights states by expected usefulness.

Let:

\[
w(x)
\]

represent the expected value of reaching state \(x\).

Then:

\[
V_{\mathcal R}(X_t)
=
\sum_{x\in\mathcal R_H(X_t)}
w(x).
\]

More generally:

\[
w(x)
\]

may depend on demand probability, timing, reliability, and substitution.

This formalizes the idea that a capability is valuable because of the future situations it helps solve, not because it mechanically increases graph size.

---

## 59. The Feasible-Frontier Principle

\[
\boxed{
\textbf{Feasible-Frontier Principle}
}
\]

> A bounded agent should distinguish the transitions represented as existing from the transitions currently judged executable, and ordinary planning should operate on the latter.

This prevents impossible actions from being treated as merely unattractive.

---

## 60. The Reality-Representation Principle

\[
\boxed{
\textbf{Reality-Representation Principle}
}
\]

> The actual transition structure of the world and the agent's represented transition structure are distinct objects; planning quality depends both on the quality of the representation and on the quality of search within it.

A perfect planner on a bad world model still fails.

---

## 61. The Capability-Composition Principle

\[
\boxed{
\textbf{Capability-Composition Principle}
}
\]

> Effective capability often emerges from combinations of skill, authorization, access, resources, compatibility, and availability rather than from any single possessed asset.

Thus frontier value may be highly non-additive.

---

## 62. The Blocking-Constraint Principle

\[
\boxed{
\textbf{Blocking-Constraint Principle}
}
\]

> When a valuable plan fails, preserve the causal explanation of failure and use the blocking constraints to generate targeted exploration and frontier interventions.

This turns failure into structured architectural information.

---

## 63. The Demand-Weighted Frontier Principle

\[
\boxed{
\textbf{Demand-Weighted Frontier Principle}
}
\]

> A frontier change should be valued by how it improves expected performance over plausible future demands, not by the raw number of actions or states it makes reachable.

This separates useful flexibility from meaningless breadth.

---

## 64. The Reversibility Principle

\[
\boxed{
\textbf{Reversibility Principle}
}
\]

> Under substantial uncertainty, prefer provisional, testable, or reversible frontier changes when they provide enough information to evaluate a later irreversible commitment.

This preserves option value.

---

## 65. The Maintenance-Debt Principle

\[
\boxed{
\textbf{Maintenance-Debt Principle}
}
\]

> Every acquired capability should be evaluated not only by what it unlocks but also by the recurring resources, dependencies, obligations, and failure modes required to keep it usable.

This prevents frontier growth from being mistaken for free improvement.

---

## 66. The Non-Monotonic Frontier Principle

\[
\boxed{
\textbf{Non-Monotonic Frontier Principle}
}
\]

> Rational frontier management may expand, compress, substitute, or abandon capabilities; the goal is not the largest feasible-action set but the highest-value maintainable architecture.

Thus:

\[
\text{more possible actions}
\]

is not always:

\[
\text{better}.
\]

---

## 67. The Open-World Principle

\[
\boxed{
\textbf{Open-World Principle}
}
\]

> The agent should treat its current modes, constraints, categories, and intervention types as operationally useful but structurally incomplete.

New reality may require:

```text
new values
new variables
new categories
new constraints
new actions
new capability types
```

The representation itself must therefore remain revisable.

---

## 68. A Complete Control Loop

```text
OBSERVE CURRENT STATE
↓
update represented world
↓
construct represented transition graph
↓
evaluate constraints
↓
project feasible graph
↓
receive current demand
↓
is a satisfactory feasible plan available?
├── yes
│   ↓
│   search / compare / execute
│   ↓
│   observe cost, reliability, and outcome
│   ↓
│   update world and agent state
│
└── no
    ↓
    generate near-feasible candidate plans
    ↓
    inspect blocking constraints
    ↓
    are important blockers unknown?
    ├── yes
    │   ↓
    │   explore / retrieve / test
    │   ↓
    │   update representation
    │   ↓
    │   recompute feasible graph
    │
    └── no
        ↓
        identify minimal blocking sets
        ↓
        classify blockers:
            external immutable
            agent-changeable
            compatibility
            resource
            location
            representation
        ↓
        generate targeted interventions
        ↓
        construct counterfactual architecture states
        ↓
        recompute counterfactual feasible graphs
        ↓
        evaluate over future demand distribution
        ↓
        include:
            acquisition cost
            maintenance debt
            dependency burden
            robustness value
            reversibility
            acquisition latency
        ↓
        trial reversibly where useful
        ↓
        acquire / subscribe / learn / relocate / reconfigure
        ↓
        recompute feasible graph

IN PARALLEL:
↓
track repeated failures
↓
update frontier pressure
↓
forecast future demand classes
↓
detect slow-to-acquire capabilities
↓
prefetch when justified
↓
detect stale or missing representation
↓
revise ontology when necessary
↓
periodically evaluate unused capability debt
↓
retain / substitute / abandon capabilities
```

---

## 69. Why This Architecture Is Computationally Plausible

A naive endogenous agent could face an enormous problem.

At every moment it might ask:

```text
Which of all imaginable capabilities should I acquire?
Which of all imaginable representations should I invent?
Which of all imaginable resources should I obtain?
```

That search is intractable.

The framework avoids this by introducing several forms of sparsity.

### Failure-driven sparsity

Only investigate frontier change when ordinary planning produces meaningful pressure.

### Constraint-driven sparsity

Generate interventions from blocking constraints.

### Demand-driven sparsity

Value interventions according to plausible future demand.

### Bundle sparsity

Search minimal enabling bundles rather than arbitrary capability combinations.

### Hysteresis

Do not commit after weak evidence.

### Reversibility

Use low-cost trials to eliminate bad candidates early.

Thus frontier management is not continuous arbitrary self-reinvention.

It is targeted structural adaptation.

---

## 70. The Deeper Interpretation

The agent's action space is not fixed.

But neither is it unconstrained.

At every moment:

\[
\boxed{
\text{current feasibility is binding}
}
\]

The agent cannot optimize its way through:

```text
a missing bridge
an absent authorization
an incompatible interface
an unavailable resource
an unrepresented transition
```

Yet:

\[
\boxed{
\text{some future constraints are endogenous}
}
\]

The agent may change:

```text
what it knows
what it can do
what it can access
what it is authorized to do
where it is located
what it depends on
what it can represent
```

This changes future planning possibility.

The deepest architecture is therefore:

\[
\boxed{
\text{reality}
+
\text{representation}
+
\text{agent architecture}
+
\text{constraints}
\rightarrow
\text{feasible action frontier}
\rightarrow
\text{ordinary planning}
}
\]

with the endogenous extension:

\[
\boxed{
\text{failure or future demand}
\rightarrow
\text{blocking-constraint diagnosis}
\rightarrow
\text{candidate intervention}
\rightarrow
\text{counterfactual frontier}
\rightarrow
\text{capability decision}
}
\]

---

## 71. Conclusion

A bounded agent should not be modeled as choosing among all imaginable actions.

It operates inside a real world through a limited representation and a limited architecture.

The actual world defines what transitions really exist.

The representation determines what transitions can be reasoned about.

The agent's capabilities, resources, access, compatibility, and current state determine which represented transitions appear executable.

Ordinary planning therefore occurs over:

\[
G_t^F,
\]

the represented feasible graph.

But this graph is not necessarily permanent.

Actions taken now can change:

```text
capability
authorization
access
resources
compatibility
location
dependencies
representation
```

and thereby alter:

\[
G_{t+1}^F.
\]

The planner should therefore reason at two levels.

The operational level asks:

```text
What is the best feasible action now?
```

The frontier level asks:

```text
Which present intervention would make a valuable class of future actions feasible, cheaper, more reliable, or better represented?
```

The bridge between the two is blocking-constraint diagnosis.

When valuable plans fail, the failure reveals where the current architecture is insufficient.

Those blockers can generate targeted interventions.

Candidate interventions can then be evaluated through counterfactual feasible graphs and a demand-weighted value model that includes acquisition cost, maintenance debt, dependency burden, robustness, reversibility, and acquisition latency.

This produces a more disciplined interpretation of endogenous capability growth.

The agent does not expand merely because expansion is possible.

It expands when persistent failure, predicted demand, or structural opportunity justifies changing the architecture from which later actions will be selected.

Thus the system is not merely searching a fixed action space.

It is selectively managing the conditions under which future action spaces become available.

\[
\boxed{
\text{bounded agency}
=
\text{planning within a frontier}
+
\text{reasoning about when to change the frontier}
}
\]
