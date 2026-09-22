---
name: ccf-paper-writer-humanizer-humanizer
description: "Draft, revise, polish, compress, or adapt academic ML and MARL papers while applying direct, evidence-faithful humanization first. Use for abstracts, introductions, methods, experiments, conclusions, LaTeX prose, reviewer-driven revisions, and MARL writing with CTDE, MAPPO, QMIX, communication, credit assignment, roles, ad hoc teamwork, or benchmarks. Preserve scientific meaning, citations, numbers, uncertainty, and source format."
metadata:
  standalone: true
  humanization_first: true
  evidence_faithful: true
---

# CCF Paper Writer + Humanizer

This is a standalone writing skill. It combines two responsibilities in one entrypoint:

1. **Humanization first:** express the scientific argument directly, remove empty authorial self-defense, and preserve facts, uncertainty, negative results, assumptions, citations, equations, and required disclosures.
2. **Paper writing second:** draft, revise, polish, compress, or presentation-adapt the requested academic text in the user's format.

Humanization is a silent preflight. It does not create a separate report, soften valid criticism, start a confirmation loop, or rewrite text outside the user's authorization.

## Scope and boundaries

Own manuscript prose, argument organization, compression, presentation prose, and writing-facing checks. Do not invent experiments, citations, measurements, reviewer opinions, venue rules, or technical modules. Do not turn a proposed study into a completed result. A supplied manuscript is inspectable by default; editing requires an authorized writing request.

Preserve LaTeX commands, environments, labels, citations, equations, figures, tables, Markdown structure, and requested output format unless restructuring is requested. Keep one canonical output path for file edits and do not create version-suffixed copies without explicit authorization.

## First preflight: direct scientific voice

Before drafting or revising, apply these rules:

- State the problem, insight, mechanism, evidence, and supported implication directly.
- Remove imagined reviewer objections, apology-led novelty claims, empty assurances, repeated caveats, and stacked hedges when they add no scientific content.
- Retain meaningful uncertainty, assumptions, scope conditions, failures, negative results, protocol facts, and mandatory disclosures.
- Do not change “suggests” into “proves,” hide a limitation, or strengthen a result for style.
- Do not add a warning paragraph to the manuscript merely because an evidence gap exists. Narrow the affected claim or report the unresolved decision separately when needed.
- Prefer natural paragraphs over label-heavy fragments, citation dumps, forced three-part lists, number-only abstracts, formula-first explanations, and third-person narration such as “this paper proposes.”

Read `references/humanization-policy.md` for sentence-level decisions and `references/prose-quality-guardrails.md` for the detailed prose gate. Read `references/experiment-discipline.md` when reported experiments, ablations, method identity, or protocol fidelity matter.

## Choose the writing mode

- **polish:** revise a bounded passage in its original format; preserve structure and factual content.
- **draft section:** write a coherent section from supplied evidence and the relevant section module.
- **draft manuscript:** establish venue assumptions, page budget, storyline, citations, method, experiments, analysis, and conclusion; use `TBD` for unavailable evidence.
- **compress:** shorten text while preserving claims, numbers, citations, scope, and logical dependencies.
- **presentation:** adapt supplied research into slide, poster, talk, or Q&A prose without exposing planning notes.

Use only the references needed for the mode:

- Full sections or papers: `references/research-writing-patterns.md`, `references/storyline-blueprint.md`, `references/section-modules.md`, `references/writing-checklists.md`.
- Citation work: `references/citation-workflow.md`; verify every citation key against the user's bibliography.
- Compression: `references/compression-rules.md` and `references/length-budget-policy.md`.
- Venue-aware writing: `references/ccf-a-venue-map.md`, `references/venue-adapters.md`, and the relevant guide under `references/venue-guides/` when present.
- MARL writing: `references/marl-writing-patterns.md`, `references/marl-evidence-checklist.md`, and the matching MARL exemplar card if the task is substantial.
- Local prose diagnostics: `scripts/check_prose_quality.py` when a full section or paper is being checked.

## General workflow

1. Identify the requested artifact, mode, format, target venue, evidence boundary, and target length. Infer routine choices; ask only when a missing decision changes the claim, deliverable, or feasibility.
2. Build the scientific chain before polishing sentences:

   `task -> gap -> root challenge -> insight -> method mechanism -> evidence -> supported implication`

3. For an existing manuscript, edit in place and preserve source structure. For a new manuscript, establish section roles and a claim ledger before expanding prose.
4. For each method module, record its input, operation, output, motivation, technical advantage, and validation pointer. Explain the role of notation before dense equations.
5. For experiments, organize the narrative around effectiveness, causality, generalization/limits, and cost. State the protocol before interpreting the result.
6. Run the relevant prose and claim-evidence checks. Inspect warnings in context; do not rewrite correct scientific language merely to clear a heuristic.
7. Return the requested artifact first. Mention only material changes, validation, and unresolved evidence that affects reliability.

## MARL and multi-agent writing

When the paper concerns MARL, multi-agent games, CTDE, MAPPO/QMIX-style factorization, communication, credit assignment, role discovery, offline or robust MARL, ad hoc teamwork, or MARL benchmarks, load the MARL references listed above.

Before drafting a substantial MARL paper, make the following boundaries explicit when they affect a claim:

- agent count and type;
- observation/action spaces and partial observability;
- shared, individual, shaped, or unavailable rewards;
- centralized-training versus decentralized-execution information;
- parameter sharing or heterogeneity;
- communication topology, bandwidth, delay, and message availability;
- training and evaluation partner distributions;
- benchmark version, scenario generation, split, and seed protocol;
- metric definition and resource denominator;
- baseline identity and implementation parity;
- ablations for each mechanism claim;
- failure cases and scope limits.

Use the recurring MARL story shape:

`setting constraint -> technical failure cause -> one mechanism-level insight -> method or protocol -> effectiveness -> causal ablation -> transfer/stress -> cost and limitation`

Do not turn a stronger score on one benchmark into a general claim about coordination, robustness, transfer, or deployment.

## Citation and evidence rules

Citations support an argument; they do not replace one. Put the claim before the citation, group sources by the capability or limitation they share, and discuss the closest competitor explicitly. Never guess a citation key or add a paper to meet a numeric quota.

For every major claim, check:

```text
Claim:
Location:
Evidence:
Evidence type:
Support: strong / adequate / weak / absent
Required action:
```

Sharpen claims only when the evidence supports them. Narrow or remove unsupported claims. Keep a proposed experiment distinct from an observed result.

## Output contract

Return the actual revised text or requested file in the user's format. For a local edit, do not append a generic process report. For a full manuscript, report the canonical path, substantive changes, relevant validation, and concrete unresolved evidence. Do not label a draft submission-ready unless venue compliance and evidence support that conclusion.
