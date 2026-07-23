# Realization as Exercised Capability

## Abstract

To say that a sentence, action, computation, route, institution, or interaction is realized is not merely to say that it exists after the fact.

A realized occurrence is a particular transition instantiated by an organization that was sufficiently capable, configured, supported, and coupled to produce it.

The capacity to speak is potential.

A spoken sentence is one exercise of that capacity.

The capacity to compute is potential.

A completed computation is one realized execution.

The capacity to navigate is potential.

A traversed route is one realized trajectory.

This yields the central claim:

> Every realization is the actual instantiation of a transition that some effective organization was capable of supporting under the realized conditions.

The relevant capability need not belong to an isolated individual. It may be distributed across:

```text
body
learned skill
language
instrument
software
infrastructure
institution
other agents
environment
```

A written sentence may therefore be realized by a coupled system containing a writer, linguistic competence, a keyboard, an editor, a computer, electrical infrastructure, storage, and a reader.

The realization witnesses the effective organization of that system.

This framework also explains why human environments are not organized around arbitrary physical distinctions. Displays are constructed for human vision. Speakers are constructed for human hearing. Buildings are constructed for human bodies. Languages must be producible, perceivable, learnable, and reusable by human organisms. Supermarkets organize the acquisition of human food. Entertainment is dominated by human and anthropomorphic agents because it is realized within human perceptual, emotional, and social capability systems.

Human organization recursively begins from human capability, extends it through tools and institutions, and then uses the extended capability as the basis for further organization.

The resulting pattern is:

```text
existing capability
        ->
compatible organization
        ->
realized interaction
        ->
extended capability
        ->
new compatible organization
```

The document develops realization and capability as complementary notions:

```text
capability
=
maintained potential for a class of realizations
```

```text
realization
=
a particular instantiated transition
```

---

## 1. Starting Point

Consider the sentence:

```text
This sentence is realized.
```

The sentence is not waiting outside reality for realization to be assigned to it.

If it is written, displayed, spoken, stored, transmitted, or interpreted, then an organized transition has already occurred.

But the occurrence did not arise from nowhere.

Its realization required some organization capable of producing and carrying it.

For a spoken sentence, this may include:

```text
linguistic competence
memory
attention
breathing
vocal control
articulation
hearing
social context
```

For a written sentence, it may include:

```text
symbol knowledge
motor control
writing surface or keyboard
text system
storage
rendering
visual interpretation
```

The realized sentence therefore points in two directions.

It points forward as an actual occurrence.

It points backward toward the capability and organization whose exercise instantiated it.

---

## 2. Capability and Realization Are Complementary

Capability and realization should not be collapsed.

A capability is modal.

It concerns what an organized system can realize under a declared region of conditions.

A realization is actual.

It concerns what transition was instantiated in a particular occurrence.

Thus:

```text
capability
=
potential for a class of transitions
```

```text
realization
=
one actual transition token
```

The capability to say a sentence does not imply that the sentence has been said.

The sentence being said implies that a sufficient realizing organization existed during the occurrence.

This gives the asymmetric relation:


a capability may exist without being exercised

but

a realized exercise cannot occur without sufficient realizing organization.

---

## 3. The Exercise Principle

### Exercise Principle

> A realization is an actual exercise of transition-supporting organization.

Let:

```text
A = an agent or organized system
c = its current configuration
u = an operator, skill, policy, or transition schema
a = invocation parameters
η = an execution trace
```

A realized exercise may be represented as:

\[
(A,c)
\xRightarrow{u(a)}
\eta
\]

where the trace \(\eta\) actually occurs and instantiates the relevant transition.

The capability is not the trace.

The trace is not the capability.

The capability supports a class of possible traces.

The realized trace is one member actually produced under particular conditions.

---

## 4. Effective Capability

An isolated action label does not establish capability.

For example:

```text
SPEAK(sentence)
```

may be specified symbolically while remaining unexecutable because:

```text
the agent does not know the language
the vocal system is unavailable
the sentence exceeds working memory
the communication channel is absent
the required concepts are unresolved
the agent is not authorized to speak in the setting
```

Effective capability is therefore configuration-indexed.

Let:

\[
\operatorname{Cap}(A,c,H,\Theta)
\]

be the set of target conditions that agent or system \(A\) can reliably realize from configuration \(c\), within horizon \(H\), under conditions \(\Theta\).

The conditions may include:

```text
body state
knowledge
resources
tools
authority
time
environment
coupling
infrastructure
reliability threshold
```

Capability is not a free-floating property of an abstract agent.

It is a relation among organized potential, configuration, environment, and target class.

---

## 5. Realization Tokens

A realization token is a particular occurrence.

Examples include:

```text
one sentence spoken at time t
one file written to storage
one payment executed
one route traversed
one object grasped
one theorem proof checked
one image displayed
```

Let:

\[
\operatorname{Realized}(\eta,\phi,\Gamma)
\]

mean that execution trace \(\eta\) occurred and instantiated pattern, role, or target \(\phi\) under interpretive context \(\Gamma\).

The context matters.

The same sound may instantiate:

```text
a word
a warning
a quotation
a command
a joke
an accidental noise
```

The physical trace alone does not determine every higher-level role.

Realization therefore combines:

```text
actual occurrence
+
organized carrier
+
contextual role
```

---

## 6. Realization Presupposes Generative Sufficiency

If an event occurred, then the realized conditions were sufficient for that occurrence.

Formally:

\[
\operatorname{Realized}(\eta,\phi,\Gamma)
\Rightarrow
\exists S,c,p:
\operatorname{Executed}(S,p,c,\eta)
\land
\operatorname{Instantiates}(\eta,\phi,\Gamma)
\]

