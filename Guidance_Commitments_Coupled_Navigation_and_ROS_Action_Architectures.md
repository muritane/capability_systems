# Guidance Commitments, Coupled Navigation, and ROS Action Architectures

## Abstract

A global goal does not determine the next executable transition by itself.

The request:

```text
reach destination D
```

may require:

```text
localization
route selection
mode selection
traffic interpretation
intersection recognition
vehicle control
human attention
physical motion
progress observation
replanning
arrival verification
```

A system such as Google Maps does more than compute a route.

It maintains an evolving relation among:

```text
global target
estimated executor state
selected movement mode
maintained map and traffic structure
locally relevant decision boundaries
bounded human interpretability
observed progress
replanning conditions
```

and repeatedly emits a next instruction such as:

```text
continue for 1.2 km
turn left at the next intersection
board the train on platform 4
reroute through the next available exit
```

These instructions are not equal units of distance, time, or locomotion.

They are context-sensitive units of guidance.

This document proposes the **guidance commitment** as a general unit for such systems.

A guidance commitment is a bounded, revisable, state-indexed recommendation that selects a locally executable transition, declares the frame and conditions under which it is appropriate, identifies the expected observable effect, and specifies when completion, cancellation, or replanning should occur.

The proposal clarifies several related distinctions:

```text
physical movement
versus
task-relevant transition
```

```text
feedback
versus
guidance
```

```text
planning
versus
execution
```

```text
action server
versus
navigator
```

```text
executor state
versus
navigator belief about executor state
```

```text
one isolated capability
versus
a capability realized by a coupled guide-executor system
```

ROS Actions provide a useful architectural comparison because they already distinguish goals, ongoing feedback, cancellation, and final results.

However, a navigation-oriented capability system introduces a different division of labor.

The navigator may not execute the world-changing transition itself. It may instead maintain a model of another executor, derive successive guidance commitments, observe the executor's progress, and revise the commitments as the shared situation changes.

The resulting architecture is not merely client-server communication.

It is a coupled realization system:

```text
persistent goal
+
navigator
+
executor
+
observation channel
+
world
+
replanning loop
->
extended target-reaching capability
```

The central claim is:

> Practical guidance is the repeated production, discharge, observation, and revision of bounded transition commitments relative to a persistent target and an evolving estimate of the executor's configuration.

---

## 1. Starting Point

Consider a person driving on a highway while receiving the instruction:

```text
Continue for 40 km.
```

Relative to the car, the person's body may remain approximately stationary.

Relative to the road or map frame, both the person and the car move approximately 40 km.

Relative to the person's body, the hands, eyes, head, and feet may undergo many smaller motions.

Relative to the software state of the navigation system, the important transition may instead be:

```text
current route segment
->
next maneuver region
```

All of these descriptions may be correct.

They refer to different frames, projections, and purposes.

The central question is therefore not:

```text
Did movement occur?
```

Movement and physical change occur throughout the realization.

The more useful questions are:

```text
Which system is being tracked?
Relative to which frame?
Which state variables define progress?
Which transition is exposed to the executor?
Which observation establishes completion?
Which deviation requires replanning?
```

---

## 2. Every Realization Contains Physical Transition

Running an application is not physically motionless.

Its realization may include:

```text
finger motion
key displacement
electrical switching
memory transitions
storage transitions
packet propagation
cooling airflow
screen emission
human perception
```

Likewise, remaining seated in a moving vehicle does not imply remaining stationary in every frame.

Therefore:

```text
software transition
!=
absence of physical transition
```

and:

```text
small motion relative to one frame
!=
small motion relative to every frame
```

A task-level abstraction suppresses many physical details.

It does not remove them from the realized trajectory.

Thus:

> A transition may be non-spatial at one descriptive level while remaining physically realized through spatial, electrical, mechanical, and thermodynamic change at lower levels.

---

## 3. Frame-Indexed Change

Let:

```text
A = tracked system
F = reference frame
q_A^F(t) = represented configuration of A relative to F at time t
```

Spatial motion relative to frame \(F\) occurs when:

\[
q_A^F(t_1)
\neq
q_A^F(t_2)
\]

For a passenger \(P\) in a car \(C\):

\[
q_P^C(t_1)
\approx
q_P^C(t_2)
\]

while:

\[
q_P^{map}(t_1)
\neq
q_P^{map}(t_2)
\]

The first relation says that the passenger remains approximately fixed relative to the car.

The second says that the passenger changes position relative to the map.

Neither statement overrides the other.

They expose different relations.

This is familiar in ROS `tf`-style reasoning, where transformations are indexed by frames rather than treated as absolute properties.

The same principle can be generalized beyond spatial pose.

---

## 4. Generalized Frames of Relevance

A frame need not be only a Cartesian coordinate frame.

For practical guidance, a **frame of relevance** declares the state projection under which a transition is evaluated.

Examples include:

```text
map frame
:
vehicle pose and route progress
```

```text
body frame
:
limb configuration and contact relations
```

```text
deployment frame
:
packages, services, credentials, and runtime state
```

```text
institutional frame
:
roles, approvals, records, and legal status
```

```text
conversation frame
:
shared references, commitments, and unresolved questions
```

```text
capability frame
:
currently executable operators and reachable target regions
```

Let:

\[
\pi_F(c)
\]

be the projection of full configuration \(c\) into frame of relevance \(F\).

Then task-relevant change may be represented as:

\[
\pi_F(c_t)
\to
\pi_F(c_{t+1})
\]

while many other components of the full physical configuration also change.

The projection is not the whole realization.

