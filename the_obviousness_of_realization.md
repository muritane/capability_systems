# The Obviousness of Realization

## Why Labels Cannot Supply Missing Information, Models Cannot Override Their Data, and Authority Cannot Replace Causal Structure

### Abstract

Some of the most consequential errors in reasoning arise not from complicated logical failures, but from overlooking dependencies so elementary that they appear unworthy of explicit examination.

An ordinary material object requires physical realization. An observation requires some accessible distinction. Empirical learning requires information on which a learning process can operate. A classification requires criteria by which relevant differences can be distinguished. A reliable capability requires mechanisms that actually support the relevant behavior. An authorization requires a rule, relationship, or institution within which the authorization has meaning.

None of these dependencies is especially surprising.

Yet representations can obscure them.

A label can be mistaken for the property it is intended to describe. A certificate can be treated as though it produces the capability it certifies. A model can be expected to distinguish outcomes despite receiving a representation that has eliminated the relevant distinctions. An institutional category can be treated as though it determines the underlying structure of reality. A human capability can be regarded as irreducibly human even when its relevant informational and functional organization could, in principle, be implemented elsewhere.

The common error is the promotion of a representational distinction into an independent source of realization.

This paper proposes the **Realization-Dependency Principle**:

> A representation, classification, model, certificate, or declaration does not, by itself, supply the physical structure, information, causal mechanisms, or institutional relationships required for the properties attributed to its referent.

The principle is nearly obvious when stated explicitly.

Its significance comes from applying it consistently across different abstraction boundaries.

The resulting framework distinguishes realization, information, representation, regularity, capability, and authority without treating any of these domains as universally sovereign over the others.

It also explains why functional capabilities can become portable: their realization depends on reproducible informational and causal relationships, rather than on the prestige or identity of the category to which their original implementation belongs.

The fundamental question is therefore not which label a system possesses, but which distinctions and mechanisms actually exist, which relations they support, and whether the abstractions used to describe them preserve enough information for the conclusions being drawn.

---

## 1. Begin With the Obvious

Consider a statement:

**An ordinary material object cannot exist without the physical structure through which it is realized.**

A stone requires some physical constitution.

Its shape, mass, mechanical behavior, and thermal properties depend on the organization and interactions of its constituents.

Calling something a stone does not create that structure.

A description of a stone does not automatically instantiate one.

A certificate identifying an object as a stone does not confer mass upon an otherwise nonphysical description.

These observations appear trivial.

Now consider another statement:

**An empirical learning process cannot extract information about an unknown target from data that contain no relevant information about that target, unless additional informative assumptions, observations, or mechanisms are supplied.**

Again, the claim appears obvious.

A learning algorithm must operate on something.

That something may be an external observation, a measurement, a reward, an interaction history, a stored example, a simulated trajectory, or an internally generated signal.

But a description of learning does not automatically supply information to be learned.

Similarly:

- Calling a system intelligent does not create missing computational or causal mechanisms.
- Calling a person competent does not make an absent capability appear.
- Calling an object an agent does not establish that it possesses an internal model.
- Calling an object a non-agent does not remove its causal properties.
- Calling a classification authoritative does not establish its predictive accuracy.
- Calling a representation complete does not restore distinctions discarded by the representation.

Why do these statements become important if each appears so obvious?

Because systems can operate through many layers of abstraction.

At one level, an operation depends on physical mechanisms.

At another, it is described through information and computation.

At another, it is encapsulated behind an interface.

At another, it is assigned a name, role, category, or institutional status.

Each additional layer may make the underlying realization less visible.

The abstraction can become so convenient that the requirements supporting it disappear from attention.

The resulting mistake is not necessarily ignorance of physical or informational dependencies.

It is reasoning as though those dependencies had ceased to matter.

This is the **Abstraction-Induced Dependency Omission**:

> An error in which a representation is used as though the conditions required to realize its referent or claimed properties no longer need to be established.

The correction is simple.

Recover the dependency.

What actually realizes the property?

What information supports the inference?

What mechanism produces the result?

What relationship gives the authorization its scope?

If those questions cannot be answered, the original label may be insufficient.

---

## 2. Physical Realization Precedes Physical Description

Consider a rock.

The rock participates in physical processes whether or not any observer identifies it as a rock.

It has properties determined by its physical organization and interactions.

It may resist compression, exchange heat, exert gravitational influence, fracture under stress, or transfer momentum during a collision.

None of these interactions requires the rock to recognize itself.

Nor must it possess preferences, goals, intentions, representations, or an internal theory of mechanics.

A falling rock can kill a human.

The rock's causal influence does not depend on its membership in the category *agent*.

For predicting the consequences of the falling rock, its mass, velocity, trajectory, composition, geometry, and surrounding conditions may be highly relevant.

Whether it is classified as an agent may contribute almost nothing to that particular prediction.

Conversely, when someone places the rock on a stack of papers, the person may supply the selection, planning, and positioning.

The rock supplies physical properties that make it useful as a paperweight.

The person does not grant the rock causal participation.

