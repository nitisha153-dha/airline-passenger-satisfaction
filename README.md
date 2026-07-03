# Airline-Passenger-Satisfaction
Predicting customer satisfaction for Invistico Airlines using machine learning, and identifying the service factors that matter most to passengers.
---
## Business Problem

Airlines collect huge amounts of feedback on every part of the flying experience — seat comfort, food, wifi, boarding, cleanliness, staff service — but rarely turn that feedback into a clear, prioritized action plan. Without knowing *which* factors actually drive satisfaction, an airline risks spending money improving things passengers don't care much about, while the real pain points go unaddressed.

This project uses a dataset of **103,904 passenger surveys** from Invistico Airlines to answer two business questions:

1. Can we predict whether a passenger will be satisfied or not, based on their flight experience?
2. Which specific service factors have the biggest impact on satisfaction — so the airline knows where to invest first?
---
## Solution

I built and compared four classification models to predict passenger satisfaction, then used the best-performing model to rank service factors by how much they actually influence satisfaction. The output is a data-backed priority list the airline's operations and product teams could act on directly, rather than guessing which improvements matter most.
---
## Methodology

**1. Data Cleaning & Preparation**
- Standardized column names and removed identifier columns that don't contribute to prediction
- Handled missing values in `Arrival Delay in Minutes` (~0.3% of rows)
- Detected and removed outliers in `Flight Distance` using the IQR method
- Checked for and confirmed no duplicate records

**2. Exploratory Data Analysis**
- Analyzed the class balance of the target variable (56% neutral/dissatisfied vs. 44% satisfied)
- Reviewed distributions for age, flight distance, and delay times
- Built a correlation matrix and pairplots across numerical variables to check for redundancy and relationships with satisfaction
- Removed `Arrival Delay in Minutes` after finding it highly correlated with `Departure Delay in Minutes`, to avoid feeding the model duplicate information

**3. Feature Engineering**
- One-hot encoded categorical variables (gender, customer type, travel type, class)
- Applied Min-Max scaling to numerical features so no single variable would dominate the model due to scale

**4. Model Building & Comparison**
Trained and evaluated four classification models on the same train/test split:

| Model                |Accuracy | F1 Score (weighted, 3-fold CV) | 
| Random Forest        | 96%     | 94.8% |
| Decision Tree        | 94%     | 93.6% |
| Logistic Regression  | 93%     | 93.1% |
| K-Nearest Neighbors  | 93%     | 92.3% |

**5. Hyperparameter Tuning**
- Tuned the Random Forest model with `GridSearchCV`, searching across tree depth, number of estimators, and max features
- Validated the tuned model with cross-validation to confirm it generalizes well and isn't overfitting to the training data

**6. Feature Importance Analysis**
- Extracted feature importance scores from the tuned Random Forest model to identify which factors most strongly predict satisfaction

---

## Skills Demonstrated

`Python` `pandas` `NumPy` `scikit-learn` `seaborn` `matplotlib` `Exploratory Data Analysis` `Data Cleaning & Outlier Treatment` `One-Hot Encoding` `Feature Scaling` `Classification Modeling` `Cross-Validation` `Hyperparameter Tuning (GridSearchCV)` `Feature Importance Analysis` `Business Storytelling`

---

## Results

- The **Random Forest Classifier** was the strongest performer, reaching **96% test accuracy** and a **94.8% weighted F1 score**, meaning it reliably predicts satisfaction without being skewed by the slight class imbalance in the data.
- Feature importance analysis showed that **inflight wifi service** and **online boarding** were the two strongest drivers of passenger satisfaction — ahead of traditionally assumed factors like food quality and seat comfort.
- This was a genuinely useful finding: it suggests passengers weight their *digital* experience (getting online, boarding smoothly) more heavily than physical comfort factors when forming an overall opinion of the flight.

---

## Business Recommendations

1. **Prioritize wifi reliability and speed.** Since it's the single strongest predictor of dissatisfaction, even incremental improvements here are likely to move overall satisfaction more than spending in other areas.
2. **Streamline the online boarding process.** Simplifying or speeding up digital boarding (app clarity, fewer steps, less friction) is a comparatively low-cost fix with high potential impact.
3. **Don't over-invest in areas passengers rate as less influential**, such as food and drink or gate location, relative to their cost — the model suggests these matter less to overall satisfaction than digital-experience factors.
4. **Segment further by travel type and class.** Business travelers and Economy passengers may weight these factors differently; a follow-up segmented analysis would sharpen these recommendations.

---

## Next Steps

- Test the model's stability on more recent survey data to confirm findings hold over time
- Build a segmented model (by travel class or travel type) to see if satisfaction drivers differ across passenger groups
- Deploy the tuned model as a lightweight scoring tool the customer experience team could use on new survey responses
- Explore whether a simpler model (e.g. tuned Logistic Regression) could reach similar accuracy with better interpretability for non-technical stakeholders

---

---

## Resources

- **Dataset:** [Invistico Airline Dataset — Kaggle](https://www.kaggle.com/datasets/likhari/invistico-airline-dataset)
- **scikit-learn documentation:** [https://scikit-learn.org/stable/](https://scikit-learn.org/stable/)
- **pandas documentation:** [https://pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)
- **GridSearchCV reference:** [https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html)

## Repository Contents

```
├── airlines.ipynb      # Full analysis: cleaning, EDA, modeling, tuning, feature importance
├── train.csv            # Passenger survey dataset (103,904 records)
└── README.md
```

**Dataset:** Invistico Airlines passenger satisfaction survey, 103,904 records across 24 features covering demographics, travel details, and service ratings (0–5 scale).
👤 Nitisha

Aspiring Data Analyst
Skills: SQL | Excel | Power BI | Data Analysis Projects
