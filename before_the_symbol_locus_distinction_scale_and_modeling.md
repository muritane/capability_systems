# Before the Symbol: Locus, Distinction, Scale, and the Minimum Commitments of Modeling

## Abstract

A formal model is often presented as though its primitive symbols are already available.

One writes:

\[
x,
y,
+,
=,
0,
1
\]

and then asks what the symbols mean or what rules govern them.

But a prior question is usually left implicit:

> What must already be operative for anything to appear as a symbol, state, object, node, number, or model element at all?

Before `x` can function as a character, some bounded agent or process must distinguish a selected configuration from what is not selected, segment it at some resolution, recognize it as repeatable, assign or recover an address, and preserve enough context for later occurrences and relations to remain interpretable.

The first modeling act is therefore not necessarily naming.

It is a cut.

The cut does not need to reveal a metaphysically final boundary. It establishes a locally sufficient distinction between what is treated as focal and what is left as background, environment, remainder, or unresolved context.

From that cut, further capabilities become possible:

```text
selection
contrast
segmentation
resolution
identity
addressability
relation
operation
evaluation
continuity
maintenance
```

These capabilities do not all appear at once, and not every model needs every one of them. A static classification may require no explicit transition system. An algebra requires operations and equations. A dynamical model additionally requires state, change, and identity across change. An empirical model requires evidence and an adequacy relation to some represented realization.

This document develops a layered account of those commitments.

It argues that a locus is not best understood as the smallest constituent of reality. It is the first reusable modeling organization in which a distinction becomes bounded, addressable, interpretable, and available for constrained attribution.

On this view, a maintained locus of constrained realization is not necessarily a thing that is itself repaired or physically preserved. What is maintained may instead be the operative identity, address, and interpretive organization through which changing realizations can continue to be counted, compared, related, and acted upon.

The result is a possible coherence audit for models: any model can be examined by asking which cuts, scales, identities, addresses, operations, evaluation rules, and continuity assumptions it silently relies upon.

---

## 1. The Question Before the Symbol

Consider the inscription:

```text
x y
```

It is tempting to begin by saying that there are two characters, `x` and `y`.

But that description is already highly structured.

At the level of a display, the inscription may initially be only a distribution of:

```text
light and dark pixels
strokes and gaps
foreground and background
ink and paper
activated and inactive cells
```

To call part of that distribution `x` requires several prior operations.

Someone or something must already be able to:

```text
select a region
separate selected from nonselected variation
choose a scale
segment the region
recognize a repeatable configuration
assign or recover an identity
address the configuration again
```

The question is therefore not merely:

> What does `x` mean?

It is first:

> Under what conditions can this variation function as one addressable distinction called `x`?

This is the pre-symbolic problem of modeling.

---

## 2. This Is Not a Metaphysics of an Undifferentiated Universe

It is useful to speak of a field before a symbol, but the term `field` must be handled carefully.

The claim is not that reality is intrinsically one undifferentiated totality until a mind divides it.

Nor is the claim that no distinctions exist independently of a modeler.

The weaker and more useful claim is:

> A model does not receive all possible distinctions simultaneously. It operates over some presented or accessible field in which only selected differences become operative for the current modeling process.

Let:

\[
U_C
\]

denote the field available in context \(C\).

This may be:

```text
a pixel array
a stream of sensor values
a page of marks
a memory region
a collection of records
a physical environment
a legal archive
a token sequence
a set of measured variables
```

The field is already context-relative.

It is not all reality.

It is what is currently available for discrimination, interpretation, or action.

---

## 3. The First Cut: Selected and Nonselected

Suppose a selection regime \(\alpha\) acts on the available field:

\[
\alpha_C(U_C)=S.
\]

Then \(S\) is the selected region or variation, while:

\[
U_C\setminus S
\]

is the nonselected remainder relative to that cut.

This produces the first operational distinction:

\[
S
\quad\middle|\quad
U_C\setminus S.
\]

The two sides need not be metaphysically different kinds of thing.

The distinction is functional:

```text
selected / nonselected
foreground / background
focus / remainder
signal / ignored variation
inside the current cut / outside the current cut
```

The same material may reverse roles under another question.

A blank region may be background in optical character recognition and foreground in an analysis of spacing.

A space between `x` and `y` may be ignored in one tokenization and treated as a meaningful delimiter in another.

