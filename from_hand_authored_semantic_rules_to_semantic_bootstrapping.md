# From Hand-Authored Semantic Rules to Semantic Bootstrapping: Reflective Discovery, Rule Synthesis, Validation, and Persistent Knowledge

## Abstract

A goal-directed development system should not require a manually maintained ontology describing every version of every tool, language runtime, middleware, package manager, build system, CLI, and deployment environment.

That approach does not scale.

The more promising architecture is to begin from a much smaller question:

```text
What semantic structure can be discovered from the environment that is actually accessible now?
```

and then ask:

```text
What objects exist?
Which of them can be inspected?
Which expose schemas, registries, metadata, types, signatures, grammars, interfaces, or dependency structure?
Which can be executed safely?
Which can be probed experimentally?
Which candidate semantic rules can be extracted?
How can those rules be validated?
Which discovered rules are specific to this version, environment, scope, or configuration?
Which discovery methods are reusable across many systems?
Which results should be cached and reused?
Where does automated discovery stop and human interpretation become necessary?
```

The central proposal is:

\[
\boxed{
\text{do not primarily author domain rules;
author and validate methods for discovering rules}
}
\]

A useful system therefore combines two forms of goal-directed reasoning:

```text
target elaboration
    reasons with semantic rules

semantic bootstrapping
    discovers, tests, and admits semantic rules
```

The same epistemic discipline should govern both.

A discovered rule is not automatically architectural truth. It is a candidate supported by evidence, scoped to an environment, and admitted only when its extraction and validation satisfy an appropriate trust policy.

The long-term objective is not a universal hand-written knowledge base.

It is a small semantic bootloader capable of locating useful machine-readable structure, expanding it recursively, testing uncertain behavior, persisting validated knowledge, and requesting human assistance only at the remaining semantic frontier.

---

## 1. The Rule-Authoring Problem Is the Wrong Scaling Problem

Suppose a development system wants to reason about:

```text
ROS 2
Python
Bash
Docker
CMake
Cargo
Kubernetes
systemd
GPU runtimes
network services
package managers
generated interfaces
build tools
cloud CLIs
```

A direct rule-authoring approach suggests:

```text
write semantic rules for ROS 2
write semantic rules for Python
write semantic rules for Docker
write semantic rules for every CLI
update them for every release
repeat forever
```

This is structurally unattractive.

Software versions change.

Plugins add new behavior.

Generated interfaces change.

CLI grammars change.

Packages install new entry points.

Environment variables alter interpretation.

Build configuration changes available targets.

Runtime capabilities depend on the current host, container, device, network, credentials, and policy.

A static semantic inventory therefore becomes stale precisely where useful reasoning needs to remain environment-specific.

The more scalable question is:

> What generic methods can discover useful semantics from whatever software environment is actually present?

This moves the engineering effort from:

```text
enumerating behavior
```

toward:

```text
discovering behavior
extracting structure
validating structure
remembering validated structure
```

The important reusable artifact is no longer primarily:

```text
Rule #1837:
ROS2 Jazzy package resolution behaves like ...
```

It becomes something closer to:

```text
Method:
when an installed ecosystem exposes a package registry,
enumerate it and derive package-identity candidates.

Method:
when a CLI exposes structured help or completion metadata,
derive a candidate command grammar.

Method:
when an interface description language is present,
derive typed message/service/action propositions.

Method:
when static semantics remain uncertain,
execute a constrained differential probe and validate the candidate relation.
```

These methods can survive version churn because they interrogate the installed system rather than assuming that the installed system still matches a previously authored description.

---

## 2. The Central Distinction: Domain Rules and Discovery Rules

A goal-directed rule system may contain ordinary semantic or domain rules such as:

```text
DockerBackendReady
AND CompatibleROSImage
AND RequiredDeviceMappingRepresentable
→ ROS2EnvironmentRealized
```

Such a rule says something about the domain.

But there is another class of rule:

```text
PythonDistribution(x)
→ EntryPointMetadataQueryable(x)
```

followed by an observation effect:

```text
EntryPointMetadataQueryable(x)
--EnumerateEntryPoints-->
CandidateEntryPoints(x, entries)
```

or:

```text
CLIExecutable(x)
--InspectHelpSurface-->
CandidateCommandGrammar(x, grammar)
```

or:

```text
InterfaceDefinitionArtifact(x)
--ParseInterfaceSchema-->
CandidateTypedInterface(x, schema)
```

These are not ordinary domain rules.

They are **discovery rules**, **metarules**, or **semantic extraction methods**.

They explain how additional semantic structure can become known.

A useful architecture therefore distinguishes:

```text
DOMAIN RULE
    describes one way a proposition can be justified or realized

DISCOVERY RULE
    describes one way semantic objects, claims, or rules can be discovered
```

The second class is the scaling mechanism for the first.

---

## 3. Rules Are Often Already Latent in the Environment

Modern software systems already contain large amounts of semantic structure.

The problem is usually not total absence.

The problem is fragmentation.

Useful information may be distributed across:

```text
package metadata
plugin registries
entry-point registries
type annotations
function signatures
reflection APIs
argument parser definitions
shell completion specifications
interface definition languages
OpenAPI schemas
protocol descriptors
generated code
build-system metadata
dependency manifests
lockfiles
binary metadata
dynamic-link information
environment variables
configuration files
runtime registries
introspection commands
tests
examples
source code
observed behavior
```

Each representation exists for a local purpose.

For example:

```text
argument parser
    exists to parse commands

IDL
    exists to generate interoperable types

package metadata
    exists to describe installed distributions

plugin registry
    exists to discover extensions

type hints
    exist for static reasoning and tooling

tests
    exist to validate behavior
```

What is usually missing is a common question over all of them:

```text
What semantic propositions, operations, prerequisites,
effects, observations, and typed boundaries can this artifact justify?
```

Semantic bootstrapping is the process of turning these fragmented local representations into target-relevant rule structures.

---

## 4. The Environment Is Not Merely State; It Is a Search Space for Semantics

Traditional environment inspection asks:

```text
What files exist?
What packages are installed?
What commands are on PATH?
What processes are running?
```

A semantic bootstrapping system asks a stronger question:

> Which accessible objects may contain machine-usable semantics, and which discovery operations are applicable to them?

Let the current accessible environment expose a set of objects:

\[
\mathcal O.
\]

Objects may include:

```text
files
directories
executables
libraries
packages
modules
classes
functions
processes
sockets
devices
registries
schemas
services
containers
build targets
configuration objects
runtime graph entities
```

The system does not initially need to know the full semantics of these objects.

It needs enough primitive knowledge to determine:

```text
what can be located
what can be read
what can be queried
what can be imported
what can be executed
what can be isolated
what can be observed
what can be modified
what policy permits
```

This is the **discovery context**.

---

## 5. A Semantic Bootstrapping Kernel

The initial bootstrapping kernel can remain small.

It may know only a bounded set of primitive affordances:

```text
ResolvePath(name)
EnumerateDirectory(path)
ReadArtifact(path)
IdentifyFileType(path)
IdentifyExecutable(path)
QueryEnvironmentVariable(name)
EnumerateEnvironment()
QueryPackageDatabase(...)
InspectBinaryMetadata(...)
LoadLanguageRuntime(...)
ImportModule(...)
ReflectObject(...)
InvokeExecutable(...)
CaptureOutput(...)
ObserveFilesystemDelta(...)
ObserveProcessDelta(...)
ObserveNetworkDelta(...)
CreateIsolatedEnvironment(...)
DestroyIsolatedEnvironment(...)
```

