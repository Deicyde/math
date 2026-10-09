# OpenAI math: Comparator fixes

This is a mirror of [OpenAI's math repository](https://github.com/openai/math) that tries to fix all the Comparator challenges, following [issues raised by Alex Meiburg](https://x.com/Timeroot/status/2108437139742691827). Everything else is unchanged from OpenAI's commit [`fd4aeeb`](https://github.com/openai/math/tree/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb). Their README is [here](https://github.com/openai/math/blob/main/README.md).

## Changes from OpenAI's repo

1. [#1](https://github.com/Deicyde/math/pull/1), [`957d817`](https://github.com/Deicyde/math/commit/957d8171d3e861f181f3ae6fa6baf0ac8f858c32): Remove `definition_names` from all 10 comparator jsons that had one; every other config already had `[]`. Of the changed challenges, DefocusingNLS, SpinAngle, and OccupiedOverlap broke.
2. [#2](https://github.com/Deicyde/math/pull/2), [`3aed706`](https://github.com/Deicyde/math/commit/3aed70691e5357d2c8c0b7ed57425c127b6aedf3): fix OccupiedOverlap in the solution. 
3. [#3](https://github.com/Deicyde/math/pull/3), [`dad1b2e`](https://github.com/Deicyde/math/commit/dad1b2e618ca0447dcf24175ac2f3a56a6680ce1): fix SpinAngle in the solution. 

With 1–3, 8/10 of the challenges in #1 pass Comparator with no `definition_names`, and the challenge files are unchanged. 
DefocusingNLS is still failing due to a `by sorry` in one of its definitions.
ElementaryPositivity now checks nothing, because its hole was its only target.
Setup: Lean v4.34.1, Mathlib `d13f23b7`, Comparator `d03acab`. 
