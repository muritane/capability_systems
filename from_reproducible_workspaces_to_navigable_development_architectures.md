# From Reproducible Workspaces to Navigable Development Architectures: Capability Maps, Realization Paths, Persistent State, and Constructive Guidance

## Abstract

Development environments are usually treated as background assumptions.

A repository is cloned.

A workspace is presumed to exist.

A sequence of shell commands is copied from documentation.

Dependencies are installed.

A build system is invoked.

A container may be constructed.

A test suite may run.

An image may eventually be exported.

What is rarely represented explicitly is the organized structure that makes these transitions possible.

The relevant problem is therefore not only:

> How can a development workspace be reproduced?

It is more generally:

> Which development states, transformations, dependencies, interfaces, realization conditions, and continuation paths are currently available; which target states are reachable; why are others blocked; and which changes would make them reachable?

This suggests a development architecture closer to a map than to a setup script.

A road network does not choose a destination.

It represents available routes, restrictions, junctions, closures, vehicle-dependent reachability, and alternative continuations.

Likewise, a development architecture need not decide what a developer wants to build.

It should make explicit:

```text
where the workspace currently is
which capabilities are already realized
which transformations are available
which dependencies each transformation requires
which paths are blocked
which paths require preparation
which paths require architectural extension
which states are healthy, stale, degraded, or unknown
which actions are reversible
which artifacts can be produced
which assumptions produced those artifacts
and which downstream systems can consume them
```

The existing software ecosystem already provides much of the road network.

Linux, shells, package managers, compilers, build systems, language runtimes, interface generators, container systems, robotics middleware, OCI registries, deployment systems, and cluster orchestrators each stabilize reusable transformations.

The missing layer is often a persistent representation of how those transformations compose for one particular workspace.

This document develops that layer as a **navigable development capability architecture**.

The central proposal is:

\[
\boxed{
\text{a development workspace should be represented as a persistent,
typed graph of realizable transformations through which a finite user
can inspect, reproduce, navigate, extend, and repair capability}
}
\]

This view combines several earlier themes:

```text
question-relative representation
composable interfaces
viable realization
operating regimes
organized interaction
reachability before preference
persistent intermediate structure
finite leverage through factorization
```

It adds a practical consequence.

The developer should not need to reconstruct the architecture mentally from scattered READMEs, shell history, copied examples, Dockerfiles, package manifests, CI configuration, build errors, source code, and tribal knowledge.

The architecture itself should expose the roads.

---

## 1. The Problem Is Larger Than Workspace Creation

A workspace directory is only one state in a much larger development process.

For example:

```text
repository absent
→ repository acquired
→ environment identified
→ dependencies resolvable
→ environment realized
→ interfaces generated
→ source buildable
→ build current
→ tests executable
→ tests passed
→ package constructible
→ image constructible
→ artifact exportable
→ artifact deployable
```

A conventional tool may automate one transition.

A package manager installs dependencies.

A build system compiles.

A container builder constructs an image.

A deployment system runs the image.

But a developer encountering an unfamiliar repository must still answer:

```text
What exists here?

What kind of workspace is this?

Which tools are required?

Which versions matter?

What has already been realized?

Which state is stale?

What can I execute safely?

Why does this command fail?

What is the next missing capability?

Is the missing capability installable?

Does it require changing the workspace?

Does it require changing the host?

Can it be isolated?

Can the current result be reproduced elsewhere?

What produced this artifact?

Can the environment be repaired rather than recreated manually?

What remains useful after deployment?
```

These are not merely command-discovery questions.

They are questions about a represented architecture of possible continuation.

---

## 2. A Road Network Is Not a Route

A useful analogy is a map.

Consider:

```text
road
intersection
bridge
tunnel
one-way restriction
vehicle limit
construction closure
fuel station
current location
destination
route
alternate route
```

The road network exists before one destination is selected.

A map can therefore answer:

```text
Where am I?

Which destinations are represented?

Which are reachable?

Which route is shortest?

Which route is currently blocked?

Which route requires a different vehicle?

Which route becomes available if a bridge is repaired?

Which alternatives remain if one road closes?
```

The map does not need to decide:

> Where should the traveler want to go?

This distinction transfers naturally to development infrastructure.

Existing technical systems define roads:

```text
source file
    --compiler-->
object file

object files
    --linker-->
executable

package manifest
    --dependency resolver-->
dependency closure

ROS interface definition
    --interface generator-->
language-specific representation

workspace source
    --colcon/CMake/Cargo/etc.-->
built workspace

Dockerfile + context
    --container builder-->
OCI image

OCI image
    --registry protocol-->
published artifact

deployment description + image
    --cluster orchestration-->
running workload
```

The route is a selected composition through those transformations.

Thus:

\[
\boxed{
\text{development infrastructure defines supported movement;
a development task selects a route through it}
}
\]

---

## 3. Existing Tools Are Roads, Not Obstacles to Abstraction

A navigable development architecture should not begin by replacing established tools.

It should begin by representing them.

Examples include:

```text
Linux
Bash
PowerShell
apt
dnf
pacman
Nix
Homebrew
Python
uv
pip
Node.js
npm
Cargo
CMake
Ninja
Make
colcon
rosdep
rosidl
Docker
Podman
BuildKit
OCI
Git
GitHub Actions
GitLab CI
Kubernetes
Flux
```

Each already supplies stabilized semantics.

For example:

```text
apt
    package identity
    dependency relations
    installation

CMake
    build configuration
    target dependency structure
    generator output

Cargo
    package graph
    dependency resolution
    compilation
    testing

Docker
    filesystem/environment construction
    isolation boundary
    process execution
    image persistence

ROS
    package conventions
    interface definitions
    middleware abstractions
    message/service/action semantics
```

The higher-level tool should therefore ask:

> Which existing transformation can satisfy this edge?

rather than:

> How can the core reimplement this transformation?

This yields:

\[
\boxed{
\text{the architecture should compose ecosystem capabilities
rather than replace them with one universal mechanism}
}
\]

---

## 4. The Primary Object Is a Capability Graph

Let a development architecture be represented by a typed graph:

\[
G=(V,E,\tau_V,\tau_E).
\]

Here:

```text
V
    represented development states, capabilities, artifacts,
    environments, interfaces, or intermediate results

E
    transformations, dependencies, constraints, observations,
    repairs, exports, or realization relations

tau_V
    node types

tau_E
    edge types
```

A simple fragment may be:

\[
\text{source}
\xrightarrow{\text{build}}
\text{binary}
\xrightarrow{\text{package}}
\text{image}
\xrightarrow{\text{publish}}
\text{registry artifact}.
\]

But realistic development graphs include branches, joins, constraints, and alternate realizations.

For example:

```text
                         ┌──────── host backend ────────┐
source → ROS provider ───┤                              ├→ executable
                         └────── Docker backend ────────┘
```

or:

```text
IDL
 ├─→ C++ generator ─→ generated C++ ─→ rclcpp
 ├─→ Python generator → generated Python → rclpy
 └─→ language X generator → generated X → client binding X
```

The graph is therefore not merely a pipeline.

It can contain:

```text
alternatives
dependencies
fallbacks
optional capabilities
shared intermediates
repair paths
redesign edges
validation edges
export edges
observational edges
```

---

## 5. Node Types Should Preserve Useful Distinctions

A single undifferentiated node type called `state` is too weak.

Useful node classes may include:

```text
SourceState
EnvironmentDefinition
EnvironmentRealization
ProviderCapability
BackendCapability
DependencySet
GeneratedInterface
BuildState
TestState
RuntimeCapability
Artifact
PublishedArtifact
DeploymentInput
ObservedHealth
Constraint
LockState
ProvenanceRecord
```

The point is not to maximize ontology.

The point is to preserve distinctions that change downstream reasoning.

For example:

```text
build exists
```

is not equivalent to:

```text
build is current relative to source
```

Likewise:

```text
Docker installed
```

is not equivalent to:

```text
the declared Docker backend can realize this workspace
```

And:

```text
ROS package detected
```

is not equivalent to:

```text
the selected language binding can consume every required ROS interface
```

Thus the representation should distinguish exactly the states required for useful queries.

---

## 6. Edge Types Matter Even More

An edge:

\[
a\rightarrow b
\]

is ambiguous without semantics.

It might mean:

```text
requires
produces
generates
builds
tests
observes
validates
contains
sources
mounts
executes-in
depends-on
constrains
repairs
invalidates
exports
publishes
supports
implements
binds-to
translates
```

These are not interchangeable.

For example:

```text
source --builds--> binary
binary --tested-by--> test-result
test-result --validates--> build-state
Docker --executes-in--> isolated-environment
rosidl --generates--> language-interface
language-interface --binds-to--> client-library
```

Typed edges enable useful questions:

```text
Why is this state unavailable?

Which dependency blocks it?

Which transformation would realize it?

Which output became stale?

Which consumer depends on this representation?

Which repair path restores viability?

Which alternative backend can satisfy the same role?
```

---

## 7. Capability Is a Realizable Path

Suppose a target capability is \(\kappa\).

A development environment is capable of \(\kappa\) only if there exists a realizable path through the current architecture.

Let:

\[
p=(e_1,e_2,\ldots,e_n)
\]