The cut creates an asymmetry of attention.

It says, in effect:

> Preserve this difference for the current operation.

---

## 4. Focus and Complement Are Not Yet Two Objects

After the first cut, it is still too early to claim that two objects exist.

The cut establishes a selected side and a complement.

It does not yet establish:

```text
stable identity
internal segmentation
countable units
symbol types
semantic denotation
```

The expression:

\[
S
\quad\middle|\quad
U_C\setminus S
\]

means only that some variation has become operationally focal.

The complement is defined relative to that selection. It may contain many unresolved structures, or no structures that matter for the present model.

Therefore the first distinction is not necessarily:

```text
object A versus object B
```

It is more minimally:

```text
this selected variation versus what is not currently selected as this
```

This distinction is already bounded, but only with respect to the current field and selection regime.

---

## 5. Marks Are Not Yet Characters

A character is not merely a visible shape.

The same pixels may be interpreted as:

```text
a lowercase x
a multiplication sign
two crossing strokes
a decorative mark
noise
part of a larger glyph
```

A mark becomes a character only when it participates in a maintained recognition and interpretation regime.

Let:

\[
\operatorname{Recognizes}_C(m,\tau)
\]

mean that mark occurrence \(m\) is recognized in context \(C\) as an instance of symbol type \(\tau\).

Then:

\[
\operatorname{Recognizes}_C(m_x,\texttt{x})
\]

is not determined by the pixels alone.

It depends on such things as:

```text
resolution
orientation
font conventions
segmentation
alphabet
reading direction
noise tolerance
current task
```

The physical or digital carrier constrains interpretation, but does not carry one interpretation independently of context.

---

## 6. Segmentation Precedes Counting

Return to:

```text
x y
```

Possible segmentations include:

```text
[x y]
[x][ y]
[x ][y]
[x][ ][y]
[pixel_1][pixel_2]...[pixel_n]
[stroke_1][stroke_2]...[stroke_k]
```

The inscription does not announce its uniquely correct segmentation at every analytical level.

A segmentation operator may be written:

\[
\sigma_{C,\rho}(S)
=
(s_1,\ldots,s_n),
\]

where:

```text
C = interpretation context
rho = selected resolution or granularity
S = selected field region
s_i = resulting segments
```

Only after segmentation can the model count candidate units.

Thus counting presupposes at least:

```text
a field
a selection
a segmentation regime
a criterion of unit identity
```

The number of elements is therefore not simply waiting in the raw carrier independently of all unit criteria.

It is constrained by the carrier, but made countable through a selected decomposition.

---

## 7. Scale Is Not an Optional Detail

Every segmentation operates at some scale.

At one scale:

```text
x
```

is one character.

At another scale, it is:

```text
two crossing strokes
```

At another:

```text
a set of dark pixels
```

At another:

```text
subpixel activations
```

At another:

```text
electrical states in display hardware
```

None of these descriptions needs to be false.

They answer different questions at different resolutions.

Let:

\[
\rho
\]

denote a resolution regime.

Then identity and segmentation are indexed by \(\rho\):

\[
\operatorname{Same}_{C,\rho}(a,b),
\]

\[
\sigma_{C,\rho}(S).
\]

Without a sufficiently specified resolution, it may remain unclear whether something is:

```text
one symbol
several symbols
part of a symbol
a compound expression
a carrier containing many lower-level events
```

Scale is therefore not merely a later measurement parameter.

It participates in constituting the modeled units.

---

## 8. Boundedness and Resolution

A usable distinction must be bounded enough to be addressed.

But `bounded` does not necessarily mean:

```text
small
closed
materially isolated
perfectly known
permanently fixed
```

It means that the model has selected a locally sufficient difference between what is retained as part of the unit and what is treated as external, unresolved, delegated, or irrelevant for the present purpose.

A character is bounded because it does not include the entire display.

A variable is bounded because it occupies a selected role in an expression.

A state is bounded because it retains selected variables rather than all properties of reality.

A context window is bounded because it preserves only a finite region of available history.

Resolution and boundedness are therefore related:

- resolution determines which variations can count as distinct;
- boundedness determines which of those variations are retained together as one addressable unit.

Neither requires a final physical boundary.

Both require a declared or recoverable analytical cut.

---

## 9. Distinction Does Not Yet Guarantee Identity

