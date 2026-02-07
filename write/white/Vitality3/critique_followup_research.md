# Follow-Up Research: Two Questions on the Entropy Critique

*Generated from research on the critique in `critique_symbols_and_entropy.md`*

---

## Question 1: Does the Critique Hold if the Representation Problem is Solved?

### The Setup

Suppose we grant that connectionist mechanisms — learned embeddings, sparse autoencoders (Templeton et al. 2024), VQ-VAE discrete codebooks (van den Oord et al. 2017), DreamCoder's program libraries (Ellis et al. 2021) — solve the representation/grounding problem. Representations are generated bottom-up and indexed into a discrete, manipulable vocabulary. Could a probabilistic upper layer then operate over this vocabulary using information-theoretic objectives (empowerment, free energy, MI maximization)?

### Short Answer

**Partially rescued, but the three remaining critiques still bite.** Solving the representation problem is a genuine advance that makes the other problems more tractable in practice, but it does not eliminate them.

---

### Critique 1 (Representation Presupposed): Largely Resolved

If connectionist mechanisms produce grounded, indexed representations, the circularity objection dissolves. Shannon information can now be computed over a well-defined symbol set that was *learned* rather than presupposed.

**Supporting evidence:**
- Templeton et al. (2024) extracted millions of interpretable, multilingual, multimodal features from Claude 3 Sonnet using sparse autoencoders — discrete structure genuinely emergent from continuous activations.
- VQ-VAE codebooks of size K=512 with spatial grids provide enormous expressive capacity (512^1024 configurations) from a finite discrete vocabulary.
- DreamCoder bootstraps compositional program libraries through wake-sleep learning, discovering 93% of 60 physical laws by first learning building blocks of vector algebra.

**Verdict: Critique (1) is addressed.** The question is whether this rescue propagates.

---

### Critique 2 (MI Intractability): Significantly Mitigated but Not Eliminated

**What the O(ln N) bound actually says:** McAllester & Stratos (2020) proved that any *distribution-free* high-confidence lower bound on MI from N samples cannot exceed O(ln N). The key escape clause: this is for the distribution-free setting. With a **known, finite alphabet**, the situation changes.

**How discretization helps:**
- For jointly discrete random variables with alphabet size K, MI can be computed as a finite sum: I(X;Y) = Σ P(x,y) log(P(x,y) / P(x)P(y)). The challenge shifts from estimation to obtaining good probability estimates.
- The Blahut-Arimoto algorithm can compute channel capacity (the empowerment quantity) exactly for discrete memoryless channels.
- With a codebook of manageable size (K=512), probability estimation over K² joint states is feasible.

**Where the problem persists:**
1. **Exponential scaling with time horizon.** Even in discrete spaces, n-step empowerment requires considering all |A|^n action sequences. Long-horizon planning remains intractable.
2. **Combinatorial state spaces.** Compositional states (e.g., a 32×32 grid of codebook entries) have astronomically large effective state spaces, and the distribution-free bound reasserts itself.
3. **Variational approximations still needed.** Mohamed & Rezende (2015) showed that practical empowerment maximization in high-dimensional settings requires variational bounds, reintroducing the gap between estimated and true MI.

**Verdict: The O(ln N) bound is *circumvented for small finite alphabets* but *resurfaces* through exponential horizon scaling and combinatorial explosion of compositional states. Weakened from fundamental impossibility to engineering scaling challenge.**

---

### Critique 3 (Structural Impoverishment): Partially Mitigated

**How discrete codebooks help:**
- Information geometry provides richer structure on discrete spaces. The probability simplex over K outcomes is a (K-1)-dimensional Riemannian manifold with the Fisher information metric — the unique invariant metric under Markov embeddings.
- Discrete Codebook World Models (Scannell et al., ICLR 2025) demonstrate that discrete codebook encodings "preserve ordinal relationships between observations."
- Partial Information Decomposition (Williams & Beer 2010; extended 2024) decomposes joint information into unique, redundant, and synergistic components — structure invisible to scalar entropy.

**Where the problem persists:**
1. **Optimization objectives remain scalar.** If you optimize "maximize empowerment" or "minimize free energy," you are still hill-climbing on a scalar, even if the underlying representations are structured. The optimizer cannot distinguish between two states with identical MI but different compositional structure.
2. **Codebook structure is implicit.** VQ-VAE codebooks learn vectors by reconstruction pressure, but relational structure between entries is emergent and not captured by the information-theoretic objective. The *codebook collapse* problem (many entries going unused) demonstrates insufficient structural pressure.
3. **Synergistic information is invisible to standard measures.** PNAS (2023) showed that synergistic information "cannot be reduced to pairs" and is "invisible to standard network-based approaches."

**Verdict: The codebook gives you a structured space; the entropy objective then throws away most of that structure when deciding what to do.**

---

### Critique 4 (Causal Blindness): Essentially Unrescued

**This is the hardest critique, and discretization does essentially nothing to address it.**

The Causal Hierarchy Theorem (Bareinboim et al. 2022) is a *structural* result about the relationship between statistical and causal information. It does not depend on whether representations are continuous or discrete, high-dimensional or low-dimensional, learned or hand-crafted.

Even with a perfect discrete codebook:
- **MI is symmetric:** I(X;Y) = I(Y;X). Causation is directional. No amount of MI computation can determine causal direction — only the "causal skeleton."
- **Confounders are invisible to MI:** Non-zero MI between X and Y can arise from a common cause Z.
- **Empowerment measures channel capacity, not causal effect.** It describes what states *correlate* with what actions under current dynamics, not what would happen under novel interventions.
- **Active inference fails the frame problem.** Parvizi-Wayne (2024) argues that active inference has "heretofore failed to resolve the problem of relevance" — precision-weighting mechanisms are "explanatorily weak."

**What would be needed:** Causal Representation Learning (Schölkopf et al.) can identify latent causal variables "up to permutation and elementwise reparameterization" — but requires *interventional data* as input. GFlowNets for Causal Discovery (Deleu, Bengio et al.) combine learned discrete representations with causal structure learning — but the causal structure is not emerging from the information-theoretic objective alone.

**Verdict: The CHT is a mathematical theorem about the structure of causal reasoning, not about representation quality. Even a perfect discrete vocabulary with perfect probability estimates operating under a pure information-theoretic objective cannot perform interventional or counterfactual reasoning.**