The person organizes an interaction that exploits causal properties already available.

This yields a basic distinction:

**Causal participation is not conditional on agency.**

Agency may describe a particular organization of causal processes.

It is not a prerequisite for causal relevance.

### 2.1 Material constitution is an example, not a universal ontology

For ordinary material objects, atomic and molecular organization is often an appropriate level of explanation.

But not every physical entity is an atomic object.

Electromagnetic radiation, fields, and other physical phenomena require descriptions that cannot be reduced to the claim that every physical thing must consist of atoms.

The more general point is:

> An actually realized physical entity or process requires whatever physical conditions constitute its realization; describing or naming it does not substitute for those conditions.

The principle does not require a final theory of physics.

It requires only that descriptions not be confused with the realization of what they describe.

### 2.2 The category cannot impose an additional physical law

Suppose an observer defines:

\[
L(x)=\text{Non-agent}
\]

This label groups the rock with other systems under some classification rule.

But the label does not imply:

\[
\text{Causal influence}(x)=0
\]

unless that implication is independently justified by the definition and the underlying system.

A category can preserve useful regularities.

It cannot make unsupported physical consequences disappear.

The rock does not become causally insignificant because a model emphasizes goal-directed behavior.

And a system classified as an agent does not become causally sovereign because its behavior can be represented through goals.

The classification is a representational operation.

The causal interactions remain realized processes.

---

## 3. Categories Are Equivalence Classes Relative to Selected Distinctions

A category can be understood as grouping objects or states that are treated as equivalent for a particular purpose.

Let \(S\) denote a space of realized states.

Let:

\[
\alpha:S\rightarrow A
\]

be an abstraction mapping those states into a set of categories \(A\).

We can define an equivalence relation:

\[
x\sim_\alpha y
\iff
\alpha(x)=\alpha(y)
\]

Two states are equivalent under the abstraction when they receive the same abstract representation.

This does not require them to be physically identical.

It means that the abstraction does not distinguish them.

The abstraction may intentionally discard differences considered irrelevant to some task.

For example, two different rocks might be assigned the same material classification despite differing in shape, position, temperature, and fracture history.

This may be entirely appropriate for predicting one property.

It may be inadequate for predicting another.

An abstraction therefore establishes a boundary of distinguishability.

It does not establish a boundary of reality.

### 3.1 Equivalence in a model is not equivalence under every possible operation

Suppose:

\[
\alpha(x_1)=\alpha(x_2)
\]

The model treats the two states as equivalent.

Now suppose an operation produces different consequences:

\[
f(x_1)\neq f(x_2)
\]

Then the abstraction has discarded a distinction relevant to the operation \(f\).

This does not necessarily make the abstraction defective.

It makes it insufficient for that particular inference.

An abstraction can be accurate for one task and inadequate for another.

For example, classifying two vehicles by exterior appearance may preserve distinctions useful for visual identification.

It may not preserve distinctions relevant to operating them safely.

The underlying vehicle configurations may differ in braking behavior, mass distribution, control interfaces, or operating requirements.

No amount of confidence in the visual category can recover an operational difference that the representation does not preserve.

### 3.2 Categories do not legislate reality

This yields the **Abstraction Non-Sovereignty Principle**:

> Membership in a descriptive category does not, by itself, establish the full causal properties, reachable states, possible interactions, or normative status of the system being classified.

The principle does not imply that categories are meaningless.

A good category can preserve highly useful regularities.

The error arises when the category is treated as more complete than its construction and evidence justify.

An abstraction is useful insofar as it preserves the distinctions required for an inference.

It is not an authority capable of eliminating distinctions it fails to represent.

---

## 4. Information Must Be Available for Information-Dependent Learning

The same dependency appears in machine learning.

A learning system may be described as capable of classification, prediction, adaptation, or model construction.

But the description does not establish which information the system can access.

Suppose an unknown target property is \(Y\).

The learner receives an observation \(X\).

It constructs a representation:

\[
Z=\alpha(X)
\]

and attempts to predict:

\[
\hat{Y}=g(Z)
\]

If the representation \(Z\) preserves distinctions relevant to \(Y\), the learner may be able to construct a useful predictive relationship.

If it does not, the learner faces an information limitation.

### 4.1 A missing distinction cannot be recovered from the same insufficient representation alone

Suppose two possible observations become identical after abstraction:

\[
\alpha(x_1)=\alpha(x_2)
\]

but the required outputs differ:

\[
f(x_1)\neq f(x_2)
\]

Then no deterministic function \(g\) of the representation alone can satisfy both:

\[
g(\alpha(x_1))=f(x_1)
\]

and

\[
g(\alpha(x_2))=f(x_2)
\]

because the left-hand arguments are identical while the required outputs differ.

The limitation is not a lack of confidence.

It is not insufficient authority.

It is not a deficiency that disappears when the learner is called intelligent.

**The information required to distinguish the cases is unavailable in the representation.**

The learner must obtain additional information, modify the representation, introduce informative assumptions, or tolerate uncertainty and error.

