# Capabilities, Dependencies, and the Missing Architecture

## Introduction

A recurring source of confusion is the assumption that a desired capability should follow directly from a visible property, a label, a representation, or a declaration.

The reasoning often looks like this:

```text
property
↓
capability
↓
expected result
```

Examples:

```text
intelligent
↓
should solve the problem
```

```text
expensive
↓
should be reliable
```

```text
right declared
↓
service available
```

```text
successful-looking structure
↓
working system
```

But a capability is rarely produced by a label or visible structure alone. It is produced by mechanisms operating under conditions.

A more accurate model is:

```text
mechanisms
+
resources
+
interfaces
+
constraints
+
environment
+
time
↓
capability
↓
observable results
```

The central mistake is not merely that expectations fail to match reality. It is that the dependency structure generating those expectations is often incomplete, reversed, or left implicit.

This document develops a general way to reason about that problem.

---

## 1. A Declaration Is Not an Implementation

Writing the following does not instantiate a capability:

```python
my_capability = "ultimate and should be praised"
```

It creates a value bound to a name. It does not produce the mechanisms associated with the description.

Likewise, statements such as these do not implement what they describe:

```text
This organization is innovative.
This system is intelligent.
Everyone should receive immediate service.
This process is scalable.
```

They may express classifications, intentions, goals, or requirements. None of them supplies an implementation.

The basic distinction is:

```text
description ≠ mechanism
specification ≠ implementation
requested result ≠ causal generator
```

A specification can be useful. It tells us what an implementation must accomplish. But the specification does not compete with the implementation and cannot replace it.

---

## 2. Capabilities Are Conditional

A capability is usually not an isolated property of an object.

Instead of writing:

```text
Capability = f(system)
```

it is usually more accurate to write:

```text
Capability = f(system, task, environment, resources, constraints, time)
```

For example, the statement:

```text
This machine can detect dogs.
```

is incomplete unless the relevant conditions are understood.

The result may depend on:

- image quality;
- lighting;
- viewing angle;
- the training distribution;
- occlusion;
- acceptable error rate;
- processing time;
- available hardware;
- what counts as a dog;
- whether adversarial inputs are permitted.

The machine may have the capability under one contract and lack it under another.

A better statement is:

```text
Given image distribution D,
resolution R,
latency budget L,
and error tolerance E,
the system detects dogs with performance P.
```

This is not an attempt to evade the capability claim. It is an attempt to make the claim precise enough to test.

---

## 3. Why Human Capabilities Look Simpler Than They Are

Humans often perform difficult tasks effortlessly. That makes the underlying mechanism appear small.

Dog detection is a useful example.

A person looks at an image and says:

```text
dog
```

The visible operation appears trivial. But the capability rests on extensive hidden support:

```text
evolution
+
perceptual development
+
embodied experience
+
object permanence
+
world knowledge
+
multimodal learning
+
attention
+
memory
↓
dog recognition
```

When transferring this capability to a machine, people may transfer only the visible specification:

```text
Input: image
Output: dog or not dog
```

What was not transferred is the generator that made the human behavior possible.

The failure is therefore not necessarily an overestimate of the machine. It may be an underestimate of the human support structure.

---

## 4. Representations and Generators

A **representation** is an observable state, artifact, output, or structure.

A **generator** is the mechanism or process capable of producing and reproducing such representations.

Examples:

| Representation | Generator |
|---|---|
| A successful product | Engineering, design, operations, distribution |
| A correct answer | Knowledge, reasoning, retrieval, verification |
| A castle in a strategy game | Economy, labor, resources, logistics, defense |
| A trained model checkpoint | Data, optimization, compute, evaluation |
| A musical performance | Skill, practice, perception, coordination |
| A functioning service | Infrastructure, staffing, maintenance, monitoring |

Two errors follow from confusing them.

### 4.1 Representation implies generator

```text
visible success
↓
assumed viable generator
```

Examples:

```text
The demo worked.
Therefore the system is production-ready.
```

```text
The company has the same organizational chart.
Therefore it has the same capabilities.
```

```text
The building exists.
Therefore the institution works.
```

A representation may be copied without copying the process that produced it.

### 4.2 Missing representation implies missing generator

```text
no visible output
↓
assumed absence of useful process
```

Examples:

```text
No publication yet.
Therefore the research is useless.
```

```text
No immediate improvement.
Therefore the infrastructure work has no value.
```

```text
This socket has no power.
Therefore the electricity supply is useless.
```

