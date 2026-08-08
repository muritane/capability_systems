# From Questions to Composable Interfaces: Sufficiency, Factorization, Shared State, and Scalable Architecture

## Abstract

A system cannot expose every microscopic detail of its realization, nor can an interface anticipate every question that any future consumer might ask.

Useful architecture therefore requires selective representation.

The central problem is not simply:

> Which internal variables should be exposed?

It is:

> Which distinctions must survive an interface so that the intended family of downstream questions remains answerable, while the producing system exposes only what it can reliably observe, classify, and guarantee?

This yields a general architectural sequence:

\[
\boxed{
\begin{aligned}
&\text{underlying system state}\\
&\rightarrow \text{measurement and classification}\\
&\rightarrow \text{shared architectural state}\\
&\rightarrow \text{question-relative representations}\\
&\rightarrow \text{capability preconditions and margins}\\
&\rightarrow \text{decisions and controlled transitions}\\
&\rightarrow \text{higher-level capabilities}.
\end{aligned}
}
\]

The same pattern appears in resource monitors, diagnostics, lifecycle systems, robotics middleware, orchestration frameworks, standardized protocols, health models, layered software, and learned representations.

The important distinction is not fundamentally between “functional” and “realization” variables.

A battery state may be a realization condition for navigation, a functional input for energy management, and a diagnostic output for maintenance.

The more general distinction is between:

```text
state distinctions available in the system
and
state distinctions required by a selected family of downstream questions
```

A good interface preserves the latter without unnecessarily exposing the former.

This document develops that principle through question families, equivalence classes, capability-conditioned constraints, shared interfaces, recursive factorization, composability, hierarchy, and minimal sufficient representations.

---

## 1. The Architectural Problem Is Selective Distinctness

Suppose the detailed state of a system is:

\[
x\in X.
\]

The state may include:

```text
sensor readings
controller states
battery state
CPU load
temperature
memory pressure
joint positions
network state
task state
component lifecycle state
physical wear
environmental conditions
```

No useful architecture normally exposes all of \(X\).

Instead, it constructs a representation:

\[
q:X\rightarrow Z.
\]

The representation deliberately merges many states.

If:

\[
q(x)=q(y),
\]

then the interface is declaring that the distinction between \(x\) and \(y\) is irrelevant for the consumers that are expected to use \(Z\).

This immediately raises the central question:

> Irrelevant for which questions?

An abstraction cannot be judged independently of the decisions it is meant to support.

---

## 2. Question Families Define Relevant Distinctions

Let:

\[
\mathcal Q=\{Q_1,Q_2,\ldots,Q_k\}
\]

be a family of downstream questions.

Examples for a battery subsystem might include:

```text
Can navigation start?
Can manipulation start?
Can the robot return home?
How much task time remains?
Should charging be scheduled?
Which of several tasks is feasible?
```

A representation:

\[
q:X\rightarrow Z
\]

is sufficient for \(\mathcal Q\) when every relevant question can be answered from \(q(x)\).

That is, for every:

\[
Q_i\in\mathcal Q,
\]

there exists some function:

\[
g_i:Z\rightarrow Y_i
\]

such that:

\[
Q_i(x)=g_i(q(x))
\]

or, for noisy and approximate systems,

\[
Q_i(x)\approx g_i(q(x)).
\]

This is the essential sufficiency condition.

The representation is not required to reconstruct \(x\).

It is required to preserve the distinctions needed to answer the selected questions.

---

## 3. Question-Relative Equivalence

The question family induces an equivalence relation on the original state space.

Define:

\[
x\sim_{\mathcal Q}y
\]

when:

\[
Q(x)=Q(y)
\qquad
\text{for all }Q\in\mathcal Q.
\]

States in the same equivalence class are indistinguishable with respect to the selected questions.

The ideal compression therefore resembles the quotient:

\[
X/{\sim_{\mathcal Q}}.
\]

The abstraction should merge states that no relevant downstream question needs to distinguish.

This yields a general principle:

\[
\boxed{
\text{A useful abstraction preserves question-relevant distinctness.}
}
\]