---

### Could We Have a Probabilistic Upper Layer?

**Yes, but it cannot be *purely* information-theoretic.** Every successful hybrid system supplements information theory with additional structure:

| System | Bottom Layer | Upper Layer | What the upper layer adds beyond MI |
|--------|-------------|-------------|-------------------------------------|
| GFlowNets (Bengio et al. 2023) | Neural network | Discrete compositional sampling | Explicit reward/energy functions, structural assumptions |
| DreamCoder (Ellis et al. 2021) | Neural search policy | Program library | Compositional programming language with syntax/semantics |
| DCWM + DC-MPC (ICLR 2025) | VQ-VAE codebook | Model predictive control | Explicit forward simulation and optimization |
| DeepProbLog / Scallop | Neural perception | Probabilistic logic programs | Logical/causal structure |
| Active Inference (discrete POMDP) | Sensory model | Expected free energy | Prior preferences, temporal depth |

**The pattern:** In every case, the upper layer imports structure from outside information theory — causal models, logical programs, planning algorithms, or compositional program libraries. Pure "probabilistic layer doing MI optimization over learned vocabulary" is insufficient.

---

### Summary: Critique Survival After Discretization

| Critique | Effect of Connectionist Discretization | Residual Severity |
|----------|---------------------------------------|-------------------|
| (1) Representation presupposed | **Largely resolved** | Low |
| (2) MI estimation intractable | **Significantly mitigated** for small alphabets; resurfaces for compositional spaces and long horizons | Medium |
| (3) Entropy collapses structure | **Partially mitigated** by information geometry / PID; but optimization remains scalar | Medium-High |
| (4) No causal structure (CHT) | **Essentially unaffected** | High — unchanged |

**Bottom line:** Solving the representation problem is necessary but not sufficient. The upper layer needs to be richer than information theory alone — it needs causal structure, compositional guarantees, or both.

---

## Question 2: If Not Entropy, What?

### The Landscape of Post-Entropic Frameworks

If information theory cannot serve as the "mother of all valleys" — the universal optimization landscape for autonomy and cognition — what are the concrete alternatives? Seven candidates are assessed below, each probed for mathematical maturity, computational operationalization, what it can do that entropy cannot, and what it still lacks.

---

### 1. Constructor Theory (Deutsch & Marletto)

**Overview:** Reformulates physics not as "what happens given initial conditions" but as "which transformations are possible and which are impossible, and why." A *constructor* is any entity that can cause a task and retain the ability to do so again — a heat engine, a catalyst, an organism, a factory.

**Key papers:**
- Marletto (2015), "Constructor Theory of Information," *Proc. R. Soc. A* — defines information without presupposing dynamics or scale. An "information variable" is a set of attributes that can be cloned and distinguished. Explicitly counterfactual: an object carries information only if it *could have been* in a different state.
- Marletto (2015), "Constructor Theory of Life," *J. R. Soc. Interface* — exact physics-level formulation of self-reproduction and natural selection. Knowledge is information that can act as a constructor and cause itself to remain instantiated. The only non-trivial condition: the laws of physics must allow digital information to be physically instantiated.
- Deutsch & Marletto (2025), "Constructor Theory of Time," arXiv:2505.08692.

**Key advantage:** Scale- and dynamics-independent. Unlike the no-cloning theorem (requires quantum theory) or the second law (requires macroscopic scale), constructor-theoretic laws hold at all scales without presupposing equations of motion.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | Medium-High. Axiomatic structure published in top journals, but not yet a computational calculus with derivation rules. |
| Computational | Very Low. A Python demonstration simulator exists (GitHub: gvelesandro/constructor-theory-simulator) but no agent implementations. |
| Beyond entropy | Counterfactuals as fundamental primitives. Substrate-independent information. Scale-free laws. |
| Key gap | No optimization calculus. No connection to gradient-based methods or any existing AI pipeline. |

---

### 2. Rosen's (M,R)-Systems and Organizational Closure

**Overview:** Robert Rosen's Metabolism-Repair systems (1950s–1991) use category theory to model organisms as systems "closed to efficient causation." Unlike machines, the repair mechanism is generated internally. Rosen showed this closure involves an impredicative set, meaning no finite Turing machine can fully simulate it.

**Key developments:**
- Louie extended Rosen's work in category theory, showing closure to efficient causation means certain mapping diagrams have no "largest model."
- Letelier, Soto-Andrade & Cárdenas demonstrated metabolic closure through functional closure equations in the category of sets.
- Montévil & Mossio (2015), "Biological Organisation as Closure of Constraints," *J. Theor. Biol.* — distinguished *processes* (changes in thermodynamic conditions) from *constraints* (entities that channel processes while remaining conserved). Closure: constraints mutually depend on and maintain each other.
- **Igamberdiev (2024)**, "Toward the Relational Formulation of Biological Thermodynamics," *Entropy* 26(1):43 — in systems closed to efficient causation, classical thermodynamic attractors including thermodynamic equilibrium and *the standard notion of thermodynamic entropy lose their validity*. A "teleonomic attractor" replaces equilibrium.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | High in categorical formulation. Closure-of-constraints is conceptually precise but less computationally explicit. |
| Computational | Very limited. Some computational realizations of (M,R)-systems exist. Rosen's non-computability thesis is controversial. |
| Beyond entropy | Organizational closure — the system produces its own conditions of existence. Igamberdiev: in these systems, *entropy itself ceases to be a valid state function*. |
| Key gap | Computational tractability. If non-computability is taken literally, (M,R)-systems cannot be simulated. Needs bridge theorems to implementable objectives. |

---

### 3. Category Theory as Metalanguage

**Overview:** Not so much an alternative to entropy as a *metalanguage* that can express both entropic and non-entropic concepts — potentially the most promising avenue for transcending the entropy-or-not dichotomy.

**Key programs:**

**Phillips & Wilson (2010)**, *PLoS Computational Biology*: Systematicity of cognition is a *necessary consequence* of categorical structure (adjunctions), not an accidental byproduct. Re-centers cognitive science from representational states to *relationships between transformations*.

