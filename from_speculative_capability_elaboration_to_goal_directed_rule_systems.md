# From Speculative Capability Elaboration to Goal-Directed Rule Systems: Minimal Kernels, AND/OR Planning, Epistemic Frontiers, and Executable Proofs

## Abstract

Development tooling is often organized around commands, packages, files, processes, and infrastructure objects.

A stronger architecture can instead begin from a desired proposition:

```text
make T true
```

and ask:

```text
What would justify T?
What alternative ways exist to establish it?
Which prerequisites already hold?
Which are realizable?
Which are merely unobserved?
Which observations would reduce uncertainty?
Which routes are impossible under the represented architecture?
Which action advances the target with the least cost, mutation, and risk?
```

This document develops a compact refinement of speculative capability elaboration around a smaller formal kernel.

The central proposal is:

\[
\boxed{
\text{model development as goal-directed reasoning over typed propositions,
AND/OR rules, evidence-bearing claims, and executable effects}
}
\]

Rather than treating capabilities, requirements, observations, commands, and execution steps as unrelated categories, the architecture can derive most of them from four primitives:

```text
Proposition
Rule
Claim
Effect
```

A proposition states what may hold.

A rule states what would justify or establish a proposition.

A claim records why the system currently believes a proposition, under which scope and validity conditions.

An effect is an executable transition that may change the world, knowledge, or both.

This yields an architecture that is closer to:

```text
typed logic programming
AND/OR planning
compiler elaboration
partial evaluation
active diagnosis
proof search
build-system dependency reasoning
effect systems
provenance tracking
```

than to a universal command runner.

The principal interface becomes:

```text
elaborate(target)
```

whose purpose is not merely to execute the target, but to construct the smallest defensible route from desired proposition to evidence-backed realization.

---

## 1. The Core Problem Is Not Command Execution

Consider a target:

```text
Launch(robot_bringup, bringup.launch.py)
```

A command-oriented system asks:

```text
Which command should I run?
```

A capability-oriented system asks:

```text
What must be true for Launch(...) to be meaningful and successful?
```

A goal-directed rule system asks a more precise question:

> What rules can establish this proposition, what premises do those rules require, and what evidence currently supports those premises?

This shift is important.

The environment contains far more state than any one target requires.

A development system therefore should not begin by attempting to know everything.

It should begin with a target and open only the distinctions that influence its justification.

Let the desired proposition be:

\[
T.
\]

Then the relevant architecture is not the entire world model.

It is the target-induced subspace:

\[
\mathcal R(T).
\]

The system's job is to construct enough of \(\mathcal R(T)\) to determine:

```text
whether T is meaningful
whether T is currently justified
whether T can be realized
what assumptions make T conditionally reachable
what observations are required
what alternative routes exist
what next action is useful
```

This is the fundamental economy principle.

---

## 2. A Smaller Kernel

A rich capability architecture can accumulate many nouns:

```text
capability
predicate
semantic action
requirement
claim
observer
realization
provider
backend
continuation
frontier
route
artifact
state
```

Many of these distinctions are useful at the interface level.

They do not all need to be primitive in the reasoning kernel.

A smaller kernel can begin with four concepts.

### Proposition

A typed statement that may hold.

Examples:

```text
ROS2EnvironmentRealized(workspace)
PackageResolvable(robot_bringup)
LaunchFileResolvable(robot_bringup, bringup.launch.py)
CameraDeviceOpenable(/dev/video0)
TopicPublishing(/scan, min_rate=5Hz)
ImageBuilt(source_digest, image_digest)
RuntimeHealthy(image_digest)
```

A proposition is neither a command nor a Boolean variable stored forever.

It is a semantic statement whose truth may depend on scope, time, assumptions, and evidence.

### Rule

A typed relation describing one way to derive or establish a proposition.

Conceptually:

\[
r:
P_1 \land P_2 \land \cdots \land P_n
\Rightarrow Q.
\]

Multiple rules may have the same conclusion.

Thus:

\[
r_1:A\land B\Rightarrow Q
\]

and:

\[
r_2:C\land D\Rightarrow Q
\]

encode alternative routes to \(Q\).

### Claim

An evidence-bearing assertion about a proposition.

Conceptually:

```text
Claim(
    proposition,
    value,
    evidence,
    scope,
    observed_at,
    validity,
    assumptions,
    provenance
)
```

Claims are the durable epistemic state of the system.

### Effect

An executable operation that may produce new world state, new evidence, or both.

Examples:

```text
InstallPackages(...)
BuildImage(...)
StartProcess(...)
ProbeDevice(...)
InspectManifest(...)
SampleTopic(...)
RunCompileCheck(...)
```

An effect has preconditions, expected outcomes, side effects, cost, and validation requirements.

Most higher-level concepts can then be reconstructed from these primitives.

---

## 3. Capability Is a Role Played by a Proposition

A capability need not require a separate metaphysical category.

A proposition becomes capability-like when another rule depends on it.

For example:

```text
ROS2EnvironmentRealized(workspace)
```

acts as a capability because it enables other derivations:

```text
ROS2EnvironmentRealized
→ PackageResolutionAvailable

ROS2EnvironmentRealized
→ ROSGraphObservationAvailable

ROS2EnvironmentRealized
→ ROSLaunchSemanticsExecutable
```

Likewise:

```text
DockerBackendReady
```

is useful not because it has a special ontological status, but because many effects require it.

Thus capability can be treated as:

> a proposition used as an enabling premise in one or more rules.

This makes the kernel smaller without removing the architectural usefulness of capability terminology.

---

## 4. Requirements Are Premises of Rules

A requirement is likewise relational.

Suppose:

```text
ROSLaunch(package, launch_file)
```

has a realization rule:

```text
ROS2EnvironmentRealized
AND PackageResolvable(package)
AND LaunchFileResolvable(package, launch_file)
AND RuntimeDependenciesSatisfied(package)
→ ROSLaunchExecutable(package, launch_file)
```

Then the requirements are simply the premises of the selected rule.

This matters because different rules may impose different requirements.

For example:

```text
HostROS2Installed
AND HostPackageIndexAvailable
→ ROS2EnvironmentRealized
```

while:

```text
DockerAvailable
AND ROS2ImageAvailable
→ ROS2EnvironmentRealized
```

There is no universal flat list of requirements for `ROS2EnvironmentRealized`.

Requirements are route-relative.

---

## 5. The Correct Structure Is AND/OR, Not Merely a Dependency Graph

Ordinary dependency graphs are insufficient once a target has alternative realizations.

Consider:

```text
ROS2EnvironmentRealized
```

which may be established by:

```text
HostInstallRoute
OR DockerRoute
OR RemoteEnvironmentRoute
```

Each route may itself require multiple conditions:

```text
DockerRoute
    requires:
        DockerBackendReady
        CompatibleROSImage
        RequiredDeviceMappingRepresentable
```

This produces an AND/OR structure.

At proposition nodes:

```text
OR
```

selects among alternative rules.

Within a rule:

```text
AND
```

requires its premises jointly.

Conceptually:

```text
                         ROS2EnvironmentRealized
                         /          |           \
                       OR           OR           OR
                      /             |             \
             HostInstall       DockerRoute      RemoteRoute
                |                  |                 |
               AND                AND               AND
             /  |  \            /  |  \           /   \
           ... ... ...         ... ... ...        ...  ...
```

More precisely, the system is naturally represented as a directed hypergraph.

A rule is a hyperedge:

\[
\{P_1,\ldots,P_n\}\rightarrow Q.
\]

Multiple incoming hyperedges to \(Q\) encode alternatives.

This is a better formal substrate than a simple directed graph.

---

## 6. Why AND/OR Structure Changes Planning

Suppose:

```text
Target T
```

has two routes.

Route A:

```text
A1 AND A2 AND A3 → T
```

Route B:

```text
B1 AND B2 → T
```

