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
  $$ df = n - 1 $$ (estimate one mean)
- **Paired t-test**:  
  $$ df = n - 1 $$ (differences treated as one sample)

### Two-Sample t-Tests and Regression
- **Two-sample t-test**:  
  $$ df = n_1 + n_2 - 2 $$ (estimate two means)
- **Regression t-test (slope)**:  
  $$ df = n - 2 $$ (estimate intercept and slope)

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

- $$ n = 5 $$
- $$ \sum X = 60 + 70 + 80 + 90 + 100 = 400 $$
- $$ \sum Y = 400 + 500 + 550 + 600 + 650 = 2700 $$
- $$ \sum X^2 = 60^2 + 70^2 + 80^2 + 90^2 + 100^2 = 33000 $$
- $$ \sum Y^2 = 400^2 + 500^2 + 550^2 + 600^2 + 650^2 = 1502500 $$
- $$ \sum XY = (60\times400) + (70\times500) + (80\times550) + (90\times600) + (100\times650) = 227000 $$

---

## 5. Step 2: Calculate Sum of Squares

$$
SS_{XX} = \sum X^2 - \frac{(\sum X)^2}{n} = 33000 - \frac{400^2}{5} = 33000 - 32000 = 1000
$$

$$
SS_{YY} = \sum Y^2 - \frac{(\sum Y)^2}{n} = 1502500 - \frac{2700^2}{5} = 1502500 - 1458000 = 44500
$$

$$
SS_{XY} = \sum XY - \frac{(\sum X)(\sum Y)}{n} = 227000 - \frac{400 \times 2700}{5} = 227000 - 216000 = 11000
$$

---

## 6. Step 3: Calculate Regression Coefficients

$$
b_1 = \frac{SS_{XY}}{SS_{XX}} = \frac{11000}{1000} = 11
$$

$$
\bar{X} = \frac{400}{5} = 80
$$

$$
\bar{Y} = \frac{2700}{5} = 540
$$

$$
b_0 = \bar{Y} - b_1 \bar{X} = 540 - (11 \times 80) = 540 - 880 = -340
$$

### Regression Equation

$$
\hat{Y} = -340 + 11X
$$

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

$$
SSE = \sum e^2 = 6400 + 4900 + 100 + 2500 + 12100 = 26000
$$

$$
MSE = \frac{SSE}{n-2} = \frac{26000}{3} \approx 8666.67
$$

$$
s = \sqrt{MSE} = \sqrt{8666.67} \approx 93.10
$$

---

## 9. Step 6: Hypothesis Test for the Slope

### Hypotheses
- $$ H_0: \beta_1 = 0 $$
- $$ H_1: \beta_1 \neq 0 $$

### Standard Error of the Slope

$$
s_{b_1} = \frac{s}{\sqrt{SS_{XX}}} = \frac{93.10}{\sqrt{1000}} \approx 2.944
$$

### Test Statistic

$$
t = \frac{b_1 - 0}{s_{b_1}} = \frac{11}{2.944} \approx 3.736
$$

### Critical Value
- Significance level: $$ \alpha = 0.05 $$
- Degrees of freedom: $$ df = 3 $$
- Critical value: $$ t_{0.025,3} = 3.182 $$

### Decision
Since $$ |t| = 3.736 > 3.182 $$, **reject $$ H_0 $$**.

**Conclusion**: There is a statistically significant relationship between body weight and total lift.

---

## 10. Step 7: Confidence Interval for the Slope

$$
95\%\ CI = b_1 \pm t_{\alpha/2} \times s_{b_1}
$$

$$
= 11 \pm (3.182 \times 2.944) \approx 11 \pm 9.37 = (1.63, 20.37)
$$

---

## 11. Step 8: Goodness of Fit

$$
SST = SS_{YY} = 44500
$$

$$
SSR = SST - SSE = 44500 - 26000 = 18500
$$

$$
R^2 = \frac{SSR}{SST} = \frac{18500}{44500} \approx 0.4157
$$

### Interpretation
**41.57%** of the variation in total lift is explained by body weight.

---

## 12. Summary of All Formulas

### Core Sums of Squares
- $$ SS_{XX} = \sum X^2 - \frac{(\sum X)^2}{n} $$
- $$ SS_{YY} = \sum Y^2 - \frac{(\sum Y)^2}{n} $$
- $$ SS_{XY} = \sum XY - \frac{(\sum X)(\sum Y)}{n} $$

### Regression Coefficients
- $$ b_1 = \frac{SS_{XY}}{SS_{XX}} $$
- $$ b_0 = \bar{Y} - b_1 \bar{X} $$

### Prediction and Residuals
- $$ \hat{Y}_i = b_0 + b_1 X_i $$
- $$ e_i = Y_i - \hat{Y}_i $$

### Error Measures
- $$ SSE = \sum e_i^2 $$
- $$ MSE = \frac{SSE}{n-2} $$
- $$ s = \sqrt{MSE} $$

### Hypothesis Test on Slope
- $$ s_{b_1} = \frac{s}{\sqrt{SS_{XX}}} $$
- $$ t = \frac{b_1}{s_{b_1}} $$ (for $$ H_0: \beta_1 = 0 $$)

### Coefficient of Determination
- $$ R^2 = 1 - \frac{SSE}{SS_{YY}} $$ (or $$ \frac{SSR}{SST} $$)

---

## 13. Formulas for Testing the Slope

For testing $$ H_0: \beta_1 = 0 $$, you need:

1. $$ SSE = \sum (Y_i - \hat{Y}_i)^2 $$
2. $$ MSE = \frac{SSE}{n-2} $$
3. $$ s = \sqrt{MSE} $$
4. $$ s_{b_1} = \frac{s}{\sqrt{SS_{XX}}} $$
5. $$ t = \frac{b_1}{s_{b_1}} $$

---

## 14. Further Explanation about the Slope

Variation means how much the values of a variable differ from their average. Variation is always about Y, not X.

### The Fundamental Decomposition

$$
SST = SSR + SSE
$$

- **SST**: Total variation in Y
- **SSR**: Variation in Y explained by X
- **SSE**: Variation in Y not explained by X

---

## 15. R² Connects Everything

$$
R^2 = \frac{SSR}{SST} = 1 - \frac{SSE}{SST}
$$

- $$ R^2 \approx 0.42 $$ → 42% of Y variation explained
- $$ R^2 = 1 $$ → perfect explanation
- $$ R^2 = 0 $$ → X explains nothing