This is stronger than saying that an abstraction “hides detail.”

It states which detail may legitimately be hidden.

---

## 4. Boolean State Is Not Inferior to Continuous State

Suppose battery state of charge is:

\[
s\in[0,1].
\]

A task \(t\) has a required reserve:

\[
r(t)\in[0,1].
\]

Define:

\[
c_{\text{battery}}(t,s)=r(t)-s.
\]

Then:

\[
\operatorname{battery\_okay}(t,s)
\iff
c_{\text{battery}}(t,s)\le0.
\]

Equivalently:

\[
\operatorname{battery\_okay}(t,s)
=
\mathbf 1[s\ge r(t)].
\]

If the downstream question is only:

> May task \(t\) start?

then the Boolean value:

```text
true
false
```

may be a perfectly sufficient representation.

The states:

\[
s=0.51,\quad s=0.72,\quad s=0.94
\]

need not remain distinct if they all produce the same answer to every relevant question.

Therefore:

\[
\boxed{
\text{more numerical precision does not automatically mean a better abstraction.}
}
\]

The correct representation is the least detailed one that remains sufficient for the intended decisions.

---

## 5. Measurement, Margin, and Decision Are Different Interface Levels

For the same battery example, several representations are possible.

### Measurement

\[
SOC=0.37.
\]

### Capability-relative margin

\[
m(t)=SOC-r(t).
\]

### Decision

\[
\operatorname{battery\_okay}(t)=
\mathbf 1[m(t)\ge0].
\]

These can be organized as:

\[
SOC
\rightarrow
SOC-r(t)
\rightarrow
\{0,1\}.
\]

Each stage discards distinctions.

The correct stage to expose depends on the question family.

If consumers ask only:

```text
Can task t begin?
```

the Boolean may be enough.

If consumers ask:

```text
Which task has the largest reserve?
How much more work can be scheduled?
How close are we to the boundary?
```

then the margin may be required.

If consumers ask:

```text
How should future tasks be planned?
How quickly is the battery depleting?
What charging strategy should be used?
```

then SOC, discharge rate, temperature, health, or additional variables may be required.

The issue is therefore not:

```text
continuous good
Boolean bad
```

but:

```text
which distinctions are necessary for the selected downstream questions?
```

---

## 6. Constraints Should Be Capability-Relative

An operating constraint is often written:

\[
c_j(x)\le0.
\]

But many practical constraints depend on which capability is requested.

A more useful form is:

\[
c_j(K,x)\le0,
\]

where \(K\) denotes the capability.

For navigation:

\[
c_{\text{battery}}(K,x)
=
SOC_{\text{required}}(K)-SOC(x).
\]

For localization:

\[
c_{\text{loc}}(K,x)
=
L_{\text{required}}(K)-L(x).
\]

For temperature:

\[
c_{\text{thermal}}(K,x)
=
T(x)-T_{\max}(K).
\]

The capability-relative admissible region becomes:

\[
\Omega_K
=
\left\{
x:
c_j(K,x)\le0
\text{ for all relevant }j
\right\}.
\]

Then:

\[
K\text{ is currently admissible}
\iff
x\in\Omega_K.
\]

A higher-level Boolean can itself summarize the entire conjunction:

\[
q_K(x)
=
\mathbf1[x\in\Omega_K].
\]

This gives a hierarchy:

\[
x
\rightarrow
(c_1,\ldots,c_n)
\rightarrow
\text{margins}
\rightarrow
\text{ready/not ready}.
\]

---

## 7. Noise Produces Boundary Regions, Not Merely Exact Boundaries

In mathematical descriptions, a constraint may appear as:

\[
c(x)\le0.
\]

Real systems usually contain:

```text
sensor noise
estimation error
delayed observations
model error
quantization
floating-point approximation
environmental variation
unmodeled disturbances
```

Therefore a boundary should often be treated as a region of uncertainty rather than an infinitely precise separator.

A simple representation is:

\[
c(x)\le-\epsilon
\]

for comfortably admissible states,

