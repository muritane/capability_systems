# From Primitive Distinction to Self-Refining Representation

## Bootstrap Thresholds, Residual Structure, Split–Merge Learning, and the Construction of New Distinctions

## Abstract

A single bit provides one explicit distinction:

\[
0\mid 1.
\]

It does not, by itself, provide perception, memory, action, prediction,
language, mathematics, self-modeling, or even an internal notion that the bit
exists.

The distinction is visible to an external observer because the observer already
possesses a richer representational system capable of identifying the bit,
assigning states to it, and relating those states to consequences.

This creates a bootstrap problem.

If an agent begins with only one explicit distinction, then it cannot yet ask:

```text
Is my representation sufficient?
What am I failing to distinguish?
Should I add a new variable?
Should two states be split apart?
Should two distinctions be merged?
```

Those questions require additional machinery.

The central problem is therefore not only how a bounded system allocates a
finite distinguishability budget. It is also:

\[
\boxed{
\text{how can a system acquire enough representational machinery to detect
when its own distinctions are insufficient?}
}
\]

This paper develops a constructive answer.

The key mechanism is **structured residual**: when states treated as equivalent
produce systematically different predictions, outcomes, actions, risks, or
verification results, the current representation contains an equivalence class
that is too coarse.

A self-refining system can then search for a candidate distinction whose
introduction reduces that structured failure enough to justify its cost.

This yields two fundamental representational operations:

\[
\boxed{
\text{split distinctions when hidden variation becomes consequential}
}
\]

and

\[
\boxed{
\text{merge distinctions when preserving them no longer justifies their cost}
}
\]

Regularization, pruning, compression, feature selection, model expansion,
scientific hypothesis formation, active sensing, and representation learning can
all be interpreted as special cases of controlling this split–merge process.

The resulting architecture separates three stages:

```text
externally supplied distinctions
        ↓
bootstrap machinery for detecting insufficiency
        ↓
self-directed representational refinement
```

The transition between the second and third stages is a **bootstrap threshold**:
the point at which the system can begin proposing and evaluating changes to its
own problem representation.

The broader claim is:

\[
\boxed{
\text{intelligence is not only search over represented states;
it also requires control over which distinctions are representable}
}
\]

---

# 1. Begin With One Explicit Distinction

Let the complete represented state be one bit:

\[
B=\{0,1\}.
\]

An external designer may assign an interpretation such as:

```text
0 = dead
1 = alive
```

or:

```text
0 = no experience
1 = experience
```

or:

```text
0 = inactive
1 = active
```

The choice of label does not change the physical representational capacity.

The system still contains exactly two explicitly distinguishable states.

Thus:

\[
\boxed{
\text{one bit supplies one explicit distinction, not an intelligent ontology}
}
\]

The external observer may already understand concepts such as:

```text
bit
state
agent
existence
life
experience
cause
change
```

but none of those concepts follows from the bit alone.

---

# 2. The First Important Asymmetry Is Between the Observer and the Bit

To an observer, the bit is obvious.

The observer can say:

```text
there is a storage element
it has two states
its state changed
its current value is 1
```

But this description depends on the observer's representational machinery.

The bit does not necessarily contain internal representations of:

```text
itself
its own value
the fact that it has two states
the passage of time
an observer
a transition
an alternative state
```

Therefore:

\[
\boxed{
\text{a distinction can exist for an observer without existing as a represented
object for the system carrying that distinction}
}
\]

This asymmetry is central to the bootstrap problem.

---

# 3. One Bit Does Not Contain Perception

Suppose:

\[
1=\text{alive}.
\]

Then all living situations collapse into the same represented state.

For example:

```text
alive and safe          → 1
alive and hungry        → 1
alive and burning       → 1
alive and falling       → 1
alive and sleeping      → 1
alive and threatened    → 1
```

The representation preserves none of those internal distinctions.

A world may contain enormous variation while the represented system sees only:

\[
0\mid1.
\]

Thus:

\[
\boxed{
\text{world complexity does not imply represented complexity}
}
\]

---

# 4. One Bit Does Not Contain Action

An action system requires distinctions such as:

```text
act / do not act
left / right
approach / avoid
continue / stop
open / close
apply force / release force
```

If no such alternatives are represented or physically available, then one bit
cannot choose among them.

Even the phrase:

```text
choose an action
```

already assumes:

```text
a set of possible actions
an addressable action interface
some selection mechanism
some relation between state and consequence
```

Thus the transition from passive state to agency requires additional structure.

---

# 5. One Bit Does Not Contain Memory

Memory requires at least some way to distinguish:

```text
current
past
```

or:

```text
before
now
```

or to maintain another state that survives across transitions.

Without memory, the system cannot explicitly represent:

\[
\text{what happened previously}.
\]

Without that distinction, it also cannot explicitly compare:

\[
\text{expected outcome}
\]

with:

\[
\text{observed outcome}.
\]

This becomes important later because detecting representational insufficiency
requires comparison.

---

# 6. One Bit Does Not Contain Prediction

Prediction requires at minimum some relation resembling:

\[
\text{current represented state}
\rightarrow
\text{expected future represented state}.
\]

The system must somehow distinguish:

```text
what is
```

from:

```text
what is expected to happen.
```

A prediction error then requires an additional comparison:

\[
\text{prediction}
\neq
\text{observation}.
\]

Thus even the primitive statement:

> The model was wrong.

already presupposes multiple representational distinctions.

---

# 7. One Bit Is Not Enough to Represent an Arbitrary Byte

A single bit has:

\[
2
\]

possible states.

Eight bits have:

\[
2^8=256
\]

possible bit patterns.

Therefore one bit cannot encode an arbitrary 8-bit byte.

But even eight bits do not produce language.

They produce 256 physical or logical code points.

To interpret those code points as characters requires an encoding convention.

To interpret characters as words requires additional structure.

To interpret words as meaningful claims about the world requires still more.

