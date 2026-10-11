# OpenAI math: Comparator fixes

This is a mirror of [OpenAI's math repository](https://github.com/openai/math) that fixes the Comparator challenges that used definition holes, following [issues raised by Alex Meiburg](https://x.com/Timeroot/status/2108437139742691827). Everything else is unchanged from OpenAI's commit [`fd4aeeb`](https://github.com/openai/math/tree/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb). Their README is [here](https://github.com/openai/math/blob/main/README.md).

## Changes from OpenAI's repo

1. [#1](https://github.com/Deicyde/math/pull/1), [`957d817`](https://github.com/Deicyde/math/commit/957d8171d3e861f181f3ae6fa6baf0ac8f858c32): Remove `definition_names` from all 10 comparator jsons that had a non-empty one. Of the changed challenges, DefocusingNLS, SpinAngle, and OccupiedOverlap broke, and ElementaryPositivity lost its only target.
2. [#2](https://github.com/Deicyde/math/pull/2), [`3aed706`](https://github.com/Deicyde/math/commit/3aed70691e5357d2c8c0b7ed57425c127b6aedf3): fix OccupiedOverlap.
3. [#3](https://github.com/Deicyde/math/pull/3), [`dad1b2e`](https://github.com/Deicyde/math/commit/dad1b2e618ca0447dcf24175ac2f3a56a6680ce1): fix SpinAngle.
4. [#6](https://github.com/Deicyde/math/pull/6), [`fcccdda`](https://github.com/Deicyde/math/commit/fcccdda6a55de9bc8e8075c9298f9494603e2438): give ElementaryPositivity a theorem target.
5. [#7](https://github.com/Deicyde/math/pull/7), [`bac8588`](https://github.com/Deicyde/math/commit/bac85884a3a45c02bf27ff44bbaaf8b52b7ec66a): fix DefocusingNLS.

With 1–5, all 10 of the challenges in #1 pass Comparator with no `definition_names`. 

Setup: Lean v4.34.1, Mathlib `d13f23b7`, Comparator `d03acab`, lean4export `076e8e5`. The runs were on macOS, where Comparator's sandbox is not available, and used the Lean kernel only. The other 406 challenges were not run.
