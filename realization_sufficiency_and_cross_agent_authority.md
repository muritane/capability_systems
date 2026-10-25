# Realization, Sufficiency, and Authority Across Independent Criteria

## A standalone extension of the realization constraint

### Abstract

Representations can name relationships, encode instructions, classify states, specify outcomes, and express standards of success. Their existence does not, by itself, establish that the corresponding relationships obtain in a target system. This is the **realization constraint**. Its implications extend beyond the familiar distinction between specification and execution. They concern the recognition of symbols, partial and multidimensional success, the transfer of conclusions between evaluation criteria, and the attempted transfer of normative authority between independent agents.

This paper develops four linked distinctions: **representation is not recognition; recognition is not successful action; realized performance is not automatically sufficient for a given claim; and sufficiency under one criterion does not automatically confer authority over other criteria or their holders**. It argues that operational adequacy is generally indexed to the relation claimed, the relevant system and environment, the conditions and time horizon, and the required tolerances. Degrees of realization may be measured in particular cases, but there is no generally warranted scalar that combines every kind of recognition, control, evidential support, and normative legitimacy. The appropriate representation may instead be a profile of partly independent capabilities and constraints.

For interacting agents, a further consequence follows: the existence, consistency, adoption, or successful use of one agent's evaluative criterion does not alone make that criterion binding on another agent. This is a **non-derivability of automatic cross-agent authority**, not a proof that no objective truths, better criteria, justified institutions, or binding obligations can exist. Such conclusions require separate grounds. The same rule applies symmetrically to every participant.

The resulting framework is a discipline of **bounded attribution**: identify what relation actually holds, how it is realized or supported, what it suffices for, and which additional bridges are needed before making a stronger claim. It does not supply a universal moral ranking, erase genuine differences in power, or convert every dispute into a numerical optimization problem.

> **Central principle:** No representation, realized outcome, evaluation criterion, or participant's perspective gains authority over a different relationship or domain merely by being named, realized, or preferred. Each additional attribution requires the specific grounds that support it.

---

## 1. The starting point: the realization constraint

The realization constraint begins with a modest separation:

> A represented operational relation has no operational force by representation alone. The relation requires sufficiently supporting structure in the system or environment where it is alleged to hold.

A written command is not yet an executed transition. An interface label is not yet a reliable capability. A policy text is not automatically its own enforcement. A goal is not automatically reachable. A statement that two things are equivalent under one comparison is not proof that they are interchangeable under every other comparison.

The earlier formulation focused on the physical, computational, causal, and institutional dependencies of operational commitments. A complementary formulation makes two bridges explicit:

```text
claim or representation
         ↓  interpretation / specification
criterion for the intended relation
         ↓  realization and/or evidential support
relationship alleged to hold in a target system
```

These are distinct bridges. A mechanism may *make* an outcome occur; evidence, measurement, or proof may *justify believing* a relationship holds. Some true relations were not deliberately produced by a special mechanism. The framework therefore must not equate **realization**, **causation**, **verification**, and **truth**.

Its methodological core is: **infer no more than the established connection preserves**.

The new question is what happens when the connection is partial, when the relevant criteria differ, or when several independent agents claim the right to choose which criteria govern.

---

## 2. Physical patterns are not automatically recognized symbols

Imagine the physical marks `SOUTH` printed on a stone. The marks have shape, reflect light, can be scratched away, and may affect other objects through ordinary physical interactions. But they are not an instruction *for a rock* simply because they happen to resemble familiar characters to a human reader.

To function as a word for a particular system, the pattern must enter a relevant recognition and interpretation relation. Such a relation might involve perception, discrimination of characters, parsing, a learned language convention, stored associations, social practices, or some functional equivalent. An agent may then employ orientation, actuation, and feedback to respond to the interpreted instruction.

It is useful to distinguish at least five questions:

1. **Pattern:** Does the physical or informational distinction exist?
2. **Detection and recognition:** Can a particular system discriminate the pattern as a relevant signal or token?
3. **Interpretation:** Does it associate the signal with the intended content, within an applicable convention or model?
4. **Operational coupling:** Can that interpretation influence a mechanism or behavior relevant to the content?
5. **Outcome:** Does the coupled behavior satisfy the intended criterion?