A distinction marks a difference.

Identity allows a difference to be treated as the same difference again.

These are not identical capabilities.

Suppose two mark occurrences appear:

```text
x ... x
```

To treat them as occurrences of the same character type, the model requires an equivalence criterion:

\[
m_1 \equiv_{C,\rho} m_2.
\]

The marks need not be pixel-identical.

They may differ in:

```text
font
size
position
antialiasing
medium
handwriting
```

Identity therefore does not mean complete sameness.

It means sameness under a selected criterion.

This gives at least three levels:

```text
mark occurrence
symbol type
possible denotation
```

For example:

```text
this rendered x       = mark occurrence
x                     = symbol type
some variable value   = possible denotation
```

Confusing these levels produces many apparent paradoxes.

---

## 10. Addressability

Identity becomes operationally useful when the model can refer to the selected unit again.

This is addressability.

An address may be:

```text
a spatial coordinate
a token position
a variable name
a database key
a memory address
a legal identifier
a graph-node identifier
a path
a role
a descriptive relation
```

Let:

\[
a_C(\ell)
\]

be an address for locus \(\ell\) in context \(C\).

Addressability does not require that the underlying realization remain materially unchanged.

A database record may change values while retaining its key.

A person may change location and physical state while retaining a legal identity.

A variable may receive different values while remaining the same variable.

A state holder may change state while preserving the address under which those changes are attributed.

Thus addressability enables variation to be organized around a maintained point of reference.

---

## 11. A First Definition of Locus

A locus can now be introduced without treating it as a metaphysical atom.

> A locus is a bounded and addressable modeling organization produced by a selected cut, at a selected resolution, under an identity and interpretation regime.

A minimal representation may be written:

\[
\ell
=
(S,\rho,B,I,a,C),
\]

where:

```text
S = selected variation or organization
rho = operative resolution
B = boundary or cut relation
I = identity criterion
a = address or reference scheme
C = sufficient interpretation context
```

This is not yet a full dynamical or realization model.

It is the minimum carrier required for later attribution.

Once a locus exists, a model can attribute:

```text
state
relations
requirements
provisions
operations
evidence
transformations
```

to something that remains referentially available.

---

## 12. Relation

With at least two addressable loci, the model can introduce a relation.

Let:

\[
R\subseteq L_1\times L_2.
\]

Then:

\[
R(\ell_1,\ell_2)
\]

states that the two loci occupy specified roles in relation \(R\).

However, two written symbols do not by themselves determine a semantic relation.

The inscription:

```text
x y
```

may indicate:

```text
two adjacent characters
a product under omitted multiplication
a pair
a command and argument
a name with a separator
one larger token
```

A relation therefore requires more than visible coexistence.

It requires a rule that assigns roles to selected units.

This introduces typing or positional interpretation:

\[
\operatorname{Role}_C(\ell_i,R)=r_i.
\]

---

## 13. Operation

An operation is a relation with a specified mode of application and result.

A binary operation may be represented as:

\[
\oplus:A\times B\rightharpoonup D.
\]

The partial arrow is important.

Not every pair of elements needs to admit the operation.

Writing:

\[
x+y
\]

silently invokes at least:

```text
an operator type
two operand roles
an order or symmetry convention
a domain of admissible inputs
a result domain
an evaluation rule, even if the result is not yet computed
```

The expression does not require three distinct denotations.

In:

\[
x+y=z,
\]

`x`, `y`, and `z` are three symbol occurrences or roles, but they may denote fewer than three distinct elements.

For example:

\[
0+0=0.
\]

The same denotation occupies both operand roles and the result role.

The necessary commitment is therefore not `three elements`.

It is:

> two input positions, one result position, and a rule relating them.

---

## 14. Expression, Assertion, and Evaluation

The string:

\[
x+y
\]

is an expression.

The string:

\[
x+y=z
\]

can function as an assertion when `=` is interpreted as an evaluable relation.

This introduces another level:

```text
well-formed expression
interpreted operation
claim about a result
criterion for acceptance or rejection
```

Let:

\[
\operatorname{Eval}_C(e)
\]

map an expression to a result, truth value, status, or evidence-bearing outcome.

Possible evaluations include:

```text
true / false
defined / undefined
valid / invalid
type-correct / type-error
accepted / rejected
reachable / unreachable
supported / unsupported
```