These operations do not encode ROS, Python frameworks, Docker, or application-specific semantics.

They merely provide controlled access to possible semantic entry points.

The kernel then asks:

```text
Given object x,
which discovery methods are applicable?
```

A method may produce:

```text
new objects
candidate propositions
candidate rules
candidate observers
candidate effect descriptions
new discovery methods
```

Thus semantic discovery can recursively enlarge its own search space.

---

## 6. Discovery Methods Are Typed Transformations

A discovery method should not be an arbitrary script whose output is silently trusted.

It should have a contract.

Conceptually:

```yaml
discovery_method:
  id: enumerate-python-entry-points

  applies_to:
    - PythonDistribution($distribution)

  requires:
    - PythonMetadataReadable($distribution)

  observes:
    - EntryPointDeclarations($distribution)

  produces:
    objects:
      - PythonEntryPoint(...)

    candidate_claims:
      - RegisteredEntryPoint(...)

    candidate_rules:
      - ...

  side_effects:
    mutation: none

  evidence_kind:
    declared_metadata

  invalidated_by:
    - distribution_identity_changed
    - environment_identity_changed
```

A different method may inspect a CLI:

```yaml
discovery_method:
  id: infer-cli-grammar-from-help

  applies_to:
    - Executable($x)

  requires:
    - ExecutionPermitted($x)

  effect:
    kind: KNOWLEDGE
    operation: invoke_help_surface

  produces:
    candidate_claims:
      - HasSubcommand(...)
      - HasOption(...)
      - AcceptsArgument(...)

  evidence_kind:
    executable_introspection

  confidence:
    provisional
```

The important property is that the semantic extractor is itself inspectable, testable, versionable, and scoped.

---

## 7. Semantic Discovery Is Itself Goal-Directed

A universal crawler would be wasteful.

The system should not inspect every executable, import every Python module, parse every source file, or probe every device merely because it can.

The target should induce the semantic search.

Suppose the target contains:

```text
ros2 launch robot_bringup hardware.launch.py
```

The system may initially know only that:

```text
token "ros2" occurs in an executable position
```

That creates an obligation:

```text
InterpretExecutableToken("ros2")
```

The discovery planner can then search for applicable methods:

```text
PATH lookup
package ownership lookup
executable metadata inspection
help-surface probing
runtime tracing
source resolution
```

Once enough semantics are discovered to interpret:

```text
ros2 launch
```

there is no need to explore unrelated subcommands unless the target later requires them.

Thus:

\[
\boxed{
\text{semantic discovery should be target-relative}
}
\]

just as ordinary rule elaboration is target-relative.

---

## 8. Recursive Discovery Produces a Semantic Neighborhood

A powerful property of discovery is that one entry point reveals more entry points.

For example:

```text
PATH
↓
ros2 executable
↓
owning installation/distribution
↓
registered CLI extension mechanism
↓
subcommand providers
↓
package metadata
↓
interface definitions
↓
runtime graph observers
↓
typed topics/services/actions
```

Likewise:

```text
Python executable
↓
installed distributions
↓
entry points
↓
importable modules
↓
objects
↓
signatures
↓
annotations
↓
registries
↓
framework-specific schemas
```

The result is not merely metadata extraction.

It is a recursively generated **semantic neighborhood** around the target.

Let:

\[
N_0(T)
\]

be the immediately discoverable objects relevant to target \(T\).

Each discovery step may produce:

\[
N_{i+1}(T)
=
N_i(T)
\cup
\operatorname{Discover}(N_i(T)).
\]

Expansion stops when:

```text
the target can be interpreted and elaborated sufficiently

OR

additional discovery has lower expected value than another action

OR

policy prohibits deeper inspection

OR

the semantic frontier has been reached
```

No complete universe needs to be materialized.

---

## 9. Discovery Can Produce Rules About How to Discover More Rules

Some discovered objects may reveal new semantic extraction mechanisms.

This is important.

Suppose a framework exposes a plugin registry.

The bootloader may initially know only:

```text
RegistryLikeObject(x)
```

Inspection may reveal:

```text
registry entries reference classes implementing interface I
```

The system can then instantiate a more specialized discovery strategy:

```text
for each registered class:
    inspect declared interface
    inspect constructor contract
    inspect factory metadata
    inspect generated schema
```

This makes mechanisms such as:

```text
Dynamic Class Generation Factory
metaprogramming
plugin systems
decorator registries
dependency injection containers
code generators
reflection registries
```

especially valuable.

They are not merely implementation tricks.

They can serve as **semantic compression points** where many concrete behaviors are generated from a smaller structural mechanism.

Instead of enumerating all generated classes, commands, or handlers manually, the system can discover the generator or registry and derive the current family on demand.

---

## 10. The Most Valuable Rules May Be Rules for Finding Compression Points

Version-specific leaf behavior changes frequently.

Structural mechanisms often change more slowly.

Examples include:

```text
this package registers commands through entry points

this framework generates message classes from IDL

this CLI constructs subcommands from a registry

this build system derives targets from these manifests

this application discovers plugins implementing interface I

this code generator maps schema S to runtime representation R
```

If the system discovers one such mechanism, it may derive hundreds of target-specific facts without storing hundreds of manually authored rules.

This suggests a strong design principle:

> Search first for generative mechanisms, registries, schemas, and reflective boundaries before enumerating individual behaviors.

Call these locations **semantic compression points**.

A semantic compression point is an artifact or mechanism from which a large family of useful semantic relations can be reconstructed.

---

## 11. Semantic Contracts Should Be Extracted at the Highest Useful Level

Suppose a user calls a Python function.

They ordinarily do not need to know:

```text
bytecode
interpreter dispatch
memory layout
C runtime internals
machine instructions
```

They need a sufficient contract such as:

```text
callable identity
accepted arguments
return structure
exceptions
effects
preconditions
relevant type constraints
```

Likewise, a compiler user normally does not need to inspect the compiler's internal intermediate representation.

The implementation contains enormous detail.

But a useful semantic boundary compresses that detail.

A bootstrapping system should therefore prefer:

```text
declared contract
```

over:

```text
implementation reconstruction
```

whenever the declared contract is sufficient for the target.

The system should reopen lower layers only when:

```text
the exposed contract is incomplete

the contract is contradicted by evidence

the target requires a hidden distinction

the contract cannot answer the required question

validation fails

version/configuration drift makes the contract uncertain
```

This is semantic zoom applied to discovery.

---

## 12. Source Code Is an Evidence Source, Not the Default Interface

Source inspection is powerful.

It is also expensive and often semantically noisy.

Implementation code contains:

```text
temporary variables
internal control flow
optimization details
compatibility paths
error handling
instrumentation
implementation-specific abstractions
dead or unreachable branches
```

These details may be irrelevant to the target.

Therefore the preferred sequence should usually be:

```text
machine-declared schema
↓
registered metadata
↓
reflection
↓
generated artifacts
↓
structured CLI introspection
↓
runtime introspection
↓
tests and examples
↓
source-level structural analysis
↓
controlled behavioral experiment
↓
human interpretation
```

This is not a universal ordering.

A domain may rearrange it.

The principle is:

> Use the cheapest and strongest semantic boundary that can discharge the current obligation.