\[
-\epsilon<c(x)<\epsilon
\]

for uncertain or boundary states,

and:

\[
c(x)\ge\epsilon
\]

for clearly inadmissible states.

More generally, the margin may depend on uncertainty:

\[
c(x)+\epsilon(x)\le0.
\]

Or the decision may be probabilistic:

\[
P(c(X)\le0\mid y)\ge p_{\text{required}},
\]

where \(y\) denotes the observations.

The important point is not that continuous representations are inherently superior.

It is that an interface should preserve whatever uncertainty information downstream decisions actually require.

---

## 8. Functional and Realization State Are Roles, Not Permanent Categories

Consider:

```text
/cmd_vel
/joint_states
/battery_state
/diagnostics
/controller_state
/localization_status
/cpu_load
```

It is tempting to classify some as “functional” and others as “realization” variables.

But the classification changes with the capability being analyzed.

For navigation:

```text
battery state
controller state
localization status
```

may be enabling conditions.

For energy management:

```text
battery state
```

is a principal functional variable.

For diagnostics:

```text
CPU temperature
controller state
battery health
```

are direct functional inputs.

Therefore:

\[
\boxed{
\text{functional versus realization is capability-relative semantic role, not intrinsic variable type.}
}
\]

Once a condition is exposed through an architectural interface, it participates in the same larger state space as task state, command state, and service state.

---

## 9. Shared Architectural State

A mature system often promotes important support conditions into a shared architectural state space:

\[
Z_A=
\{
\text{task state},
\text{resource state},
\text{component state},
\text{health state},
\text{dependency state},
\text{environment state}
\}.
\]

Different capabilities consume different projections:

\[
q_K:Z_A\rightarrow Z_K.
\]

For navigation:

\[
Z_{\text{nav}}
=
(
\text{controller active},
\text{localization valid},
\text{map available},
\text{battery adequate},
\text{sensors healthy}
).
\]

For diagnostics:

\[
Z_{\text{diag}}
=
(
\text{temperature},
\text{battery health},
\text{packet loss},
\text{controller state},
\text{storage pressure}
).
\]

The shared architectural state is not a requirement that every component understand every field.

It is a common representational substrate from which different components can select the distinctions they require.

---

## 10. Explicit State Replaces Implicit Assumptions

A weak architecture may implicitly assume:

```text
controller probably started
battery is probably sufficient
network is probably reachable
dependencies probably initialized
```

A stronger architecture promotes those assumptions into named state:

```text
controller_state = active
battery_state = available
network_state = reachable
dependency_state = configured
```

A still stronger architecture attaches transition rules:

```text
navigation may activate only if:
    controller_state == active
    localization_state == valid
    map_state == available
    battery_policy(navigation) == satisfied
```

The progression is:

\[
\boxed{
\text{implicit dependency}
\rightarrow
\text{observable state}
\rightarrow
\text{named interface}
\rightarrow
\text{declared precondition}
\rightarrow
\text{managed transition}.
}
\]

Resource monitors, diagnostics, lifecycle nodes, readiness checks, controller states, and orchestration systems are implementations of this general pattern.

---

## 11. Shared Interfaces Reduce Pairwise Semantic Coupling

Suppose \(n\) component types each communicate through custom pairwise protocols.

The number of possible component pairs grows as:

\[
\frac{n(n-1)}{2}.
\]

A system does not necessarily implement every pair.

However, architecture based primarily on bespoke pairwise semantics tends toward increasing integration complexity as component diversity grows.

A shared interface changes the problem.

Instead of:

\[
C_i\leftrightarrow C_j
\]

requiring a new semantic contract for many pairs, components conform to:

\[
C_i\rightarrow I\leftarrow C_j,
\]

where \(I\) is a shared interface or vocabulary.

The runtime communication graph may still contain many edges.

The important reduction is in the number of distinct integration semantics.

This is the role played by mechanisms such as:

```text
message definitions
service definitions
action definitions
resource schemas
lifecycle conventions
health models
common units
standard status codes
standardized coordinate conventions
```

