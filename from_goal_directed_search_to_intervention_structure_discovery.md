# From Goal-Directed Search to Intervention-Structure Discovery

## Causal Handles, Open-Ended Exploration, Controllability Maps, and the Architecture of Search

## Abstract

A common way to describe intelligent behavior is:

```text
current state
→
choose a goal
→
search for a route
→
execute the route
```

This is useful when the agent already knows:

```text
what it wants
what actions exist
what those actions do
which interfaces invoke them
which constraints apply
and how success will be recognized
```

But many important forms of exploration begin before those objects are available.

An agent may enter a physical environment, software system, game, institution, body, toolchain, language, or social setting and ask a more primitive question:

> What can be changed here, through which locally available interventions, under what conditions, with what effects, and how reliably?

This paper calls that problem **intervention-structure discovery**.

The central object is not merely a destination or a route.

It is a map of accessible causal handles:

\[
\mathcal I_t
=
\{
(x,u,\Delta x,c,r,\ell,\kappa,\ldots)
\},
\]

where an entry records that from state or context \(x\), an intervention \(u\) can produce some state change \(\Delta x\), subject to conditions \(c\), with reliability \(r\), latency \(\ell\), cost \(\kappa\), and other operational metadata.

This map may be incomplete even when the underlying world already contains the relevant transition.

A command may exist but its syntax may be unknown.

A physical affordance may exist but be unnoticed.

A tool may be installed but its interface may be unavailable.

A biological variable may matter but not be directly writable.

A social resource may exist but require authorization, trust, money, language, or another locally executable route before it becomes usable.

Thus it is useful to distinguish:

\[
\boxed{
\text{world transition structure}
\neq
\text{represented intervention structure}
\neq
\text{locally executable intervention structure}
}
\]

Goal-directed route search operates only after enough of this structure is already represented.

Open-ended exploration may instead be valuable because it discovers the structure itself.

This produces a broader architecture:

\[
\boxed{
\text{observe}
\rightarrow
\text{probe}
\rightarrow
\text{discover regularity}
\rightarrow
\text{identify a causal handle}
\rightarrow
\text{make it addressable}
\rightarrow
\text{stabilize invocation}
\rightarrow
\text{retain provenance}
\rightarrow
\text{compose}
\rightarrow
\text{expand future reachable structure}
}
\]

The resulting view separates route search, system identification, interface discovery, exploration, representation change, capability expansion, and control.

It also gives a more precise account of curiosity, sandbox behavior, troubleshooting, problem solving, delegation, preparedness, and cumulative intelligence.

---

# 1. The Goal-Directed Search Assumption Is Too Strong

Suppose an agent is in state:

\[
x_t.
\]

A standard planning formulation introduces a desired target region:

\[
G.
\]

The planner then asks for a sequence of controls:

\[
u_{0:T}
\]

such that:

\[
x_T\in G.
\]

This is a legitimate problem.

But it silently assumes that the agent already possesses enough structure to ask it.

The agent must already have some representation of:

```text
states
actions
preconditions
effects
costs
constraints
available interfaces
and the target itself
```

In many real situations, the earlier problem is:

```text
What actions are actually available?
What do they affect?
How do I invoke them?
Which effects are stable?
Which apparent controls are aliases?
Which controls are hidden?
Which variables are not directly writable?
Which changes are reversible?
Which transformations compose?
```

Thus:

\[
\boxed{
\text{route search presupposes an intervention structure sufficiently rich to search over}
}
\]

When that structure is missing, stale, incomplete, or incorrectly represented, more route search may not solve the problem.

The agent may first need to discover the graph on which planning would operate.

---

# 2. A Desired State Is Not Required for Exploration

An agent can act meaningfully without trying to reach a particular terminal state.

Consider a person exploring a sandbox game.

They may:

```text
walk to an unused part of the island
push objects
shoot a barrel
watch enemy AI
try to climb unusual geometry
test collision behavior
change a configuration option
open a console
try a command prefix
reload a save
repeat an interaction from a different angle
stand still and observe
intentionally die
```

None of these actions necessarily serve:

```text
win the game
survive
finish the level
maximize score
```

The activity can instead be:

\[
\text{discover the transition structure exposed by the environment}.
\]

The immediate question is not:

> Which path reaches the ending?

It is:

> What does this system permit, how does it respond, and where can I intervene?

Therefore:

\[
\boxed{
\text{meaningful exploration}
\not\Rightarrow
\text{fixed terminal goal}
}
\]

A goal may arise later.

The discovered intervention structure may then make the later route cheap.

---

# 3. From Control Surfaces to Causal Handles

The phrase **control surface** is useful but can be misleading.

It suggests that reality presents clearly labeled knobs.

Often it does not.

A useful intervention may be:

```text
a hidden command
a keyboard prefix
a timing window
a pressure point on a physical mechanism
a social protocol
a legal permission
a parameter in a configuration file
a body posture
a learned motor routine
a particular question asked to the right person
a measurement that reveals a hidden branch
```

The common property is not visible surface structure.

It is causal leverage available through a locally realizable act.

Call such an object a **causal handle**.

A causal handle is not merely a variable that exists.

It is a relation between:

```text
agent-accessible intervention
and
reliably distinguishable downstream change
```

A schematic handle can be written:

\[
h
=
(
C_h,
U_h,
E_h,
R_h
),
\]

where:

- \(C_h\) is the applicability condition,
- \(U_h\) is the locally realizable invocation,
- \(E_h\) is the effect distribution,
- \(R_h\) is reliability or confidence.

A richer record may include:

\[
h=
(
C_h,
U_h,
E_h,
R_h,
L_h,
K_h,
V_h,
D_h,
P_h
),
\]

with:

```text
latency
cost
reversibility
side effects
dependency burden
provenance
resolution
scope
```

Thus:

\[
\boxed{
\text{causal handle}
\neq
\text{arbitrary causal variable}
}
\]

The variable must be operationally reachable through the current agent architecture.

---

# 4. Three Different Intervention Structures

Let:

\[
\mathcal I^*
\]

be the intervention structure that actually exists in the world.

This includes causal handles that the agent may not know about.

Let:

\[
\hat{\mathcal I}_t
\]

be the intervention structure represented by the agent at time \(t\).

And let:

\[
\mathcal I_t^F
\subseteq
\hat{\mathcal I}_t
\]

be the subset currently judged locally executable.

Then:

\[
\boxed{
\mathcal I_t^F
\subseteq
\hat{\mathcal I}_t
\not\equiv
\mathcal I^*
}
\]

is normal.

The differences matter.

A handle may be:

```text
real but unknown
known but not addressable
addressable but not authorized
invocable but unreliable
represented with the wrong syntax
available only in another version
available only through another person
physically possible but not voluntarily controllable
```

This gives several distinct failure modes.

---

# 5. Unknown Handle, Unknown Invocation, and Unavailable Handle Are Different

Suppose a software system contains a debug function.

There are at least three cases.

## Case 1: the function does not exist

\[
h\notin\mathcal I^*.
\]

No amount of syntax search will invoke it.

## Case 2: the function exists but the agent does not know it

\[
h\in\mathcal I^*
\quad\text{but}\quad
h\notin\hat{\mathcal I}_t.
\]

Discovery is required.

## Case 3: the function is represented but the invocation route is missing

\[
h\in\hat{\mathcal I}_t
\quad\text{but}\quad
h\notin\mathcal I_t^F.
\]

The agent may know that a capability exists yet lack:

```text
correct prefix
launch parameter
permission
binding
path
protocol
interface state
compatible version
```

These are not the same problem.

Therefore:

\[
\boxed{
\text{capability existence}
\neq
\text{capability knowledge}
\neq
\text{capability addressability}
\neq
\text{capability executability}
}
\]

---

# 6. The Addressability Gap

A particularly important case is the **addressability gap**.

The world contains a useful regularity.

The agent may even know approximately what it does.

But the transformation cannot yet be named, bound, or invoked through a reliable local interface.

Write:

\[
\operatorname{Exists}(h)=1
\]

while:

\[
\operatorname{Addressable}_t(h)=0.
\]

Then the practical problem is not to create the underlying transformation.

It is to construct or discover a route from current operations to the transformation.

For example:

```text
known debug capability
→
unknown console convention
→
search documentation
→
discover command namespace
→
correct invocation
→
capability becomes locally executable
```

The external system need not change at all.