These are analytical distinctions, **not an assertion that every agent contains five sequential modules**. Recognition and action can be distributed, embodied, simultaneous, learned, or otherwise organized. A compass-guided device can travel south without recognizing the English word *south* at all. A human can understand the word perfectly while unable to travel. The relevant implication is neither direction:

\[
\text{recognition} \not\Rightarrow \text{successful action},
\qquad
\text{successful action} \not\Rightarrow \text{linguistic recognition}.
\]

Calling unrecognized patterns *noise* can be useful relative to a receiver or task, but is too strong without qualification. A pattern may be informative under another decoder, interpretable by a future agent, or correlated with physical events even though the current system does not read it as language. **Meaningful-for-a-system** and **physically present** are different attributions.

The dependency form is general: a representation does not compel an arbitrary substrate to respond *as though it understood the representation*.

---

## 3. Partial realization: the case of “go south”

Suppose the instruction is *go south*. Several distinct outcomes are possible:

- A device detects the text but cannot parse it.
- An agent recognizes the phrase yet lacks an orientation reference.
- An agent understands the direction but cannot move.
- An agent moves, but northward.
- An agent moves southeast, thereby making some southerly progress.
- An agent travels sufficiently close to due south for a specified distance.
- An agent satisfies a more demanding requirement of heading, destination, safety, and reliability over time.

These outcomes should not be reduced to the binary *realized/not realized* without first specifying **which property is at issue**.

Walking north may realize the general property *movement*, but not the directional content of *going south*. Walking southeast may satisfy *positive southward displacement*, while failing *maintain a heading of 180° within ±2°*. A sentence that merely says “the instruction was partially followed” conceals the choice of criterion.

Thus there are two different questions:

- **Degree of realization:** How closely does actual behavior match some specified aspect or measure?
- **Sufficiency:** Is that degree enough to satisfy the particular commitment being asserted?

For example, define a task-specific directional alignment score \(\rho_C\) between 0 and 1, where 1 means perfect alignment under the chosen measurement and 0 indicates no alignment under that metric. A claim may establish a threshold \(\tau_C\):

\[
\operatorname{Sufficient}(S,C,V,H)
\iff \rho_C(S,V,H)\geq \tau_C.
\]

Here \(S\) is a system, \(C\) a criterion, \(V\) the validity conditions, and \(H\) the relevant time or evaluation horizon. This is a **model for cases in which a scalar score has been justified**, not a universal equation governing all realization.

In other cases, the outcome must satisfy several separate requirements, or a hard constraint may be non-compensable. A vehicle that arrives at the correct location but causes unacceptable harm has not necessarily met the commitment merely because it scores highly on route accuracy.

The central refinement is:

> **Nonzero realization of an aspect of a task is not automatically sufficient realization of the task as specified. Conversely, imperfection in an irrelevant aspect need not defeat a bounded claim.**

---

## 4. Multidimensional realization, without the fiction of one universal score

The phrase **criterion-relative, multidimensional realization sufficiency** captures a useful structure, but it risks making a single phrase do too much work. The concepts are better kept analytically separate.

A particular system might be described by a capability profile:

\[
\mathbf r(S) =
\left(r_{\mathrm{recognition}},
      r_{\mathrm{interpretation}},
      r_{\mathrm{orientation}},
      r_{\mathrm{control}},
      r_{\mathrm{outcome}},
      r_{\mathrm{reliability}}\right).
\]

This notation is **illustrative**. The components are chosen for a task; they need not be independently measurable, commensurable, or arranged in a simple linear order. For a legal entitlement, evidential records, applicable rules, consent, jurisdiction, and enforcement may matter instead. For mathematical equivalence, a definition and a proof may matter while physical actuation does not.

An evaluative rule could be modeled as

\[
E_C(\mathbf r,V,H)\in\{\text{pass},\text{fail},\text{undetermined}\},
\]

