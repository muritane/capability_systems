# Locally Executable Capability Routes: From Desired States to Reachable Transitions

## Abstract

A desired state is not an action.

An agent may want to:

```text
reach Berlin
leave debt
obtain housing
read a novel in a foreign language
express an idea clearly
become competent in a technical field
gain access to a service
escape a physical obstacle
```

but none of these descriptions, by itself, specifies an executable transition.

This creates a basic planning requirement:

\[
\boxed{
\text{a valid plan must begin with an action executable from the agent's current state}
}
\]

and continue through a sequence in which later actions become executable only after earlier actions have changed the agent, its resources, its location, its information, or its representation.

Thus:

\[
s_0
\xrightarrow{a_0}
s_1
\xrightarrow{a_1}
s_2
\rightarrow
\cdots
\rightarrow
s_n
\]

requires:

\[
a_i \in A^F(s_i)
\]

for each step \(i\).

This seems trivial in physical navigation.

If a person wants to travel to Berlin, a route planner does not answer:

```text
go to Berlin
```

or:

```text
teleport there
```

It asks where the person is, which modes are available, when the trip occurs, what constraints apply, and which sequence of currently and subsequently feasible transitions connects the present state to the destination.

Yet many capability, economic, educational, organizational, and personal problems are routinely described as if a target state were itself an action:

```text
homeless
    → buy a house

in debt
    → pay the debt

lacking a skill
    → train the skill

not an expert
    → become an expert

cannot express thoughts clearly
    → communicate better
```

These statements can be true as descriptions of the destination while containing almost no transition information.

The central claim of this framework is:

\[
\boxed{
\textbf{Do not confuse a description of the destination with a locally executable route to it.}
}
\]

Endogenous feasible-action frontier change should therefore be understood as a routing problem over changing capability states.

The agent cannot directly choose any desirable future architecture.

It must bootstrap every architectural change from actions already available locally.

---

## 1. Desired States Are Not Actions

Suppose an agent is in state:

\[
s_t
\]

and wants to reach some target region:

\[
D.
\]

A statement such as:

```text
become an expert
```

describes a desired property of a later state.

It does not define an operator.

Formally:

\[
\operatorname{Goal}(D)
\neq
\operatorname{Action}(s_t,D).
\]

Likewise:

```text
have a house
have no debt
speak fluently
understand calculus
be employable
be healthy
reach Berlin
```

are predicates over states.

They should not be inserted into a planning graph as primitive transitions unless the agent actually possesses an executable action with that effect.

Thus:

\[
\boxed{
\text{target-state specification}
\neq
\text{transition specification}
}
\]

This distinction prevents desired outcomes from being smuggled into the action set as fictional edges.

---

## 2. The Teleportation Error

Consider travel.

An agent is currently in:

\[
s_0=\text{Munich}
\]

and wants:

\[
D=\text{Berlin}.
\]

The transition:

\[
\text{Munich}
\rightarrow
\text{Berlin}
\]

may be a useful abstraction at one level.

But operationally it must decompose into executable steps.

For example:

\[
\text{home}
\rightarrow
\text{walk to station}
\rightarrow
\text{board ICE}
\rightarrow
\text{Berlin Hbf}
\rightarrow
\text{local transit}
\rightarrow
\text{destination}.
\]

A route planner does not confuse:

```text
Berlin
```

with:

```text
an action that places the agent in Berlin.
```

This error is obvious when the implied transition violates physical movement.

It is less obvious when the target is an economic, social, cognitive, or capability state.

Examples:

```text
homeless?
    just buy a house

stuck in a pit?
    just get out

have debts?
    just pay them back

lack a skill?
    just train it

not an expert?
    just become one

cannot express yourself?
    communicate more clearly
```

These answers have the same structural defect as:

```text
want to reach Berlin?
    just be in Berlin
```

The defect is not necessarily falsehood.

It is missing transition structure.

---

## 3. The Local Executability Principle

Let:

\[
A_t^F
\]

be the set of actions currently executable by the agent.

Then every plan must begin with:

\[
\boxed{
a_t \in A_t^F
}
\]

even when the purpose of \(a_t\) is to change what will be feasible later.

Suppose:

\[
a_t^E
\]

is an architecture-changing action.

It may transform:

\[
X_t
\rightarrow
X_{t+1}
\]

and therefore:

\[
A_t^F
\rightarrow
A_{t+1}^F.
\]

But:

\[
\boxed{
a_t^E \in A_t^F
}
\]

must still hold at the moment of execution.

This gives:

\[
\boxed{
\textbf{Local Executability Principle}
}
\]

> Every action that changes the future feasible-action frontier must itself be executable from the current feasible-action frontier.

Endogeneity does not imply magical self-modification.

It means that locally feasible actions may alter the conditions under which later actions are evaluated.

---

## 4. The Pit and the Ladder

Suppose an agent is trapped in a pit.

The desired state is:

\[
\text{outside pit}.
\]

A planner observes that:

```text
climbing a ladder
```

would solve the problem.

But if no ladder is present, then:

```text
use ladder
```

is not currently executable.

The planner might propose:

```text
obtain ladder
```

but this is useful only if there is a feasible route to the ladder.

Possible locally executable steps might include:

```text
call another person
use a rope already present
construct a ladder from available material
climb a rough surface
signal for assistance
dig footholds
```

If none exists, then the state may genuinely be locally absorbing relative to the represented action model.

Thus:

\[
\boxed{
\text{a counterfactual solution is not necessarily a reachable solution}
}
\]

The existence of some architecture in which the problem would be easy does not imply that the current architecture contains a path to that architecture.

---

## 5. Recursive Feasibility

A route does not require all actions to be executable at the initial state.

It requires each action to become executable when its turn arrives.

Let:

\[
p=(a_0,a_1,\ldots,a_n)
\]

produce:

\[
s_0,s_1,\ldots,s_{n+1}.
\]

Then:

\[
\boxed{
a_i \in A^F(s_i)
\quad
\forall i
}
\]

is the important condition.

An action may therefore be impossible at \(s_0\) but feasible at \(s_4\).

For example:

```text
cannot read advanced French novel
↓
learn basic pronunciation
↓
learn high-frequency vocabulary
↓
read graded texts
↓
gain contextual inference ability
↓
read ordinary prose
↓
read advanced novel
```

The final action is not executable initially.

That is not a defect in the plan.

The plan is valid if each earlier step changes the state so that the next step becomes executable.

---

## 6. Capability Routes

This suggests treating capability acquisition as route planning.

A capability route is a sequence:

\[
X_0
\xrightarrow{a_0}
X_1
\xrightarrow{a_1}
X_2
\rightarrow
\cdots
\rightarrow
X_n
\]

where:

\[
X_i
\]

is an agent architecture state and where each transition may alter:

```text
skill
knowledge
authorization
resources
access
location
compatibility
representation
social connection
tool availability
```

The purpose of an intermediate state need not be intrinsically valuable.

It may matter only because it enables a later transition.

For example:

```text
learn how to use search
```

may have little terminal value for an agent whose actual goal is:

```text
adapt successfully in unfamiliar environments.
```

But it may enable:

```text
search
→ find relevant sources
→ evaluate information
→ learn local rules
→ identify opportunities
→ act competently in new environment
```

Likewise:

```text
practice pronunciation
```

may not be an independently desired outcome.

Its value may lie in enabling:

```text
recognize spoken forms
→ pronounce unfamiliar words
→ use vocabulary socially
→ converse
→ participate
→ express complex thoughts
```

Thus:

\[
\boxed{
\text{capability acquisition can be instrumentally valuable without being a terminal demand}
}
\]

---

## 7. Terminal Value and Instrumental Value

Let:

\[
V_T(x)
\]

represent terminal value.

Let:

\[
V_I(x\mid d)
\]

represent instrumental value relative to target demand \(d\).

Then a state or capability can satisfy:

\[
V_T(x)\approx 0
\]

while:

\[
V_I(x\mid d)\gg 0.
\]

A transfer station is a simple example.

A traveler may have no reason to value:

```text
being at Hannover Hbf
```

except that it lies on a good route.

Similarly:

```text
learning how to search effectively
learning basic phonetics
obtaining a document
creating an account
installing a tool
learning notation
memorizing core vocabulary
```

may be transfer nodes in capability space.

This leads to:

\[
\boxed{
\textbf{Instrumental-State Principle}
}
\]

> Intermediate skills, resources, representations, and access states should be valued partly by the future transitions they enable, even when they are not independently demanded.

---

## 8. Why Route Planning Feels Natural in Navigation

Physical route planning usually preserves four distinct objects:

\[
(\text{current state},\text{target state},\text{constraints},\text{transition model}).
\]

A navigation system asks questions such as:

```text
Where are you?
Where are you going?
When do you want to arrive?
Do you have a car?
Can you walk?
Which transit services operate?
What is the current traffic?
What are your cost or accessibility constraints?
```

Only after establishing these does it search for a route.

The result is therefore agent-relative.

A motorway may exist in reality while being unusable to an agent who:

```text
cannot drive
has no vehicle access
is not authorized
cannot pay the toll
cannot enter the jurisdiction
```

Thus:

\[
\text{transition exists}
\not\Rightarrow
\text{transition is executable by this agent}.
\]

This is exactly the distinction required in capability planning.

---

## 9. Why Capability Advice Often Collapses the Structure

In many non-navigation domains, the same four-part structure collapses.

Instead of:

\[
(\text{current state},\text{target},\text{constraints},\text{transition model}),
\]

advice often preserves only:

\[
(\text{target}).
\]

Examples:

```text
want to write well?
    write better

want expertise?
    study more

want financial stability?
    save money

want employment?
    get a job

want housing?
    obtain housing

want confidence?
    become more confident
```

These are often linguistically formatted as imperatives.

But grammatically imperative wording does not make something an executable operator.

The target has merely been restated as if it were an action.

Thus:

\[
\boxed{
\text{linguistic action form}
\neq
\text{operational executability}
}
\]

---

## 10. Transition Information

Suppose a problem is represented as:

\[
s\neq d.
\]

An answer of the form:

```text
make s become d
```

contains almost no new transition information.

The planning problem is to identify:

\[
T:s\rightarrow d.
\]

Thus the usefulness of advice can partly be understood as the amount of decision-relevant information it contributes about:

```text
available transitions
required preconditions
sequence
constraints
cost
timing
failure modes
alternative routes
```

A tautological recommendation may be semantically correct while operationally empty.

This yields:

\[
\boxed{
\textbf{Transition-Information Principle}
}
\]

> Advice that merely restates a target state contributes little planning value unless it identifies executable transitions, preconditions, or route structure connecting the current state to that target.

---

## 11. Actionability Is Relative to the Agent

There is no universal lowest level at which instructions become executable.

Consider:

```text
search for information about X
```

For an experienced internet user, this may be primitive enough.

For another agent it may decompose into:

```text
open browser
↓
locate address/search field
↓
enter query
↓
interpret result list
↓
distinguish advertisement from result
↓
open promising page
↓
extract relevant information
```

Likewise:

```text
read the manual
```

may be executable for one agent and impossible for another because of:

```text
language
literacy
technical vocabulary
visual impairment
missing access
unknown file format
lack of prerequisite concepts
```

Therefore:

\[
\boxed{
\text{actionability is architecture-relative}
}
\]

An instruction is sufficiently decomposed when it reaches operators already supported by the current agent architecture.

---

## 12. The Primitive Executable Repertoire

Let:

\[
P_t
\]

be the set of actions that the planner treats as primitive relative to the current agent.

Examples may include:

```text
look
listen
move
speak
type
open a page
follow a link
ask a person
compare two objects
repeat a sound
copy text
try an operation
remember an observation
```

The exact set differs across agents.

Capability-route decomposition should continue until:

\[
a_i\in P_t
\]

or until a known composite action is already reliably executable.

This gives:

\[
\boxed{
\textbf{Relative Primitive Principle}
}
\]

> Stop decomposing an instruction when the next operation is already represented as reliably executable by the particular agent in the current context.

This avoids both extremes:

```text
too abstract:
    become fluent

unnecessarily microscopic:
    contract this specific muscle fiber
```

---

## 13. Bootstrap Actions

Some primitive actions are especially important because they permit the agent to change its own future possibilities.

These include epistemic operators such as:

```text
observe
compare
ask
search
read
imitate
try
test
measure
follow a reference
request explanation
```

These actions may reveal:

```text
new transitions
new resources
new constraints
new distinctions
new capability routes
new intervention types
```

Thus a small primitive repertoire can support much larger downstream adaptation.

For example:

\[
\text{search}
\rightarrow
\text{discover tutorial}
\rightarrow
\text{learn tool}
\rightarrow
\text{perform task}.
\]

Or:

\[
\text{ask}
\rightarrow
\text{discover local rule}
\rightarrow
\text{obtain authorization}
\rightarrow
\text{gain access}.
\]

These are bootstrapping routes.

---

## 14. Epistemic Pits

The pit problem has an informational analogue.

Suppose the agent lacks a concept that would reveal an important route.

If it can:

```text
observe anomaly
ask another agent
search external sources
experiment
compare successful and failed cases
```

then there may be a locally executable epistemic route toward a better representation.

But suppose the agent:

```text
has never encountered the missing phenomenon
cannot observe relevant evidence
cannot communicate with another agent
cannot search
cannot experiment
has no representation capable of expressing the distinction
```

Then the missing concept may be inaccessible from the current epistemic frontier.

Thus:

\[
\boxed{
\text{representation expansion also requires a locally executable route}
}
\]

The system cannot simply instruct itself:

```text
invent the missing concept.
```

That would reproduce the teleportation error at the representational level.

---

## 15. Maps as Decision-Relevant Representations

A map is not useful because it contains maximal information.

Its usefulness depends on a sufficiently reliable structural correspondence between representation and target domain.

Let:

\[
M
\]

be a map and:

\[
D
\]

the represented domain.

The purpose is not:

\[
M=D.
\]

Instead the map should preserve the distinctions needed for relevant decisions.

A subway map may distort geography while preserving:

```text
station ordering
line membership
interchange structure
service connectivity
```

A topographic map preserves different properties.

An accessibility map requires distinctions that an ordinary transit diagram may omit.

Thus the relevant standard is:

\[
\boxed{
\text{decision-relevant structural fidelity}
}
\]

rather than maximal descriptive fidelity.

---

## 16. The Map-Faithfulness Principle

This gives:

\[
\boxed{
\textbf{Map-Faithfulness Principle}
}
\]

> A planning representation should preserve the distinctions and transition relations necessary to predict decision-relevant feasibility in its target domain.

A representation can be:

```text
incomplete
coarse
geometrically distorted
abstract
compressed
```

and still be useful.

It fails when the omitted or distorted distinctions materially damage predictions about:

```text
what can be done
what cannot be done
what it will cost
what is required
what route will work
what intervention will change feasibility
```

---

## 17. Representation Failure as Prediction Failure

Suppose a representation predicts:

\[
\operatorname{Feasible}(a\mid s)=\text{true}
\]

but execution repeatedly fails.

Then some relevant distinction may be missing.

Conversely, suppose the model predicts:

\[
\operatorname{Feasible}(a\mid s)=\text{false}
\]

but observed agents repeatedly succeed.

Then the representation may be missing:

```text
an edge
a mode
a resource
a capability
an intervention
a compatibility relation
```

More generally:

\[
\boxed{
\text{systematic prediction error}
\rightarrow
\text{evidence of representational inadequacy}
}
\]

This does not identify the missing concept automatically.

But it provides a trigger for representational investigation.

---

## 18. Heterogeneous Outcomes Reveal Missing Distinctions

A particularly useful signal occurs when cases represented as equivalent produce systematically different transition outcomes.

Suppose:

\[
L(x_1)=L(x_2)
\]

under the current representation, but:

\[
\operatorname{Outcome}(x_1,a)
\neq
\operatorname{Outcome}(x_2,a)
\]

repeatedly.

Then the representation may be too coarse.

For example, an agent initially represents:

```text
website
```

as one category.

But some websites permit:

```text
read static content
```

while others require:

```text
authentication
form interaction
dynamic navigation
API access
account permissions
```

Repeatedly heterogeneous outcomes may justify splitting:

\[
\text{website}
\]

into more predictive categories.

Thus:

\[
\boxed{
\textbf{Predictive-Split Principle}
}
\]

> When one represented category produces materially heterogeneous action consequences, search for a distinction that better predicts feasibility and outcome.

This is one mechanism by which new map structure can be generated from experience.

---

## 19. Comparing Successful and Failed Cases

Suppose two superficially similar attempts differ:

```text
attempt A succeeds
attempt B fails
```

The planner can ask:

```text
What differed?
Which difference preceded the failure?
Which difference changes transition feasibility?
Can that difference be represented explicitly?
Does it recur across cases?
```

This process may discover variables such as:

```text
authorization
file type
language
timing
resource level
interface
jurisdiction
credential
prerequisite knowledge
physical compatibility
```

Thus successful and failed cases can function as contrastive evidence.

The important invariant is not:

```text
copy successful behavior blindly
```

but:

\[
\boxed{
\text{find distinctions that explain differences in transition outcomes}
}
\]

---

## 20. Navigation as a Model for Capability Planning

A useful capability planner could imitate the structure of navigation systems.

It asks:

### Current position

```text
What can the agent already do?
What does it know?
What tools can it use?
What resources can it access?
What is it authorized to do?
What can it currently represent?
```

### Destination

```text
What state would satisfy the demand?
```

### Constraints

```text
What prevents direct transitions?
Which blockers are known?
Which are unknown?
Which can the agent change?
```

### Modes

```text
What kinds of transitions exist?
practice
search
ask
purchase
borrow
study
move
request permission
experiment
delegate
combine tools
```

### Route evaluation

```text
Which route is fastest?
Which is cheapest?
Which is reliable?
Which creates useful future capabilities?
Which has maintenance debt?
Which depends on fragile infrastructure?
```

The result is not:

```text
become capable
```

but a route through capability space.

---

## 21. The Capability-Routing Principle

\[
\boxed{
\textbf{Capability-Routing Principle}
}
\]

> When a target requires a capability that the agent does not currently possess, search for a sequence of locally executable actions that changes the agent into states from which the required later actions become feasible.

This reframes:

```text
capability acquisition
```

as:

```text
path construction through architecture states.
```

The key object is not merely:

\[
K_{\text{missing}}.
\]

It is:

\[
\operatorname{Route}(X_t,X_{\text{enabling}}).
\]

---

## 22. Capability Prescription Versus Capability Route

Suppose a task requires programming competence.

A capability prescription says:

```text
learn programming.
```

A capability route may say:

```text
open interactive tutorial
↓
run first example
↓
modify one value
↓
observe output change
↓
learn variables
↓
write short program
↓
encounter error
↓
learn debugging
↓
combine concepts
↓
build small project
```

The route exposes:

```text
intermediate states
locally executable operations
feedback
newly enabled actions
```

The difference is structurally analogous to:

```text
go to Berlin
```

versus:

```text
walk 600 m
take train
change at station
take local transit
walk to destination
```

---

## 23. Frontier-Changing Steps as Route Segments

Consider:

\[
a_i^E:X_i\rightarrow X_{i+1}.
\]

The action is locally feasible at \(X_i\), but its importance lies partly in changing the next feasible set:

\[
A^F(X_{i+1})
\neq
A^F(X_i).
\]

For example:

```text
complete registration
```

may make:

```text
book service
```

feasible.

Then:

```text
book service
```

may make:

```text
use vehicle
```

feasible.

Then:

```text
use vehicle
```

may make:

```text
reach remote location
```

feasible.

Thus an endogenous capability route consists of locally feasible transitions whose cumulative effect changes the frontier.

---

## 24. No-Teleportation Principle

The core idea can be summarized as:

\[
\boxed{
\textbf{No-Teleportation Principle}
}
\]

> A planner may reason about distant target states and counterfactual architectures, but it must not treat them as directly selectable unless a locally feasible transition actually reaches them.

This applies equally to:

```text
physical movement
financial state
skill acquisition
social access
organizational change
software capability
representation
knowledge
authorization
```

Examples:

\[
\text{no home}
\not\xrightarrow{\text{primitive}}
\text{owns home}
\]

\[
\text{novice}
\not\xrightarrow{\text{primitive}}
\text{expert}
\]

\[
\text{no concept}
\not\xrightarrow{\text{primitive}}
\text{correct ontology}
\]

unless a real executable operator supports that transition.

---

## 25. Near-Feasible Routes

A useful planner need not consider only currently complete routes.

Suppose a desirable route contains one unavailable step.

For example:

```text
current skill
→ intermediate study
→ advanced course
→ target competence
```

but the advanced course requires:

```text
prerequisite mathematics.
```

The planner can preserve the near-feasible route and diagnose:

\[
B(p)=\{\text{prerequisite mathematics}\}.
\]

It can then search for a capability route to satisfy that blocker.

Thus route planning becomes recursive:

\[
\operatorname{Plan}(s,d)
\]

finds a promising route.

If a step is blocked by \(c\), then:

\[
\operatorname{Plan}(s,\operatorname{Satisfy}(c))
\]

may generate the enabling subroute.

This resembles route planning with intermediate waypoints, except the waypoints can alter the agent itself.

---

## 26. Feasible Decomposition

A high-level instruction may be recursively expanded:

```text
become fluent
```

into:

```text
learn language
```

then:

```text
use beginner course
```

then:

```text
complete lesson 1
```

then:

```text
listen to phrase
repeat phrase
compare output
```

At some level, the actions become executable.

This suggests:

\[
\boxed{
\textbf{Feasible-Decomposition Principle}
}
\]

> Recursively decompose a desired transformation until at least one next operation lies inside the current feasible-action set.

The decomposition need not produce the entire future plan with certainty.

It must produce a grounded next step and a plausible route structure.

---

## 27. Why the First Step Matters Disproportionately

Distant plans are uncertain.

The future world may change.

The agent may learn.

New opportunities may appear.

Therefore the planner does not need perfect foresight over every future transition.

But it must avoid fictionalizing the first transition.

This gives an asymmetric standard:

\[
\boxed{
\text{high confidence in local executability}
}
\]

with potentially lower confidence in:

\[
\text{distant route details}.
\]

This resembles navigation under changing traffic.

The exact downstream route can be recomputed.

But the next maneuver must be executable now.

---

## 28. Replanning After Capability Change

After executing:

\[
a_t^E
\]

the agent should not blindly continue an old capability route.

Instead:

```text
act
↓
observe new state
↓
update representation
↓
recompute feasible frontier
↓
replan toward target
```

New capabilities may expose better routes than those predicted before acquisition.

Likewise, an attempted capability change may fail.

Thus:

\[
\boxed{
\text{capability routing should be receding-horizon rather than rigid}
}
\]

when uncertainty is substantial.

---

## 29. Unreachable Targets

A route planner should sometimes conclude:

```text
no currently represented reachable route.
```

This is different from:

```text
the target is metaphysically impossible.
```

The absence of a represented route may result from:

```text
genuine physical impossibility
missing capability
missing resource
missing authorization
unknown constraint
missing representation
insufficient search
```

The planner should preserve this uncertainty.

But it should also avoid pretending that:

```text
desiring the target strongly
```

creates an edge.

Thus:

\[
\boxed{
\text{goal importance does not imply reachability}
}
\]

---

## 30. Structural Evaluation of Advice

Advice can be evaluated using a simple schema.

Given:

\[
(s,d,r)
\]

where \(r\) is a recommendation, ask:

```text
1. Does r describe a target or an operator?
2. Are the preconditions of r represented?
3. Are those preconditions currently satisfied?
4. If not, does r include a route to satisfy them?
5. Does at least one recommended first step lie in A^F(s)?
6. Does the route explain how later actions become feasible?
7. Are important uncertainties exposed rather than silently treated as false?
8. Can the route be replanned when observation differs from prediction?
```

A recommendation that fails at step 5 is not operationally grounded.

---

## 31. The Route-Grounded Advice Principle

\[
\boxed{
\textbf{Route-Grounded Advice Principle}
}
\]

> Advice intended to change an agent's state should identify at least one locally executable transition and should explain, explicitly or implicitly, how successive transitions can make later required actions feasible.

This does not require every answer to contain exhaustive instructions.

It requires the planner to avoid substituting:

```text
description of desired outcome
```

for:

```text
route from current conditions.
```

---

## 32. Applications

### 32.1 Housing

Target:

```text
stable housing
```

Bad transition model:

```text
homeless
→ buy house
```

Better route planning may inspect:

```text
current shelter
identity documents
income
benefits
waiting lists
local programs
social contacts
deposit requirements
transport
temporary accommodation
```

The appropriate route depends on the actual state.

---

### 32.2 Debt

Target:

```text
sustainable finances
```

Bad transition model:

```text
debt
→ repay debt
```

Useful route variables include:

```text
income
interest rate
minimum payments
legal protections
refinancing
restructuring
expenses
deadlines
liquidity
```

Again, the target is not the transition.

---

### 32.3 Expertise

Target:

```text
domain expertise
```

Bad transition model:

```text
novice
→ study
→ expert
```

Capability routing may require:

```text
prerequisite vocabulary
foundational concepts
practice tasks
feedback
error diagnosis
source evaluation
projects
exposure to edge cases
```

The route is often hierarchical and nonuniform.

---

### 32.4 Foreign-language reading

Target:

```text
read novels
```

Possible route:

```text
learn script
→ learn pronunciation
→ acquire common vocabulary
→ read graded material
→ infer meaning from context
→ tolerate ambiguity
→ read ordinary prose
→ read novels
```

Each intermediate capability exists partly because it enables later transitions.

---

### 32.5 Expressing Thoughts

Target:

```text
express complex thoughts clearly
```

A feasible route may begin with:

```text
write rough paragraph
→ identify one unclear sentence
→ generate alternative formulations
→ compare meanings
→ notice recurring ambiguity
→ learn distinction
→ reuse distinction
```

The first useful action may be extremely local.

---

## 33. A Unified Control Loop

```text
OBSERVE CURRENT STATE
↓
represent current capabilities, resources, access, knowledge, and constraints
↓
receive target state or demand
↓
search for route
↓
does the route begin with a locally executable step?
├── yes
│   ↓
│   execute
│   ↓
│   observe result
│   ↓
│   update state and representation
│   ↓
│   recompute feasible frontier
│   ↓
│   replan
│
└── no
    ↓
    inspect why the first required step is unavailable
    ↓
    is the blocker unknown?
    ├── yes
    │   ↓
    │   search / ask / test / observe / compare
    │   ↓
    │   update representation
    │
    └── no
        ↓
        classify blocker
        ↓
        capability / resource / authorization / compatibility /
        location / representation / external immutable
        ↓
        search for locally executable route to change blocker
        ↓
        if such a route exists:
            insert enabling subroute
        else:
            preserve target as currently unreachable
```

This recursively converts abstract desired transformations into executable routes.

---

## 34. The Deeper Interpretation

The central planning problem is not:

\[
\text{What state would be better?}
\]

That is often easy to answer.

Nor is it merely:

\[
\text{What capability would solve the problem?}
\]

That can still generate unreachable prescriptions.

The stronger question is:

\[
\boxed{
\text{What can the agent do from here that changes what can be done next?}
}
\]

Repeated recursively:

\[
\boxed{
\text{current state}
\rightarrow
\text{locally feasible action}
\rightarrow
\text{new state}
\rightarrow
\text{newly feasible action}
\rightarrow
\cdots
\rightarrow
\text{target}
}
\]

This is ordinary route planning extended into capability, resource, epistemic, and representational space.

The agent does not need the destination to be immediately executable.

It needs a path whose first edge is.

---

## 35. Core Principles

### Local Executability Principle

> Every frontier-changing action must itself be executable from the current feasible frontier.

### No-Teleportation Principle

> A desired future state or architecture must not be treated as directly selectable unless an executable transition reaches it.

### Capability-Routing Principle

> Missing capabilities should be treated as destinations in architecture space, with routes constructed from currently executable actions.

### Instrumental-State Principle

> Intermediate capabilities may be valuable because of the transitions they enable rather than because they are independently desired.

### Relative Primitive Principle

> An instruction is sufficiently decomposed when its next operation is already executable by the particular agent in the current context.

### Map-Faithfulness Principle

> Representations should preserve the distinctions required to predict decision-relevant feasibility in the target domain.

### Predictive-Split Principle

> Repeatedly heterogeneous outcomes among states represented as equivalent are evidence that a new distinction may be required.

### Feasible-Decomposition Principle

> Decompose desired transformations until at least one next operation belongs to the current feasible-action set.

### Route-Grounded Advice Principle

> Useful advice should identify a locally executable transition and a plausible route by which later required actions become feasible.

---

## 36. Conclusion

A bounded agent cannot act from the state it wishes it occupied.

It acts from the state it actually occupies, using capabilities it currently possesses, resources it currently accesses, distinctions it currently represents, and transitions it can currently execute.

Therefore:

\[
\boxed{
\text{the destination can be distant, but the next action must be local}
}
\]

This principle is obvious in navigation.

It should be equally binding in:

```text
learning
finance
housing
career development
software
organizations
physical problem solving
social access
representation change
capability acquisition
```

A route planner earns its usefulness by filling the space between:

\[
\textbf{YOU ARE HERE}
\]

and:

\[
\textbf{YOU WANT TO BE HERE}.
\]

A general bounded-agent planner should do the same.

The difficult part is not naming the desirable state.

The difficult part is constructing a sequence in which:

\[
\boxed{
\text{every next step is executable when reached}
}
\]

and in which some of those steps deliberately change the set of actions that will become possible afterward.

That is the core structure of locally executable capability routing.