Thus:

\[
\boxed{
\text{state multiplicity}
\neq
\text{symbolic semantics}
\neq
\text{world understanding}
}
\]

---

# 8. Encoding Is Already a Higher-Level Contract

Suppose eight bits contain:

```text
01000001
```

The pattern itself does not announce:

```text
this is the letter A
```

That interpretation depends on a decoder and a convention.

Even after decoding a character, the system still does not automatically possess:

```text
syntax
semantics
reference
concepts
truth conditions
causal models
goals
```

The hierarchy is therefore roughly:

```text
physical distinction
        ↓
code point
        ↓
symbol
        ↓
structured symbol sequence
        ↓
operational relations
        ↓
model
        ↓
prediction and control
```

Each level requires additional distinctions and additional operational structure.

---

# 9. The Naive Bootstrap Proposal Fails

A tempting idea is:

```text
start with one bit
let the system notice that one bit is insufficient
let it add another bit
```

But this immediately smuggles in the very machinery we are trying to explain.

To "notice insufficiency," the system already needs something like:

```text
memory
comparison
expectation
observation
error
alternative representation
modification procedure
evaluation criterion
```

Therefore:

\[
\boxed{
\text{self-refinement cannot begin from a representation too poor to represent
refinement failure}
}
\]

This motivates the concept of a bootstrap threshold.

---

# 10. The Bootstrap Threshold

Define the **bootstrap threshold** as the minimum supplied machinery at which a
system can begin evaluating changes to its own representation.

Before this threshold:

\[
\text{representational changes are externally supplied}.
\]

After this threshold:

\[
\text{representational changes can be internally proposed and tested}.
\]

This does not require full self-awareness.

It requires only enough machinery to implement a loop resembling:

```text
represent
predict or act
observe consequence
measure discrepancy
propose refinement
test refinement
retain or reject
```

Thus:

\[
\boxed{
\text{self-directed representation learning begins when the system can treat
its own representational inadequacy as an actionable signal}
}
\]

---

# 11. A Minimal Ladder of Supplied Distinctions

A possible bootstrap ladder is:

## Level 0: Distinction exists

```text
0 / 1
```

The system has one explicit state distinction.

## Level 1: Differential response

Different states can produce different downstream transitions.

```text
0 → behavior A
1 → behavior B
```

## Level 2: Memory

The system can preserve some distinction between:

```text
previous state
current state
```

## Level 3: Expected consequence

The system can represent a relation between current state and anticipated next
state or outcome.

## Level 4: Observed consequence

The system can encode what actually happened.

## Level 5: Discrepancy

The system can represent a difference between expectation and observation.

## Level 6: Candidate refinement

The system can consider an alternative partition or additional variable.

## Level 7: Comparative evaluation

The system can test whether the alternative reduces consequential discrepancy.

## Level 8: Representational modification

The system can retain the better representation.

## Level 9: Meta-refinement

The system can modify how it proposes, scores, and revises representations.

This ladder is conceptual rather than uniquely determined.

Its purpose is to expose which machinery must exist before representation can
become self-modifying.

---

# 12. Loss Functions Operate Inside an Already Constructed Representation

Consider a model:

\[
\hat y=f_\theta(x)
\]

with squared-error loss:

\[
L(\theta)
=
\sum_i
\left(y_i-f_\theta(x_i)\right)^2.
\]

This already assumes explicit distinctions among:

```text
input
output
target
prediction
parameter
subtraction
magnitude
aggregation
```

Minimizing the loss answers:

\[
\boxed{
\text{which parameters perform best inside this represented model?}
}
\]

It does not automatically answer:

\[
\boxed{
\text{is this the right representation?}
}
\]

That is an outer-loop question.

---

# 13. A Loss Can Reveal Failure Without Naming Its Cause

Suppose two world situations are represented identically:

\[
\phi(x_1)=\phi(x_2)=z.
\]

But their targets differ:

\[
y_1=0,
\qquad
y_2=10.
\]

A model that only sees \(z\) may produce:

\[
\hat y(z)=5.
\]

The corresponding residuals are:

\[
-5,
\qquad
+5.
\]

The optimizer may already be doing the best possible job inside the current
representation.

The error persists because the representation has collapsed two consequentially
different situations into the same state.

Thus:

\[
\boxed{
\text{optimization failure can be representational rather than parametric}
}
\]

---

# 14. The Residual Is a Signal About Hidden Distinctions

Let:

\[
e_i=y_i-\hat y_i.
\]

If the residuals behave like unstructured noise, then additional representation
may not be justified.

But suppose residuals exhibit persistent structure:

```text
condition A → residuals mostly positive
condition B → residuals mostly negative
```

Then the current model is treating situations as equivalent even though their
consequences differ systematically.

This motivates:

\[
\boxed{
\textbf{Structured-Residual Principle}
}
\]

> A persistent, decision-relevant regularity in model error is evidence that the
> current representation may have collapsed a distinction that should remain
> explicit.

The residual does not necessarily identify the missing distinction.

It indicates where the abstraction is failing.

---

# 15. Error Alone Is Not Enough

A large error can arise from many causes:

```text
noise
measurement corruption
optimization failure
insufficient data
wrong parameters
wrong model family
missing variable
collapsed state distinction
nonstationarity
unmodeled intervention
rare boundary condition
```

Therefore the rule cannot be:

```text
large error → add a variable
```

Instead, refinement should be triggered by evidence that the error contains
**persistent exploitable structure**.

The relevant question is:

\[
\boxed{
\text{can some candidate distinction reliably explain or control the residual?}
}
\]

---

# 16. Candidate Distinctions Must Come From Somewhere

A residual can indicate:

```text
something is missing
```

without saying:

```text
add temperature
```

or:

```text
split this object class by material
```

or:

```text
introduce time since last action
```

Candidate distinctions may arise from:

```text
unused sensor channels
higher-resolution measurements
alternative transformations
interventions
active experiments
latent-variable proposals
compositional feature construction
causal hypotheses
model-generated predicates
new memory traces
new temporal windows
new action-conditioned state variables
```

Thus representational refinement requires a **proposal mechanism** as well as an
evaluation mechanism.

---

# 17. The Primitive Refinement Operation Is a Split

A representation partitions world states into equivalence classes.

Suppose a current class is:

\[
E.
\]

A candidate distinction \(d\) divides it into:

\[
E_0
\qquad\text{and}\qquad
E_1.
\]

Then:

\[
E
\rightarrow
\{E_0,E_1\}.
\]

This is the primitive representational operation:

\[
\boxed{
\text{split an equivalence class when hidden variation inside it becomes consequential}
}
\]

For example:

```text
alive
├── safe
└── dangerous
```

Later:

```text
dangerous
├── avoidable
└── unavoidable
```

Later:

```text
avoidable
├── move-left useful
├── move-right useful
└── stopping useful
```

Each split increases explicit distinguishability.

---

# 18. The Primitive Compression Operation Is a Merge

If two represented classes behave sufficiently similarly for the current task,
they can be merged:

\[
E_1,E_2
\rightarrow
E.
\]

This yields:

\[
\boxed{
\text{merge distinctions when preserving their separation no longer justifies
its cost}
}
\]

Examples include:

```text
pruning
quantization
feature elimination
state aggregation
parameter tying
schema simplification
interface hiding
category consolidation
```

Thus representation learning has two complementary directions:

\[
\boxed{
\text{split}
\leftrightarrow
\text{merge}
}
\]

---

# 19. Regularization Can Be Interpreted as Pressure Against Unjustified Distinctions

A generic regularized objective has the form:

\[
J(R)
=
L(R)+\lambda C(R),
\]

where:

\[
L(R)
=
\text{task loss under representation }R
\]

and:

\[
C(R)
=
\text{cost or complexity of maintaining }R.
\]

The regularization term discourages distinctions that do not improve task
performance enough to justify their representational cost.

This suggests the interpretation:

\[
\boxed{
\text{regularization is pressure toward representational merging}
}
\]

while model expansion and feature discovery are pressure toward splitting.

---

# 20. Adding a Distinction Should Pay for Itself

Let \(d\) be a proposed new distinction.

Compare:

\[
R
\]

with:

\[
R+d.
\]

The improvement in task loss is:

\[
\Delta L(d)
=
L(R)-L(R+d).
\]

The additional representational cost is:

\[
\Delta C(d)
=
C(R+d)-C(R).
\]

A simple refinement rule is:

\[
\boxed{
\Delta L(d)
>
\lambda\Delta C(d)
}
\]

subject to any hard safety or feasibility constraints.

This converts the vague question:

> Should we model this distinction?

into:

> Does resolving this distinction improve prediction, control, safety, or
> verification enough to justify the resources required to preserve it?

---

# 21. Decision Relevance Is More Important Than Raw Prediction Error

A distinction can have small average predictive effect but enormous decision
importance.

Suppose two states differ only near a catastrophic boundary.

Collapsing them may barely affect average squared error while radically changing
risk.

Therefore a richer objective is needed:

\[
J(R)
=
L_{\text{prediction}}(R)
+
\alpha L_{\text{decision}}(R)
+
\beta L_{\text{risk}}(R)
+
\gamma C(R).
\]

The exact terms depend on the system.

The principle is:

\[
\boxed{
\text{a distinction should be judged by the consequences of collapsing it,
not merely by reconstruction fidelity}
}
\]

---

# 22. Some Distinctions Are Non-Negotiable

Not every distinction belongs inside a smooth tradeoff.

Some distinctions encode hard boundaries such as:

```text
safe / unsafe
contained / breached
authorized / unauthorized
collision-free / collision
valid / invalid
within operating envelope / outside operating envelope
```

If merging such states can cross an unacceptable boundary, the distinction may
need to be preserved regardless of its average contribution to loss.

Thus a refinement objective should contain both:

```text
soft complexity tradeoffs
hard admissibility constraints
```

---

# 23. The Real Unit of Refinement May Be a Set of Distinctions

A candidate distinction may be useless in isolation but powerful jointly with
another.

For example:

```text
temperature alone          → weak signal
pressure alone             → weak signal
temperature × pressure     → decisive regime boundary
```

Therefore a purely independent scoring rule can fail.

Instead of:

\[
V(d_i),
\]

we may need:

\[
V(S),
\]

where \(S\) is a set of candidate distinctions.

It is possible that:

\[
V(\{d_i,d_j\})
\gg
V(d_i)+V(d_j).
\]

Thus:

\[
\boxed{
\text{relevance can be conditional, interactive, and compositional}
}
\]

---

# 24. Representational Failure Is a Failure of Equivalence

A representation says, implicitly:

> These world states are equivalent for the purposes of this layer.

Formally:

\[
x_1\sim_R x_2
\]

when:

\[
\phi_R(x_1)=\phi_R(x_2).
\]

The abstraction fails when this equivalence is contradicted by consequence.

For example:

\[
\phi_R(x_1)=\phi_R(x_2)
\]

but:

\[
P(y\mid x_1,a)
\neq
P(y\mid x_2,a).
\]

Then the representation has declared two states equivalent even though the task
does not permit that equivalence.

This yields:

\[
\boxed{
\textbf{Equivalence-Failure Principle}
}
\]

> A representation should be refined when states collapsed into one represented
> class exhibit persistent differences in consequences that matter to the task.

---

# 25. Prediction Is One Detector; Control Is Another

A system need not discover missing distinctions only through passive prediction.

Suppose two states look identical under the current representation:

\[
z_1=z_2.
\]

But the same action produces different outcomes:

\[
a(z_1)\rightarrow\text{success}
\]

while:

\[
a(z_2)\rightarrow\text{failure}.
\]