where \(S\) is the realizing system and \(p\) is an admissible process, policy, composition, or physical evolution.

This is not a claim that the system represented the full process in advance.

It is not a claim that the event was intended.

It is not a claim that the system can reproduce the event reliably.

It is the narrower claim:

> The occurrence could not have been realized without an actual organization sufficient to carry its realized transition.

---

## 7. One Occurrence Does Not Always Establish Stable Capability

A distinction is required between:

```text
generative sufficiency
```

and

```text
stable operational capability
```

A random physical fluctuation might produce a meaningful-looking pattern once.

That does not imply a maintained skill capable of reproducing the pattern across relevant conditions.

Likewise:

```text
one accidental success
!=
reliable capability
```

A stable capability normally requires:

```text
repeatability
control
admissible variation
recognized conditions
sufficient reliability
maintained support
```

Therefore a realized token always witnesses sufficient realized organization for that token.

It does not always witness a stable reusable capability over a broad class.

Human sentence production normally does more than witness one accidental trace. It participates in a maintained linguistic capability that can generate many related sentence tokens.

---

## 8. Capability Type, Schema, Invocation, and Token

Four levels should be distinguished.

### Capability type

```text
can produce intelligible English discourse
```

This identifies a class of realizable outcomes.

### Realization schema

```text
select words
compose syntax
control articulation
produce an acoustic signal
```

This identifies a reusable organization for generating instances.

### Invocation

```text
say: "This sentence is realized."
```

This binds a particular content to the schema.

### Realization token

```text
agent A uttered that sentence at time t
```

This is the actual occurrence.

Thus:

```text
capability type
        ->
schema
        ->
invocation
        ->
execution
        ->
realization token
```

The layers are related but not identical.

---

## 9. Discourse as Exercised Capability

A discourse occurrence is not only a realized representation.

It is also an exercise of a discourse-producing and discourse-carrying capability system.

Let:

\[
D_A
\]

be the discourse capability of configured agent or system \(A\).

For a sentence \(s\), an utterance or inscription may be represented as:

\[
\operatorname{Produce}_A(s,c)
\Downarrow
\eta_s
\]

where \(\eta_s\) is the realized token that instantiates \(s\).

The statement:

```text
This sentence is realized.
```

therefore says more than:

```text
this token now exists
```

It also reveals:

```text
some system could select or generate the symbols
some carrier could preserve their distinctions
some process could order them
some context could interpret them as a sentence
```

The realized sentence is a witness of exercised organization.

---

## 10. The Realized Frame Is Capability-Bounded

Whenever discourse occurs, it is realized.

But not every imaginable discourse can be realized by every agent in every configuration.

A finite agent is bounded by:

```text
perception
memory
attention
language
motor control
available symbols
available media
social access
computation
time
```

The realized frame is therefore not an arbitrary container into which any content can be inserted.

It is bounded by the effective capability frontier of the realizing system.

Let:

\[
\mathcal D_{\mathrm{exec}}(A,c)
\]

be the set of discourse operations executable by \(A\) in configuration \(c\).

Then a discourse token produced now must arise through some operation in that frontier:

\[
\operatorname{RealizedDiscourse}(d,A,c)
\Rightarrow
\exists u\in\mathcal D_{\mathrm{exec}}(A,c):
\operatorname{Exec}(u,c)\models d
\]

This is the capability boundary of realized discourse.

---

## 11. Discourse Closure Is Executed Closure

Questioning, denying, analyzing, formalizing, and criticizing a realized discourse can produce further realized discourse.

This gives a closure-like property:

```text
realized discourse
        ->
executed discourse operation
        ->
new realized discourse
```

But the closure must be stated carefully.

It is not closure under every imaginable operation.

An agent may lack the capability to perform some transformations.

The correct principle is:

> The realized discourse system is closed under the discourse operations that are actually executable and executed within it.

Formally, if \(d\) is realized and \(q\) is an executable discourse operation, then executing \(q(d)\) produces another realized token:

\[
d\in D_R
\land
q\in\mathcal Q_{\mathrm{exec}}
\land
\operatorname{Executed}(q,d)
\Rightarrow
q(d)\in D_R
\]

The closure is therefore capability-indexed.

---

## 12. Self-Reference Is a Special Realization

Realization applies to discourse regardless of topic.

Self-reference appears when a realized discourse token represents or modifies a discourse process that includes itself or its own class.

For example:

```text
This sentence is realized.
```

The sentence is:

```text
realized as a token
+
about realization
+
capable of directing attention to its own occurrence
```

This makes it a mirror-like exercise of discourse capability.

The sentence does not create realization by describing it.

Its description exposes a condition already satisfied by its occurrence.

---

## 13. Realization and the Referent Remain Distinct

The realization of a sentence does not establish the existence of its referent.

For example:

```text
Unicorns live beyond the visible horizon.
```

may be realized as discourse even if no unicorn exists.

The capability exercised is the capability to instantiate the representation.

It is not necessarily the capability to instantiate the represented object.

Thus:

```text
capability to represent x
!=
capability to produce x
```

and:

```text
realized discourse about x
!=
realized x
```

This distinction prevents the capability account from collapsing discourse ontology into referent ontology.

---

## 14. Representation Extends Capability Without Producing the Referent

A representation may extend what an agent can:

```text
consider
compare
predict
coordinate
remember
request
search for
construct toward
```

without directly realizing the represented target.

A map does not realize the destination.

It extends navigation capability.

A blueprint does not realize the building.

It extends coordination and construction capability.

A sentence about an impossible machine does not realize the machine.

It realizes a representation that may support evaluation, rejection, modification, or invention.

Representational capability therefore enlarges the space of organized search even when the represented target remains unrealized.

---

