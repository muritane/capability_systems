# From Lost Provenance to Cumulative Intelligence

## 1. The central problem

A recurring mistake in reasoning about intelligence, compression, learning, and optimization is to begin from an already-flattened observation and treat the difficulty of reconstructing structure from that observation as though it were the intrinsic complexity of the underlying phenomenon.

But an observed artifact often has a history:

\[
z
\rightarrow
G
\rightarrow
x,
\]

where:

- \(z\) contains source variables, parameters, or prior state,
- \(G\) is a generative process,
- \(x\) is the resulting observation.

If the generative process, provenance, source representation, protocol, or structural metadata is already known, then discarding it and later attempting to infer equivalent structure from \(x\) introduces an artificial problem.

The important distinction is:

\[
\boxed{
\text{complexity of the phenomenon}
\neq
\text{difficulty created by a lossy representation of the phenomenon}.
}
\]

This leads to a broader principle:

\[
\boxed{
\text{Do not destroy information and then confuse the cost of inference with the complexity of reality.}
}
\]

---

# 2. Observation does not uniquely determine origin

Suppose

\[
y=f(x).
\]

If \(f\) is many-to-one, then there may exist

\[
x_1\neq x_2
\]

such that

\[
f(x_1)=f(x_2)=y.
\]

Once only \(y\) remains, there is generally no way to determine with certainty which \(x_i\) produced it.

This is not a limitation of insufficient computation.

It is a limitation of available information.

For a trivial example, observing a single Boolean output

\[
0
\]

does not determine whether it was produced by:

- `AND(0, 1)`,
- `OR(0, 0)`,
- `NOT(1)`,
- `NAND(1, 1)`,
- a constant-zero circuit,
- a program that happened to output zero,
- a failed sensor,
- or indefinitely many other processes.

The output constrains the set of possible generators.

It does not uniquely identify one.

Thus:

\[
\boxed{
\text{more computation cannot uniquely reconstruct information that the observation does not distinguish}.
}
\]

Additional observations, interventions, priors, metadata, or constraints may reduce the ambiguity.

But the ambiguity cannot be removed merely by searching harder over the same information.

---

# 3. Compression is not causal reconstruction

Suppose the observed data is

```text
0000000000000000
```

A compact model might be:

```text
repeat(0, 16)
```

That is an excellent description of the observation.

It does not imply that the true generating process was a repetition operator.

The same sequence might have arisen from:

- sixteen independent random events,
- a disconnected sensor,
- an explicit loop,
- a stored constant,
- a cryptographic process that happened to produce that prefix,
- or many other causes.

Therefore:

\[
\boxed{
\text{a good compressor of observations is not necessarily a correct reconstruction of their causal history}.
}
\]

This distinction matters whenever a learned latent structure is interpreted as though it were the structure that actually generated the data.

A model may be:

\[
\text{predictively sufficient}
\]

without being:

\[
\text{causally unique}.
\]

---

# 4. Phenomenon, representation, provenance, and model are different

It is useful to distinguish four layers.

## Phenomenon

The process or system that exists independently of a particular encoding:

\[
W.
\]

## Representation

A mapping that exposes some distinctions and hides others:

\[
R(W).
\]

## Provenance

Information about how the represented state came to exist:

\[
P.
\]

This may include:

- source code,
- transformation history,
- schema,
- protocol,
- compiler,
- build configuration,
- revision graph,
- instrumentation metadata,
- causal interventions,
- manufacturing process,
- data lineage.

## Model

A structure inferred or constructed to explain, predict, compress, or control observations:

\[
M(R(W),P).
\]

These layers should not be collapsed.

A regularity in \(M\) is not automatically a constituent of \(W\).

A regularity in \(W\) may disappear under \(R\).

A useful provenance variable in \(P\) may be impossible to recover uniquely from \(R(W)\).

This yields two symmetrical errors:

\[
\text{model structure mistaken for world structure}
\]

and

\[
\text{world structure obscured by the chosen representation}.
\]

