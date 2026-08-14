# From Action Labels to Adaptive Operator Refinement: Execution Kernels, Capability Combinators, and Bootstrapping Routes

## Abstract

A planning graph needs edges.

But what should an edge be?

A high-level action such as:

```text
ask
search
learn
move
repair
investigate
obtain information
```

is often useful for reasoning while being too abstract to execute directly.

A lower-level action such as:

```text
ask parent
search room
open browser
follow link
speak sentence
move hand
```

may be executable for one agent and still decomposable for another.

If decomposition is pushed far enough, almost every familiar action disappears into lower-level control, physiology, electronics, or physics.

Thus there is no obvious universal action vocabulary at which planning graphs should stop.

This paper develops a different view.

The central claim is:

\[
\boxed{
\text{an edge need not be primitive; it must be refinable into a locally executable realization when execution becomes consequential}
}
\]

This separates several objects that are often conflated:

```text
operator interface
concrete method
execution primitive
strategy
refinement relation
control combinator
```

A generic operator such as:

```text
ask(x,q)
```

can be treated as an interface or transition contract.

It may have many implementations:

```text
ask parent
ask teacher
ask colleague
ask librarian
ask web service
ask language model
```

Each implementation can itself decompose into lower-level operations until the decomposition reaches operations already supported by the current agent architecture.

The primitive layer is therefore agent-relative and controller-relative rather than metaphysically fixed.

Let:

\[
K_t
\]

be the current execution kernel: operations the planning layer can invoke without further internal planning.

Let:

\[
M_t
\]

be the currently available library of composite methods.

Let:

\[
\mathcal C
\]

be a small set of control and capability combinators such as sequencing, choice, iteration, binding, testing, delegation, and refinement.

Then much of the agent's effective action repertoire can be understood as a grounded closure:

\[
\boxed{
A_t^F
\subseteq
\operatorname{Closure}(K_t\cup M_t;\mathcal C,X_t)
}
\]

subject to current resources, access, constraints, representation, and world conditions.

This gives a stronger interpretation of capability bootstrapping.

The basic bootstrapping resources need not be generic words such as `ask` or `search`.

They may instead begin as concrete, locally executable routines:

```text
ask parent
imitate teacher
search room
point at object
repeat sound
follow instruction
try visible control
compare outcomes
```

From repeated concrete routines, the agent may discover common structure, construct generic operators, bind those operators to new targets, compose them into larger methods, and eventually acquire new execution mechanisms.

Capability growth then becomes not merely frontier expansion over a fixed action vocabulary, but growth in the system that generates, refines, binds, and realizes action descriptions.

The resulting architecture is hierarchical, typed, demand-refined, and locally grounded.

The action graph does not need atomic edges everywhere.

It needs enough structure to answer:

\[
\boxed{
\text{Can this candidate transition be realized from here, and if not, what part must be refined?}
}
\]

---

## 1. The Edge Problem

Suppose an agent wants to represent:

```text
ask for help
```

as an action.

At one level this is reasonable.

But what exactly is the edge?

Possible realizations include:

```text
ask parent verbally
ask teacher after class
send colleague a message
call support
enter query into web search
post on forum
ask a language model
signal another person physically
```

The abstract action:

\[
\operatorname{Ask}(q)
\]

does not identify:

```text
who is asked
how they are reached
which communication channel is used
how the question is encoded
whether the recipient can interpret it
how the answer is received
how the answer is recognized
```

Thus:

\[
\boxed{
\text{useful action label}
\neq
\text{complete execution specification}
}
\]

But the opposite extreme is also unhelpful.

If `ask parent` must always be decomposed into:

```text
turn head
locate parent
walk
coordinate speech muscles
produce pressure waves
receive auditory signal
perform linguistic parsing
```

then the planning representation becomes unnecessarily microscopic.

The problem is therefore not simply:

```text
find the primitive action vocabulary.
```

It is:

```text
find the appropriate action resolution for the current agent, controller, target, and execution context.
```

---

## 2. Action Descriptions Are Resolution Choices

An action can be represented at several resolutions.

For example:

```text
get information
```

may refine to:

```text
search
```

then:

```text
search web
```

then:

```text
open browser
enter query
inspect result list
open promising result
extract relevant statement
```

and, if necessary, further to:

```text
activate device
locate browser icon
move pointer
tap icon
wait for interface
focus search field
produce character sequence
submit input
```

No level is universally the correct one.

A description is sufficient when the next relevant transition is already supported by the current architecture.

Thus action resolution is analogous to representational resolution.

The system should not maximize decomposition.

It should decompose until operational continuation is grounded.

\[
\boxed{
\text{decompose until executable, not until physically atomic}
}
\]

---

## 3. Four Different Objects Should Be Separated

A useful action architecture should distinguish at least four levels.

### 3.1 Operator interface

An operator interface specifies a useful transformation contract.

For example:

\[
\operatorname{Ask}(x,q)
\]

may mean approximately:

```text
precondition:
    x can potentially receive a question from the agent

intended effect:
    obtain a response relevant to q
```

The interface need not specify the realization.

---

### 3.2 Concrete method

A method is one implementation of an operator.

For example:

\[
\operatorname{AskParent}(q)
\]

or:

\[
\operatorname{AskTeacher}(q)
\]

or:

\[
\operatorname{AskWebService}(q).
\]

A method specifies more concrete preconditions, resources, bindings, costs, and suboperations.

---

### 3.3 Execution primitive

An execution primitive is an operation treated as directly invocable by the planning layer in the current architecture.

Examples might include:

```text
orient
look
listen
move to reachable point
speak phrase
press interface control
copy symbol sequence
hold object
release object
```

