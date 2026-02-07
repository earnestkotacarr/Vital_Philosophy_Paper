# Two Sharp Critiques of Current Approaches to Autonomy and Cognition

## The Problem

Contemporary frameworks for general principles of autonomy and cognition — active inference, cognitive dynamic systems, empowerment maximization, predictive coding, and their relatives — share two structural deficiencies that prevent them from achieving what they claim to achieve. These are not minor objections. They are foundational gaps.

---

## Critique 1: The Missing Symbolic Layer

### The Historical Wrong Turn

Good Old-Fashioned AI (GOFAI) failed for well-understood reasons: handcrafted representations were brittle, expert systems didn't scale, and the knowledge acquisition bottleneck proved fatal. The field correctly moved on.

But in rejecting GOFAI, the field threw out the baby with the bathwater. What was discarded was not just handcrafted ontologies and brittle rule systems — it was *symbolic manipulation itself*. Turing machines, discrete combinatorial structure, compositional generativity — all of this was collapsed into subsymbolic dynamics under the connectionist paradigm and its successors (dynamical systems theory, probabilistic graphical models, deep learning, active inference).

### What Was Lost

Without a symbolic layer, you lose **creative permutation** — the ability to take known structures and recombine them into novel configurations that have never been encountered in training data or evolutionary history. Specifically:

- **Compositionality**: If A relates to B and B relates to C, symbolic systems derive A's relation to C. Subsymbolic systems must learn this from examples.
- **Abstraction**: Symbolic systems can operate on *classes* of relations (all commutative operations, all partial orders). Subsymbolic systems operate on instances.
- **Counterfactual reasoning**: "What would happen if this constraint were replaced by that one?" requires manipulating structural descriptions, not propagating activations.
- **Proof and verification**: Determining whether a system of constraints is satisfiable, or whether two constraint systems are equivalent, is a symbolic/algebraic operation.

### The Connectionist Seduction

The connectionist paradigm offers a seductive trade: abandon symbols, and you gain the ability to use probabilities *all the way up* — from low-level perception through mid-level representation to high-level cognition. No discrete-continuous interface problem. No symbol grounding problem. Everything is continuous, differentiable, and (in principle) learnable.

This continuity is why we get cheap wins with measures like **empowerment** (channel capacity between actions and future states) and why **predictive coding** can be applied at every level of a cortical hierarchy without worrying about where symbols begin and perception ends. The entire stack is homogeneous.

But homogeneity is precisely the problem. Cognition is *not* homogeneous. The operations that matter at higher levels — planning, analogy, constraint satisfaction, causal reasoning, mathematical proof — are *structurally different* from the operations that matter at lower levels. Trying to implement algebraic reasoning in a system that only has gradient descent is like trying to do arithmetic with a thermostat. You can approximate it for specific cases, but you cannot capture the generative structure.

### The Real Lesson of GOFAI

The failure of GOFAI was not a failure of symbols. It was a failure of *handcrafted representations* and *closed-world assumptions*. The symbols themselves — discrete, composable, manipulable structures — are not the problem. They are the solution to a problem that subsymbolic systems cannot solve: the problem of *structural creativity*.

What is needed is not a return to GOFAI, but a framework in which:
1. Representations are *learned* (not handcrafted), addressing the knowledge acquisition bottleneck
2. Symbolic structure *emerges* from or is *grounded in* subsymbolic dynamics, addressing the grounding problem
3. Once extracted, symbolic structures can be *manipulated combinatorially*, addressing the generativity problem

This is not a novel observation — it is the core aspiration of neurosymbolic AI. But it has not been achieved, and the dominant theoretical frameworks (active inference, predictive coding, empowerment) do not even attempt it because they have committed to the subsymbolic-all-the-way-up architecture.

---

## Critique 2: The Entropic Optimization Function Cannot Be the Highest-Level Objective

### The Convergence Toward Entropy

A striking number of current frameworks converge on information-theoretic or entropic objective functions at their highest level:

| Framework | Highest-Level Objective |
|-----------|------------------------|
| Free Energy Principle | Minimize variational free energy (KL divergence bound) |
| Active Inference | Minimize expected free energy (epistemic + pragmatic) |
| Empowerment | Maximize channel capacity between actions and states |
| InfoMax | Maximize mutual information |
| Cognitive Dynamic Systems (Haykin) | Minimize entropy of state estimate |
| Maximum Entropy Production | Maximize entropy production rate |
| Predictive Coding | Minimize prediction error (precision-weighted) |

This convergence suggests either a deep truth or a deep confusion. It is a deep confusion.

### Why Information Theory Cannot Be the Foundation

#### 1. Information presupposes the representation problem is solved

To compute any information-theoretic quantity — entropy, mutual information, KL divergence — you must first have:
- A well-defined set of random variables
- A well-defined probability space over those variables
- A well-defined measure (probability distribution)

But choosing the right variables is the hard problem. What should the state space be? What are the relevant observables? What counts as a signal versus noise? These are the foundational questions of any theory of autonomy, and information theory *assumes they are already answered*. It quantifies uncertainty over a space that someone else has already defined.

This is not a technical limitation that better mathematics will fix. It is a *conceptual circularity*: the theory that is supposed to explain how agents carve the world into relevant variables requires that the world already be carved into relevant variables.

#### 2. Information-theoretic objectives are computationally intractable

Computing mutual information in high-dimensional continuous spaces is, in the general case, intractable. This is why practical implementations of active inference, empowerment, and InfoMax all rely on variational bounds, amortized inference, or restrictive parametric assumptions (Gaussian, mean-field). These approximations are not merely practical concessions — they change the qualitative behavior of the system. A system that minimizes a variational bound on free energy is not the same as a system that minimizes free energy. The approximation *is* the theory in practice, and the approximation is chosen for tractability, not for fidelity.

