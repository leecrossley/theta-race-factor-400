# Even 800H can miss a move in the 547/727 prime race

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24411635.svg)](https://doi.org/10.5281/zenodo.24411635)

This result is now maintained in [theta-host-split-inert-race](https://github.com/leecrossley/theta-host-split-inert-race/tree/main/results/theta-race-factor-400). This repository is archived and keeps its releases and DOI.

Assume the generalised Riemann hypothesis (GRH) for the primitive Dirichlet functions in the 547/727 race and its base field, including the Riemann zeta function. Alpöge's announced Dirichlet GRH theorem supplies this input. [Announcement](https://alpo.ge/remark.pdf) [Independent formal checks](https://math.mit.edu/~drew/grh/)

**A factor of 400 fails in both directions at explicit starting heights.** In the 547/727 prime-ideal race with $`b=r=2`$, every eligible doubling gains at one height and every eligible doubling loses at another. The two certified log intervals have widths $`6`$ and $`45/8`$, both greater than $`\log200`$. [Theorem and proof](PROOF.md)

| Starting height $`H`$ | Deadline for $`2y`$, with $`y\gt H`$ | Change in $`S(2y)-S(y)`$ for every eligible start |
|---|---|---|
| $`e^{469417229.340}/(2\sqrt2)`$ | $`2e^6 H=806.857586\ldots H`$ | Gain of more than $`0.1\log2`$ |
| $`e^{484947092.225}/(2\sqrt2)`$ | $`2e^{45/8}H=554.544569\ldots H`$ | Loss of more than $`0.1\log2`$ |

There are also arbitrarily large starting heights with only gains by $`2e^6H`$, and others with only losses by that same deadline. Thus a factor guaranteeing a gain, or one guaranteeing a loss, of more than $`1.9735\log2`$ after **every** height must exceed $`2e^6`$. The previous obstruction was $`392.7397507\ldots`$. [Previous result](https://github.com/leecrossley/theta-race-distant-interval/blob/527fffe7b7808457b47a292144fea96b556158a8/PROOF.md) [Prior-work comparison](PRIOR-WORK.md)

The proof uses four cosine moments to bound every omitted zero and certifies all points of both intervals. A second calculation uses two real integrals, Cauchy–Schwarz and direct interval evaluations of the sines. The two comparisons with actual prime scores require Dirichlet GRH. [Zero brackets](evidence/zero-brackets.tsv) [Verification output](evidence/check.txt) [Upstream verification](https://math.mit.edu/~drew/grh/)

## Replay

In a Python 3.10+ virtual environment run

```sh
python -m pip install -r requirements.txt
python check_zeros.py
python paired_windows.py
python cell_check.py
python check_source.py
```

For a full replay on x86-64 Linux run `bash verify-release.sh` with Git, curl, tar and zstd installed. With Lean 4.33.1 on PATH and a clean, built Git checkout of Mathlib at commit `0df444a360eaa60ab8c11dca51a86af692955474`, run `bash verify-release.sh /path/to/mathlib4`. An optional second argument names the directory of the five upstream records. When the live audit logs change, the script checks archived copies against the published hashes. Set `THETA_WORKERS` to change the number of zero-check processes. The script checks file hashes, verifies the source records, repeats the numerical proofs and replays six local Lean deductions. The explicit formula and its analytic consequences are written proofs. [Local Lean proofs](PairedWindows.lean) [File hashes](SHA256SUMS)