If `A1` is missing, it does not follow that `A1` dominates the target.

Route B may bypass it entirely.

Therefore notions such as:

```text
dominator
blocking prerequisite
minimal route
frontier
next step
```

must be defined over alternative proof or realization structures.

A proposition dominates a target only relative to the currently admitted route set.

If a new provider introduces another route, the dominator relation may change.

Thus planning is architecture-relative.

---

## 7. Proof Search and Plan Search Are Closely Related

A successful elaboration resembles a proof:

```text
premises
→ intermediate propositions
→ target proposition
```

But a development system is not merely proving static facts.

Some premises can become true through effects.

Therefore the system searches for an executable proof.

A route can be written as:

\[
\Pi =
(C_0,E_1,C_1,E_2,\ldots,E_n,C_n)
\]

where:

```text
C_i
    is the set of justified claims after step i

E_i
    is an effect

C_n
    contains sufficient justification for target T
```

A plan is therefore not merely a sequence of commands.

It is a sequence of evidence-producing state transitions whose end condition justifies the requested proposition.

---

## 8. Realization Rules and Observation Rules Can Share One Shape

A traditional architecture may distinguish:

```text
realization graph
evidence graph
```

The distinction remains important.

But they can share one rule representation.

### World-changing effect

```text
CompatiblePlatform
AND NetworkAvailable
AND MutationPermitted
--InstallROS2-->
ROS2CLIInstalled
```

### Knowledge-changing effect

```text
ROS2CLIInstalled
--ProbeROS2Version-->
Observed(ROS2Distribution = jazzy)
```

Both are effects with:

```text
preconditions
execution semantics
outputs
validation
cost
side effects
```

The difference lies in which state dimension they primarily modify.

This suggests an effect annotation:

```text
effect_kind:
    WORLD
    KNOWLEDGE
    BOTH
```

Examples:

```text
apt install
    WORLD

inspect package.xml
    KNOWLEDGE

compile compatibility test
    BOTH
```

A compile check creates files/processes while primarily producing compatibility evidence.

---

## 9. Claims Should Replace Bare Persistent Booleans

A persistent state such as:

```text
DockerReady = true
```

is too weak.

The architecture should instead retain something like:

```yaml
claim:
  proposition: DockerBackendReady
  value: true
  evidence:
    observer: docker_info_probe
    result_digest: ...
  scope:
    host: workstation-A
    daemon: unix:///var/run/docker.sock
  observed_at: ...
  validity:
    until:
      - daemon_identity_changes
      - host_changes
  provenance:
    provider: docker-provider
    provider_version: ...
```

Then:

```text
DockerBackendReady
```

is computed from currently admissible claims.

This preserves the distinction between:

```text
declared
inferred
assumed
historically observed
currently observed
validated
stale
invalidated
```

The authoritative object is not a timeless Boolean.

It is a justified claim.

---

## 10. A Claim Is Contextual

A proposition can hold relative to a context.

For example:

```text
PackageResolvable(robot_bringup)
```

may be true under:

```text
ROS distro = jazzy
overlay = workspace/install
underlay = /opt/ros/jazzy
architecture = amd64
environment digest = E1
```

and false under another context.

Thus a claim should be interpreted as:

\[
\operatorname{Holds}(P\mid K,A,E,H)
\]

where:

```text
K = evaluation context
A = explicit assumptions
E = supporting evidence
H = validity horizon
```

This avoids promoting context-specific facts into global truths.

---

## 11. Unknown Should Be Refined

A single `UNKNOWN` state is often too coarse.

Suppose the target requires:

```text
CameraOperational
```

There are several importantly different cases.

### Unobserved

The system knows an appropriate observer but has not run it.

```text
UNOBSERVED
```

### Observer Blocked

An observer exists, but its own prerequisites do not currently hold.

```text
OBSERVATION_BLOCKED
```

Example:

```text
ROS topic observer exists
but ROS graph access is unavailable
```

### Evidence Insufficient

An observation was made, but it does not establish the proposition at the required strength.

```text
EVIDENCE_INSUFFICIENT
```

Example:

```text
process exists
```

does not establish:

```text
service healthy
```

### Observer Missing

The proposition is meaningful, but no represented observation rule can distinguish the relevant states.

```text
OBSERVER_MISSING
```

### Provider Ignorance

The current provider does not know how to reason about the proposition.

```text
SEMANTIC_UNKNOWN
```

### Open-World Unknown

The architecture has reached a legitimate boundary where external reality may contain possibilities not represented by current providers.

```text
OPEN_WORLD_UNKNOWN
```

These states should not collapse into one another.

---

## 12. A Better Frontier Classification

A proposition on the current elaboration frontier can be classified along two dimensions:

```text
world status
epistemic status
```

A practical classification might include:

```text
JUSTIFIED
    sufficient current claim exists

REALIZABLE
    no sufficient current claim exists,
    but an executable rule can establish one

OBSERVABLE
    current truth is not sufficiently known,
    but an executable observer can resolve it

CONDITIONAL
    derivable only under explicit unresolved assumptions

OBSERVATION_BLOCKED
    an observer exists but cannot currently execute

EVIDENCE_INSUFFICIENT
    available evidence is weaker than target demands

UNSUPPORTED
    proposition is meaningful but no realization route is represented

OBSERVER_MISSING
    proposition is meaningful but no adequate observation route is represented

INVALID
    target expression has no semantic interpretation

REDESIGN_REQUIRED
    fulfilling the target requires extension of the represented architecture
```

`UNKNOWN` can remain as a user-facing umbrella when detail is unnecessary.

Internally, the distinctions should remain explicit.

---

## 13. Truth, Knowledge, and Reachability Must Not Collapse

For a proposition \(P\), the system should distinguish:

```text
P may actually be true

the system currently has sufficient evidence for P

the system can execute an effect that makes P true

the system can execute an observer that determines whether P is true
```

These are different relations.

One possible notation is:

\[
\operatorname{True}(P)
\]

\[
\operatorname{Justified}(P,S)
\]

\[
\operatorname{CanRealize}(P,S)
\]

\[
\operatorname{CanObserve}(P,S)
\]

The system often cannot directly know \(\operatorname{True}(P)\).

It reasons primarily about justified claims and executable transitions.

This is a useful epistemic discipline.

---

## 14. Conditional Reachability Is Assumption-Carrying Proof Search

Suppose:

```text
ROS2EnvironmentRealized
```

is absent but realizable.

Then the target:

```text
Launch(robot)
```

may remain conditionally reachable.

Represent:

\[
\operatorname{Reachable}(S,T\mid A)
\]

where:

```text
A
```

is a set of unresolved assumptions.

A derived continuation must carry those assumptions explicitly.

For example:

```text
TARGET
    Launch(robot)

ASSUMPTIONS
    ROS2EnvironmentRealized

DERIVED UNDER ASSUMPTIONS
    PackageResolvable(robot)
    LaunchFileResolvable(...)
    ROSGraphObservationAvailable
```

No conditional conclusion may silently enter the current claim set.

Conditional derivation is useful precisely because it does not pretend that assumptions already hold.

---

## 15. Symbolic Speculation Is Partial Evaluation

Conditional elaboration can be interpreted as partial evaluation.

Suppose a rule is:

\[
A\land B\land C\Rightarrow T.
\]

If:

```text
A is justified
B is realizable but not realized
C is unknown
```

then the rule can be partially evaluated into:

```text
assuming B:
    unresolved obligation = C
```

This exposes downstream structure without mutation.

In development environments, this is usually a better first form of speculation than physically constructing candidate worlds.

---

## 16. Isolated Realization Is an Optional Stronger Form

Sometimes symbolic reasoning reaches a boundary.

For example:

```text
Will these transitive packages compile together?
```

may be difficult to answer statically.

The system may then create an isolated candidate world:

```text
temporary container
ephemeral workspace
throwaway build directory
sandbox
remote disposable runner
```