#### 3. Entropic measures are structurally impoverished

Entropy collapses all structure into a single scalar. It treats all microstates as interchangeable; it cannot distinguish between:
- An algebraic constraint (commutativity of two operations)
- A topological constraint (connectedness of a network)
- A geometric constraint (symmetry of a formation)
- A causal constraint (A must precede B)

All of these can be *encoded* as distributions and then measured entropically, but the encoding destroys the structure that makes them different kinds of constraints. This is like measuring the difficulty of both a maze and a chess problem by counting their bits of description — technically possible, but it throws away everything that matters.

#### 4. Information theory is not causally structured

Shannon information is symmetric: I(X; Y) = I(Y; X). But causation is not symmetric. An agent that needs to understand *why* something happened, or *what would happen if* it acted differently, needs causal structure that information theory does not provide. Pearl's do-calculus and structural causal models are a step in the right direction, but they are not integrated into any of the major autonomy frameworks at the foundational level.

### The Cheap Wins and Why They Mislead

The information-theoretic approach does produce results. Empowerment gives reasonable behavior in gridworlds. Active inference produces recognizable perception-action loops. Predictive coding explains some neural response properties. These are real results.

But they are cheap wins — cases where the representation problem is simple enough (small state spaces, well-defined observations, clear action spaces) that the information-theoretic framework's foundational assumptions are approximately met. They do not scale to the cases that matter: open-ended environments, novel situations, creative problem-solving, genuine autonomy.

The success of these approaches in constrained settings creates a misleading sense of progress. It is like optimizing a search algorithm on sorted lists and concluding that the sorting problem is solved.

### What Might Replace Entropy at the Top

If the highest-level optimization function cannot be informational, what can it be? Several candidates deserve investigation:

**Causal structure**: The highest-level objective may not be to minimize uncertainty but to build and maintain accurate *causal models* — understanding not just what correlates with what, but what causes what and what would happen under intervention. This requires machinery beyond information theory: structural causal models, do-calculus, or their successors.

**Algebraic closure**: The objective may involve maintaining or extending *algebraic structure* — closure properties, composition rules, symmetries. This is what Rosen was reaching for with (M,R)-systems: the organism maintains itself by maintaining the algebraic closure of its metabolism-repair cycle. This is a structural objective, not a statistical one.

**Constraint satisfaction over heterogeneous types**: Rather than a single scalar objective, the highest-level function may be a *constraint satisfaction* problem over structurally different kinds of constraints — metric, algebraic, topological, causal — that cannot be reduced to a common currency without losing their distinct structure. This would require something more like a logic or a type system than an optimization landscape.

**Formal language / grammar**: The generative capacity of symbolic systems comes from their grammar — finite rules producing infinite structures. The highest-level objective may involve acquiring, maintaining, and extending a *generative grammar* over actions, representations, and constraints. This connects back to Critique 1: without symbols, there is no grammar.

---

## The Connection Between the Two Critiques

These two critiques are not independent. They reinforce each other:

1. **Without symbols, you are stuck with entropy.** If your only representational substrate is continuous activations and probability distributions, then your only native optimization objectives are statistical — entropy, divergence, mutual information. You literally cannot express "maintain commutativity" or "preserve connectedness" without first encoding these as distributional properties, which strips away their structure.

2. **Without a non-entropic objective, you have no reason to learn symbols.** If the system's highest-level goal is to minimize free energy, there is no pressure to discover discrete combinatorial structure. Continuous approximations will always be locally sufficient. Symbols only become *necessary* when the objective itself has combinatorial or algebraic structure that continuous optimization cannot capture.

This creates a trap: the subsymbolic-entropic paradigm is self-reinforcing. It defines both the representational medium and the objective function in terms that exclude the very structures that would reveal its limitations.

Breaking out of this trap requires attacking both problems simultaneously: introducing symbolic structure AND a non-entropic objective that justifies and exploits that structure.

---

## Summary

| Critique | What's Wrong | What's Needed |
|----------|-------------|---------------|
| Missing symbolic layer | Subsymbolic-all-the-way-up architecture cannot support compositional generativity, counterfactual reasoning, or structural creativity | Symbolic/algebraic structure that is learned (not handcrafted) and grounded in (not floating above) subsymbolic dynamics |
| Entropic optimization function | Information-theoretic objectives presuppose solved representation, are intractable, structurally impoverished, and causally blind | A higher-level objective with causal and algebraic structure — constraint satisfaction, closure maintenance, or generative grammar — not reducible to a single scalar divergence |
| Their connection | Without symbols you're stuck with entropy; without non-entropic objectives you have no reason to learn symbols | Both must be addressed simultaneously to escape the subsymbolic-entropic trap |

These are not objections to specific implementations. They are structural critiques of the dominant paradigm for theories of autonomy and cognition. Any framework that claims to provide a general principle of autonomous, cognitive behavior must eventually address them.

---

## Validation and Deepening

*This section stress-tests each claim in the critique above against published literature, empirical evidence, and the strongest available counterarguments. Claims are rated: **solid**, **partially right**, **overstated**, or **wrong**.*

---

### Critique 1: The Missing Symbolic Layer

#### A. Supporting Literature

The claim that a symbolic layer is necessary has deep roots and substantial recent vindication.

**Fodor & Pylyshyn (1988), "Connectionism and Cognitive Architecture: A Critical Analysis," *Cognition* 28, 3–71.** The foundational argument. Fodor and Pylyshyn identified three properties of human cognition that require combinatorial syntactic structure: *systematicity* (anyone who can think "John loves Mary" can think "Mary loves John"), *productivity* (finite resources generating infinite novel thoughts), and *compositionality* (the meaning of a complex expression is a function of its parts and their arrangement). They argued that connectionist models can only display systematicity by implementing a classical symbol system. After 37 years, this challenge remains substantially unmet (see counterarguments below for the partial exceptions).