Then action-conditioned residuals reveal hidden structure.

Thus control supplies a powerful refinement signal:

\[
\boxed{
\text{same represented state + same action + different consequence
→ candidate missing distinction}
}
\]

---

# 26. Active Intervention Can Discover Distinctions Faster Than Observation

Some hidden distinctions cannot be identified reliably from passive data.

An agent may deliberately perform an intervention designed to separate competing
hypotheses.

For example:

```text
observe two apparently identical objects
        ↓
apply a small controlled force
        ↓
observe different responses
        ↓
infer a hidden material or attachment distinction
```

Thus representation learning can contain **epistemic actions**:

\[
a_{\text{epistemic}}
\]

whose purpose is not immediate task completion but discrimination among possible
world models.

This extends problem-space engineering into active sensing.

---

# 27. There Are Two Kinds of Action

Once representational self-modification is allowed, the system has at least two
action domains.

## World action

\[
a_t\in A_{\text{world}}
\]

changes the environment.

## Representational action

\[
r_t\in A_{\text{rep}}
\]

changes how the environment is represented.

Representational actions may include:

```text
add a variable
remove a variable
split a category
merge categories
increase numerical precision
reduce numerical precision
request another measurement
increase sampling frequency
create a memory trace
extend temporal context
change an interface
add a constraint
introduce a latent state
construct a derived feature
```

Therefore:

\[
\boxed{
\text{an adaptive agent acts both on the world and on its own problem representation}
}
\]

---

# 28. A Self-Refining Representation Can Be Written as a Control System

Let the world state be:

\[
x_t\in X.
\]

Let the current representation be parameterized by \(\rho_t\):

\[
z_t=\phi_{\rho_t}(x_t).
\]

Let the policy produce a world action:

\[
a_t=\pi_{\rho_t}(z_t).
\]

Let a verification mechanism produce a discrepancy signal:

\[
e_t=\mathcal V(x_t,z_t,a_t,y_t).
\]

Then the representation itself may be updated:

\[
\rho_{t+1}
=
F(
\rho_t,
e_t,
u_t,m_t,c_t
),
\]

where terms may include:

```text
uncertainty       ν_t
constraint margin m_t
resource cost     c_t
```

This gives a closed loop:

```text
world
  ↓
representation
  ↓
prediction / action
  ↓
consequence
  ↓
verification residual
  ↓
representation update
  ↺
```

---

# 29. The Inner Optimizer and the Representation Controller Solve Different Problems

The inner optimizer asks:

\[
\theta^*
=
\arg\min_\theta
L(\theta\mid R).
\]

The representation controller asks:

\[
R^*
=
\arg\min_R
\left[
L(\theta^*(R)\mid R)
+
\lambda C(R)
\right].
\]

The first problem assumes the representation.

The second compares representations.

Thus:

\[
\boxed{
\text{parameter optimization}
\neq
\text{representation optimization}
}
\]

A very strong inner optimizer can still fail systematically if the outer
representation is wrong.

---

# 30. Strong Optimization Makes Missing Distinctions More Dangerous

If a weak optimizer sees an incomplete representation, it may behave poorly in
many ordinary ways.

A strong optimizer may do something more concerning:

```text
find exactly the region where the omitted distinction matters most
```

If the represented feasible region differs from the real feasible region, strong
search pressure can exploit that gap.

Therefore:

\[
\boxed{
\text{increasing optimizer strength increases the value of detecting
representation failure early}
}
\]

Self-refinement is therefore not merely a convenience.

It can be a safety mechanism.

---

# 31. Regularization and Refinement Form a Bidirectional Controller

If a system only splits representations, complexity grows without bound.

If it only merges, important distinctions disappear.

A stable architecture therefore needs both pressures.

## Refinement pressure

Triggered by:

```text
structured residual
uncertainty
prediction divergence
action failure
constraint proximity
unexpected intervention response
verification failure
```

## Compression pressure

Triggered by:

```text
redundancy
low marginal utility
stable equivalence
unused variables
excess precision
low sensitivity
high maintenance cost
```

Thus:

\[
\boxed{
R_t
\xrightarrow{\text{split / merge}}
R_{t+1}
}
\]

is a representational control process.

---

# 32. Weight Magnitude Is One Special Case, Not the General Mechanism

Constraints on weights and biases can prevent pathological or unnecessarily
complex parameterizations.

Examples include pressure against:

```text
very large weights
unstable activations
excessive sensitivity
unnecessary parameter magnitude
```

But this operates mostly **inside a fixed parameterization**.

The broader question is:

> Should the represented variable, category, state, precision level, interface,
> or latent factor exist at all?

Therefore:

\[
\boxed{
\text{parameter regularization is a local instance of a broader
representational economy}
}
\]

---

# 33. Numerical Precision Is Also a Split–Merge Process

Suppose a scalar representation has adjacent machine values:

\[
z_i,
z_{i+1}.
\]

Increasing precision inserts additional distinguishable values between them.

This is effectively a split in numerical state space.

Reducing precision maps multiple values to the same code point.

This is a merge.

Thus:

```text
higher precision  → finer partition
lower precision   → coarser partition
```

Mixed precision becomes nonuniform partition control:

```text
split heavily where numerical differences matter
merge aggressively where they do not
```

---

# 34. Sensing Is Also a Split–Merge Process

A coarse sensor maps many world states to the same measurement.

Increasing spatial, temporal, spectral, or numerical resolution splits those
measurement equivalence classes.

For example:

```text
object detected
```

may refine into:

```text
object type
```

then:

```text
pose
```

then:

```text
surface geometry
```

then:

```text
local deformation
```

The correct sensing resolution depends on whether the additional distinctions
change prediction or action.

---

# 35. Memory Depth Is Also Resolution Allocation

A system may represent only:

```text
current state
```

or:

```text
current + previous
```

or an extended history:

\[
h_t=(z_t,z_{t-1},\ldots,z_{t-k}).
\]