It is the selected relation used for guidance, verification, or control.

---

## 5. Locomotion Is One Transition Family

Locomotion should not be used as the universal primitive.

It is one important transition family:

> Locomotion is a change in the spatial pose of an embodied system relative to a selected external frame, while preserving enough organizational continuity to treat it as the same moving system.

Related but distinct notions include:

```text
physical motion
=
change in spatial configuration
```

```text
articulation
=
relative movement among parts of a system
```

```text
locomotion
=
displacement of an embodied system through an environment
```

```text
transport
=
locomotion whose main mechanical realization is supplied by another coupled system
```

```text
state transition
=
any relevant change in represented configuration
```

The passenger is transported by the car and also undergoes locomotion relative to the map.

The passenger may contribute little mechanical work while still undergoing the displacement.

Therefore:

```text
displacement
!=
causal control of displacement
```

```text
being moved
!=
remaining motionless
```

```text
locomotion
!=
all transition
```

---

## 6. Transition Type and Causal Role

A realized transition may involve several systems with different roles.

For a car journey:

```text
passenger
:
target selection, supervision, possible control
```

```text
vehicle
:
mechanical transport realization
```

```text
navigation service
:
route resolution and local guidance
```

```text
road infrastructure
:
maintained traversable adjacency
```

```text
traffic system
:
dynamic constraints and interaction
```

```text
map and localization stack
:
state estimation and route-relative interpretation
```

All participate in one extended trajectory.

Their participation should not be collapsed into one undifferentiated agent.

A useful model distinguishes:

```text
what changes
who or what produces the change
who selects the change
who observes the change
who evaluates progress
who may revise the plan
```

---

## 7. Configuration Is an Argument of Transition

An operator name does not determine a transition independently of configuration.

Let:

```text
u = operator schema
a = invocation arguments
c = current configuration
e = environment
```

Then a transition candidate is:

\[
\llbracket u(a) \rrbracket(c,e)
\]

rather than:

\[
u(a)
\]

alone.

The configuration may contain:

```text
world state
represented knowledge
body or hardware state
resource state
authority state
environment
current time
active commitments
```

Thus:

\[
c=(x,k,b,r,\alpha,e,t,\kappa)
\]

where \(\kappa\) is the current set of active commitments.

The same operator may be:

```text
executable in one configuration
inapplicable in another
unsafe in another
unresolved in another
already completed in another
```

This is the structural point shared with systems such as Nix.

A systematic check is performed over a particular requested realization under a particular configuration.

The configuration is not merely background metadata.

It is an argument in the realizability relation.

---

## 8. Structural Checking and Guided Realization

A preflight resolver may answer:

```text
Can this requested realization be supported under the represented configuration?
```

A navigator must answer a temporally extended sequence of questions:

```text
What should be attempted next?
Is that recommendation still valid?
Did the executor enter the expected region?
Should the current commitment be continued, completed, cancelled, or revised?
Does the global target remain reachable?
```

The distinction is:

```text
structural check
=
evaluate one requested realization against a configuration
```

```text
guided realization
=
repeat structural selection and revision as configuration changes
```

A static resolver may be invoked once.

A navigator participates throughout an unfolding trajectory.

---

## 9. What Is the Unit of Google Maps Guidance?

The unit is not a fixed distance.

It is not a fixed duration.

It is not always one road edge.

It is not always one intersection.

Instructions vary:

```text
Continue for 40 km.
```

```text
Keep right in 300 m.
```

```text
Take the next exit.
```

```text
Board the train toward Central Station.
```

```text
Walk to platform 6.
```

```text
Wait for the delayed service.
```

```text
Make a U-turn when possible.
```

Their size depends on:

```text
speed
mode of travel
distance to decision boundary
road complexity
expected traffic
local uncertainty
quality of localization
executor reaction time
visibility of landmarks
working-memory burden
risk of missed action
communication bandwidth
```

The general unit is therefore not a geometric constant.

It is a bounded instruction selected so that the receiving executor can interpret, execute, and verify it before the next important decision boundary.

---

## 10. Decision Boundaries Determine Resolution Granularity

A long highway segment may permit coarse guidance because few choices are locally relevant.

A dense junction requires finer guidance because several transitions become possible within a short interval.

Let:

```text
D(c) = distance or time to the next decision-sensitive region
R_A = executor reaction and interpretation capacity
U(c) = uncertainty in current state
K(c) = local transition complexity
L(c) = consequence of a missed decision
```

Then guidance granularity may be treated schematically as:

\[
\operatorname{Granularity}
=
G(D,R_A,U,K,L)
\]

A useful chunk becomes smaller or earlier when:

```text
uncertainty increases
transition density increases
reaction time increases
risk increases
landmark quality decreases
```

It may become larger when:

```text
the route is stable
the next decision is distant
local alternatives are irrelevant
localization is reliable
the executor can maintain the current mode autonomously
```

Thus:

> Guidance resolution should be adapted to decision structure, not normalized to one physical unit.

---

## 11. The Resolvable Guidance Chunk

Let \(\chi_t\) be a guidance chunk issued at time \(t\).

A useful chunk should satisfy:

\[
\operatorname{Relevant}(\chi_t,\hat c_t,g)
\]

\[
\land
\operatorname{Interpretable}(\chi_t,A,\hat c_t)
\]

\[
\land
\operatorname{Executable}(\chi_t,A,\hat c_t)
\]

\[
\land
\operatorname{Verifiable}(\chi_t,O,\hat c_t)
\]

\[
\land
\operatorname{ViabilityPreserving}(\chi_t,g,H)
\]

where:

```text
A = executor
O = observation organization
hat c_t = navigator's estimated current configuration
g = retained global target
H = relevant horizon
```

The chunk should not merely be locally possible.

It should also preserve or improve the expected ability to reach the retained target.

---

## 12. From Guidance Chunk to Guidance Commitment

A bare chunk such as:

```text
Turn left.
```

omits important structure.

A stronger object is a **guidance commitment**.

A guidance commitment states approximately:

> Given the current represented configuration, target, evidence, and tolerances, this is the next transition the navigator currently endorses; this endorsement remains valid only within the declared conditions and should be revised when its completion or invalidation criteria are observed.

Let:

\[
\gamma_t
=
(
I,
G,
F,
u,
a,
P,
Q,
O,
V,
R,
\rho,
\Xi
)
\]

where:

```text
I = commitment identity and version
G = retained global goal or linked subgoal
F = frame of relevance
u = selected operator or operator family
a = bound arguments
P = entry and applicability conditions
Q = expected transition or target region
O = observation and completion contract
V = validity interval and horizon
R = risk, resource, and authority constraints
rho = confidence and evidence state
Xi = cancellation, fallback, and replanning rules
```

The commitment is more than an instruction string.

It is a bounded transition contract between guidance and execution layers.

---

## 13. Why Call It a Commitment?

The term `commitment` should be used carefully.

It does not mean:

```text
guaranteed success
```

```text
irrevocable command
```

```text
executor obligation independent of conditions
```

It means that the guiding system commits its current model and recommendation sufficiently to expose one actionable transition rather than returning only an unresolved possibility set.

The commitment is indexed by:

```text
current evidence
current state estimate
current target
current tolerances
current validity region
```

It is therefore provisional and defeasible.

A more explicit name is:

```text
state-indexed guidance commitment
```

or:

```text
guidance contract token
```

The important idea is not the word itself.

It is the transition from:

```text
many possible routes
```

to:

```text
one currently endorsed next interaction with declared limits
```

---

## 14. Guidance Is Not the Same as Feedback

Feedback is primarily descriptive.

It reports something about an unfolding execution:

```text
current pose
35 percent complete
distance remaining
battery level
current phase
error condition
```

Guidance is primarily prescriptive.

It selects or constrains what should occur next:

```text
continue on this segment
reduce speed
use the next exit
request authorization
wait for the resource
cancel before commitment boundary
```

The distinction is:

```text
feedback
=
what the system believes is occurring
```

```text
guidance
=
what the system currently recommends should occur next
```

A single message may contain both.

But their semantic roles should remain distinguishable.

---

## 15. Observation, Feedback, and Guidance Form a Loop

A guided system may contain the loop:

```text
world transition
->
sensor observation
->
state estimate
->
progress assessment
->
route or plan revision
->
guidance commitment
->
executor interpretation
->
world transition
```

Let:

```text
o_t = observation at time t
hat c_t = estimated executor-world configuration
M_t = navigator model
g = retained target
gamma_t = current guidance commitment
```

Then:

\[
\hat c_t
=
\operatorname{Estimate}(M_t,o_{0:t})
\]

\[
\gamma_t
=
\operatorname{Guide}(M_t,\hat c_t,g,\Theta)
\]

After execution and new observation:

\[
(M_{t+1},\hat c_{t+1})
=
\operatorname{Update}(M_t,\hat c_t,\gamma_t,o_{t+1})
\]

The next commitment is then recomputed or reaffirmed.

---

## 16. The Navigator Maintains a Belief, Not the Client's State Itself

It is imprecise to say that the server simply contains the client's current position.

It normally contains an estimate or belief about that position.

The distinction is:

```text
actual executor-world state
=
c_t
```

```text
navigator estimate
=
hat c_t
```

In general:

\[
\hat c_t
\not\equiv
c_t
\]

The difference may arise from:

```text
sensor error
latency
map mismatch
stale reports
ambiguous localization
unobserved manual action
communication loss
concurrent environmental change
```

Therefore guidance must be confidence- and evidence-indexed.

A responsible navigator should be able to express:

```text
state believed with high confidence
state uncertain
state inconsistent across sources
state too stale for safe guidance
```

---

## 17. Coupling Is the Source of the Capability

The coupling is not accidental complexity.

It is the organization through which the extended capability exists.

A navigator without an executor can compute or communicate routes but cannot realize the journey.

An executor without route knowledge may move but may not reach the intended destination efficiently or reliably.

An observation channel without either does not select or execute transitions.

The coupled system is:

\[
\mathcal S
=
N
\oplus
A
\oplus
O
\oplus
W
\]

where:

```text
N = navigator
A = executor or acting agent
O = observation and communication organization
W = world and supporting infrastructure
```

The joint capability may satisfy:

\[
\operatorname{Cap}(N\oplus A\oplus O\oplus W,c,H)
\supset
\operatorname{Cap}(A,c,H)
\]

for relevant target classes.

Google Maps extends navigation capability because the coupled organization can realize target-reaching trajectories unavailable or unreliable to the unaided executor.

---

## 18. Coupled Does Not Mean Undifferentiated

A system can be tightly coupled while preserving clear responsibility boundaries.

The roles may include:

```text
goal owner
:
defines or accepts the global target
```

```text
navigator
:
resolves the target into route-relative guidance
```

```text
executor
:
selects and realizes local physical or symbolic action
```

```text
observer
:
produces evidence about state and progress
```

```text
resolver
:
binds names, providers, references, and interfaces
```

```text
controller
:
stabilizes lower-level dynamics
```

```text
verifier
:
determines whether completion conditions are satisfied
```