or, where defensible, by a graded or probabilistic output. Multiple profiles may be **incomparable**: one system recognizes instructions better, another acts more reliably, and the relevant criterion does not specify how those advantages trade off.

It is important not to smuggle normativity into a measurement function. The choice of dimensions, aggregation method, threshold, exceptions, and distribution of risks may itself be contested.

**Conclusion:** The more general construct is not a universal realization number. It is a **claim-indexed sufficiency relation** on actual conditions and capabilities, possibly multidimensional, partial, probabilistic, or context-dependent.

---

## 5. From realization to sufficiency—and from sufficiency to authority

Four inferential transitions must be kept distinct:

```text
A relationship is REPRESENTED.
    ⇏ It is REALIZED in the target system.

A relationship is REALIZED in some respect.
    ⇏ It is SUFFICIENT for the asserted commitment.

A commitment is SUFFICIENTLY met under criterion C₁.
    ⇏ It is SUFFICIENT under a different criterion C₂.

A result is SUFFICIENT under someone's criterion C.
    ⇏ C has AUTHORITY over other agents or domains.
```

The symbol \(\not\Rightarrow\) means **does not follow from that premise alone**, not that the conclusion must be false.

This family of invalid promotions is broader than a failure of physical implementation. A model can predict an outcome accurately without giving an agent control over it. A system can reliably meet a technical target without establishing that deployment is acceptable. A person can cause a benefit without thereby acquiring an enforceable right to command its beneficiaries.

A compact name for the shared mistake is **unjustified promotion**: extending the scope, meaning, consequence, or authority of a supported relationship beyond what its grounds establish.

The correction is not perpetual skepticism. It is to identify the missing **bridge condition** and determine whether it holds.

---

## 6. Causal contribution does not generate authority by itself

Consider the argument:

> I succeeded because of X; therefore I now possess the right to decide Y.

At least two different bridges have been assumed:

\[
X\text{ preceded or accompanied success}
\not\Rightarrow X\text{ caused success}
\]

and

\[
X\text{ caused success}
\not\Rightarrow \text{the actor is authorized to decide }Y.
\]

Even if the causal contribution is firmly established, an authorization claim needs its own grounds. Relevant considerations might include ownership, contractual terms, legitimate delegation, applicable law, consent, institutional procedure, or a defended normative principle. Their presence must be assessed rather than presumed.

For example, introducing a useful convention does not automatically install that convention in everyone else or create unlimited jurisdiction over independent adopters. Conversely, adoption of a convention does not automatically erase intellectual-property restrictions, binding agreements, or other valid obligations. **Both originator and adopter are subject to the same constraint against self-conferred universal authority.**

The same analysis applies to merit, intelligence, efficiency, expertise, achievement, and usefulness. A person may demonstrably possess a capability that others lack, but **descriptive superiority in one dimension does not itself establish normative supremacy in another**.

This does not deny justified rights. It demands that the type and scope of a claimed right be established by appropriate grounds.

---

## 7. Independent agents and the symmetry of criteria

Let agents \(A\) and \(B\) have their own evaluation relations or criteria \(C_A\) and \(C_B\). They may differ in goals, tolerances, risks, values, information, or preferences. Each may act successfully under its own criterion.

From these premises alone, one cannot derive:

\[
C_A \succ C_B
\quad\text{or}\quad
C_B \succ C_A,
\]

where \(\succ\) denotes *greater normative authority over the shared question*. Nor can one derive that the criteria are equally correct, equally valuable, or equally binding. **Lack of an established ranking is not an established tie.**

An especially important distinction is between an agent having **a criterion** and that agent having **jurisdiction to impose it on another**. An agent can prefer a standard, use it internally, and demonstrate that it succeeds under that standard without establishing jurisdiction over anyone else.

The result is a symmetry of **justification requirements**, not necessarily a symmetry of rights, abilities, or outcomes. Two agents need not have equal power or equal evidence. An agreed procedure can validly assign one participant decision authority in a defined setting. An expert can have better evidence about an empirical question. A court may possess applicable institutional jurisdiction. A shared contract may establish obligations. But none of these differences becomes real merely because a participant announces it.

