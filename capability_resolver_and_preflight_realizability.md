# Capability Resolver and Preflight Realizability

## Abstract

A command, instruction, function call, ROS action, deployment request, or high-level intention does not guarantee realization.

The expression:

```text
run_demo
```

may be syntactically valid and still fail because:

```text
the name is unresolved
the required capability is absent
a dependency is unavailable
a version is incompatible
a permission is missing
the environment is unsafe
the invocation is ambiguous
the estimated transition is irreversible
the actual implementation does not satisfy its declared interface
```

This document proposes a **capability resolver**: an interface-oriented organization that predicts whether an invocation is currently realizable before forcing execution.

The resolver does not contain every implementation.

It maintains metadata about:

```text
capabilities
interfaces
versions
requirements
conflicts
conditions
resources
authority
risk
observations
confidence
verification history
replacement relations
```

Its role resembles a package manager, linker, build system, launch planner, static analyzer, and preflight checker operating across software, hardware, people, tools, permissions, and environments.

Where a package resolver asks:

> Can this package configuration be installed?

A capability resolver asks:

> Can this invocation become a satisfactory realization under the current organization?

The resolver computes a dependency closure, checks available providers, evaluates constraints, identifies missing relations, estimates risky or irreversible steps, and produces a realizability report before execution.

Execution remains outside the resolver.

ROS 2 is a suitable middle layer because it already supplies addressable processes, topics, services, actions, lifecycle management, controllers, tooling, and runtime observations. The capability resolver can sit above and across these mechanisms without replacing them.

The result is not an omniscient planner.

It is a maintained approximation that can answer:

```text
what appears realizable now
why it appears realizable
what is missing
which assumptions remain unverified
which repairs are reversible
which steps should not yet be attempted
how observed outcomes revise the model
```

---

## 1. Starting Point

Consider:

```text
Do it.
```

or:

```python
do_it()
```

Neither expression guarantees:

```text
compilation
interpretation
resolution
execution
communication
coordination
physical change
successful completion
intended outcome
```

The expression is an invocation candidate.

Its realization depends on a current organization containing some combination of:

```text
language competence
namespace
interpreter
libraries
running processes
hardware
permissions
tools
memory
social context
environment
available time
energy
safety conditions
```

The relevant structure is:

```text
invocation
+
current capability organization
+
current context
+
accepted risk
->
possible realization
```

The arrow is conditional.

---

## 2. The Realizability Question

The resolver is organized around one operational question:

> Given this invocation and the current represented organization, what prevents or supports realization?

Let:

```text
i = invocation
M = current capability model
c = current context
Theta = accepted conditions and tolerances
H = relevant horizon
```

Then the resolver estimates:

\[
\operatorname{Realizable}(i,M,c,\Theta,H)
\]

The result should not be only:

```text
true
false
```

It should include:

```text
resolved target
candidate providers
satisfied requirements
missing requirements
conflicts
unknown conditions
estimated risk
reversible preparation steps
irreversible steps
confidence
evidence
```

A useful answer is therefore a structured report rather than a binary verdict.

---

## 3. Repository of Realizability

The capability resolver may be understood as a repository over other relevant repositories, deployments, devices, people, services, and environments.

It does not duplicate their implementations.

It records only what is needed to reason about realizability.

For a software package, this may include:

```text
name
version
provided interfaces
required interfaces
platform constraints
conflicts
health status
location
```

For a ROS node:

```text
node identity
provided topics
required topics
provided services
required actions
lifecycle state
QoS requirements
message versions
last heartbeat
```

For a tool:

```text
tool identity
location
availability
operator requirements
safety constraints
calibration status
```

For a human capability:

```text
claimed capability
conditions
support requirements
last observed evidence
confidence
fatigue or attention limits
authority
```

For an environment:

```text
location
connectivity
power
lighting
space
weather
access restrictions
hazards
```

The repository stores organizational relations, not complete essences.

---

## 4. Capability Manifests

The basic unit is a **Capability Manifest**.

A manifest declares what a provider claims to make possible and under which conditions.

Conceptually:

```yaml
capability:
  id: run_robot_demo
  version: 1.2

provides:
  - demo.completed

requires:
  - ros.graph.available
  - workspace.built
  - robot.reachable
  - camera.stream
  - operator.authorized

optional:
  - speech.output
  - audience.display

conflicts:
  - robot.estop.engaged
  - maintenance.lock.active

resources:
  battery_minimum: 30%
  disk_free_minimum: 5GB
  expected_duration: 12m

risk:
  reversibility: mostly_reversible
  physical_motion: true
  external_side_effects: false

verification:
  last_success: 2026-07-12
  confidence: 0.86
```

The manifest does not contain the implementation of the demo.

It describes enough of the interface and conditions to support preflight reasoning.

---

## 5. Providers and Requirements

A capability may be provided by multiple organizations.

For example:

```text
camera.stream
```

may be provided by:

```text
physical USB camera
network camera
recorded ROS bag
simulation camera
remote operator stream
```

The resolver should not bind a requirement to one implementation too early.

Instead:

```text
requirement
->
provider candidates
->
constraint filtering
->
selected provider set
```

A provider relation may include:

```text
interface compatibility
version compatibility
latency
quality
cost
trust
location
energy
availability
risk
```

This supports substitution.

A physical camera can be replaced by simulation when the observational criterion permits it.

---

## 6. The Capability Dependency Closure

A high-level invocation usually expands into a graph.

For example:

```text
prepare_robot_demo
```

may require:

```text
run_robot_demo
check_room
charge_robot
load_demo_assets
verify_operator
```

Each required capability may introduce further requirements.

The resolver computes a closure:

\[
C^*(i)
=
\operatorname{Closure}(i, M, c)
\]

The closure contains the candidate set of:

```text
capabilities
providers
resources
permissions
contexts
preconditions
```

needed for realization.

This resembles package dependency resolution.

The difference is that capability dependencies may be:

```text
dynamic
uncertain
conditional
social
physical
time-bounded
partially observable
```

---

## 7. Static Hints Before Execution

The first value of the resolver is not autonomous execution.

It is early rejection of obviously unsupported invocations.

Examples:

```text
Invocation:
Run the robot demo.

Static finding:
No provider for robot.reachable.

Recommendation:
Do not launch motion processes.
```

```text
Invocation:
Deploy production.

Static finding:
Credentials are absent and the target schema version is incompatible.

Recommendation:
Do not begin migration.
```

```text
Invocation:
Submit the document.

Static finding:
Final artifact exists, but the deadline status is unknown and submission is irreversible.

Recommendation:
Resolve deadline and obtain explicit confirmation before submission.
```

These are valuable even when the model is incomplete.

A partial static hint can prevent costly failure.

---

## 8. Preflight Simulation

After static checks, the resolver may construct an attempted simulation.

The simulation is not necessarily a full physical or cognitive simulation.

It may be a dry run over declared interfaces and constraints.

```text
resolve invocation
->
expand requirements
->
select providers
->
check versions
->
check current availability
->
estimate resource use
->
identify side effects
->
order reversible preparation
->
identify commitment boundary
```

The purpose is to answer:

```text
What would have to happen?
Which steps appear safe to inspect?
Which steps would make real changes?
Where is recovery uncertain?
Which assumptions remain untested?
```

The simulation can stop before crossing an irreversible boundary.

---

## 9. Reversibility and Commitment Boundaries

Not all transitions should be treated equally.

Examples of relatively reversible actions include:

```text
read configuration
inspect ROS graph
query battery state
validate credentials
build in an isolated workspace
run simulation
open a preview
```

Examples of potentially irreversible actions include:

```text
send a message
submit a form
move physical hardware near people
delete data
publish externally
charge a credit card
flash firmware
migrate a production database
```

A capability manifest should declare side-effect classes.

Conceptually:

```yaml
side_effects:
  filesystem_write: reversible
  network_publish: externally_visible
  physical_motion: supervised
  payment: irreversible
```

The resolver should compute a **commitment boundary**:

```text
safe inspection
->
reversible preparation
->
validated plan
->
commitment boundary
->
real execution
```

The resolver may proceed automatically before the boundary while requiring stronger evidence or authority after it.

---

## 10. Approximate Layers

A high-level request is usually more permissive than a low-level controller command.

For example:

```text
"Bring me the red cup."
```

permits many realizations.

A lower layer may represent:

```text
object candidate: cup_17
estimated pose: (x, y, z)
selected grasp: grasp_4
trajectory: q(t)
controller target: joint positions
actuator output: torque commands
```