One component may occupy several roles.

The roles remain analytically distinct.

Convolution arises when the architecture hides which role owns:

```text
state estimation
transition selection
actuation authority
completion judgment
failure recovery
```

The solution is not to remove coupling.

It is to make the coupling contract explicit.

---

## 19. ROS Actions as a Structural Analogy

A typical action architecture distinguishes:

```text
goal request
ongoing feedback
cancellation
final result
```

This is useful for long-running operations whose completion cannot be represented as an immediate request-response exchange.

A conventional action relation may be summarized as:

```text
action client
->
goal
->
action server
->
internal execution
->
feedback
->
result
```

The action server normally owns or coordinates realization of the requested action.

For example:

```text
NavigateToPose(goal)
```

may be accepted by a server that plans, controls, observes, recovers, and eventually returns success or failure.

This already resembles a closed-loop realization architecture.

---

## 20. Why Guidance Is Not Identical to an Ordinary ROS Action

In a guidance system, the guiding component may not own the world-changing execution.

The relation may instead be:

```text
executor or user
->
global target
->
navigator
->
guidance commitment
->
executor
->
world transition
->
observation
->
navigator
```

The navigator chooses or recommends a local action.

The executor performs it.

Therefore the navigator is not simply an action server that internally executes the requested world transition.

It is closer to a server for **guided realization**.

Its output is not only descriptive feedback.

Its output contains new prescriptive commitments.

---

## 21. Guidance Can Still Be Represented Through Actions

The difference is semantic rather than an absolute incompatibility with ROS Actions.

A guidance architecture can be represented in several ways.

### Pattern A: Navigator owns the whole action

```text
client sends global goal
navigator coordinates executor internally
navigator returns feedback and result
```

Here the executor is an internal provider or subordinate action server.

### Pattern B: Navigator emits guidance as action feedback

```text
client sends global goal
navigator emits successive guidance commitments as feedback
client or human executes them
client reports progress through another channel
```

This is convenient but overloads `feedback` with prescriptive content.

### Pattern C: Bidirectional guided-action protocol

```text
goal channel
observation channel
guidance channel
acknowledgment channel
result channel
cancellation channel
```

This makes the coupling explicit.

### Pattern D: Nested actions

```text
global navigation action
->
local guidance action
->
executor action
->
controller actions
```

Each layer owns the transition appropriate to its responsibility boundary.

No single pattern is universally correct.

---

## 22. A Guided Realization Protocol

A general protocol may contain the following message classes.

### Goal

```text
target predicate
constraints
horizon
preferred modes
risk tolerance
completion authority
```

### State report

```text
observed configuration
timestamp
frame
source
uncertainty
active local action
```

### Guidance commitment

```text
next operator
bound arguments
entry conditions
expected effect
completion cues
validity interval
cancel and replan conditions
```

### Acknowledgment

```text
accepted
rejected
uninterpretable
inapplicable
already satisfied
requires clarification
```

### Progress observation

```text
started
ongoing
deviated
completed
failed
aborted
```

### Final result

```text
global target satisfied
target unsatisfied
target abandoned
model insufficient
execution authority withdrawn
```

This is more conversational than a one-way command stream.

But it remains structured.

---

## 23. The Guidance Commitment Lifecycle

A guidance commitment may pass through states such as:

```text
proposed
->
validated
->
issued
->
acknowledged
->
active
->
completed
```

with alternative transitions:

```text
proposed
->
rejected
```

```text
issued
->
expired
```

```text
active
->
deviated
->
replanned
```

```text
active
->
failed
->
recovered or abandoned
```

```text
active
->
cancelled
```

The lifecycle should distinguish:

```text
the guide selected an instruction
```

from:

```text
the executor received it
```

from:

```text
the executor accepted it
```

from:

```text
the world transition occurred
```

from:

```text
the transition was observed and verified
```

---

## 24. Guidance Commitment Schema

A practical schema may resemble:

```yaml
guidance_commitment:
  id: gc-1842
  version: 3

  global_goal:
    predicate: at_destination
    destination: munich_central

  local_target:
    predicate: entered_exit_corridor
    corridor: A9_exit_76

  frame:
    kind: route_progress
    spatial_reference: map
    mode: automobile

  operator:
    id: take_exit
    arguments:
      exit: 76
      direction: south

  applicability:
    route_segment: A9_southbound
    speed_range_kmh: [40, 140]
    localization_confidence_min: 0.85

  expected_transition:
    from_region: A9_mainline_before_exit_76
    to_region: exit_76_corridor

  observation:
    completion:
      - vehicle_pose_inside: exit_76_corridor
    failure:
      - vehicle_pose_beyond: exit_76_split
    uncertainty:
      - localization_confidence_below: 0.6

  validity:
    not_before: 2026-07-19T19:20:00Z
    expires_after_seconds: 90

  replanning:
    on_deviation: immediate
    on_traffic_change: if_route_cost_delta_exceeds_threshold

  assurance:
    evidence_state: observed_and_map_consistent
    confidence: 0.93

  authority:
    mode: advisory
    executor_may_refuse: true
```

The schema is illustrative.

Its purpose is to expose the relations hidden by a short instruction.

---

## 25. Advisory, Delegated, and Direct-Control Commitments

Guidance may carry different authority modes.

### Advisory

```text
The executor remains responsible for deciding whether to act.
```

Example:

```text
human navigation instruction
```

### Delegated

```text
The executor has previously authorized the guide to select local transitions within a scope.
```

Example:

```text
autopilot selecting route-following maneuvers
```

### Direct control