Reading source code is appropriate when higher-level contracts fail.

It should not be required merely to use ordinary exposed behavior.

---

## 13. The Semantic Evidence Ladder

Different discovery surfaces support different strengths of inference.

A useful system should retain this distinction.

For example:

### Declared schema

```text
IDL
OpenAPI
protocol schema
typed manifest
formal plugin interface
```

Supports strong structural claims.

### Registered metadata

```text
entry points
package metadata
plugin registry
build target registry
```

Supports identity and discoverability claims.

### Reflection

```text
function signature
class hierarchy
annotations
runtime descriptors
```

Supports callable and type-structure claims.

### Structured introspection

```text
CLI command tree
runtime graph query
package query
service discovery
```

Supports environment-specific current claims.

### Tests

Supports behavioral evidence under tested conditions.

### Source analysis

Supports candidate relations derived from implementation structure.

### Controlled experiment

Supports empirical behavioral claims within the experimental scope.

### Human interpretation

Supports candidate semantics when existing machine surfaces are inadequate.

The evidence source should remain attached to the claim or candidate rule.

A rule derived from an IDL declaration should not be epistemically identical to a rule guessed from a help string.

---

## 14. Candidate Rules Need a Lifecycle

Discovered semantic structure should not immediately enter the trusted rule set.

A candidate may move through states such as:

```text
DISCOVERED
    extraction produced a candidate

STRUCTURALLY_SUPPORTED
    candidate follows from a machine-readable structure

CORROBORATED
    independent evidence agrees

EXPERIMENTALLY_VALIDATED
    relevant behavior was tested

HUMAN_VALIDATED
    a human accepted the interpretation

TRUSTED_METHOD_DERIVED
    produced by an extraction method trusted for this class

ADMITTED
    planner may use it under its declared scope

STALE
    validity conditions no longer hold

CONTRADICTED
    later evidence disagrees

REJECTED
    candidate should not be used
```

The exact vocabulary is secondary.

The important invariant is:

```text
candidate semantic structure
≠
trusted semantic rule
```

This mirrors the distinction between effect success and semantic postcondition success.

---

## 15. Rules Themselves Can Have Claims and Provenance

If ordinary propositions require evidence, discovered rules require provenance too.

A rule may carry:

```yaml
rule:
  id: discovered-rule-73

  conclusion:
    ...

  premises:
    ...

  origin:
    discovery_method: parse-interface-schema
    artifact: ...
    artifact_digest: ...

  scope:
    environment_digest: ...
    package_version: ...
    architecture: ...
    configuration_digest: ...

  evidence:
    - declared_schema
    - runtime_validation

  confidence:
    validated

  validity:
    invalidated_by:
      - package_identity_changed
      - interface_artifact_changed
      - runtime_configuration_changed
```

This makes rules environment-sensitive without requiring a separate manually versioned rule file for every environment.

---

## 16. Version Churn Becomes an Invalidation Problem

A manually maintained ontology treats a version change as:

```text
someone must update the knowledge base
```

A semantic bootstrapping system can treat many version changes as:

```text
previous rule evidence became stale
→ invalidate
→ rediscover
→ revalidate
```

For example:

```text
CLI executable digest changed
```

may invalidate:

```text
command grammar derived from previous executable
```

A changed interface-definition digest may invalidate:

```text
message schema
generated type relations
serialization assumptions
```

A changed environment may invalidate:

```text
plugin registry contents
package resolution
available subcommands
runtime capabilities
```

Thus version drift is transformed from a documentation-maintenance problem into an evidence-validity problem.

This does not eliminate compatibility work.

It changes where the compatibility work happens.

---

## 17. The Initial Question Is: What Is Accessible Here?

Semantic bootstrapping needs a starting boundary.

Before asking what ROS, Python, or any package means, the system needs to know:

```text
what execution context am I in?

what filesystem can I inspect?

what executable search path exists?

what package databases are available?

what runtimes can be invoked?

what environment variables are visible?

what credentials are available?

what network access is permitted?

what containers or sandboxes may be created?

what devices are visible?

what mutation is permitted?

what observations are permitted?
```

This can be represented as a set of initial claims:

```text
ReadablePath(...)
ExecutableSearchPath(...)
ExecutionPermitted(...)
NetworkPolicy(...)
MutationPolicy(...)
IsolationAvailable(...)
PythonRuntimeAvailable(...)
PackageDatabaseQueryable(...)
```

These are not universal facts.

They describe the current semantic search boundary.

---

## 18. Discovery Context Is Part of the Planning Context

Let:

\[
K_D
\]

be the discovery context.

It may contain:

```text
accessible namespaces
permissions
execution policy
isolation capabilities
available runtimes
known artifact types
trusted discovery methods
cost limits
network policy
source-access policy
human-escalation policy
```

Given a target \(T\), the system searches simultaneously over:

```text
how to justify T
```

and, when required:

```text
how to discover enough semantics to know how T could be justified
```

This creates two interacting frontiers:

```text
REALIZATION FRONTIER
    what must become true?

SEMANTIC FRONTIER
    what must become understood?
```

A target can be blocked by either.

---

## 19. Unknown Semantics Should Not Collapse Into Unsupported Behavior

Suppose the system encounters:

```text
fooctl deploy x
```

and no provider understands `fooctl`.

Several cases are possible:

```text
executable does not exist

executable exists but has not been inspected

metadata exists but has not been parsed

help surface exists but has not been probed

source exists but no analyzer is available

execution is possible but policy forbids probing

candidate semantics exist but remain unvalidated

no represented discovery route remains
```

These are different states.

A useful classification might include:

```text
SEMANTICS_UNOBSERVED

SEMANTIC_DISCOVERY_AVAILABLE

SEMANTIC_DISCOVERY_BLOCKED

CANDIDATE_SEMANTICS_AVAILABLE

SEMANTIC_EVIDENCE_INSUFFICIENT

SEMANTIC_EXTRACTOR_MISSING

SEMANTIC_FRONTIER

INVALID
```

Only the last appropriate state should mean:

```text
the current architecture cannot presently continue
```

It still should not mean:

```text
the software has no semantics
```

---

## 20. A Generic Discovery Hypergraph

Discovery can use the same AND/OR machinery as target elaboration.

Suppose the system wants:

```text
SemanticContract(ros2)
```

Alternative routes may be:

```text
InstalledMetadataRoute
OR
StructuredIntrospectionRoute
OR
SourceAnalysisRoute
OR
BehavioralProbeRoute
OR
HumanInterpretationRoute
```

Each route has premises.

For example:

```text
StructuredIntrospectionRoute
AND
├── ExecutableResolvable(ros2)
├── ExecutionPermitted(ros2)
└── IntrospectionSurfaceAvailable(ros2)
```

Source analysis may require:

```text
SourceAnalysisRoute
AND
├── ImplementationSourceResolvable(ros2)
├── SourceReadable
└── ApplicableAnalyzerAvailable
```

Thus semantic discovery is naturally another target-relative directed hypergraph.

The target itself may therefore create nested elaborations:

```text
need proposition P
↓
need rule establishing P
↓
rule semantics unknown
↓
need SemanticContract(x)
↓
discover x
↓
derive candidate rule
↓
validate candidate rule
↓
resume elaboration of P
```

---

## 21. Discovery and Realization Can Interleave

Sometimes semantic discovery is purely observational.

