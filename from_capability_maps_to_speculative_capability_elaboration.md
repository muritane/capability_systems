# From Capability Maps to Speculative Capability Elaboration: Backward Constraints, Typed Continuations, Evidence Frontiers, and Hierarchical Realization

## Abstract

Development tooling is often organized around commands.

A developer runs:

```text
ros2 launch robot_bringup bringup.launch.py
```

or:

```text
docker build ...
kubectl apply ...
```

and learns what the environment means by observing which command fails first.

This places the burden of architectural reconstruction on the user.

A stronger approach begins from the intended capability and asks:

> What must be true for this target to be meaningful, realizable, executable, and verifiably achieved?

This reverses the normal direction of development reasoning.

Instead of eagerly enumerating every property of a workspace, the requested target induces the distinctions that matter.

A target such as:

```text
launch robot bringup
```

may elaborate into requirements for:

```text
ROS launch semantics
package resolution
overlay/underlay consistency
dependency closure
generated interfaces
middleware realization
device access
network assumptions
runtime observation
```

A deployment target may further require:

```text
artifact identity
runtime closure
entrypoint semantics
environment contract
platform compatibility
health evidence
publication
```

Some prerequisites may already hold.

Some may be absent but realizable.

Some may be unknown because no observer has yet established them.

Some may be semantically invalid.

Some may require architectural extension.

The central proposal is therefore:

\[
\boxed{
\text{a development system should elaborate a desired capability backward into
required predicates, intersect them with current and conditionally realizable
capability, and construct the smallest evidence-backed route to realization}
}
\]

This produces an architecture closer to a combination of:

```text
typed grammar
compiler elaboration
constraint propagation
backward chaining
partial evaluation
dependency scheduling
speculative planning
active observation
provenance-aware commit
```

than to a universal shell wrapper.

The result may be called a **speculative capability elaborator**.

Its job is not to predict arbitrary commands.

Its job is to make the valid continuation space explicit.

---

## 1. A Target Is More Than a Command String

Consider:

```text
ros2 launch robot_bringup bringup.launch.py
```

A conventional command runner sees:

```text
argv[0] = ros2
argv[1] = launch
...
```

But the expression carries substantially more structure.

If interpreted under ROS 2 semantics, it implies approximately:

```text
ROS 2 command semantics exist
launch is a valid ROS 2 command class
robot_bringup is expected to denote a resolvable package
bringup.launch.py is expected to denote a launch description
launch arguments must satisfy the launch description
required runtime packages must be available
runtime environment must be correctly realized
```

The command therefore describes both:

```text
an intended action
```

and:

```text
a family of predicates that must hold for the action to have meaning.
```

This suggests:

\[
\text{target expression}
\rightarrow
\text{semantic capability}
\rightarrow
\text{required realization conditions}.
\]

The target is therefore a useful source of architectural information.

---

## 2. Backward Elaboration Should Precede Blind Execution

Suppose the desired target is:

```text
Launch(robot_bringup, bringup.launch.py)
```

The system can ask backward:

```text
What realizes Launch?
What does that realization require?
What realizes those requirements?
Which of those already hold?
Which can be observed?
Which can be constructed?
```

For example:

```text
Launch(robot_bringup, bringup.launch.py)
← LaunchFileResolvable(robot_bringup, bringup.launch.py)
← PackageResolvable(robot_bringup)
← ROSPackageIndexAvailable
← ROS2EnvironmentRealized
```

while another branch may require:

```text
Launch(...)
← RuntimeDependenciesSatisfied
← rosdep closure
← system packages
```

and another:

```text
Launch(...)
← HardwareCapability(camera)
← device visible
← permissions sufficient
```

Thus the target induces a requirement graph before execution begins.

This is different from trying commands in sequence and converting failures into knowledge afterward.

---

## 3. The Architecture Should Be Target-Relative

An environment contains an enormous number of facts.

Most are irrelevant to any one task.

For example, a machine may have:

```text
thousands of packages
hundreds of environment variables
many kernel features
multiple network interfaces
several language runtimes
many cached artifacts
```

A system that attempts to model all of them eagerly becomes expensive and noisy.

Instead, let target capability be:

\[
T.
\]

Let backward elaboration produce a relevant predicate family:

\[
R(T)=\{r_1,r_2,\ldots,r_n\}.
\]

Then workspace inspection can be restricted primarily to predicates that influence:

\[
\operatorname{Reachable}(T).
\]

Thus:

\[
\boxed{
\text{the target determines which environmental distinctions deserve to be opened}
}
\]

This makes target-relative modeling an architectural economy principle, not merely a user-interface convenience.

---

## 4. Construction, Realization, and Evidence Are Different Problems

A useful elaborator should distinguish at least three questions.

### Construction

> Is this expression structurally and semantically meaningful?

### Realization

> What must exist for the denoted capability to be executable?

### Evidence

> How can the system know whether the relevant conditions actually hold?

For example:

```text
ros2 laaaaaunch ...
```

may fail at construction.

```text
ros2 launch ...
```

may be valid construction but fail realization because ROS 2 is absent.

A launched process may exist, yet its intended service may remain unverified because no observation establishes health.

These are different boundaries and should produce different explanations.

---

## 5. A Command Grammar Defines Valid Continuations

A CLI should not be represented as an arbitrary Cartesian product of flags.

Suppose a provider exposes:

```text
ros2
├── action
├── bag
├── interface
├── launch
├── node
├── param
├── pkg
├── run
├── service
└── topic
```

After:

```text
ros2 launch
```

the valid continuation space changes.

It may become approximately:

```text
ros2 launch
└── <package>
    └── <launch-file>
        └── <launch-argument>*
```

A parser or grammar therefore contributes more than accept/reject behavior.

Given partial expression \(p\), define:

\[
N(p)=\{c\mid p\cdot c\text{ is a valid semantic continuation}\}.
\]