```text
The guide or controller directly issues lower-level commands to actuators.
```

Example:

```text
trajectory controller commanding motor targets
```

The same abstract target may move through all three modes at different layers.

Therefore every commitment should declare its authority semantics.

---

## 26. Guidance and Control Differ by Responsibility Boundary

A controller typically stabilizes behavior within a relatively local dynamical regime.

A navigator typically selects which local regime or subgoal should be active relative to a longer-horizon target.

A planner constructs or evaluates extended composition structure.

A resolver binds abstract requirements to currently available implementations and references.

A preflight checker estimates realizability before commitment.

The distinction can be summarized as:

```text
planner
:
Which route or composition could reach the goal?
```

```text
resolver
:
Which operators, providers, and references make that route concrete now?
```

```text
navigator
:
Which locally executable commitment should be active next?
```

```text
controller
:
Which low-level corrections maintain the active local transition?
```

```text
executor
:
Which realized mechanisms actually produce the transition?
```

These roles may be nested and recursively repeated.

---

## 27. A Navigator Is a State-Dependent Resolver Over Time

Let:

```text
M_t = current capability and environment model
hat c_t = estimated configured state
g = retained target
Theta = risk, quality, and authority constraints
```

A navigator computes:

\[
\operatorname{Next}
(M_t,\hat c_t,g,\Theta)
=
\gamma_t
\]

where \(\gamma_t\) is a guidance commitment.

After the commitment is discharged or invalidated:

\[
\operatorname{Next}
(M_{t+1},\hat c_{t+1},g,\Theta)
=
\gamma_{t+1}
\]

Thus the navigator is not only a route generator.

It is a repeated state-dependent resolver operating under a persistent target.

---

## 28. The Persistent Goal and the Ephemeral Commitment

The global goal may remain stable:

```text
reach Munich
```

while local commitments change:

```text
continue south
```

```text
take exit 76
```

```text
reroute through B2
```

```text
stop and recharge
```

```text
resume route
```

This yields the distinction:

```text
persistent goal
=
long-horizon target condition
```

```text
ephemeral guidance commitment
=
currently endorsed local transition
```

The local commitment may be revoked without abandoning the global goal.

This is one reason closed-loop guidance is more robust than open-loop instruction sequences.

---

## 29. Completion Conditions Are Part of the Instruction

An instruction is incomplete if the executor cannot determine when it has been discharged.

For:

```text
Continue straight.
```

completion might mean:

```text
until the next intersection
until the route segment ends
until a new commitment is issued
until a landmark is reached
until a timeout expires
```

For:

```text
Install the dependency.
```

completion might mean:

```text
store object exists
package is present in the selected environment
service starts successfully
interface probe succeeds
tests pass
```

Therefore a guidance commitment should include an observation contract:

\[
O_\gamma
=
(O^{start},O^{progress},O^{success},O^{failure},O^{invalid})
\]

Guidance without completion semantics creates ambiguity at the responsibility boundary.

---

## 30. Guidance Must Be Revisable

A commitment may become invalid because:

```text
the executor deviated
the environment changed
the selected provider disappeared
a road closed
credentials expired
battery fell below threshold
the executor rejected the instruction
the target changed
the state estimate became unreliable
```

A commitment should therefore declare:

```text
validity region
expiration condition
observation freshness requirement
replanning trigger
safe cancellation point
fallback behavior
```

The guide should not continue to defend an outdated commitment merely because it was previously issued.

Thus:

> Commitment means explicit provisional selection, not resistance to revision.

---

## 31. Guidance Must Preserve Future Capability

A locally executable transition may still be strategically harmful.

It may:

```text
consume indispensable energy
enter a dead end
cross an irreversible boundary
lose communication
invalidate credentials
destroy rollback state
move outside the observable region
```

Let:

\[
\mathcal C_t
=
\operatorname{Cap}(A,c_t,H,\Theta)
\]

After commitment \(\gamma_t\) is realized:

\[
c_t
\xrightarrow{\gamma_t}
c_{t+1}
\]

and:

\[
\mathcal C_{t+1}
=
\operatorname{Cap}(A,c_{t+1},H,\Theta)
\]

A navigator should evaluate not only immediate progress but also future capability effects.

A guidance commitment should normally satisfy:

\[
\operatorname{ExpectedProgress}(\gamma_t,g)
\]

and:

\[
\operatorname{PreservesRequiredFutureCapability}(\gamma_t,g,H)
\]

unless an explicit trade-off authorizes otherwise.

---

## 32. Guidance at Commitment Boundaries

Some local transitions are easily reversible.

Others create substantial external effects.

Examples include:

```text
inspect package graph
```

```text
build in an isolated store
```

```text
preview route
```

```text
query current pose
```

compared with:

```text
publish message externally
```

```text
charge payment
```

```text
cross into dangerous traffic
```

```text
delete data
```

```text
move a robot near a person
```

A navigator should strengthen assurance near a commitment boundary.

The guidance may change from:

```text
continue automatically
```

to:

```text
slow down
request confirmation
increase observation frequency
require stronger localization
reserve resources
verify authority
```

Guidance granularity and assurance should therefore be risk-sensitive.

---

## 33. Human Executors Require Interpretable Guidance

A human-oriented navigator must account for capabilities such as:

```text
attention
reaction time
language comprehension
landmark recognition
working memory
visual and auditory perception
fatigue
motor coordination
```

The instruction:

```text
Turn left after the pharmacy.
```

may be more executable than:

```text
At coordinate 48.1374, 11.5755, transition to edge 1842.
```

although both refer to a similar route event.