---

# 5. Known structure and unknown structure should be treated differently

Suppose a regularity \(R\) is relevant to some data \(D\).

There are at least three distinct cases.

## Case 1: the regularity is unknown

Then genuine discovery is required:

\[
D\rightarrow \hat R.
\]

The search is justified because the structure is not already available.

## Case 2: the regularity is known and reusable

Then the natural architecture is:

\[
R+\theta\rightarrow D,
\]

where \(\theta\) contains the varying information.

The regularity should be represented once and reused.

## Case 3: the regularity is known but artificially withheld

Now the learner receives only \(D\) and must infer something like

\[
D\rightarrow\hat R,
\]

even though \(R\) already exists elsewhere in the system.

This may be a legitimate experimental setup if the target capability is explicitly:

> infer useful structure from observations without access to provenance.

But it is not the same problem as:

> represent the information as efficiently as possible using everything already known.

The distinction should be explicit.

---

# 6. The source-code / binary example

Consider:

\[
(\text{source},\text{compiler},\text{configuration})
\rightarrow
\text{binary}.
\]

The source tree and build process contain substantial information about the structure of the resulting binary.

Now imagine the following procedure:

1. compile the source,
2. discard the source,
3. discard the compiler metadata,
4. retain only the binary,
5. ask an expensive learner to recover structure from the binary,
6. reward it for rediscovering regularities implied by the discarded source and compilation process.

This can test reverse engineering.

It does not test the most efficient use of available knowledge.

If the source still exists elsewhere, then the system has created an artificial information bottleneck and is measuring performance inside that bottleneck.

The resulting difficulty is partly:

\[
\text{difficulty of the artifact}
\]

and partly:

\[
\text{difficulty introduced by deleting its provenance}.
\]

Those should not be confused.

---

# 7. Repository structure is already extracted regularity

A repository is not merely a bag of bytes.

Its organization may already encode:

- reusable templates,
- dependencies,
- naming conventions,
- deltas,
- revision history,
- shared libraries,
- schemas,
- generated files,
- source/derived distinctions,
- stable directory structure,
- build rules.

These are regularities that have already been discovered and made explicit.

Flattening the repository into a byte stream can erase exactly the organization that makes the system cheap to reason about.

One can always attempt to rediscover that organization statistically.

But if the organization is already known, the more efficient operation is usually:

\[
\boxed{
\text{preserve the structure and model only what remains unexplained by it}.
}
\]

This is the same reason a build system stores source and rules rather than treating every generated artifact as an unrelated opaque object.

---

# 8. Regularity extraction should target residual uncertainty

Let:

\[
K_t
\]

be the reusable knowledge available at time \(t\), and let:

\[
D_t
\]

be new observations.

The naive learning problem is:

\[
D_t\rightarrow R_t.
\]

But a cumulative learner should instead ask:

\[
\boxed{
R_t
=
\operatorname{Regularity}(D_t\mid K_t).
}
\]

That is:

> What remains structurally unexplained after conditioning on everything already known?

After learning something useful:

\[
K_{t+1}=K_t\cup R_t.
\]

Then future search occurs relative to the enlarged knowledge base:

\[
R_{t+1}
=
\operatorname{Regularity}(D_{t+1}\mid K_{t+1}).
\]

This is the architecture of cumulative intelligence.

The system should not repeatedly pay to rediscover the same regularity.

---

# 9. Discovery is valuable partly because it eliminates future discovery

Suppose discovering a regularity costs:

\[
C_{\text{discover}}(R).
\]

Once discovered and stabilized, using it may cost only:

\[
C_{\text{use}}(R,\theta).
\]

A useful architecture therefore tries to transform:

\[
\text{repeated discovery}
\]

into:

\[
\text{discover once}
\rightarrow
\text{encode}
\rightarrow
\text{reuse}.
\]

If the same structural fact must repeatedly be inferred from flattened observations, the system pays a rediscovery tax:

\[
C_{\text{rediscovery}}
=
\sum_t C_{\text{infer}}(R\mid D_t).
\]

