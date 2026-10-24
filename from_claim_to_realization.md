Why definitions, equivalences, and representations do not establish their own correspondence to reality

A standalone framework for examining equality, interpretation, implementation, evidence, and participation.

# Abstract

A representation can assert that two things are equal, that a program performs an operation, that a model recognizes an object, or that one participant has authority over another. Such statements may be meaningful, precisely defined, and even formally valid. Yet none of those features alone establishes that the corresponding relationship holds in the real system being described. Between a statement and its purported realization lie interpretation, implementation, relevant dependencies, and evidence. This paper develops a general discipline for making that bridge explicit.

The central proposal is a realization constraint: when a claim purports to describe, predict, authorize, or change something beyond its own formal expression, the conditions connecting that expression to the relevant system must be specified and supported. A definition determines what is claimed; it does not, by itself, make the claimed relationship obtain outside the definition. Mathematical identities remain exact within their frameworks, but their use as descriptions of physical, computational, informational, or institutional systems introduces additional obligations of interpretation and validation. The principle applies symmetrically to originators, adopters, authorities, observers, and critics. It neither denies the usefulness of abstraction nor requires impossible knowledge of the entire universe; it demands that conclusions be no broader than the grounds actually established.

> *A claim can specify a relationship. It cannot, merely by being stated, supply the conditions that realize that relationship in the system to which the claim refers.*

# 1. The question that comes before “Is it true?”

Suppose someone says, “These two things are the same.” One response is to ask whether the proposition is true or false. But a prior question is often more revealing: same in what respect? The objects might have equal dimensions, share a label, implement the same interface, generate the same decoded output, or follow identical physical trajectories. Those comparisons are not interchangeable. An argument may be locally correct under one comparison while its conclusion silently assumes another.

Likewise, suppose someone writes a command, declares a protocol, or announces a rule. The statement specifies intended behavior, but the existence of the statement does not demonstrate that a processor executed it, that a device implements the protocol, or that the rule binds the people to whom it is addressed. The missing question is not just whether the words are coherent. It is what connects those words to the actual operation or relationship being claimed.

This distinction becomes important precisely because many abstractions work well. In ordinary practice, we suppress their implementation details for efficiency. Problems arise when the suppressed bridge is mistaken for a universal guarantee, or when success in one domain is promoted into a claim about another without justification.

# 2. Three layers: claim, criterion, realization

## 2.1 The claim

A claim is an expression that asserts or proposes something: “x equals y,” “this is a cat,” “this device is compatible,” “this code computes a square,” or “this participant may control that use.” A claim can be syntactically valid without being true. It can also be true by stipulation inside a constructed formal system without yet describing an external system.

## 2.2 The criterion

A criterion states what would count as satisfying the claim. For equality, it identifies the domain, the compared properties, and the comparison relation. For software, it identifies intended input-output behavior and permitted observations. For authorization, it identifies the applicable agreement, law, role, or institutional procedure. Criteria can be exact as specifications even when their physical implementation is variable or imperfect.

## 2.3 The realization

Realization concerns the system alleged to satisfy the criterion. A real device must encode and process relevant signals; an observer must possess information sufficient for recognition; an institution must have applicable relationships and procedures; a copied data structure must actually preserve the edges needed for the asserted operation. To conclude that realization occurred, one also needs an appropriate evidential basis: proof relative to an implementation model, testing, measurement, inspection, operational records, or another warranted method.

Thus there are two bridges to examine: from the claim to its intended criterion, and from that criterion to an actual system. Neither bridge is automatically supplied by the declaration itself. “Mechanism” is useful for causal and operational questions, but it should not be confused with “evidence”: some mechanisms produce a relationship, while measurements and proofs establish grounds for believing that a relationship holds.

> *Claim → specified criterion → established realization. Each transition carries its own conditions; neither is a free inference.*

# 3. Equality is comparison under a stated relation

Ordinary language often hides the comparison relation. Two images may be “the same” because they have the same classification label even though their pixels differ. Two programs may be “equivalent” because they produce the same externally visible results on a defined input set even though their algorithms, timing, or energy consumption differ. Two electrical states may represent the same bit even though their voltages differ. Once the comparison changes, the equivalence claim may no longer follow.