The interface makes independent composition possible without requiring every component to know every other component in advance.

---

## 12. Syntax, Semantics, and Orchestration Must Be Distinguished

A shared architecture normally contains at least three layers.

### Syntax and representation

What fields exist?

What are their types?

How are they serialized?

### Semantic contract

What does:

```text
ACTIVE
READY
SOC
temperature
pose
failed
```

actually mean?

What units, frames, timing assumptions, validity conditions, and guarantees apply?

### Orchestration

Given those shared states, which transitions are allowed?

For example:

\[
A\land B\land\neg C
\Rightarrow
\operatorname{activate}(D).
\]

A shared interface does not itself perform orchestration.

It makes orchestration tractable because components can be observed and controlled through compatible contracts.

---

## 13. A Good Protocol Is Not Universally General

There are two opposite interface failures.

### Too narrow

```text
The interface cannot represent distinctions required by its target component family.
```

Consequences include:

```text
private extensions
parallel proprietary interfaces
special-case adapters
semantic ambiguity
```

### Too broad

```text
The interface attempts to represent every possible distinction.
```

Consequences include:

```text
large schemas
high implementation burden
ambiguous semantics
irrelevant fields
increased coupling
slow evolution
```

A useful protocol is therefore not maximally expressive.

It is minimally sufficient for a selected interoperability domain.

A conceptual optimization is:

\[
I^*
=
\arg\min_I
\operatorname{Complexity}(I)
\]

subject to:

\[
\operatorname{Sufficient}(I,\mathcal Q)
\]

and:

\[
\operatorname{Implementable}(I,\mathcal C),
\]

where \(\mathcal C\) is the target component family.

---

## 14. The Producer and Consumer Must Meet in the Middle

Interface design has two directions.

From the producing system:

\[
\text{underlying state}
\rightarrow
\text{what can be observed and guaranteed}.
\]

From downstream systems:

\[
\text{questions and decisions}
\rightarrow
\text{which distinctions are required}.
\]

The interface must satisfy both.

Let:

\[
m:X\rightarrow M
\]

represent the measurements or classifications the current system can actually provide.

Let:

\[
\mathcal Q
\]

be the downstream question family.

We seek:

\[
q:M\rightarrow Z
\]

such that:

\[
Q_i(x)
\approx
g_i(q(m(x)))
\]

for all relevant \(Q_i\).

Among sufficient candidates, we prefer representations that avoid unnecessary complexity.

Thus:

\[
\boxed{
\text{interface design is a negotiation between achievable guarantees and required distinctions.}
}
\]

This is a more exact form of KISS.

---

## 15. KISS as Minimal Sufficient Representation

“Keep it simple” is often too vague to guide interface design.

A more operational form is:

> Expose no distinction without a downstream reason, and omit no distinction required by the intended downstream decisions.

This can be represented as:

\[
\min_q
\operatorname{Complexity}(q)
\]

subject to:

\[
\operatorname{Sufficient}(q,\mathcal Q)
\]

and:

\[
\operatorname{Realizable}(q,\text{producer}).
\]

Simplicity is therefore not identical to:

```text
few fields
few message types
Boolean instead of float
small source code
```

A one-field interface may be too coarse.

A twenty-field interface may be exactly sufficient.

The relevant notion of simplicity is:

\[
\boxed{
\text{minimum unnecessary distinction for the required capability family.}
}
\]

---

## 16. Hierarchy Is Factorization

Suppose several capabilities share an intermediate computation:

\[
K_1(x)=f_1(g(x)),
\]

\[
K_2(x)=f_2(g(x)),
\]

\[
K_3(x)=f_3(g(x)).
\]

A flat design independently realizes:

\[
f_1\circ g,
\qquad
f_2\circ g,
\qquad
f_3\circ g.
\]

A factorized design realizes:

\[
x\rightarrow g(x)
\]

once as a reusable intermediate representation, then:

\[
g(x)
\rightarrow
\begin{cases}
f_1\\
f_2\\
f_3.
\end{cases}
\]

This gives a general criterion for a useful architectural layer:

\[
\boxed{
\text{An intermediate representation is valuable when many downstream capabilities factor through it.}
}
\]

The representation may be:

```text
joint state
pose
battery state
component readiness
filesystem abstraction
network socket
container resource
database relation
standard message
learned feature vector
```

The important property is reusable factorization.

---

## 17. The Building Analogy

A building does not normally reconstruct a new foundation independently for every higher floor.

A first floor exports reusable guarantees:

```text
load-bearing structure
electrical service
water
waste removal
access
fire boundaries
```

A second residential floor can build on those guarantees.

Conceptually:

\[
\text{ground}
\rightarrow
F_1
\rightarrow
F_2
\rightarrow
F_3.
\]

This is efficient because higher levels factor through already realized structure.

But reuse is conditional.

If a new floor requires a capability outside the guarantees of the existing structure, reuse may fail.

For example:

```text
residential floor
```

may fit existing structural guarantees, while:

```text
heavy vehicle garage
```

may not.

Then possible responses include:

```text
strengthen the existing layer
add another load path
bypass part of the abstraction
create a separate structure
change the higher-level requirement
```

Therefore hierarchy does not mean:

> Every new capability must use every existing layer.

It means:

> Reuse an existing layer when its exported guarantees are sufficient for the new capability.

---

## 18. Bypass Is Legitimate When the Interface Is Insufficient

Let a layer expose:

\[
q:X\rightarrow Z.
\]

A higher capability \(K\) can use \(q\) when:

\[
K=f\circ q
\]

for some \(f\).

If no such suitable \(f\) exists because \(q\) discarded a distinction required by \(K\), then \(K\) cannot factor through that interface.

This is not automatically an architectural failure.

Possible responses are:

```text
enrich q
create q'
allow a specialized bypass
construct a different component family
```

The mistake is not bypass itself.

The mistake is forcing a capability through an abstraction that cannot preserve the distinctions it requires.

---

## 19. Recursive Architecture

A mature architecture can therefore be represented recursively:

\[
X_0
\xrightarrow{q_1}
X_1
\xrightarrow{q_2}
X_2
\xrightarrow{q_3}
\cdots
\xrightarrow{q_n}
X_n.
\]

Each mapping:

\[
q_i:X_{i-1}\rightarrow X_i
\]

does several things:

```text
suppresses distinctions
preserves selected distinctions
creates new named state
defines new compositional possibilities
provides reusable guarantees
reduces downstream dependence on lower-level detail
```

A variable that is “realization detail” at one level may become ordinary functional state at the next.

For example:

```text
cell voltages
→ battery state

encoder transitions
→ joint position

packet exchanges
→ connection state

process internals
→ lifecycle state
```

The boundary between function and realization therefore moves recursively.

---

## 20. Neural Networks Provide a Useful but Limited Analogy

A neuron commonly computes:

\[
h(x)=\sigma(w^\top x+b).
\]

The affine term:

\[
c(x)=w^\top x+b
\]

defines a boundary:

\[
c(x)=0.
\]

A hard-threshold neuron would classify which side of the boundary contains \(x\).

A ReLU or sigmoid preserves a graded transformation around that boundary.

Multiple neurons create an intermediate representation:

\[
h_1=q_1(x).
\]

The next layer operates on that new state space:

\[
h_2=q_2(h_1).
\]

Thus:

\[
x
\rightarrow h_1
\rightarrow h_2
\rightarrow\cdots\rightarrow y
\]

is another form of recursive representation.

The useful analogy is not that neurons literally implement system operating constraints.

It is that successive transformations create intermediate state spaces in which downstream distinctions may become easier or more economical to express.

---

## 21. Universal Representation Does Not Remove Realization Cost

A mathematically expressive mapping can hide arbitrary complexity.

For any subset:

\[
S\subseteq X,
\]

one may formally define:

\[
c(x)=
\begin{cases}
-1,&x\in S,\\
+1,&x\notin S.
\end{cases}
\]

Then:

\[
S=\{x:c(x)\le0\}.
\]

But this says nothing about whether \(c\) is:

```text
easy to compute
easy to learn
easy to observe
robust to noise
small enough to store
fast enough to evaluate
composable with other systems
```

Therefore:

\[
\boxed{
\text{mathematical representability does not imply practical realizability.}
}
\]

A useful architecture is concerned with efficient and reliable factorization, not merely existence of some formal mapping.

---

## 22. Shared Interfaces and Learned Latent Representations Differ

A learned hidden representation might be:

\[
h=(0.17,-2.31,0.82,\ldots).
\]

A downstream trained layer may know how to consume it.

But an independently designed component normally does not know what those coordinates mean.

A standardized interface deliberately stabilizes semantics:

```text
pose
joint_state
battery_state
READY
ACTIVE
temperature
```

Thus there is a spectrum:

\[
\text{raw state}
\rightarrow
\text{learned latent representation}
\rightarrow
\text{stabilized shared interface}.
\]

Learned representations may provide flexible internal factorization.

Standardized interfaces provide interoperability between independently developed components.

The architectural problem is not solved merely by compressing state.

The compressed state must also carry a sufficiently stable contract when independent composition is required.

---

## 23. Composability Requires More Than Matching Dimensions

Suppose:

\[
f_1:X\rightarrow Z
\]

and:

\[
f_2:Z\rightarrow Y.
\]

Then:

\[
f_2\circ f_1
\]

is mathematically type-compatible.

But real composability requires more.

The consumer may assume:

```text
units
coordinate frame
distribution
sampling rate
timing guarantees
error bounds
valid state range
lifecycle state
semantic meaning
```

Therefore:

\[
\boxed{
\text{matching representation shape does not imply semantic compatibility.}
}
\]

A reusable interface needs both:

\[
\text{representation compatibility}
\]

and:

\[
\text{contract compatibility}.
\]

---

## 24. Orchestration Is Question Evaluation Plus Controlled Transition

Once shared state and capability predicates exist, orchestration can be described as evaluation followed by transition.

Suppose:

\[
z\in Z_A
\]

is shared architectural state.

A capability has an admissibility predicate:

\[
P_K(z)\in\{0,1\}.
\]

If:

\[
P_K(z)=1,
\]

the orchestrator may request a transition:

\[
z' = F_K(z,u).
\]

The transition must then be observed and classified:

```text
requested
accepted
in progress
succeeded
degraded
failed
rolled back
```

Thus orchestration is not merely:

```text
start component
```

but:

\[
\boxed{
\text{evaluate preconditions}
\rightarrow
\text{request transition}
\rightarrow
\text{observe result}
\rightarrow
\text{update shared state}.
}
\]

Lifecycle frameworks and controller state machines are concrete realizations of this pattern.

---

## 25. The Question Family Itself Is an Architectural Assumption

The sufficiency of an interface depends on:

\[
\mathcal Q.
\]

If the question family changes, the abstraction may become insufficient.

Suppose an interface exposes only:

```text
battery_okay(task) -> bool
```

This may support:

```text
Can task t start?
```

But later the system must answer:

```text
Which of five tasks has the largest reserve?
How much additional work can be scheduled?
What is the expected time to recharge?
```

The original Boolean interface may no longer suffice.

Therefore a system should make explicit, at least conceptually:

```text
which questions an interface is intended to support
which questions it deliberately does not support
```

This is analogous to documenting:

```text
validity range
performance envelope
supported operations
failure semantics
```

---

## 26. Question Families Cannot Be Universal Either

One might attempt to design an interface that preserves enough state to answer every possible future question.

That defeats compression.

If:

\[
\mathcal Q
\]

contains every possible question about \(X\), then the only universally sufficient representation may approach the original state itself.

Therefore abstraction requires a deliberate restriction of the question family.

The design problem is not:

> Preserve everything that might ever matter.

It is:

> Preserve the distinctions reasonably expected to matter for the intended capability family and evolution horizon.

This is another form of KISS.

---

## 27. Robust Interfaces Often Need Layering

A single perfect interface is often unnecessary.

Instead:

```text
low-level measurements
        ↓
resource and health state
        ↓
capability-relative margins
        ↓
readiness predicates
        ↓
task-level orchestration
```

Different consumers can stop at different levels.

For example:

\[
\text{cell measurements}
\rightarrow
SOC
\rightarrow
battery\_margin(task)
\rightarrow
battery\_okay(task).
\]

A diagnostics process may consume cell measurements.

A planner may consume SOC.

A capability manager may consume battery margin.

A lifecycle orchestrator may consume only the Boolean predicate.

This preserves modularity without forcing every consumer to handle the richest representation.

---

## 28. Over-Engineering and Under-Engineering

### Under-engineering

An interface is too coarse when states with materially different downstream consequences are merged.

Example:

```text
battery_okay = true
```

when downstream planning must distinguish:

```text
12 minutes remaining
120 minutes remaining
```

### Over-engineering

An interface is too fine when consumers are forced to depend on distinctions irrelevant to their questions.

Example:

```text
individual cell ADC samples
```

when the consumer only needs:

```text
enough energy to finish navigation
```

The desired design lies between them:

\[
\boxed{
\text{preserve enough distinction to support the intended questions, but no more than necessary at that boundary.}
}
\]

---

## 29. A Practical Interface Design Procedure

For a candidate architectural boundary, ask:

```text
1. Which producing subsystem owns the state?

2. What underlying state can it actually observe?

3. What can it reliably classify or guarantee?

4. Which downstream components will consume the interface?

5. Which concrete questions must those consumers answer?

6. Which distinctions in the source state change the answers to those questions?

7. Which distinctions do not change any relevant answer?

8. Can the required distinctions be represented by a smaller summary?

9. Should the interface expose measurement, margin, predicate, or several layers?

10. Which units, timing rules, frames, validity ranges, and error semantics must be standardized?

11. What capability-specific parameters should remain with the consumer, and which should belong to the producer?

12. Which preconditions and transition results should become explicit state?

13. Can multiple downstream capabilities factor through the same representation?

14. Which specialized capabilities cannot factor through it?

15. Should those capabilities enrich the interface, use another interface, or bypass the layer?

16. What uncertainty or margin information is required near boundaries?

17. What question family is explicitly unsupported?

18. How will the interface evolve when the question family changes?
```

This procedure derives interfaces from actual architectural needs rather than from arbitrary availability of measurements.

---

## 30. Failure Modes

### Question-family omission

The interface is designed without specifying which downstream questions it must support.

### Overexposure

Large amounts of internal state are exported without a consumer requirement.

### Premature collapse

A rich state is reduced to a Boolean before downstream consumers have finished making distinctions.

### Semantic underspecification

Fields are structurally defined but their meaning, units, timing, validity, or failure semantics are ambiguous.

### Pairwise protocol proliferation

Components repeatedly create private integration semantics instead of factoring through a reusable shared interface.

### Universal-interface overreach

One protocol attempts to include every conceivable component and use case.

### Invalid reuse

A higher-level capability is forced through an interface whose guarantees are insufficient for it.

### Unnecessary bypass

A new capability reconstructs lower-level state even though an existing interface already preserves all required distinctions.

### Hidden preconditions

Capability availability depends on state that is neither exposed nor included in transition rules.

### Boundary overconfidence

A hard decision is exposed without sufficient representation of measurement uncertainty or operational margin.

### Question drift

The downstream question family changes while the interface remains frozen and silently becomes insufficient.

### Representation without contract

Components exchange compatible shapes but disagree about semantic meaning.

---

## 31. Central Principles

### Question-Relative Sufficiency Principle

> An interface is sufficient only relative to the family of downstream questions it is intended to support.

### Relevant-Distinctness Principle

> States may be merged when no relevant downstream question requires them to remain distinct.

### Minimal Representation Principle

> Prefer the least detailed representation that remains sufficient for the intended decisions and can be reliably produced.

### Producer–Consumer Principle

> Interface design must reconcile what the producer can observe and guarantee with what consumers must distinguish.

### Capability-Relative Constraint Principle