A mature abstraction should reduce this toward:

\[
C_{\text{store}}(R)
+
\sum_t C_{\text{instantiate}}(R,\theta_t).
\]

Thus regularity extraction is not an end in itself.

Its purpose is partly to make that regularity unnecessary to rediscover at the next layer.

---

# 10. Abstraction is compiled knowledge

A recurring composition may initially require many lower-level operations:

\[
A\rightarrow B\rightarrow C\rightarrow D.
\]

After repeated use, it can be encapsulated as:

\[
E:=A\rightarrow B\rightarrow C\rightarrow D.
\]

Then later reasoning can invoke:

\[
E
\]

without reconstructing the sequence.

In this sense, abstraction is a kind of compilation.

It takes:

\[
\text{previous search and organization}
\]

and converts them into:

\[
\text{cheap reusable control}.
\]

A good abstraction therefore contains historical work.

Discarding it and requiring a downstream agent to recover its consequences from raw outputs is analogous to repeatedly decompiling a program rather than retaining its source-level structure.

---

# 11. Flattening can manufacture difficulty

Consider a structured object:

\[
X=(G,\theta),
\]

where \(G\) is a stable generating rule and \(\theta\) contains variable parameters.

Flatten it through some representation:

\[
F(X)=D.
\]

Now suppose \(F\) destroys the explicit distinction between \(G\) and \(\theta\).

A learner receiving only \(D\) must solve something like:

\[
D\rightarrow (\hat G,\hat\theta).
\]

The resulting optimization problem may be extremely difficult.

But the difficulty may have been introduced by:

\[
F.
\]

So before increasing search effort, a useful diagnostic is:

\[
\boxed{
\text{At which transformation in the pipeline did this become difficult?}
}
\]

If the answer is:

> when known structure was flattened into an opaque representation,

then a better architecture may be to preserve the structure rather than build a more powerful reconstruction mechanism.

---

# 12. Frame selection is itself an optimization problem

Ordinary optimization assumes a fixed problem:

\[
x^*
=
\arg\min_x L(x).
\]

But many problems depend on a chosen frame \(F\):

\[
x^*_F
=
\arg\min_x L(x\mid F).
\]

A more general search includes the frame itself:

\[
(F^*,x^*)
=
\arg\min_{F,x}
L(x\mid F)
+
C(F).
\]

The frame may determine:

- what counts as data,
- what counts as protocol,
- what counts as metadata,
- what variables are addressable,
- what regularities are explicit,
- what must be inferred,
- what costs are counted,
- what transformations are legal.

Changing the frame can therefore produce gains larger than further optimization within a fixed frame.

This is not because the local optimizer was poor.

It is because the problem definition itself determined which regularities were available.

---

# 13. Local optimization and research value are different objectives

A benchmark typically chooses a scalar objective:

\[
J_{\text{local}}.
\]

For example:

- compressed size,
- prediction loss,
- latency,
- accuracy,
- energy consumption.

But a research program may care about a vector:

\[
V=
\begin{pmatrix}
\text{local performance}\\
\text{transferability}\\
\text{robustness}\\
\text{compute cost}\\
\text{human search cost}\\
\text{maintainability}\\
\text{new abstractions}\\
\text{future option value}
\end{pmatrix}.
\]

A method can dominate on the benchmark while being poor on several other dimensions.

Thus:

\[
\boxed{
\text{benchmark optimality}
\neq
\text{research-program optimality}.
}
\]

A benchmark is useful partly because it freezes the frame and creates comparability.

But the decision to continue investing in that frame is a separate optimization problem.

---

# 14. Diminishing returns and frame risk

Let effort \(e\) produce local performance \(P(e)\):

\[
\frac{dP}{de}>0,
\qquad
\frac{d^2P}{de^2}<0.
\]

Performance continues improving, but marginal gains decline.

Now suppose the surrounding protocol, hardware, representation, API, or task may change.

Let:

\[
\tau
\]