## 15. Individual Capability Is Often Insufficient

A sentence displayed on a screen is rarely the product of one isolated human capability.

Its realization may require a distributed system:

```text
writer
language community
keyboard
software
operating system
processor
memory
electrical grid
network
screen
reader
```

The relevant unit is therefore often not:

```text
human alone
```

but:

```text
human
+
tools
+
learned organization
+
infrastructure
+
other agents
```

Let:

\[
S=A\oplus T\oplus I\oplus E
\]

where:

```text
A = agent organization
T = tools
I = infrastructure and institutions
E = environment
```

The realized capability may belong to the coupled system \(S\), even when no component can realize the outcome independently.

---

## 16. Capability Is Relational

A capability is not located entirely inside an agent.

A human may have the bodily skill to walk but lack a walkable surface.

A person may know a language but lack a listener or medium.

A computer may contain a program but lack power.

A credential may authorize an operation while the service is unavailable.

Thus:

\[
\operatorname{Capability}(A,g,c)
\]

should be understood as depending on relations among:

```text
agent organization
environmental affordances
available couplings
supporting resources
interfaces
other agents
```

The same agent can gain or lose capability without changing its internal organization if the surrounding support changes.

---

## 17. The Agent-Compatibility Principle

Human-built organizations are not distributed uniformly across all physically describable possibilities.

They are concentrated around transitions humans can perceive, invoke, interpret, maintain, and value.

### Agent-Compatibility Principle

> A maintained organization intended for repeated use by an agent class must expose interactions compatible with the perceptual, motor, cognitive, communicative, and social capabilities of that class.

This does not require perfect optimization.

It requires sufficient compatibility for the interaction to be repeatedly realized.

An interface that cannot enter the user's perceptual range cannot reliably inform the user.

An operator that cannot be invoked through the user's action range cannot function as a usable operator for that user.

---

## 18. Displays Are Organized Around Visual Capability

A monitor is not an arbitrary emitter of physical variation.

Its useful output is organized so that human visual systems can discriminate and integrate it.

Its design must coordinate such features as:

```text
spatial scale
contrast
brightness
color differentiation
temporal stability
motion presentation
viewing distance
symbol size
```

A display could emit distinctions outside unaided human visual sensitivity.

Those distinctions might be physically present while remaining unavailable to ordinary human perception.

A useful human display therefore maps machine state into a human-realizable perceptual transition:

```text
encoded machine organization
        ->
visible pattern
        ->
human visual discrimination
        ->
interpreted representation
```

The display realizes an interface between different capability systems.

---

## 19. Speakers Are Organized Around Auditory Capability

A speaker intended for humans is not useful merely because it produces pressure variation.

Its output must couple to human auditory capability in a discriminable and interpretable way.

The organization is shaped by:

```text
human hearing
speech perception
music perception
loudness tolerance
temporal resolution
spatial hearing
```

Signals outside ordinary human hearing may be physically realized without becoming ordinary human auditory experience.

The relevant capability is not:

```text
produce arbitrary vibration
```

but:

```text
produce vibration that enters a human auditory interaction system
```

---

## 20. Buildings Are Organized Around Embodied Capability

Buildings encode assumptions about their users.

They are structured around recurring human relations such as:

```text
standing
walking
reaching
sitting
carrying
seeing
hearing
entering
exiting
resting
coordinating
```

Doorways, corridors, stairs, controls, rooms, furniture, lighting, and signs are not dimensioned for arbitrary points in space.

They are organized around bodies with characteristic ranges and movement patterns.

A structure designed only for mice would expose a different operator system.

The same physical site would present different executable frontiers to:

```text
a human
a mouse
a bird
a wheelchair user
a delivery robot
```

Architecture is therefore a material projection of assumed capability relations.

---

## 21. Language Must Be Realizable by Its Users

Language contains conventional and historically contingent structure.

But it is not arbitrary with respect to every constraint.

A repeatedly used spoken language must be supportable by:

```text
human articulation
human hearing
human memory
human timing
human learning
human turn-taking
human social coordination
```

A language requiring distinctions that no participant can produce, perceive, retain, or reproduce would fail as a practical interaction system for those participants.

Pronounceability is therefore not a superficial feature.

It is one manifestation of a deeper requirement:

> Linguistic organization must remain within the executable and perceivable capability region of its users, or provide tools that translate it into that region.

Writing extends this region by allowing distinctions to persist outside immediate speech and memory.

---

## 22. Supermarkets Organize Human Acquisition

A supermarket does not sell an arbitrary sample of all physically possible matter.

It organizes goods around recurring human acquisition and consumption capabilities.

Its maintained structure coordinates:

```text
human nutrition
human taste
household storage
carrying capacity
payment systems
product recognition
shelf access
transport
regulation
cultural practice
```

The supermarket is therefore not merely a collection of objects.

It is a capability system for repeatedly realizing transitions such as:

```text
locate food
select food
exchange payment
transport food
store food
prepare food
consume food
```

Food for hypothetical organisms with incompatible chemistry would not normally participate in this system because it would not connect to the recurrent capability and demand structure of human users.

---

## 23. Entertainment Is Organized Around Human Social Capability

Entertainment could consist entirely of arbitrary changing points.

Sometimes it does.

But much entertainment is organized around:

```text
human faces
human voices
human movement
human conflict
human cooperation
human emotion
human intention
anthropomorphic agents
```

This is not accidental.

Human perceptual and social systems are highly responsive to agents, expressions, goals, relationships, and narratives.

Anthropomorphic characters map unfamiliar forms into familiar capability structures.

They allow viewers to exercise:

```text
social prediction
emotional interpretation
identity tracking
causal attribution
norm evaluation
```