but the exact set is agent-relative.

---

### 3.4 Strategy

A strategy is a conditional organization of operators or methods.

For example:

```text
resolve unknown q:
    if answer remembered:
        retrieve
    else if relevant source visible:
        inspect
    else if knowledgeable person accessible:
        ask
    else if searchable system available:
        search
    else if experiment possible:
        test
    else:
        preserve unresolved
```

A strategy is not one edge.

It is a policy over possible edges.

---

## 4. Interfaces Are Not Executions

Suppose a planner stores:

\[
\operatorname{Search}(d,q)
\]

where:

```text
d = search domain
q = target query or condition
```

This may be a valid planning operator.

But it should not be treated as directly executable merely because the word `search` exists in the ontology.

There must be some realizable method:

\[
m\in \operatorname{Methods}(\operatorname{Search},X_t).
\]

Examples:

```text
search room visually
search desk manually
search local filesystem
search phone app
search browser
search institutional database
search memory
```

Thus:

\[
\boxed{
\textbf{Interface-Method Separation Principle}
}
\]

> A generic action operator may be used for planning and abstraction, but its execution requires at least one method whose preconditions and realization are grounded in the current agent state.

---

## 5. The Execution Kernel

Let:

\[
K_t
\]

be the **execution kernel** at time \(t\).

It contains the operations the relevant planning layer may invoke without decomposing them further.

Formally:

\[
K_t
=
\{k_1,k_2,\ldots\}.
\]

The kernel is not universal.

For a human task planner it may include:

```text
walk to visible place
say sentence
read ordinary text
pick up ordinary object
write short text
use familiar phone interface
```

For an infant it may be much smaller.

For a software agent it may include:

```text
invoke tool
send HTTP request
read file
write file
parse structured output
```

For a robot mission planner it may include:

```text
navigate_to(x)
pick(object)
place(object,target)
inspect(region)
```

while the navigation and manipulation subsystems decompose those operations internally.

Thus:

\[
\boxed{
\textbf{Relative Execution-Kernel Principle}
}
\]

> Primitive executability is relative to the controller boundary: an operation is primitive for a planning layer when a lower layer already provides a reliable implementation contract for it.

---

## 6. Primitiveness Is Not an Intrinsic Property

Consider:

\[
\operatorname{WalkToKitchen}.
\]

For one adult, this may be primitive enough.

For a person learning to use a prosthetic device, it may require active decomposition.

For a robot mission planner:

\[
\operatorname{NavigateTo}(x)
\]

may be a primitive service call.

For the navigation controller it decomposes into:

```text
localization
path generation
obstacle detection
trajectory control
motor commands
```

For the motor controller, those commands decompose further.

Therefore:

\[
\operatorname{Primitive}(a)
\]

is too strong.

A more useful predicate is:

\[
\boxed{
\operatorname{Primitive}(a\mid A,t,L)
}
\]

where:

```text
A = agent architecture
 t = current state/time
 L = control layer
```

The same operation can be primitive at one layer and composite at another.

---

## 7. The Refinement Relation

Let:

\[
o
\]

be an abstract operator.

Let:

\[
\rho(o)
\]

be a refinement of that operator into a sequence, policy, or subgraph of more concrete operations.

Write:

\[
\boxed{
o
\rightsquigarrow
\rho(o)
}
\]

For example:

\[
\operatorname{Ask}(x,q)
\rightsquigarrow
\operatorname{Access}(x)
\rightarrow
\operatorname{Encode}(q)
\rightarrow
\operatorname{Signal}(x,q)
\rightarrow
\operatorname{Receive}
\rightarrow
\operatorname{Interpret}.
\]

Or:

\[
\operatorname{SearchRoom}(y)
\rightsquigarrow
\operatorname{Orient}
\rightarrow
\operatorname{InspectRegion}
\rightarrow
\operatorname{CompareWithTarget}
\rightarrow
\operatorname{MoveOrManipulate}
\rightarrow
\operatorname{RepeatUntilFoundOrExhausted}.
\]

A refinement can itself contain abstract operators.

Thus refinement is recursive.

---

## 8. Executability Requires a Realization Witness

A high-level edge should be admitted as operationally executable only if there exists at least one currently realizable refinement.

Let:

\[
\operatorname{Ref}(o,X_t)
\]

be the set of represented refinements available for operator \(o\) in architecture state \(X_t\).

Then:

\[
\boxed{
\operatorname{Executable}(o\mid X_t)
\iff
\exists \rho\in \operatorname{Ref}(o,X_t)
:\operatorname{Grounded}(\rho\mid X_t)
}
\]

where `Grounded` means that execution can recursively reach operations supported by the current execution kernel while satisfying their sequential preconditions.

The refinement therefore acts as an **execution witness**.

This gives:

\[
\boxed{
\textbf{Refinement-Witness Principle}
}
\]

> A macro-edge may remain abstract in the planning graph, but before consequential execution the system must possess or construct at least one refinement that grounds the edge in currently executable operations.

---

## 9. Recursive Grounding

Suppose:

\[
\rho=(a_1,\ldots,a_n).
\]

Let:

\[
X_0=X_t
\]

and:

\[
X_i=F(X_{i-1},a_i).
\]

Then a sequential refinement is grounded when:

\[
\boxed{
a_i\in K(X_{i-1})
\quad\text{or has a grounded refinement at }X_{i-1}
}
\]

for every step.

More compactly:

\[
\operatorname{Grounded}(a,X)
=
\begin{cases}
\text{true}, & a\in K(X) \text{ and preconditions hold}\\
\exists \rho\in\operatorname{Ref}(a,X):\operatorname{Grounded}(\rho,X), & \text{otherwise.}
\end{cases}
\]