Each layer reduces some uncertainty while introducing its own assumptions.

A useful organization is:

```text
intention
->
linguistic invocation
->
resolved task schema
->
capability dependency graph
->
selected providers
->
behavior or task plan
->
motion plan
->
control targets
->
actuation
->
physical transition
```

No layer guarantees the next.

Each layer provides a more constrained candidate realization.

---

## 11. Python and Natural Language

Python and natural language differ substantially.

Yet both can serve as permissive invocation languages.

Consider:

```python
foo(bar)
```

Its realization depends on:

```text
active namespace
binding of foo
value and type of bar
runtime
libraries
process state
external services
```

Consider:

```text
Do it.
```

Its realization depends on:

```text
referent
listener
shared history
authority
available capability
environment
```

Both expressions may be:

```text
well-formed but unresolved
resolved but unsupported
supported but refused
executed but ineffective
effective but contrary to intention
```

The capability resolver does not need to claim that natural language and Python are identical.

It only needs to exploit their shared operational property:

> A permissive symbolic invocation requires an organized resolver before it can become a transition.

---

## 12. ROS as a Middle Layer

ROS 2 already supplies many mechanisms needed by a capability resolver.

These include:

```text
nodes
topics
services
actions
parameters
lifecycle states
launch descriptions
message definitions
QoS policies
logging
introspection
rosbag recording
controllers
navigation
manipulation
simulation integration
```

ROS is useful because it separates:

```text
addressability
communication
coordination
execution
```

A high-level capability resolver can use ROS without forcing ROS to become the entire reasoning system.

The resolver may ask:

```text
Which nodes are alive?
Which interfaces are available?
Which actions are currently accepted?
Which lifecycle states are active?
Which heartbeats are stale?
Which controller resources are claimed?
Which dependencies are only declared but not observed?
```

ROS supplies current operational evidence.

The resolver supplies cross-domain realizability structure.

---

## 13. Heartbeats and Freshness

A capability claim becomes weaker when its evidence becomes stale.

A ROS node that was available yesterday may not be available now.

A person who performed a task last month may be unable to perform it under current conditions.

A credential may have expired.

A tool may have moved.

Therefore every claim should carry freshness information.

```yaml
observation:
  subject: camera.stream
  status: available
  observed_at: 2026-07-19T10:42:00+02:00
  source: ros_graph_observer
  confidence: 0.99
  expires_after: 5s
```

The resolver should distinguish:

```text
declared
observed
verified
historically successful
currently fresh
```

These are not equivalent.

---

## 14. Interface-Only Reuse

The resolver should reuse existing systems through their interfaces and metadata.

It does not need to absorb their implementations.

Examples include:

```text
package manifests
ROS interface definitions
OpenAPI schemas
container metadata
systemd units
Kubernetes resource descriptions
hardware descriptors
udev information
CI results
SBOMs
service health endpoints
calendar availability
identity and permission systems
```

For each source, the resolver extracts only what supports realizability reasoning.

This makes the resolver a **meta-organization** across heterogeneous capability providers.

It is not a universal replacement for them.

---

## 15. Existing Resolver Patterns

Many existing systems already solve restricted versions of this problem.

### Package managers

```text
resolve versions
check dependencies
identify conflicts
compute installation plan
```

### Linkers

```text
resolve symbols
bind references to implementations
reject missing or incompatible definitions
```

### Build systems

```text
construct dependency graphs
avoid unnecessary work
fail before deployment
```

### Schedulers

```text
match workloads to resources
respect constraints
reserve capacity
```

### Launch systems

```text
start processes in an order
supply configuration
monitor health
```

### Static analyzers

```text
infer possible faults without executing the full program
```

### Type systems

```text
reject some invalid compositions before runtime
```

### Safety interlocks

```text
prevent transitions when declared physical conditions are not satisfied
```

The capability resolver composes these patterns across a broader domain.

---

## 16. What Can Be Reused Directly

A first implementation can reuse substantial existing infrastructure.

### ROS 2

```text
interface transport
runtime discovery
actions
services
topics
lifecycle
logging
recording
controllers
```

### Package metadata

```text
package.xml
Python package metadata
system packages
container manifests
lock files
```

