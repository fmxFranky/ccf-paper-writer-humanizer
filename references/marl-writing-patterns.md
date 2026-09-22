# MARL Writing Patterns (2020–2025 Top-Conference Corpus)

Use this reference when the target paper concerns multi-agent reinforcement learning, cooperative or competitive Markov games, CTDE, MAPPO/QMIX-style value or policy factorization, multi-agent communication, credit assignment, emergent roles, zero-shot or ad hoc teamwork, multi-agent benchmarks, or MARL evaluation infrastructure.

This file contains transferable writing patterns extracted from a screened corpus of 52 accepted papers from ICML (21), NeurIPS (18), and ICLR (13), covering 2020–2025. The corpus includes method, theory, benchmark, infrastructure, and analysis papers. Source papers are used for structure and evidence discipline only; do not reuse their wording, claims, task examples, or technical content.

## Provenance and use boundary

The corpus was assembled from official ICML/PMLR and NeurIPS proceedings, official ICLR conference pages, and paired arXiv records when an ICLR PDF endpoint required browser verification. The source manifest records title, venue, year, authors, conference or proceedings page, PDF URL, and checksum. Treat the manifest as provenance, not as a citation list to copy into a manuscript.

Select one to four matching exemplar cards for a manuscript. Do not load the whole corpus into context. A local paragraph edit usually needs no exemplar; a full MARL manuscript or explicit style adaptation should select cards by story shape and evidence type.

## Repeated story shapes

### Failure mode -> root cause -> mechanism -> evidence

Use this for algorithm papers that repair a specific limitation of a common MARL paradigm.

1. Define the setting and the operational constraint: decentralized execution, partial observability, joint-action growth, heterogeneous agents, non-stationarity, or limited communication.
2. Show why the standard design fails. State the representational, optimization, statistical, or protocol-level cause; do not stop at "performance degrades."
3. State one mechanism-level insight that addresses that cause.
4. Introduce the method as the implementation of that insight.
5. Map each claimed benefit to a theorem, ablation, diagnostic, or benchmark result.

Weighted QMIX, DOP, FACMAC, HATRPO/HAPPO, DVD, and Difference Advantage Estimation illustrate this logic in different technical settings. Their transferable feature is the causal chain, not the particular factorization or estimator.

### Benchmark diagnosis -> protocol repair -> controlled validation

Use this for benchmark, environment, evaluation, and infrastructure papers.

1. Demonstrate that the established benchmark or evaluation protocol does not test the capability it is commonly used to support.
2. Identify the precise leakage or mismatch: open-loop solutions, fixed scenarios, insufficient stochasticity, uncontrolled partner distribution, weak partial observability, or missing compute/evaluation coverage.
3. Introduce the repaired benchmark or infrastructure with an explicit design-to-defect mapping.
4. Re-evaluate representative baselines under the repaired protocol and report what changes.
5. State the new benchmark's scope and remaining limitations.

SMACv2, Melting Pot, JaxMARL/SMAX, and PettingZoo are useful structural references. A benchmark paper must explain what the benchmark measures and why the old protocol was insufficient; a leaderboard alone is not a contribution argument.

### Setting shift -> formalization -> algorithm -> robustness

Use this when the contribution changes the information, partner, risk, or uncertainty model: robust MARL, offline MARL, ad hoc teamwork, safe MARL, or zero-shot coordination.

1. Define what is unknown or changing and who observes it.
2. Explain why the conventional MARL objective or training protocol is no longer adequate.
3. Formalize the new setting before naming the algorithm.
4. State the algorithm's information requirements and execution assumptions.
5. Evaluate both the target setting and a meaningful stress or transfer setting.

The strongest examples distinguish training partners from evaluation partners, available rewards from unavailable rewards, centralized training information from decentralized execution information, and in-distribution from unseen scenarios.

### Scaling pressure -> structure -> bound or measurement

Use this for papers where the main problem is exponential action/state growth, agent count, communication topology, or computation.

1. Quantify the scaling pressure before proposing a compact architecture.
2. Introduce the structural restriction or factorization and explain which interactions it preserves.
3. Give the bound, complexity statement, or wall-clock measurement that makes the trade-off explicit.
4. Validate both quality and cost. A faster run without a fair quality comparison is not a sample-efficiency claim.