Sometimes discovering semantics requires constructing a temporary world.

For example:

```text
Will this generated plugin actually register?
Will these dependencies compose?
What runtime object is created from this configuration?
Which command tree appears after plugin installation?
```

The system may need:

```text
temporary environment
candidate installation
controlled execution
observation
validation
discard
```

This is a discovery experiment.

Its primary purpose is knowledge, even though it performs world-changing effects inside an isolated scope.

Thus the existing distinction remains useful:

```text
WORLD
KNOWLEDGE
BOTH
```

Semantic bootstrapping makes the `BOTH` category particularly important.

---

## 22. Differential Probing Can Infer Behavioral Rules

When no useful declarative contract exists, behavior can sometimes be inferred experimentally.

Suppose an executable accepts a configuration value \(x\).

The system can compare:

```text
baseline environment
candidate environment with x changed
```

and observe:

```text
exit status
stdout/stderr structure
files created
processes created
network activity
registered runtime entities
timing
resource use
```

A candidate relation may be generated:

```text
Configuration(x=v)
→ ObservedBehavior(B)
```

This is not automatically a universal law.

It is an experimentally supported scoped rule.

Its validity may depend on:

```text
version
host
architecture
environment
input class
timing
external services
```

A mature system should prefer narrow validated claims over broad unjustified generalization.

---

## 23. Discovery Should Search for Schemas Before Instances

Suppose a runtime contains 5,000 model classes or 800 commands.

Enumerating and understanding each one independently may be wasteful.

A better search strategy is:

```text
find the registry
find the factory
find the base protocol
find the schema
find the generator
find the dispatch table
find the metaclass
find the declaration mechanism
```

Then derive the current instance family.

This is analogous to searching a pool of candidate models for objects satisfying an interface rather than maintaining a static list of every model ever created.

The question becomes:

\[
\text{Find } x \in \mathcal O
\text{ such that } x \text{ exposes structure relevant to requirement } R.
\]

For example:

```text
Find x such that:
    x describes callable objects
    AND signatures are inspectable
    AND generated objects can be enumerated
```

or:

```text
Find x such that:
    x describes message-like types
    AND field structure is recoverable
    AND runtime type identity can be validated
```

The discovery problem therefore resembles capability search over a dynamic object pool.

---

## 24. Semantic Search Can Be Requirement-Driven

Suppose the target needs something satisfying:

```text
TrainableModel
AND AcceptsDataset(D)
AND ProducesOutput(Y)
AND FitsResourceBudget(R)
```

The planner need not know every possible model in advance.

It can search the current pool for objects whose discoverable schemas satisfy the required interface.

The same applies to development tooling:

```text
Find x such that:
    CanEstablish(P)
```

or more concretely:

```text
Find x such that:
    Executable(x)
    AND HasOperation(x, Launch)
    AND AcceptsPackageIdentifier(x)
    AND AcceptsLaunchArtifact(x)
```

This reframes provider discovery as constrained semantic search rather than provider enumeration.

---

## 25. Reflective Providers

A traditional provider is a bounded source of semantic rules.

A **reflective provider** is a bounded source of methods that generate semantic rules from the current environment.

Examples:

```text
PythonReflectionProvider

CLIReflectionProvider

PackageMetadataProvider

BinaryMetadataProvider

BuildReflectionProvider

ROSReflectionProvider

ContainerReflectionProvider

RuntimeGraphProvider

SourceStructureProvider

ExperimentProvider
```

A reflective provider might not know:

```text
what packages are installed
what commands exist
what interfaces exist
```

until runtime.

It knows how to discover them.

This is a more durable boundary.

---

## 26. Providers May Be Partially Specified

A provider should not need to model its whole domain.

For example, a Python reflection provider may know how to extract:

```text
installed distributions
entry points
modules
classes
callable signatures
annotations
inheritance
```

but know nothing about:

```text
database effects
network semantics
business invariants
framework-specific lifecycle
```

That is acceptable.

The system should preserve:

```text
known
discoverable
candidate
unknown
```

rather than forcing every provider into apparent completeness.

Partial specification is a feature in an open-world system.

---

## 27. Human Assistance Belongs at the Semantic Frontier

Humans should not be treated as the primary database of all rules.

They are more valuable as validators and teachers of reusable extraction procedures.

A progression may look like:

### Stage 0 — Manual semantic investigation

```text
human finds relevant source, docs, schema, or runtime behavior
```

### Stage 1 — Assisted extraction

```text
system proposes semantic structure
human verifies each candidate
```

### Stage 2 — Method validation

```text
human verifies:
this generic extraction method is sound for this class of artifact
```

### Stage 3 — Trusted method reuse

```text
validated method generates candidate rules automatically
human inspects exceptions
```

### Stage 4 — Automatic bounded admission

```text
rules produced by a trusted method are automatically admitted
within declared scope and validation conditions
```

### Stage 5 — Frontier-only escalation

```text
human intervention occurs mainly when:
    no known semantic extraction route is adequate
    evidence conflicts
    interpretation is ambiguous
    policy requires approval
```

The objective is not to eliminate humans immediately.

It is to move human work upward from repetitive leaf-rule authoring toward validation of high-leverage discovery mechanisms.

---

## 28. AI Is Useful as a Semantic Hypothesis Generator

AI may help with:

```text
classifying unknown artifacts
suggesting likely introspection methods
mapping unstructured help text to candidate schemas
extracting candidate rules from source or documentation
identifying likely registries and factories
proposing validation experiments
explaining conflicts
ranking semantic entry points
```

But AI output should remain typed as:

```text
PROPOSED
UNVERIFIED
```

until supported by stronger evidence.

The important architectural distinction is:

```text
AI proposes semantic hypotheses
the rule system decides what evidence is sufficient to admit them
```

This allows increasing automation without allowing plausible text generation to silently become architectural truth.

---

## 29. Human Validation Can Train the System Without Conventional Model Training

The system can improve through persistent procedural knowledge even without updating neural model weights.

Suppose a human repeatedly confirms:

```text
for artifacts of class X,
discovery method M extracts reliable semantic structure
```

The system can persist:

```text
applicability conditions
method identity
validation history
known counterexamples
required corroboration
scope constraints
```

Future environments can reuse this method.

Thus the system learns operationally through:

```text
trusted discovery methods
cached extraction templates
validated provider adapters
negative knowledge
known invalidation conditions
```

This is architectural learning.

Machine learning may later assist ranking or extraction, but it is not required for the core mechanism.

---

## 30. Successful Discovery Should Compress Future Discovery

A successful semantic bootstrap can persist:

```text
object identity
artifact digest
discovery path
extraction methods used
candidate rules generated
validation evidence
admitted rules
scope
invalidators
provider versions
human decisions
```

Later targets can reuse the result as a cached semantic lemma.

For example:

```text
SemanticContract(
    executable=ros2,
    executable_digest=D1,
    environment_digest=E1
)
```

may be reused until:

```text
D1 changes
E1 changes materially
validation fails
a target requires a stronger contract
```

The system therefore converts expensive semantic investigation into reusable relative primitives.

---

## 31. Discovery Methods Themselves Should Be Cached and Versioned

There are two distinct things to persist:

### Discovered semantic knowledge

```text
this executable exposes these subcommands
this package provides this interface
this type has these fields
```

### Semantic discovery knowledge