and perform:

```text
candidate realization
→ observation
→ validation
→ discard or commit evidence
```

The result is not automatically authoritative workspace state.

It is evidence generated by an experiment.

This distinction protects the main workspace from speculative mutation.

---

## 17. Rules Should Carry More Than Preconditions

A useful rule schema should include:

```yaml
rule:
  id: ros2-env-via-docker

  concludes:
    - ROS2EnvironmentRealized(context)

  requires:
    - DockerBackendReady(host)
    - CompatibleROSImage(image, distro)
    - BackendCanRepresentResources(context)

  effect:
    kind: WORLD
    implementation: create_ros_container

  validates_with:
    - ros2_cli_probe
    - distro_probe

  invalidated_by:
    - container_removed
    - image_identity_changed
    - backend_identity_changed

  side_effects:
    - creates_container

  cost:
    latency: ...
    mutation: low
    reversibility: high
    network: maybe

  provider:
    id: ros2-provider
    version: ...
```

The exact schema is secondary.

The important point is that a rule is not merely:

```text
requires + command
```

It is an executable, observable, invalidatable contract.

---

## 18. Providers Supply Rule Families

A provider can be defined as a bounded source of semantic rules.

For example:

```text
ROS provider
```

may supply rules about:

```text
command interpretation
package identity
package resolution
launch semantics
generated interfaces
RMW selection
topic observation
node observation
parameter semantics
```

A Docker provider/backend may supply rules about:

```text
image identity
container creation
filesystem mapping
environment mapping
device mapping
network realization
process execution
```

A provider does not need universal knowledge.

It contributes a typed region of the rule space.

---

## 19. Backends Are Effect Realizers

Providers explain domain semantics.

Backends execute effects under concrete operational semantics.

For example:

```text
ROSLaunch(package, file)
```

may eventually produce:

```text
Exec(argv, env, mounts, devices, network)
```

which may be realizable by:

```text
HostBackend
DockerBackend
RemoteBackend
```

The semantic operation remains distinct from its placement.

This separation supports portability without collapsing everything into command strings.

---

## 20. Typed Boundaries Are More Important Than Shared Labels

Suppose one provider produces:

```text
CargoLibraryArtifact(
    format=cdylib,
    architecture=amd64,
    abi=gnu
)
```

and another rule requires:

```text
ROSLoadableNativeLibrary(
    architecture=amd64,
    abi=gnu,
    install_layout=ament
)
```

A generic edge labeled:

```text
output
```

is insufficient.

Composition must establish that the produced representation satisfies the expected type.

Thus provider composition is fundamentally a typed unification problem.

Conceptually:

\[
\operatorname{Produces}(r_1,X)
\]

must unify with:

\[
\operatorname{Requires}(r_2,Y).
\]

Only then should the rules compose.

---

## 21. Interpretation Is Separate From Realization

Consider:

```text
ros2 laaaaaunch robot_bringup ...
```

This may fail before any environmental reasoning.

No semantic production interprets the expression.

That is:

```text
INVALID
```

Now consider:

```text
ros2 launch robot_bringup bringup.launch.py
```

which parses and denotes a meaningful semantic action.

If ROS 2 is absent, this is:

```text
VALID
BUT NOT CURRENTLY REALIZED
```

Now consider:

```text
ROS node in language X
```

which is semantically understandable, but no binding/generator/build integration exists.

That is:

```text
SEMANTICALLY REPRESENTABLE
BUT REALIZATION ARCHITECTURE INCOMPLETE
```

These extension paths are different:

```text
grammar extension
semantic model extension
realization rule extension
observation rule extension
backend extension
```

A useful architecture reports which one is missing.

---

## 22. The Elaborator Is More Compiler-Like Than CPU-Like

A compact target may lower through increasingly explicit forms:

```text
LaunchRobot
    ↓
ROSLaunch(package, launch_file)
    ↓
ROSRuntimeContract(...)
    ↓
Exec(
    argv,
    env,
    filesystem,
    devices,
    network
)
    ↓
BackendProcess(...)
```

This resembles compiler elaboration:

```text
source
→ typed representation
→ elaborated representation
→ lowering
→ target-specific realization
```

The analogy is useful because:

```text
implicit contracts become explicit gradually
types reject invalid composition
lowering is provider-specific
high-level meaning survives multiple implementations
```

The CPU analogy remains useful for:

```text
conditional execution
candidate state
commit boundaries
```

but it should remain secondary.

The development world is open, extensible, distributed, and partially observable.

That makes it unlike a closed instruction set.

---

## 23. The Formal Core Can Be Written Compactly

Let:

\[
\mathcal P
\]

be the set of typed propositions.

Let:

\[
\mathcal R
\]

be the set of rules.

Each rule:

\[
r\in\mathcal R
\]

has:

\[
\operatorname{prem}(r)\subseteq\mathcal P
\]

and:

\[
\operatorname{conc}(r)\in\mathcal P.
\]

Let:

\[
\mathcal C
\]

be the current admissible claim set.

Let:

\[
\mathcal E
\]

be the set of executable effects.

Let:

\[
\mathcal A
\]

be the current explicit assumption set.

Then target elaboration for \(T\) searches for a proof/plan structure:

\[
\Pi(T,\mathcal C,\mathcal A)
\]

such that every leaf obligation is one of:

```text
justified by a current claim
realizable by an executable effect
observable by an executable effect
explicitly assumed
unsupported
architecturally unresolved
```

The planner then chooses which unresolved leaf to advance.

---

## 24. Backward Elaboration Is Rule Expansion

Start with:

\[
F_0=\{T\}.
\]

For each unresolved proposition \(q\), find rules:

\[
R(q)=\{r\in\mathcal R\mid \operatorname{conc}(r)=q\}.
\]

Each rule creates an alternative branch.

For rule \(r\), its premises create conjunctive obligations:

\[
\operatorname{prem}(r)=\{p_1,\ldots,p_n\}.
\]

Thus expansion alternates:

```text
OR over rules
AND over premises
```

until leaves can be classified.

The result is not a complete universal graph.

It is a target-relative proof forest.

---

## 25. Forward Analysis Supplies Executability

Backward reasoning says:

```text
what would justify T?
```

Forward analysis says:

```text
what effects can execute from the currently justified state?
```

The plan exists where the two meet.

Conceptually:

```text
                  target T
                     │
               backward rules
                     │
                     ▼
              required leaves
                     │
                     ×
                     │
              executable effects
                     ▲
                     │
             justified claims
```

The crossing point is the actionable frontier.

---

## 26. The Frontier Is a Cut Through a Proof Forest

In a simple tree, a frontier is easy to visualize.

In an AND/OR proof forest, the frontier should be understood as a cut separating:

```text
already justified structure
```

from:

```text
unresolved obligations
```

A frontier may contain propositions from several alternative routes.

Some routes may already be dominated by cheaper or safer alternatives and can be pruned.

Thus the displayed frontier need not equal every unresolved leaf in the full search space.

It can be a policy-filtered frontier.

---

## 27. Route Search Must Be Policy-Aware

A realization route is not optimal merely because it uses fewer steps.

Possible costs include:

```text
execution time
host mutation
network access
privilege
irreversibility
resource consumption
monetary cost
security exposure
user disruption
uncertainty
expected information gain
```

Define a route cost:

\[
C(\pi)=
w_tT(\pi)
+w_mM(\pi)
+w_rR(\pi)
+w_nN(\pi)
+w_iI(\pi)
-\;w_gG(\pi)
\]

where:

```text
T = time/latency
M = mutation cost
R = operational risk
N = network/external dependence
I = irreversibility
G = expected information gain
```

The exact scalarization may be inappropriate in some systems.

A Pareto frontier may be better.

The key requirement is that policy must be explicit.

---

## 28. Observation Has Value Because It Can Eliminate Routes