**Spivak (Topos Institute)**: Operadic framework for composing dynamical systems using "wiring diagrams." The category **Poly** of polynomial endofunctors provides a natural framework for mode-dependent dynamical systems. Book with Niu: *Polynomial Functors: A Mathematical Theory of Interaction* (Cambridge, 2024).

**Smithe (Topos Institute, 2021–2024)**: Compositional active inference — the most direct bridge between category theory and agent architecture:
1. *Bayesian lenses*: Bayesian updating composes according to the lens pattern.
2. *Statistical games*: The chain rule of relative entropy is a strict section; maximum likelihood and free energy are lax sections.
3. *Open dynamical systems* as coalgebras of polynomial functors.
4. *Approximate inference doctrines* functorially relating statistical games to the dynamical systems that play them.

This work shows that the free energy principle has a precise compositional (functorial) structure — *not reducible to entropy alone* but involving the interplay of lenses, doctrines, and polynomial dynamics.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | Very high. Applied category theory (Spivak, Fong, Smithe, Patterson) has produced substantial formal results. |
| Computational | Emerging. AlgebraicJulia implements operadic frameworks. Smithe's work is formalized but not yet scaled. |
| Beyond entropy | Compositional metalanguage for assembling heterogeneous subsystems. Typed morphisms instead of scalar objectives. Adjunctions capture dualities that entropy flattens. |
| Key gap | Accessibility and scalability. No gradient-descent-friendly implementations. Large gap between elegant mathematics and practical agents. |

---

### 4. Pearl's Causal Models / Do-Calculus

**Overview:** Structural Causal Models (SCMs) formalize causal reasoning using DAGs, structural equations, and do-calculus — a complete set of rules for computing interventional distributions. The CHT proves SCMs are *strictly more expressive* than any purely statistical framework.

**Causal RL:** An active research program embedding causal knowledge into world models. Agents learn to perform interventions (active causal structure learning) and use SCMs for planning (Huang et al. 2024 survey; CRL Lab at Columbia).

**Wissner-Gross & Freer (2013) — Causal Entropic Forces:** Proposed that adaptive behavior emerges from maximizing "causal path entropy." However:
- Formally equivalent to empowerment in deterministic environments.
- The causal entropy as defined is state-independent; resulting force is zero for state-independent noise.
- Both causal entropy and empowerment agents prefer unstable fixed points but stay near them — limited behavioral diversity.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | Very high. Do-calculus is complete with rigorous proof theory. CHT is a genuine impossibility result. |
| Computational | High. Causal discovery algorithms, do-calculus engines (DoWhy, CausalNex), and causal RL are deployed. |
| Beyond entropy | Distinguishes *seeing* from *doing* from *imagining*. The CHT proves this is a fundamental, not just practical, advantage. |
| Key gap | SCMs are a *representational language*, not an *optimization objective*. You still need to choose what to optimize within that language. DAG discovery is exponentially hard. |

---

### 5. Topological / Geometric Approaches

**Overview:** Persistent homology and sheaf theory capture qualitative structural invariants invisible to entropy.

**Key results:**
- Persistent homology features matched or exceeded traditional features for predicting higher-order cognitive domains (cognition, emotion, personality) from brain dynamics.
- **Ghrist & Hansen**: "Discourse sheaves" — algebraic structures on networks representing communication modes including deception. The sheaf Laplacian generalizes the graph Laplacian, enabling topology-aware consensus dynamics. Objective: *global consistency of local data*, not entropy minimization.
- **Topological optimization**: Persistent homology as a loss function using subgradients, guiding gradient descent toward desired topological features (arXiv:2203.16748).

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | High. Algebraic topology and sheaf theory are well-established. Applied TDA has strong computational foundations. |
| Computational | Moderate-to-good. Libraries: GUDHI, Ripser, PyTDA. Sheaf Laplacians have been computed. |
| Beyond entropy | Qualitative structural invariants (holes, voids, connectivity). Global inconsistency detection. Invariance under continuous deformation. |
| Key gap | No coherent theory of *topological objectives for agents*. TDA is primarily descriptive/analytical, not prescriptive. |

---

### 6. Constraint Satisfaction over Heterogeneous Types (HoTT)

**Overview:** Homotopy Type Theory unifies logic, topology, and computation. Types are spaces; equalities are paths. Voevodsky's univalence axiom identifies equivalent types.

**Relevance:** In principle, HoTT could provide a single type-theoretic language where metric, algebraic, topological, and causal constraints coexist through typed morphisms rather than being flattened to a scalar. The univalence axiom ensures equivalent formulations are interchangeable.

**MetaMo (2024–2025):** Combines category theory, functional analysis, and topology to support open-ended agents that self-modify their own goals — perhaps the closest existing attempt.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | Very high (Fields Medal-adjacent). Extremely low for agent applications. |
| Computational | HoTT has proof assistants (Agda, Coq). Zero agent optimization frameworks. |
| Beyond entropy | Heterogeneous constraint unification. Principled switching between constraint representations. |
| Key gap | Everything practical. No agent architecture, no gradient computation, no worked examples. Most powerful mathematics, least operational. |

---

### 7. Other Candidates

#### 7a. Assembly Theory (Cronin)

Measures complexity by "assembly index" — minimal construction steps from basic blocks — combined with copy number. Published in *Nature* (2023).

**Devastating critique:** Zenil et al. (2024, *PLOS Complex Systems*) demonstrated the assembly index is mathematically equivalent to LZ compression (ZIP, GZIP). An object with low assembly index has low Shannon entropy and high compressibility, in direct proportion.

**Verdict:** Does not escape the entropic valley — it *is* the entropic valley, rebranded.

#### 7b. Computational Mechanics (Crutchfield)

Defines "causal states" as equivalence classes of histories yielding the same conditional distribution over futures. The epsilon-machine is the minimal, unique representation of a process's causal structure. Key distinction: *entropy rate measures randomness; statistical complexity measures structure* — and these are independent quantities.

| Dimension | Assessment |
|-----------|-----------|
| Math maturity | High. |
| Computational | Moderate. Epsilon-machine reconstruction (CSSR algorithm) exists. |
| Beyond entropy | Explicitly separates randomness from structure. |
| Key gap | Primarily descriptive. No one has used statistical complexity as an agent optimization objective. |

#### 7c. Integrated Information Theory (Tononi)