The elaborator can expose \(N(p)\) without enumerating every invalid string.

---

## 6. Flags Should Have Grammar and Semantics Too

CLI flags are often modeled as unstructured optional strings.

This causes combinatorial ambiguity.

But flags frequently obey local grammar and semantic constraints.

For example:

```text
--ros-args
```

may open a ROS-specific argument region.

Within that region:

```text
-r <from>:=<to>
-p <name>:=<value>
```

may become valid productions.

A flag can therefore define:

```text
syntax
scope
input type
semantic effect
preconditions
conflicts
repeatability
```

Then the system reasons over structured command forms rather than all possible strings.

---

## 7. Invalid Is Not the Same as Blocked

Consider several cases.

### Invalid

```text
ros2 laaaaaunch robot_bringup ...
```

No known grammar production interprets `laaaaaunch`.

### Blocked

```text
ros2 launch robot_bringup bringup.launch.py
```

is semantically valid, but `ros2` is not currently realized.

### Preparation Required

ROS 2 is absent, but a provider knows how to realize a compatible ROS 2 environment.

### Unknown

The package may exist remotely or in an unobserved overlay, but current evidence is insufficient.

### Redesign Required

The intended capability is understood, but the architecture lacks a required provider, bridge, generator, binding, or backend.

Thus a useful vocabulary includes:

```text
INVALID
BLOCKED
PREPARATION_REQUIRED
UNKNOWN
UNSUPPORTED
REDESIGN_REQUIRED
READY
```

A single `command not found` error collapses too much information.

---

## 8. Missing Capability Need Not Stop Reasoning

Suppose:

```text
ROS2EnvironmentRealized = false
```

A conventional system may stop there.

But if the architecture knows:

\[
\operatorname{CanRealize}(ROS2EnvironmentRealized),
\]

then downstream reasoning can continue conditionally.

For example:

```text
CURRENTLY BLOCKED
    ROS2EnvironmentRealized

CONDITIONAL CONTINUATION
    assuming ROS2EnvironmentRealized:
        PackageResolvable(robot_bringup)
        LaunchFileResolvable(...)
        RuntimeDependenciesSatisfied(...)
```

The missing capability blocks execution.

It does not necessarily block elaboration.

---

## 9. Conditional Reachability Is a First-Class Relation

Ordinary reachability asks:

\[
\operatorname{Reachable}(s,T)?
\]

But capability elaboration benefits from a conditional form:

\[
\operatorname{Reachable}(s,T\mid A),
\]

where \(A\) is a set of assumptions whose realization is separately understood.

For example:

\[
\operatorname{Reachable}(
W,
Launch(robot),
\mid ROS2EnvironmentRealized
).
\]

This allows the system to distinguish:

```text
impossible under known architecture
```

from:

```text
possible after satisfying an explicit prerequisite.
```

The resulting route remains tagged as conditional until the assumption is established.

---

## 10. The Elaborator Computes a Frontier

Backward expansion cannot continue indefinitely.

Eventually the system reaches leaves classified as:

```text
SATISFIED
REALIZABLE
OBSERVABLE
UNKNOWN
UNSUPPORTED
REDESIGN_REQUIRED
```

This boundary is the current **elaboration frontier**.

For example:

```text
Launch(robot_bringup)
│
├── ROS2EnvironmentRealized
│   └── REALIZABLE
│
├── PackageResolvable(robot_bringup)
│   └── CONDITIONAL
│
├── LaunchFileResolvable(...)
│   └── CONDITIONAL
│
└── CameraOperational
    └── UNKNOWN
        └── observation required
```

The frontier tells the user not merely where execution stopped, but where present knowledge, realization, and observation stop.

---

## 11. The Next Step Is a Frontier Selection Problem

Once the frontier is explicit, guidance becomes structural.

A candidate next action should typically satisfy properties such as:

```text
it is currently executable
it removes at least one blocking predicate
it lies on a route to the declared target
its side effects are acceptable
its result can be observed
```

A simple rule is:

> select an unresolved prerequisite that dominates the target and whose own prerequisites are currently satisfiable.

Suppose:

```text
                 ROS2EnvironmentRealized
                 /          |           \
          package-index   rosdep       launch
               |            |            |
              ...          ...          ...
```

If every target route depends on `ROS2EnvironmentRealized`, it is a natural frontier action.

---

## 12. Dominating Preconditions Expose High-Leverage Steps

Let requirement graph be \(G_R\).

A predicate \(d\) dominates target \(T\) relative to frontier \(F\) when every currently represented route from \(F\) to \(T\) passes through \(d\).

Then an unresolved dominating predicate is structurally important.

This suggests a guidance heuristic:

\[
\operatorname{Next}(T)
=
\arg\min_{r\in D(T)} C(r)
\]

subject to:

```text
r is unresolved
r is currently realizable
r dominates the selected target or unlocks a required branch
```

where \(C(r)\) can include:

```text
execution cost
mutation cost
risk
network dependence
reversibility
expected information gain
```

Thus “next step” can be derived rather than guessed.

---

## 13. Unknown Predicates Create Observation Obligations

Suppose backward elaboration reaches:

```text
CameraOperational
```

but the current model has no evidence.

The correct result is not:

```text
false
```

It is:

```text
UNKNOWN
```

The system should then ask:

> What observation could distinguish the relevant states?

Possible observation levels may include:

```text
/dev/video0 exists
camera device can be opened
driver process is running
ROS topic exists
messages are being published
messages satisfy expected rate/shape
```

Each is a stronger proposition.

The target determines which one is sufficient.

---

## 14. Realization and Observation Form Distinct Graphs

It is useful to distinguish:

### Realization graph

```text
What transformations can make capability C true?
```

### Evidence graph

```text
What observations can establish sufficient evidence that C is true?
```

For example:

```text
ProcessRunning
```

may be realized by:

```text
Exec(process)
```

and observed by:

```text
PID exists
```

while:

```text
ServiceHealthy
```

may require:

```text
HTTP health probe
```

and:

```text
RobotReceivingCommands
```

may require:

```text
ROS topic observation
```

Execution truth and knowledge of execution truth should not be collapsed.

---

## 15. Observability Has a Frontier Too

A generic process monitor can observe:

```text
process existence
CPU usage
memory usage
threads
I/O
```

It cannot infer:

```text
the optimizer is making useful progress
```

unless the application exposes an observable corresponding to progress.

Likewise, a development navigator cannot infer:

```text
the robot is behaving correctly
```

from process existence alone.

Every layer therefore has an **observability frontier**.

Beyond that frontier, the system must:

```text
report UNKNOWN
use an existing probe
execute a test
instrument the application
require an observation contract
```

This is an architectural limitation, not merely missing polish.

---

## 16. Observation Is Time-Relative

Many development predicates are not permanently true once observed.

Examples include:

```text
device connected
service responsive
topic publishing
credential valid
network reachable
resource available
```

An observation should therefore carry at least:

```text
value
observer
observed_at
scope
validity/freshness relation
```

For example:

```text
TopicPublishing(/scan)
    value: true
    observed_at: 13:20:14
    observation_window: 2s
    minimum_rate: 5Hz
```

is stronger than:

```text
TopicPublishing = true
```

Historical evidence should not silently become present truth.

---

## 17. Claims May Be a Better Persistent Primitive Than Bare States

Instead of storing:

```text
DockerReady = true
```

persist an evidence-bearing claim:

```text
claim:
    subject: workspace-A
    predicate: DockerBackendReady
    value: true
    evidence: docker-info observation
    observed_at: ...
    valid_relative_to:
        daemon: ...
        host: ...
```

Then state can be computed as a projection over claims.

This helps preserve distinctions between:

```text
declared
detected
observed
verified
historical
inferred
assumed
```

A capability map should not convert weak evidence into strong state silently.

---

## 18. The Target Can Force Hidden Abstractions to Reopen

Suppose a high-level summary says:

```text
ROS2Available
```

For:

```text
ros2 pkg list
```

that may be sufficient.

For:

```text
ros2 launch robot_bringup hardware.launch.py
```

it may need to reopen into:

```text
ROS distribution
installation
underlay
overlays
package index
rosdep resolution
launch subsystem
generated interfaces
RMW implementation
DDS/network assumptions
device permissions
```

The abstraction should reopen only as far as the target requires.

Thus:

\[
\boxed{
\text{factorization depth is question-relative}
}
\]

---

## 19. A Capability Is a Relative Theorem

A statement such as:

```text
ROS2Available
```

should not necessarily be interpreted as an unconditional scalar truth.

It is closer to:

```text
ROS2Available
for capability K
under assumptions A
supported by evidence E
within validity horizon H
```

Formally, one may write:

\[
\operatorname{Holds}(C\mid K,A,E,H).
\]

This makes explicit why one coarse state can be sufficient for one query and insufficient for another.

---

## 20. Deployment Targets Push Requirements Backward

Consider:

```text
deploy image X via Kubernetes
```

The deployment target itself constrains what `X` must mean.

A useful deployable boundary may require:

```text
artifact identity
platform/architecture
entrypoint or command
runtime environment
ports
mount expectations
device/resource assumptions
health semantics
external dependencies
```

Thus:

```text
KubernetesDeployable(X)
```

can elaborate backward into:

```text
PublishedOCIArtifact(X)
RuntimeContract(X)
TargetPlatformCompatible(X)
RuntimeClosureExplicit(X)
```

The development system need not become Kubernetes.

But Kubernetes-oriented intent can force the upstream artifact contract to become more explicit.

---

## 21. Runtime Closure Is an Architectural Question

A successful image build does not establish that the image is operationally self-describing enough for deployment.

Consider hidden dependencies such as:

```text
host environment variable
unmounted configuration
local source directory
host device
implicit shell initialization
unpublished secret
architecture assumption
network service
```

A deployment target can ask:

> Which runtime assumptions remain outside the artifact and its explicit contract?

This turns “make the image closed in itself” into a tractable predicate family.

For example:

```text
RuntimeClosure
├── ExecutableEntryPoint
├── RuntimeDependenciesRepresented
├── RequiredEnvironmentRepresented
├── ExternalResourcesDeclared
└── PlatformRequirementsDeclared
```

Closure need not mean zero external dependencies.

It means external dependencies are explicit enough for the downstream realization system.

---

## 22. Capability Elaboration Resembles Compiler Elaboration

A compiler frequently turns a compact source expression into progressively more explicit intermediate representations.

Likewise:

```text
launch robot bringup
```

may lower through:

```text
LaunchRobotBringup
        ↓
ROSLaunch(
    package=robot_bringup,
    launch=bringup.launch.py
)
        ↓
ROSRuntime(
    distro=...,
    overlay=...,
    rmw=...,
    dependencies=...
)
        ↓
Exec(
    argv=...,
    env=...,
    filesystem=...,
    devices=...,
    network=...
)
        ↓
BackendProcess(...)
```

Each lowering stage makes a previously implicit contract more explicit.

---

## 23. Capability Interfaces Behave Like Hierarchical ISAs

The analogy to a CPU instruction set is useful if kept structural.

A CPU ISA exposes stable operations whose lower-level realization can remain hidden.

A development architecture can do something similar at multiple levels:

```text
User capability language
        │
        ▼
Deployment capability interface
        │
        ▼
Artifact capability interface
        │
        ▼
Workspace capability interface
        │
        ▼
ROS / Python / Cargo / CMake provider interfaces
        │
        ▼
Execution backend
        │
        ▼
OS interfaces
        │
        ▼
hardware
```

Each layer behaves like a relative instruction set for the layer above.

But no single universal development ISA is required.

---

## 24. Providers Are Decoders Plus Lowering Rules

A provider can be understood as supplying at least:

```text
recognized expressions
semantic forms
typed capability contracts
requirement expansion
realization rules
observation rules
invalidation rules
```

For example:

```text
grammar:
    ros2 launch <package> <launch-file> [args...]

semantic form:
    ROSLaunch(package, launch_file, args)

requirements:
    ROS2EnvironmentRealized
    PackageResolvable(package)
    LaunchFileResolvable(package, launch_file)
    LaunchArgumentsValid(launch_file, args)
```

The shell command is only one possible realization of that semantic form.

---

## 25. Backends Are Execution Units

A provider explains what a transformation means.

A backend explains where and under which execution semantics it is realized.

For example:

```text
ROSLaunch(...)
```

might be realized through:

```text
host backend
Docker backend
remote backend
```

subject to compatibility constraints.

This resembles an execution unit only at a structural level:

```text
semantic operation
→ compatible realization mechanism
→ concrete execution
```

The analogy is useful because it separates operation semantics from placement.

---

## 26. Speculation Should Usually Be Symbolic First

A CPU may execute instructions speculatively.

A capability elaborator can perform a cheaper form first:

```text
ASSUME ROS2EnvironmentRealized

then derive:
    package must resolve
    launch file must resolve
    hardware predicate remains unknown
    image path becomes conditionally reachable
```

No environment mutation is required.

This is better described as:

```text
symbolic speculation
conditional elaboration
partial evaluation
```

than literal CPU speculation.

---

## 27. Isolated Realization Can Become Stronger Speculation

Sometimes symbolic reasoning is insufficient.

A system may safely realize a candidate state in an isolated environment:

```text
create temporary container
install candidate dependencies
attempt configure/build
observe resulting capabilities
discard if invalid
```

This resembles stronger speculative execution.

The candidate world is not yet authoritative workspace state.

It is an experiment whose outputs require validation before commit.

---

## 28. Validation Before Commit Resembles Retirement

Suppose:

```text
docker build
```

returns success.

This may establish:

```text
ImageBuilt(digest=X)
```

but not automatically:

```text
RuntimeHealthy(X)
```

The latter requires additional evidence.

Thus a transformation should become authoritative persistent state only when its declared postconditions are sufficiently established.

Conceptually:

```text
candidate execution
→ observations
→ postcondition validation
→ provenance record
→ committed claim
```

This resembles retirement in a CPU only structurally:

speculative or intermediate work becomes architectural state at a defined commit boundary.

---

## 29. Invalidation Is as Important as Realization

A useful capability contract should specify not only how a claim becomes true, but how prior evidence can cease to justify it.

For example:

```text
BuildCurrent
```

may be invalidated by:

```text
source digest change
generator state change
dependency lock change
toolchain change
```

Similarly:

```text
DeviceAvailable
```

may be invalidated by:

```text
device disconnect
permission change
container recreation
```

A capability definition may therefore contain:

```text
requires
realize
observe
invalidate_when
produces
side_effects
```

This is more useful than an action definition that stores only a command.

---

## 30. The Graph Should Mostly Be Virtual

A literal persistent graph containing every possible node and edge may be unnecessary.

Instead, retain durable elements such as:

```text
workspace identity
declarations
locks
selected provenance
expensive observations
committed claims
```

and synthesize query-relevant graph structure from:

```text
provider rules
backend rules
repository discovery
current observations
target expression
```

Conceptually:

```text
persistent claims
      +
provider semantics
      +
backend semantics
      +
current observations
      +
target
      ↓
query-specific capability graph
```

This reduces graph inflation while preserving navigability.

---

## 31. Partial Maps Compose Through Typed Boundaries

No provider needs universal knowledge.

For example:

```text
ROS provider
    package, interface, middleware, launch semantics

Cargo provider
    Rust dependency and build semantics

Docker backend
    isolated execution semantics

OCI exporter
    artifact/runtime contract semantics

Kubernetes adapter
    downstream deployment requirements
```

Composition occurs when contracts align.

For example:

```text
Cargo-produced library
```

must satisfy the representation expected by:

```text
ROS package installation
```

A shared label such as `output` is insufficient.

Typed boundaries prevent accidental composition.

---

## 32. Unsupported Syntax and Unsupported Capability Need Different Extension Paths

Suppose:

```text
ros2 laaaaaunch ...
```

No provider grammar recognizes the expression.

Possible responses include:

```text
INVALID
```

or, if the user intends a genuinely new command class:

```text
provider grammar extension required
```

Now suppose the expression is semantically understandable:

```text
ROS node in language X
```

but no realization path exists.

This is different:

```text
REDESIGN_REQUIRED
    implement generator/binding/build integration
```

One extends the construction language.

The other extends the realization architecture.

---

## 33. Architecture Extension Changes the Effective Virtual Machine

If providers define the valid semantic operations available to the elaborator, installing or implementing a provider changes the effective capability vocabulary.

Let current architecture expose semantic set:

\[
\Sigma_G.
\]

Adding provider \(P\) yields:

\[
\Sigma_{G'}=\Sigma_G\cup\Sigma_P.
\]

A previously unrepresentable target may become representable.

A previously redesign-dependent target may become realizable.

This resembles extending a virtual machine more than merely adding another shell command.

---

## 34. The System Is Closer to an Extensible Compiler Than a Universal Executor

A universal executor says:

```text
give me a command and I will run it
```

A capability elaborator says:

```text
give me a target
I will determine whether I can interpret it
I will elaborate its requirements
I will identify current and conditional routes
I will determine what evidence is missing
I will expose the next minimal realizable frontier
```

Execution is one phase.

The deeper value is semantic elaboration and explanation.

---

## 35. A Compact Formal Model

Let a capability elaboration architecture be:

\[
\mathfrak E=
(\Sigma,\Gamma,R,O,I,S,P,H),
\]

where:

```text
Σ
    semantic capability forms and construction grammar

Γ
    elaboration and requirement rules

R
    realization rules

O
    observation/evidence rules

I
    invalidation rules

S
    current evidence-bearing state/claims

P
    provenance relations

H
    validity horizons and contextual assumptions
```

A target expression \(x\) is first interpreted:

\[
\operatorname{Interpret}(x)\Rightarrow T
\]

if a semantic form exists.

Then backward elaboration constructs:

\[
\Gamma^*(T)=R_T,
\]

where \(R_T\) is the target-relative requirement graph.

The planner intersects this with current and realizable state.

---

## 36. Elaboration Is a Backward Fixed-Point Process

Let initial frontier be:

\[
F_0=\{T\}.
\]

For each unresolved semantic predicate \(r\), provider rules may expand:

\[
r\Rightarrow \operatorname{Req}(r).
\]

Repeated expansion yields:

\[
F_{k+1}
=
\bigcup_{r\in F_k}
\operatorname{Expand}(r).
\]

Expansion can stop when every frontier element is classified as:

```text
satisfied
realizable
observable
unknown
unsupported
redesign-dependent
```

The result is not a proof that execution will succeed.

It is the strongest currently represented decomposition of what success requires.

---

## 37. Forward Realization Meets Backward Requirements

Backward elaboration alone can generate requirements without knowing what the current system can actually do.

Forward capability analysis starts from current claims and known realization edges.

Thus two structures meet:

```text
              desired target
                    │
          backward elaboration
                    │
                    ▼
             required predicates
                    │
                    ×
                    │
             available routes
                    ▲
          forward realization
                    │
             current claims
```

A plan exists where backward requirements and forward realizability connect under compatible constraints.

---

## 38. Planning Can Continue Beyond the First Failure

Suppose ROS 2 is currently absent.

A linear executor sees:

```text
ros2: command not found
```

A capability elaborator can still compute:

```text
TARGET
    Launch(robot_bringup)

BLOCKING FRONTIER
    ROS2EnvironmentRealized

KNOWN REALIZATION
    ROS2EnvironmentRealized
        via Docker image ros:...
        or host installation ...

CONDITIONAL DOWNSTREAM
    package resolution
    launch-file resolution
    runtime closure
    hardware observation
```

This reveals future blockers before the first one is physically removed.

That is one of the main practical benefits of speculation.

---

## 39. Parallel Elaboration Can Find Independent Problems Early

Suppose the target requires both:

```text
ROS2EnvironmentRealized
CameraDeviceAvailable
```

and these branches are independent.

Even if ROS 2 is missing, the system may already observe:

```text
camera device absent
```

or:

```text
camera device available but permission missing
```

Thus elaboration can expose multiple independent frontier conditions without executing them serially.

This is useful because the first runtime error is not necessarily the only or most expensive blocker.

---

## 40. Observation Actions Can Be Planned Like Realization Actions

If a target depends on an unknown predicate, the planner may search for an observation route.

For example:

```text
Required:
    TopicPublishing(/camera/image_raw)

Current:
    UNKNOWN

Observation route:
    realize ROS graph access
    resolve topic type
    sample topic for 2s
    verify minimum message count
```

Observation therefore participates in planning.

It consumes resources, has prerequisites, produces evidence, and may itself fail.

---

## 41. Tests, Pings, Probes, and Checkers Are Evidence-Producing Capabilities

A test is not merely another command.

It transforms uncertainty into evidence.

For example:

```text
UNKNOWN(ServiceHealthy)
    --HTTP probe-->
Observed(ServiceHealthy=true)
```

or:

```text
UNKNOWN(InterfaceCompatible)
    --compile test-->
Observed(InterfaceCompatible=false)
```

Thus test infrastructure belongs naturally in the evidence graph.

This also explains why an architecture may need new checkers or probes when existing systems do not expose sufficient observability.

---

## 42. Instrumentation Is Architecture Extension on the Evidence Side

Suppose the system needs to establish:

```text
OptimizerMakingProgress
```

but no existing observer can distinguish progress from a busy loop.

Then the missing capability is not necessarily execution.

It is observation.

Possible extension:

```text
add progress metric
add health endpoint
publish ROS diagnostic
emit structured event
```

This modifies the evidence architecture.

Thus redesign can occur in at least two forms:

```text
realization redesign
observation redesign
```

Both should be represented explicitly.

---

## 43. Sampling Policy Belongs to the Observation Contract

A continuously changing system cannot be observed at infinite frequency.

A task manager samples.

A ROS topic checker samples.

A health probe samples.

The observer therefore requires a temporal contract such as:

```text
sample interval
observation window
freshness threshold
minimum rate
failure tolerance
```

For example:

```text
Health(ServiceX)
    observed every 5s
    stale after 15s
```

The development architecture need not become a permanent monitoring system.

But when runtime evidence matters to development capability, sampling semantics must be explicit enough to avoid false certainty.

---

## 44. Development Observation Need Not Become Operations Monitoring

A capability elaborator may temporarily inspect:

```text
process health
ROS topic availability
device state
network connectivity
```

because those facts determine whether a development target is realizable or validated.

It does not follow that the tool should own continuous production monitoring.

A useful boundary remains:

```text
development observation
    evidence sufficient to establish development/runtime contract

operations monitoring
    ongoing application and fleet behavior after handoff
```

The same predicate may appear in both domains under different responsibility horizons.

---

## 45. Capability Contracts Should Be Reopenable

A high-level contract may initially say:

```text
DockerExecReady
```

If sufficient, the planner should treat it as a relative primitive.

If a target fails because of:

```text
UID mapping
GPU access
network namespace
device mount
```

then `DockerExecReady` must reopen.

A useful capability node therefore behaves like a cached abstraction whose internal distinctions can be reconstructed when needed.

This prevents both:

```text
eager microscopic modeling
```

and:

```text
irreversible black-box abstraction.
```

---

## 46. The Lowest Common Realization Primitive May Still Be Exec

Many domain-specific transformations eventually require process execution.

For example:

```text
build
test
generate
launch
package
probe
```

can often be lowered to:

```text
Exec(command, environment, resources)
```

But `Exec` should remain a lower-level realization primitive, not the semantic model of everything.

Thus:

```text
ROSLaunch
    is not merely a string command
```

although one realization of it may lower to:

```text
Exec([ros2, launch, ...], ROS-environment, ...)
```

This preserves semantics while reusing common execution machinery.

---

## 47. Hardware Is the Ultimate Realization Substrate, Not the Useful Modeling Level

Ultimately all execution becomes physical state transition.

Conceptually:

```text
ROS launch
→ processes
→ syscalls
→ kernel behavior
→ machine instructions
→ micro-operations
→ physical hardware state
```

But a development elaborator should not descend to hardware unless the target depends on hardware distinctions.

Examples include:

```text
AVX requirement
GPU capability
realtime scheduling
specific device
CPU architecture
memory limit
```

The architecture should stop lowering as soon as a stable lower-level contract is sufficient for the current question.

---

## 48. The CPU Analogy Has a Precise Scope

Several correspondences are useful:

```text
CPU concept                     capability elaborator

ISA instruction                 capability/action contract
decoder                         provider/parser
operands                        typed inputs/requirements
architectural state             committed workspace claims
microarchitectural state        actual host/container/tool state
dependency graph                requirement graph
execution unit                  backend/tool realization
speculation                     conditional or isolated realization
fault                           invalid/blocked realization
retirement                      validated provenance-aware commit
performance counter             observer/probe
microcode/lowering              provider-specific decomposition
```

The analogy is structural.

The development system is not a CPU emulator.

Its world is open, distributed, partially observable, and extensible.

---

## 49. The Open World Is the Major Difference From an ISA

A CPU ISA is intentionally closed and tightly specified.

Development ecosystems evolve continuously.

New elements may appear:

```text
build systems
languages
middleware
cloud platforms
devices
package managers
deployment systems
observers
```

Therefore the elaborator must support partial semantic maps.

A provider can say:

```text
I understand this region of the capability space.
```

Unknown or unsupported regions must remain explicit rather than being guessed into existence.

---

## 50. The System Should Prefer Proof-Carrying Continuations

A continuation is more useful when it carries:

```text
why it is valid
which requirements it assumes
which evidence supports those assumptions
what side effects execution may have
what observations establish success
what invalidates the result
```

Thus a proposed next action is not merely:

```text
run apt install ...
```

but something closer to:

```text
ACTION
    realize ROS2Environment

WHY
    dominates all represented routes to Launch(robot_bringup)

PRECONDITIONS
    network available
    host mutation permitted

EXPECTED POSTCONDITION
    ROS2CLIAvailable

VERIFY WITH
    ros2 --help + distro observation

SIDE EFFECTS
    host packages modified
```

This makes route guidance auditable.

---

## 51. A Minimal Capability Definition

A practical provider-level capability contract could begin with:

```yaml
capability: ROS2EnvironmentRealized

requires:
  - CompatiblePlatform

realize:
  - host_install
  - docker_environment

observe:
  - ros2_cli_probe
  - distro_probe

invalidate_when:
  - environment_changed
  - backend_removed

produces:
  - ROS2CLIAvailable
  - ROSPackageIndexPotential
```

A semantic action could then be:

```yaml
action: ROSLaunch

syntax:
  - ros2 launch <package> <launch_file> [args...]

requires:
  - ROS2EnvironmentRealized
  - PackageResolvable(package)
  - LaunchFileResolvable(package, launch_file)

realize:
  - Exec(...)

observe:
  - process_started
```

The exact schema is secondary.

The distinctions are primary.

---

## 52. The Deep Interface Becomes “Elaborate This Target”

A compact user interface might be:

```text
$ wsx elaborate "ros2 launch robot_bringup bringup.launch.py"

TARGET
    ROSLaunch(robot_bringup, bringup.launch.py)

SATISFIED
    source workspace present
    Docker backend available

BLOCKING FRONTIER
    ROS2EnvironmentRealized

REALIZABLE VIA
    Docker ROS 2 environment

CONDITIONAL DOWNSTREAM
    PackageResolvable(robot_bringup)
    LaunchFileResolvable(...)
    RuntimeDependenciesSatisfied

UNKNOWN
    CameraOperational

OBSERVATION AVAILABLE
    camera device probe

NEXT DOMINATING STEP
    realize ROS2EnvironmentRealized
```

This exposes substantially more structure than executing the command and reporting the first error.

---

## 53. A Second Interface Is “How Far Can This Target Be Elaborated?”

For emerging or partially supported ecosystems:

```text
$ wsx frontier target-X
```

could report:

```text
INTERPRETED
    target-X → CapabilityX

ELABORATED THROUGH
    provider A
    provider B
    backend C

FRONTIER
    MissingBinding(language-X)

CLASSIFICATION
    REDESIGN_REQUIRED

KNOWN CONTINUATION IF PROVIDED
    generate interfaces
    build package
    construct artifact
```

This makes the maximum represented continuation explicit.

---

## 54. A Third Interface Is “What Would I Need to Observe?”

For example:

```text
$ wsx evidence hardware-test

TARGET
    HardwareTestReady

UNKNOWN PREDICATES
    DeviceReachable(/dev/ttyACM0)
    DDSPeerVisible(robot-controller)

AVAILABLE OBSERVERS
    device-open probe
    ROS graph probe

MISSING OBSERVER
    firmware compatibility

SUGGESTED EXTENSION
    implement firmware-version probe
```

This turns missing knowledge into a concrete architectural requirement.

---

## 55. A Fourth Interface Is “What Can Be Speculated Without Mutation?”

For example:

```text
$ wsx speculate deploy

ASSUMPTIONS
    ROS2EnvironmentRealized
    RegistryReachable

DERIVED
    build route represented
    OCI packaging route represented
    Kubernetes runtime contract incomplete

MISSING DECLARATION
    target architecture
    health semantics

NO MUTATION PERFORMED
```

This is useful for planning before installing, building, or deploying anything.

---

## 56. The Planner Should Separate Knowledge Gain From State Change

Some actions primarily change the world:

```text
install package
build artifact
start service
flash firmware
```

Others primarily change knowledge:

```text
probe device
inspect manifest
run compatibility test
query package manager
sample topic
```

A planner may choose between them.

Sometimes the cheapest next step is an observation that proves an expensive realization unnecessary.

Thus route cost should include information value.

---

## 57. Explanation Should Include Counterfactual Continuations

A useful elaborator can answer:

```text
Why blocked?
```

but also:

```text
What becomes reachable if I satisfy X?
```

For example:

```text
If ROS2EnvironmentRealized:
    package resolution becomes checkable
    launch-file resolution becomes checkable
    ROS graph observers become available

If CameraDeviceAvailable:
    hardware-test remains blocked by ROS environment
```

This lets the user see leverage before executing a step.

---

## 58. The Map Is Therefore a Program Space, Not Only a State Space

A state map answers:

```text
what exists now?
```

A capability elaborator additionally answers:

```text
what expressions are meaningful?
what can those expressions denote?
what must be true for them to execute?
which conditional futures follow from realizable assumptions?
what evidence would establish each future?
```

Thus the map becomes a represented **continuation program space**.

The current state is one boundary condition on that space.

---

## 59. Repeated Elaboration Can Produce New Relative Primitives

Suppose a difficult configuration is repeatedly established:

```text
ROS2_JAZZY_ROBOT_HW_READY
```

Once its realization and evidence conditions are stable, it can become an addressable relative primitive.

Later targets can depend on:

```text
ROS2_JAZZY_ROBOT_HW_READY
```

without reopening every package, permission, middleware, and device distinction.

If a later failure requires those distinctions, the primitive reopens.

Thus repeated successful elaboration compresses future reasoning.

---

## 60. Provenance Is the Memory of Successful Elaboration

When a target succeeds, useful structure should remain:

```text
which semantic target was requested
which elaboration path was selected
which assumptions were realized
which observations established postconditions
which artifact resulted
which provider/backend versions participated
```

This converts a one-time solution into reusable architecture.

A successful route should leave behind more than shell history.

---

## 61. Failure Should Also Produce Persistent Knowledge

A failed attempt may reveal:

```text
this image cannot run on arm64
this launch file requires device X
this package version conflicts with distro Y
this backend cannot provide realtime scheduling
```

These observations can refine future elaboration.

Failure therefore contributes constraints to the knowledge base.

A mature system remembers boundaries as well as successful paths.

---

## 62. AI Is Optional but Benefits From the Same Structure

Nothing in the core requires a language model.

Deterministic machinery can provide:

```text
parsing
grammar continuation
backward requirement expansion
constraint propagation
route search
dominator analysis
observation planning
state validation
provenance
```

AI may help with:

```text
interpreting vague user intent
mapping documentation into candidate provider rules
explaining unfamiliar decompositions
proposing missing observers
proposing architecture extensions
```

But AI should not silently invent capability edges and treat them as verified infrastructure.

---

## 63. The Core Should Remain Small

Despite the large conceptual space, the core engine can remain focused on:

```text
interpret
elaborate
classify
observe
plan
realize
validate
commit
explain
```

Providers and backends supply domain knowledge.

The core supplies composition and reasoning semantics.

---

## 64. A Candidate Construction Sequence

A practical implementation could proceed as follows.

```text
1. Define semantic capability and predicate types.

2. Define provider grammar and interpretation interfaces.

3. Define backward requirement expansion.

4. Define evidence-bearing claims and validity horizons.

5. Implement one execution backend and one demanding provider.

6. Implement conditional reachability.

7. Implement frontier classification:
       satisfied
       realizable
       observable
       unknown
       redesign-required

8. Implement next-step selection from unresolved prerequisites.

9. Add explicit observation routes.

10. Add validation and provenance-aware commit.

11. Add invalidation.

12. Add isolated speculative realization.

13. Add artifact/runtime-contract elaboration.

14. Add deployment-target adapters without owning deployment reconciliation.

15. Only then explore richer cross-layer constructive completion.
```

A demanding ROS 2 + container + hardware case remains a useful first stress test because it forces the model to handle:

```text
CLI grammar
package resolution
build systems
generated interfaces
overlays
middleware
devices
permissions
network semantics
runtime observation
```

---

## 65. Failure Modes

Several implementation failures are likely.

### Eager ontology explosion

The system models everything whether or not a target depends on it.

### Untyped command collapse

Every capability becomes `run this string`.

### False speculation

Conditionally reachable states are displayed as currently available.

### Observation collapse

`not checked` becomes `healthy`.

### Stale evidence

Historical observations remain authoritative indefinitely.

### Provider overreach

One provider attempts to understand every ecosystem.

### Hidden policy

The planner silently chooses among routes with different mutation or risk properties.

### Runtime scope expansion

The development elaborator becomes a permanent production orchestrator.

Each failure weakens the central distinction between represented possibility, realization, evidence, and preference.

---

## 66. Central Principles

### Target-Induced-Structure Principle

> Model the distinctions required by the requested capability rather than eagerly representing every environmental fact.

### Construction-Before-Execution Principle

> Determine whether an expression is semantically valid before treating it as an executable command.

### Backward-Elaboration Principle

> Expand a desired capability into the predicates and intermediate capabilities required for its realization.

### Conditional-Reachability Principle

> Missing but realizable prerequisites may block execution without blocking further symbolic elaboration.

### Frontier Principle

> Stop expansion at the boundary of satisfied, realizable, observable, unknown, unsupported, and redesign-dependent predicates.

### Dominating-Prerequisite Principle

> Prefer next steps that remove structurally necessary blockers shared by the selected target's represented routes.

### Evidence-Separation Principle

> A capability being realized and the system having sufficient evidence of that capability are different relations.

### Observation-Obligation Principle

> An unknown predicate required by a target induces a search for an observation capable of resolving it.

### Temporal-Evidence Principle

> Dynamic observations must carry freshness and scope rather than becoming timeless truth.

### Reopenable-Abstraction Principle

> Treat stable lower-level capability as a primitive until a target depends on distinctions hidden inside it.

### Hierarchical-ISA Principle

> Stable capability contracts may serve as instruction-like interfaces between abstraction levels without requiring one universal development instruction set.

### Symbolic-Speculation Principle

> Continue reasoning under explicit realizable assumptions before performing mutating execution.

### Validated-Commit Principle

> Persist a derived state as authoritative only after its required postconditions have sufficient evidence.

### Partial-Map Principle

> Providers contribute bounded semantic regions; unsupported regions remain explicit.

### Runtime-Closure Principle

> Deployment intent should force runtime assumptions to become explicit at the artifact handoff boundary.

### Knowledge-Persistence Principle

> Successful and failed elaborations should leave reusable constraints, evidence, provenance, and relative primitives.

---

## 67. A Compact Architecture

A compact implementation may look like:

```text
                 ┌──────────────────────────┐
                 │      target expression   │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ parser / semantic        │
                 │ interpretation           │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ backward capability      │
                 │ elaboration              │
                 └────────────┬─────────────┘
                              │
                 ┌────────────┴─────────────┐
                 │                          │
                 ▼                          ▼
        ┌─────────────────┐       ┌─────────────────┐
        │ realization     │       │ evidence        │
        │ requirements    │       │ requirements    │
        └────────┬────────┘       └────────┬────────┘
                 │                          │
                 └────────────┬─────────────┘
                              ▼
                 ┌──────────────────────────┐
                 │ frontier classification  │
                 │ + conditional reachability│
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ route / observation      │
                 │ planner                  │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ providers + backends     │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ existing tools / OS      │
                 │ / hardware               │
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ observations + validation│
                 └────────────┬─────────────┘
                              │
                              ▼
                 ┌──────────────────────────┐
                 │ committed claims +       │
                 │ provenance               │
                 └──────────────────────────┘
```

The system remains useful even if most graph structure is synthesized on demand rather than stored literally.

---

## 68. Conclusion

Development systems already expose many kinds of structured semantics.

A CLI parser knows which command forms are valid.

A package manager knows dependency relations.

A build system knows producible targets.

A middleware provider knows interface and runtime requirements.

A container backend knows isolation and execution semantics.

A deployment platform imposes a runtime contract on the artifact it can consume.

A probe or test can convert an unknown condition into evidence.

The missing layer is not necessarily another executor.

It is an architecture that composes these structures around a requested target.

The key shift is:

```text
current workspace
→ enumerate what exists
```

becoming:

```text
desired capability
→ elaborate what must be true
→ intersect with what is currently true
→ continue through what is conditionally realizable
→ identify what must be observed
→ expose the current frontier
→ select a minimal high-leverage next step
→ realize
→ validate
→ commit evidence and provenance
```

This makes several distinctions explicit:

```text
invalid expression
≠ blocked realization
≠ missing preparation
≠ unknown state
≠ missing observer
≠ architectural redesign
```

It also clarifies the role of speculation.

The system need not mutate the environment merely to reason beyond the first missing dependency.

It can elaborate conditionally.

It can ask what would become reachable if a known prerequisite were realized.

It can search for independent blockers in parallel.

It can construct observation routes for unknown predicates.

Only later does it execute concrete transformations.

The CPU analogy is useful because both systems benefit from:

```text
typed operations
dependency structure
conditional continuation
separation of intermediate and committed state
explicit observation
stable abstraction boundaries
```

But the development world is open and only partially observable.

Therefore the better architectural model is not one fixed universal ISA.

It is a hierarchy of extensible capability interfaces with explicit lowering, realization, observation, invalidation, and provenance semantics.

The resulting system can be summarized as:

\[
\boxed{
\begin{aligned}
&\text{target expression}\\
&\xrightarrow{\text{interpret}} \text{semantic capability}\\
&\xrightarrow{\text{backward elaborate}} \text{required predicates}\\
&\xrightarrow{\text{intersect}} \text{current + conditional frontier}\\
&\xrightarrow{\text{plan}} \text{realization and observation routes}\\
&\xrightarrow{\text{execute}} \text{candidate states}\\
&\xrightarrow{\text{validate}} \text{evidence-backed claims}\\
&\xrightarrow{\text{persist}} \text{reusable capability knowledge}.
\end{aligned}
}
\]

The deepest interface is therefore no longer only:

> Where can I go from here?

It becomes:

> Given what I want to make true, how far can its requirements be elaborated; which of them already hold; which can be realized or observed; where does the current frontier lie; and what is the smallest action that meaningfully advances that frontier?

That is the role of a **speculative capability elaborator**.

---

## Relation to the Navigable Development Architecture Framework

This document is a standalone refinement of the earlier capability-map view developed in:

```text
From Reproducible Workspaces to Navigable Development Architectures:
Capability Maps, Realization Paths, Persistent State, and Constructive Guidance
```

The earlier framework emphasizes:

```text
typed capability graphs
providers
backends
reachability
persistent state
provenance
semantic zoom
constructive guidance
```

The present framework changes the center of gravity from:

```text
represent the development map and navigate it
```

toward:

```text
start from a desired capability
elaborate its necessary structure backward
use the existing map as a knowledge and realization substrate
and synthesize only the target-relative continuation space that matters.
```

The two views are compatible.

The capability map supplies the reusable roads.

The elaborator determines which roads, assumptions, observations, and extensions become relevant for the target currently under consideration.