### A limited derivation

Assume only that:

1. \(A\) holds or applies \(C_A\).
2. \(B\) holds or applies \(C_B\).
3. Each criterion may be internally coherent and usable by its holder.
4. No additional relation of delegation, shared commitment, jurisdiction, or superior normative ground has yet been supplied.

Then the authority of \(C_A\) over \(B\) (and the converse) is **not derivable from those premises**. To infer it requires an additional premise specifying a valid cross-agent bridge.

This is a logical limit on what the stated premises establish. It is **not**, by itself, a proof of the stronger thesis that no objectively authoritative moral standard can ever exist. That would be a separate argument in metaethics or political philosophy.

> **Non-automatic authority principle:** Independent adoption or successful realization of a criterion supplies no automatic entitlement to impose that criterion on another agent. Any claimed cross-agent authority requires independent grounds of applicability.

The word *independent* here does not mean metaphysically isolated, invulnerable, or unconstrained. Agents can share resources and causal environments while retaining divergent standards.

---

## 8. Shared reality constrains everyone without selecting everyone's values

Two agents may disagree about how a bridge should be used, whether it should be built, or which risks are acceptable. Nevertheless, bridge loads, material behavior, and resource limits are not made different simply by different preferences.

Thus:

\[
\text{no automatic normative priority}
\not\Rightarrow
\text{no common physical or informational constraints}.
\]

Equally:

\[
\text{common constraints}
\not\Rightarrow
\text{one uniquely mandated evaluation criterion}.
\]

An agent may be wrong about a shared empirical fact. Another may have better evidence. Both can be causally constrained by the same environment. Yet the choice between risk tolerances, competing interests, or permissible uses may still involve distinct normative questions.

This protects the framework from collapsing into crude relativism. **Different perspectives do not make every factual claim equally supported**, and **a shared fact does not automatically settle every normative disagreement**.

---

## 9. Why disputes over evaluation functions recur

Many conflicts occur because participants disagree over one or more separate elements:

| Disagreement | Illustrative question |
|---|---|
| **Referent or facts** | What actually happened? |
| **Criterion** | What would count as success? |
| **Dimensions** | Which properties should matter? |
| **Tolerance** | How much deviation or risk is acceptable? |
| **Horizon** | For how long must performance persist? |
| **Distribution** | Whose gains, losses, or exposures count? |
| **Procedure** | Who decides and how are objections handled? |
| **Jurisdiction** | Why would this decision bind another party? |
| **Realizability** | Can the intended outcome actually be brought about? |
| **Desirability** | Should the outcome be brought about at all? |

These questions are related but not interchangeable. A dispute framed as disagreement over a number may in fact concern who was allowed to choose the metric. A system can pass its technical benchmark while failing an ethically important constraint that the benchmark omitted.

The reverse is also possible: parties may agree on criteria yet disagree because evidence is missing, mechanisms fail, or resources are inadequate.

One can mathematically encode many positions as objective functions. But **encoding a dispute as optimization does not create consent, legitimate jurisdiction, commensurability, or an agreed method of aggregation**. Those are additional relationships to be justified or realized.

What persists across domains is not one universal human objective. It is the need to keep separate the existence of a criterion, its satisfaction, and its authority.

---

## 10. Criteria, authority, and the absence of a built-in sovereign evaluator

A criterion does not become universally authoritative merely because it is described as *rational*, *objective*, *optimal*, *natural*, *efficient*, or *universal*. Each label is a claim whose scope and grounds remain open to examination.

This has two-sided consequences:

- There is no valid shortcut from **my criterion is realized or successful** to **you must adopt it**.
- There is also no valid shortcut from **nobody has demonstrated universal authority** to **all criteria must be equally legitimate or no authority can ever be justified**.

The framework therefore rejects **self-certifying authority**, not all authority. It leaves open the possibility of objective answers, reasons that rationally bear on all parties, binding agreements, justified institutional procedures, and legitimate claims against others. It simply requires that the relevant bridge be argued for rather than assumed.