Entertainment organization therefore reflects the capabilities through which humans can sustain attention, interpretation, and concern.

---

## 24. Why Some Interaction Systems Are Rare

Humans do not maintain equally rich interaction systems for every physical domain.

Ordinary environments contain fewer direct interfaces for:

```text
ultrasound perception
infrared perception
extreme pressure
extreme temperature
Earth-core access
unaided flight
microscopic manipulation
```

Several constraints may explain the difference:

```text
missing biological capability
weak direct coupling
high energy cost
high material cost
high danger
low recurrent demand
poor controllability
insufficient infrastructure
```

The absence of a common platform does not prove the underlying phenomenon is unreal.

It shows that the phenomenon is not included in the ordinary executable frontier of the current human capability system.

---

## 25. Physical Possibility Is Not Agent Capability

The world may permit a transition in principle while a particular agent cannot realize it.

Thus:

```text
physically possible
!=
currently realizable by this agent
```

and:

```text
currently unrealizable
!=
physically impossible
```

A human cannot directly see infrared.

A suitable sensor can transform infrared variation into visible or otherwise interpretable output.

The tool constructs a bridge:

```text
previously inaccessible physical distinction
        ->
sensor transduction
        ->
human-compatible representation
        ->
new realized perceptual capability
```

Capability expansion often consists precisely in building such bridges.

---

## 26. Tools Transform Capability Frontiers

A tool is not merely an object held by an agent.

It reorganizes which transitions the coupled system can realize.

Examples include:

```text
glasses
->
extended visual discrimination
```

```text
microphone
->
extended sound capture
```

```text
ultrasound scanner
->
translated access to otherwise unavailable structure
```

```text
writing
->
extended memory and communication
```

```text
vehicle
->
extended locomotion
```

```text
computer
->
extended symbolic transformation
```

```text
Google Maps
->
extended navigation and route resolution
```

A tool therefore participates in a capability transformation:

\[
\operatorname{Cap}(A\oplus T,c,H)
\supseteq
\operatorname{Cap}(A,c,H)
\]

for some relevant target classes.

The inclusion need not hold universally because tools also impose costs, dependencies, and new failure modes.

---

## 27. Recursive Capability Construction

Human organization is recursively capability-shaped.

Initial biological and learned capabilities support the construction of tools.

The tools extend capability.

The extended capability supports new tools and institutions.

Let:

\[
C_0
\]

be an initial capability system.

Let organization \(O_1\) be constructible and usable through \(C_0\).

The coupled system yields:

\[
C_1
=
\operatorname{Closure}_{\mathrm{feasible}}(C_0,O_1)
\]

A later organization \(O_2\) may then be constructible only through \(C_1\):

\[
C_2
=
\operatorname{Closure}_{\mathrm{feasible}}(C_1,O_2)
\]

Thus:

```text
C0
-> O1
-> C1
-> O2
-> C2
-> ...
```

Examples include:

```text
speech
->
shared instruction
->
coordinated construction
->
writing
->
persistent records
->
institutions
->
large-scale infrastructure
->
computation
->
networked coordination
```

Each layer becomes part of the capability base for the next.

---

## 28. Infrastructure Becomes an Inherited Capability Layer

An individual born into an organized society does not personally reconstruct every supporting capability.

The individual inherits access to maintained layers such as:

```text
language
roads
power grids
schools
markets
legal systems
communication networks
medical systems
software platforms
maps
```

These layers expose high-level operators whose internal realization is distributed across many people and mechanisms.

For example:

```text
buy food
```

compresses:

```text
agriculture
manufacturing
transport
storage
regulation
pricing
payment
retail coordination
```

The individual's practical capability therefore depends on organized history that is not represented in each invocation.

---

## 29. Organizations Also Shape Agents

The recursion is not one-directional.

Humans construct organizations around human capability.

Those organizations then train, constrain, and transform human capability.

For example:

```text
language shapes discriminations
writing changes memory practice
schools stabilize learned operators
cities change locomotion patterns
markets shape acquisition behavior
software changes attention and coordination
institutions define authority capabilities
```

The coupled recursion is:

```text
agent capability
        ->
constructed organization
        ->
repeated participation
        ->
modified agent capability
        ->
new organization
```

Human environments are therefore neither arbitrary external containers nor simple projections of fixed human nature.

They are historically accumulated capability relations.

---

## 30. Locality Bounds Every Realization

Every actual exercise occurs through local, finite, physically admissible transitions.

An agent cannot execute an entire long-horizon trajectory in one step.

A sentence is articulated through successive transitions.

A building is constructed through successive transitions.

A route is traversed through successive transitions.

A social institution persists through successive acts of maintenance.

Thus:

> Capability may concern an extended target class, but realization occurs through locally executable transitions.

This yields:

```text
extended capability
        ->
resolution into local operators
        ->
local execution
        ->
observation
        ->
updated capability state
```

Locality is not an optional design preference.

It is a condition of physical realization.

---

## 31. Local Execution Is Necessary but Not Sufficient for Extended Outcomes

Every realized trajectory is composed of locally executable transitions.

But the availability of local transitions does not guarantee a desired extended outcome.

An agent may repeatedly execute actions while:

```text
entering a dead end
consuming indispensable resources
destroying future options
cycling without progress
following a misleading local gradient
creating irreversible commitments
```

The missing requirement is not nonlocal execution.

Execution remains local.

The missing requirement is organization capable of selecting and composing local transitions across a longer horizon.

Thus:

```text
local executability
!=
long-horizon reachability
```

---

## 32. Steering as Capability-Conditioned Selection

Steering need not imply a global controller outside the agent.

It can be defined more modestly.

### Steering

> Steering is the repeated selection, execution, and revision of locally executable transitions relative to represented constraints, target conditions, and future capability effects.