> Operational constraints should be parameterized by the capability whose admissibility they determine when their thresholds depend on that capability.

### Layered Representation Principle

> Measurement, margin, predicate, and task-level readiness are different abstraction levels and may all be useful to different consumers.

### Shared-Interface Principle

> Common interfaces reduce the need for bespoke pairwise semantic contracts and make independent composition more tractable.

### Semantic Contract Principle

> Shared structure alone is insufficient; reusable interfaces require stable meaning, units, timing, validity, and failure semantics.

### Factorization Principle

> An intermediate representation is architecturally valuable when many downstream capabilities can factor through it.

### Conditional Reuse Principle

> Existing layers should be reused when their exported guarantees are sufficient for the new capability, not merely because they already exist.

### Legitimate Bypass Principle

> A capability may bypass or extend an existing abstraction when the abstraction discarded distinctions required by that capability.

### Question-Family Limitation Principle

> No useful finite abstraction should be expected to answer every possible future question.

### Recursive Promotion Principle

> State that is implementation detail at one level may become ordinary functional state at the next when it is promoted into an explicit shared interface.

### Controlled-Orchestration Principle

> Orchestration consists of evaluating explicit preconditions, requesting transitions, observing their outcomes, and updating shared architectural state.

---

## 32. A More General Architectural Sequence

The resulting architecture can be summarized as:

\[
\boxed{
\begin{aligned}
&\text{underlying state }X\\
&\xrightarrow{\text{measurement}}
\text{observable state }M\\
&\xrightarrow{\text{classification / compression}}
\text{shared representation }Z\\
&\xrightarrow{\text{capability-relative projection}}
\text{required distinctions }Z_K\\
&\xrightarrow{\text{constraint evaluation}}
\text{margins and predicates}\\
&\xrightarrow{\text{orchestration}}
\text{controlled transition}\\
&\xrightarrow{\text{observation}}
\text{updated shared state}\\
&\xrightarrow{\text{factorization and reuse}}
\text{higher-level capability}.
\end{aligned}
}
\]

At every boundary, the same question recurs:

> Which distinctions must survive so that the intended downstream questions remain answerable?

---

## 33. Conclusion

Architecture is not primarily the exposure of more state.

It is the disciplined selection of state.

A system begins with more detail than any consumer can or should use.

Measurements classify part of that detail.

Interfaces stabilize selected classifications.

Capabilities interpret those interfaces through their own requirements.

Constraints turn state into margins.

Margins can be collapsed into predicates.

Predicates enable controlled transitions.

Successful intermediate representations become reusable foundations for higher-level capabilities.

The resulting hierarchy is not merely organizational convenience.

It is a factorization of repeated dependencies.

A good layer allows many higher-level capabilities to reuse an already solved intermediate problem.

A bad layer either hides distinctions that its consumers require or exposes distinctions that force consumers to understand unnecessary implementation detail.

The practical objective is therefore neither maximal visibility nor maximal abstraction.

It is:

\[
\boxed{
\text{the smallest realizable shared representation sufficient for the intended family of downstream questions.}
}
\]

This also gives a more precise interpretation of KISS.

Keep the interface simple not by minimizing fields arbitrarily, but by minimizing unnecessary distinctions.

Keep the architecture composable not by forcing every capability through one universal protocol, but by constructing shared representations through which useful families of capabilities can factor.

Keep the hierarchy reusable not by forbidding bypass, but by making reuse the default whenever the existing layer's guarantees are sufficient.

And keep orchestration explicit by turning assumptions, preconditions, margins, transition states, and outcomes into shared architectural state wherever downstream decisions genuinely depend on them.

The central design question becomes:

\[
\boxed{
\begin{aligned}
&\text{What questions must downstream systems answer;}\\
&\text{which distinctions change those answers;}\\
&\text{which of those distinctions can the producer reliably expose;}\\
&\text{what is the smallest stable interface that preserves them;}\\
&\text{which capabilities can factor through that interface;}\\
&\text{and when must a lower-level distinction be reintroduced?}
\end{aligned}
}
\]