be a path through the graph.

Then:

\[
\operatorname{Capable}(G,\kappa,C)
\iff
\exists p\;
\operatorname{Realizes}(p,\kappa,C),
\]

where \(C\) is the current context.

This is stronger than asking:

> Is the target theoretically possible?

A programming language may be computationally universal.

A host may be capable of running arbitrary machine code.

A container may support arbitrary processes.

None of these facts implies that a usable path currently exists from:

```text
this repository
```

to:

```text
this desired capability.
```

The practical question is:

\[
\boxed{
\text{Is there a viable composed path from the current represented state
to the target capability?}
}
\]

---

## 8. Possibility, Reachability, Viability, Admissibility, and Preference Must Remain Separate

For a candidate target \(x\), distinguish:

\[
\operatorname{Possible}(x),
\]

\[
\operatorname{Represented}(x),
\]

\[
\operatorname{Reachable}(x),
\]

\[
\operatorname{Viable}(x),
\]

\[
\operatorname{Admissible}(x),
\]

and:

\[
\operatorname{Preferred}(x).
\]

These answer different questions.

A target may be:

```text
possible in principle
but not represented by the current provider

represented
but disconnected from the current workspace state

reachable
but only through a broken or unsafe environment

viable
but prohibited by project policy

admissible
but not desired by the developer
```

A mature tool should not collapse all of these into:

```text
yes / no
```

or:

```text
works / fails
```

A richer status vocabulary may be:

```text
READY
PREPARATION_REQUIRED
STALE
DEGRADED
BLOCKED
UNSUPPORTED
UNKNOWN
REDESIGN_REQUIRED
PROHIBITED
```

---

## 9. The Current Workspace State Is a Position on the Map

The developer should be able to ask:

> Where am I?

For example:

```text
Workspace: robot-control

Source
    present
    commit: abc123

Environment
    declared
    Docker backend selected
    image available

Dependencies
    resolved

Interfaces
    generated

Build
    stale

Tests
    blocked by stale build

Runtime
    available with old artifact

Export
    blocked by unvalidated build
```

This is not merely metadata.

It defines the current reachable continuation space.

The same repository on another host may occupy a different state:

```text
Source
    present

Environment
    not realized

Docker
    missing

ROS provider
    recognized

Build
    absent
```

Therefore workspace identity and workspace realization should remain separate.

---

## 10. “Why Am I Here?” Is a Provenance Query

Current state should not be represented without causal or dependency context.

Suppose:

```text
build = stale
```

The tool should be able to explain:

```text
build became stale
because src/controller.cpp changed
after build artifact B was produced
from source state S0
```

Likewise:

```text
test unavailable
because test requires a current build
and the current build is stale
```

Thus the user can ask:

```text
Why am I here?

Why is build stale?

Why is this edge blocked?

What changed?

Which previous transformation established this state?

Which assumption no longer holds?
```

This suggests persistent provenance edges.

For example:

\[
\operatorname{ProducedBy}(artifact,build\_execution),
\]

\[
\operatorname{UsedInput}(build\_execution,source\_digest),
\]

\[
\operatorname{UsedEnvironment}(build\_execution,environment\_lock).
\]

Then state is not merely remembered.

It is explainable.

---

## 11. The Next Step Should Be Derived, Not Mystically Recommended

A useful development navigator may propose a plausible next transition.

But the distinction between availability and preference should remain explicit.

Suppose:

```text
declared target:
    validated runtime image

current state:
    source changed
    build stale
    tests require current build
    image requires passed tests
```

Then:

```text
build
```

is a plausible next step because it lies on a dependency path toward the declared target.

The explanation is structural:

```text
source changed
→ current build invalidated
→ tests depend on current build
→ image export depends on validated tests
→ therefore build is the nearest blocked prerequisite
```

The tool need not claim:

> Building is what you should want.

It can say:

> Given the declared target, this transition removes the nearest currently blocking dependency.

Thus:

\[
\boxed{
\text{guidance should be derived from represented reachability and declared intent,
not confused with autonomous goal selection}
}
\]

---

## 12. Providers Encode Domain-Specific Roads

A provider contributes semantic knowledge about one ecosystem.

For example, a ROS provider may know:

```text
package.xml
ROS distribution
rosdep
colcon
ament
rosidl
message/service/action definitions
underlays
overlays
environment sourcing
RMW selection
DDS configuration
```

A Python provider may know:

```text
pyproject.toml
interpreter version
dependency lock
virtual environment
test runner
package build
```

A CMake provider may know:

```text
CMakeLists.txt
configure state
generator
targets
build directory
install prefix
```

The provider does not own execution placement.

It describes domain-specific states and transformations.

This separation is important.

---

## 13. Backends Encode Where and How Realization Occurs

A backend answers a different question:

> Where and under which isolation/execution semantics does a transformation run?

Examples:

```text
host
Docker
Podman
Nix shell
remote machine
SSH execution
cluster build service
```

A Docker backend may know:

```text
image identity
container lifecycle
mounts
devices
groups
networking
environment variables
working directory
UID/GID mapping
cache mounts
process execution
```

A host backend may know:

```text
installed tools
PATH
shell environment
filesystem permissions
system packages
```

Thus:

```text
provider
    what transformation means

backend
    where/how the transformation is realized
```

This permits:

```text
ROS build + host
ROS build + Docker
Python test + host
Python test + Nix
```

without duplicating the whole architecture.

---

## 14. Actions Are Named Route Patterns

Commands such as:

```text
build
test
exec
shell
package
image
export
```

should not be hard-coded as identical operations across all workspaces.

They are semantic action classes.

A provider may resolve:

```text
build
```

into:

```text
colcon build
```

or:

```text
cargo build
```

or:

```text
cmake --build ...
```

The backend then realizes the command in the selected environment.

Conceptually:

```text
wsx build
    ↓
resolve action semantics
    ↓
verify preconditions
    ↓
select backend realization
    ↓
execute
    ↓
observe outputs
    ↓
update state/provenance
```

Thus a generic action is a reusable route pattern over provider- and backend-specific edges.

---

## 15. `exec` Is the Lowest Common Operational Invariant

Many commands can be understood as specialized execution.

For example:

```text
build
test
format
lint
run
generate
package
```

all ultimately require:

> execute a transformation in the correct realized environment.

Therefore a foundational invariant may be:

\[
\boxed{
\operatorname{ExecReady}(W,c)
}
\]

meaning:

> command \(c\) can be executed in workspace \(W\) under the declared environment with its required assumptions satisfied.

Then:

```text
build
```

is:

```text
provider-specific command
+ backend execution
+ state transition semantics
```

and:

```text
shell
```

is simply an interactive execution session.

This makes execution a useful unifying primitive without reducing the architecture to a shell wrapper.

---

## 16. Health Is Capability-Relative

There is no universal scalar called:

```text
workspace health
```

independent of purpose.

A workspace may be healthy for:

```text
editing source
```

while unhealthy for:

```text
building
```

It may be healthy for:

```text
building
```

while unhealthy for:

```text
hardware integration testing
```

It may be healthy for:

```text
simulation
```

while lacking:

```text
GPU access
CAN access
realtime scheduling
DDS network visibility
```

Therefore let:

\[
q_K(x)
\]

be a health or viability summary of detailed state \(x\) relative to capability \(K\).

The summary should preserve only the distinctions that change continuation for \(K\).

For ROS hardware development, this may include:

```text
ROS distribution
dependency closure
overlay consistency
device availability
group membership
network mode
RMW implementation
realtime permissions
GPU compatibility
```

For ordinary Python unit testing, most of those distinctions are irrelevant.

---

## 17. `doctor` Is Selective Observability

A useful diagnostic command should not dump every environmental variable.

It should answer:

> Which currently observable distinctions are sufficient to determine whether the selected capability can continue?

For example:

```text
$ wsx doctor build

✓ environment realized
✓ compiler available
✓ dependency lock satisfied
✓ generated interfaces current
✗ source/build relation stale
```

Or:

```text
$ wsx doctor hardware-test

✓ build current
✓ /dev/ttyACM0 present
✗ user lacks dialout access
? realtime scheduler permission not verified
```

The diagnostic vocabulary should include uncertainty.

For example:

```text
healthy
degraded
near-boundary
stale
broken
unknown
not-observable
```

A missing observation is different from a negative observation.

---

## 18. Repair Is a Path Back Into a Viable Region

Repair should not mean:

> erase everything and recreate blindly.

It means:

> identify which realization conditions no longer satisfy the declared capability and select transformations that restore them.

Suppose:

```text
desired environment
    image digest D
    dependency lock L
    generated interfaces G

actual environment
    image D
    dependency lock differs
    generated interfaces stale
```

Then repair may require only:

```text
restore dependencies
regenerate interfaces
```

not:

```text
destroy entire workspace
```

Formally, if:

\[
x\notin\Omega_K
\]

where \(\Omega_K\) is the viable realization region for capability \(K\), repair seeks:

\[
x\xrightarrow{r^*}x'
\]

such that:

\[
x'\in\Omega_K.
\]

The target is restoration of capability-relevant equivalence, not exact restoration of every prior bit.

---