A convenient notation is x ~C y, meaning that x and y are equivalent according to criterion C. If C is a classifier, one possible definition is x ~C y if and only if C(x) = C(y). This relation deliberately groups distinctions that the classifier does not retain. The resulting equivalence is real as a relationship in the model, but it does not prove that the objects are identical under every possible description.

The expression “categorically equal” can serve as an informal prompt: “Equal according to which category or criterion?” For technical writing, “criterion-relative equivalence” or “equivalence under C” is less ambiguous, since “categorical” has other meanings in philosophy and mathematics. The underlying question is useful regardless of terminology.

## 3.1 Mathematical identity is not an exemption

Within standard mathematical semantics, the symbol “=” expresses identity of elements in an identified domain; it is finer than many other equivalence relations. For example, 2 and 5 are different integers but equivalent modulo 3. That distinction is mathematically precise. It does not entitle a speaker to treat equality of two numerical outputs as identity of the physical events producing them. The mathematical framework fixes what “=” means in that context; applying the result to a different domain requires a relevant mapping and justification.

Nor does making a comparison criterion explicit render every conclusion arbitrary. Once a domain, interpretation, axioms, and rules are fixed, they constrain what can legitimately be inferred. The objection is not to definition or abstraction. It is to extending what follows from one definition into an unestablished claim about another system.

# 4. Digital bits show how categories are physically realized

Consider a simplified digital input. The device specification may designate voltages at or below one limit as valid LOW, voltages at or above another as valid HIGH, and an intermediate interval in which the logic level is not guaranteed. The physical input does not consist of a pure mathematical zero or one. It consists of electrical states with variation, noise, device tolerances, environmental dependencies, and possible faults. A circuit and a convention connect those states to logical categories.

Two different voltages may both count as logical zero. That classification is many-to-one: it preserves the distinction needed for a specified operation while disregarding other physical differences. This is a categorical abstraction rather than necessarily a numerical approximation of the voltage to the number zero. Measurements and switching thresholds can have uncertainty, but numerical approximation, measurement uncertainty, categorical classification, and physical variability should not be collapsed into a single concept.

The logical rule can be precise while the physical apparatus realizing it is fallible. Conversely, the fact that two physical executions differ does not establish that their decoded numerical outputs differ. Saying that a computation is “exact” can legitimately mean that, under the specified integer semantics and correct-operation assumptions, the returned integer equals the mathematical result without numerical rounding. It does not mean that the entire electrical trajectory is a perfect copy of an ideal mathematical operation.

> *Exactness of a specified result is not physical identity of the process that realizes it; physical difference of processes is not proof of inequality of their specified results.*

# 5. Code is not execution

The source expression “result = 2 \* 2” has an intended meaning in a programming language. But written source does not demonstrate that any machine has executed it. An interpreter or compiler, runtime environment, instruction set, hardware, inputs, and execution conditions connect a program representation to observable behavior. The details of that connection matter to claims about what actually happened.

Even a successful compilation establishes less than completed physical execution. A compiler might optimize the multiplication into a constant assignment; the processor may never execute a multiply instruction. An execution record can show that a particular run produced 4, but that observation alone cannot establish correctness for every possible input of a more general squaring routine. Verification can prove a program correct relative to a formal specification and assumptions about its implementation model; it is not a demonstration that hardware is invulnerable to every fault.

There are exact algorithms for integers and rationals over their supported domains. This is not refuted by the finite precision of measuring voltages. It is equally true that a finite physical computer cannot store arbitrary real numbers with unbounded precision or guarantee unbounded resources. The claim must specify which domain and which notion of correctness is meant. “Computes squares exactly” is defensible for an appropriately implemented arbitrary-precision integer algorithm subject to resources; it is not a claim of exact physical reproduction of an unbounded mathematical universe.

## 5.1 Testing, proof, and execution establish different things

