# Recursive Requirement–Provision Networks: Self-Similar Capability Transformation Across Engineering, Governance, and Evaluation

## Abstract

A capability provision network is usually introduced from the viewpoint of one consumer:

```text
consumer
requires capability
provider supplies capability
```

This is useful but incomplete.

The provider is normally also a consumer of upstream capabilities. The requirement being consumed is often itself the output of another process. The interface through which provision occurs is maintained by further actors. The evidence used to justify a binding depends on additional observational capabilities. The criteria used to evaluate the requirement may themselves have been selected, justified, and maintained by another provision network.

The same structure therefore reappears at multiple scales:

```text
requirements are produced
capabilities are provided
provision depends on requirements
requirements depend on capabilities
```

A requirements engineer provides requirement specifications while consuming stakeholder access, domain knowledge, organizational authority, analytical methods, time, and evidence. A stakeholder provides desired outcomes while consuming interpretation, forecasts, institutional memory, and communication. A system provides an operational capability while consuming implementations, infrastructure, permissions, maintenance, and monitoring. An evaluator provides a judgment while consuming criteria, observations, comparison classes, and reasoning capability.

No layer is automatically outside the network.

This document develops a recursive interpretation of requirement–provision systems. Its central claim is:

> A requirement is not only an input to realization. It may also be the provided output of another capability transformation.

A second claim follows:

> Provider and consumer are viewpoint-relative roles in a recursively nested graph of requirement production, capability transformation, provision, evaluation, maintenance, and revision.

The network is self-similar, though not necessarily a mathematical fractal in the strict geometric sense. When one node is decomposed, the same pattern often appears again:

```text
incoming requirements
+
local resources and organization
+
transformation
->
outgoing provisions
```

This reframes requirements engineering, architecture, operation, monitoring, governance, evaluation, and maintenance as different cuts through one underlying relational structure.

---

## 1. Starting Point

Consider a system specification:

```text
Application A requires network connectivity.
Provider B supplies network connectivity.
```

This appears to contain two roles:

```text
consumer: Application A
provider: Provider B
```

But Provider B may require:

```text
power
radio spectrum
backhaul
routing
identity services
software
operators
maintenance
funding
```

Application A may itself provide:

```text
report generation
control decisions
communication
record processing
```

to another consumer.

The original pair is therefore only one local view of a larger network.

The same node may be:

```text
a consumer relative to one capability
a provider relative to another capability
a mediator relative to a third capability
a maintainer relative to a fourth relation
an evidence source relative to a fifth decision
```

Roles are not permanent labels attached to entities.

They are indexed by relation, capability, context, and viewpoint.

---

## 2. Requirements Are Not Primitive Inputs

A requirement is often treated as the starting point of engineering:

```text
requirement
->
design
->
implementation
->
operation
```

But requirements do not normally appear without support.

A requirement may depend on:

```text
stakeholder goals
observed problems
regulation
risk models
budget constraints
organizational strategy
technical possibilities
historical commitments
negotiation
interpretation
```

Thus a requirement can itself be an engineered artifact.

For example:

```text
stakeholder concerns
+
domain evidence
+
legal constraints
+
requirements analysis
->
typed requirement specification
```

The requirement specification is provided to architects, developers, operators, auditors, or procurement systems.

Therefore:

> A requirement may be the output of one provision network and the input to another.

---

## 3. Requirement Production as Capability Provision

A requirements engineer may provide:

```text
requirement elicitation
conflict identification
constraint normalization
traceability
acceptance criteria
priority ordering
```

to a project or decision process.

The requirements engineer consumes:

```text
stakeholder access
domain knowledge
organizational authority
modeling tools
communication channels
time
budget
records
evidence
```

The relation can be written:

\[
T_{req}:
(G,E,C,A,M)
\rightharpoonup
R,
\]

where:

```text
G = goals or concerns
E = evidence
C = constraints
A = authority and interpretation
M = elicitation and modeling methods
R = produced requirement set
```

Requirements engineering is therefore not outside capability provision.

It is one capability transformation inside it.

---

## 4. Desired Outcomes Are Also Provided

A stakeholder is often treated as the source of requirements.

But a stakeholder may not initially possess a clear, stable, or internally consistent requirement.

