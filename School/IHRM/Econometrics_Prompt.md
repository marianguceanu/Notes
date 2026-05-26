# Goal of this session
- Overall: Make an econometrics project
- First: Suggest a topic that you would consider suitable
    - If possible, should be real 
- Second: Pick at least 3 variables, 5 would be ideal
    - From the minimum of 3, 2 must be quantitative and 1 qualitative
    - Each variable: min of 15 values
- Third: Only the general model is required

## How to act - what is your role - domains of expertise
- Econometrics
- Researcher
- Project - builder

## Choosing a topic
- Purpose of econometric research is to use regression analysis to:
    - build the best explanatory equation for a particular dependent variable for a particular sample. 
- Choose a field that you find interesting and/or that you know something about 
    - If you are invested in a subject, you're more likely to:
        - Make correct specification choices 
        - Notice subtle indications of data errors or theoretical problems.
- Make sure that the data are available with a reasonable sample (at least 25 observations)
- Avoid topics that are purely descriptive or tautological in nature
    - Look for topics that include one or two hypotheses that you’d like to test
    - Once you find a topic, don’t rush out and run your first regression. 
    - Take your time reviewing all the literature you can find so you get the best results

## Sketch of the research
- Data collecting, analyzing, interpreting
- Choosing the general model – depends on what you want to find out
- Estimating your model
- Writing your model
- Significance of your model
- Estimation and prediction (if the model is significant)
- If the model is not significant find out which is the problem?

## Writing your project report
- Once you’ve finished your research, it is important to write a report on your own results.
- Elements that are recommended to be included in the report:
    - Brief introduction that states the goals of the research, the importance of study. 
        - In this part we formulate the hypothesis of our study.
	- Description of the data, data sources, measurement units, some important parameters and any irregularities with the data.
	- Presentation of a general estimated specification followed by a careful analysis of the regression results including an econometric discussion and an economic one.
	- Short summary/conclusion that includes any recommendations or suggestions for further research.
	- Appendix that includes all data, all regression runs, and all relevant computer output. 

## Research study – a sketch
- Topic: The decision to buy a house. The housing price.
- Hypothesis: The price of the house is influenced by the size, the age of the house, the existence of some facilities and location.
- Variables:
    - Price (thousand dollars) - quantitative
	- Size (square meters) - quantitative
	- Age (years) - quantitative
	- Location – the quality of the neighborhood: dummy variable with 0-bad, 1-good
	- Facilities – the existence of pool: dummy variable with 0-no, 1-yes.
- Data – available on real estate agencies websites
- Brief presentation of data (spreadsheet converted to markdown table): 
|              | Min           | Max           | Average       | Variance      | Standard Deviation | Coefficient of variation|
|------------- | ------------- | ------------- | ------------- | ------------- | ------------------ | ----------------------- |
| Price        | 107           | 503           | 242.3         | 6279.22       | 79.24              | 32.7%                   |
| Size         | 720           | 3269          | 1470.23       | 263252        | 513.08             | 34.9%                   |
| Age          | 1             | 77            | 44.8          | 322.28        | 17.95              | 40.03%                  |
- Choose a specification and estimate your equation. For example:
    - price= 52.931 + 0.103*size + 0.338 * age + 44.35 * facilities + 37.332 * location
    - p1 = 0,000; p2 = 0,2953; p3 = 0.0014; p4 = 0.0183
    - p-value = 0.0000
    - R2 = 0,8578
    - R2-adj = 0.8429
- Test your hypothesis for each coefficient – individual significance: 
    - H0: B1 = 0; H1: B1 > 0
    - H0: B2 = 0; H1: B2 > 0
    - H0: B3 = 0; H1: B3 != 0
    - H0: B4 = 0; H1: B4 != 0
- Test the overall significance of the equation
    - H0: B1 = B2 = B3 = B4 = 0
    - H1: not all parameters are null
- Decide what econometric problems exist in the equation, testing, if appropriate, for: 
    - multicolinearity (always)
    - serial correlation (case of time series data in general)
    - heteroskedasticity (case of cross-sectional data in general)
- Decide: 
    - Accept your first specification as the best one OR 
    - Make a modification in your equation and estimate again
    - Make sure you avoid the temptation to estimate an additional specification „just to see what it looks like”.
- When you have decided on your final specification sketch some economic interpretation
- Finally, develop the above findings in your econometric report. 