Tesseract, Deep Coordination Graphs, communication-topology papers, and scalable safe MARL papers demonstrate the pattern.

### Diagnostic analysis -> practical recommendation

Use this for papers that revisit accepted design practices.

1. Name the community practice and the conditions under which it is assumed to help.
2. Construct a minimal setting that isolates the practice.
3. Give theoretical or controlled evidence for the failure mode.
4. Test whether the finding survives on standard benchmarks.
5. End with a bounded recommendation: when the practice is useful, when it is risky, and what to report.

Do not turn a diagnostic into a universal condemnation. Keep the recommendation tied to the tested reward landscape, observation model, agent heterogeneity, and training protocol.

## Abstract construction for MARL

Prefer the following order:

1. Task and exact game or cooperation setting.
2. Technical obstacle, including the source of non-stationarity, credit ambiguity, scaling, or generalization failure.
3. One insight sentence that predicts why the proposed mechanism should help.
4. Method name and the mechanism it instantiates.
5. Evidence scope: environments, partner distribution, benchmark version, theoretical result, or transfer condition.
6. Bounded result statement; retain uncertainty and do not claim field-wide superiority.

Do not write a list of algorithm modules followed by a list of win-rate improvements. State what the method changes in the learning or execution process, then give only the measurements that establish that change.

## Introduction construction

Build a claim ledger before drafting:

| Claim | Root reason | Closest prior work | Evidence needed | Where checked |
| --- | --- | --- | --- | --- |
| What the paper establishes | Why the problem persists | The nearest method, benchmark, or theory | Result, proof, or diagnostic | Section/table/figure |

A MARL introduction usually needs these moves:

1. Define the game setting and execution constraint. Say whether agents share parameters, observations, rewards, communication, or a centralized critic.
2. Organize prior work by the capability it adds: value factorization, policy gradients, roles, communication, offline learning, robust or safe objectives, benchmark design, or partner generalization.
3. Identify the closest failure case and its technical cause. Do not use a generic "complex environments" gap.
4. State one insight and show which assumption it relaxes or which interaction it preserves.
5. Preview the evidence package. If the claim concerns unseen partners, new agent counts, robustness, or efficiency, name the corresponding evaluation rather than only the standard training benchmark.
6. Keep contributions aligned with the evidence. A method, theorem, benchmark, and analysis are separate contributions only when each has a corresponding artifact.

Use citations to group paradigms by shared capability. Cite the closest competitor explicitly and avoid a flat inventory of algorithm names.

## Method exposition

Before drafting, fill one row per module:

| Module | Inputs available at train time | Inputs available at execution | Operation | Why needed | Tested by |
| --- | --- | --- | --- | --- | --- |

Then write the method in this order:

1. Setting and objective.
2. Mechanism overview with the information flow between agents, critic, mixer, communication channel, role variables, or dynamics model.
3. One subsection per mechanism, each beginning with its purpose.
4. Optimization or update rule, including which quantities are centralized and which are local.
5. Assumptions and complexity.
6. Algorithm or implementation details needed for reproduction.
7. A pointer to the ablation, theorem, or analysis that tests the mechanism.

Explain a symbol's scientific role before presenting a dense equation. State whether a claimed factorization is exact, approximate, monotonic, or only used during training. Do not blur centralized training with centralized execution.

## MARL evidence writing

Every full MARL paper should answer four questions:

1. **Effectiveness:** Does the method improve the target objective over strong, protocol-matched baselines?
2. **Causality:** Which mechanism creates the improvement? Remove or replace each central module.
3. **Generalization:** Does the method transfer across seeds, scenarios, agent counts, partners, maps, or reward conditions claimed in the introduction?
4. **Cost and limits:** What communication, computation, memory, sample, safety, or performance trade-off remains?

Narrate evidence as claim -> setting -> observation -> interpretation. For each main result, state the benchmark version and evaluation distribution before the conclusion. Keep training curves, final performance, win rates, returns, regret, sample efficiency, and wall-clock speed conceptually separate.