The last conclusion is especially revealing. A failed socket may result from:

```text
broken outlet
or
tripped breaker
or
damaged wiring
or
device failure
or
local circuit isolation
or
building-wide outage
or
supply failure
```

One local representation does not uniquely identify the state of the generator.

The relation is:

```text
generator
↓
many possible representations across time and context
```

A generator may exist before its outputs become visible. A representation may remain after the generator has degraded.

---

## 5. Invisible Infrastructure

Support structures become difficult to notice when they are always present.

On Mars, the absence of an internet connection would be obvious because the missing infrastructure is salient.

In an ordinary office, people may barely notice:

- electricity;
- plumbing;
- authentication;
- network routing;
- heating;
- waste removal;
- software updates;
- legal permissions;
- supply chains;
- maintenance;
- documentation;
- institutional memory.

These conditions disappear into the background until one fails.

This creates an observational asymmetry:

```text
visible endpoint
+
invisible support
↓
apparent simplicity
```

A person sees:

```python
result = model.predict(image)
```

but not:

```text
training data
+
model architecture
+
optimization
+
hardware
+
preprocessing
+
deployment
+
monitoring
+
evaluation
↓
predict()
```

The interface is visible. The capability stack is not.

---

## 6. Copying Visible Structures in Games and Organizations

Games expose this mistake clearly because they make dependency structures explicit.

A player may copy a castle, factory, army, or high-level building while ignoring the network that sustains it.

```text
castle
↓
defense capability
```

is usually incomplete.

A more realistic dependency graph is:

```text
food
+
workers
+
housing
+
materials
+
transport
+
maintenance
+
command structure
+
defensive positioning
↓
operational castle
```

Factory-building games make the same point:

```text
science output
```

is not located only in the final assembler. It is distributed across:

```text
mining
+
power
+
transport
+
intermediate goods
+
storage
+
throughput balancing
+
maintenance
↓
science output
```

Organizations make a similar mistake when copying:

- meeting formats;
- titles;
- process documents;
- organizational charts;
- office layouts;
- slogans;
- performance rituals.

These are representations of an operating system, not necessarily the operating system itself.

To transfer the capability, enough of the generating structure must also transfer.

---

## 7. Expectation as a Compressed Causal Model

An expectation is not only a desire. It often contains an implicit prediction.

For example:

```text
I am talented.
Therefore I should succeed.
```

The hidden model is:

```text
talent
↓
success
```

But the real structure may be:

```text
talent
+
task fit
+
practice
+
resources
+
timing
+
coordination
+
feedback
+
opportunity
+
persistence
↓
probability of success
```

The expectation fails because the causal model compressed too many dependencies into one visible property.

What looks like an exception may simply be an omitted variable becoming visible.

---

## 8. Desire Does Not Produce the Desired State

Another dependency reversal occurs when a desired end state is treated as if it were a cause.

```text
I want X.
↓
X should happen.
```

But the actual relation is closer to:

```text
desire for X
+
agreement
+
resources
+
incentives
+
authority
+
coordination
+
execution
↓
X may happen
```

A desire can motivate mechanisms. It is not itself the mechanism.

Likewise:

```text
I expect X.
↓
X is owed to me.
```

is not automatically valid.

An expectation may be justified, but only when another structure supports it.

---

## 9. Normative Systems and Causal Systems

A causal system concerns what produces an outcome.

```text
cause
↓
effect
```

A normative system concerns what ought to happen according to a rule, role, agreement, promise, right, or obligation.

```text
recognized rule
↓
obligation
↓
justified expectation
```

Examples include:

### Loan

```text
loan agreement
↓
obligation to repay
↓
reasonable expectation of repayment
```

### Employment

```text
employment contract
+
work performed
↓
employer obligation
↓
employee expectation of payment
```

### Queue

```text
first arrival
+
shared queue norm
↓
priority to be served first
```

### Promise

```text
promise
↓
commitment
↓
reasonable expectation
```

A common reversal is:

```text
expectation
↓
assumed obligation
```

instead of:

```text
agreement, rule, role, or promise
↓
obligation
↓
expectation
```

The expectation is evidence of a belief about the norm. It is not automatically the source of the norm.

---

## 10. Rights, Freedom, and Obligations Under Constraints

Many social conflicts concern the distribution of:

- rights;
- freedoms;
- benefits;
- costs;
- risks;
- duties;
- authority;
- constraints.

Physics imposes bounded resources:

```text
available energy = finite
available labor = finite
available time = finite
available capacity = finite
```

Normative systems decide how those limits should be handled.

The conflict often takes this shape:

```text
one side seeks more freedom or benefit
↓
another side bears more cost or obligation
```

A stable arrangement usually requires a defensible relationship among:

```text
rights
+
resources
+
responsibilities
+
enforcement
+
capacity
```

Declaring a right can establish a normative claim. It does not automatically instantiate the physical capacity required to fulfill it.

```text
declared right
≠
implemented capability
```

The full dependency is more like:

```text
normative commitment
+
institutions
+
funding
+
workers
+
infrastructure
+
coordination
↓
ability to fulfill the right
```

The normative claim and the implementation are different layers. Neither eliminates the need for the other.

---

## 11. The Infinite-Integer Analogy

Python integers are conceptually unbounded:

```python
x = 10**1000000
```

But actual execution remains constrained by:

- memory;
- processor time;
- energy;
- operating system limits;
- implementation details.

This gives a useful three-layer model:

```text
specification
↓
architecture
↓
runtime
```

The specification states what is permitted or required.

The architecture provides the mechanisms.

The runtime determines whether the mechanisms execute under actual constraints.

A declaration such as:

```text
Everyone should receive immediate care.
```

resembles a high-level specification.

It still requires an architecture:

```text
staffing
+
training
+
facilities
+
triage
+
transport
+
equipment
+
scheduling
+
funding
↓
care delivery
```

And that architecture still executes under physical limits.

The abstraction is not wrong. The error is skipping the architecture layer.

---

## 12. An Architecture Compiler

A conventional compiler checks whether a program conforms to a language and whether certain properties can be established.

An architecture compiler would check whether a proposed capability is supported by the declared mechanisms and constraints.

Example input:

```text
Goal:
    serve 100,000 patients

Architecture:
    20 doctors

Constraints:
    maximum waiting time = 30 minutes
    working time per doctor = 8 hours/day
    average consultation = 20 minutes
```

Possible result:

```text
FAIL: demand exceeds service capacity
FAIL: target waiting time cannot be guaranteed
MISSING: emergency-case handling model
MISSING: supporting-staff capacity
WARNING: no failure tolerance
```

This checker does not need to decide whether healthcare ought to exist. It evaluates whether the architecture satisfies a declared contract.

Partial versions already exist:

- type checkers;
- contract systems;
- SAT and SMT solvers;
- model checkers;
- theorem provers;
- schedulers;
- queueing models;
- capacity planners;
- circuit simulators;
- structural analysis;
- database constraint systems;
- dependency resolvers;
- performance models.

The general idea is not alien. It is an extension of existing formalization.

---

## 13. Are Architectural Properties Different From Types?

Not fundamentally.

Primitive programming types already express constraints.

```text
int
string
array
```

But they often erase domain meaning.

Consider:

```python
def transfer(amount: int, source: int, destination: int) -> None:
    ...
```

The type system sees:

```text
int × int × int
```

The domain sees:

```text
PositiveMoney
× ExistingAccount
× ExistingAccount
× Authorization
× AvailableBalance
× RegulatoryContext
```

The values are not merely integers. They participate in different rules.

A stronger model may use:

```text
Money
AccountId
Currency
AuthorizedTransfer
```

and enforce invariants such as:

```text
amount > 0
source exists
destination exists
source balance ≥ amount
currencies are compatible
transfer limit is not exceeded
```

These are architectural constraints expressed at the domain level.

---

## 14. Domain-Driven Development as Partial Architecture Typing

Domain-driven development moves in this direction by making domain distinctions explicit.

Instead of:

```python
customer_id: str
price: float
currency: str
status: str
```

a richer model uses:

```text
CustomerId
Money
Currency
OrderStatus
```

It may also encode valid transitions:

```text
Draft → Submitted → Paid → Shipped
```

and reject invalid ones:

```text
Cancelled → Shipped
```

This is already a kind of architecture checker.

The progression is:

```text
raw values
→ primitive types
→ domain types
→ refined types
→ contracts
→ invariants
→ state machines
→ system constraints
→ capability contracts
```

The difference between ordinary types and architectural properties is not categorical. Architectural types usually involve more relations, time, resources, and environment parameters.

---

## 15. “It Depends” Is Not the Conclusion

Consider:

```text
Can 20 doctors adequately serve 100,000 people?
```

The unhelpful answer is:

```text
It depends.
```

The useful answer is:

```text
Which variables does it depend on?
```

