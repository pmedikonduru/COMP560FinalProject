# Bayesian Network Inference for Diabetes Risk Prediction

**Authors:** Pranav Medikonduru, Lucas Engel, Alexandra Gonzales

## Overview

This project implements a Bayesian Network to model diabetes risk using CDC's 2015 BRFSS dataset (253,680 adults). We compare exact inference (Variable Elimination) with approximate inference (Likelihood Weighting).

## Dataset

- **9 variables:** Diabetes, BMI, HighBP, HighChol, Smoker, PhysActivity, Age, HeartDisease, Stroke
- **BMI discretized:** normal (<25), overweight (25-30), obese (>30)

## Network Structure

```
Lifestyle → Physiological Markers → Disease Outcomes
Age, Smoker, PhysActivity → BMI, HighChol, HighBP → Diabetes → HeartDisease, Stroke
```

## Key Results

- **High-risk profile** (obese, inactive, high cholesterol): 37.8% diabetes risk
- **Low-risk profile** (normal weight, active): 5.3% diabetes risk
- **Variable Elimination:** Fast exact inference (~50ms)
- **Likelihood Weighting (N=5000):** L1 error < 0.01, runtime ~86s

## Implementation

1. Parameter learning with Laplace smoothing
2. Variable elimination for exact inference
3. Likelihood weighting with convergence analysis (N=100 to 10,000)
4. 5 medical queries testing different risk profiles

## Dependencies

```python
pandas, numpy, matplotlib, itertools, time
```

## Usage

Run `560final_project.ipynb` to:
- Learn CPTs from data
- Execute Variable Elimination and Likelihood Weighting
- Generate convergence plots and comparison tables

## References

CDC BRFSS 2015, Pearl (1988), Koller & Friedman (2009)