What changes is the agent's operational map.

Thus:

\[
\boxed{
\text{newly usable capability}
\not\Rightarrow
\text{newly created world capability}
}
\]

Some frontier expansion is epistemic and interface-level rather than physical.

---

# 7. Route Search and Intervention Discovery Are Different Problems

Goal-directed route search asks:

\[
\boxed{
x_t\rightarrow ?\rightarrow G}
\]

Intervention discovery asks something more like:

\[
\boxed{
(x,u)\rightarrow ?\rightarrow \Delta x
}
\]

or:

\[
\boxed{
\text{Which locally realizable }u
\text{ produces a stable and useful distinction in outcome?}
}
\]

The first searches through a represented transition graph.

The second learns or refines the transition relation itself.

This is close to system identification, active experimentation, affordance discovery, interface learning, and causal probing.

But the emphasis here is specifically operational:

> Which discovered regularities can become reusable components of future action?

Thus:

\[
\boxed{
\text{search over routes}
\neq
\text{search for the handles from which routes can later be built}
}
\]

---

# 8. Forward Models and Inverse Problems Come Later

Suppose the agent has learned a transition model:

\[
x_{t+1}=F(x_t,u_t,w_t),
\]

where \(w_t\) represents uncontrolled or unknown factors.

A forward question is:

> If I apply \(u_t\), what happens?

An inverse question is:

> Which \(u_{0:T}\) could produce a desired state?

But both depend on having enough representation of \(F\).

Intervention discovery is partly the process that makes those questions answerable.

The architecture may therefore proceed:

\[
\text{probe}
\rightarrow
\hat F_t
\rightarrow
\text{reachability analysis}
\rightarrow
\text{inverse search}
\rightarrow
\text{trajectory selection}.
\]

This ordering matters.

A planner should not confuse lack of a known route with proof that no route exists.

Nor should it confuse the existence of a desired state with the existence of an admissible route.

---

# 9. Zero, One, Many, or Infinitely Many Solutions

Once a target is introduced, the familiar inverse-problem cases appear.

Let:

\[
\mathcal U(G\mid x_t)
\]

be the set of admissible intervention sequences that reach target region \(G\).

Then:

## No solution

\[
|\mathcal U|=0.
\]

The target is not reachable under the represented constraints.

## One solution

\[
|\mathcal U|=1.
\]

Constraints may leave a unique admissible path.

## Several solutions

\[
1<|\mathcal U|<\infty.
\]

The agent must choose among alternatives.

## Infinitely many solutions

\[
|\mathcal U|=\infty.
\]

Continuous control often admits many trajectories satisfying the same endpoint condition.

Therefore the target alone does not specify behavior.

A second criterion is required:

\[
\min_{u_{0:T}}
J(x_{0:T},u_{0:T}).
\]

Possible terms include:

```text
risk
energy expenditure
money
time
uncertainty
irreversibility
maintenance burden
attention
social cost
future option loss
```

Thus:

\[
\boxed{
\text{desired endpoint}
\neq
\text{unique trajectory}
}
\]

and:

\[
\boxed{
\text{existence of a trajectory}
\neq
\text{desirability of that trajectory}
}
\]

---

# 10. Open-Ended Exploration Is Intervention Cartography

When no terminal goal is active, exploration can still have structure.

Call the process **intervention cartography**.

The agent builds a map:

\[
\mathcal M_t:
(
\text{context},
\text{invocation}
)
\mapsto
(
\text{effect},
\text{uncertainty},
\text{cost},
\text{reversibility}
).
\]

The map need not be globally complete.

It can be local and sparse.

For example:

```text
this object can be pushed
this wall cannot be climbed from here
this command uses one parser
that command uses another parser
this NPC reacts to sound but not to light
this configuration change requires restart
this shortcut works only in version X
this physical motion is possible but unreliable
```

The value is not necessarily immediate reward.

The value may be:

\[
\text{future reduction in search cost}
+
\text{future option value}
+
\text{better causal models}
+
\text{new composable operators}.
\]

---

# 11. Curiosity as Long-Horizon Control Discovery

Curiosity is often described as a drive for information.

That is broad enough to include many things.

A more operational subtype is:

\[
\boxed{
\text{curiosity for controllability}
=
\text{exploration that discovers reusable intervention structure before a specific demand requires it}
}
\]

This is not identical to semantic prefetch.

Semantic prefetch prepares distinctions likely to become relevant to an anticipated execution path.

Control discovery can be more open-ended:

```text
try this because the mechanism is unknown
inspect that because it may expose a new class of actions
repeat a reversible variation because the effect structure is unclear
explore an unused region because it may contain new affordances
```

The horizon can be long and the future demand distribution diffuse.

The agent is building a library of possibilities.

---

# 12. Exploration, Exploitation, Expansion, Representation, and Cartography

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
\cup
A_{\text{map}}.
\]

The categories overlap, but their primary effects differ.

## Exploitation

Use currently known feasible transitions to satisfy present demand.

## Exploration

Reduce uncertainty about currently represented variables or transitions.

## Expansion

Change capability, access, resources, authorization, compatibility, location, or another condition so that previously infeasible transitions become feasible.

## Representation change

Introduce, remove, or revise distinctions used to describe the world and action space.

## Intervention cartography

Discover, localize, characterize, and operationalize causal handles.

Cartography can cause the other categories to change.

A probe may reveal that:

```text
a represented action was fictitious
a hidden action already existed
a known action had a different precondition
a coarse action actually contains multiple interfaces
a new representation is required to distinguish outcomes
a capability can be composed from existing primitives
```

Thus intervention cartography sits near the boundary between epistemic and capability change.

---

# 13. Active Probing Is Stronger Than Passive Observation

Suppose an observation \(y\) could have been generated by many processes:

\[
y=G_i(z_i).
\]

Passive observation may leave the generator underdetermined.

An intervention can alter the input conditions:

\[
\operatorname{do}(u_1)
\rightarrow
y_1,
\]

\[
\operatorname{do}(u_2)
\rightarrow
y_2.
\]

Different candidate generators may predict different responses.

Then probing can simultaneously:

```text
change the world
reveal how the world changes
discriminate among causal models
locate a usable handle
estimate reliability
identify side effects
```

Therefore:

\[
\boxed{
\text{intervention has both control value and identification value}
}
\]

This connects provenance reconstruction with capability discovery.

An intervention can reveal not only what state is reachable but also what kind of mechanism is producing the observed behavior.

---

# 14. The Output Does Not Identify the Generator

An undesirable state is not itself a causal explanation.

Suppose:

\[
G(z)\rightarrow y.
\]

Observing \(y\) constrains possible generators.

It does not generally identify one.

Thus:

```text
observed failure
≠
known cause
```

and:

```text
strong dislike of failure
≠
causal localization
```

An emotional response may correctly indicate:

\[
\text{desired state}\neq\text{observed state}.
\]

But a problem-solving loop requires additional work:

\[
\text{mismatch}
\rightarrow
\text{candidate generators}
\rightarrow
\text{discriminating observations or probes}
\rightarrow
\text{causal localization}
\rightarrow
\text{candidate interventions}.
\]

The important transition is not simply:

```text
negative state
→
positive state
```

It is:

```text
unlocalized failure
→
localized intervention structure
```

---

# 15. Error Detection and Error Localization Are Different

A system can detect that something is wrong without knowing where it is wrong.

Let:

\[
e_t=r_t-y_t
\]

be a mismatch between desired and observed state.

Nonzero \(e_t\) detects deviation.

But corrective action requires a mapping from deviation to intervention:

\[
e_t
\rightarrow
\text{candidate cause}
\rightarrow
\text{candidate handle}
\rightarrow
u_t.
\]

Without localization, the agent may repeatedly apply an ineffective action.

This produces:

\[
\text{failure}
\rightarrow
\text{repeat same intervention}
\rightarrow
\text{failure}
\rightarrow
\text{increased effort}
\]

without increasing control.

A better loop is:

\[
\boxed{
\text{failure}
\rightarrow
\text{localize missing or incorrect causal link}
\rightarrow
\text{probe}
\rightarrow
\text{update intervention map}
\rightarrow
\text{retry}
}
\]

---

# 16. Repeated Success Creates Strong Interface Priors

An agent with long experience in a system develops expectations not only about outcomes but about **where controllability normally lives**.

For example:

```text
configuration files usually expose this class of behavior
console commands usually use this syntax
mods usually alter this subsystem
reloading usually resets this state
this kind of object usually obeys this physics
```

These become interface priors.

Then a failure can be especially destabilizing when:

\[
\text{expected controllability}
\neq
\text{observed controllability}.
\]

The surprise is not merely:

```text
I failed to reach the target.
```

It may be:

```text
The control architecture I thought I understood is no longer exposing the handle where I expected it.
```

This predicts why experts can become sharply frustrated by small interface changes.

They have more accumulated structure to invalidate.

---

# 17. A Hidden Interface Can Be a Meta-Level Blocker

Suppose an ordinary action is difficult.

The agent normally uses a higher-level control path to alter the problem.

Then that higher-level path becomes inaccessible.

There are now two levels:

```text
object-level problem:
    difficult encounter

meta-level problem:
    usual mechanism for changing the encounter is unavailable
```

The second can dominate the first.

A person may not care about solving the object-level problem in the conventional way.

They may instead care about restoring the sandbox's controllability.

Thus:

\[
\boxed{
\text{failure of a meta-control interface can matter more than failure of the immediate task}
}
\]

This is one reason tooling failures, permission failures, missing debug access, and broken introspection can be disproportionately disruptive.

They remove the mechanism normally used to recover from many other failures.

---

# 18. Small Inputs Can Have High Causal Leverage

Control should not be confused with large energy expenditure.

Suppose a vehicle is drifting slightly within a lane.

A small steering correction applied early may preserve the trajectory.

If no correction occurs, a later intervention may require:

```text
large steering angle
hard braking
collision avoidance
impact absorption
medical repair
vehicle replacement
```

The late response can involve vastly more physical energy while producing a worse outcome.

Thus:

\[
\boxed{
\text{intervention magnitude}
\neq
\text{control quality}
}
\]

A more useful quantity is causal leverage:

\[
\Lambda(u)
=
\frac{
\text{valuable change in future trajectory}
}{
\text{intervention cost}
}.
\]

High leverage can come from:

```text
correct timing
correct location
correct representation
correct syntax
correct information
correctly chosen variable
```

not from large force.

---

# 19. Viability Is Usually a Bounded-Region Problem

Many functioning systems are not trying to maximize every internal variable.

They remain within regions compatible with continued operation.

Let:

\[
\mathcal V
\subseteq
X
\]

be a viability region.

A robust controller attempts to keep:

\[
x_t\in\mathcal V
\]

under disturbances.

Examples include maintaining bounded ranges of:

```text
temperature
speed
voltage
pressure
attention
fatigue
position
resource depletion
structural stress
```

The objective is often not:

\[
\max \text{energy}
\]

or:

\[
\max \text{output at every instant}.
\]

It is closer to:

\[
\boxed{
\text{preserve viable continuation while accomplishing useful transformations}
}
\]

This makes low-amplitude, well-timed correction central.

---

# 20. Late Compensation and Early Regulation Occupy Different Causal Positions

Suppose a small direct correction is available early.

If it is missed, the system may later require generalized resources to compensate.

A rough sequence is:

\[
\text{prediction}
\rightarrow
\text{avoidance}
\rightarrow
\text{small correction}
\rightarrow
\text{compensation}
\rightarrow
\text{repair}
\rightarrow
\text{replacement}
\rightarrow
\text{irreversible loss}.
\]

As the process moves rightward:

```text
cost may rise
reversibility may fall
state uncertainty may rise
available trajectories may shrink
```

Therefore:

\[
\boxed{
\text{generalized reserve resources are valuable}
\text{ but may enter after direct preservation has partly failed}
}
\]

This distinction matters for money, insurance, backup systems, emergency medicine, repair capacity, and other compensatory resources.

---

# 21. Money Is a Generalized Access and Substitution Resource

Money is often described as power or energy.

A more precise operational description is:

\[
\boxed{
\text{money expands access to socially maintained substitutions, services, resources, and delegated transformations}
}
\]

Money usually does not directly set the target variable.

Instead it can route through other capabilities:

\[
\text{money}
\rightarrow
\text{labor}
\rightarrow
\text{reduced load},
\]

\[
\text{money}
\rightarrow
\text{transport}
\rightarrow
\text{changed location},
\]

\[
\text{money}
\rightarrow
\text{equipment}
\rightarrow
\text{new physical interface},
\]

\[
\text{money}
\rightarrow
\text{expertise}
\rightarrow
\text{better diagnosis or intervention},
\]

\[
\text{money}
\rightarrow
\text{time without immediate income}
\rightarrow
\text{recovery opportunity}.
\]

Thus money is not a universal causal handle.

It is a highly fungible **access mediator** to many other handles.

Its value depends on:

```text
market availability
legal access
location
trust
service quality
time
irreversibility of the underlying loss
```

---

# 22. Delegation Changes Who Executes the Transformation

Suppose an agent cannot or does not want to perform action \(a\).

Delegation constructs:

\[
\text{agent A intent}
\rightarrow
\text{communication / contract}
\rightarrow
\text{agent B action}
\rightarrow
\text{world transition}.
\]

The original agent does not directly execute the transformation.

They invoke another controller.

This matters because another person is not merely a passive control surface.

They are an autonomous system with:

```text
their own observations
their own goals
their own capabilities
their own refusal conditions
their own models
their own errors
```

Therefore:

\[
\boxed{
\text{other agent}
\neq
\text{deterministic actuator}
}
\]

Trust, contracts, norms, communication, payment, and shared context are mechanisms for coupling controllers, not for converting a person into a writable variable.

---

# 23. Trusted Agents Can Provide Redundant Regulation

Although another person is not a control surface, a trusted autonomous agent can expand robustness.

Suppose one member of a coupled system becomes temporarily impaired.

The other may:

```text
notice the impairment
infer the missing task
act without microscopic instruction
preserve shared state
seek help
change the plan
```

This differs from money.

Money can purchase services.

A trusted agent can contribute context-sensitive autonomous regulation.

Thus:

\[
\boxed{
\text{distributed control among trusted agents}
\text{ can preserve viability when one controller temporarily loses capacity}
}
\]

The quality of the coupling matters more than the mere existence of another person.

---

# 24. Some Desired States Are Internally Generated Transitions

Not every valued outcome is an external resource.

Some are state transitions produced by the organism itself.

Examples include:

```text
sleep
relaxation
arousal
orgasm
flow
certain forms of motor coordination
```

These often cannot be commanded directly as:

```text
STATE = TRUE
```

The agent instead changes enabling conditions.

Thus:

\[
\boxed{
\text{desired internal state}
\neq
\text{directly writable variable}
}
\]

The relevant inverse problem may be underdetermined, stochastic, state-dependent, and sensitive to attempts at control.

More effort can sometimes reduce success.

This is another reason to distinguish:

```text
available energy
from
accessible control structure.
```

---

# 25. Problem Solving Is Search for Causally Relevant Degrees of Freedom

A useful problem-solving orientation can be written:

\[
\text{undesired observation}
\rightarrow
\text{candidate generators}
\rightarrow
\text{modifiable variables}
\rightarrow
\text{accessible handles}
\rightarrow
\text{intervention}
\rightarrow
\text{feedback}.
\]

The agent asks:

```text
What changed?
What could have produced this?
Which possibilities can be discriminated?
Which relevant variables are actually modifiable?
Which are modifiable only indirectly?
Which intervention is locally executable?
What side effects does it introduce?
Did the intervention work?
```

This is stronger than merely maintaining a positive mental state.

The important allocation is attention toward distinctions that can alter causal inference or action.

Thus:

\[
\boxed{
\text{problem-solving attention}
\approx
\text{attention allocated to distinctions with expected causal or control value}
}
\]

---

# 26. Search Can Be Search for Where Search Should Continue

Ordinary search assumes a search space.

But a bounded agent may not know which representation or interface contains the relevant continuation.

Then the process becomes meta-search:

```text
search file system
→ no useful handle
search editor
→ modification ineffective
search documentation
→ partial clue
search console behavior
→ discover namespace distinction
search command syntax
→ successful invocation
```

The agent is not simply moving through one fixed state graph.

It is deciding which **search surface** or **control layer** deserves further resolution.

Thus:

\[
\boxed{
\text{search may operate over candidate representations and interfaces, not only over world states}
}
\]

This suggests a hierarchy:

\[
\text{world-state search}
\subset
\text{method search}
\subset
\text{interface search}
\subset
\text{representation search}
\subset
\text{architecture search}.
\]

---

# 27. Failure Can Reveal a Missing Edge, a Wrong Edge, or a Missing Coordinate

When an action fails, several explanations are possible.

## Missing edge

The represented transition does not actually exist.

## Hidden edge

A real transition exists but is absent from the model.

## Wrong precondition

The transition exists but only under conditions not currently satisfied.

## Wrong method

The abstract operator is valid but the selected implementation is not.

## Wrong interface

The method exists but the invocation protocol is incorrect.

## Wrong representation

The model lacks a distinction necessary to explain why apparently identical cases behave differently.

Therefore:

\[
\boxed{
\text{action failure should update more than action value}
}
\]

It should update beliefs about:

```text
world structure
constraints
interfaces
methods
representations
and capability boundaries.
```

---

# 28. Intervention Discovery Requires Reversible Variation

Open-ended probing can be dangerous or expensive.

A bounded agent should therefore prefer experiments with high information value and controlled downside.

Let an exploratory intervention \(u\) have:

\[
V_{\text{info}}(u)
\]

information value,

\[
C(u)
\]

cost, and:

\[
R_{\text{irr}}(u)
\]

irreversibility risk.

A rough exploration score might be:

\[
Q(u)
=
V_{\text{info}}(u)
+
V_{\text{option}}(u)
-
C(u)
-
\lambda R_{\text{irr}}(u).
\]

High-value probes often have properties such as:

```text
cheap
reversible
local
repeatable
observable
highly discriminating
low side-effect
```

This explains the importance of:

```text
sandbox environments
test rigs
simulation
save/reload
debuggers
version control
staging systems
controlled experiments
```

They lower the cost of intervention cartography.

---

# 29. Sandboxes Are Architectures for Cheap Counterfactual Control

A sandbox is valuable because it makes many interventions:

```text
cheap
reversible
repeatable
observable
low-consequence
```

This changes the exploration economics.

Suppose an intervention in the real environment has expected downside:

\[
D_{\text{real}}(u).
\]

A sandbox may reduce it to:

\[
D_{\text{sandbox}}(u)
\ll
D_{\text{real}}(u).
\]

Then many experiments that would be irrational in production become rational in the sandbox.

Therefore:

\[
\boxed{
\text{sandbox value}
\text{ includes the value of cheaply learning intervention structure}
}
\]

This applies to games, simulation, test environments, laboratories, virtual machines, prototypes, and rehearsal spaces.

---

# 30. A Game Can Be a Generative-Control Laboratory

A game is often represented as:

```text
rules
→
objectives
→
win / lose
```

But a reusable sandbox game can instead be experienced as:

```text
physics
AI
geometry
weapons
scripts
console
mods
configuration
bugs
engine limits
level design
```

The player may repeatedly traverse the same world under altered constraints:

```text
one weapon only
fists only
left-handed control
speedrunner route
modded rules
debug commands
unusual physics interactions
self-imposed restrictions
```

These are not merely alternate routes to the same terminal objective.

They are experiments over the game's generative and controllable structure.

The repeated world becomes valuable because accumulated intervention knowledge transfers across experiments.

Thus:

\[
\boxed{
\text{replay value can come from a stable world supporting repeated causal probing under altered control constraints}
}
\]

---

# 31. Constraints Can Be Chosen to Expose Structure

A self-imposed constraint may reduce immediate performance while increasing information.

For example:

```text
use only one weapon
avoid a familiar shortcut
control with the other hand
forbid a known exploit
use a fixed resource budget
```

Why do this?

Because removing a familiar high-level operator forces the system to resolve lower-level structure.

Let:

\[
A_t^F
\]

be the ordinary feasible action set.

A self-imposed constraint produces:

\[
A_t^{F,c}
\subset
A_t^F.
\]

This may reduce short-horizon reward but expose hidden dependencies:

\[
\boxed{
\text{reduced immediate action freedom}
\text{ can increase model resolution and future method diversity}
}
\]

This is one reason drills, handicaps, restricted play, and controlled ablations can improve understanding.

---

# 32. Discovery Can Turn a World Regularity into an Operator

A raw regularity is not yet a reusable action.

The progression is:

\[
\text{observe effect}
\rightarrow
\text{repeat}
\rightarrow
\text{identify conditions}
\rightarrow
\text{make invocation addressable}
\rightarrow
\text{estimate reliability}
\rightarrow
\text{store method}
\rightarrow
\text{compose}.
\]

Suppose repeated probes reveal:

\[
C
\land
u
\Rightarrow
E
\]

with sufficient reliability.

The agent can construct an operator:

\[
O=(C,u,E).
\]

This produces:

\[
\boxed{
\text{causal discovery}
\rightarrow
\text{operator acquisition}
}
\]

when the discovered regularity is locally invocable and reusable.

Not every causal fact becomes a capability.

The critical additional properties are addressability and executability.

---

# 33. Operators Can Be Learned Before Their Future Uses Are Known

A discovered operator may have no immediate demand.

Its future value may come from fan-out.

Let:

\[
\operatorname{FanOut}(O,H)
\]

measure the expected value of methods, plans, or distinctions reachable through operator \(O\) within horizon \(H\).

Then an operator can be worth learning when:

\[
V_{\text{now}}(O)\approx 0
\]

but:

\[
\operatorname{FanOut}(O,H)\gg 0.
\]

This is option value.

Thus:

\[
\boxed{
\text{absence of an immediate goal}
\not\Rightarrow
\text{absence of rational exploration value}
}
\]

The difficulty is boundedness.

The agent cannot map every possible handle.

Exploration policy must still allocate attention selectively.

---

# 34. Control Preparedness

Preparedness can be extended from states and information to intervention structure.

Define:

\[
\rho_t(h)
\]

as the operational readiness of causal handle \(h\).

A handle may be:

```text
unknown
suspected
known but unvalidated
validated but forgotten
known but slow to retrieve
known but not currently authorized
known but requiring setup
immediately invocable
well-practiced and composable
```

Thus control preparedness is not binary.

The relevant question becomes:

> Which causal handles should remain operationally ready before demand becomes urgent?

This includes:

```text
remembering emergency procedures
maintaining tools
keeping debug access functional
retaining documentation
preserving passwords and authorization
practicing rarely used skills
keeping backups
maintaining trusted relationships
```

The common structure is readiness of intervention.

---

# 35. Intervention Prefetch

Suppose a likely future state may require handle \(h\).

If discovering or activating \(h\) only after the state becomes blocking has latency:

\[
L(h),
\]

then anticipatory preparation may be valuable.

A rough condition is:

\[
p(h)
\cdot
L_{\text{saved}}(h)
\cdot
V_{\text{future}}(h)
>
C_{\text{prepare}}(h).
\]

Call this **intervention prefetch**.

Examples include:

```text
learning the console before a hard encounter
checking rescue equipment before entering remote terrain
knowing rollback procedures before deployment
learning how to contact support before failure
rehearsing an emergency maneuver before it is required
```

This is more specific than generic preparedness.

It prepares a future control path.

---

# 36. Preserve Operational Provenance

Once a difficult handle has been discovered, discarding its invocation history can recreate the problem later.

A useful operator record should preserve more than a label.

It may include:

```text
where it was discovered
which version it applies to
required launch state
syntax
namespace
preconditions
known side effects
validation examples
failure cases
fallback methods
```

This is **operational provenance**.

Without it, the agent may retain:

```text
"there was some way to do this"
```

while losing the locally executable route.

Thus:

\[
\boxed{
\text{remembering that a capability exists}
\neq
\text{preserving how to regain or invoke it}
}
\]

Cumulative intelligence requires retention of the transition path, not merely the endpoint fact.

---

# 37. Provenance and Controllability Reinforce Each Other

Provenance tells the agent how a state or artifact came to exist.

Intervention structure tells the agent how current actions can alter future states.

These are temporal complements.

A compact view is:

\[
\boxed{
\text{provenance}
=
\text{usable structure about the past transition path}
}
\]

and:

\[
\boxed{
\text{controllability map}
=
\text{usable structure about candidate future transition paths}
}
\]

Preserving both reduces repeated inference.

The system need not rediscover:

```text
how this state was generated
or
how this transformation can be invoked
```

whenever the same structure recurs.

---