**Marcus (2018), "Deep Learning: A Critical Appraisal," *arXiv:1801.00631*.** Identified ten specific challenges facing deep learning, including: inability to handle hierarchical structure, no open-ended inference, no integration of prior knowledge, inability to distinguish causation from correlation, and brittleness under distributional shift. Marcus (2020), "The Next Decade in AI: Four Steps Towards Robust Artificial Intelligence," *arXiv:2002.06177*, argued explicitly that "the only machinery we know of that can manipulate abstract knowledge reliably is the apparatus of symbol-manipulation." His four prerequisites for robust AI — hybrid architecture, large-scale knowledge, reasoning, and cognitive models — all require symbolic components.

**Lake, Ullman, Tenenbaum & Gershman (2017), "Building Machines That Learn and Think Like People," *Behavioral and Brain Sciences* 40, e253.** Identified compositionality, causal models, intuitive physics, and intuitive psychology as ingredients missing from deep learning. Drew the fundamental distinction between pattern recognition and model building: "The difference between pattern recognition and model building, between prediction and explanation, is central to our view of human intelligence."

**Greff, van Steenkiste & Schmidhuber (2020), "On the Binding Problem in Artificial Neural Networks," *arXiv:2012.05208*.** Decomposed the binding problem into segregation, representation, and composition. Concluded that "neural networks' inability to dynamically and flexibly bind information that is distributed throughout the network affects their capacity to acquire a compositional understanding of the world." Identified the core deficit as a lack of "mechanisms for dynamic information routing based on context — a capacity essential for flexible symbol manipulation."

**Battaglia et al. (2018), "Relational inductive biases, deep learning, and graph networks," *arXiv:1806.01261*.** This DeepMind paper argued that "combinatorial generalization must be a top priority for AI to achieve human-like abilities, and that structured representations and computations are key to realizing this objective." An explicit admission from within the subsymbolic camp that standard deep learning lacks the necessary relational/compositional structure.

**Concrete failures:**

- *The Reversal Curse*: Berglund et al. (2023), "The Reversal Curse: LLMs trained on 'A is B' fail to learn 'B is A'," *arXiv:2309.12288*. LLMs trained on "Tom Smith's wife is Mary Stone" systematically fail to answer "Mary Stone's husband is ___." A 2025 analysis (arXiv:2504.01928) explicitly connected this to the binding problem: "The Reversal Curse in LLMs is caused by inconsistency and entanglements of concept representations, two aspects of the binding problem."
- *SCAN benchmark*: Lake & Baroni (2018), "Generalization without Systematicity," *arXiv:1711.00350*. Standard seq2seq networks fail dramatically on compositional generalization — accuracy drops to near zero when tested on novel combinations of known primitives.
- *Csordas et al. (2025), "Fodor and Pylyshyn's Legacy — Still No Human-like Systematic Compositionality in Neural Networks," *arXiv:2506.01820*. Re-evaluated even the best connectionist results and concluded: "Fodor and Pylyshyn's main criteria for modeling human-like compositionality remain unchallenged or unsatisfied by modern approaches," including GPT-4.

#### B. Counterarguments

**1. Emergent symbolic structure in transformers.** Mechanistic interpretability has revealed discrete structure emerging inside continuous systems. Nanda et al. (2023), "Progress measures for grokking via mechanistic interpretability" (ICLR 2023), showed that transformers trained on modular arithmetic develop discrete Fourier features — genuine algebraic structure from gradient descent. Olsson et al. (2022), "In-context Learning and Induction Heads," identified specific circuits (induction heads) that implement a copy-and-complete algorithm. Templeton et al. (2024), "Scaling Monosemanticity" (Anthropic), extracted millions of interpretable features from Claude 3 Sonnet using sparse autoencoders — features that are multilingual, multimodal, and highly abstract.

*Assessment*: **Strong for existence, weak for manipulation.** These results establish that discrete structure *emerges* from gradient descent. But "features exist inside the network" is different from "the network performs compositional symbolic computation." The critique's claim is about manipulation and recombination, not mere existence. The strongest version of this counterargument would require showing that transformers perform variable binding and rule application internally — which has not been conclusively demonstrated at scale.

**2. Lake & Baroni (2023), "Human-like systematic generalization through a meta-learning neural network," *Nature* 623, 115–121.** Meta-Learning for Compositionality (MLC) — a training procedure where a transformer is continuously updated across episodes to improve compositional skills — achieved human-like systematic generalization. This is a pure neural network achieving human-level compositionality, published in *Nature*.

*Assessment*: **The strongest single counterargument.** However, the 2025 rebuttal by Csordas et al. (arXiv:2506.01820) found that MLC "can only perform such tasks, if at all, under a very narrow and restricted definition of a meta-learning setup." Under more stringent testing, systematic behavior breaks down. If this rebuttal holds, MLC achieves systematicity within its training distribution of meta-learning episodes but not open-ended compositional generalization.

**3. LLM performance on symbolic tasks.** GPT-4 and successors perform impressively on mathematical reasoning (o1 achieves 94.8% on MATH), code generation (o1 at 89th percentile in competitive programming), and logical reasoning. OpenAI o3 scored 88% on ARC-AGI-1.

*Assessment*: **Impressive but double-edged.** ARC Prize researchers described o3's approach as "deep learning-guided program search" — generating chains of thought that function as natural language programs. This is arguably *internal symbolic computation* performed at the token level. The best results use chain-of-thought (internal program synthesis) or hybrid neuro-symbolic methods. Performance drops sharply on genuinely novel problems (Olympiad-level: ~50-60%). A 2024 study (arXiv:2512.03272) found that integrating symbolic solvers with LLMs significantly improves performance on constraint satisfaction and deductive reasoning, while pure LLMs perform better only on shallow tasks. These successes may *demonstrate* the necessity of symbolic computation rather than refuting it.

