# MARL Claim–Evidence Checklist

Use this checklist for a full MARL manuscript, a substantial section revision, or a MARL writing review. It is an internal evidence contract, not a visible template unless the user asks for an audit.

## Claim record

For every central claim, record:

```text
Claim ID:
Claim:
Setting:
Mechanism:
Evidence type: theorem / controlled ablation / benchmark comparison / transfer / efficiency / qualitative analysis
Evidence location:
Protocol boundary:
Support: strong / adequate / weak / absent
Required action:
```

## Minimum evidence package

- Main comparison uses strong, identity-matched baselines under the same environment, observation, reward, seed, and compute protocol.
- Each method claim has a mechanism-level ablation or a theorem/analysis that actually isolates it.
- Generalization claims identify the held-out dimension: partners, maps, agent count, scenario generation, reward, dynamics, or communication topology.
- Efficiency claims report the resource denominator: environment steps, gradient updates, wall-clock time, communication, memory, or number of parameters.
- Robustness or safety claims specify the perturbation, uncertainty set, constraint, or failure criterion.
- Benchmark claims establish what the protocol measures and why the protocol is valid for the claimed capability.
- Offline MARL claims report data coverage, behavior-policy or dataset assumptions, and how out-of-distribution joint actions are handled.
- Communication claims report topology, message schedule, bandwidth or delay, and whether messages are available during evaluation.
- CTDE claims distinguish centralized information during training from local information at execution.

## Common narrowing actions

- Replace field-wide superiority with benchmark- and protocol-scoped support.
- Replace "improves coordination" with the measured coordination proxy and its evaluation setting.
- Replace "generalizes" with the held-out dimension and observed transfer range.
- Replace "sample efficient" with the sample axis, budget, and comparison protocol.
- Replace "robust" with the tested uncertainty, adversary, perturbation, or constraint.
- Mark a mechanism interpretation as compatible when the ablation does not isolate causality.
- Move an unmeasured deployment or communication claim to future work only when the scope is clear; do not present it as an observed result.