# 38. Representation Determines Which Handles Can Be Seen

A causal handle can remain invisible if the representation collapses the distinction on which it depends.

Suppose outcomes differ according to hidden context \(c\):

\[
F(x,u,c_1)
eq F(x,u,c_2).
\]

If the representation maps:

\[
c_1,c_2\mapsto c,
\]

then the action may appear unreliable or random.

The agent may conclude:

```text
this command works inconsistently
```

when the real issue is:

```text
the representation omitted a precondition.
```

Thus:

\[
\boxed{
\text{apparent stochasticity can be unresolved conditional structure}
}
\]

A representation update can convert an unreliable action into a reliable conditional operator.

---

# 39. Control Discovery Can Trigger Semantic Refinement

Suppose repeated probes produce two outcome classes:

\[
y_a,
y_b.
\]

The current ontology treats the initial states as equivalent.

Then action failure creates semantic pressure:

```text
same represented state
+ same represented action
→ different outcomes
```

The agent may need to refine the state description until:

\[
(x_a,u)\rightarrow y_a
\]

and:

\[
(x_b,u)\rightarrow y_b
\]

become conditionally predictable.

This gives a closed loop:

\[
\boxed{
\text{control failure}
\rightarrow
\text{representational refinement}
\rightarrow
\text{better conditional operator}
\rightarrow
\text{improved control}
}
\]

Thus semantic resolution and control architecture co-evolve.

---

# 40. Not Every Handle Should Be Exposed

More control is not automatically better.

A system may contain handles that are:

```text
dangerous
fragile
security-sensitive
high-maintenance
hard to validate
likely to be misused
cheap to invoke accidentally
```

An architecture may deliberately hide them behind:

```text
permissions
confirmation
namespaces
interlocks
rate limits
expert interfaces
staging environments
```

Thus:

\[
\boxed{
\text{world controllability}
\neq
\text{desirable user-facing controllability}
}
\]

Good abstraction does not expose every microscopic degree of freedom.

It exposes a robust control vocabulary appropriate to the controller and context.

---

# 41. The Smallest Useful Control Vocabulary Can Dominate Microscopic Access

Suppose one architecture exposes millions of low-level variables.

Another exposes a small number of stable, composable operations.

The second may produce greater practical reachability.

A useful objective is not:

\[
\max |U|.
\]

It is closer to:

\[
\max
\frac{
\text{useful reachable structure}
}{
\text{control complexity}
+
\text{maintenance burden}
+
\text{failure risk}
}.
\]

Thus abstraction and control discovery interact.

Exploration finds regularity.

Architecture compresses that regularity into reusable interfaces.

The next layer no longer needs to micromanage the underlying transitions.

---

# 42. Search Is Often Search for Leverage, Not Search for Location

The word **search** can mean several structurally different operations.

## Search for an object

```text
Where is X?
```

## Search for information

```text
What is true about X?
```

## Search for a route

```text
How do I get from A to B?
```

## Search for a cause

```text
What generated Y?
```

## Search for an interface

```text
How can I invoke capability C?
```

## Search for a causal handle

```text
What can I change that reliably changes the future state?
```

## Search for a new representation

```text
Which missing distinction would make the behavior predictable?
```

## Search for architecture

```text
Which new operator or interface would expand future feasible action?
```

These should not be collapsed into one generic graph traversal.

---

# 43. A General Search Stack

A bounded agent may operate through a stack such as:

```text
Level 0: execute known local action
Level 1: search among known methods
Level 2: refine an abstract operator into an executable method
Level 3: search for a missing interface or invocation protocol
Level 4: probe the environment to discover intervention structure
Level 5: refine representation to expose conditional regularity
Level 6: acquire or construct new capability
Level 7: redesign the generator of future methods
```

Failure at one level can create pressure to descend or move outward.

But the system should not descend automatically.

A useful control rule is:

\[
\boxed{
\text{refine only the layer implicated by the blocking failure}
}
\]

This prevents unnecessary microscopic search.

---

# 44. The Control-Discovery Loop

A generic intervention-discovery loop is:

```text
1. maintain current intervention map
2. observe mismatch, uncertainty, novelty, or spare exploration opportunity
3. choose a local region or mechanism worth resolving
4. generate reversible candidate probes
5. predict discriminating outcomes
6. execute a locally feasible probe
7. observe consequences
8. update causal and interface hypotheses
9. identify stable conditional regularity
10. bind it to an addressable invocation
11. validate reliability and side effects
12. retain operational provenance
13. expose as method or operator when useful
14. compose with existing methods
15. stop when additional resolution has insufficient value
```

This is neither pure planning nor pure learning.

It is architecture-building through interaction.

---

# 45. A Schematic Intervention Map

Let the agent maintain:

\[
\mathcal I_t
=
\{h_1,\ldots,h_n\}.
\]

Each handle may contain:

\[
h_i=
(
S_i,
U_i,
Y_i,
P_i,
R_i,
C_i,
L_i,
V_i,
D_i
),
\]

where:

- \(S_i\): applicability state or context,
- \(U_i\): invocation method,
- \(Y_i\): expected outcome distribution,
- \(P_i\): provenance and discovery history,
- \(R_i\): reliability,
- \(C_i\): cost,
- \(L_i\): latency,
- \(V_i\): reversibility,
- \(D_i\): dependencies and side effects.

A candidate probe \(q\) can be evaluated by:

\[
Q(q)
=
V_{\text{info}}(q)
+
V_{\text{control}}(q)
+
V_{\text{option}}(q)
+
V_{\text{representation}}(q)
-
C(q)
-
R(q).
\]

This need not be computed numerically.

It identifies the terms a bounded architecture should keep conceptually distinct.

---

# 46. Control Value and Information Value Can Diverge

A probe may have low immediate control value but high information value.

Example:

```text
press a harmless unknown button in a sandbox
```

The resulting state may not be desirable.

But the observation may reveal a whole interface family.

Conversely, an action may have high immediate control value but low information value:

```text
use a familiar shortcut that always works
```

Thus:

\[
\boxed{
V_{\text{control}}(u)
\neq
V_{\text{information}}(u)
}
\]

A mature agent allocates effort between them according to urgency, uncertainty, reversibility, and horizon.

---

# 47. A Failed Workaround Can Still Be Informative

Suppose an agent edits a parameter believed to control damage.

The system still fails.

The attempt may have zero task reward.

But it can eliminate hypotheses:

```text
wrong variable
wrong subsystem
wrong load order
wrong version
wrong target of damage
wrong file
change not applied
```

Therefore:

\[
\boxed{
\text{failed intervention}
\not\Rightarrow
\text{zero value}
}
\]

when the failure changes the causal model.

This requires preserving the attempt and its conditions.

Otherwise the same hypothesis may be tested repeatedly.

---

# 48. Cumulative Intelligence Requires More Than Facts

A system that stores only propositions may remember:

```text
this game has a debug mode
this machine has a reset function
this institution has an appeal process
this body responds to a treatment
```

But practical intelligence also needs:

```text
how to invoke it
under what conditions
how reliable it is
what it changes
what it costs
how long it takes
what can go wrong
how to verify success
```

Thus cumulative intelligence should preserve at least:

\[
\boxed{
\text{facts}
+
\text{provenance}
+
\text{interfaces}
+
\text{methods}
+
\text{conditional transition structure}
}
\]

This turns past exploration into future local executability.

---

# 49. Intelligence Can Be Viewed as Growing an Actionable World Model

A predictive world model answers:

> What is likely to happen?

An actionable world model also answers:

> What can I locally do, how can I invoke it, and what changes if I do?

This suggests:

\[
\boxed{
\text{actionable model}
=
\text{predictive structure}
+
\text{addressable intervention structure}
}
\]

The distinction is important.

A system can predict a phenomenon accurately while having no control over it.

A system can also possess a crude predictive model while having a highly reliable operational interface learned through practice.

Prediction and control overlap but are not identical.

---

# 50. World Possibility, Agent Feasibility, and Agent Discoverability

Existing frontier models distinguish world possibility from agent feasibility.

Intervention discovery adds another layer.

Let:

\[
\mathcal P
\]

be physically or institutionally possible transformations.

Let:

\[
\mathcal F_t
\subseteq
\mathcal P
\]

be transformations actually feasible for the current agent.

Let:

\[
\mathcal D_t
\subseteq
\mathcal F_t
\]