| **What is available**  | **What it can establish—and what it does not automatically establish**                           |
|------------------------|--------------------------------------------------------------------------------------------------|
| Source code            | An expressed procedure under specified language semantics; not evidence that it ran.             |
| Successful compilation | A translated artifact under assumptions about the toolchain; not proof of execution.             |
| A passing test         | Observed behavior for the tested conditions; not universal correctness.                          |
| A formal proof         | A conclusion under axioms, specification, model, and proof assumptions; not fault-free hardware. |
| Execution evidence     | That some physical or operational events occurred; not automatically all intended properties.    |

The point is not to demand every one of these methods for every trivial statement. The point is to avoid silently treating one form of support as if it supplied all the others.

# 6. Copies, mappings, and classifiers do not inherit every relation

## 6.1 A copied node is not a copied network

A data structure can store a node with an identifier, a label, and attributes. Copying that node need not reproduce the references, subscriptions, permissions, owners, or external services on which its behavior depends. A copy of an edge description does not necessarily create the external relationship it describes. In a purely abstract graph, by contrast, adding an edge creates an edge within that graph by definition. The apparent contradiction disappears when we distinguish edges in a model from relations in the system modeled.

If a copying operation is expressly defined and implemented to preserve certain relationships, those relationships can be preserved. But that is an additional property of the operation, not a consequence of the word “copy.” A graph homomorphism, isomorphism, or other structure-preserving map imposes specific preservation requirements. Naming a map does not demonstrate that an arbitrary physical or computational transformation satisfies those requirements.

## 6.2 A shared label is not a shared representation

Suppose an image classifier outputs “cat.” That result establishes only what the output and its supporting validation establish: a category assignment under the system’s classification procedure. It does not by itself establish that the classifier possesses every association a person might have with cats, such as texture, disposition, color, or cultural meaning. Nor does the absence of explicit labels prove that those distinctions are absent internally; models can encode latent features not represented in the final output. The valid conclusion tracks what the representation reveals and what examination of the model supports.

## 6.3 Perspective is not transferable by declaration

Seeing a book from the front may establish the appearance of its front face from one position. It does not establish what another observer sees from behind it. One may reconstruct the other view using additional information, but the first observation alone does not contain the missing perspective. Similarly, sharing a descriptive word does not grant the same sensory access, knowledge, or capabilities to every participant.

# 7. Application: the symmetry of realized participation

Representations circulate between people and institutions. Someone creates a term, interface, practice, or standard; others learn, implement, adapt, or refuse it. The original paper on the Symmetry of Realized Participation emphasizes that no role—originator, adopter, maintainer, regulator, or observer—can create every required relationship through declaration alone. The present analysis supplies a more general explanation: claims about recognition, control, and continuation must cross the same gap between representation and realization.

An originator may introduce a convention, but that act does not itself install the relevant knowledge or obligations in everyone else. An adopter may learn the convention, but learning does not automatically confer copyright permission, access to protected infrastructure, or authority over others. When many participants independently maintain a practice, the originator’s withdrawal does not by itself erase their knowledge or implementations. Conversely, independently learned knowledge does not by itself settle outstanding contractual or legal restrictions.

This is a symmetry of constraints, not of positions or outcomes. Different participants can have genuinely different rights, powers, duties, and dependencies. Those differences require their own applicable grounds. A right is not invalid merely because it is institutional rather than physically coercive; institutional norms are among the real relationships that can support a claim. Nor does a declaration cease to matter: in an authorized procedure, declaring can itself be an effective action because an operative system connects that act to its consequence.

> *Neither creating a representation nor adopting it grants universal control. Each asserted capability, obligation, restriction, or effect depends on the relationships that actually support it.*

# 8. Mechanism, measurement, and evidence must be kept distinct

It is tempting to say, “Every equality needs a mechanism that implements it.” This captures the practical concern but overstates it if applied without distinction. A mechanism may produce synchronization between two clocks; a measuring procedure may discover that two independent objects have equal lengths; and a formal derivation may establish equality inside a mathematical system without bringing a new physical equality into existence. These cases require different accounts.

