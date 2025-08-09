# <Project Name>

> Team: **<Team Name>**  
> WISER Quantum Walks & Monte Carlo Challenge

---

## Team Members

| Name | WISER Enrollment ID | Role (optional) |
|---|---|---|
| <Member 1 Full Name> | <WISER-XXXX> | <e.g., Circuits/Algorithms> |
| <Member 2 Full Name> | <WISER-XXXX> | <e.g., Simulation/Analysis> |
| <Member 3 Full Name> | <WISER-XXXX> | <e.g., Noise/Visualization> |

---

## Project Summary (≈500 words)

<!-- Replace everything below with your own narrative. Aim for ~500 words. -->

**Problem & Goal.**  
Briefly describe the goal of the challenge and what your project set out to demonstrate: implementing a scalable quantum Galton board, matching target distributions (Gaussian/binomial, exponential, and a Hadamard quantum walk), and evaluating noise-resilient performance.

**Approach.**  
Summarize the approach for each task:
- **Task 1–2 (Baseline Galton board):** One-hot position encoding, coin reset at each layer, verification vs. binomial using TV/JS/W1, χ² goodness-of-fit with tail merging.
- **Task 3 (Alternative distributions):** Exponential target via monotone logistic bias \(p_\ell=\sigma(a+b\ell)\) → \(\theta_\ell = 2\arcsin\sqrt{p_\ell}\); proper DTQW Hadamard walk with conditional shifts (CSWAP cascades), one-hot decode, and comparison against classical RW.
- **Task 4 (Noise & optimization):** Aer noise model (depolarizing + thermal relaxation + readout), hardware-aware basis/transpile, simple error mitigation (multi-run averaging / ZNE demo), and quantitative impact via TV/JS/W1.
- **Task 5 (Stats & uncertainty):** Minimal, consistent metrics on common support; bootstrap confidence for means/stds where needed.

**Results.**  
Call out key quantitative highlights (e.g., near-binomial match at n=12 with JS < 0.1; exponential fit distances; DTQW wider spread than classical; noise deltas). Mention figures/plots the reviewers can find in the notebook.

**What’s Novel / Useful.**  
Point to the paper-aligned one-hot design, stable discrete-distance metrics (TV, JS distance, Wasserstein-1 via CDFs), and a compact noise demo that’s easy to reproduce.

**Limitations & Future Work.**  
Briefly note limits (CSWAP depth, edge effects for small position registers, approximate noise model) and next steps (device execution via IBM Runtime, better error mitigation/calibration, larger n).

---

## Project Presentation Deck

- Deck (PDF or Google Slides): **[Link to presentation]**  
  *(If in-repo, place it under `/docs/` and link like `docs/presentation.pdf`.)*

---

## Repository Structure

