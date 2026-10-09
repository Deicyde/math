# OpenAI math: Comparator fixes

This is a mirror of [OpenAI's math repository](https://github.com/openai/math) that tries to fix all the Comparator challenges, following [issues raised by Alex Meiburg](https://x.com/Timeroot/status/2108437139742691827). Everything else is unchanged from OpenAI's commit [`fd4aeeb`](https://github.com/openai/math/tree/fd4aeeb2ee4fc729c18d98444fed42fd0529eeeb). Their README is [here](https://github.com/openai/math/blob/main/README.md).

## Changes from OpenAI's repo

1. [#1](https://github.com/Deicyde/math/pull/1), [`957d817`](https://github.com/Deicyde/math/commit/957d8171d3e861f181f3ae6fa6baf0ac8f858c32): remove the definition holes. Comparator never checks the body of a definition listed in `definition_names`, so a solution could redefine it. For example, `ProperColoring := False` passed EuclideanFiveColor. The list is removed from 8 challenges (Brenier, EuclideanFiveColor, KServer, LogspaceEquality, Naimark, OccupiedOverlap, Rokhlin, SpinAngle) and emptied in the only 2 others that had one; every other config already had `[]`. Of those 2, DefocusingNLS now fails, because its challenge has a `sorry` inside `sobolevProduct`. ElementaryPositivity now checks nothing, because its hole was its only target.
2. [#2](https://github.com/Deicyde/math/pull/2), [`b724aff`](https://github.com/Deicyde/math/commit/b724aff3e1730b5d7ce9fc2690b03fd9c78f4330): fix OccupiedOverlap in the solution. 
3. [#3](https://github.com/Deicyde/math/pull/3), [`4fba076`](https://github.com/Deicyde/math/commit/4fba076174369a096df31c4a7253c4e144fdc984): fix SpinAngle in the solution. 
4. [#4](https://github.com/Deicyde/math/pull/4) (open), [`638b35a`](https://github.com/Deicyde/math/commit/638b35a2b17c7d70abbec6cc111eb4ddb71065c2): remove `definition_names` from the other 403 challenges. 401 of them had an empty list. DefocusingNLS will fail, because its challenge has a `sorry` inside `sobolevProduct`. ElementaryPositivity will check nothing, because its hole was its only target.
5. This README.

With 1–3, 9/10 of the challenges in #1 pass Comparator with no `definition_names`, and the challenge files are unchanged. Setup: Lean v4.34.1, Mathlib `d13f23b7`, Comparator `d03acab`. We are still waiting on DefocusingNLS.
