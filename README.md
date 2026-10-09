# OpenAI math: Comparator fixes

This is a mirror of [OpenAI's math repository](https://github.com/openai/math) that tries to fix all the Comparator challenges, following [issues raised by Alex Meiburg](https://x.com/Timeroot/status/2108437139742691827). Everything else is unchanged from OpenAI's commit [`fd4aeeb`](https://github.com/openai/math/tree/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb). Their README is [here](https://github.com/openai/math/blob/main/README.md).

## Changes from OpenAI's repo

1. [#1](https://github.com/Deicyde/math/pull/1), [`957d817`](https://github.com/Deicyde/math/commit/957d8171d3e861f181f3ae6fa6baf0ac8f858c32): remove the definition holes. Comparator never checks the body of a definition listed in `definition_names`, so a solution could redefine it. For example, `ProperColoring := False` passed EuclideanFiveColor. The list is removed from 8 challenges (Brenier, EuclideanFiveColor, KServer, LogspaceEquality, Naimark, OccupiedOverlap, Rokhlin, SpinAngle) and emptied in the only 2 others that had one; every other config already had `[]`. Of those 2, DefocusingNLS now fails, because its challenge has a `sorry` inside `sobolevProduct`. ElementaryPositivity now checks nothing, because its hole was its only target.
2. [#2](https://github.com/Deicyde/math/pull/2), [`3aed706`](https://github.com/Deicyde/math/commit/3aed70691e5357d2c8c0b7ed57425c127b6aedf3): fix OccupiedOverlap in the solution. `RowColumn/Basic.lean` writes out the `2` in `Real.log (… + 2)` using the challenge's auxiliary lemma `hilbertEquiv._proof_1`, so challenge and solution elaborate to the same term.
3. [#3](https://github.com/Deicyde/math/pull/3), [`dad1b2e`](https://github.com/Deicyde/math/commit/dad1b2e618ca0447dcf24175ac2f3a56a6680ce1): fix SpinAngle in the solution. `SpinAngle/Core.lean` closes and reopens its namespace, so `occupiedRow` and `missingInRow` get the same universe names as in the challenge.
4. This README.

With 1–3, all 8 challenges whose list was removed pass Comparator, and the challenge files are unchanged. Setup: Lean v4.34.1, Mathlib `d13f23b7`, Comparator `d03acab`.