Increasing history length creates additional temporal distinctions.

This consumes memory and compute.

A useful representation should extend temporal resolution only when shorter
histories collapse states with different future consequences.

Thus:

\[
\boxed{
\text{temporal context can be allocated by the same consequence-sensitive
refinement rule}
}
\]

---

# 36. Language Can Be Seen as Extremely Deep Distinction Architecture

Language does not appear when enough bits are accumulated.

A language-capable system requires many layers of distinction:

```text
signal boundaries
symbol identity
symbol order
composition
syntactic role
reference
semantic relation
speaker state
context
pragmatic consequence
```

Each layer introduces equivalence classes and refinements.

For example, the same physical signal may be treated as equivalent despite
speaker identity, or distinguished when speaker identity affects meaning.

Thus language is not merely stored information.

It is a highly structured architecture of distinctions whose usefulness depends
on operational context.

---

# 37. Mathematics Is Not Contained in Numerals

Representing the character:

```text
2
```

does not by itself provide the mathematical concept of two.

Likewise, storing:

```text
2 + 2 = 4
```

does not automatically provide arithmetic competence.

Mathematical representation requires stable operational relations among symbols,
transformations, equivalence classes, and rules.

Thus:

\[
\boxed{
\text{symbol capacity is necessary for explicit mathematics but not sufficient
for mathematical semantics}
}
\]

---

# 38. Scientific Discovery Can Be Interpreted as Representational Refinement

A scientific model creates equivalence classes:

```text
these observations are instances of the same mechanism
```

An anomaly is evidence that this equivalence may be too coarse.

The scientific response may be to introduce a distinction:

```text
new variable
new regime
new hidden state
new interaction term
new causal mechanism
```

The refinement is retained when it explains persistent residual structure and
continues to do so under new observations or interventions.

Thus scientific hypothesis formation can be interpreted as:

\[
\boxed{
\text{search over candidate partitions of observable and latent world states}
}
\]

---

# 39. Generalization Requires Resisting Gratuitous Splits

A system could perfectly fit finite observations by assigning each observation
its own distinct state.

That representation would maximize local distinguishability but destroy useful
abstraction.

Therefore the objective is not:

\[
\text{maximize distinctions}.
\]

It is:

\[
\boxed{
\text{preserve the smallest set of distinctions sufficient for reliable
prediction, decision, control, and safety}
}
\]

This is why compression and generalization are inseparable from refinement.

---

# 40. The Central Tension Is Under-Distinction Versus Over-Distinction

A representation can fail in two opposite ways.

## Under-distinction

Different consequential situations are collapsed:

\[
\phi(x_1)=\phi(x_2)
\]

when they should differ.

Symptoms include:

```text
systematic residuals
inconsistent action outcomes
unexplained variance
constraint violations
unreliable transfer
```

## Over-distinction

Situations that are operationally equivalent are represented separately.

Symptoms include:

```text
overfitting
excess memory
fragile categories
poor transfer
high verification burden
needless numerical precision
```

The representational controller must operate between these extremes.

---

# 41. A General Split Criterion

Let \(E\) be a represented equivalence class.

Let \(d\) be a candidate distinction that partitions it into:

\[
E_0,
E_1,
\ldots,
E_k.
\]

Define the expected benefit of the split as:

\[
B(d\mid E)
=
\Delta P
+
\alpha\Delta D
+
\beta\Delta S
+
\gamma\Delta U,
\]

where the terms may represent improvements in:

```text
prediction      ΔP
decision quality ΔD
safety          ΔS
uncertainty     ΔU
```

Let the cost be:

\[
C(d\mid E)
=
C_{\text{memory}}
+
C_{\text{compute}}
+
C_{\text{sensing}}
+
C_{\text{verification}}
+
C_{\text{complexity}}.
\]

Then refine when:

\[
\boxed{
B(d\mid E)>\lambda C(d\mid E)
}
\]

subject to hard constraints.

---

# 42. A General Merge Criterion

Let two represented classes be:

\[
E_i,
E_j.
\]

Suppose replacing them with one class changes task performance by only:

\[
\epsilon.
\]

If the savings in representational cost exceed the consequence of that loss,
then merge:

\[
\boxed{
\text{merge }E_i,E_j
\text{ when }
\Delta C_{\text{saved}}
>
\lambda^{-1}\Delta L_{\text{introduced}}
}
\]

again subject to hard boundaries that cannot be collapsed.

---

# 43. A Minimal Self-Refining Algorithm

A generic algorithm can now be written.

```text
initialize representation R
initialize model M over R

loop:
    observe current represented state z
    predict or choose action
    observe consequence y
    compute verification residual e

    if residual is unstructured and acceptable:
        continue

    identify region E where failure is concentrated
    generate candidate distinctions d1 ... dn

    for each candidate distinction d:
        construct provisional representation R + d
        refit or adapt model under R + d
        estimate out-of-sample benefit B(d)
        estimate representational cost C(d)
        test hard constraints

    if some candidate has sufficient net value:
        adopt best refinement

    periodically test existing distinctions for redundancy

    if a distinction can be removed without consequential loss:
        merge or prune it
```

This is not tied to any one learning method.

The essential structure is:

\[
\boxed{
\text{failure}
\rightarrow
\text{localize}
\rightarrow
\text{propose distinction}
\rightarrow
\text{test}
\rightarrow
\text{split or reject}
\rightarrow
\text{compress when possible}
}
\]

---

# 44. The Candidate Generator Is the Hard Part

Evaluation is comparatively straightforward once a candidate distinction is
available.

The harder problem is generating useful candidates.

A candidate generator may operate over:

```text
sensor dimensions
feature transformations
latent factors
temporal aggregates
interaction terms
causal hypotheses
symbolic predicates
new experiments
new measurements
new memory variables
new actions
```

A sufficiently advanced system may generate candidates from its own learned
models.