This recursively combines hierarchical decomposition with local executability.

---

## 10. No-Facade Executability

A generic API-like action can hide implementation complexity.

That is useful.

But it creates a failure mode.

Suppose the planner contains:

```text
search_web(q)
```

while the agent currently has:

```text
no device
no network
no browser
no account
no interface knowledge
```

The existence of the interface in the planner does not create an execution path.

Similarly:

```text
ask expert
```

is not executable when no expert is reachable through any usable communication channel.

Thus:

\[
\boxed{
\textbf{No-Facade Executability Principle}
}
\]

> The presence of an action interface, command name, instruction, or conceptual operator does not imply executability; executability depends on a grounded realization under current constraints.

This is the action-level analogue of not confusing a desired state with a transition.

---

## 11. Search Is Usually a Strategy, Not a Primitive

The word:

```text
search
```

can hide several different structures.

A generic search process may contain:

\[
\boxed{
\text{generate locus}
\rightarrow
\text{access locus}
\rightarrow
\text{observe}
\rightarrow
\text{compare}
\rightarrow
\text{update}
\rightarrow
\text{select next locus}
\rightarrow
\text{repeat}
}
\]

Different search methods instantiate the same rough pattern differently.

### Room search

```text
choose region
look
move objects if necessary
compare observed item with target
continue
```

### Filesystem search

```text
choose directory or index
invoke search operation
inspect matches
refine query
continue
```

### Web search

```text
choose service
form query
submit
inspect result summary
open candidate
validate relevance
reformulate if necessary
```

### Memory search

```text
activate cue
retrieve candidate
compare candidate to target need
change cue if unsuccessful
```

The generic operator is useful because it compresses common structure.

But no claim is required that `search` is biologically, computationally, or physically primitive.

---

## 12. Ask Is Usually a Communication Program

Likewise:

```text
ask
```

is better treated as a family of methods around a communication contract.

A simplified decomposition is:

\[
\boxed{
\operatorname{Ask}
\approx
\operatorname{SelectRecipient}
\circ
\operatorname{AccessChannel}
\circ
\operatorname{EncodeQuestion}
\circ
\operatorname{Signal}
\circ
\operatorname{Receive}
\circ
\operatorname{Interpret}
}
\]

Some methods collapse several components.

For example:

```text
ask parent verbally
```

may already be a familiar chunk.

Others require substantial setup:

```text
ask remote specialist
→ identify specialist
→ obtain contact mechanism
→ create account
→ request access
→ formulate message
→ send
→ wait
→ interpret response
```

The same operator interface can therefore have very different transition costs and prerequisite structures.

---

## 13. Generic Operators Can Be Polymorphic

An operator can be parameterized over target, resource, channel, or method class.

For example:

\[
\operatorname{Ask}(x,q,c)
\]

where:

```text
x = respondent
q = question
c = communication channel
```

or:

\[
\operatorname{Search}(d,q,m)
\]

where:

```text
d = domain
q = sought condition
m = search method
```

A planner may reason with partially bound operators:

\[
\operatorname{Ask}(?,q,?)
\]

and later solve the binding problem:

```text
who is reachable?
who is likely to know?
which channel is available?
which method is cheap enough?
```

Thus action selection can include **operator binding** rather than only choosing among fully instantiated edges.

---

## 14. Binding Is One of the Fundamental Capability Operations

Suppose an agent knows a generic method schema:

\[
M(x,q).
\]

The schema becomes executable only after parameters are bound to locally available objects.

For example:

\[
\operatorname{Ask}(x,q)
\]

becomes:

\[
\operatorname{Ask}(\text{teacher},q)
\]

when:

```text
teacher is present
communication is permitted
shared language exists
teacher is an appropriate information source
```

Binding therefore converts abstract capability into situated capability.

\[
\boxed{
\text{generic method}
+
\text{local binding}
\rightarrow
\text{candidate executable method}
}
\]

This is analogous to substituting values into a function.

---

## 15. Capability Combinators

If `ask`, `search`, and `learn` are not universal primitives, what plays the role of arithmetic or logical operators in capability construction?

The strongest candidates are not domain verbs.

They are **combinators** that organize grounded operations into larger methods.

A small control algebra may include:

```text
SEQUENCE
CHOICE
CONDITION
ITERATE
BIND
COMPARE / TEST
OBSERVE
TRANSFORM
DELEGATE / INVOKE
COMPOSE
RETAIN / RETRIEVE
REFINE
```

These are still representational abstractions rather than metaphysical atoms.

But they recur across many method families.

---

## 16. Sequence

The simplest combinator is sequential composition.

If:

\[
a:X\rightarrow Y
\]

and:

\[
b:Y\rightarrow Z,
\]

then:

\[
\boxed{
b\circ a:X\rightarrow Z.}
\]

Most capabilities are constructed from sequences whose intermediate states satisfy later preconditions.

For example:

```text
open browser
→ enter query
→ inspect result
```

or:

```text
obtain document
→ read requirement
→ submit application
```

Sequence is therefore central to capability routing.

---

## 17. Choice and Condition

A capable agent often does not possess one fixed realization.

It possesses alternatives.

Let:

\[
\rho_1,\rho_2,\ldots,\rho_n
\]

be methods implementing the same interface.

Then:

\[
\operatorname{Choice}(\rho_1,\ldots,\rho_n)
\]

selects among them according to current state.

For example:

```text
need information
├── person nearby → ask
├── manual available → read
├── network available → search web
├── safe experiment possible → test
└── none available → preserve unresolved
```