Human guidance is therefore not merely a compressed machine route.

It is a translation into a human-compatible local invocation language.

This explains why navigation guidance is often organized around:

```text
visible landmarks
named roads
relative timing
turn categories
lane cues
expected duration
```

The guide must resolve the route into distinctions the executor can perceive and act upon.

---

## 34. Machine Executors Also Have Bounded Interfaces

A machine executor is not infinitely detailed or context-free.

It may require:

```text
typed messages
bounded command frequency
coordinate-frame agreement
timestamp synchronization
resource reservations
safety envelopes
controller-compatible trajectories
```

A mission planner should not send raw motor voltages unless that is the declared responsibility boundary.

A local planner should not send a vague mission statement to a motor controller.

Each layer requires a guidance commitment expressed in its local executable language.

Thus:

> Guidance is always relative to the receiving layer's invocation vocabulary, state model, timing, and verification capability.

---

## 35. Nested Guidance Commitments

A commitment at one level may be resolved into commitments at lower levels.

For example:

```text
Reach Munich.
```

may resolve to:

```text
Drive to the central station.
```

which resolves to:

```text
Take exit 76.
```

which resolves to:

```text
move into the right lane
```

which resolves to:

```text
track lateral trajectory q(t)
```

which resolves to:

```text
apply steering and velocity commands
```

The hierarchy is:

```text
global goal
->
mission commitment
->
route commitment
->
maneuver commitment
->
trajectory commitment
->
control commitment
->
actuation
```

Each commitment should stop at the responsibility boundary of the receiving layer.

---

## 36. Guidance Promotion and Skill Formation

A repeatedly successful sequence of commitments may be stabilized into a higher-level skill.

For example:

```text
check mirror
signal
change lane
stabilize position
```

may be promoted into:

```text
ChangeLane(target_lane)
```

The promoted skill becomes a locally invocable operator for the level above.

Thus:

\[
\gamma_1
\circ
\gamma_2
\circ
\cdots
\circ
\gamma_n
\rightsquigarrow
s
\]

where \(s\) is a maintained skill contract.

Promotion reduces guidance bandwidth and transfers resolution depth into the executor.

This gives one operational interpretation of autonomy:

> A more autonomous executor can accept commitments at a higher level because it internally resolves more of the goal-to-control hierarchy.

---

## 37. Guidance Failure Modes

A guided realization can fail in several distinct ways.

### Resolution failure

```text
no suitable next commitment can be constructed
```

### Reference failure

```text
the instruction refers to an unresolved road, object, service, or landmark
```

### Interpretation failure

```text
the executor cannot understand the commitment
```

### Applicability failure

```text
the commitment was valid for a different state
```

### Execution failure

```text
the executor attempted the transition but did not realize the expected effect
```

### Observation failure

```text
the system cannot determine what occurred
```

### Verification failure

```text
an observation exists but does not establish completion
```

### Coordination failure

```text
guide and executor disagree about the active commitment or version
```

### Model failure

```text
the represented map, capability graph, or transition model is incorrect
```

These failures should not be collapsed into one generic action failure.

---

## 38. Synchronization and Commitment Identity

Because guidance is revised over time, the executor and navigator must agree on which commitment is active.

Each commitment should carry:

```text
identity
version
issue time
validity interval
supersedes relation
linked global goal
linked predecessor commitment
```

An executor report should reference the commitment it concerns.

This prevents errors such as:

```text
executing an expired turn instruction
reporting completion for the wrong route version
continuing after cancellation
combining observations from incompatible frames
```

The protocol therefore needs referential continuity, not merely message delivery.

---

## 39. Shared State Is Never Perfectly Shared

The phrase `shared state` may suggest that guide and executor possess one identical state object.

In distributed realization, each participant normally has a local representation.

Let:

```text
k_N = navigator knowledge state
k_A = executor knowledge state
x = actual relevant world state
```

In general:

\[
k_N
\not\equiv
k_A
\not\equiv
x
\]

Coordination depends on sufficiently aligned representations for the current purpose.

The system should therefore expose:

```text
state source
timestamp
frame
uncertainty
version
assumptions
```

The goal is not metaphysical identity of representations.

It is operationally adequate synchronization.

---

## 40. Guidance as a Contract Between Belief and Action

A guidance commitment links two different domains.

On the navigator side:

```text
belief
prediction
route evaluation
risk estimate
```

On the executor side:

```text
interpretation
local decision
physical or symbolic realization
```

The commitment acts as a contract between represented expectation and attempted action.

It should make explicit:

```text
what the guide currently believes
what action is being endorsed
what evidence would count as progress
what evidence would invalidate the endorsement
```

This is why guidance is richer than a bare command and more prescriptive than feedback.

---

## 41. Guidance Is a Jointly Realized Dialogue

The guide does not merely emit messages into a passive client.

The executor contributes:

```text
state reports
acceptance or refusal
execution traces
local discoveries
failure information
new constraints
```

The guide contributes:

```text
route structure
next-step selection
contextual interpretation
replanning
expected completion conditions
```

The trajectory emerges from repeated interaction.

Thus:

```text
guide speaks
executor acts
guide observes
executor reports
guide revises
```

This is a structured dialogue over realization.

The coupling becomes convoluted only when the protocol fails to distinguish the semantic roles of its messages.

---

## 42. Relation to a Capability Mirror

A capability mirror may maintain an evolving approximation of the executor's current organization.

The navigator can use that mirror to answer:

```text
Which modes are available?
Which operators are currently executable?
Which instructions are interpretable?
Which resources remain?
Which observations are fresh?
Which previous commitments succeeded or failed?
```