### Planning representations

```text
behavior trees
task graphs
state machines
PDDL-like preconditions and effects
```

### Perception outputs

```text
object detections
segmentation
pose estimates
speech recognition
identity recognition
scene graphs
```

### Monitoring

```text
heartbeats
health checks
metrics
traces
resource monitors
```

### Simulation

```text
Gazebo
MuJoCo
Isaac Sim
Webots
mock providers
dry-run adapters
```

### Policy and authority

```text
access-control lists
roles
capability tokens
approval workflows
```

The resolver should initially integrate these rather than reimplement them.

---

## 17. What Is Still Missing

The primary gap is not the absence of all component technology.

The gap is the absence of a maintained cross-domain representation connecting them.

Commonly missing elements include:

```text
one capability manifest format spanning software, hardware, humans, and environment
current dependency closure across those domains
explicit distinction between declared and observed capability
confidence and freshness attached to capability claims
reversibility metadata
commitment boundaries
revision after unexpected success or failure
branching alternative self-models
explanations of the smallest blocking dependency set
```

Existing systems often know pieces of this.

They usually do not maintain one revisable graph of current realizability.

---

## 18. Images, Recognition, and High-Level Concepts

Images and recognition outputs fit into the same organization as evidence-producing capabilities.

For example:

```text
Invocation:
Find the red cup.
```

may require:

```text
camera.stream
image.decode
object.detect
color.classify
spatial.localize
referent.resolve
```

The result is not simply:

```text
cup found
```

It should carry:

```text
candidate identity
confidence
observation time
location estimate
provider chain
known ambiguities
```

A recognition capability manifest may declare:

```yaml
capability:
  id: object.detect
  version: 3.0

requires:
  - image.rgb

provides:
  - object.candidates

conditions:
  lighting: sufficient
  occlusion: limited

quality:
  confidence_calibrated: partially
  supported_classes:
    - cup
    - bottle
    - tool
```

The capability resolver does not perform recognition unless it also hosts the implementation.

It decides whether a recognition provider appears suitable and how its uncertainty propagates upward.

---

## 19. Recognition Is Not Resolution

Recognizing an object is not the same as resolving an invocation.

For example:

```text
"Bring me my mug."
```

may require:

```text
detect mug-shaped objects
identify ownership or habitual use
resolve speaker reference
check whether transport is permitted
verify graspability
plan movement
```

A vision system may detect three mugs.

The invocation remains unresolved.

Therefore the resolver should separate:

```text
perceptual evidence
semantic candidate
referent resolution
capability feasibility
execution plan
```

This prevents a confident detector from being mistaken for a complete task interpretation.

---

## 20. Minimal Blocking Sets

A useful resolver should identify the smallest set of unsatisfied relations that blocks realization.

For example:

```text
Invocation:
Run the demo.

Blocking set A:
- robot.reachable

Blocking set B:
- simulator.available
- simulation_assets.installed
```

The invocation may become realizable by satisfying either set.

This is more useful than listing every dependency in the full graph.

Formally, the resolver may seek minimal sets:

\[
B_1, B_2, \ldots, B_n
\]

such that satisfying one admissible set enables a complete provider assignment.

This resembles diagnosis, SAT solving, dependency repair, and fault-tree analysis.

---

## 21. Repair Planning

After identifying blockers, the resolver may propose repair actions.

Repairs should themselves be capabilities with dependencies and risks.

Example:

```text
Missing:
robot.reachable
```

Candidate repairs:

```text
power_on_robot
connect_network
switch_to_simulator
request_remote_operator
```

Each repair has different:

```text
cost
risk
time
authority
reversibility
confidence
```

The resolver should not merely say:

```text
missing dependency
```

It should be able to say:

```text
The least risky repair is to start the simulator.
The fastest repair is to reconnect the robot network.
Physical execution still requires operator authorization.
```

---

## 22. Evidence and Confidence

Capability claims should be supported by evidence.

Possible evidence includes:

```text
successful execution
failed execution
health check
interface introspection
user declaration
test result
simulation
historical pattern
external certification
```

A claim should not be treated as equally strong under all evidence sources.

Conceptually:

```yaml
claim:
  capability: robot.navigate
  conditions:
    map: warehouse_a
  confidence: 0.78
  evidence:
    - type: observed_success
      timestamp: 2026-07-18T15:20:00+02:00
    - type: stale_health_check
      timestamp: 2026-07-19T08:00:00+02:00
```

Confidence is not certainty.

It should decrease when:

```text
evidence becomes stale
conditions change
providers change
failures accumulate
conflicting observations appear
```

---

## 23. Failure as Graph Revision

A failed execution is not only a failed task.

It is evidence that the capability model was incomplete, stale, or wrongly resolved.

Suppose:

```text
predicted:
run_demo succeeds
```

but:

```text
observed:
launch fails because GPU memory is exhausted
```

The revision may add:

```text
run_demo
requires
gpu.memory >= 4GB free
```

The next invocation can then fail statically rather than physically.

This is a central growth mechanism:

```text
prediction
->
realization
->
discrepancy
->
new dependency or revised condition
->
better future preflight
```

---

## 24. Unexpected Success

Unexpected success is equally informative.

Suppose the resolver predicts:

```text
object.pick unavailable because depth camera is missing
```

but a human operator successfully provides a pose estimate through a manual interface.

The model may discover a new provider:

```text
human.pose_estimation
provides
object.pose
```

The graph should then record:

```text
supported-action capability
manual fallback
new interface relation
additional authority requirement
```

A capability model should grow through both failure and improvisation.

---

## 25. Branches and Alternative Configurations

The resolver should preserve alternative configurations rather than forcing one global state.

Examples:

```text
physical robot configuration
simulation configuration
remote-operation configuration
low-energy configuration
maintenance configuration
home configuration
work configuration
```

The same invocation may be realizable in one branch and not another.

For example:

```text
run_demo
```

may resolve to:

```text
physical demo
```

or:

```text
simulation demo
```

depending on available providers and accepted criteria.

Branching preserves useful alternatives without pretending they are identical.

---

## 26. Capability Linking

A linker resolves symbolic references to implementations.

A capability resolver performs a similar operation across heterogeneous providers.

```text
required interface
->
matching provider
->
compatible conditions
->
bound realization candidate
```

This suggests the term:

```text
capability linker
```

The linker does not need to understand every implementation internally.

It needs:

```text
stable handles
interface declarations
compatibility rules
provider availability
conflict rules
```

The final linked organization may include:

```text
software service
ROS node
robot controller
human operator
physical tool
permission
environmental condition
```

---

## 27. Capability Type Checking

A type system rejects some invalid compositions before runtime.

A capability resolver can perform analogous checks.

For example:

```text
requires:
object.pose<frame=map>
```

should not be satisfied by:

```text
object.pose<frame=camera>
```

without a transform provider.

Likewise:

```text
requires:
operator.authorization<level=physical_motion>
```

should not be satisfied by:

```text
operator.authorization<level=read_only>
```

Capability types may include:

```text
version
unit
coordinate frame
latency
precision
trust level
authority level
privacy class
risk class
```

This allows useful static rejection before execution.

---

## 28. Capability Negotiation

Some requirements can be weakened or renegotiated.

For example:

```text
Invocation:
Show me the room.
```

Preferred provider:

```text
live high-resolution camera
```

Fallback providers:

```text
low-resolution camera
recent stored image
map reconstruction
human description
```

The resolver should distinguish:

```text
required criterion
preferred criterion
acceptable degradation
unacceptable substitution
```

This enables graceful degradation rather than immediate failure.

---

## 29. Planner and Resolver Are Different

A planner asks:

> Which sequence of actions may reach the goal?

A resolver asks:

> Which required capabilities and conditions currently appear satisfiable?

They interact, but they are not the same.

A planner may propose:

```text
navigate
pick
return
place
```

The resolver may reject the plan because:

```text
gripper unavailable
battery insufficient
navigation map stale
operator permission missing
```

Conversely, the resolver may identify available capabilities without choosing a goal-directed sequence.

A robust architecture should keep both roles explicit.

---

## 30. Simulation and Resolution Are Different

A simulator predicts traces under a model.

A resolver predicts whether the necessary organization can be assembled.

The resolver may call a simulator as one provider of evidence.

For example:

```text
resolver:
all declared dependencies satisfied
```

then:

```text
simulator:
trajectory collides with table
```

The result revises realizability.

Thus:

```text
resolution
+
simulation
+
policy
->
preflight decision
```

No single layer is sufficient.

---

## 31. Proposed ROS 2 Nodes

A minimal ROS 2 implementation may include:

```text
/invocation_gateway
/capability_registry
/provider_observer
/capability_resolver
/preflight_simulator
/risk_guard
/execution_gateway
/outcome_comparator
/history_store
/tamagotchi_state
```

### `/invocation_gateway`

Receives:

```text
natural language
structured commands
ROS actions
scheduled requests
```

Produces candidate invocation schemas.

### `/capability_registry`

Stores manifests, interfaces, versions, conditions, and provider relations.

### `/provider_observer`

Observes current runtime state:

```text
nodes
topics
services
devices
resources
heartbeats
permissions
```

### `/capability_resolver`

Computes dependency closures, provider bindings, conflicts, blockers, and alternatives.

### `/preflight_simulator`

Runs dry checks, mocks, simulations, and resource estimates.

### `/risk_guard`

Identifies commitment boundaries and enforces authority requirements.

### `/execution_gateway`

Invokes external implementations after resolution and authorization.

### `/outcome_comparator`

Compares predicted and observed traces.

### `/history_store`

Preserves evidence, revisions, branches, and superseded claims.

### `/tamagotchi_state`

Exposes compact model-health indicators.

---

## 32. Suggested Messages

### CapabilityManifest

```text
capability_id
version
provides
requires
optional
conflicts
conditions
resources
side_effects
risk
provider_reference
```

### ProviderObservation

```text
provider_id
interfaces
status
observed_at
freshness
confidence
source
```

### InvocationRequest

```text
token
source
intended_target
parameters
context_reference
accepted_risk
authority_reference
```

### ResolutionReport

```text
resolved_target
selected_providers
dependency_closure
satisfied_requirements
missing_requirements
conflicts
unknowns
minimal_blocking_sets
candidate_repairs
confidence
```

### PreflightReport

```text
resolution_reference
simulated_steps
resource_estimates
predicted_side_effects
commitment_boundary
recovery_plan
remaining_uncertainty
```

### ObservedOutcome

```text
invocation_reference
observed_trace
outcome
unexpected_dependencies
unexpected_providers
side_effects
```

### ModelRevision

```text
prior_claim
revised_claim
evidence
reason
confidence_change
```

---

## 33. Basic Resolution Algorithm

A minimal resolver may follow:

```text
1. Parse or accept an invocation schema.
2. Resolve the intended target capability.
3. Expand mandatory and conditional requirements.
4. Query current provider observations.
5. Filter providers by interface, version, condition, authority, and risk.
6. Compute candidate provider assignments.
7. Detect conflicts and cycles.
8. Compute minimal blocking sets.
9. Propose reversible repairs or degradations.
10. Run available preflight simulations.
11. Identify commitment boundaries.
12. Return a report without executing.
```

Only after a separate authorization step should the execution gateway be invoked.

---

## 34. Example: Robot Demonstration

Invocation:

```text
Prepare and run the robot demonstration.
```

Resolved capability:

```text
robot_demo.completed
```

Dependency closure:

```text
workspace.built
robot.reachable
robot.safe
camera.stream
navigation.available
demo.assets
operator.authorized
audience.area.clear
```

Observed state:

```text
workspace.built: yes
robot.reachable: no
simulator.available: yes
camera.stream: yes
operator.authorized: yes
audience.area.clear: unknown
```

Resolver report:

```text
Physical demo:
not currently realizable

Blocking set:
- robot.reachable
- audience.area.clear

Simulation demo:
realizable with confidence 0.91

Suggested preparation:
- start simulator
- validate demo assets
- request room-clear observation

Commitment boundary:
physical motor activation
```

No motor command needs to be issued to produce this report.

---

## 35. Example: High-Level Image Request

Invocation:

```text
Find the image where the red robot is holding a cup.
```

Candidate capability graph:

```text
image.collection.access
image.decode
object.detect<robot>
object.detect<cup>
color.classify<red>
relation.recognize<holding>
result.rank
```

Possible blockers:

```text
collection unavailable
image format unsupported
relation model absent
privacy restriction
insufficient confidence
```

The resolver may determine:

```text
object detection is available
color classification is available
holding-relation recognition has no provider
```