The broader requirement is correspondence support. If a proposition purports to describe reality, its application must be grounded by appropriate evidence, operational criteria, or validated mechanisms. What counts as appropriate depends on the claim. To establish that a particular instruction executed, inspect an execution trace or another reliable observation of the run. To establish that a compiler preserves language semantics, use a suitable correctness argument. To establish that a person possesses a legal entitlement, investigate the governing sources and facts. No single evidential procedure fits every domain.

Proofs, observations, and instruments themselves rely on assumptions and interpretation. This need not trigger a requirement to copy the entire universe and replay every event. Scientific and engineering claims are ordinarily conditional: they identify relevant variables, acceptable tolerances, causal models, and limits of inference. If a challenged conclusion requires a previously ignored dependency, that dependency must be investigated. If it does not, demanding it may add no information to the specific question at issue.

The absence of absolute certainty is not a license to treat all claims as equally unsupported. Nor does reproducible success justify every possible extrapolation. Warrant is neither magical certainty nor mere arbitrary assertion; it is support adequate to an identified claim and scope.

# 9. A practical test for claims of correspondence

When someone says that two systems are equal, that an implementation fulfills a specification, or that a declaration has an effect, apply the following sequence. The purpose is diagnostic: it locates the exact step where a valid observation or definition is being promoted into a broader, unsupported conclusion.

- Fix the claim. State exactly which property, behavior, right, or outcome is alleged; avoid switching meanings during the analysis.

- Identify the domain and comparison criterion. Ask “equal in what respect?” and specify the relevant inputs, outputs, observers, conditions, or governing rules.

- Distinguish representation from referent. Identify which elements are symbols, labels, code, models, observations, or descriptions—and which belong to the system supposedly represented.

- Trace the connecting relation. Look for decoders, mappings, algorithms, interfaces, causal paths, access rights, agreements, norms, or other operative relationships.

- Specify the preservation claim. If information or authority moves between contexts, state which properties the transfer allegedly preserves and what it may discard.

- Examine realization and evidence. Determine whether the relationship was implemented, observed, tested, proved under assumptions, or merely asserted.

- Check the scope. Do not infer all inputs from a few tests, physical identity from equal outputs, authorization from capability, or general adoption from one person’s recognition.

- Apply the test symmetrically. Scrutinize the originator, adopter, observer, institution, and critic under the same demand for adequate grounds.

The test can terminate when the claim is sufficiently established for its actual purpose. It is not a requirement to demonstrate every microscopic event or every philosophical foundation before making ordinary, bounded statements.

# 10. What the framework does—and does not—claim

The framework is not a new proof that mathematical equality is impossible, not a theorem that every computation is numerically approximate, and not an assertion that objective correspondence can never be established. Those conclusions do not follow. An exact equality within a mathematical model can be valid; a digital circuit can reliably implement a discrete abstraction; a compiler can preserve specified semantics; a participant can hold enforceable rights. The question is which claim each result actually supports.

Nor is the framework a replacement for logic, scientific measurement, formal semantics, epistemology, or legal analysis. It organizes familiar distinctions—identity versus equivalence, specification versus implementation, map versus territory, capability versus authorization, observation versus generalization—into a common test. Its contribution is methodological: it makes the bridges explicit and demands that the same discipline apply across representations and participants.

This also explains why a simple warning not to “claim more than the grounds support” can expand into a long discussion. Much of the complexity lies in naming the grounds and identifying the precise crossing between domains. The framework should not multiply principles whenever one careful distinction will do. Its strength lies in a repeatable question rather than in an ever-growing vocabulary.

# 11. Final statement: the realization constraint

> *A statement, definition, classification, equivalence, instruction, or declaration establishes no more about a system than the applicable interpretation, realization conditions, and evidence support. Where a claim reaches from a representation into physical, computational, informational, social, or institutional reality, the relationship connecting the two must be identified and appropriately established. No participant, role, or formalism receives an exemption merely by naming the relationship.*

The compact form is: define what is being claimed; identify what would count as satisfying it; establish the relevant correspondence; and infer no more than that correspondence preserves.

This is why the decisive challenge to an alleged equality or effect is often not “Can you define it?” but “What actually makes it true of the system you are talking about?”