### 4.2 Digits do not spontaneously become missing information

Imagine a dataset containing only digit symbols.

An observer wants a learner to distinguish properties represented by alphabetic characters.

There are two possibilities.

First, the digits may encode the relevant information.

A numerical encoding can represent letters, images, sound, or arbitrary structured data.

In that case, the visual appearance of the symbols is not the limiting factor.

Second, the digits may contain no information about the intended alphabetic target.

Then the desired distinction cannot be recovered merely by renaming the dataset or declaring the output category.

The essential question is not whether the input looks like digits or letters.

It is whether the input, together with available assumptions and mechanisms, contains information sufficient to support the intended inference.

This gives the **Task-Relative Information Sufficiency Principle**:

> A representation supports a reliable inference only to the extent that it preserves, or can be combined with available information to recover, the distinctions required for that inference under the relevant conditions.

This principle is elementary.

Its consequences are substantial.

---

## 5. The Information-Theoretic Boundary

Information theory provides a formal expression of the same dependency.

Suppose:

\[
Y\rightarrow X\rightarrow Z
\]

forms a Markov chain, where \(Z\) is obtained by processing \(X\), without additional information about \(Y\).

The data processing inequality gives:

\[
\boxed{I(Y;Z)\leq I(Y;X)}
\]

Here, \(I\) denotes mutual information.

The processed representation cannot contain more mutual information about the target than the information available in the original observation under these assumptions.

A transformation can reorganize information.

It can make relevant patterns easier to access.

It can discard irrelevant variation.

It can produce a compact and operationally useful representation.

But it cannot recover distinctions that are absent from its entire information source merely by applying a prestigious label to the result.

### 5.1 Compression is not inherently information failure

The objective is not necessarily to preserve every microscopic detail.

A representation can discard enormous amounts of information while retaining everything required for a particular task.

Suppose the relevant property is:

\[
f:S\rightarrow Y
\]

and the abstraction is:

\[
\alpha:S\rightarrow A
\]

For the abstraction to determine \(f\) exactly, there must exist a function:

\[
g:A\rightarrow Y
\]

such that:

\[
\boxed{f=g\circ\alpha}
\]

Equivalently, whenever:

\[
\alpha(x_1)=\alpha(x_2)
\]

we must have:

\[
f(x_1)=f(x_2)
\]

The relevant target property must be constant within each equivalence class of the abstraction.

If this condition holds, the abstraction preserves enough information for the specified deterministic task.

If it fails, the abstraction is insufficient for that task.

For stochastic tasks, a related requirement is that the abstract representation preserve the relevant conditional distribution of outcomes, rather than determine one exact answer.

### 5.2 The failure is task-dependent

An abstraction that is insufficient for one target may be sufficient for another.

A photograph might preserve enough information to distinguish vehicle models.

It may not preserve enough information to determine the condition of a concealed braking component.

A certificate might preserve information about successful completion of a qualification procedure.

It may not preserve enough information to determine a person's current physical fitness to operate a vehicle.

Therefore, information loss is not simply an absolute defect.

It must be evaluated relative to the distinctions a task requires.

---

## 6. Labels Are Not the Data They Describe

Consider a dataset containing observations of cats.

An authority assigns the label *dog* to each observation.

What has changed?

The physical animals have not changed.

The measured image features have not changed.

The original causal processes producing the observations have not changed.

The assigned labels have changed.

A supervised learning system may then learn to associate the features of cats with the output token *dog*.

Whether this is an error depends on the intended semantics of the label.

If *dog* is merely an arbitrary token intentionally defined to mean cats, the system may learn that convention accurately.

But if the task requires the ordinary distinction between cats and dogs, the labels are inconsistent with the intended target.

The model is being trained toward a relationship that does not match the desired classification.

### 6.1 Supervision is an information source, not a guarantee of truth

In supervised learning, supplied targets guide the optimization process.

A typical objective is:

\[
\theta^*
=
\arg\min_\theta
\sum_{i=1}^{n}
\ell(f_\theta(x_i),y_i)
\]

where \(x_i\) is an input, \(y_i\) is its supplied label, and \(\ell\) measures prediction error relative to that label.

The optimization procedure does not automatically establish that \(y_i\) corresponds to the relevant property of reality.

It establishes pressure to reproduce the supplied targets.

If the targets are systematically inaccurate, the optimization can favor a systematically inaccurate predictor.

The labeler may be human.

The labeler may be an institution.

The labeler may be another model.

None of these identities makes the labels automatically correct.

Their usefulness depends on the relationship between the labels and the target being learned.

### 6.2 Unsupervised learning does not eliminate the problem

Unsupervised learning attempts to identify structure without predefined labels for the specific task.

But discovered clusters do not automatically establish unique natural categories.

Different feature spaces, distance metrics, objectives, and resolutions may produce different groupings.

Data can support multiple useful abstractions.

Some useful targets do not form clean clusters at all.

Therefore, the solution is not a universal rule that labels must always be inferred from clusters.

The more precise requirement is:

> The selected representation and classification must preserve the regularities relevant to the intended task, and claims about those regularities must be supported by appropriate evidence.

Supervised and unsupervised learning are different arrangements for extracting or organizing information.

Neither grants its categories independent authority over the data-generating process.

---

## 7. No Data, No Empirical Correction

The phrase *without data there is nothing for learning to operate on* captures a foundational constraint, but requires a precise scope.

A system can possess built-in structure before receiving observations.

An algorithm may include prior assumptions, an initial model, programmed rules, or parameters inherited from earlier training.

It can also generate internal trajectories through simulation.

Such a system may perform computation or deduction without receiving new external measurements.

But it cannot obtain new evidence about an otherwise unconstrained external target merely by asserting that it is learning.

If no informative signal about the target is available, empirical discrimination among possibilities is limited by the assumptions already supplied.

### 7.1 Learning requires an informational difference

Consider a learner updating an internal state:

\[
m_{t+1}=U(m_t,d_t)
\]

where:

- \(m_t\) is its current model or memory;
- \(d_t\) is information available during the update;
- \(U\) is the update mechanism.

For an update to become an evidence-grounded refinement of a target, the available information must support some relevant distinction.

The update may be driven by prediction error, observation, reward, feedback, interaction history, or another informative signal.

Without such information, changing the model is not necessarily learning something new about the target.

A parameter can change without becoming more accurate.

A system can become more confident without gaining evidence.

A representation can become more complicated without preserving additional task-relevant information.

### 7.2 Simulation does not escape realization requirements

A model may generate synthetic examples.

Those examples can support useful learning when the simulator embodies relevant structure.

But the simulator's outputs depend on its assumptions, implementation, initial conditions, and available information.

A synthetic dataset does not become an independent empirical authority merely because it contains many examples.

Its usefulness depends on whether the simulated regularities transfer to the target system.

This is another instance of the same principle:

**Generated representations do not automatically supply the missing correspondence between a model and the world it intends to describe.**

---

## 8. Capability Is Realized Through Mechanisms, Not Conferred by Names

Now consider the category *capable*.

Suppose someone declares:

"This system can perform operation \(a\)."

The declaration is a proposition about the system.

Whether the operation is actually realizable depends on the relevant mechanisms and conditions.

A machine may possess the necessary actuator but lack power.

A controller may have the correct decision rule but lack the required sensor.

A trained model may classify an intended action accurately but possess no interface through which to execute it.

A human may know how to perform a task but lack the equipment required in a particular environment.

These are not merely linguistic differences.

They concern distinct causal pathways.

### 8.1 Recognition is not execution

A system may recognize a condition without being able to modify it.

For example, a detector can identify an electrical fault.

Whether it can interrupt the circuit depends on its coupling to a protective mechanism.

Conversely, a physical mechanism can affect an environment without representing that environment explicitly.

A falling rock transfers momentum.

A spring responds to displacement.

A basic protective circuit responds to electrical conditions.

None requires a symbolic account of its actions.

More elaborate systems may include feedback, memory, learning, prediction, and self-modification.

These can extend or reorganize capabilities.

But each additional capacity depends on corresponding mechanisms.

The classification *agent* does not supply them.

### 8.2 Capability is condition-dependent

Let:

\[
C(s,a,e)
\]

mean that system \(s\) can reliably perform action \(a\) under conditions \(e\).

Capability is not necessarily a permanent property independent of context.

A vehicle may be operable on one surface but not another.

A person may be competent when rested and impaired when exhausted.

A machine may work within a specified temperature range and fail outside it.

A reliable capability claim therefore requires conditions under which reliability is expected.

A label that omits those conditions may be useful shorthand.

It should not be mistaken for an unconditional guarantee.

---

## 9. The Certificate Problem: Classification, Capability, and Permission

The distinction becomes especially visible in institutional certification.

Suppose a person receives a qualification to operate a particular category of vehicle.

An institution performs an assessment.

The assessment produces evidence.

A certification procedure evaluates that evidence according to established rules.

The institution issues a credential.

The credential is then recognized by a legal or organizational system.

Several different relationships exist within this process.

### 9.1 Capability

The person's realized ability to operate the vehicle under relevant conditions.

### 9.2 Assessment

A procedure that attempts to infer capability from observed performance or other evidence.

### 9.3 Certification

An institutional representation that certain assessment or eligibility conditions have been satisfied.

### 9.4 Permission

A normative or institutional relationship under which the person is authorized to perform specified actions.

These relationships interact.

But they are not identical.

A capable person can lack a valid certificate.

A certified person can lose relevant competence.

A certificate can remain administratively valid while its reliability as a predictor of present capability changes.

A person can have capability and certification while still facing additional restrictions on a particular action.

Thus:

\[
\text{Capability}
\not\equiv
\text{Certification}
\not\equiv
\text{Permission}
\]

The institution can establish rules for issuing and recognizing certificates.

It cannot make an absent physical or cognitive capability appear merely through issuance.

### 9.5 Authority has a domain

