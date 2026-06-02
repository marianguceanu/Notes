---
author: Racoți Diana, Guceanu Marian
date: Car Fuel Consumption
paging: slide %d / %d
---

# 1. The research question
## "Determine which technical characteristics of passenger cars influence fuel consumption."
- **Dependent** variables
    - Fuel consumption (L/100km)
- **Independent** variables:
    - Power *(HP)*
    - Weight *(kg)*
    - Transmission type *(Manual vs Automatic)*
    - Fuel type *(Petrol vs Diesel)*

---

# 2. Hypotheses
## Hypotheses H1-H4
  **Variable**          **Expected Effect**
<br>
- *Power*           *H1*: More powerful engines should consume more fuel
- *Weight*          *H2*: Heavier cars should require more energy 
- *Manual*          *H3*: May affect efficiency depending on driving 
- *Petrol*          *H4*: Typically consumes more than diesel

---

# 3. The sample (Observations)
- 30 passenger cars
- Different manufacturers
- Cross-sectional data
- Data collected from automotive databases
- Mix of petrol/diesel and manual/automatic vehicles

---


# 4. Regression model(1) and estimated equation(2)
- For ease of read, let us denote:  
    - FuelConsumption -> *FC*
    - Power           -> *Pw*
    - Weight          -> *W* 
    - Manual          -> *M* 
    - Petrol          -> *Pe*
- (1) FC = **β0**    +  **β1**    ⋅*Pw*  +  **β2**      ⋅*W*  +  **β3**  ⋅*M*  +  **β4**  ⋅*Pe*  +  **ε**
- (2) FC = **3.69**  +  **0.0078**⋅*Pw*  +  **0.000084**⋅*W*  +  **0.26**⋅*M*  +  **0.33**⋅*Pe*  +  **0**

---

# 5. Results, interpretation
- *Power* :  +1 hp      -> + **0.0078**     L/100km
- *Weight*:  +1 kg      -> + **0.000084**   L/100km
- *Manual*:  if manual  -> + **0.000084**   L/100km (compared to automatics)
- *Petrol*:  if petrol  -> + **0.33**       L/100km (compared to diesel)

---
# 6. Key finding
```




                        All coefficients have the expected sign, but
                        NONE are statistically significant




```

---

# 7. Statistical significance

  **Variable**          **p-value**
<br>
- *Power*           0.176
- *Weight*          0.924
- *Manual*          0.416
- *Petrol*          0.309

*Interpretation:* 
```
                All p-values are greater than 0.05, therefore 
                NONE of the variables are individually significant
```

---

# 8. Overall model significance
- F Statistic = 0.95
- Significance F = 0.452

*Interpretation:*
```
                Because 0.452 > 0.05, we cannot reject the null hypothesis: 
                all coefficients are jointly equal to zero.

                Therefore, the model is not statistically significant overall.
```

---

# 9. R² interpretation
- R² = 0.132
- Adjusted R² = -0.007

*Interpretation:*
```
                Only about 13% of the variation in fuel consumption 
                is explained by the variables included in the model.

                After accounting for the number of explanatory variables, 
                the model performs no better than a model with no predictors.
```

---

# 10. Why the model performed poorly
- *Small sample*
    - Only 30 observations
- *Missing variables*
    - Engine displacement
    - Vehicle class
    - Hybrid technology
    - Aerodynamics
    - SUV vs Sedan
    - Driving conditions