**4. GFlowNets and discrete bottleneck architectures.** Bengio et al. (2023), "GFlowNet Foundations," *JMLR 24*. GFlowNets learn to sample from combinatorial spaces through sequential decision-making. VQ-VAE (van den Oord et al., NeurIPS 2017) learns discrete latent representations through vector quantization.

*Assessment*: **Actually supports the critique.** GFlowNets are explicitly designed to handle discrete, combinatorial structure — they concede the necessity of discrete structure and provide neural tools for navigating it. VQ-VAE imposes discretization architecturally. Both succeed precisely because they introduce discrete/combinatorial mechanisms.

**5. Embodied cognition (Lakoff & Johnson).** Argues that conceptual structure arises from embodied experience — image schemas and conceptual metaphors — dissolving the need for classical disembodied symbols.

*Assessment*: **Tangential.** Embodied cognition provides an argument about *grounding*, not about *compositionality*. Lakoff's own theory relies on systematic mappings between domains and structured combinations of primitives — functionally symbolic operations. The critique already accommodates this: point (2) says representations should be "grounded in subsymbolic dynamics." Embodied cognition enriches the grounding story but does not dissolve the need for compositional manipulation.

**6. The Bitter Lesson (Sutton, 2019).** General methods (search and learning) consistently outperform hand-designed solutions as compute scales.

*Assessment*: **Strong against GOFAI, irrelevant to the critique.** The bitter lesson says "don't hand-design features"; it does not say "discrete structure is unnecessary." The critique explicitly agrees that representations should be learned, not handcrafted. Moreover, the most impressive recent results (o3 on ARC-AGI, chain-of-thought reasoning) succeed by introducing what looks like symbolic computation at test time.

**7. Smolensky's tensor product representations (1990).** Provides a mathematical method for encoding variable-value bindings in distributed connectionist systems using tensor products.

*Assessment*: **Mathematically rigorous but limited.** As Fodor & McLaughlin pointed out, the resulting representations have only *weak* compositionality — the constituents are there in the mathematical sense, but the system cannot perform structure-sensitive operations (like moving a constituent from one structural position to another) that classical systems can.

**8. Chalmers (1993), "Connectionism and Compositionality: Why Fodor and Pylyshyn Were Wrong."** Argues that if Fodor and Pylyshyn's argument is valid, it implies no connectionist network can support compositional semantics — not even a connectionist implementation of a Turing machine. But connectionist networks can implement Turing machines, so the argument proves too much.

*Assessment*: **Logically compelling but deflating.** Chalmers is correct that connectionist networks can *implement* symbol systems. But this is the "mere implementation" objection that Fodor and Pylyshyn anticipated. The question is whether the connectionist level is the right level of explanation, and whether pure connectionist training procedures (gradient descent on continuous loss) can *discover* the needed symbolic structure without it being architecturally provided.

#### C. Accuracy Assessment

| Claim | Rating | Assessment |
|-------|--------|------------|
| "The field threw out the baby with the bathwater" | **Solid** | Well-supported by the historical record. Battaglia et al. (2018), Lake et al. (2017), and Marcus (2018, 2020) all make this argument explicitly. |
| "Without symbols you lose compositionality" | **Solid** | SCAN, COGS, CFQ benchmarks confirm systematic failure. Csordas et al. (2025) confirm this holds even against the best neural results. The reversal curse (Berglund et al. 2023) is a vivid demonstration. |
| "Without symbols you lose abstraction" | **Partially right** | Transformers *do* develop abstract features (Templeton et al. 2024). But the abstraction is extractable by researchers, not necessarily manipulable by the system. The claim should be sharpened to: "Without symbols you lose *manipulable* abstraction — the ability to reason about classes of structures rather than merely recognizing instances." |
| "Without symbols you lose counterfactual reasoning" | **Solid** | Pearl's causal hierarchy theorem (Bareinboim et al. 2022) formally establishes that observational data underdetermines interventional and counterfactual quantities. LLMs can *simulate* counterfactual reasoning through chain-of-thought, but this is arguably internal symbolic computation. |
| "Without symbols you lose proof and verification" | **Solid** | AlphaGeometry (DeepMind, 2024) — the best AI theorem prover — uses a neural language model to guide a *symbolic deduction engine*. The symbolic component is necessary. Hybrid systems (arXiv:2512.03272) consistently outperform pure LLMs on deductive tasks. |
| "Trying to implement algebraic reasoning with gradient descent is like doing arithmetic with a thermostat" | **Overstated** | LLMs can approximate algebraic reasoning impressively, even if the approximation breaks at the edges. A better formulation: "Gradient descent can approximate algebraic reasoning for cases seen during training, but cannot capture the generative structure that guarantees correctness on novel cases." |
| "The failure of GOFAI was a failure of handcrafted representations, not of symbols" | **Solid** | The neurosymbolic AI field (Garcez & Lamb 2023, Mao et al. 2019) is premised on exactly this distinction. |
| "Dominant frameworks do not even attempt a symbolic layer" | **Partially right** | Active inference, predictive coding, and empowerment frameworks are indeed committed to continuous substrates. But Bengio's System 2 program (NeurIPS 2019 keynote) and GFlowNets represent attempts from *within* the deep learning community to address this. The claim should be: "The dominant *theoretical* frameworks do not provide mechanisms for symbolic emergence, even though some *architectural* work is moving in that direction." |

#### D. Blind Spots