This does not make institutional authority meaningless.

A legitimate authority may establish binding rules within its jurisdiction.

A license can affect access to infrastructure, insurance, enforcement, and legal responsibility.

These are real consequences.

But they occur through social, legal, and technical mechanisms that recognize the credential.

The authority does not thereby gain universal control over the underlying capability.

**Authority over a classification or authorization process is not equivalent to authority over the causal regularity the classification is intended to track.**

### 9.6 A failed prediction does not automatically invalidate jurisdiction

Suppose a licensed operator proves unable to perform safely.

This provides evidence against the claim that licensing guarantees current competence.

It does not automatically establish that the issuing institution lacks legitimate authority.

The institutional rule and the predictive reliability of its assessment are different questions.

A classification can be inaccurate while its issuing procedure remains legally valid.

An accurate classification can also be produced by someone lacking authority to issue an official credential.

Separating these relationships is necessary for precise reasoning.

---

## 10. Can Certification Remain Aligned With Reality Indefinitely?

A category may be accurate at one point and become inadequate later.

Let the realized system state evolve according to:

\[
s_{t+1}=T(s_t,a_t,e_t)
\]

where \(a_t\) represents an intervention and \(e_t\) represents relevant environmental conditions.

Let:

\[
\alpha_t(s_t)
\]

be the system's classification at time \(t\).

An abstract state-transition model is exact when the abstraction preserves the distinctions required to determine the abstract successor.

For a deterministic transition system, one possible compatibility requirement is:

\[
\alpha(T(s))=\bar T(\alpha(s))
\]

for some abstract transition function \(\bar T\).

If no such function exists, the abstract category alone does not determine the next abstract state.

For example, two people holding the same license may experience different changes in ability because their relevant physical conditions, training, and environments differ.

The license classification does not preserve all information necessary to predict those changes.

### 10.1 Stable labels do not guarantee stable properties

An institutional record may remain unchanged while the realized system evolves.

The certificate may still exist.

The person may still possess it.

The classification may still be recognized.

Yet the underlying capability may have changed.

This introduces a **Classification–Realization Drift Problem**:

> A classification can remain fixed, or continue to be applied under unchanged rules, while the properties relevant to its intended interpretation change.

The appropriate response depends on the application.

It may involve reassessment, additional measurement, narrower claims, revised categories, or explicit uncertainty.

The correction is not necessarily to abolish certification.

It is to avoid treating certification as an infallible substitute for continued correspondence with the relevant realized conditions.

---

## 11. The Human Exceptionalism Problem

The same logic applies to claims about human and machine capabilities.

Suppose a human performs a classification task reliably.

An observer may describe the performance as intuition, expertise, understanding, or judgment.

Those descriptions can be useful.

But they do not eliminate the mechanisms through which the performance occurs.

The human system receives information.

It processes observations through learned and inherited organization.

It distinguishes relevant patterns.

It produces outputs or interventions.

If another realized system can reproduce the information-processing and causal relationships required for the task, there is no general logical requirement that the capability remain exclusive to the original human implementation.

This yields the **Functional Portability Principle**:

> A capability is portable across realized systems to the extent that the information, transformations, feedback, and causal mechanisms required for its reliable operation can be reproduced or functionally substituted under the relevant conditions.

This is not a guarantee that every human capability can be transferred with current technology.

It is a statement about what determines successful transfer.

### 11.1 The original implementation is not necessarily the required implementation

A bird flies using biological structures.

An aircraft flies through different mechanical structures.

The two systems do not need identical internal mechanisms to produce certain comparable outcomes.

Likewise, a human expert may recognize a fault through experience-dependent perceptual mechanisms.

A machine may implement a related diagnostic capability through a different sensor architecture and learned inference procedure.

The relevant question is whether the new implementation preserves the functional requirements of the task.

It is not whether the new system belongs to the same biological category.

### 11.2 Behavioral imitation is not necessarily capability transfer

However, reproducing an expert's answers on a finite dataset does not automatically establish equivalent capability.

The dataset may omit relevant conditions.

The expert may use additional contextual information.

The environment may change.

The machine may fail when inputs leave the region represented by its training examples.

Therefore, capability transfer requires a validity domain and appropriate verification.

It may require additional sensing, active intervention, feedback, or adaptation.

A classifier trained to reproduce human responses is not necessarily equivalent to the human system over every possible condition.

But neither does the category *human* establish an intrinsic impossibility of functional transfer.

### 11.3 Humans are not infallible reference systems

A human expert may provide useful labels.

Those labels can also be wrong.

If a machine reproduces the expert's errors, high agreement with the expert does not establish high accuracy relative to the underlying task.

Where an independent target can be established, both human and machine performance should be evaluated against it.

The human may be the source of training data.

That does not make the human the sovereign authority over the regularity being investigated.

The same applies in reverse.

Calling a system an artificial intelligence does not establish that it possesses the mechanisms or information required for a claimed capability.

Both systems remain subject to the conditions of their realization.

---