The stakeholder may require:

```text
problem framing
forecasting
comparison of alternatives
translation of consequences
legal interpretation
technical explanation
facilitation
organizational memory
```

A business analyst, advisor, researcher, regulator, or community process may provide the capability through which a desire becomes expressible as a decision-relevant objective.

For example:

```text
unclear concern
+
facilitated inquiry
+
operational evidence
->
articulated desired outcome
```

Thus even the apparent source of a requirement may be consuming upstream provision.

---

## 5. No Privileged Meta-Level

A common model divides the world into levels:

```text
object level:
  system operation

meta level:
  requirements, evaluation, governance
```

The distinction may be useful for analysis.

It does not imply that the meta level is ontologically outside the network.

Requirements engineering requires capabilities.

Evaluation requires capabilities.

Governance requires capabilities.

Monitoring requires capabilities.

Modeling requires capabilities.

The framework used to inspect provision relations is itself produced, communicated, interpreted, and maintained through provision relations.

Therefore:

> A meta-level process is often an ordinary provision network viewed from the level below it.

---

## 6. Viewpoint-Relative Roles

Let:

```text
v = a node
kappa = a capability
u = a consumer
p = a provider
```

The statements:

\[
\operatorname{Provides}(v,u,\kappa)
\]

and:

\[
\operatorname{Requires}(v,\kappa')
\]

may both hold.

A node does not have one globally fixed role.

A requirements engineer may be:

```text
provider of normalized requirements
consumer of stakeholder access
consumer of domain evidence
provider of traceability
consumer of organizational authority
```

A regulator may be:

```text
provider of constraints
consumer of scientific evidence
provider of authorization
consumer of political legitimacy
```

A model may be:

```text
provider of generated text
consumer of prompts
consumer of computation
provider of intermediate representations
consumer of evaluation criteria during training
```

Role identity is relational.

---

## 7. The Recursive Node

A node can be modeled as a transformation from required inputs to provided outputs.

Let node \(v\) consume capabilities:

\[
\kappa_1,\ldots,\kappa_n
\]

and provide:

\[
\lambda_1,\ldots,\lambda_m.
\]

Then:

\[
T_v:
(\kappa_1,\ldots,\kappa_n,c_v)
\rightharpoonup
(\lambda_1,\ldots,\lambda_m),
\]

where \(c_v\) contains local state, configuration, organization, and commitments.

The outputs may immediately become requirements for other nodes.

The node therefore acts as a boundary across which requirements are transformed into provisions.

---

## 8. From Provision Networks to Requirement–Provision Networks

A provision-only graph emphasizes supplied capabilities.

A recursive model should represent both sides:

```text
required capability
provided capability
requirement-producing process
provider-producing process
binding process
maintenance process
```

Let:

\[
N=(V,E_R,E_P,E_T),
\]

where:

```text
V   = actors, artifacts, systems, interfaces, processes, and institutions
E_R = requirement relations
E_P = provision relations
E_T = transformation relations
```

A requirement edge identifies what a node needs.

A provision edge identifies what another node exposes.

A transformation edge records how one set of required inputs is converted into provided outputs.

---

## 9. Requirements as Artifacts and Relations

The word `requirement` can refer to several different things:

```text
a dependency relation
a written specification
a negotiated commitment
a desired outcome
a constraint
a quality threshold
a testable acceptance condition
```

These should be distinguished.

Let:

```text
R_rel = the relation that a consumer needs a capability
R_art = an artifact representing that relation
R_commit = an accepted obligation to satisfy it
R_test = an operational criterion used to judge satisfaction
```

A requirements engineer may provide \(R_{art}\).

A governance process may authorize \(R_{commit}\).

A test designer may provide \(R_{test}\).

The consumer remains related to \(R_{rel}\).

Collapsing all four into one object hides important failure modes.

---

## 10. Requirement Interpretation

A written requirement does not automatically determine one operational meaning.

For example:

```text
The service shall be reliable.
```

may be interpreted as:

```text
99.9% monthly availability
no more than 5 minutes interruption
successful recovery after one server failure
correct responses for 95% of target cases
```

Interpretation is itself a provided capability.

A standards body, domain expert, contract, test protocol, or institutional practice may provide the mapping:

\[
I:
R_{art}
\rightharpoonup
R_{operational}.
\]

The interpretation may be contested, versioned, incomplete, or context-dependent.

Therefore a requirement artifact is not identical to the operational requirement it is taken to express.

---

## 11. Evaluation Criteria as Requirements

A criterion such as:

```text
a good framework minimizes ambiguity
```

may appear normative.

But it can also be normalized as a requirement-relative criterion.

Suppose an evaluator must provide:

```text
reliable framework discrimination
```

under conditions including:

```text
limited time
uncertain future use
multiple domains
incomplete evidence
```

The evaluator may require criteria that improve this capability:

```text
conceptual differentiation
internal coherence
operational usefulness
compression
generativity
failure visibility
```

The criterion is then justified by the role it plays in providing an evaluation capability.

The structure becomes:

```text
evaluation objective
->
evaluator capability requirement
->
selected criteria
->
judgment
```

This does not prove that all norms reduce to instrumental requirements.

It shows that many apparently primitive evaluation rules can be analyzed as requirement-relative provisions.

---

## 12. Criteria Are Also Produced and Maintained

Evaluation criteria have histories.

They may be produced through:

```text
successful practice
failure analysis
scientific investigation
formal proof
institutional negotiation
professional training
legal precedent
standardization
```

A criterion may persist because institutions provide:

```text
education
certification
documentation
review procedures
shared vocabulary
enforcement
revision mechanisms
```

Thus criteria are not merely stored propositions.

Their usability depends on maintained interpretation and application capabilities.

---

## 13. Historical Origin Is Not Operational Provision

It is important not to confuse:

```text
where a capability historically came from
```

with:

```text
what currently provides that capability to a consumer
```

An engineering tradition may influence the training of an evaluator.

But the current provider of evaluation may be:

```text
a human reviewer
a trained model
a review board
a software analyzer
```

The historical tradition is part of the formation path.

The current evaluator is part of the operational provision path.

The distinction is:

\[
\operatorname{ProducedByHistory}(x,h)
\neq
\operatorname{CurrentlyProvidedBy}(u,p,x).
\]

Both relations may matter, but they answer different questions.

---

## 14. Formation Networks and Operation Networks

A capability may have at least two relevant dependency structures.

### Formation network

The processes that produced the current capability:

```text
training
construction
education
development
institutional formation
capital investment
```

### Operation network

The processes that currently expose and maintain the capability:

```text
runtime infrastructure
staffing
interfaces
access control
monitoring
repair
funding
```

A physician's current judgment capability depends historically on education and presently on records, tools, authorization, time, and health.

A model endpoint depends historically on training and presently on serving infrastructure.

A requirement specification depends historically on elicitation and presently on storage, interpretation, authority, and traceability.

The formation network explains how a capability came to exist.

The operation network explains how it remains available now.

---

## 15. Self-Similarity

The structure often repeats when one node is decomposed.

At one scale:

```text
application
requires connectivity
network provider supplies connectivity
```

Zoom into the network provider:

```text
network provider
requires power, routing, operators, and spectrum
upstream providers supply them
```

Zoom into the operator role:

```text
operator
requires training, authority, information, and tools
institutions and systems supply them
```

Zoom into training:

```text
training system
requires instructors, curricula, facilities, evidence, and funding
other providers supply them
```

The pattern recurs.

This is self-similarity, not necessarily strict fractality.

A mathematical fractal normally requires more precise scale invariance or recursive construction.

Requirement–provision systems exhibit structural recurrence without exact geometric repetition.

---

## 16. Why “Fractal” Is Useful but Limited

The fractal metaphor is useful because it emphasizes:

```text
recursion
nested dependency
repeated role structure
scale-relative boundaries
no final privileged layer
```

It becomes misleading if interpreted to mean:

```text
all scales are identical
all nodes have the same internal form
decomposition continues indefinitely in practice
quantitative scaling laws necessarily exist
```

The stronger statement is:

> Many nodes reveal another requirement–provision network when decomposed, and the same relational vocabulary remains applicable across levels.

---

## 17. Boundaries Are Analytical Cuts

A system boundary selects which dependencies are represented explicitly and which are delegated.

For one analysis:

```text
cloud service = provider
```

For another:

```text
cloud service = network of compute, storage, identity, operators, contracts, and power
```

Neither description is automatically false.

They answer questions at different resolutions.

A boundary is therefore an analytical cut through a recursive network.

The cut should be chosen according to:

```text
decision relevance
risk
uncertainty
cost
centrality
failure impact
ability to intervene
```

---

## 18. Encapsulation as Controlled Non-Decomposition

An interface allows downstream consumers to avoid continuously expanding the provider's internal network.

Encapsulation means:

```text
accept the provider contract
without representing all internal requirements
unless discrepancies make decomposition necessary
```

The recursive model does not imply that every dependency must always be expanded.

It explains why expansion is possible and when it may become necessary.

A stable interface is a maintained boundary that suppresses repeated reconstruction cost.

---

## 19. Requirement Providers

If a requirement can be an output, then some nodes may be called requirement providers.

Examples include:

```text
stakeholders providing desired outcomes
regulators providing constraints
architects providing derived technical requirements
risk analysts providing mitigation requirements
test designers providing acceptance requirements
maintainers providing maintainability requirements
operators providing operability requirements
```

But `requirement provider` should not imply unilateral authority.

A requirement may be:

```text
proposed
negotiated
derived
inherited
mandated
observed
inferred
```

The authority to introduce a requirement is itself a provision relation.

---

## 20. Requirement Authority

A requirement may exist as text without being admissible for a project.

Its force may depend on:

```text
contractual authority
organizational role
legal jurisdiction
technical derivation
safety case
budget approval
stakeholder consent
```

Let:

\[
\operatorname{AdmissibleRequirement}(R,u,c)
\]

hold only when the requirement is properly scoped, interpreted, and authorized for consumer \(u\) in context \(c\).

This parallels operational provider existence.

A named requirement is not automatically a binding requirement.

---

## 21. Requirements Can Conflict

Multiple requirement providers may produce incompatible demands.

For example:

```text
security requires strict access control
usability requires low interaction cost
finance requires low operating expense
operations requires rapid recovery
privacy requires limited retention
analytics requires extensive retention
```

Conflict resolution is itself a capability provision.

A governance process may provide:

```text
priority selection
trade-off justification
exception handling
scope resolution
commitment allocation
```

The resolver consumes:

```text
requirements
authority
evidence
risk tolerances
organizational objectives
```

and produces an admissible requirement set.

---

## 22. Requirements Can Be Unsatisfied, Unsupported, or Misproduced

A failed system is not always caused by a missing capability provider.

The requirement itself may fail through:

### Requirement absence

```text
A decision-relevant need was never represented.
```

### Requirement ambiguity

```text
The artifact does not determine an operational interpretation.
```

### Requirement mismatch

```text
The specified requirement does not correspond to the actual need.
```

### Requirement authority failure

```text
The requirement was introduced without valid authority.
```

### Requirement conflict

```text
The selected set cannot be jointly satisfied.
```

### Requirement staleness

```text
The environment changed while the requirement remained fixed.
```

### Requirement evidence failure

```text
The need is asserted without adequate supporting observation.
```

The recursive framework therefore exposes failure surfaces on both the requirement side and the provision side.

---

## 23. Requirement Maintenance

Requirements may need maintenance over time.

A maintained requirement process may include:

```text
revalidation
stakeholder review
change detection
traceability updates
version control
conflict reassessment
retirement
replacement
```

A requirement that was justified at time \(t_0\) may become harmful at time \(t_1\).

Let:

\[
R_t
\]

be the admissible requirement set at time \(t\).

Maintained engineering may require:

\[
\forall t\in H:
\operatorname{Current}(R_t,c_t)
\land
\operatorname{Authorized}(R_t)
\land
\operatorname{Traceable}(R_t).
\]

Continuity may therefore involve requirement substitution as well as provider substitution.

---

## 24. Provision Can Change the Requirement

Provision is not always a one-way response to a fixed demand.

A new capability may alter what consumers can reasonably require.

Examples include:

```text
cheap storage changes retention expectations
fast communication changes coordination requirements
new medical diagnostics change treatment standards
new model capabilities change workflow design
new regulation changes acceptable service envelopes
```

Thus:

```text
requirements shape provision
provision reshapes requirements
```

The network may contain feedback.

A static acyclic pipeline is therefore often insufficient.

---

## 25. Recursive Feedback

Let:

```text
R_t = requirements at time t
P_t = available provisions at time t
C_t = context at time t
```

Then requirements may evolve according to:

\[
R_{t+1}=F(R_t,P_t,C_t),
\]

while provision evolves according to:

\[
P_{t+1}=G(P_t,R_{t+1},C_t).
\]

The system is co-evolutionary.

Requirements are not merely external commands.

Providers are not merely passive responders.

Each side influences the future structure of the other.

---

## 26. Evaluation Is a Provision Network

An evaluator provides a judgment to a consumer such as:

```text
a decision-maker
a design team
a regulator
a reader
a procurement process
```

The evaluator requires:

```text
the object being evaluated
criteria
comparison classes
evidence
reasoning capability
time
interpretive context
```

The judgment may be represented as:

\[
J=
T_{eval}(X,K,E,C),
\]

where:

```text
X = evaluated object
K = evaluation criteria
E = evidence
C = context and purpose
```

The claim:

```text
framework F is strong
```

is therefore shorthand for a provisioned evaluation under a declared or implicit envelope.

---

## 27. Evaluation Envelopes

A framework may be strong for one purpose and weak for another.

Possible evaluation envelopes include:

```text
conceptual clarification
formal proof
empirical prediction
operational review
software implementation
organizational coordination
teaching
policy design
```

The criteria should be indexed by the target capability.

For conceptual clarification, useful criteria may include:

```text
differentiation
coherence
compression
generativity
scope
```

For predictive science, they may include:

```text
measurement
falsifiability
quantitative accuracy
out-of-sample prediction
```

For operational engineering, they may include:

```text
actionability
traceability
failure detection
cost of use
reliability improvement
```

There is no single unqualified strength relation.

---

## 28. Reflexive Application

The framework can be applied to itself.

To use a requirement–provision framework, a consumer may require:

```text
concept comprehension
model construction
boundary selection
evidence access
notation
review time
institutional acceptance
```

The document provides some of these through:

```text
definitions
examples
formal relations
procedures
reports
failure modes
```

Its use still depends on interpreters, tools, organizations, and decisions.

The framework is therefore not an external spectator.

It is another provision artifact embedded in the networks it describes.

---

## 29. Reflexivity Does Not Imply Circular Invalidity

A framework describing frameworks does not become invalid merely because it applies to itself.

The relevant question is whether the recursive relations are well-founded enough for the current task.

A monitoring system may monitor itself partially.

A compiler may compile its own source.

A requirements process may specify requirements for requirements tooling.

An evaluator may evaluate its own criteria.

Reflexivity becomes problematic when it produces:

```text
unresolvable circular dependence
unsupported self-certification
infinite regress without a stopping rule
hidden conflicts of interest
```

The presence of recursion is not itself a defect.

---

## 30. Practical Stopping Rules

Because every node may reveal further dependencies, decomposition requires a stopping rule.

Stop expanding when additional detail is unlikely to change:

```text
provider selection
requirement interpretation
risk estimate
repair plan
commitment decision
cost estimate
acceptance judgment
```

Expand when a hidden dependency is:

```text
high impact
poorly evidenced
highly central
weakly substitutable
contested
stale
irreversible
likely to change the decision
```

The stopping point is decision-relative rather than metaphysically final.

---

## 31. A Recursive Resolution Procedure

A recursive analysis may proceed as follows:

```text
1. Select a focal consumer and desired outcome.
2. Normalize the outcome into capability requirements.
3. Identify who or what produced those requirements.
4. Check interpretation, evidence, authority, and currency.
5. Identify candidate provision paths.
6. Decompose decision-relevant provider dependencies.
7. Identify the requirements consumed by mediators, maintainers, and evidence sources.
8. Check compatibility, capacity, quality, authority, cost, and timing.
9. Identify feedback by which current provision may alter future requirements.
10. Select a stopping boundary.
11. Record unresolved assumptions on both the requirement and provision sides.
12. Maintain the requirement set, provider bindings, and evidence over the relevant horizon.
```

The procedure does not assume that requirements are correct merely because they are written.

Nor does it assume that providers are adequate merely because they exist.

---

## 32. Recursive Provision Report

A recursive report may include:

```yaml
focus:
  consumer: application_A
  desired_outcome: reliable_external_communication

requirement_relation:
  capability: network.connectivity
  horizon: 8h
  quality:
    availability_min: 0.995
    latency_max: 150ms

requirement_origin:
  proposed_by: operations_team
  derived_from:
    - customer_support_commitment
    - incident_response_need
  interpretation_provider: systems_architecture_group
  authority: service_owner
  evidence:
    - incident_history
    - contractual_response_window
  reviewed_at: 2026-07-27

selected_binding:
  provider: mobile_operator_B
  access_point: modem_1
  interface: ip_connectivity

provider_requirements:
  - electrical_power
  - radio_coverage
  - subscription_authorization
  - backhaul

maintenance:
  requirement_review_interval: 90d
  provider_recheck_interval: 5m
  fallback: office_fiber

feedback:
  condition:
    new_low_latency_control_workload
  effect:
    revise_latency_requirement
```

This report treats the requirement and its provider as equally inspectable.

---

## 33. A Minimal Formal Model

### Requirement relation

\[
R=(u,\kappa,\Theta,Q,H,A,E_R),
\]

where:

```text
u   = consumer
kappa = required capability
Theta = applicability conditions
Q   = required service envelope
H   = horizon
A   = authority and commitment state
E_R = evidence supporting the requirement
```

### Provider offer

\[
O=(p,\kappa,i,\Omega,Q_O,C,E_O),
\]

where:

```text
p   = provider
i   = interface or access point
Omega = provider applicability region
Q_O = offered service envelope
C   = cost and commitment terms
E_O = provider evidence
```

### Binding

\[
B=(R,O,\pi),
\]

where \(\pi\) is the mediated provision path.

### Transformation node

\[
T_v:
(R_1,\ldots,R_n,c_v)
\rightharpoonup
(O_1,\ldots,O_m).
\]

### Recursive network

\[
N=(V,E_R,E_P,E_T,E_E,E_M),
\]

where:

```text
E_R = requirement relations
E_P = provision relations
E_T = transformation relations
E_E = evidence relations
E_M = maintenance relations
```

---

## 34. Recursive Realizability

A requirement is currently realizable when there exists an admissible binding:

\[
\operatorname{Realizable}(R,N,c)
\iff
\exists O,\pi:
\operatorname{Admissible}(R,O,\pi,N,c).
\]

But recursive realizability additionally asks whether decision-relevant requirements inside the selected binding are themselves supported:

\[
\operatorname{RecursivelyRealizable}(R,N,c,d)
\]

where \(d\) is the selected decomposition depth or stopping policy.

This does not imply complete expansion to physical primitives.

It means that every dependency exposed by the current decision boundary has at least one admissible provision path.

---

## 35. Maintained Recursive Realizability

Maintained provision requires more than a provider existing at each instant.

It may require continuity of:

```text
requirements
interpretations
provider bindings
interfaces
evidence
authority
repair capability
substitution capability
```

A maintained recursive condition may be written:

\[
\forall t\in H:
\exists R_t,O_t,\pi_t
\]

such that:

\[
\operatorname{Current}(R_t)
\land
\operatorname{Authorized}(R_t)
\land
\operatorname{Admissible}(R_t,O_t,\pi_t)
\land
\operatorname{RecoverableWithin}(\Delta_{max}).
\]

The requirement itself may change while the desired outcome remains continuous.

The provider may change while the required capability remains continuous.

The interface may change if mediation preserves compatibility.

Continuity is relational rather than material.

---

## 36. Recursive Failure Modes

### Requirement-production failure

```text
No adequate process produces the requirement.
```

### Interpretation failure

```text
The requirement artifact cannot be mapped to an operational condition.
```

### Authority failure

```text
The requirement or provider binding lacks legitimate commitment.
```

### Provision failure

```text
No admissible provider path exists.
```

### Evidence failure

```text
The requirement or provider claim is unsupported or stale.
```

### Transformation failure

```text
A node cannot convert its incoming provisions into promised outputs.
```

### Feedback failure

```text
The system does not revise requirements after context or capability changes.
```

### Boundary failure

```text
The analysis stops before a decision-relevant dependency is exposed.
```

### Recursive maintenance failure

```text
The network maintains the service but not the requirement, interpretation, authority, or recovery relation that makes the service useful.
```

---

## 37. Central Principles

### Requirement-Output Principle

> A requirement may be the provided output of another capability transformation.

### Viewpoint-Relative Role Principle

> Provider, consumer, mediator, maintainer, evaluator, and requirement source are relational roles rather than permanent entity classes.

### Recursive-Node Principle

> A node may be modeled as a transformation from incoming required capabilities to outgoing provided capabilities.

### No-Privileged-Meta-Level Principle

> Requirements engineering, evaluation, governance, monitoring, and modeling are provision networks rather than external observers of provision networks.

### Requirement-Authority Principle

> A named requirement becomes binding only through an admissible interpretation and authority relation.

### Requirement-Evidence Principle

> Requirements require evidence and freshness checks just as provider claims do.

### Formation–Operation Distinction

> The historical processes that form a capability are distinct from the current processes that expose and maintain it.

### Self-Similarity Principle

> Decomposing a node often reveals another requirement–provision network governed by the same relational vocabulary.

### Boundary-as-Cut Principle

> A system boundary is an analytical cut selected according to decision relevance, not an absolute end of dependency.

### Co-Evolution Principle

> Requirements shape provision, and available provision reshapes future requirements.

### Reflexive-Application Principle

> A requirement–provision framework is itself a provision artifact embedded in the networks it describes.

---

## 38. Central Statements

> Requirements do not merely precede provision; they are often produced by provision.

> A stakeholder can provide a desired outcome while consuming interpretation and analysis.

> A requirements engineer can provide a specification while consuming evidence, authority, and stakeholder access.

> A provider can be a consumer when viewed through its upstream dependencies.

> A consumer can be a provider when viewed through its downstream outputs.

> A requirement artifact is not identical to the dependency relation, commitment, interpretation, or acceptance test it represents.

> Evaluation criteria can often be understood as capabilities required to provide a decision-relative judgment.

> Historical intellectual traditions may help form an evaluator without being the current operational provider of evaluation.

> The same relational structure reappears across engineering, operation, governance, evaluation, training, maintenance, and institutional continuity.

> The network is self-similar without needing to be a strict mathematical fractal.

> There is no automatically privileged meta-layer outside the requirement–provision network.

> The final decomposition boundary is chosen for a decision, not discovered as an absolute foundation.

---

## 39. Conclusion

A simple capability provision model begins with a consumer that requires something and a provider that supplies it.

A recursive model asks where the requirement came from, what capabilities were needed to produce it, who interprets it, who authorizes it, what evidence supports it, and how it changes over time.

It also asks what the provider requires, who maintains its interface, who supplies evidence about it, and what preserves substitution when it fails.

The resulting structure is not a linear chain:

```text
requirement
->
provider
->
realization
```

It is a recursively nested and feedback-sensitive network:

```text
desired outcomes
->
requirement production
->
requirement interpretation and authority
->
provider resolution
->
capability transformation
->
operational provision
->
observation and evaluation
->
requirement revision
```

Every stage consumes capabilities and provides others.

Requirements engineering is inside this network.

Evaluation is inside this network.

Governance is inside this network.

Maintenance is inside this network.

The same node may change role depending on which relation is selected.

The same system may appear simple at one scale and reveal another complete requirement–provision network at the next.

The enduring object is therefore not only a maintained provision relation.

It is a maintained recursive organization in which:

```text
requirements remain justified
providers remain admissible
transformations remain effective
interfaces remain usable
evidence remains fresh
authority remains valid
feedback remains possible
and decomposition remains sufficient for the decisions being made
```

The central evaluation question becomes:

> For each requirement and each provision in the selected view, who or what produces it, what does that producer require, how is the relation interpreted and authorized, what evidence supports it, how is it maintained, and where should the current analysis stop?