Evaluation is where constraints become explicit.

A formalism is constrained when not every possible inscription or interpretation is admissible.

---

## 15. Equality

Equality is not merely a visible mark.

It is an identity relation governed by rules.

At minimum, an equality relation often commits to:

\[
x=x
\]

and to some treatment of substitution.

But different equalities may use different criteria:

```text
symbolic identity
numerical equality
reference identity
structural equality
observational equivalence
legal identity
functional equivalence
```

Thus:

\[
=_{C,\rho,q}
\]

may be more precise than an unindexed `=`.

The equation:

\[
0+0=0
\]

is meaningful only after the model supplies:

```text
a domain containing 0
an interpretation of +
an interpretation of =
a closure or typing rule
an evaluation procedure or axiom
```

The glyphs alone do not supply these commitments, but using them non-arbitrarily presupposes some maintained context that does.

---

## 16. Inequality and Exclusion

The inscription:

\[
0\neq1
\]

introduces explicit non-identity.

In many programming languages:

```text
!=
```

is one inequality token composed from two glyphs.

In another grammar, `!` and `=` may remain separate tokens with different rules.

This again shows that visible decomposition does not determine formal decomposition.

The statement:

\[
1+1\neq1
\]

requires more than the appearance of `!`.

It requires:

```text
a domain
an addition rule
an equality criterion
a negation or non-equality rule
an evaluation regime
```

The same character sequence may evaluate differently in different structures.

For example, in Boolean algebra:

\[
1\lor1=1.
\]

In ordinary natural-number addition:

\[
1+1=2.
\]

The symbols are constrained, but the constraints are supplied by the interpreted structure.

---

## 17. Natural Numbers and Counting

Numbers illustrate why context-dependence does not imply arbitrariness.

The natural number \(5\) does not intrinsically mean:

```text
five apples
five events
five failures
five people
five dimensions
```

A counting relation connects a selected domain to a numerical structure.

Let \(A\) be a collection whose units have been distinguished under some criterion.

Then:

\[
\operatorname{Count}_{C,\rho,I}(A)=5.
\]

The result depends on:

```text
what is included
what counts as one unit
which occurrences count as the same
which scale is operative
which ordering or pairing procedure is accepted
```

Yet the result is not arbitrary.

The selected realization constrains whether a one-to-one correspondence with five positions can be established.

Thus numbers can maintain portable identities across different counted realizations:

\[
5\mapsto
\{
\text{collections of cardinality }5
\}.
\]

The number is not physically maintained as a thing.

What is maintained is an inferential and referential organization that makes the numerical identity reusable.

---

## 18. Reconsidering Maintenance

The phrase:

> maintained locus of constrained realization

can be misread as saying:

> the represented thing must itself undergo repair, preservation, or homeostatic upkeep.

That is too narrow.

Several distinct forms of maintenance should be separated.

### Referential maintenance

The model preserves a usable identity or address across relevant variation.

\[
\operatorname{Ref}_C(a_t)
\approx
\operatorname{Ref}_C(a_{t+1}).
\]

### Interpretive maintenance

The context preserves enough syntax, semantics, typing, and convention for the same marks to remain operationally interpretable.

### Realization maintenance

The supporting network preserves the capabilities through which an interpretation, operation, or attribution can continue to be realized.

### Target maintenance

The represented organization itself may be repaired, stabilized, reproduced, defended, or kept viable.

This fourth form is important in many domains, but it is not required in every application of the locus primitive.

A mountain can be followed as one locus across erosion without being repaired.

A historical event can remain an addressable locus of evidence without continuing to occur.

A number can remain usable without being physically preserved as one object.

The most general sense of maintenance is therefore:

> preservation of an operative distinction, identity, address, or realization relation across the transformations relevant to the model.

---

## 19. Constrained Realization

A realization is constrained when not every possible state, mapping, transition, or interpretation is admissible.

Let \(P\) be a possibility space and \(A_C\subseteq P\) the admissible subset in context \(C\).

Then:

\[
r\text{ is realizable in }C
\quad\Longrightarrow\quad
r\in A_C.
\]

Constraints may be:

```text
physical
logical
syntactic
typing-related
causal
institutional
legal
computational
resource-bound
evidentiary
```

The context does not arbitrarily invent realization.

It supplies and exposes the constraints under which selected possibilities can become operative.