This turns an abstract capability into a dispatch structure.

---

## 18. Iteration

Many useful operators are not one-shot transitions.

Search, practice, debugging, learning, and experimentation often have the form:

\[
\boxed{
\operatorname{Repeat}(a)
\text{ until }c
}
\]

For example:

```text
observe
compare to target
modify
repeat
```

Iteration can transform a weak primitive repertoire into a much more powerful adaptive process.

An agent need not know the complete solution before acting if it can repeatedly:

```text
try
observe
compare
update
```

under useful stopping conditions.

---

## 19. Observation and Test

Some operations primarily change the agent's information state.

Let the full planning state be:

\[
Z_t=(S_t,X_t,L_t,C_t),
\]

where:

```text
S_t = task/world-relative state
X_t = capability/resource/access architecture
L_t = representation or belief state
C_t = represented constraints
```

An observation can leave the physical component nearly unchanged while changing:

\[
L_t\rightarrow L_{t+1}.
\]

Likewise a test can change:

\[
c=\text{unknown}
\]

into:

\[
c=\text{true}
\]

or:

\[
c=\text{false}.
\]

Thus epistemic actions are ordinary state transitions in an enriched state model.

They do not require a separate terminal objective.

---

## 20. Information Acquisition Serves the Same Route

Suppose the agent wants target \(D\).

It has candidate route \(p\), but a required constraint is insufficiently known:

\[
\operatorname{Conf}(c)<\theta.
\]

Then the next locally executable action may be:

\[
a_t=\operatorname{Verify}(c).
\]

The structure is:

```text
target D
→ candidate route p
→ route requires c
→ confidence in c below sufficient threshold
→ verify c
→ update represented route feasibility
→ continue or replan toward D
```

The information action is not an unrelated goal.

It is a subroute created by the same target.

Thus:

\[
\boxed{
\textbf{Information-Route Integration Principle}
}
\]

> Information gathering should be represented as part of the same target-directed route whenever uncertainty about a transition, constraint, or method blocks sufficiently reliable continuation.

---

## 21. Transform and Acquire

Some combinators organize changes to controlled state.

A generic transformation can be written:

\[
\operatorname{Transform}(x,f):x\rightarrow f(x).
\]

Examples include:

```text
move object
edit file
change parameter
translate representation
reshape material
practice procedure
```

A generic acquisition schema is:

\[
\boxed{
\operatorname{Acquire}(r):
\neg Accessible_t(r)
\rightarrow
Accessible_{t+1}(r)
}
\]

Examples:

```text
pick up tool
borrow book
download file
obtain authorization
receive answer
install software
acquire skill
```

The concrete method determines how acquisition occurs.

---

## 22. Release, Separate, and Reconfigure

Frontier change is not only additive.

An agent may need to:

```text
release resource
remove dependency
delete obsolete structure
separate coupled components
abandon method
unlearn bad mapping
revoke permission
switch provider
```

Thus capability algebra should not be interpreted as monotonically adding actions.

One generic family is:

\[
\operatorname{Release}(r):
Controlled_t(r)
\rightarrow
\neg Controlled_{t+1}(r).
\]

Another is:

\[
\operatorname{Separate}(z)\rightarrow(x,y,\ldots).
\]

A third is:

\[
\operatorname{Reconfigure}(X_t)\rightarrow X_{t+1}.
\]

These operators may improve future feasibility by reducing maintenance debt or removing constraints.

---

## 23. Delegation and Invocation

A powerful class of bootstrapping methods invokes capability already embodied elsewhere.

Examples:

```text
ask parent
ask teacher
call technician
use calculator
invoke compiler
use navigation system
query database
use language model
```

Delegation can be represented as:

\[
\operatorname{Delegate}(B,g)
\]

where another agent or subsystem \(B\) performs some transformation relevant to goal \(g\).

Delegation does not magically import all of \(B\)'s internal capabilities into the planner.

It creates an executable interface edge only when:

```text
B is accessible
invocation protocol is usable
inputs can be encoded
outputs can be received
trust or validation conditions are adequate
```

This makes `ask parent` a particularly important bootstrap routine.

It is a locally executable path to capability that already exists in another architecture.

---

## 24. Concrete Bootstrap Routines Come Before Universal Abstractions

A child need not begin with the abstract operator:

\[
\operatorname{Ask}(x,q).
\]

It may begin with learned or scaffolded routines such as:

```text
ask parent
point at desired object
imitate adult
repeat demonstrated sound
look where adult points
search familiar room
try visible control
```

These are concrete methods tied to specific people, places, channels, and situations.

Only later may the agent observe structural similarity among:

```text
ask parent
ask teacher
ask older sibling
ask librarian
```

and construct a more general schema:

\[
\operatorname{Ask}(x,q).
\]

Thus abstraction can proceed from grounded methods upward.

\[
\boxed{
\text{specific executable routines}
\rightarrow
\text{comparison}
\rightarrow
\text{shared structure}
\rightarrow
\text{generic operator}
}
\]

This is the reverse of assuming a universal abstract action vocabulary first.

---

## 25. Method Abstraction

Suppose several methods:

\[
m_1,m_2,m_3
\]

have similar transition structure.

The agent may construct an abstraction:

\[
O
\]

such that:

\[
m_i\models O.
\]

For example:

```text
ask parent
ask teacher
ask librarian
```

may share:

```text
select respondent
signal information need
receive response
interpret response
```

The abstraction reduces planning cost and enables transfer.

Later a novel implementation:

```text
ask remote service
```

can be recognized as another method satisfying the same operator contract.

This produces reusable action semantics without requiring that the abstract operator was originally primitive.

---