measure how much of the accumulated advantage transfers after such a change.

Then two research strategies may look like:

\[
A:
\quad
P_A\gg P_B,
\qquad
\tau_A\ll\tau_B.
\]

The locally superior strategy may be globally inferior if its gains disappear when the frame changes.

This motivates the idea of **frame risk**:

\[
\boxed{
\operatorname{FrameRisk}(R)
=
\text{fraction of the value of }R
\text{ destroyed by plausible reframing}.
}
\]

Examples of reframing include:

- protocol replacement,
- API redesign,
- hardware change,
- new representation,
- different data modality,
- new scale,
- new environment,
- new benchmark.

Highly specialized tricks may have high frame risk.

Structural principles may have low frame risk.

---

# 15. Transferability can be treated as performance across frames

Let:

\[
F\sim\mathcal D_F
\]

represent a distribution of possible future problem frames.

For an abstraction or algorithm \(A\), define:

\[
G(A,F)
\]

as its useful gain inside frame \(F\).

Then transfer value can be written as:

\[
\boxed{
T(A)
=
\mathbb E_{F\sim\mathcal D_F}[G(A,F)].
}
\]

A highly specialized method may have:

\[
G(A,F_0)\gg 0
\]

but:

\[
T(A)\approx 0.
\]

A more general structural insight may have smaller local gain but much larger expected transfer.

Of course, the future frame distribution is not known exactly.

That uncertainty is itself part of the problem.

But ignoring it entirely effectively assumes:

\[
F_{\text{future}}=F_{\text{current}},
\]

which is often the strongest and least visible assumption in local optimization.

---

# 16. Deep regularities survive reframing

A regularity can be evaluated not only by how much it compresses one dataset, but by how well it survives transformations of the problem.

Let:

\[
\mathcal T
\]

be a family of plausible reframings.

Then define a rough robustness measure:

\[
\rho(R)
=
\Pr_{T\sim\mathcal T}
[
R
\text{ remains useful after }T
].
\]

A representation-specific trick may have low \(\rho\).

A principle such as:

\[
\text{repeated structure}
\rightarrow
\text{store rule once + transmit parameters}
\]

has much higher \(\rho\).

This suggests a useful heuristic:

\[
\boxed{
\text{the deeper a regularity, the more transformations of representation it tends to survive}.
}
\]

This is not an absolute law.

Some valuable domain-specific structures are necessarily narrow.

But reframing robustness is an important dimension that local compression or prediction scores do not measure.

---

# 17. Known provenance changes the optimal learning problem

Suppose the complete state available to an agent is:

\[
I=(D,P,K),
\]

where:

- \(D\) is observation,
- \(P\) is provenance,
- \(K\) is existing reusable knowledge.

A learner that intentionally ignores \(P\) and \(K\) solves:

\[
M(D).
\]

A learner using all available information solves:

\[
M(D\mid P,K).
\]

These are different tasks.

The first may be useful for measuring robustness under information deprivation.

The second is generally the relevant problem for an agent trying to act efficiently in the world.

Thus a benchmark can legitimately ask:

> Can an agent infer structure when provenance is unavailable?

But a production architecture should normally ask:

> What does the agent still need to infer after exploiting all available provenance and prior structure?

---

# 18. Information deprivation can be a benchmark, but it should be named

Artificially withholding structure is not inherently meaningless.

It can test:

- reconstruction,
- reverse engineering,
- robustness,
- scientific inference,
- unsupervised discovery,
- generalization without metadata,
- recovery from damaged or missing infrastructure.

These are real capabilities.

The methodological mistake occurs when the test is interpreted as though the deprived condition were the natural or optimal information architecture.

A benchmark may intentionally specify:

\[
\boxed{\text{solve the problem from this restricted view}.}
\]

That is useful for comparability.

But it does not follow that a real system should voluntarily remain inside that restricted view once more informative structure is available.

---

# 19. Inference cannot reverse information destruction for free

The general principle can be written as:

\[
\boxed{
\text{lost provenance}
+
\text{remaining observation}
\not\Rightarrow
\text{unique provenance}.
}
\]

Search can enumerate candidates.

Priors can rank them.

Additional evidence can eliminate them.

Interventions can distinguish them.

But computation alone cannot manufacture the missing distinctions.

Therefore, if provenance is already known, preserving it usually dominates destroying it and attempting to infer it again.

This suggests an architectural rule:

\[
\boxed{
\text{preserve information that is expensive or impossible to reconstruct uniquely}.
}
\]

That includes not only raw data but also:

- transformation history,
- source/derived relationships,
- schemas,
- causal metadata,
- dependency structure,
- semantic labels when trustworthy,
- version history,
- interfaces,
- reusable generators.

---

# 20. Cumulative intelligence minimizes repeated uncertainty

A weak learning architecture repeatedly asks:

\[
\text{What structure can I infer from this observation?}
\]

A cumulative architecture asks:

\[
\text{What uncertainty remains after everything already learned has been reused?}
\]

The difference is:

\[
\text{repeated inference}
\]

versus:

\[
\text{monotonic accumulation of reusable structure}.
\]

The idealized process is:

\[
\text{observe}
\]

\[
\downarrow
\]

\[
\text{condition on existing knowledge}
\]

\[
\downarrow
\]

\[
\text{extract residual regularity}
\]

\[
\downarrow
\]

\[
\text{validate}
\]

\[
\downarrow
\]

\[
\text{encode as reusable structure}
\]

\[
\downarrow
\]

\[
\text{never solve the same problem at full cost again}.
\]

This is learning as infrastructure accumulation.

---

# 21. Research efficiency should include transfer and reuse

A local measure might be:

\[
\frac{\Delta P}{\Delta e},
\]

where \(P\) is benchmark performance and \(e\) is effort.

A broader measure should account for what survives after the immediate task:

\[
\boxed{
\operatorname{ResearchEfficiency}
=
\frac{
\text{local gain}
+
\text{expected transfer}
+
\text{reusable abstractions}
+
\text{future search avoided}
}{
\text{compute}
+
\text{human effort}
+
\text{maintenance}
+
\text{adaptation cost}
}.
}
\]

This makes explicit why an optimization with diminishing local returns may still consume enormous resources while producing little durable knowledge.

Conversely, a modest local result may be highly valuable if it discovers an abstraction that eliminates entire future search problems.

---

# 22. Search should move between levels

A system should not always search harder at the current representation.

It should compare at least two marginal returns:

\[
\text{benefit of more search within the current frame}
\]

versus

\[
\text{benefit of searching for a better frame}.
\]

This gives a meta-search loop:

\[
\text{choose frame}
\]

\[
\downarrow
\]

\[
\text{exploit known structure}
\]

\[
\downarrow
\]

\[
\text{search residual uncertainty}
\]

\[
\downarrow
\]

\[
\text{measure diminishing returns}
\]

\[
\downarrow
\]

\[
\text{test transferability}
\]

\[
\downarrow
\]

\[
\text{promote robust discoveries into infrastructure}
\]

\[
\downarrow
\]

\[
\text{reframe when the current boundary becomes the bottleneck}.
\]

The scarce resource is not merely computation.

It is:

\[
\boxed{
\text{search effort allocated across levels of representation and abstraction}.
}
\]

---

# 23. A stronger criterion for abstraction

An abstraction is useful when it removes unnecessary detail.

A stronger abstraction is useful across multiple nearby representations.

A very strong abstraction survives substantial reframing.

Thus abstraction quality can be thought of as involving:

\[
\text{compression}
\]

\[
+
\text{control leverage}
\]

\[
+
\text{transferability}
\]

\[
+
\text{reframing robustness}
\]

\[
+
\text{future search avoided}.
\]

A compact domain-specific trick may be excellent engineering.

A compact rule that remains useful across different protocols, encodings, tasks, and implementations is closer to reusable theory.

---

# 24. The danger of mistaking reconstruction for discovery