```text
this method successfully extracts command grammars from artifacts of class C
this registry reveals generated plugin types
this probe distinguishes readiness from process existence
```

The second can be more valuable than the first.

A versioned discovery method should record:

```text
method implementation
applicability predicate
expected evidence
validation suite
known limitations
false-positive history
false-negative history
trusted scope
```

This makes semantic extraction infrastructure inspectable and reproducible.

---

## 32. Negative Discovery Knowledge Is Valuable

The system should remember failed approaches.

Examples:

```text
--help does not enumerate dynamically loaded subcommands for version X

source parser Y cannot resolve generated decorators in package P

registry R omits plugins loaded from environment variable E

probe Z is insufficient to establish readiness

artifact type A has no stable reflection API

method M produced false schemas for framework F version V
```

These facts can prune future discovery routes.

Negative knowledge should remain scoped just like positive knowledge.

---

## 33. A Worked Bootstrap Example: Unknown `ros2`

Suppose the target is:

```text
ros2 launch robot_bringup hardware.launch.py
```

and the core has no ROS-specific semantic rules.

### Step 1 — Resolve the first semantic object

Target interpretation produces:

```text
ExecutableToken("ros2")
```

A generic discovery method establishes:

```text
ExecutableResolvable("ros2")
```

and records:

```text
resolved path
file identity
environment scope
```

### Step 2 — Search for high-level semantic boundaries

Applicable discovery routes include:

```text
package metadata inspection
structured CLI introspection
implementation ownership lookup
source resolution
behavioral probing
```

Suppose package metadata and CLI introspection are available.

### Step 3 — Discover command structure

The system obtains candidate structure:

```text
Command(ros2)
HasSubcommand(ros2, launch)
...
```

The exact discovered set depends on the installed environment.

No hard-coded list is required.

### Step 4 — Follow the relevant branch only

The target uses:

```text
launch
```

so semantic discovery continues into that branch.

It asks:

```text
what arguments does launch accept?
how are package names resolved?
how are launch artifacts identified?
which registry or plugin supplies this command?
```

### Step 5 — Discover deeper semantic entry points

Inspection may reveal:

```text
package metadata
plugin registry
Python callable
generated interfaces
runtime graph introspection
```

Each becomes a possible semantic object.

### Step 6 — Generate candidate domain rules

The discovered structures may support candidates such as:

```text
PackageDiscoverable(package, context)
AND LaunchArtifactDiscoverable(package, file, context)
→ LaunchTargetInterpretable(package, file, context)
```

The candidate is scoped to the discovered implementation and environment.

### Step 7 — Validate

Validation may use:

```text
package query
interface query
dry interpretation
sandbox execution
runtime observation
```

Only then does the candidate become admissible for planning.

### Step 8 — Cache

The discovered semantic contract is persisted relative to:

```text
executable identity
package identity
plugin identities
environment digest
```

A later target can reuse it without rediscovering everything.

This is the intended bootstrapping loop.

---

## 34. A Worked Example: Dynamic Class Generation

Suppose a framework dynamically generates classes from a schema.

A naive semantic model may try to enumerate:

```text
GeneratedClassA
GeneratedClassB
GeneratedClassC
...
```

A bootstrapping system instead searches for the generating mechanism.

It may discover:

```text
SchemaArtifact(S)
Factory(F)
FactoryConsumes(F, S)
FactoryProducesClassFamily(F, C)
```

The system can then derive classes lazily when the target requires one.

If a new schema version appears:

```text
S1 → S2
```

the system does not require a manually updated ontology.

It invalidates generated semantic claims tied to `S1` and reruns the trusted factory-introspection method.

This is a major reason to model generative mechanisms rather than leaf instances.

---

## 35. A Worked Example: CLI Grammar Drift

Suppose version \(V_1\) of a tool exposes:

```text
tool deploy --region ...
```

and version \(V_2\) changes the grammar.

A manually authored rule may remain stale.

A discovered rule carries:

```text
ExecutableIdentity(tool, digest=D1)
DerivedGrammar(G1)
```

When the executable changes to digest \(D2\):

```text
G1 becomes stale
```

The planner reruns:

```text
InspectHelpSurface
InspectCompletionSurface
InspectParserMetadata
```

depending on what is available.

A new candidate grammar is extracted and validated.

Version churn therefore becomes routine rediscovery instead of centralized manual ontology maintenance.

---

## 36. Behavioral Semantics May Remain Irreducibly Empirical

Not every semantic property is available from schemas.

Examples:

```text
ServiceReady
TopicPublishingAtRequiredRate
DeviceActuallyUsable
PackageCombinationCompiles
PluginActuallyLoads
NetworkPathActuallyWorks
```

These require observation or experimentation.

A bootstrapping architecture should not attempt to infer all behavior statically.

Instead:

```text
declarative discovery
    exposes what should be possible

experimental discovery
    tests what is actually possible here
```

Both produce evidence-bearing claims.

---

## 37. A Semantic Contract Is Target-Relative

There is no need to discover the complete meaning of `ros2`, Python, Bash, or any other system.

For one target, the sufficient contract may be:

```text
this executable resolves
this subcommand exists
these argument positions have these roles
this package identifier is resolvable
this launch artifact exists
```

Another target may require:

```text
topic type identity
QoS compatibility
DDS network reachability
message serialization
```

The abstraction should reopen only when the target requires those hidden distinctions.

Thus even semantic contracts are relative primitives.

---

## 38. Discovery Cost Must Be Explicit

Semantic discovery has costs:

```text
latency
CPU
filesystem scanning
process creation
network access
source download
sandbox creation
mutation
security exposure
human attention
```

A planner should compare:

```text
cost of discovering semantics
```

with:

```text
cost of acting without them
```

For example:

```text
cheap CLI introspection
```

may be preferable to:

```text
expensive source checkout and static analysis
```

if both can answer the same target-relevant question.

Likewise a small sandbox probe may be cheaper than attempting a large real deployment under uncertainty.

---

## 39. Information Gain Applies to Semantic Discovery Too

Suppose three possible semantic routes exist:

```text
A: command implemented through package metadata
B: command supplied through dynamic plugin registry
C: command is a native opaque executable
```

A cheap identity query may eliminate two routes.

Thus the next semantic discovery action should consider:

```text
expected information gain
number of discovery branches eliminated
cost
mutation
risk
reversibility
```

Semantic bootstrapping is therefore an active diagnosis problem as much as a parsing problem.

---

## 40. Security and Policy Are Fundamental

A semantic bootstrapper can become powerful quickly.

It may be able to:

```text
read configuration
inspect credentials
execute binaries
open network connections
load plugins
import untrusted modules
create containers
trace processes
inspect source
```

Therefore discovery policy must be explicit.

The system should distinguish:

```text
read-only metadata inspection

safe local introspection

controlled execution

isolated experimental execution

networked execution

host mutation

privileged inspection
```

A discovery method being technically available does not mean it is policy-admissible.

Policy pruning should remain distinct from semantic impossibility.

---

## 41. Importing Code Is Not Always Observation-Only

In dynamic languages, reflection may execute code.

For example:

```text
import module
```

may trigger:

```text
filesystem writes
network calls
registration
environment mutation
process creation
```

Therefore:

```text
ImportModule
```

should not automatically be classified as a pure knowledge effect.

A safer hierarchy may be:

```text
static metadata inspection

static syntax/AST inspection

sandboxed import

live import

live invocation
```