This marks a deeper stage of self-directed representation engineering.

---

# 45. Self-Modeling Is Not Required at the Beginning

A system does not need the explicit sentence:

> My representation is insufficient.

It needs only a functional equivalent.

For example:

```text
persistent residual detected
        ↓
refinement routine activated
```

This can occur without linguistic self-awareness.

Thus the bootstrap threshold is operational, not philosophical.

The question is not whether the system possesses a human-like concept of itself.

The question is whether it can use its own failure signals to alter the
representation producing those failures.

---

# 46. Self-Modeling Can Emerge Later as Another Useful Distinction

At some point, behavior may improve if the system distinguishes:

```text
world state
```

from:

```text
its own internal state
```

or:

```text
external uncertainty
```

from:

```text
model uncertainty
```

or:

```text
task failure
```

from:

```text
representation failure
```

These distinctions need not be present initially.

They can themselves become justified when collapsing them causes systematic
errors.

Thus even self-modeling can be treated as representational refinement rather
than an assumed starting primitive.

---

# 47. The Bootstrap Process Can Be Externally Scaffolded

The earliest system may be incapable of proposing new distinctions.

An external designer, evolutionary process, training curriculum, or development
process can supply them incrementally.

For example:

```text
stage 0: one binary state
stage 1: add memory
stage 2: add prediction target
stage 3: add residual detector
stage 4: add candidate feature pool
stage 5: add split evaluator
stage 6: add autonomous feature generation
stage 7: add meta-learning over refinement strategy
```

The important transition occurs when the system no longer requires an external
agent to specify every new distinction.

---

# 48. Bootstrapping Can Be Viewed as Delegation of Representation Design

Initially:

\[
\text{designer chooses representation}.
\]

Later:

\[
\text{designer chooses rules for representation change}.
\]

Later still:

\[
\text{system learns rules for representation change}.
\]

Thus the locus of design moves outward:

```text
choose state
        ↓
choose how state may change
        ↓
choose how representation may change
        ↓
choose how representation-change rules may change
```

This resembles the broader transition from manual parameter choice to automated
optimization, but one level higher.

---

# 49. The Meta-System Recursion Does Not Disappear

If a system can modify its own representation, one may ask:

> What representation does the representation-modification mechanism use?

The recursion is real.

But it does not make the architecture useless.

Engineering systems routinely terminate recursion at a trusted lower layer.

For example:

```text
hardware substrate
fixed update rules
verified meta-controller
bounded candidate language
```

The important question is where the self-modification boundary is placed and how
that boundary is verified.

Thus:

\[
\boxed{
\text{self-refinement does not require infinite self-description}
}
\]

It requires a sufficiently capable and sufficiently trustworthy refinement layer.

---

# 50. Verification Is What Makes Representation Change Safe

A candidate distinction should not be retained merely because it improves
training loss.

It should survive verification against:

```text
held-out observations
interventions
constraint checks
robustness tests
resource limits
counterfactual tests
safety boundaries
longer-horizon outcomes
```

Without verification, the system may simply replace one bad abstraction with
another.

Thus:

\[
\boxed{
\text{representation refinement requires a verification loop, not only a loss
reduction signal}
}
\]

---

# 51. The Distinction Generator and the Verifier Should Be Partly Independent

If the same mechanism proposes and validates every distinction, it may repeatedly
confirm its own biases.

A stronger architecture separates:

```text
proposal
```

from:

```text
verification
```

at least partially.

For example:

```text
model proposes a new latent distinction
independent test evaluates predictive consequence
constraint system checks admissibility
resource controller checks cost
```

This creates an internal analogue of hypothesis generation followed by empirical
test.

---

# 52. A Representation Can Fail Locally Without Failing Globally

A representation may be adequate in most of the state space but insufficient
near a small region.

For example:

```text
coarse geometry works during free motion
fine geometry is needed near contact
```

Therefore refinement should often be local rather than global.

Instead of replacing:

\[
R
\]

with a uniformly more detailed representation, construct:

\[
R'(x)
=
\begin{cases}
R_{\text{coarse}}(x), & x\notin\Omega_{\text{critical}}\\
R_{\text{fine}}(x), & x\in\Omega_{\text{critical}}
\end{cases}
\]

This yields adaptive resolution.

---

# 53. The Best Representation May Be Conditional on the Current Goal

A distinction relevant for one task may be irrelevant for another.

For example:

```text
paint color
```

may be irrelevant to grasping but essential to sorting by color.

Therefore relevance depends on:

\[
\text{world state}
+
\text{goal}
+
\text{available actions}
+
\text{constraints}
+
\text{verification criterion}.
\]

Thus the representation may need to be dynamically task-conditioned.

---

# 54. Representation Cost Is Multidimensional

The cost of preserving a distinction is not only storage.

It may include:

```text
sensor cost
memory
compute
bandwidth
latency
energy
sample complexity
verification burden
interface complexity
human interpretability cost
coordination cost
maintenance cost
```

Therefore the distinguishability budget is generally a vector of constrained
resources rather than a single number.

A candidate refinement can be worthwhile under one hardware or organizational
envelope and not another.

---

# 55. Problem-Space Engineering Becomes a Dynamic Process

Problem-space engineering is often described as constructing:

```text
state
actions
constraints
interfaces
objectives
evaluation
```

But if representation can be revised, then problem-space engineering is not only
an initial design phase.

It becomes a repeated loop:

\[
\boxed{
\text{construct}
\rightarrow
\text{search}
\rightarrow
\text{observe failure}
\rightarrow
\text{refine space}
\rightarrow
\text{search again}
}
\]

The problem space itself becomes an adaptive object.

---

# 56. The Full Architecture Has Three Nested Loops

The framework suggests three nested loops.

## Loop 1: Action or parameter optimization

```text
given the current problem space, find a good solution
```

## Loop 2: Representation refinement