The process may be:

```text
current configuration
        ->
executable frontier
        ->
selection
        ->
local realization
        ->
observation
        ->
updated configuration
        ->
reselection
```

A map, policy, value function, norm, plan, habit, institution, or learned model may influence selection.

None must contain the complete future trace.

Their role is to alter which local transition is exercised now.

---

## 33. Capability Preservation

An action changes more than the immediate state.

It can change the future capability set.

Let:

\[
\mathcal C_t
=
\operatorname{Cap}(A,c_t,H,\Theta)
\]

After transition \(u_t\):

\[
c_t
\xrightarrow{u_t}
c_{t+1}
\]

we obtain:

\[
\mathcal C_{t+1}
=
\operatorname{Cap}(A,c_{t+1},H,\Theta)
\]

The action may:

```text
enlarge capability
preserve capability
specialize capability
consume capability
transfer capability
irreversibly destroy capability
```

Capability preservation therefore means maintaining the organization required to keep relevant future transitions realizable.

This is not necessarily the agent's supreme objective.

It is a structural consideration in any extended trajectory.

---

## 34. Which Trajectories Matter?

Capability alone does not determine selection.

An agent may be capable of many mutually incompatible trajectories.

Selection depends on maintained evaluative organization such as:

```text
biological regulation
learned reward
pain avoidance
attachment
identity
social norm
religious commitment
institutional role
explicit goal
legal obligation
habit
forecast
```

These structures determine which states, transitions, identities, relationships, or institutions the agent treats as important.

They may be:

```text
evolved
learned
imitated
negotiated
imposed
reflected upon
revised
```

The realization framework does not supply one universal objective.

It explains how any objective that participates in action must itself be realized through an organization capable of affecting selection.

---

## 35. Objectives Are Realized Selection Constraints

An objective that changes no representation, policy, attention, or action has no operational role in the realized process.

For an objective \(g\) to guide agent \(A\), some realized organization must connect \(g\) to transition selection.

Formally:

\[
\operatorname{Guides}(g,A,c)
\Rightarrow
\exists \rho_g:
\operatorname{Realizes}(\rho_g,g,A,c)
\land
\operatorname{ModifiesSelection}(\rho_g,A,c)
\]

The realizing organization may include:

```text
memory
emotion
policy
symbolic commitment
social enforcement
ritual
institutional record
external reminder
```

An objective is therefore not operationally active merely because it can be stated.

It must participate in the selection machinery of the agent or organization.

---

## 36. Sacrifice Can Be Coherent Under a Different Capability Objective

An observer may assume that an agent's primary objective is individual survival.

But an agent may organize action around the preservation of:

```text
family
religion
community
nation
reputation
truth
future generations
institution
principle
```

An individual may therefore accept the destruction of personal future capability to preserve a capability or identity attributed to a larger organization.

This does not establish that the action is factually informed, morally justified, or strategically effective.

It shows only that evaluation depends on the realized objective hierarchy.

The relevant system boundary may be:

```text
individual organism
```

or:

```text
individual
+
community
+
tradition
+
future continuation
```

Different boundaries produce different interpretations of preservation and loss.

---

## 37. Relationships as Anticipated Capability Reorganization

Searching for a relationship often involves an anticipated transformation of future life.

The expected effects may include:

```text
companionship
care
belonging
shared resources
family formation
sexual intimacy
social recognition
emotional regulation
expanded coordination
```

A person may therefore evaluate a relationship partly by its expected effect on:

```text
quality of life
future options
stability
identity
safety
meaning
```

The search is not simply for another object.

It is a search for a coupled organization expected to alter the future capability and valuation structure of both participants.

The expectation can be mistaken.

But the action can still be intelligible relative to the agent's represented trajectory.

---

## 38. Irrationality Often Compresses Away Context

The label `irrational` is frequently applied after replacing the actor's realized context with a simplified observer model.

At least five distinctions should remain separate.

### Internal inconsistency

The action conflicts with the agent's maintained objectives or commitments.

### False or incomplete belief

The action follows coherently from a representation that does not match the relevant world conditions.

### Capability misestimation

The agent incorrectly estimates what transitions are executable or reachable.

### Different valuation

The observer and actor assign different importance to outcomes.

### Different system boundary

The actor evaluates preservation at the level of a family, religion, institution, or future collective rather than the individual alone.

Calling all five cases irrational removes the very organization needed to explain the realized transition.

---

## 39. Realized History and Remaining Uncertainty

After an event occurs, uncertainty about whether that exact event will occur is no longer future uncertainty.

The occurrence is realized.

But many uncertainties can remain:

```text
what exactly occurred
which description is accurate
which causal factors mattered
which alternatives were executable
what the agent knew beforehand
which objective guided selection
whether the result was intended
whether the process is reproducible
```

Therefore:

```text
realized occurrence
!=
complete knowledge of the occurrence
```

A realized token fixes the event's occurrence.

It does not automatically fix its explanation, interpretation, counterfactual structure, or value.

---

## 40. Hindsight Discusses a Realized Token From a New Configuration

Commentary after an event is itself a new realized discourse event.

Let:

\[
\eta_0
\]

be the original realized event.

Let:

\[
\eta_1
\]

be later commentary about \(\eta_0\).

Then:

```text
η0
=
realized event
```

```text
η1
=
new realized discourse about the event
```

The commentator now possesses information produced by \(\eta_0\).

The actor before \(\eta_0\) did not necessarily possess that information.

Therefore retrospective evaluation occurs from a different configuration:

\[
c_{\mathrm{after}}
\neq
c_{\mathrm{before}}
\]

Treating the after-configuration as if it had been available before the event erases uncertainty and capability limits that were part of the original realization.