IIT 4.0 (2023) measures "integrated information" (Φ) capturing intrinsic causal power.

**Problems:** Aaronson showed IIT assigns unbounded consciousness to simple logic gate arrays. Computing Φ is NP-hard. Characterized by some scholars as unfalsifiable.

**Verdict:** Captures something entropy cannot (intrinsic causal power of a partition) but scalability is a fatal problem and the theory is contested.

#### 7d. Autopoiesis Formalized

Maturana & Varela's autopoiesis (1972) has been formalized categorically by Nomura and connected to (M,R)-systems by Letelier et al. A 2024 study reconsidered whether topological boundary formation is strictly necessary.

**Verdict:** Categorical formalizations exist but are thin — they demonstrate autopoiesis *can* be represented categorically but don't yet derive deep consequences.

---

### Comparative Assessment

| Framework | Math | Compute | Beyond entropy | Key gap |
|-----------|:----:|:-------:|----------------|---------|
| Constructor Theory | ★★★☆ | ★☆☆☆ | Counterfactuals, scale-free | No optimization calculus |
| (M,R) / Closure | ★★★★ | ★☆☆☆ | Entropy invalidation | Non-computability |
| Category Theory | ★★★★★ | ★★☆☆ | Compositionality, types | No gradient methods |
| Pearl's SCMs | ★★★★★ | ★★★★ | Interventions, CHT | Not an objective |
| Topological | ★★★★ | ★★★☆ | Qualitative invariants | No agent theory |
| HoTT | ★★★★★ | ☆☆☆☆ | Heterogeneous constraints | Everything practical |
| Assembly Theory | ★☆☆☆ | ★★★☆ | Nothing (≡ LZ compression) | Not an alternative |
| Comp. Mechanics | ★★★★ | ★★★☆ | Structure ≠ randomness | Descriptive only |
| IIT | ★★☆☆ | ★☆☆☆ | Intrinsic causal power | NP-hard, contested |

---

## Synthesis: Implications for Vitality

### What This Means for the Vitality Framework

The Vitality project (Version 2) defines lifelikeness through three components: viability (set-based), vitality (bidirectional empowerment-plasticity coupling via harmonic mean of morphogens E_t and P_t), and NTIC audit (non-trivial information closure). The critique and this follow-up research have direct implications:

1. **Vitality's harmonic mean V_t(λ) = 2E_tP_t/(E_t + P_t) is an entropic objective.** Both E_t (empowerment) and P_t (plasticity) are mutual information quantities. The V_t score inherits all the limitations catalogued above: scalar structural impoverishment, causal blindness, and intractability at scale. If representations are discretized (e.g., via VQ-VAE codebook of agent states), the intractability softens but the causal and structural limitations remain.

2. **NTIC as a third-person audit is the right instinct.** The critique shows that any purely first-person entropic objective will admit trivial-closure pathologies. The NTIC audit functions as a proto-causal check — it verifies that internal dynamics carry world-structure, not just statistical correlation. But NTIC as currently defined (a scalar in [0,1]) may itself be insufficient. A *causal* NTIC — verifying interventional, not just associational, coupling — would be strictly stronger.

3. **The morphogen internalization (E_t, P_t) is a step toward the right architecture.** The slow morphogens modulating the fast loop resemble the "connectionist bottom / structured top" hybrid that Q1 identifies as viable. The key question is whether the top layer's objective can be enriched beyond MI.

---

## Interventional Vitality: Upgrading Empowerment and Plasticity to Layer 2

### The Problem with Associational Empowerment

Vitality V2 defines empowerment and plasticity as mutual information quantities:

- **Empowerment:** E_t(lambda) := I(A -> O; lambda)_t — channel capacity from actions to observations
- **Plasticity:** P_t(lambda) := I(O -> A; lambda)_t — channel capacity from observations to actions

Both are **Layer 1 (associational)** quantities in Pearl's causal hierarchy. They measure statistical dependence, not causal influence. The Causal Hierarchy Theorem (Bareinboim et al. 2022) proves that associational and interventional quantities are *generically different* — the set of causal models where they coincide has Lebesgue measure zero.

This means Vitality V2's core score V_t = 2E_tP_t/(E_t + P_t) can be inflated by:

- **Confounded coupling:** A shared environmental process Z drives both the agent's actions and future observations (Z -> A and Z -> O). Standard empowerment registers this as agent influence.
- **Environmental drift mimicry:** If autonomous environmental dynamics happen to correlate with the agent's action patterns (e.g., both follow periodic cycles), standard empowerment is nonzero even when the agent has zero causal effect.
- **Passive observation inflation:** In multi-agent settings, an agent that merely *observes* other agents' effects on the environment can have high standard empowerment, because its observations are informative about the world — but its *actions* cause nothing.

These are precisely the kinds of pathologies that Vitality's NTIC audit is meant to catch. But NTIC as currently defined is itself an associational quantity. A causal upgrade is needed at the foundation.

### Existing Causal Influence Measures

The mathematical machinery for interventional empowerment already exists, scattered across several research programs:

**Ay & Polani (2008), "Information Flows in Causal Networks," *Advances in Complex Systems* 11(1).** Define **causal information flow** using Pearl's do-operator. Their information flow from a set of source nodes C to target j is:

> IF(C -> j) = sum over x_C of p(x_C) * D_KL( P(x_j | do(x_C)) || P(x_j | do()) )

This uses the interventional distribution P(x_j | do(x_C)), which severs incoming edges to the source variable, eliminating confounding. Ay and Polani show that their information flow and transfer entropy coincide when there is no confounding, but **diverge when there are hidden common causes** — exactly the regime where the distinction matters.

**Janzing et al. (2013), "Quantifying Causal Influences," *Annals of Statistics* 41(5).** Define causal strength as a KL divergence between the original joint distribution and the distribution when a specific edge is "cut" (replaced by noise). This is an edge-specific measure, not a channel capacity, but shares the interventional foundation.

**Simoes et al. (2024), "Fundamental Properties of Causal Entropy and Information Gain," *PMLR* 236.** Define **causal entropy** H(Y | do(X)) and **causal information gain** — the reduction in uncertainty about Y when intervening on X. They prove that causal information gain can be *negative* (unlike standard MI), meaning that intervening on certain variables can increase uncertainty. This has direct implications: in confounded systems, the agent's actual causal information gain may be *less* than standard MI suggests.

