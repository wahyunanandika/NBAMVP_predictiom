# NBA MVP Prediction Project

## Introduction

This project focuses on predicting NBA MVP candidates using machine learning models. The goal is to identify and rank the top MVP candidates based on various player statistics.

### Data

The dataset includes features such as:
- **Player Name**: Name of the player
- **Year**: NBA season year
- **VORP**: Value Over Replacement Player
- **Win Shares**: Win Shares
- **PER**: Player Efficiency Rating
- **Losses**: Number of losses
- **Games Behind**: Games behind the leader

## Experiments

### Evaluation Metrics

- **RMSE (Root Mean Square Error)**: Measures how accurately the model predicts player performance.
- **MAP@K (Mean Average Precision at K)**: Assesses the model's ability to rank the top 5 MVP candidates.

### Data Processing

- **PCA (Principal Component Analysis)**: Used to reduce the dimensionality of the data but did not improve model performance in this case. Models trained without PCA performed better.
- **Time-Series Cross-Validation**: Used to handle the temporal structure of the data, ensuring no data leakage.

### Results

#### Model Performance

The following table shows the performance of various models, both with and without PCA, using RMSE and MAP@K:

| Model                        | Train Score (GridSearchCV) | Valid Score (GridSearchCV) | MAP@K  | RMSE   |
|------------------------------|----------------------------|----------------------------|--------|--------|
| Random Forest with PCA       | 0.018772                   | 0.033112                   | 0.006993| 0.030149|
| AdaBoost DT with PCA         | 0.019940                   | 0.033859                   | 0.006993| 0.031851|
| Gradient Boosting with PCA   | 0.017942                   | 0.034033                   | 0.006294| 0.029389|
| XGB with PCA                 | 0.017780                   | 0.035193                   | 0.006993| 0.023138|
| Random Forest                | 0.015922                   | 0.035439                   | 0.007692| 0.018517|
| AdaBoost DT                  | 0.016231                   | 0.036406                   | 0.006294| 0.023484|
| Gradient Boosting            | 0.010163                   | 0.037198                   | 0.006294| 0.029389|
| XGB                          | 0.015148                   | 0.037417                   | 0.008042| 0.018860|
| Ridge                        | 0.048889                   | 0.050544                   | 0.006294| 0.044986|
| ElasticNet                   | 0.048938                   | 0.050621                   | 0.006294| 0.045019|
| Lasso                        | 0.048832                   | 0.050672                   | 0.006643| 0.045063|
| Baseline                     | 0.058868                   | 0.058671                   | 0.000000| 0.054093|

#### Top Model Insights

- **XGB without PCA**: Best performance with MAP@K of 0.008042 and RMSE of 0.018860.
- **Feature Importance**: Key features include VORP, Win Shares, and PER. Metrics like Losses and Games Behind have less impact.

### Example Predictions

The XGB model without PCA made accurate predictions for the top MVP candidates:

- Nikola Jokić: Predicted 1st, Actual 1st
- Shai Gilgeous-Alexander: Predicted 2nd, Actual 2nd
- Luka Dončić: Predicted 4th, Actual 3rd
- Giannis Antetokounmpo: Predicted 3rd, Actual 4th

## Discussion

The XGB and Random Forest models performed well, even though PCA did not improve results. The models effectively predicted the top MVP candidates but showed less accuracy for lower-ranked players. Future work will include enhancing feature sets and refining predictions for lower-ranked candidates.

## Conclusion

The XGB and Random Forest models were effective in predicting MVP candidates, leveraging ensemble methods to capture complex data relationships. While PCA did not enhance model performance, the insights gained from feature analysis were valuable.

## Future Work

- **Deploy Models**: Create a portfolio website for real-time MVP predictions.
- **Update Models**: Implement self-training models and automated data pipelines.
- **Enhance Accuracy**: Explore advanced statistics and refine feature sets.
- **Dashboard**: Develop a dashboard to visualize predictions and feature importance.

## Note

The web scraping feature still works, but the website has updated its table layout. You will need to update the web scraping script and data cleaning model. The current scripts will work with the data collected two weeks ago.

## Paper

For a detailed analysis and methodology, please refer to the paper available in this GitHub repository in either Word or PDF format.

## References

1. [WebScraping](https://www.youtube.com/watch?v=JGQGd-oa0l4)
2. [Predicting the NBA MVP with Machine Learning](https://towardsdatascience.com/predicting-the-nba-mvp-with-machine-learning-c3e5b755f42e)