1. **The Kahneman connection is underexplored.** Bengio (2019) explicitly mapped System 1 (fast, intuitive) to current deep learning and System 2 (deliberate, compositional) to what deep learning needs to become. Gronchi & Perini (2024, *Frontiers in Cognition*) developed this into architectural proposals for neurosymbolic AI. The critique would be strengthened by noting that the System 1/System 2 distinction is essentially the subsymbol/symbol distinction in cognitive science clothing.

2. **The critique understates what LLMs have achieved.** The chain-of-thought revolution (o1, o3) represents a genuine advance — LLMs learning to perform internal program synthesis. The right framing is not "LLMs can't do symbolic reasoning" but "LLMs succeed at symbolic reasoning precisely when they learn to approximate symbolic computation, which demonstrates the necessity of the symbolic layer rather than refuting it."

3. **Variable binding deserves more attention.** Wu et al. (2025, ICML, arXiv:2505.20896) found that transformers learn to use the residual stream as an "addressable memory space" for variable binding — but this binding is fragile and context-dependent. This is the sharpest empirical pressure point for the critique.

---

### Critique 2: The Entropic Optimization Function

#### A. Supporting Literature

**1. FEP unfalsifiability / tautology.** A substantial and growing critical literature now exists:

- *Biehl, Pollock & Kanai (2021), "A Technical Critique of Some Parts of the Free Energy Principle," Entropy 23(3), 293.* The mathematically most precise critique. Found that various definitions of "Markov blanket" used across FEP publications are not equivalent, crucial derivation steps are not generally correct without unstated assumptions, and the original "free energy lemma" is proved wrong by counterexample.
- *Andrews (2021), "The Math is Not the Territory," Biology & Philosophy 36(3).* Distinguishes model structure from model construal. Argues the FEP is best understood as a mathematical framework (like Lagrangian mechanics), not an empirical theory. Implication: the FEP *itself* is not falsifiable and has no explanatory content beyond what specific construals provide.
- *Bruineberg, Dolega, Dewhurst & Baltieri (2022), "The Emperor's New Markov Blankets," Behavioral and Brain Sciences 45.* Distinguishes Pearl blankets (statistical tools) from Friston blankets (ontological claims about agent boundaries). Shows the FEP slides between these interpretations — a fallacy of equivocation.
- *Raja, Valluri, Baggs, Chemero & Anderson (2021), "The Markov Blanket Trick," Physics of Life Reviews 39.* Concludes that FEP is "at most a modeling framework that permits us to understand some properties of some systems in terms of Bayesian inference."
- *Aguilera, Millidge, Tschantz & Buckley (2022), "How Particular is the Physics of the Free Energy Principle?" Physics of Life Reviews 40, 24–50.* Examined FEP in the simplest possible systems and found its core requirements hold only for "a very narrow space of parameters."
- *Mangalam et al. (2025), "The Emperor's New Pseudo-Theory: How the Free Energy Principle Ransacked Neuroscience."* Calls for the "immediate retirement" of FEP as a scientific framework, characterizing it as "a distributed protocol of rhetorical laundering."

**2. Computational intractability of mutual information.** Now formally proven:

- *McAllester & Stratos (2020), "Formal Limitations on the Measurement of Mutual Information," AISTATS 2020.* **Any distribution-free high-confidence lower bound on MI estimated from N samples cannot be larger than O(ln N).** The number of samples required is exponential in the true MI. This is a theorem, not an opinion.
- *Poole, Ozair, Van Den Oord, Alemi & Tucker (2019), "On Variational Bounds of Mutual Information," ICML 2019.* Variational lower bounds on MI degrade when MI is large — either high bias or high variance.
- *Song & Ermon (2020), "Understanding the Limitations of Variational Mutual Information Estimators," ICLR 2020.* Estimators like MINE exhibit variance that grows exponentially with true MI. Existing estimators fail to satisfy basic self-consistency properties (data processing inequality, additivity under independence).

**3. Information theory cannot capture causation.** Formally established:

- *Pearl (2009), Causality, 2nd ed.* "There is nothing in the joint distribution that tells us how distributions would differ if external conditions changed."
- *Bareinboim, Correa, Ibeling & Icard (2022), "On Pearl's Hierarchy and the Foundations of Causal Inference."* The **Causal Hierarchy Theorem (CHT)**: the three layers of Pearl's hierarchy (association, intervention, counterfactual) almost always separate in a measure-theoretic sense. Observational data virtually always underdetermines interventional and counterfactual quantities. Since information theory operates at Layer 1, it is *provably* insufficient for the causal reasoning required for autonomous cognition.

**4. Maximum Entropy Production is non-explanatory.** Even its proponents concede this:

- *Dewar (2009), "Don't Shoot the Messenger," Entropy 11(4), 931.* Admits MEP is equivalent to Jaynes' MaxEnt inference algorithm — "it has no physical content." It is inference, not physics.
- *Grinstein & Linsker (2007)* showed Dewar's earlier derivation required near-equilibrium conditions. *Bruers* presented a counterexample. *Martyushev & Seleznev (2014)* catalogued the restrictions and noted counterexamples (Ginzburg-Landau equation stability violations).
- *Volk & Pauluis (2010), Philosophical Transactions of the Royal Society B:* "It should matter to Earth's meridional transport if the ocean were made of vinegar" — but MEP cannot capture this.

**5. The representation presupposition.** Well-grounded in the foundations of information theory:

- *Shannon & Weaver (1949)*: Shannon explicitly stated that "the semantic aspects of communication are irrelevant to the engineering problem." Information theory measures quantities of surprise over pre-specified symbol sets. What those symbols mean, or whether they carve the world at its joints, is outside the theory's scope.
- *Bickhard, "Foundational Issues in Artificial Intelligence and Cognitive Science" (1995)*: Coined "encodingism" — the presupposition that all representation has the nature of encodings. Argues this is "at root logically incoherent" because encodings have representational content only by virtue of the encoding-user already knowing what that content is. Information theory inherits this circularity.
- *Dretske (1981), Knowledge and the Flow of Information*: Attempted to ground cognition in information theory and failed — his account cannot handle misrepresentation, a fatal flaw for any theory of cognition. Later critiques confirmed that "the physics of the manifestation of an arbitrary object sets forth an informational boundary stating that information cannot be enough to support our cognitive processes."