## 19. Reproduction Is Re-Realization From Persistent Structure

A shell history is not a reproducible environment.

A Dockerfile alone is not necessarily a complete workspace model.

A README is not executable state.

A useful reproduction architecture preserves enough information to answer:

```text
What was declared?

Which inputs were resolved?

Which tool versions mattered?

Which generated states were derived?

Which transformations were executed?

Which outputs resulted?

Which host properties remained relevant?

Which external resources were assumed?

Which state can be regenerated?

Which state must be persisted?
```

A conceptual layout might therefore distinguish:

```text
workspace declaration
    committed intent

lock state
    resolved external inputs

derived state
    rebuildable local results

runtime state
    ephemeral execution state

provenance
    relation between inputs, transformations, and outputs
```

For example:

```text
project/
├── wsx.yaml
├── wsx.lock
├── src/
└── .wsx/
    ├── state.json
    ├── provenance/
    └── cache/
```

The exact file format is secondary.

The important distinction is architectural.

---

## 20. Persistence Is What Prevents Repeated Cognitive Reconstruction

Development environments often lose their intermediate reasoning.

A person discovers:

```text
which branch of a dependency is needed
which package generator is missing
which device group is required
which environment variable makes DDS work
which build order resolves the interface problem
```

Then that knowledge disappears into:

```text
terminal history
chat messages
personal memory
README edits
CI snippets
copy-pasted scripts
```

The next person reconstructs it.

This is a failure of addressability and persistence.

A better system turns resolved structure into a reusable relative primitive.

For example:

```text
ROS2_RUST_JAZZY_READY
```

should not merely be a human memory.

It should correspond to a represented state whose realization conditions are inspectable.

Then later operations can begin from that state rather than rediscovering the path.

---

## 21. Development Infrastructure Should Survive Artifact Creation

Conventional pipelines often behave conceptually like:

```text
source
→ temporary setup knowledge
→ build
→ artifact

discard setup reasoning
```

This is wasteful.

The build artifact is one output.

The development architecture has produced other valuable intermediate structure:

```text
dependency resolution
environment realization
interface compatibility
toolchain constraints
test evidence
build provenance
repair knowledge
known failure boundaries
export semantics
```

These should remain available.

A stronger lifecycle is:

```text
                 persistent workspace architecture
                            │
          ┌─────────────────┼──────────────────┐
          │                 │                  │
      environment         evidence          provenance
          │                 │                  │
          └───────→ build → test → package ←──┘
                              │
                              ▼
                           artifact
                              │
                              ▼
                           deploy
```

The development architecture does not need to become the deployment controller.

It remains the durable explanation of how the deployable object was realized.

---

## 22. Artifact Export Is a Natural Boundary

A development lifecycle can terminate in a well-defined artifact.

Examples:

```text
binary
library
package
wheel
archive
OCI image
firmware image
generated deployment description
```

At that point a downstream system may assume responsibility.

For example:

```text
workspace architecture
      ↓
verified OCI image
      ↓
registry
      ↓
deployment configuration
      ↓
Flux
      ↓
Kubernetes
```

The upstream system answers:

```text
Can this artifact be produced?

From which source?

Under which environment?

With which tests?

With which provenance?

With which runtime declaration?
```

The deployment system answers:

```text
Where should this artifact run?

How many replicas?

On which nodes?

Under which policies?

How should runtime state converge?
```

Thus:

\[
\boxed{
\text{workspace reconciliation and deployment reconciliation
operate over different state spaces}
}
\]

---

## 23. This Is Not Kubernetes for a Laptop

The analogy to reconciliation should not be overextended.

A development workspace manager may compare:

```text
desired workspace state
```

with:

```text
actual workspace state
```

and provide:

```text
status
repair
realize
```

But this does not imply the need for:

```text
persistent controllers
distributed consensus
cluster scheduling
service discovery
replica management
continuous background reconciliation
```

A developer-controlled lifecycle can remain explicit:

```text
inspect
→ plan
→ realize
→ execute
→ observe
→ repair
```

Continuous cluster reconciliation belongs elsewhere.

The architectural resemblance is useful only at the level of:

```text
declared state
actual state
difference
convergence
```

The domains remain distinct.

---

## 24. This Is Not Flux Either

Flux assumes a deployment-oriented desired state and reconciles cluster resources from declared sources.

A development navigator should stop before assuming responsibility for the running production system.

A useful boundary is:

```text
DEVELOPMENT / BUILD

source
→ environment
→ dependencies
→ generated interfaces
→ build
→ tests
→ package
→ artifact
→ publication

---------------- handoff ----------------

DEPLOYMENT / OPERATION

artifact reference
→ deployment declaration
→ cluster reconciliation
→ runtime workload
→ operational monitoring
```

Export support may cross the boundary descriptively.

For example:

```text
wsx export kubernetes
```

could produce a starting representation.

But:

```text
wsx reconcile production forever
```

would indicate architectural scope expansion into another problem.

---

## 25. Semantic Zoom Is a Natural Consequence

Maps work at several scales.

A country-level view does not show every lane marking.

A street-level view does.

The same should apply to development architecture.

At a high level:

```text
source
→ build
→ test
→ image
→ export
```

Zoom into `build`:

```text
dependencies
→ interface generation
→ configure
→ compile
→ link
→ install
```

Zoom into `interface generation`:

```text
schema
→ parser
→ normalized representation
→ language generator
→ generated source
→ runtime type support
```

Zoom into container realization:

```text
base image
→ system packages
→ user mapping
→ source mount
→ device mapping
→ environment variables
→ process execution
```

Each higher-level node is therefore a relative primitive.

The user should not be forced to carry every lower-level distinction unless a lower-level condition becomes relevant.

---

## 26. A Missing Language Binding Is a Reachability Gap

Suppose a developer asks:

> Can I write this middleware component in language \(L\)?

The wrong first answer is:

```text
language L is expressive enough
```

That establishes very little.

The relevant path may require:

```text
interface schema
→ parser
→ normalized IDL
→ language-specific generator
→ generated language types
→ serialization/type-support layer
→ client-library binding
→ middleware interface
→ build integration
→ package integration
→ runtime support
```

If any required edge is missing, then the desired capability may be:

```text
possible in principle
```

but:

```text
not currently reachable.
```

This distinction is essential.

---

## 27. ROS Makes the End-to-End Path Visible

Consider a generic ROS-style language-support chain:

```text
.msg / .srv / .action
        │
        ▼
interface parser
        │
        ▼
normalized interface representation
        │
        ▼
language generator
        │
        ▼
generated language types
        │
        ▼
type support / serialization
        │
        ▼
language client library
        │
        ▼
rcl
        │
        ▼
rmw
        │
        ▼
middleware
```

A developer who wants a new language does not merely need:

```text
syntax for publishers and subscribers
```

They need a viable path through the required architecture.

Some parts may be shared.

Some may require new bridges.

Some may already exist but not be integrated into the selected build system.

A map-like tool should expose the path.

---

## 28. Unsupported Does Not Mean Impossible

Suppose the desired route is absent.

The system should distinguish:

```text
UNSUPPORTED:
    no known provider implementation describes the path

BLOCKED:
    path exists but a required dependency is unavailable

PREPARATION_REQUIRED:
    path exists and missing prerequisites can be realized

REDESIGN_REQUIRED:
    current architecture lacks an edge that must be implemented

UNKNOWN:
    the model does not contain enough information
```

This matters because:

```text
no route currently represented
```

is not equivalent to:

```text
no route can ever exist.
```

A tool that understands this distinction can help users extend the architecture rather than merely reject them.

---

## 29. Architecture Extension Is Road Construction

If a target becomes reachable only after adding:

```text
new interface generator
new FFI bridge
new backend adapter
new compiler integration
new schema mapping
new packaging rule
```

then the developer is not merely traversing the current map.

They are modifying the road network.

Let the current architecture be:

\[
G.
\]

An extension produces:

\[
G\rightarrow G'.
\]

A target \(t\) may satisfy:

\[
t\notin\operatorname{Reachable}(G)
\]

while:

\[
t\in\operatorname{Reachable}(G').
\]

The tool should make this explicit.

It should not present the redesign-dependent route as if it were already available.

---

## 30. The Tool Can Explain What New Support Would Require

Suppose a requested language target is currently unreachable.

Instead of:

```text
not supported
```

the architecture may derive:

```text
Target:
    ROS node in language X

Missing realization path:

✓ interface parser
✗ language generator
✗ generated type mapping
? serialization bridge
✓ low-level middleware API
✗ build-system integration
✗ package-provider integration
```

Then:

```text
To make the target reachable:

1. implement language generator
2. define primitive and compound type mapping
3. connect generated representation to type support
4. expose language client binding
5. add build/package integration
6. validate minimal publisher/subscriber path
```

This transforms failure into architectural guidance.

---

## 31. Documentation Should Not Be the Only Map

Today many development tasks are learned through:

```text
README
tutorial
blog post
Stack Overflow answer
copied repository
source-code inspection
trial and error
```

These are useful.

But they often describe routes without exposing the underlying road network.

For example:

```text
run command A
then B
then clone C
then export D
```

may work without explaining:

```text
which capability each step establishes
which later step consumes it
whether the sequence has alternatives
which state can be cached
which state is host-specific
which step is merely incidental
```

A navigable architecture should preserve those relations directly.

Documentation then becomes explanation over an explicit model rather than the sole carrier of that model.

---

## 32. Copying Examples Is Often a Symptom of Missing Constructive Guidance

A developer encountering an unfamiliar interface often works like this:

```text
search for example
copy example
rename symbols
change fields
compile
read errors
change code
repeat
```

This can be effective.

But it often means the valid construction space is not being exposed directly.

The developer does not know:

```text
what objects can be constructed
which fields are required
which types satisfy them
which transformations are legal
which combinations compose
```

The information often already exists inside:

```text
grammar
parser
schema
type checker
interface definition
compiler
generator
API contract
```

The question is whether this knowledge can be made navigable.

---

## 33. A Parser Defines More Than Acceptance

A parser is commonly treated as a function:

\[
P:s\rightarrow \{\text{accept},\text{reject}\}.
\]

But a grammar contains more structure.

Given a partial construction \(p\), one may ask:

\[
N(p)=\{\text{valid next syntactic continuations}\}.
\]

A parser or incremental parser can therefore contribute to constructive guidance.

For example:

```text
message-definition field
→ allowed type forms
→ valid identifier
→ optional array bounds
```

or:

```text
function call
→ expected argument structure
```

This is not generally reducible to regular expressions.

Context-free grammar, semantic analysis, symbol tables, type systems, and domain constraints may all matter.

---

## 34. Type Systems Further Restrict the Navigable Space

Syntax answers:

> What can be written?

Types answer a stronger question:

> Which written constructions satisfy the required interface relation?

Suppose an expression expects:

\[
T.
\]

Then a constructive tool can search for available expressions:

\[
e
\]

such that:

\[
\operatorname{type}(e)\preceq T.
\]

This already underlies many language-server features.

But the same principle can be generalized beyond one programming language.

For example:

```text
expected:
    geometry message

available:
    generated geometry type

requires:
    generated interface package

blocked because:
    interface generation not realized
```

The missing state may therefore be above the code editor.

---

## 35. Schemas Define Constructive Possibility Spaces

Suppose a message schema is:

```text
Twist
    linear: Vector3
    angular: Vector3

Vector3
    x: float64
    y: float64
    z: float64
```

Then the schema already defines a constrained construction space.

A tool need not require the user to search source code merely to discover:

```text
which fields exist
which nested structures are required
which primitive values are legal
```

A constructive interface can expose:

```text
Twist
├── linear
│   ├── x
│   ├── y
│   └── z
└── angular
    ├── x
    ├── y
    └── z
```

The same idea extends to:

```text
service requests
service responses
action goals
configuration schemas
container manifests
deployment manifests
package manifests
build target graphs
```

---

## 36. From Recognition to Reverse Construction

There is a useful duality.

A recognizer answers:

\[
\text{candidate}\rightarrow\text{valid?}
\]

A constructive navigator asks:

\[
\text{current partial state}\rightarrow
\text{which valid continuations exist?}
\]

For finite structured domains, this may be approximated through:

```text
grammar expansion
schema enumeration
type-directed search
constraint solving
symbol lookup
dependency graph traversal
capability matching
```

Thus the same formal machinery used to reject invalid constructions can sometimes support valid next-step generation.

This gives:

\[
\boxed{
\text{validation knowledge can often be reused as construction guidance}
}
\]

---

## 37. The Development Map Can Extend Across Tool Boundaries

Today autocompletion is often scoped to one language server.

But a development capability graph can connect several levels.

For example:

```text
User intent:
    publish /cmd_vel

ROS graph/schema:
    topic type = Twist

Generated interface:
    Twist available in C++

Language type system:
    publisher expects Twist

Build graph:
    package must depend on geometry_msgs

Workspace state:
    geometry_msgs dependency unresolved
```

A cross-layer navigator can therefore explain:

```text
You cannot complete this construction yet because
the required generated type is absent from the current
dependency/build realization.
```

This is different from a local compiler error.

It connects architectural state to source-level guidance.

---

## 38. “Autocomplete” Can Mean Architectural Completion, Not Only Text Completion

A richer system may offer completion at several scales.

### Text completion

```text
which token can appear next?
```

### Type completion

```text
which expression satisfies this expected type?
```

### Interface completion

```text
which fields/messages/roles satisfy this contract?
```

### Dependency completion

```text
which package supplies the missing representation?
```

### Environment completion

```text
which provider/backend action realizes the missing package?
```

### Capability completion

```text
which sequence makes the requested target reachable?
```

This gives a hierarchy:

```text
token
→ expression
→ interface
→ package
→ environment
→ capability
```

A map-like development system could connect these rather than treating them as unrelated forms of assistance.

---

## 39. Constraint Solving Is More General Than Regex

The constructive problem can be written abstractly.

Let:

\[
C=\{c_1,c_2,\ldots,c_n\}
\]

be constraints induced by:

```text
syntax
types
schemas
dependency relations
versions
platform
backend
permissions
resource limits
interface compatibility
```

The next valid continuation \(y\) should satisfy:

\[
c_i(y)=\text{true}
\]

for the relevant constraint family.

The tool need not globally solve all possible program synthesis.

It can solve small local navigation questions:

```text
Which package provides this interface?

Which generated type satisfies this schema?

Which backend can provide this device?

Which target can produce this artifact?

Which missing edge blocks this route?

Which action restores this invariant?
```

The finite-leverage principle applies here as well.

Do not solve the entire world.

Stabilize reusable local structure.

---

## 40. Plans Should Be Validated Before Execution

A route can be represented before it is traversed.

Suppose a target requires:

```text
install dependency
→ regenerate interfaces
→ rebuild
→ test
→ image
```

The tool can first validate:

```text
dependency source available?
version compatible?
backend writable?
generator installed?
build command defined?
test action defined?
image backend available?
```

Only then execute.

This yields:

```text
target
→ route generation
→ precondition validation
→ resource validation
→ side-effect/reversibility analysis
→ execution
→ observation
→ state update
→ rollback/repair if required
```

For low-cost transformations, validation may be lightweight.

For destructive or expensive transformations, it becomes more important.

---

## 41. Reversibility and Recovery Should Be Represented

Not all edges have equal failure semantics.

Examples:

```text
compile source
    cheap, repeatable

delete cache
    recoverable

upgrade host package
    host-mutating

flash firmware
    potentially high consequence

publish immutable artifact
    externally persistent

deploy to production
    outside normal workspace lifecycle
```

A capability map should therefore be able to annotate:

```text
reversible
idempotent
destructive
host-mutating
isolated
cached
externally persistent
requires backup
```

Then route selection can account for more than path existence.

---

## 42. Isolation Is One Property of a Route

A core motivation is often:

> run something without breaking the host.

This should not require the whole architecture to be “about Docker.”

Instead, execution paths can carry isolation properties.

For example:

```text
host backend
    direct host mutation possible

Docker backend
    filesystem/process isolation
    selected host mounts/devices

Nix backend
    declarative package environment

remote backend
    execution off-host
```

Then a user may ask:

```text
Can this target be reached without mutating the host?

Which backend satisfies that constraint?
```

The answer becomes route selection under a constraint.

---

## 43. Reproduction Strength Should Be Explicit

The word `reproducible` hides several levels.

A workspace may be:

### Repeatable

The same procedure can be attempted again.

### Resolved

External dependencies have concrete selected versions or identities.

### Locked

Important dependency choices are persisted.

### Environment-reproducible

Equivalent declared environment semantics can be realized again.

### Build-reproducible

Equivalent inputs reliably produce equivalent outputs.

### Bit-reproducible

The resulting artifact bytes are identical.

These should not be collapsed.

A container build using mutable package repositories may be repeatable without being bit-reproducible.

The system should state which guarantee it actually supports.

---

## 44. Provenance Connects Development to Deployment Without Merging Them

Suppose production runs artifact:

```text
sha256:XYZ
```

The development architecture may retain:

```text
artifact XYZ
    produced by build B

build B
    used source commit S

build B
    used environment lock E

build B
    passed tests T

image packaging
    used runtime declaration R
```

Then deployment tooling can remain separate while still benefiting from development provenance.

This gives a durable bridge:

```text
runtime failure
→ artifact identity
→ build provenance
→ source/environment state
→ reproducible investigation
```

Development infrastructure is therefore not discarded after deployment.

Its operational responsibility ends, but its explanatory state remains useful.

---

## 45. The Map Should Be Reopenable

No abstraction is permanently sufficient.

A high-level state may say:

```text
Docker backend healthy
```

until a lower-level issue matters:

```text
UID mapping wrong
device missing
kernel feature unavailable
network namespace incompatible
```

Then the abstraction should reopen.

Likewise:

```text
ROS provider ready
```

may need to reopen into:

```text
interface generator
type support
RMW implementation
overlay chain
```

when a new capability depends on those distinctions.

Thus:

\[
\boxed{
\text{zoom into hidden structure only when the current abstraction
no longer preserves the distinctions required by the question}
}
\]

This prevents both:

```text
permanent microscopic complexity
```

and:

```text
opaque high-level magic.
```

---

## 46. Providers Can Be Treated as Partial Maps

A provider need not claim universal coverage.

Let provider \(P\) expose a partial subgraph:

\[
G_P\subseteq G.
\]

For example:

```text
ROS provider
    recognizes package.xml
    knows rosdep
    knows colcon
    knows interface generation
    knows environment sourcing
```

but may not know:

```text
custom FPGA toolchain
```

Another provider can contribute that structure.

Composition occurs when interfaces are compatible.

This allows the architecture to grow without forcing one provider to understand every ecosystem.

---

## 47. Provider Composition Must Be Explicit

Suppose:

```text
ROS package
contains Rust component
built through Cargo
packaged into Docker
```

Then several providers may participate.

A simplistic universal provider can become brittle.

Instead:

```text
ROS provider
    package and middleware semantics

Cargo provider
    Rust dependency/build semantics

Docker backend
    isolated realization

OCI exporter
    artifact semantics
```

The architecture must establish compatibility between their shared boundaries.

For example:

```text
Cargo output location
must satisfy
ROS package install expectation
```

A shared label such as `build output` is insufficient if semantics disagree.

---

## 48. Build Systems Already Contain Valuable Maps

Many build systems expose graph structure.

Examples include:

```text
targets
dependencies
generated files
inputs
outputs
commands
cache keys
```

A workspace navigator should reuse this information.

It should not infer everything from timestamps if the build system already knows more.

Likewise package managers expose:

```text
dependency graphs
version resolution
features
platform constraints
```

Interface generators expose:

```text
source schema
generated artifacts
language mappings
```

The development map is therefore partly a composition of maps already present inside existing tools.

---

## 49. The System Should Prefer Evidence Over Guessing

A route edge can have different evidence strengths.

For example:

```text
declared:
    manifest says Docker is required

detected:
    Dockerfile exists

verified:
    image successfully built

observed:
    container currently running

historical:
    this route worked under previous lock state

unknown:
    requirement not checked
```

These distinctions matter.

A tool should not silently transform:

```text
Dockerfile exists
```

into:

```text
Docker environment works.
```

Likewise:

```text
package declares test command
```

does not imply:

```text
tests pass.
```

---

## 50. State Should Be Time-Aware

Development state changes.

A build can become stale.

A dependency source can disappear.

A cached image can remain valid while source changes.

A device can disconnect.

A credential can expire.

Thus state should carry:

```text
observation time
source/version relation
validity horizon where relevant
dependency identity
```

For example:

```text
BUILD_CURRENT
relative to source digest S
and generator state G
```

not merely:

```text
build directory exists.
```

---

## 51. The Workspace Is a Persistent Identity, Not One Realization

A repository can be realized through several environments:

```text
host
Docker
Podman
remote builder
```

These may all belong to the same logical workspace.

Therefore:

```text
workspace identity
```

should be distinct from:

```text
workspace realization.
```

A workspace-local manifest can preserve durable identity and declared capability.

Host-global discovery can index it.

The host registry should not need to become the sole source of truth.

This supports:

```text
clone
discover
inspect
realize
```

without manually recreating hidden host registration state.

---

## 52. A Workspace Manifest Is a Map Seed, Not the Whole Map

A declarative manifest may specify:

```yaml
workspace:
  name: robot-control

providers:
  - ros

environment:
  backend: docker

targets:
  - build
  - test
  - runtime-image
```

But the complete graph emerges from several sources:

```text
manifest
repository structure
provider semantics
backend capabilities
lock state
host observation
build-system graph
generated artifacts
runtime observations
```

Thus:

\[
\text{declared model}
+
\text{discovered structure}
+
\text{observed state}
\rightarrow
\text{current capability map}.
\]

The manifest should not be forced to duplicate information already available reliably elsewhere.

---

## 53. Discovery Is Therefore First-Class

A useful system should be able to inspect an existing repository and say:

```text
Detected:
    ROS package structure
    CMake build
    Python package
    Dockerfile
    .repos dependency declaration
    CI workflow

Potential providers:
    ROS
    CMake
    Python
    Docker

Unknown:
    intended runtime target
```

This creates an initial map.

The developer can then enrich it rather than writing a complete model from zero.

---

## 54. The Map Should Distinguish Existing Roads From Proposed Roads

Suppose discovery reveals:

```text
CMake build path exists
```

while a user asks for:

```text
Rust implementation
```

The tool may infer that a new integration is required.

It should represent:

```text
existing edge
```

differently from:

```text
candidate extension edge.
```

For example:

```text
solid:
    verified current capability

dashed:
    declared but unrealized

dotted:
    inferred possible extension

blocked:
    known missing prerequisite
```

This is conceptually useful even if no GUI is ever implemented.

A CLI can express the same distinctions textually.

---

## 55. A GUI Is Not Required for a Map-Like Architecture

The map metaphor is structural, not visual.

A useful interface may remain entirely CLI-based:

```text
wsx status
wsx routes build
wsx why test
wsx doctor
wsx plan image
wsx repair
wsx exec -- ...
```

For example:

```text
$ wsx routes image

CURRENT
    source: changed
    build: stale

ROUTE 1
    build
    test
    image

BLOCKERS
    none

ROUTE 2
    use previous build
    image

INVALID
    image requires validated current build
```

The value comes from the represented graph and explanations, not from rendering a dashboard.

---

## 56. Do Not Turn It Into a ROS Operations Dashboard

The development architecture may know:

```text
ROS_DOMAIN_ID
RMW implementation
network mode
DDS dependencies
```

because these affect workspace realization.

It does not therefore need to become:

```text
topic graph visualizer
bag viewer
robot telemetry dashboard
DDS packet inspector
fleet UI
```

A scope test is:

> Does this information determine development/build capability, realization, reproduction, diagnosis, repair, execution, or artifact handoff?

If yes, it belongs.

If it primarily inspects the application after it is running as an application, another tool probably owns it.

---

## 57. Do Not Turn It Into a Universal Build System

Build systems already solve difficult subproblems.

The architecture should not replace:

```text
CMake target semantics
Cargo dependency resolution
Bazel build graph
colcon package orchestration
```

unless a provider must add missing integration.

The generic layer should invoke and interpret these systems.

This follows the principle:

\[
\boxed{
\text{reuse stabilized transformations as relative primitives
instead of reopening solved lower-level complexity by default}
}
\]

---

## 58. Do Not Turn It Into a Universal Package Manager

Likewise, the system should not attempt to own every dependency.

It may coordinate:

```text
apt
rosdep
pip
uv
Cargo
npm
Nix
```

and persist resolved state where useful.

But the package manager remains the expert in its own domain.

The higher-level question is:

> Which dependency capability must be realized for the selected route?

---

## 59. The Core Lifecycle Can Remain Small

Despite the large conceptual space, the core operations can remain compact.

For example:

```text
discover
inspect
plan
realize
execute
observe
repair
persist
export
```

These can surface as:

```text
wsx init
wsx list
wsx status
wsx up
wsx plan
wsx doctor
wsx repair
wsx exec
wsx shell
wsx build
wsx test
wsx export
```

The apparent variety reduces to a small number of architectural operations over the capability graph.

---

## 60. A Minimal Formal Workspace Model

A practical metamodel could begin with:

\[
\mathfrak W=
(V,E,\tau,S,D,O,A,R,P,H),
\]

where:

```text
V
    typed state/capability/artifact nodes

E
    typed relations and transformations

tau
    node and edge semantics

S
    current observed state

D
    declared desired/target states

O
    observation functions

A
    executable actions

R
    resources, dependencies, and realization conditions

P
    provenance and persistence relations

H
    selected horizon or validity context
```

A provider contributes:

\[
G_P=(V_P,E_P).
\]

A backend contributes:

\[
G_B=(V_B,E_B).
\]

The current workspace graph is assembled approximately as:

\[
G_W
=
G_{\text{declared}}
\cup
G_{\text{discovered}}
\cup
\bigcup_PG_P
\cup
\bigcup_BG_B
\cup
G_{\text{observed}}.
\]

Compatibility conditions determine whether edges compose.

---

## 61. Route Search Is Constraint-Relative

Let:

\[
s_0
\]

be the current state and:

\[
T
\]

a target capability.

A candidate route is:

\[
p:s_0\leadsto T.
\]

But route selection may be constrained by:

```text
do not mutate host
must use locked dependencies
must support offline build
must preserve cache
must use GPU
must avoid privileged containers
must produce OCI artifact
```

Let constraint family be:

\[
\mathcal C.
\]

Then route search asks:

\[
p^*
\in
\{p:s_0\leadsto T\mid p\models\mathcal C\}.
\]

Cost may then include:

\[
C(p)
=
C_{\text{time}}
+
C_{\text{risk}}
+
C_{\text{mutation}}
+
C_{\text{network}}
+
C_{\text{repair}}
+
C_{\text{cognitive}}.
\]

This makes the map analogy operational.

---

## 62. Cognitive Cost Is a Real Architectural Cost

A development route that requires:

```text
read seven READMEs
inspect three Dockerfiles
remember sourcing order
guess package names
copy code from another project
manually infer generated types
```

may be technically feasible.

But it has high cognitive cost.

A good intermediate representation reduces the amount of architecture each developer must reconstruct locally.

Thus:

\[
\boxed{
\text{developer comprehensibility is part of total realization cost}
}
\]

This is one reason persistent capability maps create leverage.

---

## 63. The Architecture Can Preserve “Why This Exists”

A common maintenance problem is an unexplained line such as:

```bash
export SOME_FLAG=1
```

Months later, no one knows why it exists.

A represented dependency can preserve:

```text
SOME_FLAG=1
    required by middleware compatibility condition M
    introduced for capability hardware-test
    verified under environment lock E
```

Then removing it can trigger:

```text
This change invalidates capability:
    hardware-test
because:
    condition M no longer holds.
```

This is substantially stronger than configuration as unstructured text.

---

## 64. Repetition Should Create New Relative Primitives

Suppose many projects repeatedly require:

```text
ROS Jazzy
+ Docker
+ realtime
+ input devices
+ dialout
+ Cyclone DDS
```

That repeated composition can be stabilized.

For example:

```text
profile:
    ros2-hardware-dev
```

But the profile should not become opaque.

It remains reopenable into its contributing conditions.

This follows:

```text
repeated composition
→ stabilization
→ addressability
→ reuse as new primitive
```

A template or profile earns its existence when it materially reduces repeated reconstruction.

---

## 65. Templates Should Encode Capability, Not Merely File Scaffolding

A conventional template may create:

```text
Dockerfile
compose.yaml
src/
.gitignore
```

A stronger template declares:

```text
this workspace intends to support:
    build
    test
    isolated execution
    hardware access
    OCI export
```

Then the generated files are one realization of those capabilities.

The capability survives even if the underlying implementation later changes.

For example:

```text
Docker → Podman
```

may preserve the same higher-level backend contract.

---

## 66. Substitution Should Be Contract-Relative

Two backends may be interchangeable for one action and not another.

For example:

```text
host
Docker
```

may both satisfy:

```text
compile C++ package
```

but only one may satisfy:

```text
access GPU with required driver stack
```

Thus:

\[
B_1\sim_KB_2
\]

only relative to capability \(K\).

Similarly:

```text
C++ client binding
Rust client binding
```

may both satisfy a high-level publisher contract while differing in:

```text
feature completeness
performance
build integration
supported interface types
```

Substitution is therefore relative to observed contract distinctions.

---

## 67. Unknown Must Remain a First-Class State

A system that tries to be helpful may be tempted to infer too much.

But:

```text
not checked
```

must remain distinct from:

```text
healthy.
```

Likewise:

```text
provider does not know
```

must remain distinct from:

```text
impossible.
```

Useful states include:

```text
unknown
unobserved
unsupported-by-model
ambiguous
conflicting-evidence
```

This prevents false confidence.

---

## 68. Explanation Is Part of the Interface

A route planner that only outputs:

```text
run these commands
```

still leaves the user dependent on hidden reasoning.

A stronger interface exposes:

```text
target
current state
blocking dependency
selected route
alternative route
side effects
evidence
expected resulting state
```

For example:

```text
TARGET
    test

CURRENT
    build stale

BLOCKER
    tests consume installed artifacts from build B
    source has changed since B

PLAN
    rebuild
    run tests

WHY
    rebuild restores source/build consistency required by test action
```

This makes the architecture teachable.

---

## 69. The Tool Can Support Learning Without Becoming a Tutor

By exposing structure, the tool naturally explains ecosystems.

A developer learns that:

```text
rosidl is required
```

not because documentation says so arbitrarily, but because the map shows:

```text
interface definition
→ rosidl generator
→ generated language type
→ client-library API
```

Likewise, they learn why:

```text
source /opt/ros/...
```

matters when the environment path is represented.

The architecture teaches by making dependency visible.

It does not need to generate generic tutorials for every topic.

---

## 70. Source-Level Guidance and Workspace Guidance Can Meet

A future integration may connect editor state to workspace state.

Suppose the user writes:

```text
publisher.publish(...)
```

The language server knows the expected generated type.

The workspace map knows whether that type is currently generated and which package provides it.

Then completion can cross layers:

```text
expected type:
    Twist

provider:
    geometry_msgs

workspace:
    dependency missing

available transition:
    add/resolve geometry_msgs
```

This is a qualitatively different form of assistance.

It links:

```text
what can I type here?
```

with:

```text
what must the workspace realize before that type exists?
```

---

## 71. Constructive Search Should Remain Local and Factorized

The system need not synthesize arbitrary programs.

That would be an unnecessarily broad problem.

Instead, it can answer bounded compositional questions:

```text
which next field is valid?
which type satisfies this contract?
which package provides this symbol?
which generator creates this representation?
which build target produces this artifact?
which backend supports this device?
which action removes this blocker?
```

Each local answer can be stabilized and reused.

This is more tractable and more aligned with existing formal interfaces.

---

## 72. Development Navigation Is a Finite-Leverage Problem

A developer has finite:

```text
attention
memory
time
working context
ecosystem familiarity
```

The total architecture may include:

```text
operating system
toolchain
build graph
dependency graph
generated code
middleware
containers
CI
runtime packaging
deployment interfaces
```

No user should need all of that active simultaneously.

The solution is not to erase complexity.

It is to factor it.

Thus:

```text
complex ecosystem
→ stable intermediate representations
→ local addressable capability
→ reusable route segments
→ higher-level navigation
```

The map is therefore a practical finite-leverage mechanism.

---

## 73. Failure Should Reveal the Nearest Relevant Boundary

Suppose a build fails because a generated interface is missing.

The architecture should avoid jumping immediately to:

```text
compiler error
```

as the only state.

It can classify:

```text
BUILD_FAILED

nearest violated capability boundary:
    generated interface unavailable

cause:
    interface generator dependency absent

repair route:
    realize generator
    regenerate interfaces
    rebuild
```

The error becomes an observation that updates the graph.

This is more useful than treating every failure as a novel exception.

---

## 74. Repair Knowledge Is Reusable Architecture

Once a failure is understood, its repair path should become reusable.

For example:

```text
symptom:
    permission denied /dev/ttyACM0

diagnosis:
    device exists
    backend exposes it
    process user lacks required group

repair:
    add dialout group mapping
```

The next workspace with the same structure can reuse the distinction.

This is another form of factorization:

```text
individual debugging episode
→ stabilized diagnostic representation
→ reusable repair capability
```

---

## 75. The Architecture Should Support Multiple Valid Routes

There may be several ways to reach the same target.

For example:

```text
build on host

build in Docker

build remotely

build through Nix environment
```

The target may be equivalent while costs differ.

Likewise:

```text
run tests locally
run tests in container
run tests through CI
```

A route map should expose alternatives rather than silently assume one global workflow.

The user can constrain selection.

---

## 76. A Target Can Be Declarative Without Being Mandatory

A project may declare:

```text
supported targets:
    build
    unit-test
    simulation
    runtime-image
```

This does not mean every user must traverse all of them.

It means the architecture can explain the routes.

For example:

```text
wsx plan simulation
```

and:

```text
wsx plan runtime-image
```

may diverge after a shared build state.

The map supports intention without encoding one fixed lifecycle.

---

## 77. Lifecycle Is a Graph, Not a Universal Sequence

A simple lifecycle:

```text
build
→ test
→ package
→ export
```

is useful but not universal.

Real projects may contain:

```text
generate
branch
parallel build
hardware test
simulation test
integration test
code generation feedback
multiple package outputs
```

Therefore lifecycle semantics should permit graph structure.

Named lifecycle stages can remain convenient projections.

---

## 78. Export Should Preserve Enough Semantic Contract

An artifact alone may be insufficient.

For example, an OCI image may also require:

```text
entrypoint
ports
devices
volumes
environment variables
capabilities
architecture
health command
```

A neutral export representation might therefore contain:

```yaml
artifact:
  type: oci
  digest: sha256:...

runtime:
  command: [...]
  environment: [...]
  devices: [...]
```

A Kubernetes exporter could translate that.

But the neutral runtime contract need not itself become Kubernetes.

---

## 79. Deployment Can Feed Evidence Back Without Collapsing the Boundary

Operational systems may report:

```text
image fails on architecture arm64
missing runtime device
resource limit too low
health command invalid
```

These observations can update development knowledge.

For example:

```text
runtime requirement:
    architecture = amd64 only
```

may become explicit in the artifact contract.

Thus the lifecycle can be informationally cyclic:

```text
development
→ artifact
→ deployment
→ observation
→ revised development model
```

while responsibility remains separated.

---

## 80. The Architecture Should Remain Tool-Agnostic but Not Semantically Empty

There is a dangerous form of generality:

```text
everything is just a command.
```

That creates a universal shell runner but loses the distinctions required for navigation.

There is an opposite danger:

```text
hard-code every ecosystem into the core.
```

The middle ground is:

```text
generic typed capability graph
+
provider-specific semantics
+
backend-specific realization
+
explicit contracts
```

This is general enough to compose ecosystems while specific enough to answer useful questions.

---

## 81. A Generic Command Is Not Yet a Capability

Consider:

```yaml
actions:
  build:
    run: some-command
```

This may be useful.

But it does not by itself explain:

```text
what the command consumes
what it produces
what state it invalidates
what dependencies it requires
what constitutes success
whether it is safe to repeat
```

A richer action contract may include:

```text
preconditions
inputs
outputs
invalidations
observations
side effects
repair semantics
```

The command is one realization.

The capability contract is the reusable abstraction.

---

## 82. Build/Test/Exec/Export Can Be Seen as Questions About Reachability

Each common command can be reframed.

### Build

> Is there a viable path from current source state to a current build artifact?

### Test

> Is there a viable path from current build state to validated evidence?

### Exec

> Is there a viable environment in which this command can run under the declared assumptions?

### Repair

> Which transformations return the workspace to a capability-valid region?

### Export

> Which verified development state can be transformed into a downstream-consumable artifact?

### Reproduce

> Can an equivalent capability state be realized again from persistent declarations and resolved inputs?

This unifies the lifecycle.

---

## 83. The Deepest Interface May Be “Where Can I Go From Here?”

A workspace navigator should answer:

```text
$ wsx next

CURRENT
    environment ready
    dependencies ready
    build stale

AVAILABLE
    build
    shell
    exec using previous artifact

BLOCKED
    test
        requires current build

    image
        requires passed tests

REDESIGN-DEPENDENT
    build with language X
        missing provider integration
```

This is closer to navigation than command memorization.

---

## 84. A Second Deep Interface Is “Why Can I Not Go There?”

For example:

```text
$ wsx why image

image is represented but not currently reachable

requires:
    package-ready

package-ready requires:
    tests-passed

tests-passed requires:
    build-current

build-current is false because:
    source digest changed after last build
```

This transforms the dependency graph into explanation.

---

## 85. A Third Deep Interface Is “What Would Make It Reachable?”

For example:

```text
$ wsx route rust-node

target:
    ROS node implemented in Rust

current architecture:
    ROS interfaces available
    Rust toolchain available
    client binding unavailable

missing edges:
    language generator
    generated type support
    package/build integration

classification:
    REDESIGN_REQUIRED
```

Or, if implementations already exist but are absent:

```text
classification:
    PREPARATION_REQUIRED

route:
    install provider components
    resolve interface packages
    generate types
    build
```

This distinction is especially powerful for emerging ecosystems.

---

## 86. A Fourth Deep Interface Is “What Did This Result Depend On?”

For example:

```text
$ wsx provenance image:sha256:XYZ

source:
    commit abc123

environment:
    lock 91f...

build:
    execution B7

tests:
    suite T4 passed

packaging:
    OCI exporter v...

runtime contract:
    R2
```

This supports reproduction and debugging after the original development session has ended.

---

## 87. This Suggests a Small Set of Architectural Invariants

A robust implementation should preserve at least these invariants.

### Identity invariant

Workspace identity is distinct from one host realization.

### Dependency invariant

A capability is not reported reachable unless its required path composes.

### Evidence invariant

Declared, detected, verified, observed, and unknown state remain distinct.

### Provenance invariant

Important derived outputs retain enough relation to their inputs and realization environment.

### Reopenability invariant

Hidden structure can be exposed when a higher-level summary becomes insufficient.

### Scope invariant

Deployment operation remains downstream unless explicitly represented as an external provider.

### Preference invariant

Available routes are not silently equated with desired routes.

---

## 88. Failure Modes

### Command-wrapper collapse

Everything becomes an arbitrary shell command, eliminating semantic navigation.

### Universal-provider overreach

The core attempts to understand every ecosystem directly.

### Backend collapse

Docker-specific assumptions become synonymous with workspace semantics.

### Health without capability

Metrics are reported without saying which capability they protect.

### Binary reachability

`works` and `does not work` replace richer distinctions such as preparation, unknown, blocked, and redesign-required.

### Hidden provenance

Artifacts exist without a persistent account of what produced them.

### Reproduction overclaim

A repeatable setup is described as bit-reproducible without sufficient guarantees.

### Documentation dependence

The real architecture remains encoded only in prose and human memory.

### Example dependence

Users can act only by copying existing implementations.

### Validation-only tooling

Parsers and type systems reject invalid states but do not expose constructive next possibilities.

### Architecture-as-goal confusion

The infrastructure begins choosing goals rather than representing viable paths.

### Kubernetes drift

Workspace state management grows into persistent deployment orchestration.

### Dashboard drift

Development-state observability expands into unrelated runtime application visualization.

### Premature universal GUI

A visualization layer is built before the semantic graph is stable.

### Opaque automation

The system executes repairs without exposing why they were selected or what they change.

---

## 89. A Candidate Construction Sequence

A practical project could proceed as follows.

```text
1. Define persistent workspace identity.

2. Define typed state and transformation primitives.

3. Implement workspace discovery.

4. Implement current-state observation.

5. Implement host and Docker backends.

6. Implement one demanding provider, such as ROS 2.

7. Represent build/test/exec paths.

8. Add capability-relative doctor checks.

9. Add provenance for derived states.

10. Add repair planning.

11. Add route explanation:
        where am I?
        why blocked?
        what next?
        what would make this reachable?

12. Add artifact export.

13. Preserve deployment as a downstream boundary.

14. Only then explore richer cross-layer constructive guidance.
```

The first demanding provider is valuable because it tests:

```text
system dependencies
build systems
generated interfaces
environment sourcing
multiple languages
hardware access
containers
network semantics
middleware
large dependency graphs
```

If the abstraction survives that case, broader reuse becomes more plausible.

---

## 90. The Initial Project Need Not Solve General Program Synthesis

The most ambitious constructive-guidance ideas should not inflate the initial scope.

Version one can focus on:

```text
workspace identity
environment realization
state
health
repair
build
test
exec
artifact export
```

The underlying architecture should nevertheless avoid assumptions that prevent later extension toward:

```text
schema-guided construction
type-directed suggestions
interface-path explanation
cross-layer completion
```

This preserves an evolution path without requiring premature implementation.

---

## 91. The Google Maps Analogy Can Be Stated Precisely

The analogy is not:

> developers need a graphical map.

It is:

```text
physical transport                  development

road network                        available tool/interface graph
current position                    current workspace state
vehicle capabilities                backend/provider capabilities
road restrictions                   constraints/preconditions
closure                             broken/unavailable edge
route                               action composition
destination                         declared target capability
detour                              alternative realization
bridge construction                 architecture extension
traffic/road health                 current realization viability
navigation explanation              dependency/provenance explanation
map zoom                            abstraction reopening
```

Most importantly:

```text
the map does not choose the destination.
```

The development system exposes viable continuation.

The user selects the target.

---

## 92. The Architecture Is Valuable Even Without AI

Nothing in the core requires a language model.

A deterministic system can already provide:

```text
dependency traversal
route search
constraint validation
state comparison
health checks
provenance
repair plans
schema enumeration
type-directed candidate filtering
```

AI may later help with:

```text
interpreting intent
explaining unfamiliar paths
mapping unstructured documentation into candidate provider knowledge
proposing missing architecture edges
```

But the semantic graph should remain inspectable independently.

This reduces the risk that assistance becomes ungrounded guesswork.

---

## 93. AI Becomes More Useful When It Has a Map

An assistant without architecture often sees:

```text
error message
repository text
documentation
```

and guesses a plausible command.

An assistant with the capability graph can reason over:

```text
current state
declared target
verified provider semantics
blocked edges
available repair paths
provenance
```

Then suggestions can be grounded in explicit workspace structure.

The map therefore improves both human and machine navigation.

---

## 94. The Architecture Can Preserve User Autonomy

Because possibility and preference remain separate, the system can expose:

```text
three viable routes
```

without selecting one silently.

It can say:

```text
Route A
    fastest
    mutates host

Route B
    isolated
    slower

Route C
    remote
    requires network
```

The developer chooses.

This is a better architecture than one hidden automation path whose tradeoffs are invisible.

---

## 95. A More General Principle of Constructive Infrastructure

The discussion suggests a broader pattern.

Infrastructure becomes more usable when it exposes not only:

```text
what exists
```

but:

```text
what can be constructed from what exists.
```

A schema is more useful when it supports valid construction.

A type system is more useful when it supports type-directed discovery.

A build graph is more useful when it exposes producible targets.

A package graph is more useful when it explains providers of missing capability.

A workspace model is more useful when it exposes reachable development states.

Thus:

\[
\boxed{
\text{constructive infrastructure makes its continuation space addressable}
}
\]

---

## 96. The Development Environment Becomes a Represented Possibility Space

The strongest conceptual shift is therefore:

```text
environment
```

should not mean only:

```text
set of environment variables
```

or:

```text
container filesystem.
```

It is more usefully treated as:

> the currently realized support structure within which a selected family of development transformations is available.

This includes:

```text
tools
versions
dependencies
generated interfaces
permissions
devices
runtime assumptions
backend capabilities
build state
```

but only as far as they change the relevant continuation space.

---

## 97. The Workspace Becomes a Persistent Continuation Architecture

Likewise:

```text
workspace
```

should not mean only:

```text
folder containing src/.
```

It becomes:

> a persistent identity around source, declared capability, realized environments, derived state, provenance, and available development continuations.

This identity can survive:

```text
host changes
backend changes
environment recreation
build cleanup
container deletion
```

because no single realization is the workspace itself.

---

## 98. The Artifact Becomes a Stabilized Boundary Object

An artifact is then one stabilized result of the workspace architecture.

It may become a relative primitive for another system.

For example:

```text
source + build environment + tests
→ OCI image
```

After the image is stabilized:

```text
Kubernetes
```

does not need to reopen every compiler command.

It can treat the image as a primitive under its own contract.

This is compositional scale.

The workspace system's job is to preserve enough provenance that the image can later be reopened if deployment evidence makes lower-level distinctions relevant.

---

## 99. Development and Deployment Become Adjacent Layers Rather Than Disconnected Worlds

A common tooling experience is:

```text
development scripts
```

and:

```text
deployment manifests
```

with little explicit relation.

The proposed architecture connects them through stable boundary objects:

```text
verified artifact
runtime contract
provenance
```

This gives:

```text
development realization
→ stabilized artifact contract
→ deployment realization
```

without requiring one mega-platform to own both.

That middle boundary is likely the right integration point.

---

## 100. Central Principles

### Development-Map Principle

> A development environment should expose the currently available states, transformations, constraints, and continuation paths rather than requiring users to reconstruct them from scattered implementation detail.

### Infrastructure-Potential Principle

> Existing infrastructure primarily defines supported and constrained possibilities; it need not select the developer's desired target.

### Reachability-Before-Execution Principle

> A requested capability should be evaluated against the currently realized transformation graph before it is treated as executable.

### Capability-as-Path Principle

> A development capability exists when a viable composed path through providers, backends, interfaces, dependencies, and resources realizes it.

### Existing-Road Principle

> Established compilers, package managers, build systems, container runtimes, middleware, and deployment tools should be reused as stabilized transformations rather than unnecessarily reimplemented.

### Typed-Transformation Principle

> Development relations must preserve semantics such as requires, generates, builds, validates, executes, repairs, and exports rather than collapsing every edge into an untyped command.

### Provider Principle

> Providers encode ecosystem-specific development semantics.

### Backend Principle

> Backends encode where and under which isolation and execution semantics transformations are realized.

### Capability-Relative-Health Principle

> Health is meaningful only relative to the capability whose continuation the observed conditions are intended to protect.

### Selective-Doctor Principle

> Diagnostics should expose the smallest set of realization distinctions sufficient to explain capability viability, degradation, or failure.

### Repair-as-Reentry Principle

> Repair should restore the workspace to a capability-valid region rather than blindly reconstruct every detail.

### Persistent-Provenance Principle

> Important derived states and artifacts should remain connected to the source, environment, transformations, and evidence that produced them.

### Reproduction-Level Principle

> Repeatability, locked realization, environment reproducibility, build reproducibility, and bit reproducibility are different guarantees and should be named separately.

### Relative-Primitive Principle

> Repeatedly solved development compositions should become stable, addressable building blocks for later work.

### Architecture-Extension Principle

> A target reachable only after a new provider, bridge, generator, binding, or backend is added is redesign-dependent rather than currently reachable.

### Constructive-Validation Principle

> Knowledge used to reject invalid constructions can often be reused to expose valid next constructions.

### Cross-Layer-Completion Principle

> Constructive guidance may connect syntax, types, schemas, packages, environments, and capabilities when their interfaces are represented explicitly.

### Semantic-Zoom Principle

> Lower-level development structure should remain hidden while current summaries are sufficient and reopen when a new question depends on discarded distinctions.

### Explanation Principle

> Route selection, failure, repair, and next-step guidance should be explainable from explicit dependency and provenance structure.

### Preference-Separation Principle

> The architecture may expose and rank viable routes without confusing technical availability with the developer's goals or values.

### Development-Deployment Boundary Principle

> Development tooling should produce verified, provenance-bearing artifacts and runtime contracts; persistent deployment reconciliation should remain the responsibility of deployment systems.

### Non-Discard Principle

> Development infrastructure should preserve reusable environment, dependency, diagnostic, and provenance structure after an artifact is produced rather than discarding the knowledge that made the artifact possible.

---

## 101. A Compact Architecture

The resulting architecture can be summarized as:

```text
                             USER TARGET
                                  │
                                  ▼
                         route / capability query
                                  │
                                  ▼
                    ┌───────────────────────────┐
                    │      WORKSPACE MAP        │
                    │                           │
                    │ current state             │
                    │ typed transformations     │
                    │ dependencies              │
                    │ constraints               │
                    │ health / viability        │
                    │ provenance                │
                    │ repair paths              │
                    └─────────────┬─────────────┘
                                  │
                    ┌─────────────┴─────────────┐
                    │                           │
                 PROVIDERS                   BACKENDS
                    │                           │
              ROS / Python /                host / Docker /
              CMake / Cargo / ...          Podman / Nix / ...
                    │                           │
                    └─────────────┬─────────────┘
                                  │
                                  ▼
                         EXISTING ECOSYSTEM
                                  │
                 compilers / generators / package
                 managers / build systems / runtimes
                                  │
                                  ▼
                         verified artifact
                                  │
                         persistent provenance
                                  │
                 ─────────── handoff ───────────
                                  │
                                  ▼
                      deployment / operation
                      Kubernetes / Flux / ...
```

The architecture does not replace the ecosystem.

It makes the ecosystem navigable.

---

## 102. Conclusion

Development systems already contain enormous amounts of organized structure.

A compiler knows which constructions are syntactically and semantically valid.

A type system knows which values satisfy which interfaces.

A schema knows which fields and relations constitute a valid message.

A package manager knows dependency structure.

A build system knows how targets are produced.

A container system knows how an isolated execution environment is realized.

A middleware stack knows how language-level operations connect to transport.

An OCI system knows how runtime artifacts are represented and moved.

A deployment system knows how artifacts become managed workloads.

Yet the developer often experiences these systems as disconnected commands.

The missing problem is therefore not simply automation.

It is representation.

A finite developer cannot keep the complete architecture active in working memory.

Nor should they need to reconstruct it from first principles every time.

The relevant task is to stabilize the intermediate structure:

```text
what exists
what it means
what it requires
what it produces
what is currently realized
what is currently viable
what can be reached
what is blocked
what can be repaired
what would require redesign
what produced the current artifact
and which next transformations remain available
```

This makes development more like navigation.

The existing ecosystem supplies the roads and the rules.

The workspace model supplies the map.

The current machine state determines the present position.

Providers expose domain-specific roads.

Backends expose realization alternatives.

Health checks expose closures and weakened bridges.

Repair restores routes.

Build, test, execution, and export are traversals.

New language bindings or tool integrations construct new roads.

Artifacts become stable boundary objects for deployment.

Deployment systems then operate at the next scale without requiring the development architecture to become a cluster orchestrator.

The central proposal can therefore be stated compactly:

\[
\boxed{
\begin{aligned}
&\text{existing technical infrastructure}\\
&\xrightarrow{\text{representation}}
\text{typed development capability graph}\\
&\xrightarrow{\text{observation}}
\text{current workspace position and viability}\\
&\xrightarrow{\text{target query}}
\text{reachable, blocked, and redesign-dependent routes}\\
&\xrightarrow{\text{execution}}
\text{builds, tests, runtime actions, and artifacts}\\
&\xrightarrow{\text{persistence}}
\text{reusable state, provenance, repair knowledge, and relative primitives}\\
&\xrightarrow{\text{handoff}}
\text{downstream deployment and operation}.
\end{aligned}
}
\]

And the corresponding practical principle is:

\[
\boxed{
\text{do not make developers memorize the road network;
make the development architecture itself navigable}
}
\]

---

## Related Foundational Works

This synthesis develops a concrete software-architecture consequence of themes explored in:

```text
Compositional Factorization and Finite Leverage:
Representation, Addressability, Universality, and Scale

From Interfaces to Representation Formation:
Question-Relative Sufficiency, Factorization, and Scale-Independent Abstraction

From Questions to Composable Interfaces:
Sufficiency, Factorization, Shared State, and Scalable Architecture

From Function to Viable Realization:
Operating Regimes, Local Condition Flow, Bottlenecks, and Recursive Architecture

From Abstraction to Realizable Classification:
Dependency, Coherence, Perturbation, and the Physical Cost of Stable Meaning

From Interaction Dependencies to Organized Constraint:
Regularity, Non-Commutativity, Viability, and Architecture-Relative Control

From Lawful Evolution to Hierarchical Interaction Organization:
Constraints, Realization, Scale, and Architecture-Relative Meaning

From Lawful Transformation to Organized Interaction:
Persistent Difference, Finite Capacity, Throughput, and the Derivation of Interaction Architecture

From Role-Bound Identity to Viable Interaction Architecture:
Protocol-Relative Equivalence Classes, Reachability Before Desire,
and Reopenable Human-Agent Infrastructure

From Distributed Identity to Viable Self-Continuation:
Typed Distinction Networks, Enabling and Constraining Supports,
Commitment-Relative Corridors, and Reopenable Identity Architecture
```

The present document narrows those general frameworks to the development-workspace problem.

Its distinctive claim is that reproducible development should be treated not merely as environment reconstruction, but as the persistent representation and navigation of a capability space.