After every commitment:

\[
M_{t+1}
=
U(M_t,\gamma_t,o_{t+1},\eta_t)
\]

where:

```text
M_t = current mirror
Gamma_t = issued commitment
O_{t+1} = observation
Eta_t = realized or attempted trace
```

Unexpected success may reveal hidden capability.

Unexpected failure may reveal missing preconditions, stale state, or incorrect provider claims.

The guidance loop therefore also becomes a model-revision loop.

---

## 43. Relation to Preflight Realizability

Preflight checking and navigation are complementary.

Before issuing a commitment, the system may ask:

```text
Is the selected transition currently realizable?
```

The answer may include:

```text
provider availability
resource sufficiency
authority
risk
observability
reversibility
confidence
```

After execution, observation updates the model.

The combined loop is:

```text
resolve candidate
->
preflight candidate
->
issue guidance commitment
->
execute
->
observe
->
verify
->
revise model
->
resolve again
```

This combines the structural discipline of configuration checking with the temporal discipline of closed-loop navigation.

---

## 44. Relation to Nix-Like Structural Realization

A Nix-like system provides a strong model for evaluating whether a particular requested software realization follows from a declared configuration and dependency structure.

The reusable structural lesson is:

```text
requested output
+
explicit configuration
+
resolved dependencies
+
known realization rules
->
realization attempt or valid existing realization
```

A capability navigator generalizes the pattern temporally:

```text
persistent target
+
current estimated configuration
+
resolved executable structure
+
observed outcomes
->
next bounded realization attempt
```

The first emphasizes reproducible structural realization.

The second emphasizes repeated state-indexed transition selection under changing conditions.

The shared core is that configuration participates in the transition judgment.

The difference is that navigation repeatedly re-evaluates the judgment as the world and executor change.

---

## 45. Minimal Formal Model

Let:

```text
A = executor
N = navigator
W = world
M_t = navigator model
c_t = actual configured state
hat c_t = estimated configured state
g = persistent goal
Theta = constraints and tolerances
Gamma_t = active guidance commitment
```

The guide-selection relation is:

\[
N(M_t,\hat c_t,g,\Theta)
\Downarrow
\gamma_t
\]

The executor relation is:

\[
(A,c_t)
\xRightarrow{\gamma_t}
\eta_t
\]

The world and executor reach:

\[
c_t
\xrightarrow{\eta_t}
c_{t+1}
\]

The observation relation is:

\[
O(c_{t+1},\eta_t)
\Downarrow
o_{t+1}
\]

The update relation is:

\[
(M_{t+1},\hat c_{t+1})
=
U(M_t,\hat c_t,\gamma_t,o_{t+1})
\]

The cycle continues until:

\[
c_t\models g
\]

or until the system concludes that the target is:

```text
unreachable under current conditions
unsafe
unauthorized
abandoned
insufficiently observable
```

---

## 46. Guidance Correctness

A guidance commitment can be evaluated along several dimensions.

### Local validity

\[
P_\gamma(\hat c_t)
\]

The represented entry conditions hold.

### Executability

\[
\operatorname{Executable}(A,\gamma,\hat c_t)
\]

The executor appears able to discharge the commitment.

### Interpretability

\[
\operatorname{Interpretable}(A,\gamma,\hat c_t)
\]

The executor can bind and understand the instruction.

### Expected progress

\[
\mathbb E[d(c_{t+1},G)]
<
d(c_t,G)
\]

under an appropriate target-distance or viability measure.

### Observability

\[
\operatorname{ObservableCompletion}(O,\gamma)
\]

The outcome can be sufficiently determined.

### Revision safety

\[
\operatorname{RecoverableOnInvalidation}(\gamma)
\]

The system has an acceptable response when the commitment becomes invalid.

No single scalar necessarily captures all dimensions.

---

## 47. Assurance Levels for Guidance

A guidance system may distinguish assurance states such as:

```text
structurally admissible
```

```text
provider-resolved
```

```text
state-compatible
```

```text
observationally supported
```

```text
resource-reserved
```

```text
executor-acknowledged
```

```text
actively monitored
```

```text
completion-verified
```

A low-risk advisory instruction may require only weak assurance.

An irreversible or safety-critical commitment may require stronger evidence, reservation, authority, and monitoring.

---

## 48. Suggested ROS 2 Decomposition

A prototype could separate the following nodes or components.

### Goal manager

Maintains the persistent target, constraints, and cancellation state.

### Capability resolver

Determines which operator families and providers appear available.

### State estimator

Maintains the current estimated executor-world configuration and uncertainty.

### Navigator

Selects the next guidance commitment.

### Commitment manager

Versions, publishes, expires, supersedes, and records commitments.

### Executor adapter

Translates a commitment into the executor's local interface.

### Observation collector

Receives state, progress, and failure evidence.

### Verifier

Determines whether local and global completion conditions are met.

### Model updater

Revises capability, reliability, and environment claims from discrepancy.

The decomposition may be implemented through topics, services, actions, lifecycle nodes, and behavior-tree or planning components.

The conceptual boundaries matter more than one fixed ROS graph.

---

## 49. Suggested Interface Sketch

Conceptually:

```text
/guidance/goal
```

carries:

```text
global target
constraints
priority
horizon
authority
```

```text
/guidance/state_report
```

carries:

```text
estimated or observed state
frame
timestamp
uncertainty
active commitment
```

```text
/guidance/commitment
```

carries:

```text
next operator
arguments
applicability
completion contract
validity
replanning rules
```

```text
/guidance/acknowledgment
```

carries:

```text
accepted
rejected
unresolved
inapplicable
```

```text
/guidance/outcome
```

carries:

```text
started
progress
completed
failed
deviated
cancelled
```

An action interface may wrap the global lifecycle while topics or subordinate actions carry state and commitments.

---

## 50. Prototype Scope

A minimal prototype should avoid beginning with unrestricted natural-language goals or arbitrary human capability modeling.

A useful first domain could be:

```text
mobile robot
+
small mapped environment
+
limited operator vocabulary
+
explicit localization uncertainty
+
structured guidance commitments
```

Possible operators:

```text
ProceedToRegion(region)
TurnAtJunction(junction, direction)
Wait(duration)
RequestHumanClearance(area)
Dock(charger)
Stop(reason)
```

The prototype should demonstrate:

```text
persistent target
state-indexed commitment generation
commitment versioning
executor acknowledgment
completion observation
deviation detection
replanning
model update after discrepancy
```

A second prototype could apply the same protocol to software deployment:

```text
resolve dependency
build artifact
activate environment
start service
verify endpoint
rollback on failed verification
```

The common architecture should remain visible despite the different frames of relevance.

---

## 51. Central Principles

### Principle 1: All practical realization is physically instantiated

Task-level non-spatial descriptions do not remove lower-level physical transition.

### Principle 2: Motion is frame-indexed

The same system may be stationary relative to one frame and moving relative to another.

### Principle 3: Locomotion is one transition family

It should not be used as the universal unit of guidance.

### Principle 4: Configuration is an argument of transition

An operator instance is evaluated relative to the current configured state and environment.

### Principle 5: Guidance granularity is decision-relative

The next useful unit depends on decision boundaries, uncertainty, mode, risk, and executor capacity.

### Principle 6: A guidance commitment is a bounded transition endorsement

It identifies a locally executable operator, expected effect, validity conditions, and revision rules.

### Principle 7: Feedback and guidance are semantically distinct

Feedback describes progress; guidance prescribes the next endorsed transition.

### Principle 8: The navigator maintains a belief state

Its representation of the executor is approximate, time-indexed, and evidence-dependent.

### Principle 9: Coupling creates extended capability

Navigator, executor, observer, infrastructure, and world jointly realize trajectories that no isolated component realizes alone.

### Principle 10: Coupling should preserve responsibility boundaries

Goal ownership, state estimation, selection, execution, observation, and verification should remain explicit.

### Principle 11: ROS Actions provide a useful lifecycle pattern

Goals, feedback, cancellation, and results support long-running realization, but guidance may require additional prescriptive and bidirectional semantics.

### Principle 12: Persistent goals coexist with ephemeral commitments

The global target may remain stable while local recommendations are repeatedly revised.

### Principle 13: Completion conditions are part of guidance

An executor must know what discharges, invalidates, or expires the current commitment.

### Principle 14: Local progress must preserve global viability

A locally executable action may still be rejected if it destroys required future capability.

### Principle 15: Guidance is hierarchical

Each layer resolves its target into a commitment appropriate to the next layer's interface and horizon.

### Principle 16: Repeated guidance can be promoted into skill

Stable local resolution can be internalized by the executor and exposed as a higher-level operator.

### Principle 17: Guided execution is also model revision

Observed success, failure, deviation, and uncertainty update the capability and environment model.

### Principle 18: Preflight and navigation are complementary

Preflight checks one candidate transition; navigation repeatedly selects and checks candidates over time.

---

## 52. Central Claim

A global target does not contain its route.

A route does not contain every control transition.

A control transition does not contain its own realization.

A movement is not absolute but frame-indexed.

A task-relevant transition is a projection of a larger physical realization.

A navigator does not possess the executor's actual state.

It maintains a revisable estimate.

An executor does not need the entire trajectory at once.

It needs a locally interpretable and executable commitment.

Feedback alone does not select the next action.

Guidance does.

Guidance alone does not change the world.

Execution does.

Execution alone does not establish known success.

Observation and verification do.

Therefore:

> Practical navigation is a coupled process in which a persistent target is repeatedly resolved against an evolving state estimate into bounded guidance commitments; those commitments are interpreted and exercised by an executor, observed through a fallible evidence system, and completed, cancelled, or revised as the joint realization unfolds.

The general unit is not locomotion, distance, time, or intersection count.

It is a state-indexed, frame-declared, locally executable and verifiable transition commitment at the current responsibility boundary.

---

## 53. Conclusion

Google Maps is useful as an architectural model because it combines:

```text
a retained destination
a maintained map
a model of the executor's position
a selected mode of movement
a route through persistent infrastructure
bounded local instructions
progress observation
deviation detection
replanning
arrival verification
```

Its guidance is designed for human executors who can walk, drive, cycle, board transport, interpret landmarks, and locally control vehicles or bodies.

But the underlying structure is not restricted to locomotion.

The same organization can guide:

```text
software deployment
robot manipulation
institutional procedure
laboratory work
human-machine collaboration
resource acquisition
permission resolution
recovery from failure
```

The relevant transition differs by frame of relevance.

The coupling remains:

```text
target
+
state estimate
+
executable capability structure
+
next guidance commitment
+
executor
+
observation
+
revision
```

ROS Actions resemble this architecture because they already model temporally extended goals with feedback, cancellation, and results.

The additional insight is that some action-like servers do not directly own the requested world transition.

They participate as navigators in a coupled system, repeatedly prescribing the next local commitment to another executor whose changing state they only approximately observe.

The architecture is therefore neither a simple RPC nor an undifferentiated controller.

It is a structured dialogue between resolution and realization.