**Cao et al. (2025), "Towards Empowerment Gain through Causal Structure Learning in Model-Based RL," arXiv:2502.10077.** The Empowerment through Causal Learning (ECL) framework combines causal structure learning with empowerment maximization, using learned causal graphs to compute empowerment over genuine causal pathways rather than confounded associations. This is the closest published work to interventional empowerment, though it does not define the formal quantity.

**Yiu et al. (2025), "Empowerment Gain and Causal Model Construction," *Philosophical Transactions A* (accepted).** From Gopnik's lab. Proposes a bidirectional link: accurate causal world models increase empowerment, and empowerment-maximizing exploration leads to better causal models. Cognitive science justification for why empowerment and causal structure are tightly coupled.

### The Gap: Nobody Has Written Down the Definition

Despite all this machinery, no published paper defines "interventional empowerment" as a named quantity. The components exist (Pearl's do-calculus, Ay-Polani information flow, Klyubin-Polani empowerment, Abel et al.'s directed information framework), but nobody has combined them. This is the contribution.

### Formal Definition: Interventional Empowerment

Using Pearl's truncated factorization — where do(A = a) severs all incoming edges to A and fixes its value — we define:

> **Definition (Interventional Empowerment).** The interventional empowerment of agent lambda at time t is:
>
> E^do_t(lambda) := max_{p(a)} I_do(A; O)
>
> where I_do(A; O) := sum_{a,o} P(o | do(a)) * p(a) * log[ P(o | do(a)) / P_do(o) ]
>
> and P_do(o) = sum_a p(a) * P(o | do(a)) is the marginal under intervention.

The key difference from standard empowerment: **P(O | do(A)) replaces P(O | A).** The do-operator severs confounding paths, isolating the genuine causal channel from actions to observations.

### Formal Definition: Interventional Plasticity

Symmetrically:

> **Definition (Interventional Plasticity).** The interventional plasticity is:
>
> P^do_t(lambda) := max_{p(o)} I_do(O; A)
>
> where I_do(O; A) uses P(a | do(o)) — the distribution over actions when observations are *intervened upon* rather than merely conditioned on.

This measures the agent's genuine causal responsiveness to environmental inputs. A puppet whose actions are driven by an external controller has high *associational* plasticity (its actions correlate with observations) but low *interventional* plasticity (the observations are not the *cause* of its actions — the controller is).

### Interventional Vitality

> **Definition (Interventional Vitality).** The interventional Vitality score at time t is:
>
> V^do_t(lambda) := 2 * E^do_t * P^do_t / (E^do_t + P^do_t)

The harmonic mean structure is preserved. The interpretation shifts: V^do_t measures the agent's balanced capacity for **genuine causal influence** (not just correlation) and **genuine causal responsiveness** (not just puppetry).

### Interventional Morphogens

The slow morphogens internalize the interventional quantities:

> E^do_{t+1} = (1 - alpha_E) * E^do_t + alpha_E * E^do_t(lambda)
>
> P^do_{t+1} = (1 - alpha_P) * P^do_t + alpha_P * P^do_t(lambda)

First-person time is now constituted by the agent's *causal* influence and *causal* responsiveness, not mere statistical coupling.

### Interventional NTIC

The NTIC audit strengthens naturally:

> **Definition (Causal NTIC).** NTIC^do_t(lambda) measures the non-triviality of the agent's information closure using interventional distributions. The agent passes the causal NTIC audit if its internal dynamics carry world-structure through genuine causal pathways — not through confounders, not through passive correlation.

Formally, replace the information flow J(W -> Y)_t := I(W_t; Y_{t+1} | Y_t) with its interventional counterpart:

> J^do(W -> Y)_t := I(do(W_t); Y_{t+1} | Y_t)

This measures how much *intervening* on the world state changes the agent's internal state — genuine causal coupling, not spurious association.

### What This Excludes

| Pathology | Standard Vitality | Interventional Vitality |
|-----------|:-:|:-:|
| Confounded coupling (shared Z drives A and O) | Inflated E_t, false positive | E^do_t = 0 correctly |
| Environmental drift mimicry (correlated cycles) | Inflated E_t | E^do_t = 0 correctly |
| Passive observer in multi-agent setting | Inflated E_t | E^do_t = 0 correctly |
| Puppet (external controller drives A) | Inflated P_t | P^do_t = 0 correctly |
| Simulator cave (internal model decoupled from world) | May pass NTIC | Fails causal NTIC |

### Why Klyubin-Polani Didn't Need This

In the original gridworld experiments (Klyubin, Polani & Nehaniv 2005, 2008), the environment was fully observable, deterministic, single-agent, with no hidden common causes. Under these conditions, P(O|A) = P(O|do(A)) automatically — there is nothing to confound. The distinction only matters in richer, more realistic settings: partial observability, multi-agent environments, autonomous environmental dynamics, learned policies from confounded datasets.

Abel et al. (2025), "Plasticity as the Mirror of Empowerment" (*NeurIPS 2025*, arXiv:2505.10361), which provides the tradeoff geometry for Vitality V2, explicitly uses Generalized Directed Information (temporal, not interventional). They acknowledge that temporal ordering is not a guarantee of causal identification. Upgrading from GDI to interventional directed information would preserve the tradeoff theorem while grounding it causally.

### Identification and Tractability

In practice, P(O | do(A)) may not be directly observable. Three identification strategies:

1. **Backdoor adjustment:** If the causal graph is known and a sufficient adjustment set Z exists, then P(O | do(A)) = sum_z P(O | A, z) P(z). This is computable from observational data.
2. **Frontdoor adjustment:** If there is a mediator M on the causal path A -> M -> O, interventional distributions can be recovered even without observing confounders.
3. **Actual interventions:** The agent can *experiment* — perform randomized actions and observe outcomes. This is the most direct approach and connects to the exploration-exploitation literature. An agent that actively experiments to estimate its own interventional empowerment is performing causal structure learning.

Strategy (3) is particularly natural for Vitality: a vital agent should be one that *tests its own causal influence* rather than passively assuming it.

### Key References for Interventional Vitality