**6. Structural impoverishment.** Supported by the organizational biology literature:

- *Moreno & Mossio (2015), Biological Autonomy, Springer.* Biological systems operate under two distinct causal regimes: thermodynamic processes (open) and constraints (organizationally closed). Constraints constitute a distinct regime of causation irreducible to thermodynamic flow. Autonomous systems exhibit *closure of constraints* — a topological and algebraic property, not a scalar one.
- *Montévil & Mossio (2015), "Biological Organisation as Closure of Constraints," J. Theor. Biol. 372, 179–191.* Organizational closure involves a set of internally produced and mutually dependent constraints — a relational structure that cannot be collapsed into a single entropy measure.

#### B. Counterarguments

**1. FEP as principle, not empirical theory.** Friston and defenders (Hohwy, Ramstead et al.) argue that the FEP is like Hamilton's principle in physics — a mathematical framework, not a falsifiable hypothesis. Demanding falsifiability is a category mistake.

*Assessment*: **Logically valid but double-edged.** If FEP is just a mathematical framework, it has no more explanatory power than saying "systems that persist tend to minimize surprise relative to their model." The explanatory work is done by specific process theories, which are independent commitments. This defense saves the FEP from falsification by emptying it of content.

**2. Successes of information-theoretic objectives.** Empowerment (Klyubin, Polani & Neumann, 2005) produces sophisticated behavior in simple environments including wall-following, corridor-centering, and proto-niche-construction. Active inference achieves 93–100% success on manipulation tasks in robotics (AIF-VPL framework, 2024). Contrastive learning (InfoNCE, SimCLR, CLIP) has been transformative for representation learning.

*Assessment*: **Real but domain-limited.** These are genuine successes in constrained settings. But empowerment has not demonstrated clear advantages in open-ended high-dimensional settings. Active inference has not outperformed standard RL in unconstrained domains. And a critical finding undermines the MI interpretation: BYOL (Bootstrap Your Own Latent) apparently succeeds *without* explicit MI maximization — analysis revealed it implicitly performs contrastive learning through batch statistics, and recent work (f-MICL, 2024, arXiv:2402.10150) suggests contrastive learning's success may not depend on tight MI estimation. The information-theoretic explanation may be post-hoc rationalization.

**3. Jaynes' MaxEnt and the Shore-Johnson uniqueness theorem.** Jaynes argued MaxEnt is the only consistent way to assign probabilities given constraints. Shore & Johnson (1980), "Axiomatic Derivation of the Principle of Maximum Entropy," proved under four axioms (uniqueness, permutation invariance, subset independence, system independence) that Shannon entropy is the *unique* measure suitable for probability updating. Cox's theorem (1946) further establishes that probability theory is the unique consistent extension of logic to uncertain reasoning.

*Assessment*: **Very strong within its scope — which is narrower than it appears.** Shore-Johnson genuinely proves a uniqueness result for the problem of assigning probabilities given expected-value constraints. But this does not establish that entropy is the right *objective function for agent behavior*. The uniqueness of MaxEnt for inference does not imply entropy is the right objective for action and organization. These are different problems.

**4. Information geometry reveals rich structure.** Amari's information geometry (1985–2021) shows that the space of probability distributions is a Riemannian manifold with the Fisher information metric (the unique invariant metric under Markov embeddings), alpha-connections, and dual geometric structure. Baez, Fritz & Leinster (2011), "A Characterization of Entropy in Terms of Information Loss," showed Shannon entropy is uniquely characterized as a functor preserving natural categorical axioms.

*Assessment*: **Strong against the claim that information theory is structurally impoverished in general.** This is a genuine correction to the critique. The full information-geometric apparatus is mathematically rich. However, the critique's specific target is correct: *Shannon entropy as a scalar objective* is structurally impoverished, even if the space of distributions has rich geometry. Optimizing a scalar (minimize H, minimize KL, maximize MI) discards the geometric structure that information geometry reveals. The structural impoverishment claim should be narrowed to scalar entropic objectives, not to information theory as a mathematical field.

**5. Transfer entropy and causal information theory.** Schreiber (2000), "Measuring Information Transfer," *Physical Review Letters*. Transfer entropy quantifies directed information transfer between processes, capturing genuine directed influence. Barnett, Barrett & Seth (2009) proved that for Gaussian variables, Granger causality and transfer entropy are mathematically equivalent. Ay & Polani (2008), "Information Flows in Causal Networks," incorporated interventionist concepts into information-theoretic measures.

*Assessment*: **Strong against "information theory cannot capture causation" as stated, but revealing on closer inspection.** Transfer entropy captures *predictive* causation (Granger causation), not *interventionist* causation (Pearl causation) — it can be fooled by confounders and does not support counterfactual reasoning. Ay & Polani's causal information flow *works* but imports causal structure from outside information theory (virtual interventions, causal graphs). The pattern: to capture causation in information-theoretic terms, you must *add* causal structure. The causal structure does the explanatory work; the information theory provides the quantification.

#### C. Accuracy Assessment

