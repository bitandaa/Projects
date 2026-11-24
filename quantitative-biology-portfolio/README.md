# Quantitative Biology & Computational Biophysics Portfolio

A curated collection of computational biology, biophysics simulation, experimental data analysis, and Bayesian statistical modeling projects developed in Python during my MSc in **Quantitative Biology** at the *Università degli Studi di Milano*.

---

## Projects Overview

| Project | Domain | Key Methods & Concepts | Core Libraries |
| :--- | :--- | :--- | :--- |
| [**AFM PSD Signal Analysis**](./afm-psd-signal-analysis/afm_psd_fitting.ipynb) | Experimental Data Analysis | 5-parameter nonlinear least-squares fitting, asymptotic initial-guess estimation, residual & RMS analysis | `NumPy`, `SciPy`, `Matplotlib` |
| [**2D Particle Diffusion in a Box**](./2d-particle-diffusion/diffusion_in_a_box.ipynb) | Molecular Biophysics | Vectorized random-walk simulation, periodic boundary conditions, spatial variance equilibration, open vs. closed systems | `NumPy`, `Matplotlib` |
| [**DNA Thermodynamics with NUPACK**](./dna-thermodynamics-nupack/dna_thermodynamics_nupack.ipynb) | Molecular Biophysics | MFE structure prediction, partition-function ensemble analysis, concentration-dependent hybridization, genomic specificity | `NUPACK`, `NumPy`, `Matplotlib` |
| [**Animal Hibernation Bayesian Analysis**](./hibernation-bayesian-analysis/hibernation_bayesian_analysis.ipynb) | Biological Data Science | Vectorized `pandas` pipelines, type-hinted & doctested utilities, longitudinal plotting, Bayesian linear regression (MCMC) | `Pandas`, `PyMC`, `ArviZ`, `Matplotlib` |

---

## Project Summaries

### 1. AFM Cantilever PSD Nonlinear Fitting
- **Notebook:** [`afm-psd-signal-analysis/afm_psd_fitting.ipynb`](./afm-psd-signal-analysis/afm_psd_fitting.ipynb)
- Fits a 5-parameter physical model (resonance peak + white noise floor + $1/f$ nonlinear baseline) to 15,886 experimental Atomic Force Microscope (AFM) cantilever deflection PSD points.
- Derives physically grounded initial guesses ($p_0$) from asymptotic limits before running `scipy.optimize.curve_fit`, extracts parameter uncertainties from the covariance matrix, and validates fit quality via residual distribution and RMS error.

### 2. 2D Particle Diffusion Simulation
- **Notebook:** [`2d-particle-diffusion/diffusion_in_a_box.ipynb`](./2d-particle-diffusion/diffusion_in_a_box.ipynb)
- Implements vectorized 2D random walks for $N = 1,000$ particles using `NumPy` to study equilibration dynamics in closed (periodic boundary) and open (infinite-pool) systems.
- Compares spatial variance $\sigma^2(t)$ against the theoretical uniform equilibrium limit ($L^2/12$) across point-source, linear, and uniform-grid initializations.

### 3. DNA Hybridization & Thermodynamics Analysis
- **Notebook:** [`dna-thermodynamics-nupack/dna_thermodynamics_nupack.ipynb`](./dna-thermodynamics-nupack/dna_thermodynamics_nupack.ipynb)
- Uses **NUPACK** to compute Minimum Free Energy (MFE) and ensemble free energies for single-stranded and multi-stranded DNA complexes (up to trimers).
- Evaluates concentration effects ($10^{-6}\,\mathrm{M}$ vs. $10^{-9}\,\mathrm{M}$), samples background interaction energies across 200 random 20-nt sequences, and quantifies probe specificity in a $10^9\,\mathrm{bp}$ genome.

### 4. Animal Hibernation Patterns & Bayesian Modeling
- **Notebook:** [`hibernation-bayesian-analysis/hibernation_bayesian_analysis.ipynb`](./hibernation-bayesian-analysis/hibernation_bayesian_analysis.ipynb)
- Performs end-to-end biological data cleaning, vectorized aggregation, and longitudinal visualization on animal hibernation records.
- Includes a type-hinted, `doctest`-verified moving average utility and a Bayesian linear regression model (`PyMC` + `ArviZ`) estimating post-hibernation body mass from hibernation duration in reproductively active females.

---

## Getting Started

```bash
pip install numpy scipy pandas matplotlib pymc arviz
```

> **Note:** The DNA thermodynamics notebook additionally requires [NUPACK](https://docs.nupack.org/). To re-execute the data analysis notebooks locally, place `noisy_PSD_with_baseline.txt` inside `afm-psd-signal-analysis/` and `hibernation.csv` inside `hibernation-bayesian-analysis/`.