A particularly strange pipeline is:

\[
\text{known structure}
\]

\[
\downarrow
\]

\[
\text{erase or hide structure}
\]

\[
\downarrow
\]

\[
\text{infer surrogate structure}
\]

\[
\downarrow
\]

\[
\text{treat surrogate as a discovery about reality}.
\]

This can produce two errors simultaneously.

First, the system spends resources reconstructing information it already possessed.

Second, the inferred surrogate may be only one of many observationally equivalent explanations.

Therefore:

\[
\hat G
\]

may explain the flattened observations while still differing from:

\[
G_{\text{actual}}.
\]

The architecture has converted known causal structure into uncertain inferred structure.

That is not progress unless the purpose was specifically to test reconstruction under deprivation.

---

# 25. Representation can create its own "heaven"

Suppose a phenomenon is represented through some model that introduces a latent object:

\[
H.
\]

If \(H\) helps organize predictions, one may be tempted to conclude:

\[
H\in W.
\]

But all that has been established may be:

\[
H\in M.
\]

The phenomenon may be real while the named latent object is merely one useful coordinate system for it.

Conversely, an important real structure may be absent from the model because the representation erased the distinctions needed to expose it.

Thus:

\[
\boxed{
\text{do not fight the ontology of the representation as though it were necessarily the ontology of the world}.
}
\]

The problem may be real.

The category in which the problem appears may be constructed.

This is another reason reframing can produce abrupt gains: it changes which distinctions are treated as fundamental.

---

# 26. A practical diagnostic

Before launching a large search or optimization process, ask:

1. **What information existed before the current representation was produced?**
2. **Which parts of that information were discarded?**
3. **Was the discarded structure already known?**
4. **Is the learner now being asked to rediscover it?**
5. **Can the missing information be reconstructed uniquely, or only guessed probabilistically?**
6. **What regularity remains genuinely unknown after existing knowledge is restored?**
7. **Would preserving provenance make the problem substantially cheaper?**
8. **Are current gains transferable if the protocol or representation changes?**
9. **Is marginal effort better spent optimizing locally or changing the frame?**
10. **Which discoveries can be promoted into reusable infrastructure so they never require full-cost rediscovery again?**

These questions separate genuine unknown structure from difficulty manufactured by information loss.

---

# 27. A general architecture

The overall process can be summarized as:

\[
\boxed{
\begin{array}{c}
\text{phenomenon / generative process}\\
\downarrow\\
\text{preserve provenance}\\
\downarrow\\
\text{choose a useful representation}\\
\downarrow\\
\text{reuse known regularities}\\
\downarrow\\
\text{identify residual uncertainty}\\
\downarrow\\
\text{search for new regularities}\\
\downarrow\\
\text{validate and stabilize}\\
\downarrow\\
\text{encode as reusable abstraction}\\
\downarrow\\
\text{measure transfer and frame risk}\\
\downarrow\\
\text{reframe when necessary}
\end{array}
}
\]

The central objective is not maximum inference from minimum context.

It is:

\[
\boxed{
\text{minimum repeated inference for maximum durable understanding and control}.
}
\]

---

# 28. Final principle

Regularity extraction is essential when structure is unknown.

It is wasteful when the same structure is already known and merely inaccessible because the representation discarded it.

The mature system therefore does not glorify reconstruction for its own sake.

It tries to preserve the path by which knowledge was obtained, accumulate abstractions, and direct new search only toward genuine residual uncertainty.

The deepest recurring pattern is:

\[
\boxed{
\text{discover}
\rightarrow
\text{preserve}
\rightarrow
\text{reuse}
\rightarrow
\text{search only the remainder}.
}
\]

Or, stated negatively:

\[
\boxed{
\text{Do not erase solved structure and then measure intelligence by the cost of solving it again.}
}
\]

The purpose of intelligence is not to repeatedly recover a world from unnecessary ignorance.

It is to turn discoveries into persistent structure so that future effort can begin where previous effort ended.
