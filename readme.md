# <Project Name>

> Team: **BIASQ**  
> WISER Quantum Walks & Monte Carlo Challenge

---

## Team Members

| Name | WISER Enrollment ID |
|---|---|
| Nikhila Yeturi | gst-RTmFG919DXao1Xe |
| Pranav | gst-JeRpsGICDUrvULg |

---

## Problem & Goal  
The goal of this project was to design and simulate a scalable **Quantum Galton Board** framework that can reproduce and compare different target probability distributions, Gaussian/binomial, exponential, and quantum walk while analyzing performance under realistic noise conditions. The challenge included validating the quantum implementation against classical distributions, quantifying similarity using robust statistical metrics, and demonstrating a minimal yet reproducible workflow that integrates visualization, performance evaluation, and Monte Carlo–style statistical analysis.  

---

## Approach  

### **Task 1–2 (Baseline Galton Board)**  
- Implemented a one-hot position encoding scheme to represent ball positions at each step.  
- Reset coin qubit at each layer to avoid correlation buildup.  
- Collected simulation results for multiple distributions and computed:
  - **Total Variation Distance (TV)**
  - **Jensen–Shannon Distance (JS)**
  - **Wasserstein-1 Distance (W1)**
- Compared the measured distribution against the binomial target and performed a χ² goodness-of-fit test with tail merging for low-count bins.  

### **Task 3 (Alternative Distributions)**  
- Generated an **Exponential target distribution** using a monotone logistic bias function:  
  \[
  p_\ell = \sigma(a + b\ell), \quad \theta_\ell = 2 \arcsin \sqrt{p_\ell}
  \]  
- Implemented a proper **Discrete-Time Quantum Walk (DTQW)** with Hadamard coin and conditional shifts using CSWAP cascades.  
- Decoded the final quantum state to extract position probabilities.  
- Compared the DTQW results against a classical random walk to highlight spread and shape differences.

### **Task 4 (Noise & Optimization)**  
- Integrated **Qiskit Aer noise models** with depolarizing errors, thermal relaxation, and readout errors.  
- Applied hardware-aware transpilation to reduce circuit depth and improve execution fidelity.  
- Demonstrated simple error mitigation strategies, including multi-run averaging and a placeholder for Zero Noise Extrapolation (ZNE).  
- Measured the effect of noise by comparing TV, JS, and W1 distances pre- and post-noise simulation.

### **Task 5 (Stats & Uncertainty)**  
- Created a **minimal distribution summary function** that:
  - Aligns all probability mass functions (PMFs) to a common integer bin support.
  - Produces side-by-side bar plots for each distribution.
  - Computes pairwise distances (TV, JS) between all distributions.
  - Outputs descriptive statistics (mean, standard deviation, sample count).
- Metrics were computed on consistent bins to avoid binning bias, enabling fair comparisons.

---

## Results  
### **Gaussian/Binomial Case (n=12)**  
- Achieved a near-perfect binomial shape with **JS distance = 0.079** vs. exponential, and **JS distance = 0.035** vs. quantum walk.  
- **Total Variation (TV)** for Gaussian vs quantum walk: **0.041** (low).  

### **Exponential Target**  
- Produced using logistic biasing; distribution skewed towards lower positions as expected.  
- **JS distance** with quantum walk = **0.684**, showing strong statistical divergence.  

### **Quantum Walk vs. Classical**  
- Quantum walk showed broader and more irregular spread compared to the symmetric binomial.  
- Classical random walk remained symmetric and concentrated near the center.  
- Pairwise metrics: **TV = 0.231**, **JS = 0.218**, **W1 = 0.487**.  

### **Noise Impact**  
- Inclusion of depolarizing + relaxation noise increased both TV and JS distances across all comparisons.  
- **Noiseless vs Noisy**: **TV = 0.1421**, **JS = 0.0983**, **W1 = 0.2117**.  
- Quantum walk suffered greater degradation under noise compared to exponential/gaussian, due to its reliance on interference patterns.  

### **Visualization & Metrics**  
- Minimal plots provided clear side-by-side probability comparisons.  
- Summary tables made it easy to compare statistical metrics across tasks.  
- Monte Carlo sampling (`shots = 20000` and `shots = 10000`) ensured smooth PMFs and stable distance estimates.  

## Project Presentation Deck

- Deck (PDF or Google Slides): Please go through the available Pitch deck in the files above.  