## 26. Method Specialization

Abstraction is only half of the process.

A generic operator may need specialization when current conditions make its hidden differences consequential.

Suppose the planner treats:

```text
ask person
```

as one category.

Repeated outcomes may reveal useful distinctions:

```text
ask trusted expert
ask stranger
ask authority
ask person with no shared language
ask person who controls permission
```

The generic operator can then split into specialized subtypes.

Likewise:

```text
search web
```

may split according to:

```text
authenticated search
public search
structured database query
dynamic website interaction
local index search
```

when their execution requirements diverge.

Thus operator schemas should remain mutable.

---

## 27. Failure-Directed Action Refinement

A macro-edge should not be decomposed merely because finer detail exists.

It should be refined when the current abstraction fails to predict or support execution.

Suppose:

\[
\operatorname{Executable}(o\mid X_t)=\text{predicted true}
\]

but execution fails.

Possible causes include:

```text
missing precondition
wrong method binding
hidden authorization requirement
unavailable resource
incorrect interface assumption
missing intermediate step
wrong decomposition
representation too coarse
```

The system should localize the failure and refine the implicated operator.

\[
\boxed{
\textbf{Failure-Directed Refinement Principle}
}
\]

> When an abstract action fails, increase action resolution around the failed realization or hidden precondition rather than globally decomposing the entire action model.

---

## 28. Adaptive Action Resolution

This yields an action-side analogue of adaptive semantic resolution.

The planner begins with the coarsest action description sufficient for current continuation.

If the edge is supported by a reliable method, retain the abstraction.

If continuation fails because executability cannot be established, refine the local action frontier.

A control loop is:

```text
CURRENT TARGET
↓
construct candidate route at current action resolution
↓
next macro-edge available?
├── yes
│   ↓
│   grounded realization already known?
│   ├── yes
│   │   ↓
│   │   execute
│   │   ↓
│   │   observe result
│   │   ↓
│   │   retain abstraction if prediction remains adequate
│   │
│   └── no
│       ↓
│       refine edge locally
│       ↓
│       bind target / resource / channel / method
│       ↓
│       recursively test executability
│
└── no
    ↓
    diagnose blocking capability, resource, representation, or access condition
    ↓
    search for locally executable enabling route
```

Thus:

\[
\boxed{
\textbf{Adaptive Action-Resolution Principle}
}
\]

> Preserve coarse action operators while they support reliable continuation; refine only the action frontier whose hidden realization prevents local executability from being established.

---

## 29. Semantic Resolution and Action Resolution Are Dual Problems

A bounded agent faces two related compression problems.

### Semantic side

```text
How much of the world must be distinguished to decide what to do?
```

### Action side

```text
How much of the transition must be decomposed to establish that it can be done?
```

Both admit the same broad policy:

```text
preserve useful abstraction
refine locally under pressure
stop when sufficient continuation is restored
```

Thus:

\[
\boxed{
\text{adaptive semantic resolution}
\leftrightarrow
\text{adaptive action decomposition}
}
\]

The first refines state representation.

The second refines transition representation.

A general planner needs both.

---

## 30. The Action Graph Can Be Hierarchical

A conventional graph uses edges:

\[
e=(u,v).
\]

A hierarchical capability graph can instead store something closer to:

\[
e=
(u,v,O,P,E,R,\mathcal M,\Gamma),
\]

where:

```text
O   operator/interface type
P   represented preconditions
E   represented effects
R   resource/access requirements
M   known implementation methods
Γ   refinement or decomposition metadata
```

An edge may therefore represent:

```text
abstract contract
+
known realizations
+
conditions under which each realization applies
```

The graph need not flatten every method into primitive edges before planning begins.

---

## 31. Abstract Search Can Precede Concrete Refinement

Suppose a high-level planner compares:

```text
ask knowledgeable person
search documentation
experiment directly
```

It may not need to expand every candidate fully.

It can first estimate:

```text
expected relevance
cost
latency
risk
known feasibility
refinement burden
```

Only a promising candidate may need detailed grounding.

This resembles lazy evaluation.

\[
\boxed{
\text{plan coarsely where sufficient; refine the branch that becomes consequential}
}
\]

This avoids combinatorial explosion from eagerly decomposing every possible route.

---

## 32. Executability Proofs Can Be Cached

Once an agent has repeatedly executed:

```text
search familiar browser
```

successfully, it need not reconstruct the decomposition every time.

The method can become a cached executable chunk.

Let:

\[
\operatorname{Witness}(o,X_c)=\rho
\]

be a previously validated realization under context class \(X_c\).

Future execution may reuse \(\rho\) while its validity conditions remain satisfied.

If relevant dependencies change:

```text
browser removed
interface redesigned
account expired
network unavailable
```

then the witness becomes stale and may require refinement or reacquisition.

Thus method libraries have the same retention, invalidation, and revalidation problems as semantic structures.

---

## 33. Learned Chunks Change the Execution Kernel

A composite action can become effectively primitive through practice, tooling, compilation, automation, or delegation.

Initially:

```text
open editor
create file
write boilerplate
invoke compiler
inspect error
```

may require active planning.

Later:

```text
build project
```

may become a reliable chunk.

Likewise a trained physical sequence may become executable without conscious decomposition.

Thus:

\[
K_{t+1}\neq K_t
\]

can occur even when the underlying physical primitives remain unchanged.

The architectural boundary of what the planner treats as primitive can migrate upward.

This is a form of capability compression.

---

## 34. Tools Can Compile Composite Methods Into New Primitives

A tool may package a long action route behind a short interface.

For example:

```text
manual arithmetic sequence
→ calculator button sequence
```

or:

```text
manual deployment procedure
→ deploy command
```

or:

```text
many navigation operations
→ navigate_to(destination)
```

A capability-changing intervention can therefore create a new effective primitive:

\[
\rho
\rightarrow
k_{new}.
\]

This is one reason tool acquisition can expand the feasible-action frontier dramatically.

The tool does not create magic.

It encapsulates or delegates a realizable process behind a new invocation contract.

---

## 35. Bootstrapping as Growth of the Method-Generation System

Capability expansion is often described as acquiring more actions.

A stronger view is that the agent acquires mechanisms for constructing actions it did not previously know how to realize.

For example:

```text
ask parent
→ receive demonstration
→ imitate demonstration
→ compare outcome
→ repeat
→ stabilize method
→ generalize method
→ apply method in novel context
```

The result is not merely one new edge.

The agent may gain a reusable method schema with many future bindings.

Thus bootstrapping can expand:

```text
method library
operator library
binding competence
refinement competence
delegation access
execution kernel
representation of preconditions
```

simultaneously.

---

## 36. A Grounded Closure Model

Let:

\[
K_t
\]

be the execution kernel.

Let:

\[
M_t
\]

be the currently known composite methods.

Let:

\[
I_t
\]

be the represented operator interfaces.

Let:

\[
\mathcal C
\]

be the available capability combinators.

Let:

\[
B_t
\]

be the currently available bindings over agents, resources, locations, tools, and channels.

Then define the represented constructible action space:

\[
\mathcal A_t^{C}
=
\operatorname{Closure}
(
K_t\cup M_t\cup I_t;
\mathcal C,
B_t
).
\]

The feasible action set is the grounded subset:

\[
\boxed{
A_t^F
=
\{a\in\mathcal A_t^{C}
\mid
\operatorname{Grounded}(a\mid X_t,C_t)
\}.
}
\]

This separates:

```text
expressible action
constructible method
represented method
grounded executable method
```

---

## 37. Capability Expansion Can Change Every Term

A frontier-changing action may modify:

\[
K_t,
M_t,
I_t,
\mathcal C,
B_t,
X_t,
C_t.
\]

Examples:

### Learn a tool

```text
M_t changes
possibly K_t changes through chunking
```

### Meet knowledgeable person

```text
B_t changes
new delegation methods become available
```

### Learn a general abstraction

```text
I_t changes
new method families become representable
```

### Learn conditional reasoning or debugging routine

```text
C changes in practical richness
```

### Obtain device

```text
X_t changes
new invocation primitives become available
```

### Learn that an action has a hidden prerequisite

```text
C_t and refinement metadata change
```

Thus endogenous feasible-action frontier expansion can include changes to the **action-construction architecture itself**.

---

## 38. The Closest Analogue to Arithmetic Operators

The question:

```text
What are the addition, subtraction, multiplication, division, and logical operators of capability bootstrapping?
```

should probably not be answered with one fixed list of verbs such as:

```text
ask
search
read
learn
```

Those are already substantial programs.

A better candidate is a small family of structural operators:

```text
bind a method to a local object
compose methods sequentially
choose among implementations
branch on observed condition
iterate a transformation
compare outcome with target
invoke another controller
retain successful composition as a chunk
refine a failed macro
abstract common structure across methods
specialize an abstraction when hidden differences matter
```

These operators manipulate **methods and transition structures**, not merely world objects.

They are closer to an algebra of capability construction.

---

## 39. No Universal Finite Basis Is Assumed

It would be tempting to claim that one small operator set is computationally or cognitively universal.

That claim is not required here.

The weaker claim is:

\[
\boxed{
\text{a bounded agent benefits from reusable combinators that generate many grounded methods from a smaller locally available repertoire}
}
\]

Different architectures may use different bases.

A human, robot, software agent, institution, and child may have different execution kernels and different composition mechanisms.

The important structural questions are:

```text
What is grounded now?
What can be composed from it?
What abstractions can be reused?
What refinements are known?
What failures trigger specialization?
What bootstrap routes can expand the generator itself?
```

---

## 40. Scaffolded Bootstrapping

An initially weak agent may rely on environment-provided scaffolds.

Examples:

```text
parent
teacher
manual
interface convention
social instruction
example solution
visible affordance
tutorial
error message
```

A scaffold can expose a route that the agent could not invent from its current representation alone.

For example:

```text
unknown device
→ ask teacher
→ teacher demonstrates button sequence
→ imitate
→ observe result
→ repeat
→ store method
```

The bootstrap route begins with an action already executable by the agent:

```text
ask teacher
```

but can terminate in a new method:

```text
operate device
```

The environment therefore participates in capability construction without violating local executability.

---

## 41. Bootstrap Operators Have High Fan-Out

Some methods are especially valuable because they can generate many downstream methods.

For bootstrap method \(b\), define roughly:

\[
\operatorname{FanOut}(b,H)
=
\text{expected value of new methods or bindings reachable through }b
\]

over horizon \(H\).

Methods such as:

```text
ask trusted knowledgeable person
read instructional material
imitate demonstration
compare success and failure
try reversible variation
follow reference
use search interface
```

may have high fan-out.

Their value is not just the immediate answer or observation.

They increase the rate at which future action structure can be discovered and installed.

---

## 42. But Bootstrap Methods Still Require Grounding

High fan-out does not make a method universally available.

For example:

```text
search web
```

may be unavailable because:

```text
no device
no network
no literacy
no query formulation ability
no usable interface
```

Likewise:

```text
ask parent
```

may be unavailable because:

```text
parent absent
no communication channel
no shared language
no social permission
```

Thus even bootstrap operators obey:

\[
\boxed{
\text{every capability-generating method must itself have a locally executable realization}
}
\]

This is the Local Executability Principle applied recursively to the machinery of bootstrapping.

---

## 43. Capability Combinators Can Also Be Learned

The combinator set itself need not be completely innate or fixed.

An agent may learn better ways to:

```text
sequence tasks
split problems
compare alternatives
form stopping conditions
reuse prior methods
delegate appropriately
test hypotheses
recover from failure
```

Thus:

\[
\mathcal C_{t+1}\neq\mathcal C_t
\]

is possible.

A person can become better not only at a domain operation but at **constructing routes through unfamiliar operations**.

This gives a formal place for metacapability.

---

## 44. Metacapability Is Transition-Construction Competence

A static capability inventory asks:

```text
Which operators are already ready?
```

A metacapability model also asks:

```text
How effectively can the agent bind, refine, compose, test, learn, and stabilize new methods?
```

Let:

\[
\Lambda_A(o\rightarrow m)
\]

represent the latency with which agent \(A\) can turn an insufficiently grounded operator \(o\) into a usable method \(m\).

Two agents may have similar current method libraries while differing greatly in:

\[
\Lambda_A.
\]

This is one reason current skill labels can underestimate future operational competence.

---

## 45. Method Inheritance and Override

Generic methods can share structure.

Suppose:

```text
Search(domain,target)
```

provides a default control pattern:

```text
select locus
inspect
compare
update candidate set
repeat
```

A specialized method:

```text
SearchWeb
```

may inherit that control pattern while overriding:

```text
access mechanism
query encoding
navigation method
validation rules
latency model
```

Likewise:

```text
SearchRoom
```

may inherit the same broad interface while overriding:

```text
spatial traversal
physical manipulation
visibility assumptions
termination criteria
```

The programming analogy should not be taken literally as the ontology of cognition.

But interface, specialization, and override are useful structural concepts for avoiding duplicated action models.

---

## 46. Action Contracts Should Preserve Preconditions and Effects

A reusable operator should not be stored only as a name.

A richer contract may contain:

```yaml
operator: ask
parameters:
  respondent: ...
  question: ...
preconditions:
  respondent_accessible: ...
  channel_available: ...
  encoding_supported: ...
  permission_adequate: ...
effects:
  response_may_be_received: true
uncertainty:
  response_probability: ...
  answer_reliability: ...
methods:
  - verbal_local
  - text_message
  - service_query
refinement_triggers:
  - channel_unknown
  - recipient_unreachable
  - repeated misunderstanding
```

This turns the edge into an inspectable transition contract rather than a linguistic command.

---

## 47. Action Abstraction Must Remain Faithful to Executability

A coarse operator is useful only while it preserves the distinctions needed to predict whether some realization will work.

Suppose the planner groups all actions under:

```text
open website
```

but some sites require:

```text
authentication
form interaction
JavaScript execution
account permissions
payment
```

Repeated heterogeneous execution outcomes indicate that the action schema is too coarse.

Thus the same predictive-split logic that applies to state representation also applies to operator representation.

\[
\boxed{
\text{same action category}
+
\text{systematically different executability}
\rightarrow
\text{refine operator schema}
}
\]

---

## 48. The Planner Need Not Know Every Future Decomposition

A route:

\[
p=(o_0,o_1,\ldots,o_n)
\]

may contain future macro-operators whose exact realization is not yet known.

This need not invalidate the route immediately.

What matters asymmetrically is:

\[
\boxed{
\text{the next consequential operator needs a grounded realization with high confidence}
}
\]

while distant operators may remain abstract if plausible refinement routes exist.

As the agent moves, it can resolve later methods under the new state.

This is hierarchical receding-horizon planning.

---

## 49. Near-Grounded Operators

An operator may be almost executable except for one unresolved binding or prerequisite.

For example:

```text
ask specialist
```

may have a known method except:

```text
specialist identity unknown
```

or:

```text
search database
```

may be known except:

```text
account permission missing
```

The planner should preserve these as **near-grounded operators** and diagnose the missing witness component.

Let:

\[
B(o,X_t)
\]

be the unresolved grounding blockers.

Then:

\[
B(o,X_t)=\varnothing
\]

indicates grounded executability.

Otherwise the planner can route toward satisfying one or more members of \(B\).

---

## 50. Grounding Failure Can Produce a Subroute

Suppose:

\[
B(o,X_t)=\{b_1,\ldots,b_k\}.
\]

The planner may recursively solve:

\[
\operatorname{Plan}(X_t,\operatorname{Satisfy}(b_i)).
\]

For example:

```text
search web
blocked by no browser
↓
install browser
blocked by no software repository access
↓
ask administrator
blocked by administrator identity unknown
↓
search local contact directory
```

The decomposition and capability route can interleave.

There is no clean boundary between:

```text
refining an action
```

and:

```text
changing the agent so the refined action becomes executable.
```

Both are part of grounded route construction.

---

## 51. A Unified Hierarchical Control Loop

```text
OBSERVE CURRENT STATE
↓
update task state, architecture state, representation, and constraints
↓
receive target
↓
construct route using currently useful action abstraction
↓
select next macro-operator o
↓
is o represented as executable with a valid realization witness?
├── yes
│   ↓
│   invoke method
│   ↓
│   observe outcome
│   ↓
│   did execution match predicted contract?
│   ├── yes
│   │   ↓
│   │   cache / strengthen witness
│   │   ↓
│   │   continue
│   │
│   └── no
│       ↓
│       locate failed precondition / method / hidden distinction
│       ↓
│       refine implicated operator schema
│       ↓
│       replan
│
└── no
    ↓
    inspect known refinements
    ↓
    bind available agents, tools, resources, locations, and channels
    ↓
    grounded refinement found?
    ├── yes
    │   ↓
    │   install witness
    │   ↓
    │   execute
    │
    └── no
        ↓
        identify grounding blockers
        ↓
        unknown blocker?
        ├── yes → observe / ask / test / inspect through grounded methods
        └── no
            ↓
            search for locally executable enabling route
            ↓
            capability / access / resource / representation change
            ↓
            update kernel, methods, bindings, or operator schemas
            ↓
            retry grounding
```