## 12. Agency Is an Organizational Description, Not a Rank of Existence

A related problem appears when systems are arranged according to increasing agency, intelligence, autonomy, or control.

One might compare:

- a rock;
- a condition-sensitive circuit;
- a feedback controller;
- an adaptive cellular system;
- an animal nervous system;
- a learning computational system;
- a system capable of modifying aspects of its own organization.

These systems exhibit different forms of causal structure.

They may differ in sensing, memory, feedback, representation, prediction, adaptation, and self-modification.

Such differences are worth studying.

But the classification must not silently become a ranking of existential participation.

A rock already participates in physical processes.

A circuit does not become more real because it responds conditionally.

A cell does not gain a greater right to exist because it adapts.

An animal does not become causally sovereign because it possesses internal models.

A sophisticated computational system does not escape physical and informational constraints because it can modify its own parameters.

**Increasing organizational complexity does not retroactively establish the participation of a system that was already realized.**

### 12.1 Adaptation introduces additional mechanisms

One useful distinction concerns the modification of response mechanisms.

A fixed circuit may respond differently to different inputs while retaining the same response rule.

An adaptive system can alter its future response characteristics based on prior interactions.

A learning system may change internal representations or parameters.

A more elaborate system may modify aspects of its learning or control architecture.

These developments can expand reachable behaviors.

But they are additional realizable capabilities, not certificates of participation.

### 12.2 Organizational categories remain task-relative

A distinction between agents and non-agents may be highly useful for predicting goal-directed behavior.

It may be nearly irrelevant for predicting the mechanical consequences of a falling object.

Neither result makes the category universally correct or universally useless.

Its value depends on whether it preserves the distinctions needed for the particular question.

---

## 13. Why the Word "Just" Often Reveals the Error

Consider these statements:

"It's just a rock."

"It's just a chemical reaction."

"It's just a machine."

"It's just an algorithm."

"It's just a model."

"It's just reality."

Each may be grammatically ordinary.

But the modifier *just* can conceal an unsupported inference.

The reasoning may implicitly proceed as follows:

1. A system can be described using category \(C\).
2. The speaker associates \(C\) with a limited set of properties.
3. The speaker concludes that other properties or consequences are irrelevant, absent, or unworthy of investigation.

The conclusion does not follow merely from category membership.

A chemical reaction may be extraordinarily consequential.

A machine may implement complex behavior.

An algorithm may support useful inference.

A rock may transfer lethal kinetic energy.

And describing something as reality does not resolve the structure, origins, or consequences of what is real.

### 13.1 Reduction is not elimination

Showing that a phenomenon has a physical realization does not demonstrate that higher-level descriptions are useless.

Conversely, finding a useful high-level description does not establish that the description has independent authority over its realization.

A system may be describable at multiple levels.

The levels may preserve different regularities.

An adequate model must be evaluated according to what it explains or predicts.

The term *just* is justified when the intended reduction is actually supported.

It becomes misleading when it transforms a partial explanation into a claim of completeness.

### 13.2 Epistemic humility is preserving the distinction between known and omitted properties

An epistemically careful classification does not require refusing to classify.

It requires recognizing what the classification establishes and what it leaves unresolved.

For example:

"This object is classified as a non-agent under the selected criteria. That classification does not determine its mechanical consequences."

Or:

"This person holds a valid credential. That credential does not by itself establish current competence under every operating condition."

Or:

"This model predicts the supplied labels accurately. That does not establish that the labels are correct relative to the intended real-world target."

The qualification is not indecision.

It is control over the scope of inference.

---

## 14. Representation Can Affect Reality Without Becoming Sovereign Over It

A potential objection arises.

If categories are merely representations, how can they have consequences?

A driver's license can change whether someone is allowed to operate a vehicle.

A database role can change which operations a user may perform.

A classifier can trigger an alarm.

A model output can cause a robot to move.

Do these examples show that representations create reality?

They show something more precise.

**Representations can participate causally when realized mechanisms respond to them.**

Suppose a system receives a label \(L\).

A control mechanism implements:

\[
a=\pi(L,s)
\]

where \(s\) includes additional relevant system state.

The label can influence the selected action.

But this influence depends on a mechanism that interprets the label and connects it to an actual transition.

A database credential affects access because software checks the credential and applies rules.

A legal document affects institutional behavior because social and legal mechanisms recognize it.

A classification changes machine behavior because the classifier's output is coupled to an action-selection process.

The representation matters.

But its causal effect is realized through mechanisms that are not supplied merely by the abstract meaning of the label.

### 14.1 Institutional authority is a realized relationship

Authority itself is not necessarily illusory.

It can be realized through enforceable rules, institutional arrangements, recognized obligations, technical infrastructure, and coordinated behavior.

But its existence and scope depend on those relationships.

An authority that can issue a qualification certificate does not thereby acquire control over the underlying laws governing the qualified activity.

A legal prohibition can affect behavior and consequences without altering whether the prohibited action is physically possible.

A system can be capable of an action while lacking authorization to perform it.