Then expose them.

```text
N = number of doctors
P = population
λ = patient arrival rate
μ = service rate per doctor
D = case-complexity distribution
H = working hours
S = supporting-staff capacity
G = geographic distribution
W = maximum acceptable waiting time
F = failure tolerance
```

Now define a contract.

For example:

```text
Given:
    arrival rate λ
    doctor count N
    service rate μ

Require:
    backlog remains bounded
    average waiting time ≤ W
    emergency response ≤ E
```

A necessary capacity condition might be:

```text
Nμ > λ
```

This does not solve the whole healthcare problem. It turns one vague claim into a checkable proposition.

The proper response to missing definitions is not indefinite complaint. It is parameterization.

```text
"It depends"
↓
identify dependencies
↓
define interfaces and bounds
↓
derive conditions
↓
test the architecture
```

---

## 16. The Sorting Parallel

When designing a sorting algorithm, one does not model every possible number, machine, user, and future runtime condition.

One defines a contract:

```text
Input:
    finite sequence of comparable elements

Output:
    ordered permutation of the input
```

The algorithm requires an ordering relation.

This may be:

- built into the value type;
- supplied as `cmp`;
- derived through a key;
- encoded in the representation.

Example:

```python
sorted(items, key=lambda item: item.score)
```

The ordering mechanism has not disappeared. It is supplied through `score`.

Without an ordering relation, “sort these objects” is incomplete.

There are then only a few options:

1. implement the comparison;
2. obtain it from an existing interface;
3. derive it from a key;
4. restrict the domain;
5. change the representation;
6. weaken the requirement;
7. accept that sorting is unavailable.

There is no mechanism-free sorting algorithm.

The same is true for general capabilities.

```text
requested outcome
+
required mechanism
+
valid assumptions
↓
available capability
```

If a required mechanism does not exist, expectation cannot substitute for it.

---

## 17. The Entire World Is Not Required

An architectural model does not need to contain the entire changing world.

A sorting algorithm does not know every possible value of `T`. It requires only a contract such as:

```text
Comparable<T>
```

Likewise, an architecture can abstract its environment through an interface.

```text
Environment {
    load range
    failure model
    latency range
    resource bounds
}
```

The capability claim becomes conditional:

```text
Given assumptions A,
for inputs in domain D,
using resources R,
the system guarantees property P
within bounds B.
```

This is the architectural equivalent of an algorithmic contract.

The goal is not perfect prediction. The goal is to state exactly what has been proved, tested, or assumed.

---

## 18. Capability as a Parameterized Type

A capability can be represented conceptually as a highly parameterized type:

```text
Capability<
    System,
    Task,
    Environment,
    Resources,
    Time,
    FailureModel,
    SuccessCriterion
>
```

For example:

```text
DogDetector<
    image_distribution = D,
    resolution ≥ R,
    latency ≤ L,
    error_rate ≤ E
>
```

Or:

```text
ScalableService<
    load ≤ 1,000,000 requests/day,
    p99_latency ≤ 200 ms,
    availability ≥ 99.9%,
    budget ≤ B
>
```

Or:

```text
HealthcareCapacity<
    arrival_rate ≤ λ,
    service_rate ≥ μ,
    emergency_response ≤ E,
    average_wait ≤ W
>
```

Removing the parameters makes the capability appear intrinsic:

```text
scalable
intelligent
adequate
reliable
fair
```

But these labels are usually compressed contracts.

The job is to decompress them.

---

## 19. Mechanism Availability Is Binary, Guarantees Are Conditional

At the deepest level:

```text
required mechanism exists
or
required mechanism does not exist
```

But the guarantee is usually conditional:

```text
mechanism exists
+
preconditions hold
+
resources remain within bounds
+
interfaces behave as specified
↓
guarantee holds
```

This resembles ordinary programming.

A function may be correct under its preconditions and fail outside them.

```text
precondition
↓
execution
↓
postcondition
```

The same applies to architectures.

```text
environment contract
↓
system operation
↓
capability guarantee
```

The key is not to demand unconditional capability from a conditional mechanism.

---

## 20. Common Failure Patterns

### 20.1 Label substitution

```text
label
↓
assumed capability
```

Examples:

```text
expert → correct
AI-powered → intelligent
open source → secure
expensive → reliable
```

### 20.2 Representation substitution

```text
copied artifact
↓
assumed generator
```

Examples:

```text
same process document → same organizational ability
same interface → same implementation quality
same building → same institution
```

