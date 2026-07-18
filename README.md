# Capability Systems, Hierarchical Resolution, and Locally Executable Guidance

## Abstract

A finite agent does not act by representing every possible transition, continuously processing an unlimited instruction stream, or reasoning from a distant goal directly to microscopic control signals.

It acts through an organized hierarchy.

Physical and computational components realize primitive functions.

Interfaces expose selected functions as invocable operators.

Controllers and learned policies stabilize recurring compositions into skills.

The feasible composition closure of these operators and skills determines which outcomes the configured agent can reliably realize.

Goals create inverse reachability problems:

```text
given current configuration
+
desired target condition
->
find an executable composition that reaches the target
```

Because direct interaction is local and agent capacity is finite, a useful architecture does not transmit the entire trajectory at once. It resolves the global target into successive context-sensitive chunks that are small enough to interpret, verify, and execute from the current configuration.

Navigation systems, drone autopilots, humanoid control stacks, operating systems, language-guided action, and institutional procedures all exhibit this structure:

```text
global target
->
route or plan
->
locally relevant subgoal
->
executable operator instance
->
control realization
->
observation
->
updated resolution
```

The central claim is:

> Capability is the stable availability of successful composition realizations, while practical guidance is the repeated resolution of a global target into locally executable chunks under changing context.

This document develops that claim as a standalone framework.

---

## 1. Starting Point

A finite agent may receive a target such as:

```text
reach Munich
```

```text
grasp the cup
```

```text
clean the room
```

```text
compile the program
```

```text
deliver the package
```

```text
obtain legal approval
```

The target rarely specifies every intermediate transition.

A navigation destination does not contain every steering correction.

A request to grasp a cup does not contain every joint torque.

A software requirement does not contain every machine instruction.

A legal objective does not contain every filing, review, signature, and registry transition.

Yet agents often act successfully because they inherit organized structures that connect high-level targets to lower-level realizations.

These structures include:

```text
maps
policies
controllers
skills
instruction sets
interfaces
resolvers
registries
procedures
routing systems
learned models
persistent infrastructure
```

The central problem is therefore not merely:

```text
Which actions exist?
```

It is:

```text
Which actions are available to this configured agent?
Which invocations are currently executable?
Which compositions reach the target?
Which references and meanings resolve?
Which local chunk should be exposed next?
How should execution be monitored and replanned?
```

---

## 2. Four Distinct Objects

The framework distinguishes four objects that are often collapsed.

### Operator

An operator is an invocable transition schema.