```text
when systematic failure appears, revise the distinctions defining the problem
space
```

## Loop 3: Meta-refinement

```text
improve how candidate distinctions are generated, evaluated, and verified
```

Schematically:

\[
\boxed{
\text{optimize behavior}
\subset
\text{optimize representation}
\subset
\text{optimize representation-change strategy}
}
\]

---

# 57. A Possible Formal Objective

Let:

\[
R
\]

be the current representation,

\[
\theta_R
\]

the best model parameters available under that representation, and

\[
\mathcal E(R,\theta_R)
\]

the expected consequential error.

Let:

\[
C(R)
\]

be representational cost.

Then one broad outer objective is:

\[
R^*
=
\arg\min_R
\left[
\mathcal E(R,\theta_R)
+
\lambda C(R)
\right]
\]

subject to:

\[
R\in\mathcal R_{\text{admissible}}.
\]

But because the system cannot search all possible representations, the practical
problem is local:

\[
R_{t+1}
\in
\mathcal N(R_t),
\]

where \(\mathcal N(R_t)\) is a manageable neighborhood of candidate split, merge,
precision, sensing, memory, and interface operations.

Thus the algorithm is a search over **representation edits**.

---

# 58. Representation Edits Form a Language

A self-refining system needs a bounded language of legal edits.

Possible primitives include:

```text
SPLIT(category, predicate)
MERGE(category_a, category_b)
ADD(feature)
REMOVE(feature)
INCREASE_PRECISION(variable)
DECREASE_PRECISION(variable)
EXTEND_MEMORY(window)
SHORTEN_MEMORY(window)
ADD_SENSOR(channel)
QUERY_SENSOR(channel)
ADD_CONSTRAINT(predicate)
ADD_LATENT_STATE(model)
CREATE_INTERACTION(feature_a, feature_b)
```

This makes representational self-modification explicit and auditable.

It also avoids requiring arbitrary unconstrained rewriting of the entire system.

---

# 59. The Representation-Edit Language Is Itself a Problem-Space Boundary

Once legal representation edits are specified, the system searches inside that
meta-space.

Thus there are two feasible regions:

\[
A_F
\]

for world actions and:

\[
R_F
\]

for representation edits.

The system may optimize only within:

\[
A_F\times R_F.
\]

This creates a natural safety architecture:

```text
allow flexible optimization inside the world-action space
allow flexible refinement inside the representation-edit space
verify both boundaries externally or with trusted mechanisms
```

---

# 60. The Bootstrap Threshold Can Be Engineered Explicitly

Instead of asking whether self-directed representation learning will somehow
emerge spontaneously, one can design for it.

Supply only the primitives required for:

```text
1. storing state
2. remembering consequences
3. predicting
4. computing discrepancy
5. localizing systematic discrepancy
6. generating candidate distinctions
7. testing candidates
8. retaining beneficial refinements
9. pruning redundant refinements
```

Then observe what representations develop.

This creates a concrete experimental program.

---

# 61. A Minimal Experimental System

Consider a simple simulated environment.

The agent begins with an intentionally impoverished representation:

\[
R_0=\{0,1\}.
\]

The environment contains hidden variables that affect outcomes.

The agent is given:

```text
a small memory
one prediction target
one residual signal
a restricted library of candidate measurements
a split operation
a merge operation
a complexity penalty
```

The experiment asks:

```text
which distinctions does the system choose to preserve?
in what order?
under what failures?
how stable are the discovered distinctions?
do they correspond to causal structure?
do they transfer to new tasks?
```

This directly tests the framework.

---

# 62. A Stronger Experimental System

A later system can be given no fixed candidate feature list.

Instead, it may construct candidates from:

```text
compositions of existing features
latent clustering
counterfactual predictions
temporal patterns
intervention results
program synthesis
symbolic predicates
```

Then the central question becomes:

\[
\boxed{
\text{can useful representational primitives emerge from failure-driven
partition refinement?}
}
\]

---

# 63. Transfer Is an Important Test of Whether a Distinction Is Real Enough

A distinction may improve one dataset by accident.

A more meaningful distinction should often retain value across:

```text
new samples
new contexts
new interventions
new tasks
new environments
```

Transfer therefore provides evidence that the distinction captures persistent
regularity rather than local noise.

Thus:

\[
\boxed{
\text{a good split should survive beyond the residual that originally motivated it}
}
\]

---

# 64. Causal Distinctions Are Often More Valuable Than Correlational Ones

A candidate feature may predict residuals without representing a stable causal
regularity.

If interventions break the relation, the distinction may be brittle.

Therefore refinement can rank candidate distinctions partly by causal leverage:

```text
does intervening on this variable change outcome?
does this split remain predictive under policy change?
does it preserve invariant structure across environments?
```

Causal validation therefore strengthens representational refinement.

---

# 65. Uncertainty Can Trigger Resolution Before Failure Occurs

Waiting for overt failure may be too late near dangerous boundaries.

A system can refine proactively when:

```text
predictive uncertainty rises
model disagreement increases
constraint margin shrinks
state novelty increases
counterfactual outcomes diverge
```

Thus refinement triggers include both:

```text
observed failure
```

and:

```text
predicted insufficiency
```

This makes the architecture anticipatory rather than purely reactive.

---

# 66. The System Can Learn Where Not to Spend Distinguishability

Self-refinement is not only about discovering missing variables.

It should also learn stable irrelevance.

For example:

```text
factory latitude never changes the control decision
paint texture has no measurable influence on grasp success
extra precision in one accumulator never changes the final output
```

Such evidence supports merging or hiding those distinctions.

Therefore the system accumulates not only a model of relevance but a model of
**irrelevance envelopes**.

---

# 67. An Abstraction Should Carry Its Own Failure Conditions

A mature abstraction should ideally contain:

```text
what it represents
what it hides
where it is valid
what residuals are expected
which boundary conditions invalidate it
how to escalate resolution
```

