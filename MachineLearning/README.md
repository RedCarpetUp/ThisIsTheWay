# Data Science and Machine Learning

The following repository contains the various resources one might need to use in their daily ML tasks. The repository contains links of blogs, tutorials etc.

## XG-Boost 
##### About the algorithm
- [XGB for Regression](https://www.youtube.com/watch?v=OtD8wVaFm6E)
- [XGB for Classification](https://www.youtube.com/watch?v=8b1JEDvenQU&t=703s)
- [Official Documentation](https://xgboost.readthedocs.io/en/latest/)
- [XGB for handling Imbalanced class distributions](https://machinelearningmastery.com/xgboost-for-imbalanced-classification/)
- [XGB Bias and variance tradeoff](https://kehuiyao.github.io/2019/03/21/xgboost-tuning-parameters/)
- [XGB Bias and variance tradeoff](https://xgboost.readthedocs.io/en/latest/tutorials/param_tuning.html)

### SHAP values
> We at RedCarpet give a high focus to model explainability and interpretability, and for this we use the latest SHAP algorithm which gives local as well as global explanation of our ML models built over XGBoost

- [Official Repository for SHAP](https://github.com/slundberg/shap)
- [Amazing blog on SHAP written by the author of SHAP](https://towardsdatascience.com/interpretable-machine-learning-with-xgboost-9ec80d148d27)
- [For the Mathematics nerd](https://christophm.github.io/interpretable-ml-book/shap.html)

## EDA 

> Exploratory data analysis is a very important part of any data scientist's toolbox. 
> The typical data one gets at RedCarpet is never less than 300 features, there are many missing variables, outliers etc. To tackle all this we use an efficient plotting technique:
 - [FACETS grid](https://github.com/PAIR-code/facets) 

Use this piece of code, if faced with datatype conflicts:
```sh
d = dict(zip(df.columns,[*df.dtypes]))
final = df.astype(dict(zip(df.columns,[*df.dtypes])))
```

