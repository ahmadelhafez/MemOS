# TanDamn Proposal-Only Integration

This branch adapts the local MemOS plugin as a candidate proposal engine for
TanDamn Mortal Memory. TanDamn remains the authority and audit system.

## Boundary

- Set `algorithm.proposalOnly: true` for every TanDamn-owned runtime.
- MemOS may collect evidence, score patterns, and produce candidates.
- MemOS may not promote policies, feedback experiences, or skills to `active`.
- TanDamn rejects donor status, approval, activation, and decision fields.
- A candidate becomes active only after TanDamn records past and unseen
  rehearsals, a teach-back, and Ahmad's explicit approval.
- TanDamn reopens an active contract when its prediction misses or its review
  or expiry boundary is reached.

Use `examples/tandamn-proposal-only.config.yaml` as the authority-safe config
overlay. This file does not include credentials, model endpoints, or secrets.

## Verification

```text
pnpm run lint
pnpm exec vitest run tests/unit/config/load.test.ts tests/unit/memory/l2/gain.test.ts tests/unit/skill/lifecycle.test.ts tests/unit/experience/feedback-builder.test.ts
```

The TanDamn repository independently tests the intake gateway against donor
authority injection and donor-unavailable failure cases.