---

## 41. Realization May Be Shared While Access Is Unequal

A single event may participate in the histories of multiple observers.

But their access can differ because of:

```text
position
sensing
attention
memory
language
records
trust
institutional role
```

It is therefore too strong to say without qualification that realization is simply shared.

A more precise statement is:

> Multiple agents may refer to the same realized event token while possessing different realized representations of it.

The event does not become a different event merely because valuations differ.

But the descriptions, causal models, and evaluations may remain non-identical.

---

## 42. Valuation Is Also Capability-Bounded

An agent cannot evaluate every possible consequence with unlimited precision.

Valuation depends on capabilities such as:

```text
perception
memory
simulation
comparison
language
social learning
emotional response
counterfactual reasoning
```

A consequence outside the agent's representational capability may fail to affect choice.

A distant future may be weakly represented.

An unfamiliar organism may not trigger ordinary empathy.

An invisible risk may require instrumentation and education before it enters valuation.

Therefore objectives and evaluations are not arbitrary symbols attached from outside.

They are realized through finite evaluative capability systems.

---

## 43. Social Networks and Economies Are Distributed Capability Systems

Social networks, economies, cities, countries, and other institutions can be analyzed as distributed organizations that expose recurring transition possibilities.

They support capabilities such as:

```text
identify another agent
communicate
exchange
coordinate
travel
store claims
resolve disputes
distribute resources
preserve records
assign authority
```

Their interfaces remain shaped by the capabilities of participating humans and machines.

At the same time, no individual participant contains the entire capability.

A modern economy can realize transitions that no isolated person could organize alone.

Thus:

```text
individual capability
+
coordination organization
+
maintained interfaces
->
distributed social capability
```

---

## 44. Districts, Cities, Countries, and Continents as Scope Organizations

Spatial and political divisions are not merely labels on geometry.

They organize different scopes of interaction, authority, identity, infrastructure, and coordination.

A district may support local services.

A city may coordinate transport, utilities, housing, and dense interaction.

A country may organize law, taxation, citizenship, defense, and large-scale redistribution.

A continent may support broader geographical, ecological, historical, and logistical distinctions.

These scopes help finite agents and institutions resolve large systems into manageable interfaces.

Their boundaries are historically contingent, but their organizational role responds to finite capability:

```text
limited attention
limited travel
limited communication
limited administrative resolution
limited authority
```

Hierarchical scope is one way distributed capability remains locally executable.

---

## 45. Hierarchy Does Not Eliminate Locality

A global map, institution, plan, or mission-control layer does not execute from outside physics.

It is itself realized through local processes.

Its role is to organize information and selection across scopes.

For example:

```text
global target
        ->
regional route
        ->
local instruction
        ->
motor transition
```

Every layer is realized.

Every interface must connect to the capability of the next layer.

Hierarchy therefore does not oppose locality.

It is one organization for translating extended constraints into locally executable transitions.

---

## 46. Gradients Are Capability-Relative Signals

A gradient indicates a locally improving direction relative to:

```text
a represented objective
a parameterization
a neighborhood relation
a measurement process
```

It is not a universal command.

An agent may become trapped when:

```text
the objective is misspecified
the representation omits distant structure
the neighborhood excludes necessary transitions
the path requires temporary loss
the landscape contains local optima
the action destroys future capability
```

The issue is not that gradients are unreal.

A computed gradient is a realized informational structure.

The issue is that its guidance is bounded by the capability, representation, and scope that generated it.

Long-horizon organization may require maintaining alternatives that a narrow local signal would discard.

---

## 47. Capability Preservation Is Not Universal Maximization

The framework should not be reduced to:

```text
always maximize capability
```

An agent may rationally consume capability to realize another objective.

Examples include:

```text
spending money for care
using energy to finish a task
accepting injury to rescue another person
specializing rather than preserving every option
committing to a relationship
retiring an obsolete system
```

Capability preservation becomes relevant when future realization depends on retained organization.

It is a constraint and evaluative dimension, not automatically the only value.

The important question is:

> Which capabilities must remain available for the maintained objectives and identities of the relevant agent or organization?

---

## 48. The Realization-Capability Duality

Capability and realization provide two views of the same organized transition system.

### Forward view

Given a configured capability system, which realizations can it produce?

\[
(A,c,\mathfrak O)
\Rightarrow
\mathcal R_{\mathrm{possible}}
\]

### Retrospective view

Given a realized token, what organization and conditions were sufficient to instantiate it?

\[
\eta
\Rightarrow
\text{realizing organization and exercised transition structure}
\]

The forward view supports planning and design.

The retrospective view supports explanation, diagnosis, and capability inference.

Neither view is complete by itself.

---

## 49. Realization as a Capability Witness

A realized token can function as evidence.

If a person produced a grammatical sentence, the occurrence is evidence of some relevant linguistic organization.

If a system completed a payment, the occurrence is evidence that some payment realization path was executable.

If a structure remained standing, the occurrence is evidence that its realized material and support organization sustained the encountered conditions.

But inference must remain bounded.

From one token we cannot automatically infer:

```text
broad competence
future reliability
full understanding
intention
legal authority
safe repeatability
correct valuation
```

Thus:

> Realization witnesses sufficient organization for the realized token, while stronger capability claims require evidence across a declared region of conditions.

---

## 50. Capability Failure Explains Unrealized Possibility

A represented target may remain unrealized for different reasons.

```text
physically impossible target
missing operator
missing skill
missing resource
missing authority
missing interface
missing knowledge
missing coordination
missing demand
excessive risk
insufficient maintenance
```

These should not be collapsed into one category.

The question:

```text
Why is this not realized?
```

can be refined into:

```text
Which required capability relation is absent?
Which transition is not executable?
Which support does not persist?
Which representation does not resolve?
Which organization has not been constructed?
```

This turns absence into a capability diagnosis.

---

## 51. Design as Capability-to-Realization Engineering

Design can be understood as constructing an organization that maps intended user capability into reliable realization.

A successful interface coordinates:

```text
what the user can perceive
what the user can invoke
what the system can execute
what result the user can observe
what errors the user can recover from
```

A design failure often occurs when one of these relations breaks.

Examples include:

```text
output outside perceptual range
controls outside motor range
symbols outside learned interpretation
hidden system state
unrecoverable failure
resource demand beyond user capability
```

Design is therefore not merely arrangement of form.

It is the organization of a realizable capability relation.

---

## 52. Learning as Capability Reorganization

Learning changes the set of transitions an agent can reliably realize.

It may create:

```text
new distinctions
new operators
new compositions
new predictions
new error corrections
new representations
new evaluative relations
```

Let the agent capability system at time \(t\) be \(C_t\).

Learning produces:

\[
C_{t+1}
=
\Lambda(C_t,\eta_t,\text{feedback},\text{instruction},\text{practice})
\]

A learned sentence pattern becomes producible.

A learned route becomes navigable.

A learned social norm changes action selection.

Learning is therefore not mere accumulation of descriptions.

It is a realized transformation of future realizability.

---

## 53. Attention Selects Which Capability Is Exercised

An agent may possess many capabilities while exercising only one narrow transition at a time.

Attention helps allocate finite processing and control toward a selected realization.

The realized frame of discourse is therefore shaped by:

```text
what can be represented
what is currently attended
what can be expressed
what the medium preserves
what the interaction rewards
```

Noticing that a sentence is realized is not attention to an arbitrary quirk.

It is attention to the capability-to-token relation already active in the occurrence.

The sentence becomes a mirror for the process that instantiated it.

---

## 54. The Capability-Bounded Realization Principle

### Capability-Bounded Realization Principle

> An agent or organized system cannot realize a transition outside the effective capability of its actual configuration and couplings.

Formally:

\[
\operatorname{RealizedBy}(A,\eta,c)
\Rightarrow
\eta
\in
\operatorname{ExecClosure}(A,c)
\]

where \(\operatorname{ExecClosure}(A,c)\) is the feasible closure of transitions supported by the configured agent, its tools, infrastructure, environment, and collaborators.

This principle does not imply that the agent explicitly represented every transition.

It implies that the realized process remained within the transition structure actually supported by the coupled organization.

---

## 55. The Recursive Agent-Shaping Principle

### Recursive Agent-Shaping Principle

> Repeated organizations are shaped by the capabilities of their users, and repeated participation in those organizations reshapes the capabilities of the users.

Formally, let:

```text
C_t = agent capability organization
O_t = surrounding maintained organization
```

Then:

\[
O_{t+1}
=
F(O_t,C_t,\eta_t)
\]

and:

\[
C_{t+1}
=
G(C_t,O_{t+1},\eta_t)
\]

The coupled evolution is:

\[
(C_t,O_t)
\to
(C_{t+1},O_{t+1})
\]

This captures the co-development of:

```text
humans and language
humans and tools
humans and cities
humans and markets
humans and media
humans and institutions
```

---

## 56. The Interface Translation Principle

### Interface Translation Principle

> An interface extends capability when it converts distinctions and transitions from one system into forms executable or perceivable by another.

For source domain \(X\) and agent-accessible domain \(Y\), an interface \(T\) provides:

\[
T:X\to Y
\]

subject to preservation of the relations relevant to the task.

Examples include:

```text
infrared sensor
->
visible image
```

```text
microphone
->
digital signal
```

```text
map database
->
route instruction
```

```text
legal code
->
procedural form
```

```text
machine state
->
monitor display
```

The interface does not abolish either capability system.

It constructs a realizable coupling between them.

---

## 57. The Historical Capability Principle

### Historical Capability Principle

> A present capability may depend on realization histories whose intermediate organizations are absent from the current token but retained through infrastructure, training, standards, and artifacts.

A person can invoke a navigation service without reconstructing:

```text
satellite systems
surveying
coordinate standards
road databases
software stacks
network protocols
```

The omitted history is not present in full detail in the invocation.

But its organizational result remains embedded in the capability system.

Current realizability is therefore historically accumulated.

---

## 58. Limits of the Framework

The framework does not by itself determine:

```text
which objectives are morally correct
which social system is legitimate
which capability should be preserved
whether a referent exists independently
whether one realization is the unique correct implementation
whether a one-time occurrence proves stable competence
```

It also does not require every capability to belong to a conscious agent.

Biological, mechanical, computational, and institutional systems may support transition classes without reflective awareness.

The word `exercise` should therefore be interpreted operationally unless intention is explicitly required.

A realized exercise may be:

```text
intentional
habitual
automatic
learned
controlled
accidental
emergent
```

The central requirement is instantiated transition-supporting organization.

---

## 59. Open Questions

Several questions remain.

### Capability identity

When do two differently realized systems possess the same capability?

### System boundary

Which parts of body, tool, institution, and environment belong to the relevant capability system?

### Stability threshold

How much repeatability is required before generative sufficiency becomes operational capability?

### Representation

Which relations must be preserved for one realized token to instantiate the same sentence, concept, or operator as another?

### Objective formation

How do biological regulation, learning, culture, institutions, and reflection reorganize evaluative capability?

### Capability conflict

How should an agent choose when preserving one capability destroys another?

### Distributed responsibility

How should credit, blame, authority, and ownership be assigned when a realization depends on a large coupled system?

### Expansion limits