Suppose two realization routes exist.

Route A:

```text
install large dependency set
→ build
→ launch
```

Route B:

```text
use already-present remote service
→ launch client
```

but whether the remote service exists is unknown.

A cheap observation:

```text
probe remote endpoint
```

may eliminate the expensive route entirely.

Thus observation actions can have high expected value even when they do not directly change the target world state.

The planner should compare:

```text
cost of knowing
```

against:

```text
cost of acting under uncertainty
```

This is one reason information gain belongs in route selection.

---

## 29. Evidence Strength Should Be Target-Relative

Suppose the target requires:

```text
ServiceHealthy
```

Available evidence may include:

```text
PID exists
port open
HTTP 200
health endpoint reports ready
domain transaction succeeds
```

These are not equivalent.

A target:

```text
ProcessStarted
```

may be satisfied by PID existence.

A target:

```text
ServiceReadyForTraffic
```

may require the health endpoint.

A target:

```text
RobotRespondingCorrectly
```

may require a domain-level interaction.

Thus evidence strength is relative to the proposition being justified.

The architecture should avoid a universal concept of "healthy."

---

## 30. Observation Contracts Need Temporal Semantics

Dynamic propositions decay.

Examples:

```text
DeviceConnected
NetworkReachable
CredentialValid
TopicPublishing
ServiceResponsive
ResourceAvailable
```

An observation should therefore include:

```text
observed_at
observation_window
freshness_threshold
scope
sampling policy
invalidators
```

For example:

```yaml
claim:
  proposition: TopicPublishing(/scan, min_rate=5Hz)
  value: true
  observed_at: 13:20:14
  observation_window: 2s
  valid_for: 5s
  scope:
    ros_domain_id: 7
    network_namespace: container-A
```

A historical observation must not silently become present truth.

---

## 31. Invalidation Is a Rule Over Claims

A claim may cease to be admissible when its dependencies change.

For example:

```text
BuildCurrent(source_digest=S1)
```

may be invalidated by:

```text
source_digest != S1
dependency_lock changed
toolchain identity changed
generator state changed
```

Rather than directly deleting arbitrary state, invalidation can be represented as a relation:

\[
\operatorname{Valid}(c,S)
\]

computed against the current context.

This allows the provenance record to remain historically available while preventing stale evidence from justifying current conclusions.

---

## 32. Persistent State Should Be Smaller Than the Virtual Rule Space

The full AND/OR space can be enormous.

It should not be materialized eagerly.

Persist mostly:

```text
workspace identity
user declarations
provider configuration
locks
artifact identities
expensive observations
claims
provenance
known failures
```

Generate on demand:

```text
target-relative rule expansions
conditional continuations
route alternatives
frontier nodes
dominator relations
observation obligations
```

Thus:

```text
persistent claims
+
provider rules
+
backend rules
+
current observations
+
target
↓
query-specific proof forest
```

The durable system remembers evidence and architecture.

It need not remember every hypothetical graph node.

---

## 33. Reopenable Abstractions Become Cached Lemmas

Suppose repeated elaborations establish a stable proposition:

```text
ROS2_JAZZY_ROBOT_HW_READY(workspace)
```

with strong provenance.

Future targets can use it as a relative primitive.

In proof terms, it behaves like a cached lemma.

The system does not need to reopen:

```text
distro
overlay
interfaces
middleware
permissions
devices
```

unless:

```text
the claim becomes invalid
the target demands stronger evidence
a failure contradicts the abstraction
a hidden distinction becomes relevant
```

This gives a principled interpretation of semantic zoom.

---

## 34. Successful Elaborations Compress Future Search

Repeated successful routes provide reusable structure.

A successful route can persist:

```text
target proposition
selected rule path
assumptions discharged
effects executed
observations obtained
artifacts produced
provider/backend versions
claim validity dependencies
```

Later elaboration can reuse this as a higher-level rule or cached proof.

Thus the system gradually converts expensive reasoning into reusable relative primitives.

This is a form of architectural learning without requiring machine learning.

---

## 35. Failure Also Produces Rules

Suppose an isolated build establishes:

```text
PackageVersion(vision_stack, 3.1)
AND ROSDistro(jazzy)
→ CompileFailure(reason=ABIConflict)
```

This is not useless history.

It can become a negative constraint.

Future plans can prune equivalent routes.

Examples of persistent negative knowledge:

```text
image digest X cannot execute on arm64
backend B cannot expose required realtime capability
package P conflicts with distro D
launch file L requires device class H
observer O cannot establish proposition Q
```

A mature elaborator remembers impossibility boundaries.

---

## 36. Negative Knowledge Needs Scope Too

Failure facts should not become universal prohibitions.

For example:

```text
ImageXCannotRun
```

is too coarse.

Prefer:

```text
ImageExecutable(
    image=X,
    architecture=arm64,
    kernel_features=K,
    backend=B
) = false
```

with evidence and provenance.

A later backend or rebuilt image may make the proposition true.

Negative claims need the same contextual discipline as positive claims.

---

## 37. Counterfactual Queries Are First-Class

Once conditional elaboration exists, the system can answer:

```text
What becomes reachable if I satisfy X?
```

This is often more useful than:

```text
Why am I blocked?
```

For example:

```text
IF ROS2EnvironmentRealized:
    PackageResolvable becomes observable
    LaunchFileResolvable becomes observable
    ROSGraphAccess becomes realizable

IF CameraDeviceAvailable:
    hardware branch advances
    target still remains blocked by ROS environment
```

This reveals leverage.

It also helps compare candidate next actions before executing them.

---

## 38. Next-Step Selection Should Be Route-Sensitive

A simplistic next-step rule might select:

> the unresolved proposition that dominates the target.

That remains useful, but must be interpreted over the active AND/OR route space.

A better procedure is:

```text
1. enumerate currently competitive target routes
2. prune routes violating hard policy
3. identify unresolved obligations shared by many remaining routes
4. estimate effect and observation costs
5. prefer actions that:
       advance at least one competitive route
       eliminate many alternatives
       reduce uncertainty
       remain reversible where possible
```

This generalizes dominator-based guidance.

---

## 39. High-Leverage Actions Can Be Shared Across Alternatives

Suppose:

```text
Route A requires NetworkAvailable + DockerReady
Route B requires NetworkAvailable + RemoteBackendReady
Route C requires OfflineCacheAvailable
```

`NetworkAvailable` does not dominate the target because Route C bypasses it.

But if Route C is expensive or unsupported under current policy, `NetworkAvailable` may dominate the competitive route set.

Thus leverage is policy-relative.

This is another reason the planner should expose its assumptions and route pruning decisions.

---

## 40. Explanations Should Be Proof-Carrying

A suggested action should include enough structure to answer:

```text
Why this action?
What does it assume?
What can it change?
What will count as success?
What becomes possible afterward?
What would invalidate the result?
```

Example:

```text
ACTION
    Realize ROS2Environment via Docker

WHY
    lies on both currently competitive routes to Launch(robot)
    removes the largest shared unresolved prerequisite

PRECONDITIONS
    DockerBackendReady
    CompatibleROSImage
    device mapping policy permits requested devices

EXPECTED POSTCONDITION
    ROS2EnvironmentRealized(context=C1)

VALIDATE WITH
    ros2 CLI probe
    distro identity probe

SIDE EFFECTS
    creates disposable container

COUNTERFACTUAL VALUE
    package resolution becomes observable
    launch-file resolution becomes observable

INVALIDATED BY
    container deletion
    image identity change
```

This is substantially stronger than:

```text
run docker ...
```

---

## 41. The Deep Interface Is an Elaborator, Not a Runner

A useful interface is:

```text
$ wsx elaborate "launch robot bringup"
```

Possible output:

```text
TARGET
    ROSLaunch(robot_bringup, bringup.launch.py)

INTERPRETATION
    valid

COMPETITIVE ROUTES
    A: host ROS 2
    B: Docker ROS 2

JUSTIFIED
    source workspace present
    Docker backend ready

UNRESOLVED SHARED OBLIGATION
    package source must be discoverable

ROUTE A BLOCKER
    HostROS2Installed

ROUTE B REALIZABLE
    CompatibleROSImage

EPISTEMIC FRONTIER
    CameraOperational
        UNOBSERVED
        observer: device-open probe

NEXT ACTION
    probe camera device

WHY
    cheap knowledge gain
    may invalidate the entire hardware launch route before environment mutation
```

The system is explaining the target's continuation space.

Execution is optional.

---

## 42. A Separate Interface Can Ask for the Proof Forest

For expert users:

```text
$ wsx elaborate --explain-rules target-X
```

could expose:

```text
T
├── rule r1
│   ├── A
│   ├── B
│   └── C
│
└── rule r2
    ├── D
    └── E
```

with leaf states:

```text
A JUSTIFIED
B REALIZABLE
C UNOBSERVED
D UNSUPPORTED
E JUSTIFIED
```

This makes alternatives explicit and debuggable.

---

## 43. A Separate Interface Can Ask Only for Epistemic Debt

For example:

```text
$ wsx evidence target-X
```

could report:

```text
REQUIRED BUT NOT JUSTIFIED

CameraOperational
    state: UNOBSERVED
    observer: device_open_probe
    cost: low

FirmwareCompatible
    state: OBSERVER_MISSING
    suggested extension:
        firmware_version_probe

ServiceHealthy
    state: EVIDENCE_INSUFFICIENT
    current evidence:
        process exists
    stronger evidence required:
        health endpoint
```

This turns uncertainty into concrete engineering work.

---

## 44. A Separate Interface Can Ask Only for Non-Mutating Futures

For example:

```text
$ wsx speculate deploy
```

could produce:

```text
ASSUME
    RegistryReachable
    DockerBackendReady

DERIVE
    image build route exists
    OCI publication route exists
    Kubernetes handoff requires RuntimeContract

MISSING
    target architecture
    health semantics
    external secret declaration

MUTATION
    none
```

This interface supports design work before execution.

---

## 45. The System Should Distinguish Hard Constraints From Preferences

Some route conditions are mandatory:

```text
architecture compatibility
ABI compatibility
required device access
semantic validity
```

Others are preferences:

```text
avoid host mutation
prefer cached artifacts
avoid network
prefer reversible operations
minimize latency
```

The planner should not encode preferences as if they were truth conditions.

Represent:

```text
hard constraints
policy constraints
optimization preferences
```

separately.

Otherwise planning choices become difficult to explain.

---

## 46. Policy Is Part of Planning Context, Not Provider Truth

A provider may know:

```text
host installation can realize ROS2Environment
```

A policy may say:

```text
do not mutate host packages
```

The provider rule remains valid.

The planner simply excludes that route under the current policy.

This prevents organizational or user preferences from contaminating semantic knowledge.

---

## 47. Target Interpretation May Produce Multiple Semantic Candidates

Natural-language or ambiguous CLI input may admit multiple interpretations.

For example:

```text
run camera
```

could mean:

```text
launch camera driver
execute camera test
open camera viewer
start camera service
```

The interpreter may produce candidates:

\[
T_1,T_2,\ldots,T_n.
\]

These should carry confidence or ambiguity information.

However, once a semantic target is selected, downstream rule reasoning should remain deterministic where possible.

AI can assist interpretation.

It should not silently fabricate realization rules.

---

## 48. AI Fits at Open Semantic Boundaries

AI can help with:

```text
mapping vague intent to candidate propositions
extracting candidate rules from documentation
explaining proof forests
suggesting missing observations
suggesting provider extensions
ranking plausible interpretations
```

But candidate AI-produced rules should be typed as:

```text
PROPOSED
UNVERIFIED
```

until validated by:

```text
documentation
tests
provider authorship
execution evidence
```

This preserves the distinction between reasoning assistance and architectural truth.

---

## 49. The First Prototype Should Test One Hypothesis

The full architecture supports many advanced ideas.

The first prototype should test a narrower claim:

> Can backward AND/OR elaboration expose useful second and third blockers before the first blocker is physically removed?

This can be tested without implementing:

```text
learned primitives
distributed provenance
isolated speculation
deployment adapters
AI-generated rules
rich persistent graphs
advanced route optimization
```

The first system only needs enough machinery to demonstrate anticipatory guidance.

---

## 50. Minimal Prototype Kernel

A first engine can implement:

```text
1. typed propositions

2. typed AND/OR rules

3. current claims

4. rule expansion from a target

5. leaf classification:
       JUSTIFIED
       REALIZABLE
       OBSERVABLE
       CONDITIONAL
       UNSUPPORTED

6. one effect backend

7. observation effects

8. explicit assumptions

9. simple route cost

10. re-elaboration after every effect
```

This is sufficient to test the central interaction model.

---

## 51. A Minimal Data Model

For example:

```yaml
proposition:
  type: PackageResolvable
  args:
    package: robot_bringup
    context: ros_ctx_1
```

A rule:

```yaml
rule:
  id: package-resolvable-from-index

  concludes:
    type: PackageResolvable
    args:
      package: $package
      context: $context

  requires:
    - type: ROSPackageIndexAvailable
      args:
        context: $context

    - type: PackageIndexed
      args:
        package: $package
        context: $context
```

A claim:

```yaml
claim:
  proposition:
    type: ROSPackageIndexAvailable
    args:
      context: ros_ctx_1

  value: true

  evidence:
    observer: ament_index_probe

  observed_at: ...

  valid_relative_to:
    environment_digest: E7
```

An effect:

```yaml
effect:
  id: probe-ament-index

  requires:
    - ROS2EnvironmentRealized($context)

  produces_evidence_for:
    - ROSPackageIndexAvailable($context)

  implementation:
    backend: exec
    argv: [...]
```

This is enough for a meaningful prototype.

---

## 52. Rule Expansion Can Stay Lazy

Pseudo-algorithm:

```text
function elaborate(target, claims, assumptions):
    open := [target]
    forest := empty

    while open not empty:
        q := choose(open)

        if justified(q, claims):
            mark q JUSTIFIED
            continue

        rules := rules_concluding(q)

        if rules empty:
            classify q from available effects/providers
            continue

        for r in rules:
            add OR alternative r under q

            for p in premises(r):
                if p in assumptions:
                    mark p ASSUMED
                else:
                    add p to open

    return forest
```

No universal graph is required.

Only target-relevant structure is opened.

---

## 53. Classification Can Use Executability

For an unresolved proposition \(q\):

```text
if sufficient claim exists:
    JUSTIFIED

else if executable realization effect exists:
    REALIZABLE

else if executable observation effect exists:
    OBSERVABLE

else if realization exists but requires unresolved assumptions:
    CONDITIONAL

else if observer exists but cannot execute:
    OBSERVATION_BLOCKED

else if semantic rules exist but no realization route:
    UNSUPPORTED

else:
    SEMANTIC_UNKNOWN
```

The exact ordering should be domain-aware.

The important property is that classification is explainable.

---

## 54. Re-Elaboration After Each Action Is Simpler Than Maintaining Perfect Incrementality

A prototype does not need a sophisticated incremental theorem engine.

After an effect:

```text
execute
→ collect observations
→ validate
→ update claims
→ invalidate affected claims
→ elaborate target again
```

Because the graph is target-relative and mostly virtual, re-elaboration can be cheap enough initially.

Incremental optimization can come later.

---

## 55. ROS 2 + Container + Hardware Is a Good Stress Case

Consider target:

```text
ROSLaunch(robot_bringup, hardware.launch.py)
```

Candidate rules may require:

```text
ROS2EnvironmentRealized
PackageResolvable(robot_bringup)
LaunchFileResolvable(robot_bringup, hardware.launch.py)
RuntimeDependenciesSatisfied(robot_bringup)
CameraOperational
DDSConnectivitySufficient
```

The environment route may be:

```text
HostROS2Route
OR DockerROS2Route
```

The camera proposition may elaborate into:

```text
DeviceNodeExists
AND DeviceOpenable
AND DriverCompatible
```

The DDS proposition may elaborate differently depending on backend placement.

This one target forces:

```text
grammar
package semantics
alternative realization
environment scoping
device access
permissions
network semantics
observation
temporal evidence
```

It is difficult enough to falsify weak models quickly.

---

## 56. Worked Example: Initial State

Suppose current claims establish:

```text
WorkspacePresent
DockerBackendReady
SourceContainsPackage(robot_bringup)
```

but do not establish:

```text
HostROS2Installed
CameraOperational
CompatibleROSImageAvailable
```

Target:

```text
ROSLaunch(robot_bringup, hardware.launch.py)
```

Backward expansion yields:

```text
ROSLaunch(...)
AND
├── ROS2EnvironmentRealized
├── PackageResolvable(robot_bringup)
├── LaunchFileResolvable(...)
├── RuntimeDependenciesSatisfied(...)
└── CameraOperational
```

Now expand the environment:

```text
ROS2EnvironmentRealized
OR
├── HostROS2Route
└── DockerROS2Route
```

The Docker route:

```text
DockerROS2Route
AND
├── DockerBackendReady
├── CompatibleROSImageAvailable
└── RequiredDeviceMappingRepresentable
```

Already, the elaborator can see beyond the missing environment.

---

## 57. Worked Example: Independent Observation

Even before realizing ROS 2, the system may know how to probe:

```text
CameraOperational
```

through:

```text
DeviceNodeExists
→ DeviceOpenable
→ optional domain probe
```

Suppose:

```text
/dev/video0 does not exist
```

The system can report:

```text
TARGET
    ROSLaunch(robot_bringup, hardware.launch.py)

ENVIRONMENT
    Docker route potentially realizable

INDEPENDENT BLOCKER
    CameraOperational = false
    evidence: device enumeration

CONSEQUENCE
    target remains impossible even if ROS 2 environment is realized
```

This is the central payoff.

The system discovered a later blocker before paying the cost of removing the first one.

---

## 58. Worked Example: Conditional Downstream Structure

Assume instead the camera exists.

The system may derive:

```text
ASSUME ROS2EnvironmentRealized(context=C)

THEN
    package resolution becomes observable
    launch file resolution becomes observable
    rosdep closure becomes computable
    ROS graph probes become available
```

This conditional structure is useful even though no container has yet been created.

It supports planning.

---

## 59. Worked Example: Selecting Between Observation and Mutation

Candidate action A:

```text
Create ROS 2 container
cost:
    mutation: low
    time: medium
    information gain: medium
```

Candidate action B:

```text
Probe camera permissions
cost:
    mutation: none
    time: low
    information gain: high
```

If camera permissions are required by all competitive routes, B may be the better next action.

A linear command runner would likely attempt A first.

A goal-directed elaborator can prefer B.

---

## 60. Worked Example: Validation

Suppose the system creates the ROS container successfully.

That effect does not automatically justify:

```text
ROS2EnvironmentRealized
```

The rule declares validation:

```text
ros2 CLI executable
distribution identity matches required distro
package index reachable
```

Only after those observations should the claim be committed.

Thus:

```text
effect success
≠ semantic postcondition success
```

This is a critical invariant.

---

## 61. Worked Example: Reopening an Abstraction

Later, the system has a cached claim:

```text
DockerExecReady
```

A new target requires GPU access.

The old abstraction may be insufficient.

It reopens into:

```text
daemon available
runtime supports GPU
required device nodes visible
container runtime configured
driver compatibility established
```

The abstraction is not discarded.

It is refined only because the target requires hidden distinctions.

---

## 62. The Main Failure Mode Is Ontology Expansion

A framework this expressive invites premature modeling.

The system may attempt to define:

```text
every package
every environment variable
every OS feature
every device state
every deployment object
every possible command
```

This would destroy the target-relative economy.

The correct discipline is:

```text
do not model a distinction until a rule or target requires it
```

Providers should expose lazily expandable semantics.

---

## 63. Another Failure Mode Is Rule Collapse Into Commands

A rule such as:

```yaml
realize:
  command: "apt install ..."
```

is insufficient if it lacks:

```text
semantic conclusion
preconditions
validation
scope
invalidators
side effects
```

Otherwise the architecture degenerates into a command catalog.

The command is an implementation detail of an effect.

It is not the semantic contract.

---

## 64. Another Failure Mode Is Treating Successful Execution as Proof

Examples:

```text
docker build exited 0
```

does not imply:

```text
RuntimeHealthy
```

```text
process started
```

does not imply:

```text
ServiceReady
```

```text
topic exists
```

does not imply:

```text
TopicPublishingAtRequiredRate
```

Validation must match the target proposition.

---

## 65. Another Failure Mode Is Hiding Alternative Routes

If the planner silently chooses Docker over host installation, the user loses important information.

A useful explanation should distinguish:

```text
represented alternatives
eliminated alternatives
policy-pruned alternatives
selected alternative
```

This is especially important when routes differ in:

```text
mutation
privilege
network dependence
reversibility
cost
```

---

## 66. Another Failure Mode Is Treating Missing Knowledge as False

If no observation establishes:

```text
CameraOperational
```

the system must not store:

```text
CameraOperational = false
```

Likewise it must not store:

```text
CameraOperational = true
```

because a camera process exists.

The architecture should preserve epistemic uncertainty until an adequate observer resolves it.

---

## 67. Another Failure Mode Is Overusing the CPU Analogy

The CPU analogy can clarify:

```text
typed operations
dependency structure
speculation
commit boundaries
```

But it can also encourage misleading assumptions:

```text
closed world
complete instruction semantics
deterministic hardware state
centralized execution
precise fault model
```

Development ecosystems do not have these properties.

The core formal description should therefore stand without the analogy.

The analogy should remain pedagogical.

---

## 68. A Better Headline Description

The architecture can be described as:

> a goal-directed elaborator over an open, typed, partially observable AND/OR rule system.

Or more operationally:

> a system that turns a desired development proposition into an executable, evidence-backed proof plan.

These descriptions emphasize the core behavior without depending on a hardware metaphor.

---

## 69. Relationship to Build Systems

Build systems already implement a restricted version of this architecture.

They reason about:

```text
targets
dependencies
producibility
incrementality
invalidations
artifacts
```

But their proposition language is usually narrower.

A speculative capability elaborator generalizes the idea beyond build artifacts to:

```text
runtime environments
services
devices
middleware state
deployment contracts
observations
health evidence
```

The build-system analogy is therefore structurally strong.

---

## 70. Relationship to Logic Programming

Logic programming contributes:

```text
goal-directed search
rules
unification
backward chaining
alternative clauses
```

But a development elaborator must additionally model:

```text
effects
side effects
cost
time
freshness
invalidation
external observation
partial provider knowledge
```

Thus it is not merely a Prolog engine.

It is effectful, temporal, and open-world.

---

## 71. Relationship to Automated Planning

Automated planning contributes:

```text
actions
preconditions
effects
costs
goal states
```

But a capability elaborator places unusually strong emphasis on:

```text
semantic interpretation
typed provider boundaries
evidence
observation
provenance
conditional elaboration without mutation
```

It combines planning with epistemic reasoning.

---

## 72. Relationship to Active Diagnosis

When an unknown proposition blocks a target, the system asks:

```text
which observation best distinguishes the remaining possibilities?
```

This resembles active diagnosis.

For example:

```text
ServiceUnavailable
```

could result from:

```text
process absent
port binding failure
network namespace mismatch
credential failure
dependency unavailable
```