Each carries different side effects and trust requirements.

This is a concrete example of why semantic extraction methods need effect contracts.

---

## 42. Machine-Readable Does Not Mean Semantically Sufficient

A parser may reveal:

```text
--force is a Boolean option
```

without revealing:

```text
what force changes
what safety checks it bypasses
what state it mutates
```

Likewise a function signature may reveal:

```text
f(path: str) -> Result
```

without revealing:

```text
filesystem effects
network effects
required permissions
semantic invariants
```

Therefore introspection produces partial semantics.

The system must preserve those boundaries.

A candidate contract may be:

```text
KNOWN:
    syntax
    types

UNKNOWN:
    behavioral effects
    safety implications
```

This is preferable to pretending the schema is complete.

---

## 43. Tests Are Executable Semantic Documentation

Tests often encode knowledge absent from prose documentation.

A test may reveal:

```text
given X
when operation Y executes
then Z must hold
```

That has an obvious rule-like shape.

However tests still need interpretation:

```text
what scope does this test cover?
is it current?
is it integration or unit level?
what mocks alter its meaning?
what behavior is incidental?
```

A test extractor should therefore produce candidate rules with provenance, not unquestioned truth.

Still, tests can be particularly useful because they combine:

```text
behavioral intent
executable validation
environment setup
expected outcomes
```

They are potential semantic compression points.

---

## 44. Documentation Becomes One Candidate Source Among Many

Human documentation remains useful.

But it should not be the sole authority when:

```text
installed code differs
versions drift
plugins alter behavior
generated interfaces change
runtime environment changes
```

A system may combine:

```text
documentation claim
installed metadata
runtime introspection
experiment
```

and detect disagreement.

For example:

```text
documentation says option exists
installed command grammar does not expose it
```

This should become an explicit conflict requiring resolution.

The architecture should not silently privilege whichever source was loaded first.

---

## 45. Conflict Resolution Is Evidence Comparison

Suppose:

```text
documentation implies P

runtime probe implies not-P
```

The system should record:

```text
Claim(P, source=documentation, scope=S1)
Claim(not-P, source=runtime_probe, scope=S2)
```

and inspect whether:

```text
versions differ
contexts differ
configuration differs
one source is stale
one observation is insufficient
```

Semantic bootstrapping therefore benefits directly from evidence-bearing claims and contextual validity.

Without those, auto-extracted rule systems would become brittle.

---

## 46. The System Needs an Abstention Mechanism

Some semantics cannot be inferred safely.

The system should be able to say:

```text
I can establish the command grammar,
but not the operational meaning of --force.

I can identify the callable signature,
but not whether it mutates external state.

I can infer the plugin registry,
but not the semantic contract of plugin P.

I can observe one successful execution,
but cannot generalize it to all inputs.
```

Abstention is not failure.

It is an epistemic boundary.

A trustworthy bootstrapping system should make semantic gaps visible.

---

## 47. The Bootloader Should Know Where Rules Might Exist

The deepest primitive knowledge may not be domain rules at all.

It may be knowledge of **semantic reservoirs**.

Examples:

```text
PATH may contain executable entry points

package databases may contain ownership and dependency metadata

language runtimes may expose reflection

plugin systems may expose registries

build systems may expose target graphs

schemas may expose typed contracts

processes may expose runtime state

files may contain declarations

tests may expose behavioral contracts

source trees may expose implementation structure
```

These are rules about **where useful rules can come from**.

That is a plausible bootstrapping base.

---

## 48. Semantic Reservoirs Can Be Ranked

Not every reservoir should be searched immediately.

A reasonable default ranking may prefer:

```text
1. trusted structured declarations
2. local registered metadata
3. non-executing reflection
4. read-only introspection
5. isolated execution
6. source analysis
7. network retrieval
8. live mutation
9. human interpretation
```

The ranking depends on policy and domain.

The point is that semantic search can be planned rather than improvised.

---

## 49. A Compact Formalization

Let:

\[
\mathcal P
\]

be typed propositions.

Let:

\[
\mathcal R
\]

be admitted semantic rules.

Let:

\[
\mathcal C
\]

be admissible claims.

Let:

\[
\mathcal E
\]

be executable effects.

Now introduce:

\[
\mathcal O
\]

the currently known semantic objects.

Let:

\[
\mathcal M
\]

be discovery methods.

A discovery method:

\[
m \in \mathcal M
\]

maps applicable objects and context to candidate semantic knowledge:

\[
m:
(\mathcal O, K_D)
\rightarrow
(\Delta \mathcal O,
 \widetilde{\mathcal C},
 \widetilde{\mathcal R})
\]

where:

```text
ΔO
    newly discovered semantic objects

C~
    candidate claims

R~
    candidate semantic rules
```

Candidates are passed through validation:

\[
\operatorname{Validate}
(
\widetilde{\mathcal C},
\widetilde{\mathcal R},
E
)
\]

and only admissible results enter:

\[
\mathcal C
\quad\text{or}\quad
\mathcal R.
\]

Thus the semantic knowledge base is not assumed complete.

It is incrementally constructed from accessible evidence.

---

## 50. Target Elaboration and Semantic Bootstrapping Form One Loop

A combined engine may behave as:

```text
target
↓
interpret with current semantics
↓
elaborate proof forest
↓
encounter semantic gap
↓
create semantic discovery obligation
↓
search applicable discovery methods
↓
inspect / reflect / probe / experiment
↓
generate candidate claims and rules
↓
validate
↓
admit trusted semantic knowledge
↓
resume target elaboration
↓
select realization or observation effect
↓
execute
↓
validate world claims
↓
re-elaborate
```

This is the central architecture.

Semantic discovery is not an offline preprocessing phase.

It is part of goal-directed reasoning.

---

## 51. Two Kinds of Cached Lemmas

The system can accumulate:

### World lemmas

```text
DockerBackendReady(host)
ROS2EnvironmentRealized(context)
PackageResolvable(package, context)
```

### Semantic lemmas

```text
SemanticContract(executable, identity)
CommandGrammar(executable, identity)
InterfaceSchema(package, digest)
TrustedExtractor(method, artifact_class)
```

Both should be reopenable.

A new target may require a stronger world distinction.

A new environment may require a stronger semantic distinction.

---

## 52. The Highest-Leverage Cached Object May Be a Trusted Extractor

Suppose a human verifies 200 individual rules.

That is useful.

Suppose instead a human verifies one extraction method that correctly generates those 200 rules whenever a schema is present.

That is much more useful.

This suggests an optimization objective:

\[
\text{maximize reusable semantic leverage per human validation}
\]

Human effort should preferentially validate:

```text
generators
extractors
schemas
registries
factory interpretations
validation methods
invalidation rules
```

rather than individual leaf facts.

---

## 53. Rule Discovery Can Become Self-Improving

Over time, the system may learn:

```text
artifact pattern A
→ extractor M is usually applicable

framework pattern F
→ registry R is a strong semantic entry point

candidate rule class C
→ validation probe V is sufficient

source construct S
→ generated object family G

failure pattern X
→ extractor Y is unreliable
```

This can improve:

```text
discovery route ranking
expected information gain
human escalation frequency
validation cost
semantic coverage
```

Again, this does not require the core reasoning kernel itself to become opaque.

The accumulated knowledge can remain evidence-bearing and inspectable.

---

## 54. The Main Research Question Changes