| Claim | Rating | Assessment |
|-------|--------|------------|
| "Information presupposes the representation problem is solved" | **Solid** | Shannon himself excluded semantics. Bickhard's "encodingism" critique is logically precise. Dretske's attempt to bridge the gap failed. No one has refuted this. |
| "Information-theoretic objectives are computationally intractable" | **Solid** | McAllester & Stratos (2020) formally proved the O(ln N) bound. Song & Ermon (2020) proved exponential variance. This is theorem-level evidence. |
| "Entropy collapses all structure into a single scalar" | **Partially right → needs sharpening** | True of scalar entropic objectives (H, KL, MI used as optimization targets). Not true of information geometry or categorical information theory. Sharpen to: "Using entropy, KL divergence, or mutual information as a *scalar optimization objective* collapses structurally distinct constraint types into a common currency, losing the structure that distinguishes them." |
| "Shannon information is symmetric" | **Solid** | I(X;Y) = I(Y;X) by definition. This is a mathematical fact. |
| "Information theory is not causally structured" | **Partially right → needs sharpening** | Standard Shannon information theory is acausal. But extensions exist: transfer entropy, Ay-Polani information flow, causal entropy (2023). Sharpen to: "*Standard* information theory lacks causal structure. Extensions can incorporate it, but only by importing causal assumptions from outside — the causal structure does the work, and the information theory provides the measurement." |
| "Empowerment gives reasonable behavior in gridworlds" (cheap wins) | **Solid** | Accurate characterization. Empowerment does produce sophisticated behavior but only in simple environments. |
| "The convergence on entropy suggests a deep confusion" | **Overstated** | The convergence partly reflects genuine mathematical properties (Shannon-Johnson uniqueness, Cox's theorem) and partly reflects paradigm momentum. A more accurate claim: "The convergence on entropy reflects both genuine mathematical properties of probability theory and an unjustified leap from 'entropy is the right way to do inference' to 'entropy is the right objective for autonomous cognition.'" |
| "These cheap wins do not scale" | **Solid** | No information-theoretic framework has demonstrated scaling to open-ended autonomy. Active inference and empowerment remain in constrained domains. |
| FEP critique (implicit throughout) | **Solid** | The critical literature (Biehl et al. 2021, Andrews 2021, Bruineberg et al. 2022, Raja et al. 2021, Aguilera et al. 2022, Mangalam et al. 2025) is now substantial and technically rigorous. |

#### D. Alternatives to Entropy: What Exists and What's Promising

**Constructor theory (Deutsch & Marletto).** Marletto (2015), "Constructor Theory of Information," *Proc. R. Soc. A*; Marletto (2015), "Constructor Theory of Life," *J. R. Soc. Interface*; Marletto (2017), "Constructor Theory of Thermodynamics," *arXiv:1608.02625*. Replaces laws specifying what *happens* with laws specifying which *transformations are possible and which are impossible*. Provides an exact, non-approximative, scale-independent formulation of thermodynamic laws. *Assessment*: The strongest candidate for a genuinely non-entropic foundation. Explicitly designed to replace the probabilistic/dynamical framework with a counterfactual one.

**Rosen's (M,R)-systems and organizational closure.** Igamberdiev (2024), "Toward the Relational Formulation of Biological Thermodynamics," *Entropy 26(1), 43*, argues explicitly that in systems exhibiting closure to efficient causation, "attractors such as thermodynamic equilibrium, as well as the notion of thermodynamic entropy, lose their validity." The Moreno-Mossio framework of *closure of constraints* explicitly distinguishes the organizational (non-entropic) level from the thermodynamic (entropic) level. *Assessment*: Strong. Algebraic closure is genuinely non-entropic and well-formalized categorically (Louie, Letelier, Cárdenas).

**Category theory as metalanguage.** Phillips & Wilson (2010), "Categorial Compositionality," *PLoS Comput. Biol.*, showed that systematicity emerges as a natural consequence of category-theoretic structure (functorial relationships). Spivak's work on operads provides compositional frameworks for dynamical systems. Smithe (Topos Institute) is developing "compositional active inference" using categorical semantics. *Assessment*: Category theory does not so much offer an *alternative* to entropy as a *metalanguage* that can express both entropic and non-entropic concepts — the most promising avenue for transcending the entropy-or-not dichotomy.

**Kolmogorov complexity.** Measures information content of individual objects rather than ensembles. Hutter's AIXI uses Solomonoff induction with Kolmogorov-weighted priors. *Assessment*: Complementary to Shannon entropy, not a replacement. Non-computable in the general case. Remains within the information-theoretic paradigm.

**Causal structure as objective.** Pearl's causal hierarchy provides structurally richer framework, but Pearl himself does not propose it as a *replacement* for entropy — it extends statistical frameworks. Wissner-Gross & Freer (2013) tried deriving intelligence from *causal entropy maximization* but were criticized for making no connection to knowledge or rationality. *Assessment*: Causal structure is necessary but not currently formulated as a standalone master objective.

#### E. Blind Spots

1. **The critique understates the strength of the Jaynes-Cox-Shore-Johnson program.** Entropy is not arbitrary — it is uniquely characterized by multiple independent axiomatic approaches. The critique should acknowledge this and clarify that the objection is not "entropy is the wrong measure for inference" (it is provably the right one) but "entropy-as-objective-for-action is a category mistake — the right measure for updating beliefs is not the right objective for organizing behavior."

2. **The Dark Room Problem deserves mention.** If organisms minimize surprise, they should seek unchanging environments and stay there. Defenders resolve this with expected free energy over temporal horizons, but this introduces prior preferences and temporal depth that do the actual explanatory work — not the free energy principle itself.

3. **BYOL undermines the MI interpretation.** If contrastive learning succeeds for reasons other than MI maximization, the information-theoretic explanation of its success may be post-hoc rationalization rather than genuine mechanism.

---

### The Connection Between the Two Critiques

#### A. Has Anyone Made This Argument?

Extensive search reveals that the specific argument — that the symbol problem and the entropy problem are *self-reinforcingly linked* — is **genuinely novel**. The closest existing work:

- *Deacon (2025), "Grounding Information in Thermodynamics and the Ungroundedness of Language," BioSystems.* Connects symbol grounding to thermodynamic entropy, arguing they are coupled through thermodynamic work. But Deacon grounds symbols *in* thermodynamics rather than arguing that the problems are manifestations of a single paradigm trap.
- *Abrahão (2025), "An Algorithmic Information-Theoretic Perspective on the Symbol Grounding Problem," arXiv:2510.05153.* Uses Kolmogorov complexity to show that purely symbolic systems cannot ground most worlds and that grounding acts are non-inferable. Links symbols to information-theoretic limitations but does not address paradigm lock-in.
- *Di Paolo, Buhrmann & Barandiaran (2022), "The Problem of Meaning: The Free Energy Principle and Artificial Agency," Front. Neurorobot.* Shows from *within* the entropy paradigm that "statistical correlation does not suffice to make it the case that the states of a system are meaningful *for* the system." Acknowledges the limitation but does not connect it to the symbol problem as a linked failure.

No published work makes the *meta-argument* that the dominance of entropy as foundational framework *itself causes* the symbol problem to be unsolvable within that framework, and that these two problems are mutually reinforcing through paradigm choice.

#### B. Has Anyone Described the Subsymbolic-Entropic Paradigm as Self-Reinforcing?

- *Collins (2024), "Why Artificial Intelligence Needs Sociology of Knowledge," AI & Society.* Identifies "thought styles" that function as paradigms in AI research. Argues current approaches are socially embedded to the degree that alternatives are structurally invisible. But focuses on social/political dimensions, not mathematical/conceptual lock-in.
- *Zhu et al. (2020), "Dark, Beyond Deep: A Paradigm Shift to Cognitive AI," Engineering.* Calls for a paradigm shift from "big data for small tasks" to "small data for big tasks." Identifies functionality, physics, intent, causality, and utility as "dark matter" invisible to current approaches. But does not connect this to the entropy-as-foundation issue.
- *Schneider (1987), "Connectionism: Is It a Paradigm Shift for Psychology?" Behavior Research Methods 19, 73–83.* Kuhnian analysis of connectionism. Descriptive, not critical.

The framing of the *conjunction* of subsymbolic methods + entropy-based objectives as a self-reinforcing paradigm dyad **does not appear in the literature**.

#### C. Accuracy Assessment

| Claim | Rating | Assessment |
|-------|--------|------------|
| "Without symbols, you are stuck with entropy" | **Solid** | If your representational substrate is continuous activations and probability distributions, your native objectives are statistical. This is logically correct. The only caveat: category theory provides a metalanguage that can express non-entropic concepts over continuous substrates, but this has not been operationalized in any autonomy framework. |
| "Without a non-entropic objective, you have no reason to learn symbols" | **Partially right** | The logic is sound: minimizing free energy provides no pressure for discrete structure since continuous approximations are locally sufficient. However, LLMs trained with next-token prediction (a simple entropic objective) *do* develop internal discrete structure (per mechanistic interpretability). The claim should be sharpened: "Without a non-entropic objective, there is no *guaranteed* pressure toward symbolic structure, even though it may sometimes emerge as a byproduct of sufficient scale and task complexity." |
| "The subsymbolic-entropic paradigm is self-reinforcing" | **Solid as a structural observation, novel as an explicit argument** | The mechanism is real: dropping symbols forces reliance on subsymbolic methods, which are inherently statistical, which presuppose entropy, which makes symbols seem unnecessary. But this has not been articulated anywhere in the literature — it is a genuine contribution. |

#### D. Novelty Assessment

The individual components — symbol grounding problem, entropy limitations, paradigm lock-in, non-entropic alternatives — are all well-established. The *specific synthesis* — that these are aspects of a single self-reinforcing paradigm structure, a trap with two locked exits — appears to be a **novel argumentative contribution**. The closest prior art is Deacon (2025), who connects symbols to thermodynamics but does not identify the self-reinforcing mechanism.

---

### Overall Verdict

**The two critiques are substantially correct but need sharpening in specific places:**

| Original Claim | Verdict | Sharpened Version |
|----------------|---------|-------------------|
| Symbols are necessary | **Solid** | Discrete compositional structure is necessary for open-ended cognition. It can and should emerge from neural learning rather than being hand-designed. Current dominant frameworks do not provide mechanisms for this emergence. |
| Information theory presupposes representation | **Solid** | Shannon himself excluded semantics. This is not fixable by better math — it is a scope limitation of the formalism. |
| MI estimation is intractable | **Solid** | Formally proven: O(ln N) bound (McAllester & Stratos 2020), exponential variance (Song & Ermon 2020). |
| Entropy is structurally impoverished | **Needs sharpening** | True of *scalar entropic objectives*. Not true of information geometry or categorical information theory. The critique targets the right thing (scalar optimization) but overstates the scope. |
| Information theory lacks causal structure | **Needs sharpening** | True of *standard* information theory. Extensions (transfer entropy, causal entropy) can incorporate causation — but only by importing causal structure from outside, which supports rather than undermines the critique. |
| Entropy convergence is a "deep confusion" | **Overstated** | Partly reflects genuine mathematical properties, partly paradigm momentum. The confusion is not in using entropy for inference but in promoting it to the master objective for autonomous behavior. |
| The symbol-entropy link is self-reinforcing | **Solid and novel** | No prior publication makes this meta-argument. It appears to be a genuine contribution to the philosophy of cognitive science and AI. |

**Most important finding:** The two formally proven results — the McAllester-Stratos O(ln N) bound on MI estimation and the Bareinboim et al. Causal Hierarchy Theorem — provide *theorem-level* support for the entropy critique. These are not matters of opinion. They establish mathematical limits on what information-theoretic objectives can achieve.