A system can be authorized to perform an action while lacking the capability required to execute it successfully.

These distinctions prevent institutional classification from being confused with causal realization.

---

## 15. A Unified Dependency Architecture

The preceding observations can be organized into a common architecture.

### Level 0 — Realization

Some physical or otherwise actually realized process exists.

Its existence is not created by the description applied to it.

### Level 1 — Causal interaction

The realized process interacts with other realized processes under the conditions governing those interactions.

Agency is not a prerequisite.

### Level 2 — Accessible distinctions

A system has informational or causal access to differences in relevant states or consequences.

The distinctions available depend on its coupling, organization, and environment.

### Level 3 — Representation

Some distinctions are retained, transformed, compressed, or organized into internal states, observations, symbols, or categories.

A representation need not preserve every property of its referent.

### Level 4 — Inference and learning

Available distinctions are used to form predictions, classifications, explanations, or updates.

The reliability of these operations depends on the information and regularities they preserve.

### Level 5 — Executable capability

A system uses realized mechanisms to produce outcomes under specified conditions.

The representation of a desired outcome does not guarantee its reachability.

### Level 6 — Interfaces and certification

Capabilities, roles, and properties may be encapsulated behind labels, interfaces, certificates, or other recognized abstractions.

These can enable coordination and reliable reuse.

They do not eliminate the mechanisms or validity conditions supporting them.

### Level 7 — Recursive refinement

A system may investigate discrepancies between representation and realization.

It can revise categories, obtain additional information, alter mechanisms, and refine its future inferences or interventions.

This architecture is not a necessary chronological sequence for every system.

A rock can participate causally without representation.

A fixed controller can respond conditionally without learning.

A learning system can adapt without possessing an explicit symbolic model.

A legal authority can recognize a certificate without being the original producer of the certified capability.

The levels distinguish dependencies and organizational properties.

They do not assign degrees of reality or existential legitimacy.

---

## 16. Verification Is Where Representational Claims Encounter Their Limits

A representation can be internally consistent while failing to correspond to the intended system.

A certificate can be validly issued while poorly predicting actual performance.

A machine-learning model can minimize its training loss while failing under new operating conditions.

A category can be coherent while discarding the distinctions needed for a particular intervention.

These failures become visible when predictions or actions encounter relevant evidence and consequences.

This is the central role of verification.

Verification does not make the target regularity true.

It tests whether the model's claims correspond to the target under the specified conditions.

### 16.1 The correction is not always additional complexity

If a representation fails, several explanations are possible:

- Relevant information was lost.
- Important information was never observed.
- The inference mechanism was inadequate.
- The underlying relationship changed.
- The target was incorrectly specified.
- The labels were systematically misleading.
- The claimed capability lacked an executable mechanism.
- The test conditions exceeded the model's validity domain.

These failures require different corrections.

Adding more parameters does not necessarily repair missing information.

Collecting more examples does not necessarily repair systematically incorrect labels.

Increasing institutional confidence does not repair an inaccurate assessment.

A more elaborate explanation does not create an absent causal pathway.

The appropriate response depends on identifying which dependency failed.

### 16.2 Reality does not have to conform to the representation

Suppose a model predicts outcome \(y\).