The key prototype question is no longer only:

> Can backward AND/OR elaboration expose later blockers before earlier blockers are physically removed?

A second, deeper question becomes:

> Can a small set of generic semantic discovery methods bootstrap enough correct target-relevant rules from an unfamiliar installed environment to support useful elaboration?

And then:

> How much human verification is required before those methods can be reused safely across environments?

These questions test whether semantic bootstrapping actually solves the rule-authoring bottleneck.

---

## 55. A Strong First Prototype

A first prototype should deliberately avoid a large hand-written ROS ontology.

Begin with:

```text
generic environment discovery

generic executable discovery

generic package metadata discovery

generic Python reflection where applicable

generic CLI introspection

filesystem and manifest inspection

one isolated execution mechanism

claims with provenance and validity

candidate-rule lifecycle

human accept/reject workflow

persistent cache
```

Then give it a target involving a moderately unfamiliar installed toolchain.

The experiment should measure whether it can discover enough semantics to:

```text
identify meaningful entry points
derive typed candidate operations
find downstream semantic objects
generate useful rules
validate those rules
reuse them on a later target
```

The amount of domain-specific seed knowledge should be kept deliberately small.

---

## 56. A More Aggressive Prototype Hypothesis

An especially informative test would be:

```text
Given only:
    generic filesystem access
    executable resolution
    package metadata access
    one language reflection adapter
    CLI probing
    sandboxed execution

Can the system discover:
    what "ros2" is
    which target-relevant subcommand exists
    where that subcommand comes from
    which further semantic artifacts it exposes
    enough schema to generate useful planning rules?
```

The objective is not complete ROS understanding.

It is evidence that semantic structure can be bootstrapped rather than enumerated.

---

## 57. Evaluation Metrics

Useful metrics include:

```text
number of manually authored domain rules required

number of useful rules generated per discovery method

fraction of generated rules admitted after validation

false semantic rule rate

human validations per reusable extractor

semantic cache hit rate

rule invalidation correctness after version changes

number of targets solved after environment change without manual rule updates

average discovery depth before useful contract found

fraction of semantic gaps correctly classified

number of unnecessary source inspections avoided

number of unnecessary mutations avoided

semantic coverage gained per unit discovery cost

fraction of explanations carrying rule provenance
```

A particularly important metric is:

```text
semantic leverage per human intervention
```

If one human validation enables many future correct derivations, the architecture is scaling in the intended direction.

---

## 58. Failure Mode: Replacing Hand-Written Rules With Hand-Written Extractors

It is possible to recreate the same problem one level higher.

For example:

```text
write a bespoke extractor for every ROS release
write a bespoke extractor for every CLI
write a bespoke extractor for every Python framework
```

This is not sufficient.

Discovery methods should target reusable structural patterns:

```text
entry-point registries
parser trees
schemas
plugin factories
type reflection
manifest graphs
generated-code conventions
```

Domain-specific adapters remain useful, but they should exploit stable semantic compression points rather than restating leaf behavior.

---

## 59. Failure Mode: Trusting Introspection Too Much

Reflection exposes what a system says about itself.

It may be:

```text
incomplete
stale
dynamically altered
configuration-dependent
misleading
```

Therefore:

```text
introspection
≠
behavioral proof
```

The evidence requirement should depend on the target.

A command grammar may be sufficient for syntax interpretation.

A deployment safety decision may require runtime validation.

---

## 60. Failure Mode: Treating Source Analysis as Omniscience

Source analysis also has limits.

Dynamic behavior may depend on:

```text
plugins
generated code
runtime imports
external services
environment variables
native extensions
reflection
network state
configuration
```

Therefore:

```text
source-visible
≠
runtime-complete
```

Source should remain one evidence source inside an open-world architecture.

---

## 61. Failure Mode: Generating Rules Faster Than They Can Be Validated

A reflective system may produce enormous numbers of candidate relations.

This can recreate ontology explosion in generated form.

The system should therefore generate lazily:

```text
only target-relevant candidate rules

only candidate rules reachable from active semantic obligations

only at the level of detail needed to distinguish current routes
```

Rule generation must remain target-directed.

---

## 62. Failure Mode: Caching Without Precise Identity

A discovered rule such as:

```text
tool supports operation X
```

is unsafe if cached without:

```text
tool identity
version/digest
environment scope
plugin set
configuration dependencies
validation provenance
```

Persistent semantic knowledge must be invalidatable.

Otherwise bootstrapping merely automates the creation of stale documentation.

---

## 63. Failure Mode: Human Approval Becomes a Rubber Stamp

If the system presents thousands of candidate rules for manual confirmation, human validation loses value.

Human review should focus on:

```text
high-leverage extractor correctness

ambiguous semantic mappings

conflicting evidence

new semantic reservoir types

new validation methods

safety-critical behavior
```

The system should minimize repetitive approvals.

---

## 64. Failure Mode: Importing or Executing Untrusted Artifacts During Discovery

Discovery itself can be dangerous.

An unknown executable or importable module may be malicious or destructive.

Therefore a semantic bootstrapper needs:

```text
capability restrictions
sandboxing
resource limits
network controls
filesystem isolation
timeout policies
effect logging
approval boundaries
```

Semantic curiosity must not override execution safety.

---

## 65. Failure Mode: Confusing Syntactic Schema With Semantic Contract

A command parser can reveal:

```text
argument names
types
defaults
subcommands
```

but not necessarily:

```text
preconditions
postconditions
side effects
invariants
safety requirements
```

A robust architecture should explicitly represent:

```text
schema coverage
```

and avoid presenting partial semantics as a complete behavioral contract.

---

## 66. A Suggested Implementation Sequence

A disciplined implementation order is:

```text
1. Define evidence-bearing claims and validity.

2. Define candidate semantic rules separately from admitted rules.

3. Define the discovery context:
       readable
       executable
       importable
       observable
       mutable
       isolatable

4. Implement generic object discovery:
       paths
       executables
       files
       packages
       runtimes

5. Implement discovery-method contracts.

6. Implement recursive semantic-object expansion.

7. Implement one structured metadata extractor.

8. Implement one reflection extractor.

9. Implement one CLI/introspection extractor.

10. Implement candidate-rule provenance.

11. Implement human accept/reject validation.

12. Persist admitted semantic rules and discovery paths.

13. Implement invalidation from artifact/environment identity changes.

14. Integrate semantic discovery obligations into target elaboration.

15. Implement isolated behavioral probing.

16. Add source-level analysis only after higher-level discovery works.

17. Add extractor trust levels and automatic bounded admission.

18. Add discovery-route costing and information gain.

19. Add negative discovery knowledge.

20. Add AI-assisted hypothesis generation only behind explicit validation.

21. Add increasingly domain-specific reflective providers.

22. Measure semantic leverage per human intervention.
```

This sequence tests the semantic bootstrapping thesis before building a large provider ecosystem.

---

## 67. The Core Engine Can Still Remain Small

The combined core may expose operations such as:

```text
interpret
unify
expand
classify
discover
inspect
reflect
probe
experiment
validate
admit
invalidate
cache
explain
```

Domain knowledge remains outside the core.

Reflective providers contribute discovery methods.

Backends contribute controlled observation and execution.

Persistence stores claims, rules, candidates, provenance, and method trust.

Policy controls which semantic reservoirs may be opened.

---

## 68. Explanations Should Include How the System Learned the Rule

