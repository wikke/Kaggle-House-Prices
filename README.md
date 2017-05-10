# House Prices: Advanced Regression Techniques

[House Prices: Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)

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

## Points

- StandardScaler调整
- cross_val_score结合**自定义scoring**定义模型performance

# 算法评估

- residual残差分布
- 预测结果-真值分布
- **Learning Curve**
- **GridSearchCV寻找模型最优参数**