Then an interface becomes more than a callable contract.

It becomes a conditional claim:

> These hidden distinctions are irrelevant while these verification conditions
> remain satisfied.

Thus:

\[
\boxed{
\text{an abstraction is safest when it includes an explicit escalation policy}
}
\]

---

# 68. The New Core Principle: Distinction Formation

The original allocation problem asks:

> Given representational capacity, which existing distinctions deserve explicit
> state?

The bootstrap problem adds an earlier question:

> How are candidate distinctions formed before they can be allocated capacity?

This yields:

\[
\boxed{
\textbf{Distinction-Formation Principle}
}
\]

> A bounded adaptive system should create a new explicit distinction when
> persistent failure reveals that a currently represented equivalence class
> contains consequentially different states, and when some candidate refinement
> can separate those states reliably enough to justify its representational and
> verification cost.

---

# 69. The Structured-Residual Principle

\[
\boxed{
\textbf{Structured-Residual Principle}
}
\]

> Error becomes evidence for representational refinement when it contains
> persistent structure that can be reduced by introducing a distinction whose
> effect generalizes beyond the observations that motivated it.

This separates:

```text
noise
```

from:

```text
missing representation
```

in operational terms.

---

# 70. The Split–Merge Principle

\[
\boxed{
\textbf{Split–Merge Principle}
}
\]

> Representation learning can be understood as controlling a partition of world
> states: split classes when collapsed differences become consequential; merge
> classes when preserved differences cease to justify their cost.

This unifies:

```text
abstraction
regularization
compression
feature discovery
state aggregation
precision control
model expansion
```

under one representational operation.

---

# 71. The Bootstrap-Threshold Principle

\[
\boxed{
\textbf{Bootstrap-Threshold Principle}
}
\]

> A system cannot self-correct a representational insufficiency until it already
> possesses enough machinery to encode expectation, observation, discrepancy,
> candidate refinement, and comparative evaluation. Before that threshold,
> representational structure must be supplied externally; after it, refinement
> can increasingly be delegated to the system itself.

---

# 72. The Representation-Action Principle

\[
\boxed{
\textbf{Representation-Action Principle}
}
\]

> An adaptive agent has two broad classes of action: actions that change the
> world and actions that change how the world is represented. Intelligent control
> requires choosing not only what to do, but sometimes what to distinguish before
> deciding what to do.

---

# 73. The Verification-Gated Refinement Principle

\[
\boxed{
\textbf{Verification-Gated Refinement Principle}
}
\]

> A candidate distinction should become part of the persistent representation
> only when its benefit survives independent tests of prediction, control,
> generalization, admissibility, and resource cost.

This prevents uncontrolled representational proliferation.

---

# 74. The Minimal-Sufficient-Distinction Principle

\[
\boxed{
\textbf{Minimal-Sufficient-Distinction Principle}
}
\]

> The objective is neither maximal compression nor maximal detail. It is the
> smallest dynamically maintained set of explicit distinctions sufficient for
> reliable prediction, decision, control, verification, and safety under the
> current task and resource envelope.

---

# 75. A Revised Hierarchy of Problem-Space Engineering

The full hierarchy now becomes:

\[
\boxed{
\begin{aligned}
&\text{primitive distinguishability}\\
&\downarrow\\
&\text{externally supplied operational structure}\\
&\downarrow\\
&\text{memory + prediction + discrepancy}\\
&\downarrow\\
&\text{bootstrap threshold}\\
&\downarrow\\
&\text{detect structured residual}\\
&\downarrow\\
&\text{propose candidate distinction}\\
&\downarrow\\
&\text{split / merge representation}\\
&\downarrow\\
&\text{construct or revise problem space}\\
&\downarrow\\
&\text{optimize inside the current space}\\
&\downarrow\\
&\text{verify against consequence}\\
&\downarrow\\
&\text{refine again}
\end{aligned}
}
\]

This closes the loop that a static representation-allocation framework leaves
open.

---

# 76. Final Synthesis

A single bit begins with one explicit distinction:

\[
0\mid1.
\]

To an external observer, that distinction can be named.

But the bit does not thereby obtain:

```text
selfhood
memory
prediction
failure
language
mathematics
world models
action semantics
representation design
```

Those require additional machinery.

The first stage of intelligence is therefore not autonomous representation
engineering.

It is **bootstrapping the machinery that makes representational inadequacy
detectable**.

Once a system can compare expected and observed consequences, a new signal
appears:

\[
\text{residual}.
\]

When residuals are systematic, they indicate that some represented equivalence
class may be too coarse.

The system can then search for a candidate distinction:

\[
d
\]

that splits the problematic class.

If the split improves consequential performance enough to justify its cost, the
new distinction is retained.

If an existing distinction contributes too little, it can be merged away.

Thus the core representational loop is:

```text
represent
    ↓
predict / act
    ↓
observe
    ↓
measure discrepancy
    ↓
search for structured residual
    ↓
propose distinction
    ↓
split or merge
    ↓
verify
    ↓
repeat
```

The result is a system that does not merely optimize parameters inside a fixed
space.

It can progressively modify the space itself.

This suggests a broader interpretation of regularization, abstraction,
representation learning, model selection, active sensing, scientific discovery,
and adaptive precision:

\[
\boxed{
\text{they are mechanisms for deciding which distinctions deserve to remain
operationally explicit}
}
\]

The deepest transition is therefore:

```text
external designer chooses distinctions
        ↓
external designer supplies refinement machinery
        ↓
system detects structured insufficiency
        ↓
system proposes and tests new distinctions
        ↓
system engineers its own problem representation
```

The central question changes from:

> How many states can the system represent?

into:

> Which equivalence classes are currently too coarse, and what evidence would
> justify splitting them?

And from:

> How should the optimizer change its parameters?

into:

> When should the system change what is capable of being represented at all?

That is the transition from finite distinguishability to **self-refining
problem-space engineering**.