Static result:

```text
The request is only partially realizable.
A candidate set can be produced, but the requested relation cannot be verified automatically.
```

This is useful without pretending the full concept has been resolved.

---

## 36. Example: Human-Supported Capability

Invocation:

```text
Assemble the prototype today.
```

Requirements:

```text
parts.available
workspace.available
assembly.instructions
operator.skill
operator.time
operator.energy
safety_equipment
```

The resolver may observe:

```text
parts.available: yes
workspace.available: yes
assembly.instructions: yes
operator.skill: historically supported
operator.time: 45 minutes
expected_duration: 120 minutes
```

Report:

```text
Full completion is unlikely within the available horizon.
Partial assembly is realizable.
The primary blocker is time rather than skill.
```

The capability claim remains condition-indexed.

It does not reduce the person to a permanent label.

---

## 37. Tamagotchi State

The Tamagotchi represents the viability of the capability model.

Possible dimensions include:

```text
freshness
coverage
calibration
coherence
dependency integrity
revision activity
unresolved uncertainty
unsafe overconfidence
```

Example:

```yaml
tamagotchi:
  freshness: 0.81
  coverage: 0.44
  calibration: 0.72
  coherence: 0.91
  dependency_integrity: 0.68
  humility: 0.84
```

The Tamagotchi should become unhealthy when:

```text
claims are stale
predictions are overconfident
contradictions accumulate
providers disappear
failures do not revise the graph
```

It should not be rewarded merely for producing answers.

---

## 38. Security and Authority

The resolver may expose sensitive capability information.

It may reveal:

```text
credentials
physical access
personal limitations
health conditions
work patterns
infrastructure topology
operational weaknesses
```

Therefore capability manifests and observations require access controls.

The system should distinguish:

```text
who may observe
who may resolve
who may simulate
who may execute
who may revise
who may export
```

An invocation being realizable does not imply it is authorized.

Thus:

```text
realizable
!=
permitted
!=
wise
```

These should remain separate report dimensions.

---

## 39. Failure Modes

The resolver may fail through:

```text
stale manifests
incorrect provider declarations
hidden side effects
unmodeled social dependencies
false confidence
interface mismatch
ontology rigidity
excessive centralization
privacy leakage
self-fulfilling incapability claims
```

A dangerous pattern is:

```text
resolver predicts impossible
->
no attempt is made
->
no counterevidence is collected
->
prediction appears confirmed
```

The model should distinguish:

```text
not observed
currently blocked
unsupported by known providers
unsafe to attempt
forbidden
proven impossible under declared assumptions
```

These are different states.

---

## 40. Minimal Prototype

A useful prototype can remain narrow.

Suggested initial domain:

```text
one ROS workspace
one robot or simulator
one operator
five to ten capabilities
```

Initial capabilities:

```text
build_workspace
start_simulator
start_robot
run_demo
record_bag
stop_system
```

Initial observations:

```text
package versions
workspace build state
ROS graph
battery or simulator state
operator authorization
disk space
```

Initial loop:

```text
1. Register manifests.
2. Observe providers.
3. Receive one invocation.
4. Compute dependency closure.
5. Produce blockers and repair options.
6. Run a dry check.
7. Execute only after authorization.
8. Record outcome.
9. Revise one claim.
```

The prototype should optimize for transparent reports rather than autonomous complexity.

---

## 41. Minimal Data Model

The first implementation may use a property graph.

### Node types

```text
Capability
Provider
Interface
Resource
Condition
Context
Authority
Observation
Invocation
Outcome
```

### Edge types

```text
PROVIDES
REQUIRES
OPTIONALLY_REQUIRES
CONFLICTS_WITH
OBSERVED_AS
VALID_UNDER
REPLACED_BY
AUTHORIZED_BY
SUPPORTED_BY
FAILED_BECAUSE_OF
```

The graph should retain history rather than mutating all prior states in place.

---

## 42. Resolution States

A capability should not be only available or unavailable.

Suggested states:

```text
AVAILABLE
DEGRADED
BLOCKED
UNKNOWN
STALE
CONFLICTING
UNAUTHORIZED
UNSAFE
SIMULATION_ONLY
HISTORICALLY_SUPPORTED
```

An invocation report may therefore say:

```text
Physical realization: BLOCKED
Simulation realization: AVAILABLE
Remote-assisted realization: DEGRADED
Authority status: UNAUTHORIZED
```

This is more informative than one boolean.

---

## 43. Formal Summary

### Invocation resolution

\[
\operatorname{Resolve}(i,M,c)
=
r
\]

### Dependency closure

\[
C^*(r)
=
\operatorname{Closure}(r,M,c)
\]

### Provider assignment

\[
P^*(r)
=
\operatorname{Bind}(C^*(r),M,c,\Theta)
\]

### Blocking sets

\[
\mathcal B(r)
=
\operatorname{MinimalBlockers}(C^*(r),P^*(r))
\]

### Preflight estimate

\[
\hat{\eta}
=
\operatorname{Simulate}(r,P^*(r),c)
\]

### Realizability report

\[
R
=
\operatorname{Report}
(
 r,
 C^*,
 P^*,
 \mathcal B,
 \hat{\eta},
 \Theta
)
\]

### Model revision

\[
M_{t+1}
=
U(M_t,R_t,\eta_t)
\]

where:

```text
R_t = predicted realizability report
eta_t = observed execution trace
```

---

## 44. Central Principles

### Interface-Only Principle

> A capability resolver should depend primarily on declared interfaces, conditions, and observations rather than duplicate the implementations it coordinates.

### Preflight Principle

> An invocation should be checked for obvious blockers, conflicts, authority requirements, and irreversible effects before execution is attempted.

### Dependency-Closure Principle

> A high-level capability is realizable only when an admissible provider assignment satisfies the relevant dependency closure under current conditions.

### Commitment-Boundary Principle

> Reversible inspection and preparation should be separated from actions that create difficult or external side effects.

### Evidence-Indexed Capability Principle

> Capability claims should carry evidence, freshness, confidence, conditions, and revision history.

### Discrepancy-Growth Principle

> Unexpected failure and unexpected success should revise the capability graph rather than remain isolated execution events.

### Heterogeneous Composition Principle

> One realization may compose software, hardware, humans, permissions, tools, and environmental conditions through declared interfaces.

---

## 45. Central Statements

> A valid invocation is not a guarantee of realization.

> A capability resolver is not an implementation repository.

> It is a repository of currently believed realizability relations.

> Package managers, linkers, schedulers, launch systems, type systems, static analyzers, and safety interlocks already solve restricted parts of the problem.

> ROS 2 provides a useful operational middle layer for addressability, process coordination, heartbeats, controllers, and runtime evidence.

> High-level language remains permissive; lower layers progressively constrain candidate realization.

> Recognition outputs are evidence providers, not complete task resolutions.

> Static hints can prevent costly or irreversible attempts even when the model is approximate.

> Capability dependencies may span repositories, services, devices, people, permissions, and environments.

> The resolver should identify the smallest blocking relations and candidate repairs.

> Realizable does not mean authorized, safe, desirable, or guaranteed.

> The Tamagotchi represents the health of the evolving capability model, not the absolute identity of the modeled organization.

---

## 46. Conclusion

A permissive invocation language is useful because it allows a system to express high-level intentions without encoding every implementation detail.

Its permissiveness also means that successful realization cannot be inferred from the written token alone.

A capability resolver fills the gap between symbolic invocation and forced execution.

It maintains a changing graph of:

```text
what is requested
what interfaces are required
which providers are available
which conditions hold
which assumptions remain uncertain
which repairs are possible
which transitions are risky
which actions cross a commitment boundary
```

The resolver resembles `apt`, a linker, and a preflight system, but its dependency graph extends beyond packages.

Its nodes may include:

```text
Python modules
ROS nodes
vision models
controllers
robots
humans
tools
credentials
rooms
power
network
social authority
```

Its purpose is not to guarantee success.

Its purpose is to make unsupported realization attempts less blind.

The resulting loop is:

```text
invocation
->
resolution
->
dependency closure
->
provider binding
->
static hints
->
preflight simulation
->
commitment decision
->
execution
->
observed outcome
->
model revision
```

This provides a concrete role for the Tamagotchi capability mirror.

It becomes a maintained, historically revisable capability linker that asks:

> Given the current organization, what appears realizable now, what blocks it, what can be checked safely, and what should be learned before the next attempt?
