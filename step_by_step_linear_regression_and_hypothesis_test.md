# Step-by-Step Linear Regression and Hypothesis Test

This document walks through a **simple linear regression analysis**, followed by a **hypothesis test on the slope** and related statistical concepts.

---

## 1. Percentage Points for the t-Distribution

To find critical values for the *t*-distribution:

- Refer to the **Cambridge PDF**
- Page marked **45** in the document (actual **PDF page 47**)
- Section titled:

> **"10. Distribution points for the t-distribution"**

These tables provide critical *t*-values for different significance levels (α) and degrees of freedom.

---

## 2. Degrees of Freedom (df)

### One-Sample and Paired t-Tests
- **One-sample t-test**:  
  df = n - 1 (estimate one mean)
- **Paired t-test**:  
  df = n - 1 (differences treated as one sample)

### Two-Sample t-Tests and Regression
- **Two-sample t-test**:  
  df = n₁ + n₂ - 2 (estimate two means)
- **Regression t-test (slope)**:  
  df = n - 2 (estimate intercept and slope)

---

## 3. Example Data

**X**: Body Weight (kg)  
**Y**: Total Lift (Squat + Bench + Deadlift) in kg

| Lifter | X (Body Weight) | Y (Total Lift) |
|--------|-----------------|----------------|
| A      | 60              | 400            |
| B      | 70              | 500            |
| C      | 80              | 550            |
| D      | 90              | 600            |
| E      | 100             | 650            |

---

## 4. Step 1: Calculate Basic Sums

- n = 5
- ΣX = 60 + 70 + 80 + 90 + 100 = 400
- ΣY = 400 + 500 + 550 + 600 + 650 = 2700
- ΣX² = 60² + 70² + 80² + 90² + 100² = 33000
- ΣY² = 400² + 500² + 550² + 600² + 650² = 1502500
- ΣXY = (60×400) + (70×500) + (80×550) + (90×600) + (100×650) = 227000

---

## 5. Step 2: Calculate Sum of Squares

SSₓₓ = ΣX² - (ΣX)²/n = 33000 - 400²/5 = 33000 - 32000 = 1000

SSᵧᵧ = ΣY² - (ΣY)²/n = 1502500 - 2700²/5 = 1502500 - 1458000 = 44500

SSₓᵧ = ΣXY - (ΣX)(ΣY)/n = 227000 - (400 × 2700)/5 = 227000 - 216000 = 11000

---

## 6. Step 3: Calculate Regression Coefficients

b₁ = SSₓᵧ / SSₓₓ = 11000 / 1000 = 11

X̄ = 400 / 5 = 80

Ȳ = 2700 / 5 = 540

b₀ = Ȳ - b₁ X̄ = 540 - (11 × 80) = 540 - 880 = -340

### Regression Equation

Ŷ = -340 + 11X

---

## 7. Step 4: Predicted Values and Residuals

| X   | Y   | Ŷ   | e = Y − Ŷ | e²    |
|-----|-----|-----|-----------|-------|
| 60  | 400 | 320 | 80        | 6400  |
| 70  | 500 | 430 | 70        | 4900  |
| 80  | 550 | 540 | 10        | 100   |
| 90  | 600 | 650 | -50       | 2500  |
| 100 | 650 | 760 | -110      | 12100 |

---

## 8. Step 5: Calculate SSE and MSE

SSE = Σe² = 6400 + 4900 + 100 + 2500 + 12100 = 26000

MSE = SSE / (n-2) = 26000 / 3 ≈ 8666.67

s = √MSE ≈ √8666.67 ≈ 93.10

---

## 9. Step 6: Hypothesis Test for the Slope

### Hypotheses
- H₀: β₁ = 0
- H₁: β₁ ≠ 0

### Standard Error of the Slope

s_{b₁} = s / √SSₓₓ = 93.10 / √1000 ≈ 2.944

### Test Statistic

t = (b₁ - 0) / s_{b₁} = 11 / 2.944 ≈ 3.736

### Critical Value
- Significance level: α = 0.05
- Degrees of freedom: df = 3
- Critical value: t_{0.025,3} = 3.182

### Decision
Since |t| = 3.736 > 3.182, **reject H₀**.

**Conclusion**: There is a statistically significant relationship between body weight and total lift.

---

## 10. Step 7: Confidence Interval for the Slope

95% CI = b₁ ± t_{α/2} × s_{b₁}  
= 11 ± (3.182 × 2.944) ≈ 11 ± 9.37 = (1.63, 20.37)

---

## 11. Step 8: Goodness of Fit

SST = SSᵧᵧ = 44500

SSR = SST - SSE = 44500 - 26000 = 18500

R² = SSR / SST = 18500 / 44500 ≈ 0.4157

### Interpretation
**41.57%** of the variation in total lift is explained by body weight.

---

## 12. Summary of All Formulas

### Core Sums of Squares
- SSₓₓ = ΣX² - (ΣX)²/n
- SSᵧᵧ = ΣY² - (ΣY)²/n
- SSₓᵧ = ΣXY - (ΣX)(ΣY)/n

### Regression Coefficients
- b₁ = SSₓᵧ / SSₓₓ
- b₀ = Ȳ - b₁ X̄

### Prediction and Residuals
- Ŷᵢ = b₀ + b₁ Xᵢ
- eᵢ = Yᵢ - Ŷᵢ

### Error Measures
- SSE = Σeᵢ²
- MSE = SSE / (n-2)
- s = √MSE

### Hypothesis Test on Slope
- SE = s / √SSₓₓ
- t = b₁ / SE (for H₀: β₁ = 0)

### Coefficient of Determination
- R² = 1 - SSE / SSᵧᵧ (or SSR / SST)

---

## 13. Formulas for Testing the Slope

For testing H₀: β₁ = 0, you need:

1. SSE = Σ(Yᵢ - Ŷᵢ)²
2. MSE = SSE / (n-2)
3. s = √MSE
4. SE = s / √SSₓₓ
5. t = b₁ / SE

---

## 14. Further Explanation about the Slope

Variation means how much the values of a variable differ from their average. Variation is always about Y, not X.

### The Fundamental Decomposition

SST = SSR + SSE

- **SST**: Total variation in Y
- **SSR**: Variation in Y explained by X
- **SSE**: Variation in Y not explained by X

---

## 15. R² Connects Everything

R² = SSR / SST = 1 - SSE / SST

- R² ≈ 0.42 → 42% of Y variation explained
- R² = 1 → perfect explanation
- R² = 0 → X explains nothing