### 20.3 Specification substitution

```text
declared goal
↓
assumed implementation
```

Examples:

```text
right declared → capacity exists
policy announced → execution occurs
function named → function implemented
```

### 20.4 Context erasure

```text
capability in context A
↓
assumed capability in context B
```

without transferring the supporting environment.

### 20.5 Local-output diagnosis

```text
one failed output
↓
entire generator judged useless
```

### 20.6 “It depends” paralysis

Dependencies are identified but never formalized.

```text
complexity noticed
↓
analysis stops
```

The corrective move is:

```text
dependency noticed
↓
parameter introduced
↓
contract defined
↓
model checked
```

---

## 21. A Practical Method

When evaluating a capability claim, use the following sequence.

### Step 1: State the capability operationally

Avoid:

```text
The system is intelligent.
```

Prefer:

```text
The system solves task class T
within error E
and time L.
```

### Step 2: Define the input domain

```text
Which inputs are accepted?
Which are excluded?
What distribution is assumed?
```

### Step 3: Define success

```text
What observable postcondition counts as success?
```

### Step 4: Identify required mechanisms

```text
What operation, resource, relation, or process makes each step possible?
```

### Step 5: Declare environmental assumptions

```text
What must the surrounding system provide?
```

### Step 6: Declare resource bounds

```text
time
energy
money
memory
labor
bandwidth
authority
attention
```

### Step 7: Define failure tolerance

```text
What failures are permitted?
How often?
How severe?
What recovery is required?
```

### Step 8: Check interactions

```text
Do the mechanisms compose?
Are there bottlenecks?
Are there cycles?
Are there contradictory constraints?
```

### Step 9: Test portability

```text
Which assumptions belong to the focal system?
Which belong to its environment?
What must move with the capability?
```

### Step 10: Produce a conditional claim

```text
Under assumptions A,
for domain D,
with resources R,
the architecture provides capability C
within bounds B.
```

---

## 22. From Informal Claim to Checkable Contract

An informal claim:

```text
This team can deliver quickly.
```

A decomposed contract:

```text
Given:
    scope ≤ S
    dependencies available by date D
    team size ≥ N
    required skills present
    interruption rate ≤ I

Guarantee:
    release within T days
    defect rate ≤ E
```

An informal claim:

```text
This model understands the request.
```

A decomposed contract:

```text
Given:
    task family F
    context length ≤ C
    required facts available
    ambiguity ≤ A

Guarantee:
    response satisfies evaluation rubric R
    with failure probability ≤ E
```

An informal claim:

```text
This policy ensures access.
```

A decomposed contract:

```text
Given:
    funding ≥ B
    provider capacity ≥ P
    demand ≤ D
    geographic coverage ≥ G

Guarantee:
    waiting time ≤ W
    denial rate ≤ E
```

The point is not that every contract must be perfect. A partial explicit model is easier to inspect, test, revise, and falsify than an implicit one.

---

## 23. The General Principle

A capability should not be treated as a free-floating adjective attached to an object.

It should be treated as a conditional result of an architecture.

```text
capability
=
implemented mechanisms
operating under declared conditions
to satisfy a defined contract
```

Or more compactly:

```text
Capability = Mechanism + Context + Contract
```

This leads to several consequences:

1. Copying a visible representation does not necessarily transfer the generator.
2. Missing visible output does not necessarily imply a useless generator.
3. A declaration does not instantiate a mechanism.
4. A justified expectation requires a supporting causal or normative structure.
5. A right can define an obligation without automatically creating fulfillment capacity.
6. “It depends” should trigger parameterization, not paralysis.
7. Architecture can be treated as an extension of typing, contracts, and formal verification.
8. Portability requires transferring enough of the structure that made the capability work.
9. Guarantees are meaningful only relative to declared preconditions and bounds.
10. When a required mechanism is absent, expectation cannot replace it.

---

## Conclusion

The recurring error is not merely optimism, entitlement, or failed prediction. It is the collapse of several distinct layers:

```text
description
specification
architecture
implementation
runtime
representation
generator
norm
obligation
expectation
```

When these layers are collapsed, people expect labels to produce capabilities, representations to imply generators, rights to imply capacity, and desires to imply obligations.

A more disciplined approach is the same one used in algorithm design:

```text
define the domain
define the operation
define the contract
implement the mechanism
state the assumptions
check the constraints
test the guarantee
```

The answer to “it depends” is not to stop.

The answer is:

```text
Then define what it depends on.
```
