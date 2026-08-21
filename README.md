# FIFA World Cup Prediction Model: 2026 Evaluation and 2027 Women's World Cup Prediction

## Project Overview

This project was developed as a Data Science Capstone project to investigate how different statistical and machine learning methods perform when predicting international soccer matches.

The project trains and compares five prediction models using historical FIFA World Cup and UEFA European Championship matches. The trained models are then evaluated against the actual results of the 2026 FIFA World Cup.

The final stage of the project extends the methodology to women's international soccer with the goal of developing a prediction model for the 2027 FIFA Women's World Cup.

## Research Questions

This project focuses on three main questions:

1. How accurately can historical international soccer data predict future World Cup matches?
2. Do more complex machine learning models outperform traditional statistical approaches such as Poisson regression?
3. Can the modeling framework developed using men's international soccer be adapted to predict the 2027 FIFA Women's World Cup?

## Historical Dataset

The men's training dataset contains 358 international tournament matches:

- FIFA World Cups: 2010, 2014, 2018, and 2022
- UEFA European Championships: 2020 and 2024

The historical match data was obtained from the OpenFootball project.

The dataset includes match results along with engineered features describing the relative strength and recent performance of each team.

Examples of model features include:

- ELO rating
- ELO rating difference
- Recent form points
- Average goals scored
- Average goals conceded
- Recent goal difference
- Win rate
- Number of recent matches
- Knockout-stage indicator

## Models

Five prediction approaches were evaluated:

### Logistic Regression

Logistic Regression provides a relatively simple baseline classification model for predicting whether Team A wins, the match ends in a draw, or Team B wins.

### Random Forest

Random Forest combines multiple decision trees to capture nonlinear relationships between team characteristics and match outcomes.

### Gradient Boosting

Gradient Boosting sequentially builds decision trees designed to correct errors made by previous trees.

### XGBoost

XGBoost provides a more advanced gradient-boosted decision tree approach and was included to determine whether additional model complexity improves World Cup prediction accuracy.

### Poisson Model

The Poisson model estimates the expected number of goals scored by each team. Those expected goal distributions are then used to calculate the probability of a Team A win, draw, or Team B win.

Unlike the classification models, the Poisson approach directly models soccer goal scoring.

## 2026 FIFA World Cup Evaluation

After training the models using historical tournament data, they were tested against the actual results of the 2026 FIFA World Cup.

The evaluation included:

- 72 group-stage matches
- 32 knockout-stage matches
- 104 total matches
- 48 national teams

The models were evaluated using prediction accuracy and Macro F1 score.

## Final Results

| Model | Correct Predictions | Accuracy | Macro F1 |
|---|---:|---:|---:|
| Poisson | 63 / 104 | 60.58% | 0.455 |
| Gradient Boosting | 54 / 104 | 51.92% | 0.481 |
| Logistic Regression | 46 / 104 | 44.23% | 0.426 |
| Random Forest | 46 / 104 | 44.23% | 0.396 |
| XGBoost | 45 / 104 | 43.27% | 0.385 |

## Key Finding

The Poisson model produced the highest overall prediction accuracy, correctly predicting 63 of the 104 matches for an accuracy of 60.58%.

Gradient Boosting produced the second-highest accuracy at 51.92% and achieved the highest Macro F1 score.

One of the most interesting findings was that increasing model complexity did not necessarily improve predictive performance. XGBoost, despite being one of the most sophisticated models tested, produced the lowest overall accuracy.

The results suggest that explicitly modeling the goal-scoring process can be particularly useful for international soccer prediction.

## Handling Teams With Limited Historical Data

The 2026 World Cup included several countries that did not appear in the 358-match historical training dataset.

For teams without sufficient historical tournament information, neutral historical feature values were used as fallback values rather than removing those teams from the analysis.

This represents an important limitation of the current model and provides an opportunity for future improvement by incorporating a larger international match database.

## Project Workflow

The project is divided into multiple stages:

1. Collect and clean historical international tournament data.
2. Calculate ELO ratings and team-performance features.
3. Construct classification and Poisson modeling datasets.
4. Train and compare five prediction models.
5. Evaluate the models against the 2026 FIFA World Cup.
6. Analyze actual versus predicted tournament results.
7. Adapt the modeling framework to women's international soccer.
8. Develop predictions for the 2027 FIFA Women's World Cup.

## Technologies

The project was developed primarily in Google Colab using Python.

Major libraries include:

- pandas
- NumPy
- scikit-learn
- XGBoost
- SciPy
- Matplotlib

## Data Source

Historical and tournament match data is based on the OpenFootball project.

OpenFootball provides openly available structured soccer datasets covering international tournaments and competitions.

## Limitations

Several limitations should be considered when interpreting the results:

- The historical training dataset contains only 358 matches.
- Some 2026 teams had little or no representation in the historical tournament dataset.
- International team strength changes over time.
- Injuries, player availability, tactical changes, and other match-specific factors are not included.
- ELO and recent-form features simplify the underlying strength of national teams.
- Soccer contains substantial randomness, particularly because matches are relatively low-scoring.
- Penalty shootouts require different treatment from normal match outcomes.

These limitations mean that the models should be interpreted as statistical prediction tools rather than deterministic forecasts.

## Next Stage: 2027 FIFA Women's World Cup

The next stage of the project applies the same general modeling framework to women's international soccer.

Women's historical match data will be processed separately, new team ratings and performance features will be calculated, and the five modeling approaches will be compared again.

The best-performing methodology will then be used to generate predictions for the 2027 FIFA Women's World Cup.

## Author

Shanila Rahman Khan  
Data Science Capstone  
Winona State University