It also distinguishes three forms of power often conflated:

1. **Causal power:** the ability to change what happens.
2. **Institutional or legal authority:** recognized powers and obligations within applicable rules and practices.
3. **Moral justification:** reasons why an act or arrangement ought to be accepted, required, or prohibited.

An actor may exercise force without thereby earning moral authority. Conversely, a valid legal entitlement may remain an entitlement even when imperfectly enforced. The operational efficacy of a norm, its legal validity, and its moral defensibility are not identical questions.

Crucially, declarations can sometimes *perform* acts—such as giving consent or issuing an authorized order—when a recognized practice makes the utterance operative. That does not violate the realization constraint: the supporting convention, authority, and circumstances are the bridge.

---

## 11. A general rule of bounded attribution

The strongest common formulation is neither “all reality is relative” nor “every truth needs a mechanism.” It is:

> **Attribute to a system, relation, agent, or representation no more than is established under the relevant interpretation, realization conditions, evidential grounds, and legitimate scope of application.**

The rule applies to both empirical and normative promotions, with different kinds of support appropriate to each.

Consider the following patterns:

| Established relation | What does not follow automatically |
|---|---|
| A classifier outputs “cat” | It possesses every concept or experience associated with cats |
| A program returns the correct integer | Its physical execution is identical to an abstract operation |
| A simulation succeeds | The deployed system will succeed under different conditions |
| An agent reaches an outcome | The agent understood the instruction that describes the outcome |
| A plan specifies a desirable goal | The goal is reachable or should be pursued |
| Two objects match under criterion \(C\) | They match under a different criterion \(D\) |
| A participant creates a convention | The participant controls every independent adopter |
| An actor contributes to a success | The actor is entitled to govern all subsequent uses |
| A policy is announced | It is enforced, just, or binding everywhere |
| A system meets a local benchmark | It is acceptable to all affected parties |

The pattern is **scope discipline**. A correct conclusion under one mapping or criterion cannot simply be transported into a stronger relationship without identifying what preserves the relevant property.

---

## 12. A more formal schema for the bridges

Let:

- \(R\): a representation or asserted relation;
- \(I\): an interpretation connecting \(R\) to a criterion;
- \(C\): the criterion or commitment being evaluated;
- \(S\): the target system, including relevant external dependencies;
- \(V\): validity conditions;
- \(H\): evaluation horizon;
- \(M_C\): the observations, proof obligations, or performance measures appropriate to \(C\);
- \(T_C\): the specified sufficiency rule for \(C\).

Then the evaluative question is whether the actual system, under the relevant conditions, satisfies the criterion:

\[
\operatorname{Sat}(S,C,V,H;M_C,T_C).
\]

This is a schematic predicate, **not an assertion that every phenomenon admits a quantitative score or the same test**.

For a family of criteria \(\mathcal C\), define a satisfaction profile:

\[
\mathcal P(S,V,H) =
\big\{(C,\operatorname{Sat}(S,C,V,H)):C\in\mathcal C\big\}.
\]

A profile does not automatically come with a total ranking. Two systems can satisfy different subsets of criteria, and agents can legitimately contest how those subsets should be compared.

To infer that satisfaction of \(C_1\) establishes satisfaction of \(C_2\), one needs a justified implication or preservation condition, such as:

\[
\forall S\in\mathcal D:\quad
\operatorname{Sat}(S,C_1)\Rightarrow\operatorname{Sat}(S,C_2),
\]

for a **specified domain** \(\mathcal D\) and the assumptions under which the implication holds. Without such a result, the transfer is unsupported.

To infer that an agent's criterion binds another agent, one needs an additional authority or applicability relation, here written schematically as

\[
\operatorname{Authority}(A,C_A,B,\mathcal K),
\]

where \(\mathcal K\) represents the governing context and relevant grounds. Possessing \(C_A\), or satisfying it, does **not** by itself establish this predicate. The framework does not define a universal moral test for \(\operatorname{Authority}\); doing so would require substantive normative premises.

This keeps two different bridging problems distinct:

**Property preservation:** Does a claim verified under one criterion warrant a claim under another?

**Normative applicability:** Why, if at all, does an evaluator's criterion govern somebody else?

A proof of the first is not automatically a proof of the second.

---

## 13. Three thought experiments

### 13.1 The sign, the stone, and the robot

A sign reads `SOUTH`. The stone beneath the sign interacts with the paint as matter, without reading it as a direction. A robot may recognize the text but lack a compass. Another robot may move south through navigation routines without reading the sign. A third may read and interpret the sign but drift southeast because of sensor error.

The lesson is not that only full semantic understanding counts. It is that **recognition, interpretation, causal coupling, and criterion satisfaction are separable**. Each additional claim needs corresponding grounds.

### 13.2 The inventor and the adopters

An originator devises a highly useful convention. Other agents independently learn and reproduce it. The originator's contribution may be causally decisive, and the adopters' continuing use may be real. Neither fact alone determines whether the originator can prohibit further use, whether adopters have permissions, or which restrictions govern. Applicable agreements, rights, institutions, and circumstances must be examined.

The lesson is **symmetrical non-self-authorization**, not the claim that originators and adopters always have identical rights.

### 13.3 The successful system nobody agrees to deploy

An autonomous service meets a benchmark for task completion. An engineer treats this as sufficient. A safety reviewer requires a stricter tail-risk guarantee. A community representative questions the distribution of risk and the procedure authorizing deployment.

All three may agree on the observed performance. They still contest different dimensions, thresholds, and the standing of evaluators. A better benchmark can address some empirical disputes but cannot, by itself, decide who is entitled to choose what counts as an acceptable risk.

The lesson is **evaluation under a criterion does not justify the criterion's jurisdiction**.

---

## 14. Testing the framework rather than merely redescribing everything

An overgeneralized framework can describe every success as adequately realized and every failure as inadequately realized. That would risk circularity. Useful application requires specifying in advance what the framework predicts or distinguishes.

A practical test proceeds as follows:

1. **Fix the target claim.** Is it about classification, performance, authorization, truth, or something else?
2. **Identify the criterion and scope.** Specify relevant properties, conditions, affected parties, tolerances, and horizon.
3. **Locate the realization path.** What decoders, mechanisms, mappings, practices, institutions, or evidence support the relationship?
4. **Separate dimensions.** Distinguish recognition from action, action from outcome, and outcome from justified reliance.
5. **Identify partial success.** Which requirements are actually met, and which remain absent or unmeasured?
6. **Check sufficiency.** Does the actual profile meet the stated commitment, without compensating away hard constraints?
7. **Check transfer.** If the conclusion moves between criteria, models, systems, or agents, what preserves its validity?
8. **Check claimed authority.** Who is said to be bound, and what independent grounds establish that applicability?
9. **Consider countercases.** Can the symbol remain unchanged while the mechanism fails? Can the outcome occur without linguistic recognition? Can two agents agree on facts but reject each other's thresholds?
10. **Bound the conclusion.** State what is established, uncertain, or outside the argument.

This procedure can yield discriminating observations. Holding text fixed while changing the decoder tests recognition. Holding an interface fixed while severing a dependency tests operational realization. Holding performance fixed while altering a criterion tests sufficiency. Holding both agents' independent criteria fixed while varying consent or institutional relationships tests the existence of an applicable authority bridge.

Such tests do not settle all moral controversies experimentally. They clarify **which part of an argument is empirical, conceptual, institutional, or normative**.

---

## 15. What follows—and what does not

### Supported conclusions

- A representation is not automatically a recognized or operative relation for every system.
- Recognition, interpretation, action, and outcome can be partly independent.
- Realization can be graded in specific respects, but sufficiency is indexed to a claim and its conditions.
- No single scalar score is warranted for all forms of realization or evaluation.
- Realization under one criterion does not automatically establish realization under another.
- Successful realization of a participant's criterion does not automatically confer authority over another participant.
- These restrictions apply symmetrically even when participants' actual positions differ.
- Shared causal constraints can bind independently evaluating agents without automatically deciding their normative rankings.
- Every stronger attribution needs the grounds appropriate to that stronger claim.