be transformations the agent currently knows how to discover, address, or invoke through its represented architecture.

Then:

\[
\boxed{
\mathcal D_t
\subseteq
\mathcal F_t
\subseteq
\mathcal P
}
\]

may hold.

A capability can be feasible in principle for the current agent yet operationally absent because the discovery or addressability route is missing.

This is an important form of **latent feasibility**.

---

# 51. Latent Feasibility

Define a transformation \(h\) as latently feasible when:

\[
h\in\mathcal F_t
\]

but:

\[
h\notin\mathcal I_t^F.
\]

The missing component may be only:

```text
knowledge
binding
syntax
attention
representation
interface state
retrieval
```

Latent feasibility differs from frontier expansion.

The agent does not need to acquire a fundamentally new external capability.

It needs to expose an already-compatible transition to its controller.

Thus:

\[
\boxed{
\text{some capability growth is the conversion of latent feasibility into explicit executability}
}
\]

This can be extremely cheap once the missing distinction is found.

---

# 52. Discovery Cost Can Dominate Execution Cost

Suppose a hidden command takes one keystroke once known.

Let:

\[
C_{\text{exec}}(h)
\]

be execution cost and:

\[
C_{\text{discover}}(h)
\]

be discovery cost.

It is possible that:

\[
C_{\text{discover}}(h)
\gg
C_{\text{exec}}(h).
\]

This pattern appears widely:

```text
finding the right API call
finding the bug
finding the correct theorem
finding the right diagnostic test
finding the correct contact person
finding the hidden configuration dependency
finding the safe physical trajectory
```

Once localized, the final intervention may be trivial.

Therefore:

\[
\boxed{
\text{difficulty of obtaining control}
\neq
\text{magnitude of the final control input}
}
\]

---

# 53. Search Effort Can Be Mostly Interface Localization

Many apparently difficult tasks may consist of:

\[
\text{large search over possible control locations}
+
\text{small final intervention}.
\]

This explains why a problem can feel impossible immediately before becoming trivial.

The world may not have changed.

The agent has crossed an epistemic-addressability threshold.

Before:

\[
\operatorname{Invoke}_t(h)=\varnothing.
\]

After:

\[
\operatorname{Invoke}_{t+1}(h)=u.
\]

The transition from unknown to known invocation can be discontinuous in practical effect.

---

# 54. Search Should Preserve Near-Misses and Dead Ends

If the agent only stores successful actions, it loses useful boundary information.

A failed probe can establish:

```text
not in this version
not through this parser
not under this launch state
not at this permission level
not with this object type
not after this sequence
```

This defines the shape of the control frontier.

Therefore a mature intervention map should preserve:

\[
\text{positive edges}
+
\text{negative evidence}
+
\text{conditions under which both were observed}.
\]

Otherwise repeated rediscovery becomes likely.

---

# 55. Negative Knowledge Can Reduce Future Search

Let candidate handles be:

\[
H=
\{h_1,\ldots,h_n\}.
\]

If a probe rules out subset:

\[
H^-\subset H,
\]

then future search occurs over:

\[
H' = H-H^-.
\]

Thus even when no new executable action is acquired:

\[
|H'|<|H|
\]

can reduce future search cost.

This gives failed experiments option value when their conditions are preserved reliably.

---

# 56. Control Architecture Is Path-Dependent

An agent's present intervention repertoire reflects accumulated history:

\[
\mathcal I_0
\rightarrow
\mathcal I_1
\rightarrow
\cdots
\rightarrow
\mathcal I_t.
\]

Each discovery can make later discoveries cheaper.

For example:

```text
learn file system
→ understand configuration locations
→ learn scripting
→ understand console commands
→ inspect engine behavior
→ create new tools
```

Thus:

\[
C(h_{t+1}\mid\mathcal I_t)
<
C(h_{t+1}\mid\mathcal I_0)
\]

may hold.

This produces compounding controllability.

---

# 57. Foundational Handles Have High Fan-Out

Some intervention capabilities expose many later actions.

Examples include:

```text
reading documentation
using a shell
using a debugger
using search
asking a knowledgeable person
measuring a variable
editing text
running a reversible experiment
using version control
```

Their value is not only the immediate action.

They alter the rate at which new handles can be found, validated, and retained.

Let:

\[
\operatorname{DiscoveryFanOut}(h,H)
\]

measure expected downstream control structure discoverable through handle \(h\).

Then foundational tools can have high value even when they do not directly satisfy current demand.

---

# 58. Some Handles Modify the Handle Generator

A particularly important class of action changes the architecture that discovers or creates future actions.

Examples include:

```text
learn programming
install instrumentation
build a debugger
learn experimental design
construct a simulator
create an API
formalize a protocol
learn a language
build a tool that generates tools
```

These are second-order capabilities.

They do not merely add one edge.

They alter the process that produces edges.

Thus:

\[
\boxed{
\text{generative capability}
>
\text{single-action capability}
}
\]

when the horizon is long enough and the maintenance cost is justified.

---

# 59. The Intervention-Structure Discovery Principle

The central principle can now be stated.

\[
\boxed{
\textbf{Intervention-Structure Discovery Principle}
}
\]

> A bounded agent should not assume that meaningful search begins only after a terminal goal and a fixed action graph are available. It may rationally explore in order to discover, localize, characterize, address, validate, and retain the causal handles from which later routes, methods, and capabilities can be constructed.

This turns exploration from generic uncertainty reduction into a more operational activity.

---

# 60. The Addressability Principle

\[
\boxed{
\textbf{Addressability Principle}
}
\]

> A transformation that exists and is compatible with the agent is not yet an operational capability unless the agent has a locally executable route that invokes it under known conditions.

Therefore:

\[
\text{existence}
\neq
\text{addressability}
\neq
\text{executability}.
\]

---

# 61. The Goal-Independence Principle

\[
\boxed{
\textbf{Goal-Independence Principle}
}
\]

> Discovery of intervention structure can have value before any specific terminal target is active, because reusable causal handles reduce future search cost, increase option value, improve causal models, and enable later composition.

This does not imply unbounded curiosity.

Exploration remains resource-constrained.

---

# 62. The Active-Probing Principle

\[
\boxed{
\textbf{Active-Probing Principle}
}
\]

> When passive observation leaves causal or interface structure ambiguous, reversible interventions can be valuable because they simultaneously test hypotheses and reveal usable transformation structure.

The preferred probe maximizes discrimination and future control value subject to cost and irreversibility.

---

# 63. The Leverage Principle

\[
\boxed{
\textbf{Control-Leverage Principle}
}
\]

> Good control should be evaluated by the causal effect of an intervention on viable future trajectories relative to its cost, not by the raw magnitude of force, energy, money, or visible effort expended.

Small correctly placed interventions can dominate large late corrections.

---

# 64. The Latent-Feasibility Principle

\[
\boxed{
\textbf{Latent-Feasibility Principle}
}
\]

> Some transformations are already compatible with the agent and world but remain unusable because the required distinction, binding, syntax, interface, or invocation route is missing from the agent's current operational representation.

Discovery can therefore expand explicit capability without changing the external world's transition structure.

---

# 65. The Operational-Provenance Principle

\[
\boxed{
\textbf{Operational-Provenance Principle}
}
\]

> When a causal handle is costly to discover, preserve not only the fact that it exists but also the locally executable path by which it can be invoked, validated, and recovered.

This turns one-time discovery into cumulative capability.

---

# 66. The Autonomous-Agent Principle

\[
\boxed{
\textbf{Autonomous-Agent Principle}
}
\]

> Another person or agent should not be modeled as a deterministic control surface. Delegation creates a coupling between controllers whose reliability depends on communication, incentives, trust, access, and independent agency.

This separates social coordination from ordinary actuation.

---

# 67. The Viable-Continuation Principle

\[
\boxed{
\textbf{Viable-Continuation Principle}
}
\]

> In many coupled systems, control quality is better represented by preservation of a viable region and future option set than by instantaneous maximization of a scalar resource or output.

This favors timely low-amplitude corrections and avoidance of irreversible boundary crossings.

---

# 68. The Cumulative-Controllability Principle

\[
\boxed{
\textbf{Cumulative-Controllability Principle}
}
\]

> Intelligence can accumulate not only predictive knowledge but also a structured library of reliable, addressable, composable interventions together with their preconditions, provenance, costs, side effects, and recovery paths.

This library changes what future planning can treat as a primitive.