---

## 52. The Deeper Bootstrap Loop

The long-run capability loop can be written:

\[
\boxed{
K_t
\rightarrow
\text{grounded routines}
\rightarrow
\text{experience}
\rightarrow
\text{comparison}
\rightarrow
\text{method abstraction}
\rightarrow
\text{new bindings}
\rightarrow
\text{new composite methods}
\rightarrow
\text{chunking / tooling / delegation}
\rightarrow
K_{t+1}
}
\]

The kernel enables method construction.

Successful method construction can eventually enlarge or reorganize the effective kernel.

This is endogenous bootstrapping without teleportation.

---

## 53. Core Principles

### Interface-Method Separation Principle

> A generic operator is a transition contract, not automatically an executable action; execution requires a locally realizable method.

### Relative Execution-Kernel Principle

> Primitive actions are primitive only relative to an agent and control layer that already provides their implementation.

### Refinement-Witness Principle

> A macro-edge is operationally executable only when at least one refinement grounds it in currently executable operations under the relevant sequential preconditions.

### No-Facade Executability Principle

> Naming an action, exposing an API, or representing an operator does not create an executable transition.

### Adaptive Action-Resolution Principle

> Preserve coarse action abstractions while they predict and support reliable continuation; refine the local action frontier when grounded executability cannot be established.

### Failure-Directed Refinement Principle

> When an action abstraction fails, refine the implicated method, precondition, binding, or hidden distinction rather than decomposing the entire action model globally.

### Information-Route Integration Principle

> Information acquisition is part of the same route when uncertainty about a transition blocks sufficiently reliable continuation toward the active target.

### Bootstrap-Scaffolding Principle

> Capability bootstrapping may begin from specific locally executable routines tied to accessible people, tools, places, and interfaces before generic operators are available.

### Method-Abstraction Principle

> Repeated concrete routines can support extraction of a shared operator schema whose later value comes from transfer across new bindings and contexts.

### Grounded-Closure Principle

> The feasible-action frontier is generated not only by possessed actions but by grounded compositions of current execution primitives, methods, bindings, and capability combinators.

### Kernel-Migration Principle

> Reliable composite methods can become effectively primitive through learning, chunking, tooling, compilation, or delegation, changing the controller boundary over time.

### Action-Schema Faithfulness Principle

> Operator abstractions should preserve the distinctions necessary to predict decision-relevant executability; heterogeneous outcomes justify specialization or schema refinement.

---

## 54. The Main Architectural Shift

A flat action ontology asks:

```text
Which actions exist?
```

A hierarchical bootstrapping architecture asks:

```text
Which interfaces are represented?
Which implementations are known?
Which are grounded here?
Which bindings are available?
Which composite methods can be generated?
Which refinements become necessary under current pressure?
Which methods can be cached as reusable chunks?
Which failures imply that an operator schema is too coarse?
Which locally executable actions can expand the method generator itself?
```

This changes the meaning of an action graph.

It is no longer only a static set of edges.

It becomes a layered structure containing:

```text
transition contracts
implementation families
execution witnesses
refinement relations
binding rules
control combinators
cached chunks
failure-driven schema updates
```

---

## 55. Conclusion

The difficult question is not:

\[
\text{What is the universal primitive action vocabulary?}
\]

There may be no useful answer at the planning level.

The stronger question is:

\[
\boxed{
\text{What does this agent currently treat as directly executable, and how can more abstract operators be grounded into that repertoire when needed?}
}
\]

This preserves the Local Executability Principle without forcing the planner to flatten every action to one universal granularity.

An abstract operator such as:

```text
ask
search
learn
investigate
repair
```

can remain useful as a planning interface.

But it must not be mistaken for a primitive transition merely because it is linguistically simple.

Its execution depends on a method.

The method depends on bindings, resources, access, representation, and lower-level operations.

Those operations are primitive only relative to some controller boundary.

Capability bootstrapping therefore begins not from magical universal verbs but from whatever grounded execution kernel the agent actually possesses.

From that kernel, the agent can:

```text
bind
sequence
branch
iterate
observe
compare
transform
delegate
compose
retain
refine
abstract
specialize
```

concrete methods.

Specific scaffolded routines such as:

```text
ask parent
ask teacher
search room
imitate demonstration
try control
compare outcomes
```

can then serve as high-fan-out routes into larger method spaces.

Repeated successful routines may be abstracted into reusable interfaces.

Repeated failures may force those interfaces to split.

Tools and learning may compile long refinements into new effective primitives.

The action representation therefore changes with the agent.

The central invariant remains local:

\[
\boxed{
\text{the next consequential transition must have a realization that is executable from the state actually reached}
}
\]

But the representation of that transition may be coarse until the moment its realization matters.

Thus the action-side counterpart of adaptive semantic resolution is:

\[
\boxed{
\text{represent actions abstractly while sufficient; refine them locally until executability is grounded}
}
\]

This turns the edge problem from a search for universal atomic actions into a problem of hierarchical realization, adaptive decomposition, and endogenous growth of the machinery that constructs executable routes.