The realized process produces outcome \(y'\).

If:

\[
y'\neq y
\]

then some aspect of the prediction, assumptions, implementation, or modeled domain requires examination.

The discrepancy does not establish that the world violated the model's authority.

The model has no such authority.

It is an instrument for describing and predicting selected aspects of a realized system.

This does not mean every observed mismatch immediately falsifies an entire theory.

Measurements can be noisy, implementations can be faulty, and models may be probabilistic.

But the burden remains on establishing correspondence, not on demanding that realization obey a classification.

---

## 17. The Obviousness Is the Point

Why build a framework around propositions that are almost self-evident?

Because complexity can obscure elementary dependencies without eliminating them.

A software interface can hide its implementation.

A learned representation can hide the original information sources.

An institutional qualification can hide the evidence and assumptions behind certification.

An expert judgment can hide the sensory, cognitive, and historical processes supporting it.

An agent-level description can hide the physical mechanisms realizing the behavior.

These abstractions are often valuable precisely because they conceal unnecessary implementation detail.

But concealment creates the possibility of overgeneralization.

A user may infer that an interface can provide an operation beyond its supported domain.

An institution may treat a credential as a permanent guarantee.

A learner may be expected to infer distinctions absent from its input.

An observer may treat intelligence or agency as though it supplies capabilities independently of mechanisms.

The recurring error is:

**The successful abstraction of a dependency is mistaken for the elimination of that dependency.**

A processor instruction does not eliminate semiconductor physics.

A database label does not eliminate stored-state requirements.

A diagnostic model does not eliminate the need for informative observations.

A driving qualification does not eliminate the conditions required for safe driving.

An agent classification does not eliminate the physical constraints governing the agent.

What has changed is the level at which the system is represented.

Not the requirement that the operation actually be realized.

### 17.1 Obvious does not mean operationally irrelevant

A dependency may be obvious in isolation yet frequently violated in complex reasoning.

This is particularly likely when the effects of a missing dependency are delayed.

An inaccurate label may produce plausible outputs for some time.

A certificate may be accepted long after the relevant competence has changed.

A model may perform successfully within a narrow test domain.

An imagined authority may influence behavior even when the corresponding permission requirement has not been established.

The abstraction continues functioning sufficiently well to conceal its limitations.

Until a relevant distinction matters.

At that point, the omitted dependency becomes visible.

---

## 18. Final Synthesis: The World Does Not Inherit the Limitations or Privileges of Our Labels

A rock is not causally insignificant because it lacks agency.

A person is not automatically competent because they possess a certificate.

A learning algorithm does not obtain absent information because it has been instructed to learn.

An inaccurate label does not change the object being labeled.

A human capability does not become fundamentally untransferable merely because its original implementation is biological.

An artificial system does not acquire an absent capability because its category name suggests intelligence.

And an authority does not acquire control over physical regularities merely because it has the power to issue recognized classifications.

These statements share one structure.

The representation does not replace the realization.

The category does not replace the relevant distinctions.

The certificate does not replace the capability.

The permission does not replace the mechanism.

The model does not replace the information required for its inference.

The prediction does not replace the event being predicted.

The successful abstraction does not eliminate the conditions supporting it.

This yields the central principle:

### Realization-Dependency Principle

> Every actual property, inference, capability, and institutionally consequential operation depends on the realized structures, information, relationships, and mechanisms that support it. Describing, classifying, authorizing, or modeling those dependencies does not, by itself, supply what is absent.

And its representational counterpart:

### Abstraction-Scope Principle

> A representation justifies only those inferences for which it preserves sufficient relevant distinctions, together with any additional justified assumptions and information on which the inference depends.

And its consequence for learning:

### Information-Grounded Learning Principle

> Empirical learning can refine a model of a target only to the extent that its available observations, feedback, prior information, or justified structural assumptions support distinctions relevant to that target.

And its consequence for capability:

### Functional Portability Principle

> A capability can be reproduced in another system when the necessary informational and causal functions can be realized sufficiently reliably within the target conditions, whether or not the new system shares the original implementation's category or structure.

And its consequence for authority:

### Authority–Realization Separation Principle

> Authority can establish recognized permissions, obligations, and classifications within applicable rule systems, but it cannot make an unsupported causal or informational claim true merely through recognition.

These principles do not eliminate abstraction.

They explain what makes abstraction reliable.

They do not eliminate categories.

They restrict the conclusions categories can justify.

They do not eliminate authority.

They preserve the distinction between legitimate institutional rules and the empirical properties those rules may attempt to track.

They do not reduce human expertise to something automatically transferable.

They identify the conditions under which relevant capabilities could be reproduced, and the evidence required to establish that reproduction.

They do not make reality trivial.

They establish that no descriptive layer can exempt itself from the requirements of realization.

The final correction is therefore almost embarrassingly simple:

**No amount of naming supplies missing structure.**

**No amount of labeling supplies missing information.**

**No amount of certification supplies missing capability.**

**No amount of authority supplies missing causal regularity.**

**And no amount of abstraction makes the conditions of realization disappear.**

An abstraction may hide those conditions.

It may compress them.

It may organize access to them.

It may enable their discovery, reuse, and modification.

But it cannot abolish them through description alone.

That is why the obviousness matters.

The problem is not that reality is too simple to require sophisticated models.

It is that sophisticated models remain dependent on relationships that can be obscured by their own success.

**The more powerful an abstraction becomes, the more important it is to remember what the abstraction has actually preserved, what it has discarded, and what must still be realized.**

---

### Relationship to *No Permission Required to Participate*

This framework extends several distinctions from *No Permission Required to Participate*.

The earlier framework establishes that actual participation does not require an additional existential authorization and that representation, agency, capability, and authority must not be conflated.

The present framework focuses on the informational and explanatory consequences of those distinctions.

It develops five connections:

1. **From realized participation to causal relevance.** Systems need not satisfy agency criteria to influence realized outcomes.
2. **From representation to information sufficiency.** A classification cannot justify distinctions that its information does not support.
3. **From capability to functional portability.** A capability depends on realizable mechanisms rather than membership in a privileged descriptive category.
4. **From authority to certification validity.** Institutional recognition and empirical correspondence are separate relationships.
5. **From recursive learning to abstraction refinement.** Models can improve by identifying which relevant distinctions have been lost, omitted, or incorrectly represented.

Together, the two frameworks support a common methodological commitment:

> Begin with what is actually realized. Identify the distinctions and mechanisms available. Construct abstractions that preserve what matters for the intended task. Test their correspondence with relevant consequences. Revise them when that correspondence fails. Never treat the abstraction itself as an authority capable of overriding its own realization conditions.

**Participation requires no existential certificate. Reliable inference requires sufficient information. Effective capability requires working mechanisms. Legitimate permission requires an applicable authority relation. None is a substitute for the others.**