---

# 69. A Compact Architecture

A system implementing these ideas could maintain:

```text
world model
represented state
feasible action frontier
intervention map
operator library
provenance store
constraint model
representation schema
preparedness state
```

A high-level loop is:

```text
observe current state
↓
update world and constraint model
↓
if current action is executable:
    continue
else if known method can be refined:
    refine method
else if known handle is unaddressable:
    recover interface / provenance
else if failure is unexplained:
    generate reversible probes
else if representation is insufficient:
    refine distinctions
else if capability is genuinely absent:
    consider frontier expansion
else:
    preserve uncertainty or revise target
↓
retain successful and failed transition evidence
↓
compile stable regularities into reusable operators
```

For open-ended exploration, the loop can also run without a blocked target:

```text
spare capacity / curiosity
↓
select high-option-value unknown region
↓
probe reversibly
↓
update intervention map
↓
retain discovered structure
```

---

# 70. Why This Is Not Just A*

A* assumes:

```text
nodes
edges
edge costs
heuristic
and target
```

Intervention-structure discovery may lack several of these.

The agent may not know:

```text
which edges exist
how an edge is invoked
whether two apparent nodes are actually distinct
whether an action is deterministic
whether the target will matter later
```

Bidirectional search can be useful after a target and transition model exist.

But the deeper problem may be to construct enough of the transition model that bidirectional search becomes meaningful.

Thus:

\[
\boxed{
\text{intervention cartography is prior to, and sometimes independent of, shortest-path search}
}
\]

---

# 71. Why This Is Not Just Inverse Kinematics

Inverse kinematics usually assumes a known mechanism:

\[
q\mapsto x.
\]

The problem is to find \(q\) for a desired \(x\).

Intervention discovery may instead ask:

```text
What are the controllable coordinates?
Which variables are coupled?
Which invocation reaches them?
What constraints define the workspace?
Does the mechanism even expose the required degree of freedom?
```

It is therefore closer to:

\[
\text{discover the joints}
+
\text{identify the kinematics}
+
\text{learn the interface}
+
\text{then solve the inverse problem}.
\]

---

# 72. Why This Is Not Just Reinforcement Learning

Reinforcement learning usually begins with some action interface, observation interface, and reward structure.

The present framework asks what happens when these are themselves incomplete or mutable.

The agent may need to discover:

```text
new actions
new action decompositions
new state variables
new interfaces
new representations
new sources of feedback
```

before ordinary reward optimization is well-posed.

Thus the architecture is not merely:

\[
\max \mathbb E[R].
\]

It includes construction of the action and representation spaces over which later optimization occurs.

---

# 73. Why This Is Not Just Affordance Detection

Affordances concern opportunities for action relative to an agent.

Intervention-structure discovery overlaps strongly with that idea.

The additional emphasis here is on:

```text
addressability
invocation protocol
operator refinement
provenance
composability
preparedness
latent feasibility
and frontier change
```

The question is not only:

> What action is afforded?

It is also:

> How does the agent discover, operationalize, retain, and compose that affordance into a growing control architecture?

---

# 74. Why This Is Not Just Causal Inference

Causal inference asks which relations are causal and how interventions would change outcomes.

The present framework adds an agent-relative operational layer.

A causal variable may be scientifically important but practically inaccessible.

For control, the agent also needs:

```text
an invocation path
current feasibility
sufficient resolution
reliability
acceptable cost
acceptable risk
```

Thus:

\[
\boxed{
\text{causal relevance}
\neq
\text{operational controllability}
}
\]

The architecture is concerned with both.

---

# 75. Why Search Sometimes Feels Like Looking for the Place Where Reality Is Writable

In software, some state is writable through:

```text
API
memory
configuration
console
filesystem
UI
network protocol
```

In physical systems, some state is writable through:

```text
force
position
heat
chemical input
electrical input
timing
geometry
```

In institutions, some transitions are writable through:

```text
application
contract
payment
permission
appeal
credential
conversation
```

In biology, direct writability is much more limited than the number of variables that exist.

Thus a recurring practical question is:

> Where does this system expose a transformation that my current architecture can actually invoke?

This can make search feel like looking for **where reality is writable from here**.

The phrase is useful if its limits are kept explicit:

```text
not everything is writable
not everything writable is safe
not everything safe is known
not everything known is addressable
not everything addressable is reliable
```

---

# 76. Control Is Always Relative to an Interface and Resolution

A person can say:

```text
move hand
```

without controlling individual motor neurons.

A programmer can say:

```text
copy folder
```

without controlling individual storage-cell transitions.

A driver can steer without controlling tire molecules.

Thus control is layered.

At one layer:

\[
u^{(k)}
\]

is a primitive.

At a lower layer it may expand into:

\[
u^{(k)}
=
\operatorname{Compose}(
u_1^{(k-1)},\ldots,\nu_m^{(k-1)}).
\]

Therefore:

\[
\boxed{
\text{primitive action}
\text{ is controller-relative, not metaphysically primitive}
}
\]

Intervention discovery can occur at any layer where the current abstraction becomes insufficient.

---

# 77. The Best Controller May Need Less Visible Intervention

A well-regulated system can appear uneventful.

The controller continuously detects small deviations and corrects them before they become large.

Let deviation be:

\[
e_t.
\]

A controller with timely feedback may maintain:

\[
|e_t|<\epsilon.
\]

A poor controller may allow:

\[
|e_t|\gg\epsilon
\]

and then require a dramatic intervention.

Thus:

\[
\boxed{
\text{large visible correction can be evidence of late control rather than strong control}
}
\]

This is important when interpreting effort, intensity, money, force, and emergency action.

---

# 78. Robustness Is Preservation of Future Action

A useful state is not merely one with high immediate utility.

It may be one from which many good future actions remain available.

Let:

\[
\mathcal R_H(x_t)
\]

be the set of useful states reachable within horizon \(H\).

A robust action may preserve or enlarge:

\[
V(\mathcal R_H(x_{t+1})).
\]

Therefore an action can be valuable because it avoids a region where:

```text
future control becomes expensive
options collapse
repair becomes irreversible
or the system terminates
```

This formalizes the intuition that staying in the lane can dominate maximizing speed.

---

# 79. The Economics of Intervention Knowledge

Control knowledge has:

```text
acquisition cost
validation cost
retention cost
reacquisition cost
maintenance cost
version sensitivity
future reuse probability
fan-out
option value
```

Let:

\[
C_{\text{learn}}(h),
C_{\text{hold}}(h),
C_{\text{refresh}}(h)
\]

be the costs of learning, retaining, and refreshing handle \(h\).

Let:

\[
p_H(h)
\]

be the probability it becomes useful within horizon \(H\).

Then preparedness policy should not retain every handle at maximum readiness.

It should allocate readiness according to expected future leverage.

---

# 80. Forgetting Can Delete Capability Without Changing the World

Suppose the world remains unchanged.

The agent forgets a syntax, procedure, or interface.

Then:

\[
\mathcal I^*
\]

is unchanged, while:

\[
\mathcal I_t^F
\]

shrinks.

Thus:

\[
\boxed{
\text{capability loss can occur entirely inside the agent's operational representation}
}
\]

This is why documentation, notes, scripts, automation, muscle memory, and maintained interfaces matter.

They externalize or stabilize addressability.

---

# 81. Automation Is Compiled Intervention Knowledge

Suppose a repeatedly rediscovered procedure is:

```text
observe condition
→ open tool
→ navigate interface
→ enter parameters
→ validate output
→ perform action
```

Automation can compress this into:

```text
invoke method()
```

The system has compiled a long causal route into a higher-level operator.

Thus:

\[
\boxed{
\text{automation}
=
\text{retained and executable compression of previously resolved intervention structure}
}
\]

The gain is not only speed.

It reduces the need to rediscover the control path.

---

# 82. Tools Externalize Control Architecture

A tool can embody:

```text
known regularities
physical leverage
measurement
protocols
error checking
stored procedures
interfaces
```

Possessing a tool therefore changes the agent's available control structure only if:

```text
the tool is accessible
the interface is understood
required resources exist
compatibility holds
and the tool itself functions
```

This gives:

\[
\boxed{
\text{tool possession}
\neq
\text{tool-assimilated capability}
}
\]

Assimilation means the tool has become integrated into a locally executable route.

---

# 83. Language Can Expose Causal Handles Indirectly

Language does not physically actuate most of the world directly.

But it can invoke socially maintained transformations:

```text
ask
instruct
request
contract
warn
teach
coordinate
query a software system
```

This gives language high fan-out as an interface layer.

A sentence can become part of a causal route when another system interprets it and acts.

Thus:

\[
\boxed{
\text{language can function as infrastructure for binding intentions to external controllers}
}
\]

Its effectiveness depends on shared schema, trust, protocol, authority, and context.

---

# 84. A Better Interpretation of “Energy” in Control Language

The word **energy** is often used to collapse several distinct things:

```text
physical energy
metabolic capacity
attention
motivation
available time
money
social support
control authority
optionality
```

These should remain distinct.

Physical energy may be necessary for action.

But useful behavior depends on how energy is organized through control structure.

A system with abundant energy and poor regulation can fail catastrophically.

A system with modest expenditure and accurate control can remain viable for long periods.

Thus:

\[
\boxed{
\text{available energy}
\neq
\text{available intervention structure}
\neq
\text{good trajectory selection}
}
\]

This separation prevents metaphor from replacing mechanism.

---

# 85. Control Resources Are Not Interchangeable

Money, physiological capacity, another person, a tool, and a learned method can all affect future reachability.

But they do so through different architectures.

```text
money
    → generalized access and substitution

physiological capacity
    → enables internal sensing, computation, and actuation

trusted person
    → autonomous coupled controller

tool
    → externalized transformation interface

learned method
    → reusable internal control routine
```

Calling all of them “energy” hides the distinctions required for planning.

---

# 86. Search Pressure Should Follow Causal Uncertainty, Not Mere Discomfort

An agent may experience a strong undesirable state.

But semantic or control elaboration should be allocated according to expected usefulness.

If the cause is already known and the intervention is clear, more causal search may be unnecessary.

If the cause is unknown and consequences are high, deeper investigation may be justified.

Thus:

\[
\boxed{
\text{subjective intensity}
\neq
\text{optimal investigation depth}
}
\]

The controller should ask where additional resolution can change action.

---

# 87. Some Problems Are Solved by Removing the Need for Control

A system does not always need a better actuator.

It can sometimes redesign the environment so the variable no longer needs active regulation.

Examples include:

```text
guard rails
mechanical stops
default-safe configuration
automatic retries
physical layout changes
simpler workflow
removing an unnecessary obligation
```

This transforms:

\[
\text{continuous control problem}
\]

into:

\[
\text{architectural constraint that prevents bad states}.
\]

Thus:

\[
\boxed{
\text{good architecture can eliminate recurring control demand}
}
\]

This is often more robust than repeatedly applying corrective effort.

---

# 88. Some Problems Are Solved by Enlarging Tolerance

Another strategy is not to control the disturbance more precisely but to enlarge the viable region.

Examples include:

```text
buffers
redundancy
savings
fault tolerance
extra time
backup capacity
error-correcting codes
multiple transport modes
```

If the original viability region is:

\[
\mathcal V_t,
\]

an architectural intervention may produce:

\[
\mathcal V_{t+1}
\supset
\mathcal V_t.
\]

This is robustness through tolerance rather than precision.

Money often plays this role indirectly by funding buffers and substitutions.

---

# 89. Precision, Redundancy, and Substitution Are Different Control Strategies

A robust architecture may combine:

## Precision

Correct small deviations early.

## Redundancy

Maintain another component that can continue when one fails.

## Substitution

Replace an unavailable transformation with another route.

## Tolerance

Allow a larger disturbance without leaving the viable region.

## Repair

Restore function after partial failure.

## Replacement

Replace a failed component.

These should not be collapsed into one scalar resource.

They occupy different causal positions.

---

# 90. Search for Handles Can Be a General Theory of “Figuring Things Out”

A large class of practical reasoning can be described as:

```text
something is possible or desired
but the locally executable route is unknown
```

The agent then searches for:

```text
a distinction
a cause
a method
a handle
an interface
a permission
a tool
a person
a representation
a sequence
```

that closes the gap.

This suggests a compact interpretation:

\[
\boxed{
\text{figuring something out}
\approx
\text{constructing enough actionable structure to make continuation locally executable}
}
\]

The result may be a route to a target.

But it may also simply be a better map of what can be done.

---

# 91. A More General Definition of Exploration

Exploration can now be defined without assuming a fixed target or action graph:

\[
\boxed{
\text{exploration}
=
\text{locally executable interaction undertaken partly for the expected value of changing the agent's future representation, intervention map, or option set}
}
\]

This includes:

```text
information gathering
causal probing
interface discovery
constraint discovery
operator discovery
representation refinement
option creation
```

The common feature is that the action changes what future reasoning or action can rely on.

---

# 92. A More General Definition of Search

Search can be understood as allocation of bounded effort over candidate continuations in a space that may itself be incomplete or mutable.

The object being searched may be:

\[
\text{state}
\]

or:

\[
\text{route}
\]

or:

\[
\text{cause}
\]

or:

\[
\text{interface}
\]

or:

\[
\text{representation}
\]

or:

\[
\text{operator}
\]

or:

\[
\text{architecture}.
\]

Thus:

\[
\boxed{
\text{search is not one algorithmic object merely because the same word is used}
}
\]

The search space and termination criterion must be made explicit.

---

# 93. The Deepest Recurring Pattern

Across games, software, machines, bodies, organizations, tools, languages, and physical environments, a recurring progression is:

\[
\boxed{
\text{world regularity}
\rightarrow
\text{noticed distinction}
\rightarrow
\text{active probe}
\rightarrow
\text{causal localization}
\rightarrow
\text{addressable handle}
\rightarrow
\text{validated operator}
\rightarrow
\text{composition}
\rightarrow
\text{higher-level capability}
\rightarrow
\text{expanded future search and control}
}
\]

The agent does not merely travel through a pre-existing graph.

It gradually learns which edges exist, which edges it can invoke, how those edges are conditioned, and how to compile recurring edge structures into higher-level methods.

---

# 94. From Search to Cumulative Controllability

The strongest interpretation is therefore not:

```text
intelligence = finding shortest routes to predefined goals
```

but something broader:

\[
\boxed{
\text{cumulative intelligence}
=
\text{the preservation and refinement of structures that make future distinctions, interventions, and compositions cheaper, more reliable, and more locally executable}
}
\]

This includes predictive knowledge.

But it also includes:

```text
where control enters
how control is invoked
which conditions matter
which interventions are reversible
which interfaces are trustworthy
which actions compose
which failures invalidate the model
which provenance prevents rediscovery
```

A mature system therefore accumulates not merely answers.

It accumulates **ways of making reality answerable and alterable from its current state**.

---

# 95. Final Synthesis

The ordinary planning picture begins too late.

It begins after the agent has:

```text
a state representation
a target
an action set
a transition model
and executable interfaces
```

But bounded agents often face a prior architectural problem.

They inhabit a world containing more distinctions and more causal structure than they can represent or control.

They must discover which transformations are:

```text
real
agent-compatible
locally addressable
reliably invocable
safe enough to test
worth retaining
and composable with existing methods
```

This makes intervention-structure discovery a distinct object.

The central separation is:

\[
\boxed{
\text{world possibility}
\neq
\text{agent feasibility}
\neq
\text{represented controllability}
\neq
\text{local executability}
}
\]

The central process is:

\[
\boxed{
\text{probe}
\rightarrow
\text{discover}
\rightarrow
\text{localize}
\rightarrow
\text{address}
\rightarrow
\text{validate}
\rightarrow
\text{retain}
\rightarrow
\text{compose}
}
\]

And the central architectural consequence is:

\[
\boxed{
\text{the action graph should not be treated as fixed when the agent can still discover, expose, refine, or construct the handles from which its future edges are generated}
}
\]

A fixed goal is therefore only one source of pressure.

Another is open-ended interest in the structure of controllability itself.

A sandbox player who wanders, tests physics, changes constraints, studies scripts, reproduces tricks, opens hidden interfaces, and deliberately explores states outside the intended progression is not necessarily failing to pursue the game's objective.

They may be engaged in a different activity altogether:

\[
\boxed{
\text{mapping the generative and controllable structure of a world}
}
\]

That map can later support goals.

But its value is not exhausted by any one goal.

It is reusable infrastructure for future reasoning, experimentation, play, repair, adaptation, and control.