\[
u(a):c\to\mathcal B(c',z)
\]

where:

```text
a  = invocation arguments
c  = current configuration
c' = resulting configuration
z  = observation or output
B  = deterministic, nondeterministic, probabilistic, or strategic behavior model
```

### Skill

A skill is a stabilized reusable realization of a behavior family, often implemented by a controller or policy.

\[
s(o_t)\mapsto a_t
\]

where observations are converted into actions over time.

### Capability

An operational capability is the stable availability of a class of successful realizations under a declared region of conditions.

### Task

A task specifies a desired target condition or outcome.

\[
\tau=(g,\Theta)
\]

where:

```text
g     = target predicate
Theta = task constraints, tolerance, horizon, or quality conditions
```

Thus:

```text
operator
=
reusable transition contract
```

```text
skill
=
stabilized behavioral realization
```

```text
capability
=
supported class of successful realizations
```

```text
task
=
requested target condition
```

---

## 3. Configured Agents

Executability is relative to a configured agent.

Let:

\[
c=(x,k,b,r,\alpha,e,t)
\]

where:

```text
x = external or target-system state
k = represented knowledge state
b = body or hardware configuration
r = resource state
α = authority and access state
e = environment
t = temporal context
```

The same abstract operator may be executable in one configuration and unavailable in another.

Examples include:

```text
a grasping skill with a damaged gripper
a route with a closed road
an API call with expired credentials
a program with insufficient memory
a human instruction in an unknown language
a legal procedure outside the relevant jurisdiction
```

Therefore:

> Capability is not a property of an abstract action name alone. It is a relation among an agent, its organization, its current configuration, an environment, and a target class.

---

## 4. Components Realize Primitive Functions

A component may implement a primitive transformation:

\[
f_i:X_i\to Y_i
\]

Examples include:

```text
camera
:
light pattern
->
image data
```

```text
motor
:
electrical command
->
torque
```

```text
radio
:
encoded data
->
transmitted signal
```

```text
parser
:
text
->
structured representation
```

```text
memory cell
:
write signal
->
retained bit state
```

The component may support a physical function without exposing it as an independently invocable operator.

A battery supplies voltage, but the system may not expose:

```text
GENERATE_VOLTAGE()
```

as a public action.

The distinction is:

```text
realized physical function
versus
invocable operator
```

An operator normally requires a stable access path, invocation language, contract, and realization.

---

## 5. The Primitive Function-Operator Set

Let:

\[
\mathcal F_0
=
\{f_1,\dots,f_m\}
\]

be the primitive function set realized by the components.

Let:

\[
\mathcal U_0
=
\{u_1,\dots,u_n\}
\]

be the primitive operator set exposed through usable control interfaces.

In general:

\[
\mathcal U_0
\not\equiv
\mathcal F_0
\]

because some functions are:

```text
not directly controlled
not separately addressable
not semantically exposed
not safe to invoke
not stable enough to promise
used only as internal infrastructure
```

Conversely, one exposed operator may depend on many primitive functions.

For example:

\[
\operatorname{CaptureImage}
\]

may require:

```text
sensor activation
clock synchronization
exposure control
memory allocation
signal conversion
image encoding
error detection
```

Thus:

> The public operator set is a curated projection of the underlying functional organization.

---

## 6. Operator Systems Are More Than Operator Inventories

An operator inventory lists available names.

An operator system also specifies how the operators can interact.

Let:

\[
\mathfrak O
=
(
\mathcal U,
\circ,
\parallel,
\Gamma,
\mathcal C,
\mathcal R
)
\]

where:

```text
U = operator set
∘ = sequential composition relation
∥ = parallel or concurrent composition relation
Γ = typing, role, and interface environment
C = state, resource, authority, temporal, and embodiment constraints
R = resolver and access infrastructure
```

Two systems may contain the same nominal operator names while supporting different capabilities because their composition rules, implementations, resources, or resolver structures differ.

Therefore:

```text
operator inventory
!=
operator system
```

and:

```text
same parts
!=
same practical capability
```

---

## 7. Controllers Organize Lower-Level Operators

A controller coordinates lower-level transitions over time.

For a grasping controller:

\[
\pi_{\text{grasp}}:
o_t\to a_t
\]

the internal realization may repeatedly combine:

```text
object tracking
pose estimation
trajectory correction
joint control
collision avoidance
force sensing
gripper closure
slip compensation
```

Externally, the system may expose one higher-level operator:

\[
\operatorname{Grasp}(object)
\]

The controller compresses a large internal interaction sequence into a stable interface.

Thus:

\[
u_1\circ u_2\circ\cdots\circ u_k
\rightsquigarrow
s
\]

where \(s\) is a promoted composite skill.

The promoted skill is not identical to one fixed sequence. It may contain feedback, branching, retries, and adaptation.

---

## 8. Skills as Stabilized Composite Operators

A skill can be modeled as a controlled composition schema:

\[
s:
\mathcal O\times C
\to
\mathcal B(C\times Z)
\]

where:

```text
O = observation histories
C = configurations
Z = outputs or execution observations
```

A skill differs from a one-time trace.

One trajectory:

```text
reach
->
align
->
close gripper
```

is an execution token.

A skill is the maintained organization capable of producing suitable trajectories across an admissible region.

Therefore:

```text
successful trace
!=
skill
```

```text
skill implementation
!=
capability in every context
```

```text
skill available
!=
particular invocation executable
```

---

## 9. Operational Capability and Authority Capability

The word `capability` has at least two important technical meanings.

### Operational capability

The system can realize a class of outcomes.

\[
\operatorname{OpCap}(A,g,c,H)
\]

means agent \(A\) can realize target \(g\) from configuration \(c\) within horizon \(H\), under the declared reliability conditions.

### Authority capability

The agent possesses a token, credential, role, or delegated right permitting selected operations.

\[
\operatorname{AuthCap}(A,u,\sigma)
\]

may represent authorization to invoke operator \(u\) within scope \(\sigma\).

The two interact but should not be confused.

An agent may:

```text
physically know how to open a door
but lack permission
```

or:

```text
possess authorization
but lack the physical means
```

Practical execution may require both:

\[
\operatorname{OpCap}
\land
\operatorname{AuthCap}
\]

---

## 10. Capability as Feasible Composition Closure

Let:

\[
\operatorname{Plans}(\mathfrak O,c,H)
\]

be the set of composition structures constructible from operator system \(\mathfrak O\), starting from configuration \(c\), within horizon \(H\).

Let:

\[
\operatorname{ExecPlans}(\mathfrak O,c,H)
\subseteq
\operatorname{Plans}(\mathfrak O,c,H)
\]

be the subset satisfying:

```text
typing
preconditions
embodiment constraints
resource constraints
authority constraints
temporal constraints
reference continuity
implementation availability
reliability thresholds
```

Then the operational capability set is:

\[
\operatorname{Cap}(\mathfrak O,c,H)
=
\left\{
g
\;\middle|\;
\exists p\in
\operatorname{ExecPlans}(\mathfrak O,c,H):
p(c)\models g
\right\}
\]

This gives the central construction:

\[
\boxed{
\text{capability}
=
\text{target effects generated by feasible operator composition}
}
\]

Capabilities therefore emerge from composition possibilities, but only from **feasible and sufficiently stable** composition possibilities.

---

## 11. Capability Is Not Mere Syntactic Closure

A grammar may allow:

\[
u_1\circ u_2
\]

while the composition remains physically impossible.

Possible failures include:

```text
output type mismatch
semantic mismatch
missing reference
insufficient energy
occupied limb
expired permission
unavailable implementation
timing violation
unsafe intermediate state
excessive failure probability
```

Therefore:

\[
\operatorname{SyntacticallyComposable}
\not\Rightarrow
\operatorname{Executable}
\]

Capability requires a constrained closure:

\[
\operatorname{Closure}_{\text{feasible}}
(
\mathfrak O,c,H
)
\]

rather than unrestricted formal composition.

---

## 12. Tasks Select Target Regions

A task does not normally prescribe every transition.

It declares a desired region:

\[
G_\tau
=
\{c\mid c\models g_\tau\}
\]

Examples include:

```text
cup is held securely
```

```text
vehicle is at destination
```

```text
floor is sufficiently clean
```

```text
program satisfies tests
```

```text
application has approved status
```

The planning problem is:

\[
\text{find }p
\]

such that:

\[
p(c_0)\in G_\tau
\]

while satisfying the task constraints.

The selected plan is a composition schema.

Its execution produces an actual trace:

\[
\eta
=
(c_0,u_1(a_1),c_1,\dots,u_n(a_n),c_n)
\]

Thus:

```text
task
->
target region
->
plan or policy
->
bound operator instances
->
execution trace
->
observed outcome
```

---

## 13. Type, Schema, and Token

A useful three-level distinction is:

### Capability type

\[
\operatorname{CanGraspCup}
\]

This denotes a class of realizable interactions.

### Composition schema

\[
\operatorname{Approach}
\circ
\operatorname{Reach}
\circ
\operatorname{Align}
\circ
\operatorname{CloseGripper}
\]

This denotes a reusable way to realize that class.

### Execution token

```text
robot R grasps cup c7 at time t
```

This is one actual occurrence.

A capability is neither merely the schema nor merely the token.

It is the maintained availability of suitable schemas and realizations over a declared region.

---

## 14. Bodies Resemble Stateful Instruction Architectures

The CPU analogy is useful.

A processor acts through:

```text
instruction set
register file
memory
privilege state
devices
pipeline state
```

A human or robot acts through:

```text
body
sensors
actuators
learned skills
working memory
tools
authority
environment
```

A processor cannot issue an instruction requiring unavailable registers, privilege, memory, or device state.

An embodied agent cannot execute an action requiring:

```text
a third hand
an absent tool
unavailable balance
excess reach
more force than the body can generate
a language it cannot interpret
a permission it does not possess
```

The analogy is not exact.

Human and robotic action systems are:

```text
continuous
adaptive
probabilistic
partly learned
dynamically recalibrated
tool-extendable
```

But the structural resemblance remains:

> Action selection occurs relative to a finite embodied architecture and its current state, not against an unlimited abstract action vocabulary.

---

## 15. Embodiment Constraints Are Usually Implicitly Resolved

A human does not normally verbalize:

```text
two arms available
left elbow range valid
right hand occupied
balance stable
visual target localized
grip aperture sufficient
```

before grasping an object.

These conditions are largely resolved by sensorimotor organization.

The agent behaves as if it maintains a changing executable frontier:

\[
\mathcal U_{\mathrm{exec}}(c)
=
\{
u(a)
\mid
c\vdash u(a)\operatorname{ executable}
\}
\]

The frontier changes when:

```text
the body moves
an object moves
a hand becomes occupied
fatigue increases
a tool is acquired
a permission is granted
an instruction is interpreted
```

This implicit constraint resolution is one reason ordinary action appears simpler than its underlying structure.

---

## 16. Operator Availability Is Not Invocation Executability

Suppose the system possesses the general operator:

\[
\operatorname{Grasp}(x)
\]

This does not imply that every invocation is executable.

For cup \(c_7\), execution may require:

\[
\operatorname{Localized}(c_7,c)
\]

\[
\land
\operatorname{ReachableByManipulator}(c_7,c)
\]

\[
\land
\operatorname{CompatibleGrip}(c_7,c)
\]

\[
\land
\operatorname{ManipulatorAvailable}(c)
\]

\[
\land
\operatorname{SufficientForce}(c)
\]

\[
\land
\operatorname{SafeTrajectoryExists}(c_7,c)
\]

If the cup lies beyond arm reach, then:

\[
\neg
\operatorname{Executable}
(
\operatorname{Grasp}(c_7),c
)
\]

even though the general grasping skill remains part of the system.

Therefore:

\[
\text{operator available}
\not\Rightarrow
\text{every parameterized instance executable}
\]

---

## 17. Direct Failure Does Not Imply Goal Failure

The direct invocation may fail while the target remains reachable through composition.

For example:

\[
\operatorname{WalkTo}(c_7)
\circ
\operatorname{Reach}
\circ
\operatorname{Grasp}(c_7)
\]

or:

\[
\operatorname{RetrieveTool}
\circ
\operatorname{UseReachTool}(c_7)
\]

Thus:

\[
\neg
\operatorname{Executable}
(
\operatorname{Grasp}(c_7),c
)
\]

does not imply:

\[
\neg
\operatorname{OpCap}
(
A,\operatorname{Held}(c_7),c,H
)
\]

The important distinction is:

```text
direct operator invocation
versus
goal reachability through composition
```

---

## 18. Goal-Directed Action Is an Inverse Reachability Problem

A forward problem asks:

\[
u(c)=c'
\]

Given an operator and a configuration, what transition follows?

A goal-directed problem asks:

\[
\text{given }c_0\text{ and }g,
\text{ find }p
\text{ such that }p(c_0)\models g
\]

This is an inverse problem because the desired outcome is given while the producing composition remains unknown.

It is not generally a mathematical inverse function.

There may be:

```text
many valid plans
no valid plan
irreversible transitions
uncertain outcomes
unknown state
unknown operators
changing environments
strategic interference
```

A more precise name is:

```text
inverse reachability search
```

or:

```text
task-conditioned synthesis of an executable composition
```

---

## 19. Search May Target More Than a State Path

An agent may search for:

```text
a path through known states
a missing operator
a bridge between representations
a suitable tool
an interpretable instruction
a reference to the target
a permission or credential
a service implementation
a reusable policy
a maintained route
a cooperating agent
```

For example, failure to grasp a distant cup may be resolved by searching for:

```text
a path closer to the cup
a reaching tool
another agent
a movable support
a different target cup
```

Therefore the inverse problem is not always:

\[
\text{search over action sequences}
\]

It may be:

\[
\text{search over executable structures}
\]

---

## 20. Why Locality Makes Action Tractable

Physical interactions are usually locally mediated.

A hand affects nearby objects.

A wheel affects the surface at its contact region.

A network packet moves through adjacent links.

A legal filing enters through a recognized procedural interface.

A machine instruction modifies architecturally accessible state.

Let:

\[
N(c)
=
\{
u(a)
\mid
u(a)\text{ is locally executable from }c
\}
\]

be the current action neighborhood.

A bounded agent can select among this local frontier more easily than among all imaginable trajectories.

Locality reduces decision complexity because it limits which distinctions matter now.

Thus:

> Global reachability is usually constructed from a succession of locally executable transitions.

---

## 21. Locality Is Agent- and Mode-Relative

The same environment presents different local neighborhoods to different agents.

A route segment may be available to:

```text
a pedestrian
```

but not:

```text
a car
```

A staircase may be available to:

```text
a walking human
```

but not:

```text
a wheeled robot
```

A narrow gap may be available to:

```text
a small drone
```

but not:

```text
a large vehicle
```

An API may be locally invocable by:

```text
an authenticated service
```

but not:

```text
an unauthenticated client
```

Therefore locality means:

\[
\operatorname{Adjacent}_A(c,c')
\]

relative to the configured agent and selected interaction mode.

---

## 22. Infrastructure Extends Effective Locality

A distant effect becomes locally invocable when infrastructure hides intermediate transitions behind a stable interface.

Examples include:

```text
telephone call
```

```text
web request
```

```text
train journey
```

```text
bank transfer
```

```text
package delivery
```

```text
database query
```

The user performs a local invocation.

A maintained system realizes the longer composition.

Thus:

```text
physical locality
+
persistent infrastructure
->
extended effective adjacency
```

A phone does not eliminate distance.

It exposes a maintained communication route through a local interface.

A navigation system does not eliminate the road graph.

It exposes the next useful road transition through a local instruction.

---

## 23. Global Planning and Local Execution

Many action systems separate at least two scales.

### Global layer

Select a route, strategy, or sequence of subgoals connecting the current region to the target region.

### Local layer

Select a safe executable transition under current observations and constraints.

A simplified hierarchy is:

```text
global target
->
route or task plan
->
local subgoal
->
trajectory
->
control action
->
actuator command
```

The global layer does not directly generate every microscopic control signal.

The local layer does not need to reconsider the entire global objective at every actuator update.

Each layer works with a representation appropriate to its horizon and bandwidth.

---

## 24. Drone Control Exhibits the Same Structure

A drone control architecture commonly resembles:

```text
mission target
->
global path planner
->
waypoint sequence
->
local trajectory planner
->
attitude and position controller
->
motor mixing
->
motor commands
```

The target might be:

\[
g=
\operatorname{AtLocation}(q_{\text{goal}})
\]

The global planner reasons over obstacles, maps, corridors, or waypoints.

The local planner adapts the route to current position, velocity, and newly observed hazards.

The low-level controller stabilizes attitude and motion.

No single layer needs the full detail of every other layer.

This resembles a compilation stack:

```text
goal specification
->
intermediate representation
->
lower-level instructions
->
physical execution
```

---

## 25. Navigation Systems Reveal Resolution Granularity

A navigation system is not valuable merely because it contains a route.

Its crucial service is that it repeatedly exposes the **next locally relevant instruction**.

The user supplies the destination once:

\[
g=
\operatorname{AtDestination}(d)
\]

The system may compute:

\[
r=(e_1,e_2,\dots,e_n)
\]

but it does not require the user to hold all route edges in working memory.

Instead it emits chunks such as:

```text
continue for 1.2 km
```

```text
take the second exit
```

```text
turn left at the next intersection
```

```text
destination is on the right
```

Each chunk is:

```text
temporally relevant
spatially local
small enough to interpret
linked to observable landmarks
compatible with current mode
revisable when state changes
```

This is not merely route planning.

It is **hierarchical resolution into executable guidance**.

---

## 26. The Resolvable Chunk

Let:

\[
\chi
\]

be a guidance chunk.

A useful chunk should satisfy:

\[
\operatorname{Relevant}(\chi,c,g)
\]

\[
\land
\operatorname{Interpretable}(\chi,A,c)
\]

\[
\land
\operatorname{Bindable}(\chi,A,c)
\]

\[
\land
\operatorname{Executable}(\chi,A,c)
\]

\[
\land
\operatorname{Verifiable}(\chi,A,c)
\]

A chunk may be represented as:

\[
\chi
=
(
h_u,
h_{\text{args}},
P,
Q,
\omega
)
\]

where:

```text
hu     = handle to the operator or skill
hargs  = handles to arguments or local targets
P      = relevant preconditions
Q      = expected local completion condition
ω      = observation or verification cue
```

The chunk need not expose the internal control trajectory.

It exposes enough structure for the receiving layer to resolve and execute the next step.

---

## 27. Finite Agents Cannot Consume an Infinite Instruction Stream

A bounded agent has finite:

```text
attention
working memory
perceptual bandwidth
control bandwidth
update rate
interpretive capacity
```

Therefore practical guidance cannot require the agent to process an unbounded description at one moment.

Let:

\[
B_A(c)
\]

be the current processing budget of agent \(A\).

A chunk should satisfy:

\[
L(\chi)
\leq
B_A(c)
\]

where \(L(\chi)\) measures the information or distinction burden relevant to interpretation and execution.

This does not imply that the total route is short.

It implies that the route is delivered through a bounded sequence of locally consumable interfaces.

Thus:

```text
large total trajectory
!=
large immediate instruction
```

---

## 28. Guidance Is Closed-Loop Resolution

A brittle architecture would transmit a complete fixed sequence:

\[
u_1,u_2,\dots,u_n
\]

and assume all future states remain as predicted.

A robust architecture repeatedly resolves the next chunk:

\[
\chi_t
=
\rho(g,c_t,k_t)
\]

The agent executes:

\[
c_{t+1}
\sim
\llbracket \chi_t\rrbracket(c_t)
\]

observes:

\[
o_{t+1}
\]

updates knowledge:

\[
k_{t+1}
=
\operatorname{Update}(k_t,o_{t+1})
\]

and resolves again:

\[
\chi_{t+1}
=
\rho(g,c_{t+1},k_{t+1})
\]

This yields:

```text
resolve
->
execute
->
observe
->
update
->
resolve again
```

The architecture supports deviation, uncertainty, and replanning.

---

## 29. Receding-Horizon Action

Only part of a long route needs to be committed at a time.

Let:

\[
p_t^{(H)}
\]

be a plan over a finite horizon \(H\) computed from the current state.

The system executes only an initial portion:

\[
\operatorname{Prefix}_h
(
p_t^{(H)}
)
\]

where:

\[
h < H
\]

Then it replans from the resulting state.

This reduces dependence on distant predictions.

A navigation system may preserve the global destination while revising the local route after:

```text
a missed turn
a road closure
traffic
new sensor information
changed preferences
resource depletion
```

Therefore:

> Long-horizon coherence does not require long-horizon open-loop control.

---

## 30. Handles Are More Efficient Than Full Trajectories

A handle provides a compact entry point into retained organization.

Examples include:

```text
Munich
the cup
open the door
call Alice
compile the project
submit the application
```

The handle does not contain the complete realization.

It depends on resolver infrastructure.

For destination \(d\):

\[
h_d
\overset{\rho_{\text{geo}}}{\longrightarrow}
q_d
\]

where \(q_d\) is a geographic target.

Then:

\[
(c,q_d)
\overset{\rho_{\text{route}}}{\longrightarrow}
r
\]

Then:

\[
(c,r)
\overset{\rho_{\text{guidance}}}{\longrightarrow}
\chi
\]

Then:

\[
(c,\chi)
\overset{\rho_{\text{control}}}{\longrightarrow}
a
\]

Thus one compact handle can activate a deep hierarchy of retained organization.

---

## 31. Language Communicates Compressed Handles

Consider:

```text
grasp the cup
```

This utterance is not a complete motor program.

It depends on the receiver resolving:

```text
the language
the verb
the intended operator
the object reference
the relevant cup
the current location
the usable hand
the grasp type
the trajectory
the completion condition
```

Language therefore often transmits:

```text
operator handles
+
argument handles
+
goal constraints
```

rather than complete physical trajectories.

Its efficiency depends on shared resolver infrastructure:

```text
vocabulary
grammar
world knowledge
perception
social context
learned skills
conventions
```

---

## 32. An Uninterpretable Instruction Is Not Executable Through That Channel

Suppose an agent receives the signal:

\[
s=\text{a word meaning grasp in an unknown language}
\]

If the agent cannot map the signal to an operator identity, then:

\[
\operatorname{Interpret}(s,\Gamma)
=
\operatorname{failure}
\]

The agent may still physically possess a grasping skill.

But the communicated invocation is not executable through the current semantic interface.

Thus:

\[
\text{physical skill}
\not\Rightarrow
\text{linguistically invocable skill}
\]

Practical invocation requires a chain such as:

\[
\text{signal}
\to
\text{recognized expression}
\to
\text{operator identity}
\to
\text{argument bindings}
\to
\text{admissible invocation}
\to
\text{control realization}
\]

A failure at any bridge interrupts the action path.

---

## 33. Resolver: Narrow and General Meanings

In a narrow sense, a resolver maps a handle to a current locator:

\[
\rho_{\text{ref}}:
H\times C
\to
L
\cup
\{\operatorname{failure}\}
\]

Examples include:

```text
domain name
->
network location
```

```text
legal identifier
->
registry record
```

```text
object name
->
perceived object instance
```

In a broader action-theoretic sense, a resolver maps an underspecified target or handle into a more concrete structure usable by the next layer.

\[
\rho_i:
H_i\times C_i
\to
H_{i+1}
\cup
\{\operatorname{failure}\}
\]

A hierarchy of resolvers progressively reduces ambiguity and increases executability.

---

## 34. Resolver Families

A practical action stack may contain several resolver classes.

### Lexical resolver

\[
\text{signal}
\to
\text{recognized symbol sequence}
\]

### Syntactic resolver

\[
\text{symbol sequence}
\to
\text{structured expression}
\]

### Semantic resolver

\[
\text{expression}
\to
\text{operator or target meaning}
\]

### Referential resolver

\[
\text{descriptive handle}
\to
\text{particular entity}
\]

### Access resolver

\[
\text{operator identity}
\to
\text{available realization or service}
\]

### Affordance resolver

\[
(\text{entity},c)
\to
\text{currently supported interactions}
\]

### Task resolver

\[
(\text{goal},c)
\to
\text{subgoal or plan}
\]

### Guidance resolver

\[
(\text{plan},c)
\to
\text{next executable chunk}
\]

### Embodiment resolver

\[
(\text{abstract action},b,c)
\to
\text{body-relative trajectory or controller}
\]

### Control resolver

\[
(\text{trajectory},c)
\to
\text{actuator commands}
\]

These need not be separate physical modules.

They identify distinct transformation obligations.

---

## 35. Hierarchical Resolution

Let:

\[
h_0=g
\]

be a global target handle.

A resolver hierarchy produces:

\[
h_0
\overset{\rho_0}{\longrightarrow}
h_1
\overset{\rho_1}{\longrightarrow}
h_2
\overset{\rho_2}{\longrightarrow}
\cdots
\overset{\rho_{n-1}}{\longrightarrow}
u(a)
\]

where each level adds distinctions required by the next.

For navigation:

```text
city name
->
geographic destination
->
route
->
road segment
->
lane maneuver
->
steering and speed target
->
actuator control
```

For manipulation:

```text
grasp the cup
->
resolve cup
->
resolve approach region
->
select hand
->
select grasp
->
generate trajectory
->
joint commands
```

For software:

```text
build project
->
resolve project
->
dependency graph
->
build targets
->
compiler invocations
->
machine instructions
```

Each layer converts one compact handle into a lower-level, more executable handle.

---

## 36. Resolution Is Progressive Constraint Satisfaction

Resolution does not merely replace names with locations.

It progressively establishes constraints.

Let:

\[
\mathcal S_i
\]

be the set of candidate meanings or realizations after resolver level \(i\).

A successful resolver narrows the candidate set:

\[
\mathcal S_{i+1}
\subseteq
\mathcal S_i
\]

while preserving at least one feasible realization.

The process ends when:

\[
|\mathcal S_n|
\]

is sufficiently small or structured for execution.

The objective is not necessarily to identify one microscopic trajectory in advance.

It is to produce enough specificity for the next responsible layer.

Thus:

> Resolution should stop at the interface where responsibility can safely pass downward.

---

## 37. Automatic Context Resolution

Agents routinely fill omitted information from context.

When a person hears:

```text
pick up the cup
```

they may automatically infer:

```text
the salient visible cup
the ordinary meaning of pick up
the nearest usable hand
a safe grasp region
a suitable force range
the expected completion state
```

Let:

\[
\Gamma_c
\]

be the active context, containing:

```text
perceptual salience
conversation history
shared conventions
current task
body state
environmental structure
social expectations
```

Then the interpretation is:

\[
\llbracket s\rrbracket_{\Gamma_c}
\]

The same signal may resolve differently under another context.

Automatic context resolution compresses communication but introduces failure risks.

---

## 38. Resolution Failures

Resolver failure modes include:

```text
unknown symbol
ambiguous operator
missing argument
ambiguous reference
stale location
unavailable implementation
wrong embodiment mapping
incompatible version
insufficient authority
unsafe local plan
semantic drift
incorrect contextual assumption
```

For example:

```text
grasp the cup
```

may fail because:

```text
no cup is visible
several cups are equally salient
the identified cup is outside reach
the agent lacks a grasping realization
the word grasp is not understood
the instruction conflicts with a safety rule
```

These failures occur at different layers and require different repairs.

---

## 39. Resolution Expands Accessible Capability

Let:

\[
\mathcal C_{\text{latent}}(c)
\]

be target classes physically supported by the configured system.

Let:

\[
\mathcal C_{\text{accessible}}(c,k,\mathcal R)
\]

be target classes the agent can identify, invoke, and realize using knowledge \(k\) and resolver system \(\mathcal R\).

Then:

\[
\mathcal C_{\text{accessible}}
\subseteq
\mathcal C_{\text{latent}}
\]

A system may contain a useful program but lack its filename.

A robot may contain a grasp controller but fail to localize the cup.

A city may contain a service but expose no discoverable procedure.

A human may possess a relevant skill but fail to recognize its applicability.

Resolvers narrow the gap between latent and accessible capability.

---

## 40. Guidance Is a Resolver-Control Interface

A guidance system occupies an intermediate role.

It does not necessarily execute the action.

It resolves a larger target into an instruction suitable for another agent or controller.

Formally:

\[
\rho_{\text{guide}}:
(G,C,K,M)
\to
\Chi
\cup
\{\operatorname{failure}\}
\]

where:

```text
G = goal
C = current configuration
K = represented knowledge
M = selected mode or embodiment
Χ = guidance chunk space
```

A good guidance interface hides irrelevant internal complexity while preserving:

```text
direction
timing
local preconditions
completion cues
critical warnings
recovery options
```

---

## 41. Guidance Granularity Is an Architectural Choice

A chunk can be too coarse.

Example:

```text
go to Munich
```

may be unusable for a driver without route knowledge.

A chunk can also be too fine.

Example:

```text
rotate steering wheel by 0.4 degrees
wait 8 milliseconds
rotate by 0.1 degrees
```

may overload the human and conflict with the vehicle’s own control loops.

Let:

\[
G(\chi,A,c)
\]

measure suitability of chunk granularity.

Useful granularity balances:

```text
interpretive burden
local autonomy
error detectability
update frequency
communication cost
state uncertainty
control stability
```

Thus:

> The correct chunk is not the smallest physically possible command. It is the smallest useful instruction for the receiving layer.

---

## 42. Delegation Depends on Resolver Depth

A high-level command delegates more resolution to the receiver.

For example:

```text
clean the room
```

requires the receiver to resolve:

```text
what counts as clean
which region is the room
which objects may be moved
which tools are usable
which sequence is efficient
which hazards must be avoided
```

A lower-level instruction:

```text
vacuum this marked floor region
```

delegates less.

A still lower-level instruction:

```text
move forward 0.5 meters
```

delegates less again.

The depth at which instruction stops and autonomous resolution begins determines the division of labor between planner and executor.

---

## 43. Autonomy Is Resolution Responsibility

Autonomy need not mean absence of external goals.

It can mean that the agent is responsible for resolving more levels between the given target and physical execution.

Let:

\[
D_A
\]

be the set of resolver layers assigned to agent \(A\).

A system with broader \(D_A\) can accept more abstract goals.

For example:

```text
teleoperated manipulator
accepts direct motion commands
```

```text
skill-based robot
accepts grasp commands
```

```text
task-level robot
accepts object relocation goals
```

```text
mission-level system
accepts broad outcome specifications
```

Thus:

> Greater autonomy corresponds partly to a larger internally maintained resolution stack.

---

## 44. Policies Preserve Prior Search

A policy converts current observations into actions without reconstructing the full decision problem each time.

\[
\pi:
O\to A
\]

A map preserves spatial search structure.

A controller preserves stabilization structure.

A skill preserves behavioral search and training.

A procedure preserves institutional search.

A compiler preserves translation structure.

All of these reduce recurring inverse-problem cost.

They differ mainly in:

```text
representation
scope
resolution depth
adaptivity
failure model
maintenance mechanism
```

Therefore persistent policies, maps, skills, and procedures are accumulated resolution infrastructure.

---

## 45. Frequently Used Compositions Become Higher-Level Operators

Suppose a recurring composition is:

\[
p=
u_1\circ u_2\circ\cdots\circ u_k
\]

If it is repeatedly useful, sufficiently stable, and worth maintaining, it may be promoted to:

\[
v=\operatorname{Promote}(p)
\]

with a simpler public interface.

The promotion may hide:

```text
internal sequencing
error recovery
resource reservation
reference management
control details
```

This creates hierarchical capability.

For example:

```text
motor torque control
->
walking controller
->
navigate to waypoint
->
deliver package
```

Each promoted operator becomes a resolvable chunk for the level above.

---

## 46. Capability Hierarchies

Let:

\[
\mathcal U^{(0)}
\]

be the primitive exposed operator set.

Let:

\[
\mathcal U^{(1)}
\]

contain promoted skills composed from level \(0\).

More generally:

\[
\mathcal U^{(i+1)}
=
\operatorname{Promote}
\left(
\operatorname{Closure}_{\text{feasible}}
(
\mathcal U^{(i)}
)
\right)
\]

The hierarchy may resemble:

```text
actuator functions
->
control primitives
->
sensorimotor skills
->
task operators
->
mission operators
->
organizational services
```

Higher levels increase usable reach by compressing validated lower-level compositions.

---

## 47. Capability Structure Rather Than a Flat Capability List

A flat list such as:

```text
walk
grasp
speak
navigate
pay
compile
```

does not expose:

```text
preconditions
composition dependencies
resource conflicts
resolver requirements
failure boundaries
supported argument regions
remaining options
```

A capability structure should represent:

\[
\mathcal G_A(c,H)
=
(
V,E,\Lambda,\Omega
)
\]

where:

```text
V = relevant configuration or subgoal regions
E = operator-generated reachable transitions
Λ = labels containing contracts, costs, authority, and reliability
Ω = resolver, interface, and observation structure
```

This is not necessarily a literal geometric map.

It is an agent-relative organization of executable reachability.

---

## 48. Capability Topology and Capability Geography

The phrase `capability geography` is useful when emphasizing:

```text
current location
target destination
mode-relative routes
local neighborhoods
barriers
bridges
maintained paths
replanning
```

The phrase `capability topology` is useful when emphasizing:

```text
connectivity
composition
reachability
interfaces
equivalence
continuity
```

The phrase `capability system` is useful when emphasizing:

```text
operators
controllers
resources
resolvers
implementations
execution
```

The formal core does not depend on choosing one metaphor.

The central object is agent-relative executable structure.

---

## 49. Why the Google Maps Analogy Is Strong

The navigation analogy captures more than route search.

It captures the full relation among:

```text
global target
current location
selected mode
maintained infrastructure
map representation
route synthesis
local guidance
state observation
deviation detection
replanning
arrival verification
```

The user does not need to continuously solve the routing problem.

The route service preserves prior mapping, traffic, naming, and search infrastructure.

The user gives the destination once and receives a sequence of locally resolvable instructions.

Thus:

> A useful capability system should not merely enumerate what could be done. It should maintain enough structured knowledge to resolve a target into the next executable interaction for the configured agent.

---

## 50. Why the Drone Analogy Is Also Strong

Drone control emphasizes the layered control architecture:

```text
mission
->
path
->
trajectory
->
stabilization
->
actuation
```

Google Maps emphasizes the interface between global routing and a bounded human executor:

```text
destination once
->
successive local instructions
```

The two analogies describe different portions of the same hierarchy.

Drone control shows downward realization.

Navigation guidance shows bounded communication and delegated local execution.

Together they suggest:

```text
global coherence
+
hierarchical resolution
+
local closed-loop control
```

---

## 51. Human Action Fits the Same Pattern

Human action often proceeds through nested abstractions.

For example:

```text
make coffee
```

may resolve to:

```text
go to kitchen
prepare machine
obtain cup
add water
add coffee
start brewing
serve
```

The subgoal:

```text
obtain cup
```

may resolve to:

```text
locate cup
approach cupboard
open door
reach
grasp
withdraw
```

The skill:

```text
grasp
```

may resolve to:

```text
select hand
shape fingers
move arm
correct trajectory
close grip
verify stability
```

The person usually does not represent all lower levels explicitly.

Different levels become conscious when:

```text
the routine fails
the environment is unfamiliar
the body is impaired
the object is unusual
the instruction is ambiguous
```

This suggests that conscious deliberation often appears when automatic resolvers cannot produce a trustworthy next chunk.

---

## 52. Product Identity Through Organized Capability

A smartphone is not merely a bag of:

```text
processor
battery
screen
camera
radio
storage
software
```

Its identity depends on an organization that exposes capabilities such as:

```text
communication
application execution
internet access
media capture
navigation
persistent data management
```

A floor-cleaning robot is not merely:

```text
wheels
motors
sensors
battery
software
```

Its organization may realize:

\[
\operatorname{CleanFloorRegion}
\]

through lower-level skills such as:

```text
localize
avoid obstacle
move
collect debris
return to dock
```

Objects are not defined only by capability, but organized capability is a major operational basis for distinguishing systems from unassembled collections of parts.

---

## 53. Learning by Imitation Produces Resolver-Compatible Skills

A demonstration provides one or more trajectories:

\[
\eta_1,\dots,\eta_n
\]

Learning attempts to infer reusable structure:

\[
\{\eta_i\}
\to
\pi
\]

where \(\pi\) is a policy or controller.

For a humanoid, imitation also requires embodiment resolution:

\[
\text{human motion}
\to
\text{robot-relative task representation}
\to
\text{robot-feasible control}
\]

The resulting policy becomes a skill only when it generalizes sufficiently across an admissible region.

It contributes to operational capability only when:

```text
the required body exists
the environment is compatible
the references resolve
the task is within the learned regime
the controller remains stable
```

Thus imitation learning can be understood as constructing new reusable resolver-compatible composition machinery.

---

## 54. Selection, Execution, and Verification Must Remain Distinct

A planner may select a chunk:

\[
\chi_t
\]

The executor may attempt it:

\[
\operatorname{Execute}(\chi_t,c_t)
\]

The observer may report:

\[
o_{t+1}
\]

These are distinct events.

The planner may choose a valid action that fails operationally.

The action may succeed while the observation is delayed or ambiguous.

The observation may indicate success incorrectly.

Therefore the loop should distinguish:

```text
selected instruction
attempted realization
actual transition
observed transition
verified local completion
```

A robust guidance system supplies not only a command but also an expected completion predicate.

---

## 55. Arrival and Completion Are Resolution Problems

A system must know when to stop or advance.

For a navigation chunk:

```text
turn left at the next intersection
```

completion may require resolving:

```text
which intersection counts as next
whether the turn has occurred
whether the vehicle entered the intended road
```

For grasping:

```text
grasp the cup
```

completion may require:

```text
contact established
gripper closed
cup lifted
slip below threshold
```

Let:

\[
Q_\chi(c,o)
\]

be the local completion predicate.

A chunk is successfully discharged when:

\[
Q_\chi(c',o')=1
\]

Without completion resolution, the system cannot reliably advance to the next chunk.

---

## 56. Global Targets Need Not Be Continuously Repeated

A global goal can remain persistently bound:

\[
g_t=g
\]

while local chunks change:

\[
\chi_t
=
\rho(g,c_t,k_t)
\]

The agent need not receive the full goal description at every low-level update.

The goal is retained as persistent context.

This resembles:

```text
destination retained by navigation system
mission retained by autopilot
function call retained by runtime
task retained by working memory
transaction retained by workflow engine
```

Persistent goal binding reduces repeated communication.

---

## 57. Context Is Part of Invocation

An instruction is not executable independently of its context.

Let:

\[
\llbracket s\rrbracket_c
\]

denote the interpretation of signal \(s\) under configuration \(c\).

The same phrase:

```text
open it
```

may denote different operator instances depending on:

```text
conversation history
pointing gesture
visible objects
active application
current task
authority
physical location
```

Therefore:

```text
signal
+
context
->
resolved invocation
```

The context is not optional decoration.

It supplies omitted bindings.

---

## 58. Too Much Context Can Also Fail

More context is not always better.

A resolver may be harmed by:

```text
stale information
conflicting instructions
irrelevant detail
excess candidate references
semantic drift
overloaded working memory
obsolete route assumptions
```

The resolution problem includes selecting which context remains relevant.

Let:

\[
\Pi_g(k)
\]

be a goal-conditioned projection of knowledge state.

A resolver should operate on:

\[
\Pi_g(k)
\]

when the full knowledge state is too large or noisy.

Thus bounded agents require not only information acquisition but context curation.

---

## 59. Local Decisions Can Preserve Global Optionality

The nearest action is not always the best action.

A local chunk should also be evaluated by the future frontier it preserves.

Let:

\[
\mathcal U_{\mathrm{exec}}(c')
\]

be the executable frontier after the chunk.

A useful local value may include:

\[
V(\chi,c,g)
=
G_{\text{progress}}
-
C_{\text{execution}}
-
C_{\text{risk}}
+
G_{\text{optionality}}
\]

A route that is slightly longer may preserve:

```text
more fuel
safer alternatives
better communication
more reliable infrastructure
lower chance of entrapment
```

Therefore locality reduces immediate decision scope, but global planning must still shape which local options are preferred.

---

## 60. The Core Resolution Loop

The full architecture can be summarized as:

\[
(g,c_t,k_t)
\overset{\rho_{\text{plan}}}{\longrightarrow}
p_t
\]

\[
(p_t,c_t,k_t)
\overset{\rho_{\text{guide}}}{\longrightarrow}
\chi_t
\]

\[
(\chi_t,c_t)
\overset{\rho_{\text{embody}}}{\longrightarrow}
a_t
\]

\[
(c_t,a_t)
\overset{\operatorname{Execute}}{\longrightarrow}
(c_{t+1},o_{t+1})
\]

\[
(k_t,o_{t+1})
\overset{\operatorname{Update}}{\longrightarrow}
k_{t+1}
\]

then repeat.

The architecture is neither purely symbolic nor purely reactive.

It combines:

```text
persistent global target
stored structural knowledge
local context
hierarchical resolution
closed-loop execution
```

---

## 61. Core Construction

The framework can be summarized as:

```text
components realize primitive functions
->
selected functions are exposed as invocable operators
```

```text
controllers and policies organize lower-level transitions
->
stable compositions become skills
```

```text
operator systems include composition, constraints, interfaces, and resolvers
->
operator inventories alone do not determine capability
```

```text
feasible composition closure
->
supported target classes
```

```text
supported target classes under declared conditions
->
operational capability
```

```text
tasks specify target regions
->
agents face inverse reachability problems
```

```text
physical interaction and finite attention are local
->
only a bounded action frontier is immediately relevant
```

```text
persistent maps, policies, skills, and infrastructure
->
large searches and trajectories can be reused
```

```text
global target
+
current configuration
+
resolver hierarchy
->
next locally executable chunk
```

```text
execution
+
observation
->
updated context and replanning
```

```text
successive resolvable chunks
->
bounded agents can realize long trajectories without receiving the whole trajectory at once
```

---

## 62. Core Principles

### Principle 1: Components and capabilities are different levels of description

Components realize functions; organized systems support capabilities.

### Principle 2: Not every function is an exposed operator

Invocability requires a stable access path, signature, contract, and realization.

### Principle 3: An operator system is more than an inventory

Composition rules, resources, embodiment, authority, interfaces, and resolvers determine practical reach.

### Principle 4: Skills are stabilized behavioral compositions

A skill compresses lower-level control and feedback into a reusable higher-level interface.

### Principle 5: Capability is feasible composition closure

Operational capability consists of target effects reachable through executable compositions under declared conditions.

### Principle 6: Capability is agent-relative

The same environment and operator vocabulary yield different executable frontiers for different bodies, tools, resources, permissions, and knowledge states.

### Principle 7: Operator availability does not imply invocation executability

A general grasp skill does not make every object graspable from every configuration.

### Principle 8: Direct failure does not imply target unreachability

A missing direct edge may be replaced by a longer valid composition.

### Principle 9: Goal-directed action is inverse reachability search

The target is given; the producing executable structure must be found.

### Principle 10: Search may target operators, bridges, tools, references, or infrastructure

The missing object is not always an action sequence.

### Principle 11: Physical interaction is locally mediated

Global outcomes are generally composed from locally executable transitions.

### Principle 12: Locality is agent- and mode-relative

Adjacency depends on embodiment, tools, authority, and selected interaction mode.

### Principle 13: Infrastructure extends effective locality

A local interface can activate a maintained long-range composition.

### Principle 14: Global planning and local execution should be separated

Different layers require different horizons, representations, and update rates.

### Principle 15: Bounded agents require bounded guidance chunks

The whole route need not fit into the current instruction.

### Principle 16: A useful chunk is resolvable, executable, and verifiable

Its meaning, arguments, local conditions, and completion cues must fit the receiving layer.

### Principle 17: Long-horizon coherence does not require open-loop control

Persistent goals can guide repeated local replanning.

### Principle 18: Handles compress retained organization

Names, task labels, and destinations are entry points into resolver hierarchies rather than complete trajectories.

### Principle 19: Language usually transmits handles, not motor programs

Shared context and learned resolver infrastructure fill omitted detail.

### Principle 20: Uninterpretable instructions are not executable through that interface

Physical capability does not guarantee semantic invocability.

### Principle 21: Resolution is progressive concretization

Each resolver layer supplies distinctions required by the next layer.

### Principle 22: Resolution should stop at the correct responsibility boundary

The next layer should receive enough detail to act, but not unnecessary lower-level complexity.

### Principle 23: Autonomy is partly internal resolution capacity

An agent that can accept abstract goals maintains more of the goal-to-control stack internally.

### Principle 24: Policies, maps, skills, and procedures preserve prior search

They are accumulated resolution infrastructure.

### Principle 25: Repeated compositions can be promoted into higher-level operators

Promotion creates hierarchical capability and reduces recurring coordination cost.

### Principle 26: Accessible capability may be smaller than latent capability

Missing references, interpretations, locators, or interfaces can hide physically supported outcomes.

### Principle 27: Selection, execution, observation, and verification are distinct

Correct planning alone does not guarantee known success.

### Principle 28: Completion conditions are part of guidance

The system must resolve when a chunk has been successfully discharged.

### Principle 29: Context is part of invocation

Omitted arguments are often supplied by perceptual, linguistic, social, or operational context.

### Principle 30: Context must be curated

Irrelevant, stale, or conflicting information can reduce resolution quality.

### Principle 31: Local action should preserve global viability

Immediate progress should be balanced against risk, resources, and remaining options.

### Principle 32: Practical capability is hierarchical, referential, and closed-loop

Useful action depends on organized transitions, resolvable handles, local execution, observation, and repeated updating.

---

## 63. Open Questions

```text
What is the correct formal boundary
between a function, an operator, a controller, a skill, and a capability?
```

```text
How should operational capability be measured
when success varies across environments and task distributions?
```

```text
What reliability threshold converts
a possible composition into a stable capability?
```

```text
How should a capability system represent
continuous embodiment constraints without enumerating every state?
```

```text
What is the minimum resolver hierarchy
needed to convert a declared target into executable control?
```

```text
When should planning return a complete route,
a subgoal, an operator instance, or only the next local chunk?
```

```text
How should guidance granularity adapt
to the receiving agent's skill, attention, and uncertainty?
```

```text
What information must a chunk expose
to remain independently verifiable?
```

```text
How should resolver failures be localized
so that the system repairs the correct layer?
```

```text
When should an ambiguous instruction trigger clarification
rather than autonomous contextual resolution?
```

```text
How can systems distinguish
helpful implicit context from unsafe hidden assumptions?
```

```text
How should global planners value
future optionality and recoverability?
```

```text
When should a frequently executed route
be promoted into a persistent skill or higher-level operator?
```

```text
How should capability maps represent
changing resources, body state, authority, and infrastructure?
```

```text
Can capability topology be learned
from demonstrations, failed attempts, and observed interventions?
```

```text
How should two agents compare capabilities
when their embodiments and interfaces differ?
```

```text
What constitutes capability transfer
across different bodies or hardware architectures?
```

```text
How can a system prove that a high-level skill
refines the contracts of its lower-level components?
```

```text
How should semantic maintenance be budgeted
when language, interfaces, and implementations change?
```

```text
Can human conscious deliberation be modeled
as escalation after automatic resolver failure?
```

```text
How should organizational procedures be analyzed
as distributed resolver stacks across multiple agents?
```

```text
What is the correct stopping rule
for inverse reachability search under finite time?
```

```text
When does local replanning destroy global coherence,
and which invariants must persist across replans?
```

```text
How should uncertainty be propagated
from global route selection to local execution guidance?
```

```text
Can one formalism cover
navigation, manipulation, software execution, institutional action, and language-guided behavior
without erasing their important differences?
```

---

## 64. Design Target

The design target is a framework in which:

```text
components
are separated from the functions they realize
```

```text
functions
are separated from exposed invocable operators
```

```text
operators
are analyzed as part of constrained composition systems
```

```text
controllers and learned policies
are represented as realizations of reusable skills
```

```text
capability
is defined through feasible target-conditioned composition closure
```

```text
tasks
are represented as target regions rather than complete trajectories
```

```text
embodiment, resources, authority, and environment
remain explicit in executability
```

```text
direct invocation failure
is separated from global target unreachability
```

```text
goal-directed action
is treated as inverse reachability search
```

```text
physical locality
is treated as the basis of immediate action
```

```text
persistent infrastructure
is treated as extension of effective locality
```

```text
global planning
is separated from local guidance and control
```

```text
resolver hierarchies
progressively convert compact handles into executable instances
```

```text
guidance chunks
are bounded, interpretable, executable, and verifiable
```

```text
persistent goals
support repeated closed-loop replanning
```

```text
maps, policies, skills, and procedures
are treated as retained solutions to recurring inverse problems
```

```text
autonomy
is partly measured by the depth of internally maintained resolution
```

```text
human action, robot control, navigation, computation, and institutions
can be compared through shared structural distinctions
without being reduced to identical mechanisms
```

---

## 65. Central Claim

A component does not by itself determine a capability.

A function does not automatically become an operator.

An operator name does not make every invocation executable.

A skill does not guarantee success in every configuration.

A possible composition does not establish a stable capability.

A target does not contain its own route.

A route does not need to be transmitted as one complete instruction.

A handle does not contain the organization it activates.

A global planner does not need to control every actuator directly.

A local controller does not need to solve the entire mission.

A bounded agent does not need an infinite stream of information.

It needs:

```text
a persistent target
+
an agent-relative model of executable structure
+
maintained operators and skills
+
resolvable references
+
a hierarchy that converts global intent into local action
+
bounded guidance chunks
+
closed-loop observation and replanning
```

Therefore:

> Capability is the stable availability of target-reaching composition realizations for a configured agent. Practical action consists in repeatedly resolving a retained global target into the next locally executable and verifiable chunk, executing it through the appropriate lower-level machinery, observing the result, and resolving again.

Long trajectories become manageable because they are not held or communicated as indivisible wholes.

They are traversed through organized, reusable, context-sensitive resolution.