Thus a locus of constrained realization is a site at which:

```text
some possibilities are addressable
some transitions are available
some relations are supported
some interpretations are excluded
```

---

## 20. State Requires a Holder of Attribution

A state is not merely a tuple of numbers.

A state is a selected configuration attributed to some addressable locus.

Let \(V_\ell\) be the variables retained for locus \(\ell\), with value domains \(D_v\).

Then a state may be represented as:

\[
s_{\ell,t}:V_\ell\to\prod_{v\in V_\ell}D_v.
\]

For example:

\[
s_{\ell,t}(\text{temperature})=20.
\]

The number `20` does not identify what has that temperature.

The locus \(\ell\) supplies the holder, identity, or address under which the value is attributed.

The state variables are themselves selected at some resolution.

A different model may represent the same realization with:

```text
temperature only
temperature and pressure
a probability distribution
a legal status
a memory configuration
a qualitative phase label
```

Therefore `state` silently assumes:

```text
an addressable state-bearer
a selected variable set
value domains
a time or comparison index when change matters
an identity relation across state variation
```

---

## 21. Objects, Nodes, Agents, and Citizens

The same analysis applies to familiar modeling primitives.

### Object

An object model usually assumes:

```text
identity
addressability
state
behavior
interface
lifetime
```

### Node

A node is a node only within a graph or relational context:

\[
v\in V(G).
\]

The same city, person, protein, or service can occupy a node role under different graph constructions.

### Agent

An agent additionally requires some organization of:

```text
observation
selection
action
state
objective or viability condition
```

### Citizen

A citizen is not merely a biological subclass of person.

Citizenship is an institutionally maintained relation:

\[
\operatorname{CitizenOf}(p,c,t,A),
\]

where \(A\) represents a relevant authority or legal context.

### Country

A country is not reducible to the set of people currently present within it.

It may depend on maintained relations of:

```text
territory
authority
recognition
records
institutions
continuity
```

These concepts are not arbitrary merely because their identity criteria are contextual.

They are constrained modeling roles realized through different networks.

---

## 22. Alphabet and Word Are Different Analytical Levels

An alphabet supplies distinguishable symbol types:

\[
\Sigma=\{a,b,c,\ldots\}.
\]

A word is a sequence over that alphabet:

\[
w\in\Sigma^*.
\]

A language or grammar selects admissible sequences:

\[
L\subseteq\Sigma^*.
\]

The alphabet should not be evaluated as though it were a word.

Likewise, a primitive modeling role should not be evaluated by the same criteria as a particular empirical claim made using that role.

At least four levels should be separated:

```text
carrier or marks
symbol types
well-formed expressions
interpreted claims about realizations
```

A coherence problem at one level cannot always be repaired by criticism directed at another.

---

## 23. A Layered Minimum Rather Than One Flat List

There may be no single flat set of properties required by every possible model.

Instead, there is a dependency hierarchy.

### Layer A: Pre-symbolic discrimination

Required for anything to become a candidate unit:

```text
available field
selection or attention
contrast
resolution
segmentation
```

### Layer B: Symbolic persistence

Required for repeatable reference:

```text
identity criterion
type-instance distinction
addressability
interpretive context
```

### Layer C: Structural modeling

Required for organized descriptions:

```text
roles
types
relations
composition
boundary
```

### Layer D: Operational modeling

Required for transformation:

```text
operations
input and output domains
admissibility
closure or partiality
```

### Layer E: Evaluative modeling

Required for claims and exclusions:

```text
assertion
equality or comparison
validation
truth, error, acceptance, or evidence criteria
```

### Layer F: Dynamical modeling

Required for state and change:

```text
time or transition index
state holder
identity across variation
continuity or succession
maintenance
```

### Layer G: Empirical realization modeling

Required when a formal model represents something beyond its own syntax:

```text
representation relation
measurement or observation
evidence
adequacy criterion
question and horizon
```

A model need not explicitly contain every higher layer.

But it cannot coherently use a higher-layer capability while leaving all of its prerequisites unavailable.

---

## 24. A Minimum Viable Locus

The minimum viable locus is not yet a full object, agent, component, or institution.

It is a reusable site of attribution.

A compact representation is:

\[
\boxed{
\ell_C
=
(S,\rho,B,I,a)
}
\]

with:

```text
S = selected organization
rho = resolution
B = boundary relative to a field
I = identity or re-identification criterion
a = addressability relation
```

The context \(C\) supplies the interpretation that makes these components operational.

A richer locus may then include:

\[
\ell
=
(S,\rho,B,I,a,X,R,\Pi,M,E),
\]

where:

```text
X = state description
R = relations and interfaces
Pi = admissible transformations
M = maintenance relations
E = evidence relations
```

The richer structure should not be mistaken for the absolute minimum required to distinguish anything.

It is the minimum needed for a realization-oriented modeling calculus with state, transformation, maintenance, and evidence.

---

## 25. The Context Required by a Locus

A context can be represented as:

\[
C
=
(U,\alpha,\rho,\sigma,\Gamma,\mathcal I,\mathcal A,H),
\]

where:

```text
U = available field or carrier
alpha = selection or attention regime
rho = resolution regime
sigma = segmentation regime
Gamma = grammar, typing, or composition rules
I = interpretation relations
A = admissibility and evaluation rules
H = relevant horizon
```

This context need not be globally complete.

It must only be sufficient for the selected question.

Let:

\[
\operatorname{Sufficient}(C,q)
\]

mean that \(C\) supports the distinctions, interpretations, operations, and evaluations required by question \(q\).

A context may be sufficient for reading `x y` as two characters and insufficient for determining their algebraic denotations.

Another context may be sufficient for parsing an equation and insufficient for deciding whether the equation accurately models a physical process.

Context sufficiency is layered.

---

## 26. Analytical Cuts Begin Before Explicit Modeling

An analytical cut is often described as though it were a later choice made over an already structured model.

But the present analysis suggests something stronger:

> The availability of a usable symbol already depends on an analytical cut.

The cut appears in:

```text
which pixels are selected
which differences count
which scale is used
which marks belong together
which occurrences count as the same
which context is retained
```

Thus:

\[
\chi_{q,C,\rho}(U)=\ell
\]

may represent not only the compression of a complex realization network into a locus, but the more basic constitution of an addressable modeling unit from an available field.

The same realization can be reopened at another scale:

\[
\operatorname{Refine}_{q',C',\rho'}(\ell)=N_\ell.
\]

Reopenability does not show that the earlier locus was false.

It shows that bounded modeling permits resolution to change with the question.

---

## 27. Model Coherence as Dependency Satisfaction

A model can be evaluated by asking whether the capabilities it uses are supported by their prerequisites.

This is not the same as asking whether the model is empirically correct.

It is a coherence audit.

### Carrier question

> In what field or medium do the model's distinctions occur?

Possible failure:

```text
symbols are treated as self-interpreting
```

### Selection question

> What makes some variation relevant and other variation background?

Possible failure:

```text
the model claims completeness while silently omitting most available variation
```

### Resolution question

> At what scale are units distinguished?

Possible failure:

```text
the model changes granularity without recording the change
```

### Segmentation question

> Why are these the units rather than another decomposition?

Possible failure:

```text
spaces, boundaries, or components are alternately ignored and treated as meaningful
```

### Identity question

> What makes two occurrences the same type or the same continuing entity?

Possible failure:

```text
material, functional, legal, and referential identity are conflated
```

### Addressability question

> How can the model refer to the unit again after change or composition?

Possible failure:

```text
state changes cannot be attributed to a stable holder
```

### Typing question

> Which roles may each unit occupy?

Possible failure:

```text
an operator is applied outside its domain
```

### Relation question

> What makes coexistence into a specific relation?

Possible failure:

```text
visual adjacency is mistaken for semantic connection
```

### Operation question

> What are the input positions, result domain, and partiality conditions?

Possible failure:

```text
an expression is written without any rule for what its result could be
```

### Evaluation question

> What distinguishes admissible from inadmissible claims?

Possible failure:

```text
nothing could count against the model
```

### Continuity question

> Which identity is preserved across state variation?

Possible failure:

```text
the model compares states without specifying what is supposedly the same across them
```

### Maintenance question

> Which distinction, address, capability, or organization must remain usable?

Possible failure:

```text
maintenance is confused with physical repair of the represented target
```

### Adequacy question

> For which question and horizon does the representation preserve enough of the target relations?

Possible failure:

```text
a model adequate at one scale is treated as universally adequate
```

---

## 28. A Compact Coherence Schema

A model \(\mathfrak M\) may be described by:

\[
\mathfrak M
=
(C,L,\mathcal R,\mathcal O,\mathcal E,\mathcal T),
\]

where:

```text
C = context of discrimination and interpretation
L = addressable loci
R = typed relations
O = operations or transformations
E = evaluation and evidence relations
T = representation targets, when any
```

A minimal coherence condition is:

\[
\operatorname{Coherent}(\mathfrak M)
\]

only if:

1. every referenced locus is distinguishable and addressable in \(C\);
2. every relation has declared or recoverable roles and domains;
3. every operation has admissible inputs and a result regime;
4. every evaluative claim has a criterion of acceptance, rejection, or suspension;
5. every dynamic attribution specifies what remains identical across change;
6. every target claim declares a representation context, question, and relevant horizon.

This condition does not prove truth.

It identifies missing commitments and category errors.

---

## 29. Common Category Errors

### Treating pixels as already being characters

Pixels are a carrier realization. Characterhood requires segmentation and interpretation.

### Treating distinct glyphs as necessarily distinct denotations

`x` and `y` may denote the same element under an assignment.

### Treating repeated glyphs as automatically identical

Repeated shapes may belong to different scopes, fonts, alphabets, or binding contexts.

### Treating an operation symbol as a complete operation

`+` requires domains, roles, a result regime, and rules.

### Treating equality as visual matching

Formal equality depends on the active identity criterion.

### Treating boundedness as material enclosure

A locus may be bounded analytically, legally, functionally, temporally, or evidentially.

### Treating maintenance as repair

The maintained feature may be a reference, interpretation, capability, or identity relation.

### Treating context as unlimited background

A usable context is itself bounded and selected.

### Treating resolution change as contradiction

A locus can be one unit at one scale and a network at another.

---

## 30. Grounding in Established AI Practice

Modern AI systems make many of these commitments unusually visible.

This does not prove the locus framework, but it provides concrete engineering examples.

### Tokenization

A model does not begin with intrinsically given words.

A tokenizer segments an input field into addressable token units under a vocabulary and algorithm.

The same visible string can receive different tokenizations under different systems.

This instantiates:

```text
field
segmentation
resolution
symbol identity
addressability
```

### Context windows

A model does not operate over all available reality or all possible history.

It operates over a bounded context assembled for a particular invocation.

The context window is an explicit analytical horizon.

### Attention

Attention operates over already addressable positions and computes context-dependent relations among them.

It does not attend directly to unsegmented reality.

### Embeddings

A token identifier acquires operational significance through an embedding and the transformations of the model.

The integer identifier alone does not contain its meaning.

### Key-value caches

A cache preserves addressable intermediate states across generation steps.

This is a direct example of referential and operational maintenance without implying that the represented subject itself is being physically repaired.

### Retrieval-augmented generation

Retrieval selects a bounded subset of external material for a question.

Ranking, chunking, and token limits create a constrained analytical cut.

The retrieved context may later be expanded when the question changes.

### Tool-using agents

An agent delegates capabilities through interfaces because its local context, memory, and action capacity are bounded.

Requirements, provisions, evidence, and maintenance paths become explicit at those interfaces.

These practices support a general observation:

> Bounded modeling systems operate by maintaining locally addressable distinctions through which selected relations and realizations become available.

---

## 31. What Is Actually Minimal?

The search for one absolutely minimal set must avoid two mistakes.

First, it must not assume that every model is dynamic, empirical, or computational.

Second, it must not treat prerequisites of use by a bounded interpreter as though they must all appear explicitly inside the formal object.

A plausible minimum for **symbolic availability** is:

```text
field
cut
resolution
segmentation
identity criterion
addressability
context
```

A plausible minimum for **structural modeling** adds:

```text
types or roles
relations
composition rules
```

A plausible minimum for **operational modeling** adds:

```text
operations
admissibility
result regimes
```

A plausible minimum for **dynamical modeling** adds:

```text
state
transition
identity across variation
maintenance
```

A plausible minimum for **empirical modeling** adds:

```text
representation relation
evidence
adequacy
question
horizon
```

The locus primitive sits near the transition from symbolic availability to structural modeling.

It is the addressable unit to which later structure can be attributed.

---

## 32. Central Principles

### Pre-Symbolic Cut Principle

> No mark functions as a symbol without a context that selects and segments it from an available field.

### Resolution Principle

> Every operational distinction is made at some resolution, whether or not that resolution is explicitly recorded.

### Bounded Addressability Principle

> A unit becomes modelable when it is bounded enough to be referred to again under an identity criterion.

### Type-Instance-Denotation Principle

> A mark occurrence, a symbol type, and a denoted realization are distinct analytical levels.

### Contextual Identity Principle

> Identity preserves selected equivalences rather than complete sameness.

### Relational Role Principle

> Co-occurrence does not determine relation; a context must assign roles and admissible connections.

### Operational Constraint Principle

> An operation is defined by admissible input roles, a result regime, and constraints on application.

### Evaluation Principle

> A formal claim becomes constrained only when some results, interpretations, or inscriptions can be rejected, suspended, or treated as undefined.

### Referential Maintenance Principle

> Maintenance most generally preserves the usability of an identity, address, distinction, capability, or realization relation across relevant change.

### Locus Principle

> A locus is a bounded, addressable organization formed by a cut at a resolution under an identity and interpretation regime.

### Layered Sufficiency Principle

> A context need only be sufficient for the distinctions and operations required by the current question; it need not contain all possible context.

### Reopenability Principle

> A bounded locus may be refined when a new question requires a different resolution without making the earlier representation intrinsically false.

### Coherence Dependency Principle

> A model is internally coherent only when the capabilities it invokes are supported by their required distinctions, identities, roles, domains, and evaluation rules.

---

## 33. Central Statements

> The first distinction is not necessarily `x` versus `y`; it is selected variation versus what is not selected as that variation.

> A visible mark is not yet a character.

> Segmentation is already a modeling decision constrained by a carrier and a task.

> Counting begins only after a criterion of unit identity has made a domain countable.

> Every usable distinction has a resolution.

> Every reusable distinction requires an identity criterion.

> Every changing attribution requires an address or holder through which the change remains comparable.

> Writing `x + y` invokes operand roles and a result regime even when the result is unnamed.

> Writing `x + y = z` does not require three distinct denotations; it requires two input positions, one result position, and an evaluable relation.

> Equality, inequality, and operation symbols do not carry their own semantics.

> Boundedness is not merely a resource defect; it is a condition of addressable representation.

> Maintenance need not mean repairing the represented thing.

> A maintained locus preserves an operative site of reference through which constrained realizations can be organized.

> A coherence audit asks what a model must already be assuming in order for its symbols, states, objects, nodes, or operations to function non-arbitrarily.

---

## 34. Conclusion

A model cannot begin from arbitrary characters and then acquire all structure afterward.

The use of a character non-arbitrarily already presupposes a bounded interpretive achievement.

Some variation has been:

```text
made available
selected
contrasted
segmented
resolved at a scale
recognized as a type
addressed as an occurrence
preserved for reuse
```

Only then can it enter relations, operations, equations, states, and claims.

The inscription:

```text
x y
```

therefore begins not with two self-evident objects, but with a field and a cut.

The next question is how the selected variation is segmented.

The next is at what resolution.

The next is which segments count as the same type.

The next is how they are addressed.

Only after those commitments are available can `x` and `y` become formal units.

Adding:

\[
+
\]

introduces operand roles and a rule-governed transformation.

Adding:

\[
=
\]

introduces an evaluable identity claim.

Adding:

\[
\neq
\]

introduces explicit exclusion under an identity criterion.

Adding state introduces selected values attributed to an addressable holder.

Adding change introduces identity across variation.

Adding empirical interpretation introduces evidence and adequacy relative to a target, question, context, and horizon.

The locus can therefore be understood as the first stable modeling carrier produced by these commitments:

\[
\boxed{
\text{selected}
+
\text{bounded}
+
\text{resolved}
+
\text{identifiable}
+
\text{addressable}
}
\]

A richer locus becomes a site of constrained realization when relations, state, transformations, maintenance, and evidence are organized through it.

The deepest claim is not that reality is literally composed of loci.

It is:

> Any bounded model that uses non-arbitrary distinctions must establish locally sufficient loci through which identities, relations, operations, and realizations can remain addressable.

This makes the locus framework more than a new vocabulary for objects.

It becomes a way to expose what formal systems, state models, graph models, object models, counting practices, and bounded AI systems already rely upon but often leave implicit.