### Stronger conclusions not established by the framework alone

- That no objective moral truths, universal reasons, or justified institutions can exist.
- That every criterion is equally good, equally rational, or equally authoritative.
- That every disagreement is fundamentally about evaluation functions.
- That the absence of demonstrated authority proves the impossibility of authority.
- That all relationships require mechanisms which deliberately produce them.
- That all partial success can be compressed into a meaningful percentage.
- That identifying the realization constraint yields a new empirical law rather than a reusable methodological discipline.

Those stronger positions would require additional argument and, when relevant, empirical evidence.

---

## 16. The persistent structure—and its limit

Why does this pattern appear in mathematics, computation, recognition, control, law, politics, and human disagreement?

In each setting, an argument can move from **a relation established in one respect** to **a broader claim about a different respect**. Sometimes the move is warranted by a proof, a validated mapping, a realized mechanism, a recognized rule, or a sound normative argument. Sometimes the speaker silently promotes the first relation into the second without supplying the bridge.

The recurrent structure is therefore not necessarily a newly discovered law of the universe. It is a persistent **constraint on legitimate attribution and inference** whenever an argument crosses between levels, criteria, systems, or participants.

The operational realization constraint contributes the question *what supports the claimed effect?* The correspondence framework contributes *what preserves the claimed relation when it is applied to its referent?* Graded sufficiency contributes *how much and which aspects are enough for this commitment?* Cross-agent symmetry contributes *why would one participant's evaluative rule bind anyone else?*

The common demand is that **no level, formalism, successful result, or participant receives an exemption from establishing the relation it claims**.

The important limit is that this discipline does not generate substantive values from nowhere. It cannot uniquely rank incompatible moral aims without additional premises, and it cannot transform a disagreement over legitimate jurisdiction into a solved optimization problem simply by describing the dispute in mathematical language.

That limitation is not a failure of the framework. It is an example of the framework applying to itself.

---

## 17. Final formulation

> **Generalized realization and attribution constraint**
>
> A representation can express a distinction, criterion, intention, rule, or relationship, but it cannot by that expression alone establish recognition, operation, success, sufficiency, or authority in another system. Recognition requires appropriate interpretive organization; operational effects require supporting causal or institutional relations; sufficiency requires satisfaction of a specified claim under relevant conditions; and transfer between criteria or participants requires grounds appropriate to that transfer. These obligations apply symmetrically, without presuming that all criteria, rights, capabilities, or outcomes are equal.

A compact version is:

```text
What is represented?                  ≠ What is recognized?
What is recognized?                   ≠ What can be done?
What can be done?                     ≠ What actually happens?
What happens?                        ≠ What is sufficient?
What is sufficient under criterion A? ≠ What is sufficient under B?
What works for A?                     ≠ What A may impose on B?
```

Every `≠` here is a warning against **automatic inference**, not a claim that the relations can never coincide. Each connection can be valid when supported.

The final practical rule is simple:

> **Do not promote an established relation beyond what establishes it. When the claim crosses a boundary, identify and justify the bridge.**

This is the general thread connecting representation, graded realization, evaluation disagreement, realized participation, and the non-automatic authority of independent criteria.

---

## Relationship to the foundational manuscripts

This paper synthesizes and extends two earlier manuscripts:

- **`realization_constraint.md`**, which develops operational accountability, mechanisms, causal reachability, interfaces, validity regions, horizons, infrastructure, delegation, verification, and the recursive persistence of realization requirements.
- **`From_Claim_to_Realization.md`**, which organizes claims, criteria, correspondence, equivalence, evidence, bounded inference, and the symmetry of realized participation.

The developments here are the explicit separation of **recognition and operational response**, **multidimensional partial realization and claim-relative sufficiency**, **the non-derivability of automatic cross-agent normative authority**, and **unjustified promotion as the common inferential failure**. They are proposed clarifications and deductions from the shared method, not claims that the foundational distinctions have no prior history in philosophy, systems theory, engineering, or social inquiry.