Instead of executing repairs blindly, the planner can choose a discriminating observation.

This is a major potential advantage over linear troubleshooting.

---

## 73. Observation Planning May Eventually Use Expected Information Gain

Suppose hypotheses are:

```text
H1: device absent
H2: device permission denied
H3: driver mismatch
```

Candidate observations:

```text
enumerate device
attempt open
inspect driver
```

A future planner could estimate which observation most reduces uncertainty per unit cost.

The first implementation does not need probabilistic inference.

A deterministic heuristic is enough:

```text
prefer cheap observations that partition many remaining routes
```

This captures much of the practical value.

---

## 74. The System Should Be Able to Explain Its Ignorance

A high-quality response is not merely:

```text
UNKNOWN
```

It should say:

```text
UNKNOWN BECAUSE
    proposition is meaningful
    no admissible claim currently justifies it
    observer O could resolve it
    observer O requires prerequisite P
    P is currently blocked
```

Or:

```text
UNKNOWN BECAUSE
    current provider has no observation rule for this proposition
```

This turns uncertainty into navigable structure.

---

## 75. Architectural Redesign Should Also Be Typed

`REDESIGN_REQUIRED` is too broad unless qualified.

Possible redesign classes include:

```text
GRAMMAR_EXTENSION
SEMANTIC_PROVIDER_EXTENSION
REALIZATION_RULE_EXTENSION
BACKEND_EXTENSION
OBSERVATION_EXTENSION
TYPE_BRIDGE_EXTENSION
ARTIFACT_CONTRACT_EXTENSION
```

This allows the system to explain where the architecture ends.

---

## 76. Provider Boundaries Should Be Explicitly Open-World

A provider should be able to state:

```text
I understand proposition family X
I can elaborate these rules
I can observe these predicates
I do not claim completeness outside this region
```

Unsupported should mean:

```text
unsupported by the represented architecture
```

not:

```text
impossible in reality
```

This distinction is essential in fast-changing development ecosystems.

---

## 77. Rule Provenance Matters

A rule may originate from:

```text
provider source code
tool documentation
workspace declaration
generated manifest
user declaration
validated learned rule
AI proposal
```

These should not all carry equal authority.

Rule provenance can support trust levels such as:

```text
AUTHORITATIVE
DECLARED
DISCOVERED
INFERRED
PROPOSED
```

A planner may use weaker rules for exploration while refusing to commit strong claims from them without validation.

---

## 78. Claims and Rules Have Different Trust Semantics

A rule says:

```text
if premises hold, this conclusion is expected under this contract
```

A claim says:

```text
this proposition is currently justified in this context
```

Rule trust and claim evidence should remain separate.

A perfectly authoritative rule may have unsatisfied premises.

A strongly observed claim may concern a proposition whose realization rule is unknown.

The architecture should preserve both dimensions.

---

## 79. Commit Is Admission Into the Current Claim Set

After an effect:

```text
candidate outputs
```

are not automatically authoritative.

Validation produces evidence.

The system then decides whether the evidence is sufficient to admit a claim.

Conceptually:

\[
\text{Effect}
\rightarrow
\text{Observation}
\rightarrow
\text{Validation}
\rightarrow
\text{Claim Admission}.
\]

"Commit" can therefore be defined precisely as:

> admitting a new evidence-backed claim into the current reasoning state.

This is cleaner than treating commit as generic persistence.

---

## 80. Persistence and Admission Are Different

A failed experiment may still be persisted historically:

```text
compile failed under context C
```

without admitting:

```text
PackageIncompatible
```

as a general current claim.

Likewise, an old health observation may remain in provenance while no longer being admissible for current reasoning.

Thus:

```text
persistent record
≠ currently admissible claim
```

This distinction helps prevent stale-state bugs.

---

## 81. The Planner Can Operate Over Admissible Claims Only

Define:

\[
\mathcal C^\star(S)
\]

as the claims admissible under current state \(S\).

A claim may be excluded because:

```text
expired
invalidated
wrong scope
assumptions no longer hold
provider version changed
artifact identity changed
```

Elaboration should use:

\[
\mathcal C^\star(S)
\]

rather than every historical claim in storage.

This creates a clean boundary between provenance database and reasoning state.

---

## 82. A Target May Require Stronger Claims Than Existing Ones

Suppose a cached claim establishes:

```text
ROS2Available
```

but a new target requires:

```text
ROS2EnvironmentRealized(
    distro=jazzy,
    rmw=cyclonedds,
    device=/dev/video0
)
```

The weaker claim cannot simply be reused as sufficient evidence.

The target forces refinement.

This is another form of reopenable abstraction.

---

## 83. Semantic Zoom Can Be Defined Through Proof Sufficiency

An abstraction may remain closed when its claim is sufficient to discharge the current obligation.

It reopens when it is not.

Thus semantic zoom can be stated as:

> expand a proposition only when existing claims do not discharge the target-relative obligation at the required type and evidence strength.

This makes "zoom" a reasoning operation rather than a UI metaphor.

---

## 84. The Target Determines Evidence Granularity

For:

```text
ListROSPackages
```

evidence that:

```text
ros2 CLI exists
package index accessible
```

may suffice.

For:

```text
LaunchHardwareRobot
```

the same `ROS2Available` abstraction may be insufficient.

The system may need:

```text
RMW compatibility
network namespace
device permissions
generated interface availability
hardware state
```

The target determines how much of the lower structure must be exposed.

---

## 85. Deployment Is a Useful Downstream Constraint Generator

A target:

```text
Deploy(image X via Kubernetes)
```

can push obligations backward:

```text
PublishedOCIArtifact(X)
RuntimeContractExplicit(X)
PlatformCompatible(X)
HealthSemanticsDeclared(X)
ExternalResourcesDeclared(X)
```

The deployment provider need not own application construction.

It contributes constraints that upstream rules must satisfy.

This is an important composition pattern:

```text
downstream consumer
→ backward contract obligations
→ upstream artifact elaboration
```

---

## 86. Runtime Closure Is Better Understood as Explicit Boundary Conditions

"Self-contained image" is often misleading.

A runtime artifact may legitimately depend on:

```text
database
secret
device
GPU
network endpoint
volume
credential
kernel capability
```

Runtime closure should mean:

> every dependency relevant to downstream realization is either represented inside the artifact or declared in its runtime contract.

This transforms hidden assumptions into explicit propositions.

---

## 87. The Architecture Can Stop Lowering Early

Ultimately:

```text
ROSLaunch
→ process
→ syscall
→ machine instruction
→ hardware transition
```

But the elaborator should stop once the current target's obligations are discharged by a stable lower-level contract.

If:

```text
ExecReady
```

is sufficient, do not inspect syscalls.

If:

```text
GPUCapability
```

matters, reopen lower hardware distinctions.

This is another target-relative economy principle.

---

## 88. The Core Engine Can Remain Small

A practical core can expose:

```text
interpret
unify
expand
classify
search
observe
execute
validate
admit
invalidate
explain
```

Providers contribute domain semantics.

Backends contribute effect execution.

Persistence stores claims and provenance.

Policy configures route selection.

The core should not contain ROS, Docker, Cargo, Kubernetes, or cloud-specific logic.

---

## 89. Suggested Implementation Sequence

A disciplined implementation sequence is:

```text
1. Define proposition typing and unification.

2. Define AND/OR rule representation.

3. Define claims with scope, evidence, and validity.

4. Implement lazy backward expansion.

5. Implement current-claim discharge.

6. Implement one effect backend.

7. Implement REALIZABLE and OBSERVABLE classification.

8. Implement explicit assumptions and CONDITIONAL derivation.

9. Implement route enumeration with simple costs.

10. Implement one observation family.

11. Implement validation and claim admission.

12. Implement invalidation.

13. Add policy-aware route pruning.

14. Add stronger epistemic classification.

15. Add isolated speculative realization.

16. Add provider composition across typed boundaries.

17. Add cached relative primitives.

18. Add deployment-induced backward constraints.

19. Only later add richer AI assistance or probabilistic information gain.
```

