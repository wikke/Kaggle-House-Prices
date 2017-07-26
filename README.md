# House Prices: Advanced Regression Techniques

[House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

> 最新加入了Stacking Ensemble技术。

# 数据处理

## 缺失情况统计

- 确实较多数据的Feature可以考虑直接drop
- 有多个Feature同时确实的行，可以直接drop

# Feature Engineering

- 可视化和outlier drop
- Feature和Result的正态化分布转化
- **正态转化后的Outlier drop**
- **所有Feature和Result在一张图展示2-2分布**
- **non-numerical categorical Feature替换为结果均值**

# Observation

- 所有numerical feature的corr heatmap

# 训练 & 预测

## 模型

- LinearRegression
- Ridge
- RidgeCV
- Lasso
- LassoCV
- ElasticNet
- ElasticNetCV
- **XGBRegressor**

## Stacking

### 第一层Base Estimators

- from sklearn.linear_model import Ridge
- from xgboost import XGBRegressor
- from sklearn.ensemble import AdaBoostRegressor
- from sklearn.ensemble import ExtraTreesRegressor
- from sklearn.ensemble import RandomForestRegressor
- from sklearn.ensemble import GradientBoostingRegressor

将原始的数据分为5 KFold，拿出一个estimator，将5个Fold中4个做train，1个做test，得到的结果暂存。然后重复5遍，得到5个不同test的预测结果，拼凑成为一个该estimator关于原始数据的预测结果，shape为(m, 1)。这6个estimator可以生成6个不同的预测结果，shape为(m, 6)。

### 第二层

采用XGBRegressor，数据数据是第一层的结果，结果是最终的预测结果。**可以理解为，输入是不同模型的预测结果，输出是groud truth，第二层权衡不同模型的预测结果，然后综合调整，得到更好的结果，这也是stacking的精髓所在。**

不过尝试了一些，效果没有明显提升。因素也有多方面吧，比如数据集不够大等等。

## Points

- StandardScaler调整
- cross_val_score结合**自定义scoring**定义模型performance

# 算法评估

- residual残差分布
- 预测结果-真值分布
- **Learning Curve**
- **GridSearchCV寻找模型最优参数**