A normal proof-carrying explanation answers:

```text
Why is this action recommended?
```

A semantic bootstrapper should additionally answer:

```text
Where did this rule come from?
Why do we trust it?
What environment is it valid for?
Which extractor generated it?
What validation was performed?
What would invalidate it?
What remains unknown?
```

Example:

```text
RULE
    LaunchSubcommandAvailable(ros2)

DISCOVERED FROM
    installed CLI introspection

OBJECT IDENTITY
    executable digest D
    environment E

VALIDATED BY
    structured help probe
    package registry corroboration

STATUS
    ADMITTED

VALID UNTIL
    executable identity changes
    plugin registry changes

LIMITATION
    establishes command availability,
    not successful launch behavior
```

This makes auto-generated semantics auditable.

---

## 69. A Semantic Frontier Should Produce an Engineering Task

When bootstrapping stops, the system should report something actionable.

For example:

```text
SEMANTIC FRONTIER

Target requires:
    EffectContract(fooctl deploy)

Known:
    executable identity
    command grammar
    package owner

Unknown:
    mutation semantics
    rollback behavior

Tried:
    metadata
    structured help
    local reflection

Blocked:
    source unavailable
    execution disallowed by policy

Possible extensions:
    permit isolated probe
    provide source
    add vendor schema
    human specifies effect contract
```

The frontier becomes a concrete provider-development or human-investigation task.

---

## 70. The Long-Term Architecture Is a Semantic Bootloader

The system can be viewed as a semantic bootloader.

It begins with almost no domain understanding.

It knows only:

```text
how to locate things
how to classify accessible artifacts
how to ask artifacts what they expose
how to observe safely
how to test candidate semantics
how to preserve evidence
how to reuse validated discoveries
```

From there it incrementally constructs the semantic world needed by the target.

Conceptually:

```text
primitive affordances
↓
semantic reservoirs
↓
discovery methods
↓
semantic objects
↓
candidate claims and rules
↓
validation
↓
admitted semantic contracts
↓
goal-directed planning
↓
new observations
↓
more semantic knowledge
```

The architecture therefore bootstraps from operational access into semantic understanding.

---

## 71. Central Principles

### Rule-Discovery Principle

> Prefer reusable procedures that discover and validate target-relevant semantic rules from accessible artifacts, metadata, reflection surfaces, registries, schemas, and experiments over enumerating version-specific behavior.

### Semantic-Bootstrapping Principle

> The initial kernel need only know how to locate, inspect, query, and safely experiment on accessible objects; richer domain semantics should be acquired lazily.

### Target-Relative Discovery Principle

> Do not inspect the whole environment. Open only semantic structures that can influence the current target.

### Semantic-Compression Principle

> Prefer generators, registries, schemas, factories, and protocols that explain families of behavior over enumerating individual instances.

### Highest-Useful-Boundary Principle

> Use the highest-level semantic contract sufficient for the target and reopen implementation details only when necessary.

### Candidate-Before-Admission Principle

> Discovered semantic structure remains provisional until supported by adequate evidence.

### Rule-Provenance Principle

> A generated rule should record how it was discovered, validated, scoped, and invalidated.

### Version-As-Invalidation Principle

> Treat software and environment changes primarily as invalidation and rediscovery events rather than manual ontology-update events.

### Partial-Semantics Principle

> A provider may expose syntax, type structure, or identity without knowing behavioral effects; preserve the unknown remainder explicitly.

### Semantic-Reservoir Principle

> The bootloader should know where semantic structure may exist even when it does not yet know the domain-specific structure itself.

### Human-Leverage Principle

> Prefer human validation of reusable extraction and validation methods over repetitive confirmation of individual leaf rules.

### AI-Hypothesis Principle

> AI may propose semantic interpretations and discovery routes, but architectural truth requires evidence-bearing admission.

### Persistent-Extractor Principle

> Persist not only discovered rules but also trusted methods for discovering rules.

### Open-World Discovery Principle

> Failure to discover semantics means the represented discovery architecture has reached a boundary; it does not imply that no semantics exist.

### Safe-Discovery Principle

> Inspection, import, execution, and experimentation are effects with explicit policy, cost, and side-effect semantics.

### Semantic-Abstention Principle

> When available evidence supports only a partial contract, report the boundary rather than fabricating stronger semantics.

---

## 72. Compact Summary

A semantic bootstrapping goal-directed system can be summarized as:

```text
TARGET
↓
interpret with current semantic knowledge
↓
lazy AND/OR elaboration
↓
semantic gap encountered
↓
discover relevant accessible objects
↓
locate semantic reservoirs
↓
apply reflective discovery methods
↓
produce candidate claims and candidate rules
↓
validate against metadata / reflection / probes / experiments / humans
↓
admit scoped semantic knowledge
↓
cache provenance and invalidators
↓
resume target elaboration
↓
choose useful observation or realization effect
↓
validate world result
↓
re-elaborate
```

The system therefore maintains two coupled forms of knowledge:

```text
knowledge about the world

knowledge about how the available software means and behaves
```

Both are contextual.

Both require evidence.

Both may become stale.

Both can be discovered incrementally.

Both can be cached as reopenable lemmas.

---

## 73. Conclusion

The difficult scaling problem in goal-directed development reasoning is unlikely to be construction of the AND/OR elaborator itself.

The deeper problem is semantic acquisition.

A system cannot reason usefully about arbitrary tools if humans must manually encode the behavior of every version of every CLI, runtime, middleware layer, package, generated interface, and framework.

But complete manual encoding is unnecessary if the environment already contains latent semantic structure.

Software systems expose pieces of their meaning through:

```text
metadata
registries
schemas
types
reflection
generators
factories
build graphs
tests
runtime introspection
source
behavior
```

The missing layer is a disciplined architecture that can search these surfaces according to the current goal.

The strongest architecture therefore does not begin with:

```text
Here are all the rules for ROS 2.
```

It begins with:

```text
Here are the ways I know how to discover semantic entry points.

Here are the things I am currently allowed to inspect, query, execute, or test.

Given the target, which semantic structure do I need?

Where can that structure exist?

Which discovery method can expose it?

What candidate rules follow?

What evidence would justify admitting them?

What can I reuse next time?
```

This shifts the system from a hand-maintained ontology toward a semantic bootloader.

The bootloader begins with primitive access to an environment.

It discovers objects.

Objects reveal registries, schemas, interfaces, factories, and other semantic compression points.

Those structures generate candidate rules.

Candidate rules are validated.

Validated rules become reusable semantic lemmas.

Repeated discoveries establish trusted extraction methods.

Trusted methods reduce human work.

Human assistance moves progressively toward the remaining frontier: ambiguous behavior, novel semantic reservoirs, conflicting evidence, and high-impact validation.

The resulting system is not merely:

```text
a planner with a large knowledge base
```

and not merely:

```text
an AI agent that reads documentation and guesses commands
```

It is closer to:

\[
\boxed{
\text{goal-directed semantic search}
+
\text{reflective rule synthesis}
+
\text{evidence-driven admission}
+
\text{persistent reusable discovery}
}
\]

The long-term goal is therefore not to teach the system every tool.

It is to teach the system how to find out what the current tools expose, how strongly that evidence supports a semantic contract, how to test what remains uncertain, and how to remember the verified result without pretending it will remain true forever.

That is the foundation of a self-extending, evidence-bearing semantic rule system.