Which physically possible distinctions can be translated into human-usable interfaces, and at what cost?

---

## 60. Compact Formal Summary

Let:

```text
A  = agent or organized system
c  = current configuration
E  = environment
T  = tools and infrastructure
u  = operator, skill, or transition schema
a  = invocation parameters
η  = realized execution trace
φ  = instantiated pattern, role, or target
Γ  = interpretive context
H  = horizon
Θ  = constraints and reliability conditions
```

### Effective capability

\[
\operatorname{Cap}(A\oplus T,c,E,H,\Theta)
=
\left\{
\phi
\middle|
\exists p\in\operatorname{ExecPlans}(A\oplus T,c,E,H,\Theta):
p(c)\models\phi
\right\}
\]

### Realized token

\[
\operatorname{Realized}(\eta,\phi,\Gamma)
\Rightarrow
\operatorname{Occurred}(\eta)
\land
\operatorname{Instantiates}(\eta,\phi,\Gamma)
\]

### Capability-bounded realization

\[
\operatorname{RealizedBy}(A,\eta,c)
\Rightarrow
\eta\in\operatorname{ExecClosure}(A,c)
\]

### Generative sufficiency

\[
\operatorname{Realized}(\eta,\phi,\Gamma)
\Rightarrow
\exists S,p,c:
\operatorname{Executed}(S,p,c,\eta)
\]

### Stable capability is stronger than one token

\[
\operatorname{RealizedOnce}(A,\phi)
\not\Rightarrow
\operatorname{StableCapability}(A,\phi,\Theta)
\]

### Discourse realization

\[
\operatorname{RealizedDiscourse}(d,A,c)
\Rightarrow
\exists u\in\mathcal D_{\mathrm{exec}}(A,c):
\operatorname{Exec}(u,c)\models d
\]

### Capability-indexed discourse closure

\[
d\in D_R
\land
q\in\mathcal Q_{\mathrm{exec}}
\land
\operatorname{Executed}(q,d)
\Rightarrow
q(d)\in D_R
\]

### Interface translation

\[
T:X\to Y
\]

where \(T\) preserves task-relevant relations while converting source distinctions into an agent-accessible form.

### Recursive capability construction

\[
C_{t+1}
=
\operatorname{Closure}_{\mathrm{feasible}}(C_t,O_{t+1})
\]

### Coupled agent-organization evolution

\[
(C_t,O_t)
\to
(C_{t+1},O_{t+1})
\]

### Future capability effect

\[
c_t
\xrightarrow{u_t}
c_{t+1}
\Rightarrow
\mathcal C_t
\to
\mathcal C_{t+1}
\]

where the transition may preserve, enlarge, specialize, transfer, consume, or destroy future capability.

---

## 61. Central Statements

> Capability is maintained potential for a class of realizations.

> Realization is a particular instantiated transition.

> A realized occurrence presupposes sufficient realized organization for that occurrence.

> A realization token witnesses generative sufficiency, but not automatically stable reusable capability.

> Whenever discourse occurs, it is realized through an exercised discourse capability system.

> A realized sentence points back toward the organization capable of producing, carrying, and interpreting it.

> An agent cannot realize a transition outside the effective capability of its actual configuration and couplings.

> Capability is relational: body, tools, infrastructure, environment, authority, and other agents may all participate.

> Human-built organizations are concentrated around human perceptual, motor, cognitive, linguistic, and social capability.

> Displays, speakers, buildings, languages, markets, and entertainment are interface organizations shaped by the agents who repeatedly use them.

> Tools expand capability by translating otherwise inaccessible distinctions into agent-accessible interactions.

> Human organization recursively extends capability, then uses the extended capability as the basis for further organization.

> Every extended trajectory is realized through locally executable transitions.

> Local executability is necessary but does not by itself guarantee long-horizon reachability.

> Objectives that guide action must themselves be realized as selection-modifying organization.

> Retrospective commentary is a new realization produced from a configuration that already contains information generated by the earlier event.

> Calling an action irrational without reconstructing capability, belief, valuation, and system boundary may remove the organization required to explain it.

> Design is the construction of a reliable relation between user capability and system realization.

> Learning reorganizes future realizability.

---

## 62. Conclusion

The statement:

```text
This sentence is realized.
```

is not merely a reminder that the sentence exists.

It reveals a relation between potential and actuality.

Before the sentence occurred, a configured system possessed enough organization to make its production possible.

During the occurrence, that organization was exercised through locally admissible transitions.

After the occurrence, the sentence remained as a realized token and as evidence of the capability system that produced it.

The same structure applies beyond language.

A realized action is an exercised capability.

A realized computation is an exercised computational capability.

A realized route is an exercised navigation capability.

A realized institution is a repeatedly exercised coordination capability.

A realized interface is a coupling between capability systems.

This explains why the organized human world repeatedly points back toward human capacities.

Monitors expose distinctions human vision can use.

Speakers expose variations human hearing can use.

Buildings expose transitions human bodies can execute.

Languages preserve distinctions humans can produce, perceive, learn, and reproduce.

Supermarkets expose acquisition paths for human consumption.

Entertainment recruits human perceptual, emotional, and social organization.

Where direct human capability ends, tools may translate new physical domains into accessible forms.

Those tools become part of an extended capability system.

The extended system then supports further realization.

The resulting picture is not one of an abstract agent choosing freely among arbitrary possibilities.

It is one of finite organized systems constructing, inheriting, exercising, and extending capability under physical constraints.

Realization and capability are therefore complementary views of organized transition:

\[
\boxed{
\text{capability is realizable potential}
}
\]

\[
\boxed{
\text{realization is exercised capability}
}
\]

A sentence already said is realized.

Its realization is also a trace of what the coupled system was able to do.