Benchmark papers should report the defect in the old protocol, the change introduced, the exact evaluation split, and the behavior of representative baselines under both protocols. Method papers should not present a new benchmark as a generic extra experiment; explain which claim it makes testable.

## MARL-specific precision checks

Before finalizing, verify that the text states or deliberately defers:

- number and type of agents;
- observation and action spaces, including partial observability;
- reward structure and whether rewards are shared, individual, shaped, or unavailable;
- centralized-training and decentralized-execution information boundaries;
- parameter sharing or heterogeneity assumptions;
- communication topology, bandwidth, delay, and message availability when relevant;
- partner distribution at training and evaluation time;
- benchmark version, scenario generation, map split, and seed protocol;
- metric definition and whether higher or lower is better;
- baseline identity and whether implementations use the same protocol;
- ablations for each mechanism-level claim;
- computation and sample budget when efficiency is claimed;
- known failure cases or scope limits.

If a paper does not report one of these details, narrow the claim or mark the evidence gap. Do not fill it with a standard MARL assumption.

## Claim language

Use "we prove" only for a theorem whose assumptions and conclusion are stated. Use "we observe" or "our experiments show" for measured results. Use "supports" when the evidence is benchmark-specific. Use "is compatible with" for a mechanism interpretation not directly isolated by an ablation. Do not turn a stronger score on SMAC into a general claim about coordination, robustness, or transfer.

## Do-not-copy boundary

Transfer the sequence of reasoning, evidence mapping, and scope discipline. Do not copy source sentences, contribution bullets, coined phrases, benchmark conclusions, numerical results, or method names. Preserve the user's problem, method, and measured evidence. When a source paper's rhetoric is stronger than its protocol supports, retain the protocol limitation rather than reproducing the rhetoric.

## Representative source anchors

- ICML 2020: [ROMA](https://proceedings.mlr.press/v119/wang20f.html), [Other-Play](https://proceedings.mlr.press/v119/hu20a.html), [Deep Coordination Graphs](https://proceedings.mlr.press/v119/boehmer20a.html).
- ICML 2022: [Revisiting Some Common Practices](https://proceedings.mlr.press/v162/fu22d.html), [Deconfounded Value Decomposition](https://proceedings.mlr.press/v162/li22l.html).
- ICML 2024: [E(3)-Equivariant Actor-Critic](https://proceedings.mlr.press/v235/chen24az.html), [Open Ad Hoc Teamwork](https://proceedings.mlr.press/v235/wang24an.html).
- NeurIPS 2020: [Weighted QMIX](https://proceedings.neurips.cc/paper_files/paper/2020/hash/73a427badebe0e32caa2e1fc7530b7f3-Abstract.html), [Learning Implicit Credit Assignment](https://proceedings.neurips.cc/paper/2020/hash/8977ecbb8cb82d77fb091c7a7f186163-Abstract.html).
- NeurIPS 2023: [SMACv2](https://proceedings.neurips.cc/paper_files/paper/2023/hash/764c18ad230f9e7bf6a77ffc2312c55e-Abstract-Conference.html).
- NeurIPS 2024: [JaxMARL](https://proceedings.neurips.cc/paper_files/paper/2024/hash/5aee125f052c90e326dcf6f380df94f6-Abstract-Datasets_and_Benchmarks_Track.html).
- ICLR 2021: [DOP](https://iclr.cc/virtual/2021/poster/2751), [QPLEX](https://iclr.cc/virtual/2021/poster/3237), [RODE](https://iclr.cc/virtual/2021/poster/2717).
- ICLR 2022: [Trust Region Policy Optimisation](https://iclr.cc/virtual/2022/poster/6244), [Online Ad Hoc Teamwork](https://iclr.cc/virtual/2022/poster/7013).
- ICLR 2025: [Multi-agent cooperation through learning-aware policy gradients](https://proceedings.iclr.cc/paper_files/paper/2025/hash/718a3e764e63a130323c5b5abf4ac332-Abstract-Conference.html), [ExpoComm](https://proceedings.iclr.cc/paper_files/paper/2025/hash/099ca577bb4201168ce2fb973ae5e94e0a9074cd-Abstract-Conference.html).