- Ay & Polani (2008), "Information Flows in Causal Networks," *Advances in Complex Systems*
- Pearl (2000/2009), *Causality*, Cambridge University Press
- Bareinboim et al. (2022), "On Pearl's Hierarchy," ACM Books
- Janzing et al. (2013), "Quantifying Causal Influences," *Annals of Statistics*
- Simoes et al. (2024), "Causal Entropy and Causal Information Gain," *PMLR* 236
- Cao et al. (2025), "Empowerment through Causal Structure Learning," arXiv:2502.10077
- Yiu et al. (2025), "Empowerment Gain and Causal Model Construction," *Phil. Trans. A*
- Abel et al. (2025), "Plasticity as the Mirror of Empowerment," arXiv:2505.10361
- Tiomkin, Salge & Polani (2025), "Process Empowerment," *J. Phys. Complexity*
- Rosas et al. (2020), "Causal Blankets," in *Active Inference*, Springer
- Klyubin, Polani & Nehaniv (2005), "Empowerment," *IEEE CEC*
- Schreiber (2000), "Measuring Information Transfer," *Phys. Rev. Lett.*

---

## Constructor-Theoretic Vitality: From Bits to Possibilities

### Motivation: Why Leave Information Theory?

Even with the interventional upgrade above, Vitality remains an information-theoretic quantity — it counts bits of causal influence. The deeper question from the critique is whether *bits* are the right unit at all. Constructor theory offers a radical alternative: instead of measuring how much information flows through the agent's causal channels, measure the *richness of transformations the agent keeps possible*.

### Constructor Theory: Core Definitions

Constructor theory (Deutsch 2013, *Synthese* 190(18); Marletto 2015a, 2015b) reformulates physics as follows:

**Task.** A task T is an ordered pair of input/output attributes: T = {a -> b}, meaning "transform substrate from attribute a to attribute b." More generally, T can be a set of such pairs.

**Constructor.** A constructor C for task T is an entity that (i) causes T to occur on the substrate, and (ii) retains the capacity to cause T again. The constructor is not consumed or degraded in a way that prevents reuse. Formally: for every epsilon > 0, C transforms the substrate from a to b with accuracy at least 1 - epsilon and can do so an unlimited number of times.

**Possible task.** T is possible if the laws of physics permit a constructor for T to exist. **Impossible task.** T is impossible if no constructor for T can exist, and the laws must explain why.

**Key property:** The distinction is *absolute* — it does not depend on initial conditions, probability distributions, or available resources. A task may be possible even if no actual constructor for it has ever been built.

### Constructor Theory of Information (Marletto 2015)

Marletto defines information without presupposing probability or dynamics:

**Information variable.** A set of attributes {x_1, x_2, ..., x_n} of a physical substrate such that:
1. **Distinguishability:** For every pair x_i, x_j, the task of distinguishing them is possible.
2. **Copiability (Cloning):** For each x_i, the task {x_i tensor b -> x_i tensor x_i} is possible (copying onto an auxiliary substrate without destroying the original).

This replaces Shannon's probabilistic framework entirely. A set of states is an information variable iff those states can be reliably told apart and reliably copied. No probability measure required.

**Superinformation medium.** A substrate supporting information variables whose full set of attributes cannot all be simultaneously copied. Quantum systems are superinformation media — elegantly capturing quantum information theory without Hilbert space formalism as foundation.

### Constructor Theory of Life (Marletto 2015)

**Self-reproducer.** An entity S is a self-reproducer if it can cause the transformation {m -> S} where m is raw material, and S retains its ability to do so again.

**Knowledge (constructor-theoretic).** Information that has the property of *causing itself to remain instantiated* in physical substrates. A gene is knowledge: its physical instantiation in a cell causes biochemical processes that copy the gene. A scientific theory in a book is knowledge: it causes people to re-copy, teach, and preserve it. Knowledge is not defined by a knowing subject but by causal self-perpetuation.

### Reformulating Empowerment: From Channel Capacity to Constructor Repertoire

Standard empowerment asks: "How many bits can I push through the action-observation channel?"

Constructor-theoretic empowerment asks: **"How many tasks can I perform as a constructor?"**

> **Definition (Constructor Repertoire).** The constructor repertoire of agent A at time t is:
>
> R_C(A, t) = { T : A can perform task T as a constructor on substrates in environment E }
>
> Each task T in R_C is a transformation {a -> b} that the agent can cause while retaining its own capacity to act further.

> **Definition (Constructor-Theoretic Empowerment).**
>
> E-hat_t = mu( R_C(A, t) )
>
> where mu is an appropriate measure on the space of tasks (cardinality for finite discrete cases, a measure-theoretic treatment for continuous cases).

**Why this is a natural translation.** Shannon empowerment measures how many distinguishable futures the agent can bring about. Constructor-theoretic empowerment measures how many distinguishable transformations the agent can cause as a constructor. The conceptual shift:

- **Shannon:** "How many bits flow through my action-observation channel?"
- **Constructor-theoretic:** "How many tasks do I keep in the *possible* category?"

**Built-in viability.** The constructor definition *requires* that the agent survive its own actions (retain capacity to act again). This automatically excludes suicidal or self-destroying actions from the empowerment count — encoding viability without needing it as a separate axiom.

**Graded version.** Let alpha(A, T) be the maximum accuracy with which agent A can perform task T. Then:

> E-hat_t = integral over T in task-space of alpha(A, T) d_mu(T)

An agent with high graded empowerment can perform many tasks with high reliability.

### Reformulating Plasticity: From Reverse Channel to Reconstructibility

Standard plasticity asks: "How many bits flow from observations to actions?"

Constructor-theoretic plasticity asks: **"How many transformations can be performed on me without destroying my capacity to act?"**