This sequence validates the kernel before expanding the ecosystem.

---

## 90. A Strong First Demonstration

A convincing demonstration would compare two systems.

### Linear execution

```text
1. attempt ros2 launch
2. fail because ros2 missing
3. install/realize ROS 2
4. retry
5. fail because package unresolved
6. repair overlay
7. retry
8. fail because camera absent
```

### Goal-directed elaboration

```text
TARGET
    launch hardware robot

BEFORE MUTATION
    ROS environment missing but Docker-realizable
    package source found
    package resolution conditional on ROS environment
    camera independently observable

OBSERVE CAMERA
    absent

CONCLUSION
    target cannot currently succeed
    realizing ROS environment now would not remove the hardware blocker
```

If the second system reliably prevents unnecessary work, the architecture has demonstrated practical value.

---

## 91. Evaluation Metrics

A prototype can be evaluated by:

```text
number of blockers exposed before first mutation

number of unnecessary actions avoided

fraction of suggested actions with explicit justification

fraction of committed claims with adequate validation

stale-claim rate

unsupported-vs-impossible classification accuracy

route explanation completeness

provider-specific code outside the core

graph materialization size relative to target scope
```

These metrics test architectural claims rather than aesthetic qualities.

---

## 92. A Useful Benchmark Family

Create targets with deliberately layered blockers:

```text
Target A
    blocker at environment layer
    blocker at package layer
    blocker at device layer

Target B
    two alternative realization routes
    one cheaper route hidden behind an observation

Target C
    successful process start
    failed health validation

Target D
    stale cached claim
    changed dependency lock

Target E
    semantically valid target
    missing observer

Target F
    provider understands target
    no realization rule exists
```

A capable elaborator should classify these differently.

---

## 93. The Most Important Invariants

The architecture should maintain these invariants:

### No conditional truth promotion

```text
assumed P
```

must never become:

```text
current justified P
```

without realization or evidence.

### No execution-proof collapse

```text
effect returned success
```

must not automatically establish the semantic postcondition.

### No observation-false collapse

```text
not observed
```

must not become:

```text
false
```

### No historical-current collapse

```text
was observed
```

must not become:

```text
currently justified
```

without validity.

### No provider-world collapse

```text
provider has no rule
```

must not become:

```text
impossible in reality
```

### No policy-semantics collapse

```text
route disallowed by policy
```

must not become:

```text
route semantically invalid
```

These invariants are more important than any particular graph representation.

---

## 94. Compact Formal Summary

A minimal speculative capability elaborator can be defined as:

\[
\mathfrak G=
(\mathcal P,\mathcal R,\mathcal C,\mathcal E,\mathcal V,\mathcal K)
\]

where:

```text
P
    typed propositions

R
    AND/OR derivation and realization rules

C
    evidence-bearing claims

E
    executable effects

V
    claim validity and invalidation semantics

K
    planning context:
        assumptions
        policy
        costs
        provider/backend availability
```

Given target \(T\), the engine:

\[
T
\xrightarrow{\text{interpret}}
P_T
\]

then lazily constructs an AND/OR proof forest:

\[
\Phi(P_T)
\]

intersects it with admissible claims:

\[
\mathcal C^\star
\]

classifies unresolved leaves, searches executable realization and observation effects, and selects a route under policy.

Execution produces candidate evidence:

\[
E_i
\]

which is validated before new claims are admitted.

The loop is:

\[
\boxed{
\text{target}
\rightarrow
\text{elaborate}
\rightarrow
\text{classify}
\rightarrow
\text{choose effect}
\rightarrow
\text{execute/observe}
\rightarrow
\text{validate}
\rightarrow
\text{admit claims}
\rightarrow
\text{re-elaborate}
}
\]

---

## 95. Central Principles

### Goal-Directed Structure Principle

> Open only the semantic distinctions required to justify the requested target.

### Minimal-Kernel Principle

> Keep the reasoning core small; derive higher-level concepts from typed propositions, rules, claims, and effects where possible.

### AND/OR Elaboration Principle

> Alternative realization rules are OR branches; the premises of each selected rule are AND obligations.

### Route-Relative Requirement Principle

> A proposition does not have one universal prerequisite list; its requirements depend on the selected realization rule.

### Evidence-Bearing State Principle

> Persistent reasoning state should consist primarily of contextual, evidence-backed claims rather than bare Boolean facts.

### Epistemic Separation Principle

> Truth, justified belief, realizability, and observability are different relations.

### Refined-Unknown Principle

> Distinguish unobserved state, blocked observation, insufficient evidence, missing observers, provider ignorance, and open-world uncertainty.

### Conditional-Proof Principle

> Continue elaboration under explicit assumptions, but never promote assumption-dependent conclusions into current truth.

### Effect-Separation Principle

> Effects may change the world, knowledge, or both; the planner should reason about these consequences explicitly.

### Validation-Before-Admission Principle

> An effect's successful execution does not justify its semantic postcondition until required validation evidence exists.

### AND/OR Frontier Principle

> The current frontier is a policy-relative cut through a target-specific proof forest, not merely the leaves of a fixed dependency graph.

### Explicit-Policy Principle

> Separate semantic validity, hard constraints, route policy, and optimization preferences.

### Typed-Composition Principle

> Provider outputs compose only when their semantic types and contextual contracts unify.

### Open-World Provider Principle

> Missing provider knowledge means unsupported by the represented architecture, not impossible in reality.

### Reopenable-Lemma Principle

> Stable capabilities may act as cached lemmas until a target requires distinctions hidden by the abstraction.

### Counterfactual-Leverage Principle

> The planner should explain not only why a target is blocked, but what becomes reachable if a candidate prerequisite is satisfied.

### Observation-Value Principle

> Prefer cheap observations when they can eliminate expensive realization routes or expose independent blockers.

### Target-Relative Evidence Principle

> The strength of evidence required depends on the proposition the target actually needs.

### Provenance-Separation Principle

> Historical records may persist even when they are no longer admissible as current claims.

---

## 96. Conclusion

A development environment is not merely a collection of commands waiting to be executed.

It is an open system containing:

```text
semantic operations
alternative realizations
hidden prerequisites
partial observations
mutable evidence
policy constraints
provider boundaries
runtime assumptions
```

The most useful organizing question is therefore not:

```text
What command should run next?
```

It is:

```text
What proposition do we want to justify,
what alternative rule structures could justify it,
which premises already have admissible evidence,
which can be realized,
which can be observed,
and which effect most usefully advances the proof?
```

This suggests a compact architecture:

```text
target expression
→ semantic proposition
→ lazy AND/OR elaboration
→ current claims
→ epistemic frontier
→ route and observation search
→ executable effect
→ validation
→ admitted claim
→ re-elaboration
```

The result is both narrower and more general than a universal development executor.

It is narrower because the core does not attempt to know every ecosystem.

Providers supply bounded rule families.

Backends supply concrete effect realization.

The engine supplies typed composition, proof search, planning, evidence, and explanation.

It is more general because the same machinery can reason about:

```text
builds
tests
runtime environments
containers
devices
middleware
deployment contracts
health checks
compatibility
observability
```

without reducing them to command strings.

The key architectural insight is that **development guidance can be treated as construction of an executable proof**.

A desired target creates obligations.

Rules expose alternative ways to satisfy them.

Claims discharge obligations when evidence is sufficient.

Effects change the world or reduce uncertainty.

Validation determines which candidate results become admissible knowledge.

The frontier exposes where the current architecture, world state, or observability ends.

And conditional elaboration allows reasoning to continue beyond the first physical blocker without pretending that unresolved assumptions are already true.

That is the foundation of a goal-directed speculative capability elaborator.