> **Definition (Reconstructibility Set).** The reconstructibility set of agent A at time t is:
>
> R_S(A, t) = { T : T can be performed on A as substrate, and after T, A remains a constructor with R_C(A') nonempty }
>
> That is, R_S is the set of transformations the environment can impose on the agent such that the agent emerges still capable of performing tasks.

> **Definition (Constructor-Theoretic Plasticity).**
>
> P-hat_t = mu( R_S(A, t) )

**Interpretation.** High plasticity means the agent can be perturbed in many ways and still recover its constructor status — robustness under transformation.

**Stronger version.** Require not just non-empty but substantially preserved repertoire:

> R_S^(theta)(A, t) = { T : T performed on A implies mu(R_C(A')) >= theta * mu(R_C(A)) }

where theta in (0,1] is a preservation threshold. A truly plastic system retains most of its capabilities under perturbation.

### Constructor-Theoretic Vitality

**Proposal 1: Harmonic-mean analog.**

> V-hat_t = 2 * E-hat_t * P-hat_t / (E-hat_t + P-hat_t)

Preserves the original mathematical form while shifting operands from MI quantities to task-set measures. The harmonic mean still penalizes imbalance: an agent with many capabilities but no tolerance for perturbation (or vice versa) has low Vitality.

**Proposal 2: Joint closure condition.**

> V-hat_t = mu( R_C(A, t) x R_S(A, t) )

The Vitality of an agent is the size of the *product* of its constructor repertoire and its reconstructibility set — capturing the idea that empowerment and plasticity must be jointly maintained.

**Proposal 3: The Vitality Condition.** Perhaps the deepest reformulation is not a scalar but a *condition*. Agent A satisfies the Vitality Condition if:

(a) R_C(A) is nonempty — it is a constructor, it can do things.

(b) R_S(A) is large enough that environmental perturbations generically preserve (a).

(c) Exercising tasks in R_C does not generically shrink R_S — acting does not make the agent fragile.

(d) Undergoing transformations in R_S does not generically shrink R_C — being perturbed does not make the agent impotent.

Conditions (c) and (d) together capture **co-maintenance**: empowerment and plasticity sustain each other. This is a form of closure reminiscent of Rosen's (M,R)-systems but stated in purely constructor-theoretic terms.

**Single-sentence reformulation:**

> *Constructor-Theoretic Vitality is the measure of how many tasks an agent keeps in the "possible" category — both tasks it can perform and tasks that can be performed on it without destroying its capacity to act.*

### Non-Trivial Constructive Closure (NTCC): The Constructor-Theoretic NTIC

NTIC in Vitality V2 distinguishes genuine agents from passively correlated systems. In constructor-theoretic terms:

> **Definition (NTCC).** Agent A satisfies Non-Trivial Constructive Closure if its internal subsystems form a closed constructive network — each internal constructor is maintained by other internal constructors, and this network is not reducible to passive correlation.

Formally, let {C_1, C_2, ..., C_n} be the internal subsystems of A. NTCC requires:

1. **Internal constructive activity:** There exist tasks T_ij such that C_i acts as a constructor for T_ij on substrate C_j. The internal parts build and maintain each other.

2. **Non-triviality:** The set of internal tasks {T_ij} is not reducible to a single task of copying external states. The agent is not merely a mirror or recorder.

3. **Closure:** Every C_i that degrades is reconstructed by some other C_j (or combination). This is the constructor-theoretic analog of Rosen's closure to efficient causation.

**Contrast with passive systems.** A thermostat correlates with temperature but performs no internal constructive activity — it fails NTCC. A living cell contains ribosomes (constructors building proteins), DNA (constructor templating RNA), membranes (constructors maintaining compartmentalization) — a rich network of internal constructive tasks. It satisfies NTCC.

### Morphogens as Knowledge

In Deutsch-Marletto's sense, **knowledge** is information that causes itself to remain instantiated. The claim is that the Vitality morphogens E_t and P_t are knowledge in this precise sense:

- A high E_t (rich constructor repertoire) is information instantiated in the agent's structure that causes transformations in the environment — which sustains the conditions for the agent's continued existence — which sustains the instantiation of that very information.
- A high P_t (rich reconstructibility) is information instantiated in the agent's architecture that causes the agent to absorb perturbations and recover — which sustains the agent's physical medium — which is where P_t is instantiated.

Both morphogens satisfy the knowledge criterion: they are information that causes itself to persist. The conjecture is that the **transition from non-lifelike to lifelike** corresponds to the point at which E_t and P_t become causally entangled with their own persistence — crossing a **knowledge threshold** from passive information (carried along by external dynamics, like a leaf in a stream) to active knowledge (causing its own continuation, like a beaver damming a stream to maintain its habitat).

### Connection to Rosen's (M,R)-Systems

The parallel between constructor-theoretic Vitality and Rosen's framework is deep:

| Concept | Rosen's (M,R)-Systems | Constructor-Theoretic Vitality |
|---------|----------------------|-------------------------------|
| Central property | Closure to efficient causation | Non-Trivial Constructive Closure (NTCC) |
| Formal language | Category of sets and mappings | Constructor-theoretic task algebra |
| Question asked | "Is the system closed?" (binary) | "How rich is the constructive closure?" (graded) |
| Computability | Non-computable (Rosen's claim) | Approximate constructors to arbitrary accuracy |
| Scope | Classical, exact | Quantum-compatible (superinformation), approximate |
| Empirical contact | Minimal | Potentially measurable via task repertoire |

A constructor-theoretic Vitality framework could be a *quantified, physically grounded, approximate* version of Rosen's qualitative insight. Where Rosen asks "is the system closed to efficient causation?" (yes/no), Vitality asks "how rich is the constructive closure?" and answers with V-hat_t.

### Constructor-Theoretic Time and First-Person Experience

Vitality V2 claims that the morphogens E_t, P_t *constitute* the agent's first-person temporal experience. In constructor-theoretic terms, this maps naturally:

- **First-person time as task execution.** Each moment of the agent's experience corresponds to performing tasks (empowerment: acting on the environment) and being transformed (plasticity: being acted upon while retaining constructor status). The succession of these events *is* the agent's time.
- **Irreversibility grounds directionality.** The constructor-theoretic account of thermodynamic irreversibility — certain transformations are possible but their reversal is impossible — provides the arrow of time without invoking probability or initial conditions. The asymmetry between possible and impossible tasks gives temporal experience its directional character.
- **Temporal richness.** One might define the "thickness" of the agent's present: tau_t = mu({T : T is currently being performed by or on A}). A richer present — more tasks simultaneously underway — corresponds to a more vivid temporal experience.

### Open Problems

1. **The measure mu.** What is the right measure on task-space? In finite discrete cases, cardinality suffices. In continuous cases, constructor theory does not yet provide a natural measure. This is the deepest technical challenge.

2. **Composition.** How does the Vitality of a composite system relate to the Vitality of its parts? Biological organisms are hierarchically organized. A full framework needs composition laws — potentially via Spivak's operadic machinery.

3. **Convergence to Shannon.** Under what conditions does V-hat_t reduce to the original V_t = 2E_tP_t/(E_t + P_t)? Conjecture: when the agent's tasks correspond to communication channels and the accuracy structure is sharp (binary possible/impossible), the constructor-theoretic measure converges to the Shannon measure.

4. **Empirical testability.** How would one measure E-hat and P-hat for a real organism? The task-repertoire of a bacterium is enormous. Approximation schemes and coarse-graining methods are needed.

5. **Quantum Vitality.** Constructor theory handles quantum information natively. Could there be quantum contributions to Vitality — tasks possible only because of entanglement or superposition?

### Key References for Constructor-Theoretic Vitality

- Deutsch (2013), "Constructor Theory," *Synthese* 190(18), 4331-4359
- Marletto (2015), "Constructor Theory of Information," *Proc. R. Soc. A* 471(2174)
- Marletto (2015), "Constructor Theory of Life," *J. R. Soc. Interface* 12(104)
- Deutsch & Marletto (2025), "Constructor Theory of Time," arXiv:2505.08692
- Rosen (1991), *Life Itself*, Columbia University Press
- Montévil & Mossio (2015), "Biological Organisation as Closure of Constraints," *J. Theor. Biol.* 372
- Igamberdiev (2024), "Relational Biological Thermodynamics," *Entropy* 26(1):43
- Klyubin, Polani & Nehaniv (2005), "Empowerment," *IEEE CEC*
- Louie, A.H., "More Than Life Itself: A Synthetic Continuation in Relational Biology"
- Letelier, Soto-Andrade & Cárdenas, "Organizational Invariance and Metabolic Closure"

---

### Roadmap: Putting It Together

The two extensions above — Interventional Vitality and Constructor-Theoretic Vitality — sit at different levels of ambition:

**Near-term (Interventional Vitality):** A direct upgrade to V2 that preserves the mathematical form (harmonic mean, morphogen internalization, NTIC audit) while replacing associational MI with interventional MI via do-calculus. This is publishable now — all the mathematical machinery exists; only the assembly is new.

**Medium-term (categorical structure):** Express the interventional Vitality framework in Smithe's compositional active inference language — morphogen dynamics as polynomial functor coalgebras, the empowerment-plasticity tradeoff as a statistical game with adjoint structure. This would make the compositionality explicit and could reveal structural constraints invisible to the scalar formulation.

**Long-term (Constructor-Theoretic Vitality):** A fundamental reformulation where Vitality is not about bits but about the richness of the agent's constructive relationship with its environment. Requires resolving the measure problem and building bridges to existing formalisms. But if successful, it would ground Vitality in physics rather than in information theory — making the framework as deep as its ambitions.

---

## Key Sources

### Question 1
- McAllester & Stratos (2020), "Formal Limitations on MI Measurement," AISTATS
- Bareinboim et al. (2022), "On Pearl's Hierarchy and Causal Inference"
- Templeton et al. (2024), "Scaling Monosemanticity," Anthropic
- Van den Oord et al. (2017), "Neural Discrete Representation Learning" (VQ-VAE)
- Ellis et al. (2021), "DreamCoder," PLDI
- Scannell et al. (2025), "Discrete Codebook World Models," ICLR
- Williams & Beer (2010), Partial Information Decomposition
- Parvizi-Wayne (2024), "What Active Inference Still Can't Do"
- Deleu & Bengio et al. (2022), "Bayesian Structure Learning with GFlowNets"
- Schölkopf et al., Causal Representation Learning

### Question 2
- Deutsch (2013), "Constructor Theory," arXiv:1210.7439
- Marletto (2015), "Constructor Theory of Information," Proc. R. Soc. A
- Marletto (2015), "Constructor Theory of Life," J. R. Soc. Interface
- Rosen (1991), *Life Itself*
- Montévil & Mossio (2015), "Biological Organisation as Closure of Constraints," J. Theor. Biol.
- Igamberdiev (2024), "Relational Biological Thermodynamics," Entropy 26(1):43
- Phillips & Wilson (2010), "Categorial Compositionality," PLoS Comp. Biol.
- Niu & Spivak (2024), *Polynomial Functors*, Cambridge
- Smithe (2021–2024), Compositional Active Inference I & II, arXiv
- Pearl (2009), *Causality*, 2nd ed.
- Hansen & Ghrist, "Opinion Dynamics on Discourse Sheaves," SIAM
- Shalizi & Crutchfield, "Computational Mechanics"
- Zenil et al. (2024), "Assembly Theory ≈ LZ Compression," PLOS Complex Systems
- Albantakis et al. (2023), "IIT 4.0," PLoS Comp. Biol.
- Biehl et al. (2021), "Technical Critique of FEP," Entropy

### Interventional Vitality
- Ay & Polani (2008), "Information Flows in Causal Networks," *Advances in Complex Systems*
- Janzing et al. (2013), "Quantifying Causal Influences," *Annals of Statistics*
- Simoes et al. (2024), "Causal Entropy and Causal Information Gain," *PMLR* 236
- Cao et al. (2025), "Empowerment through Causal Structure Learning," arXiv:2502.10077
- Yiu et al. (2025), "Empowerment Gain and Causal Model Construction," *Phil. Trans. A*
- Abel et al. (2025), "Plasticity as the Mirror of Empowerment," arXiv:2505.10361
- Tiomkin, Salge & Polani (2025), "Process Empowerment," *J. Phys. Complexity*
- Rosas et al. (2020), "Causal Blankets," in *Active Inference*, Springer

### Constructor-Theoretic Vitality
- Deutsch & Marletto (2025), "Constructor Theory of Time," arXiv:2505.08692
- Louie, A.H., "More Than Life Itself," Ontos Verlag
- Letelier, Soto-Andrade & Cárdenas, "Organizational Invariance and Metabolic Closure"
- Klyubin, Polani & Nehaniv (2005/2008), Empowerment papers, *IEEE CEC* and *PLoS ONE*
