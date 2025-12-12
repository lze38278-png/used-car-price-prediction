\#  二手车交易价格预测 (Used Car Price Prediction)



!\[Python](https://img.shields.io/badge/Python-3.8%2B-blue)

!\[Library](https://img.shields.io/badge/Library-Pandas%20%7C%20LightGBM%20%7C%20XGBoost-orange)

!\[Score](https://img.shields.io/badge/Score-MAE%20523-green)



\## 项目简介

本项目基于\*\*阿里云天池大数据竞赛\*\*题目。任务是依据二手车的各项属性（如品牌、车身类型、行驶里程、车龄等），预测其交易价格。

这是一个典型的\*\*回归预测 (Regression)\*\* 问题。通过本项目，我深入实践了数据清洗、特征工程、模型训练及模型融合的全流程。



\##  技术栈

\* \*\*语言：\*\* Python 3

\* \*\*数据处理：\*\* Pandas, NumPy

\* \*\*可视化：\*\* Matplotlib, Seaborn

\* \*\*机器学习模型：\*\* LightGBM, XGBoost

\* \*\*工具：\*\* Jupyter Notebook, PyCharm



\##  核心策略与提分点

在这个项目中，我通过以下关键步骤将评分从 Baseline 的 \*\*672\*\* 提升至 \*\*523\*\*：



1\.  \*\*数据探索 (EDA)：\*\*

&nbsp;   \* 发现价格分布严重长尾（右偏），对目标值进行了 \*\*Log 对数变换\*\* (`np.log1p`)，使其更符合正态分布，显著降低了预测误差。

&nbsp;   \* 清洗了异常数据（如价格过低的样本）。



2\.  \*\*特征工程 (Feature Engineering)：\*\*

&nbsp;   \* \*\*构造“车龄”特征：\*\* 将 `regDate`（注册日期）和 `creatDate`（上线日期）解析为时间格式，计算出车辆的使用天数 (`used\_time`)，这是影响价格的最关键因素。

&nbsp;   \* \*\*处理脏数据：\*\* 修复了 `notRepairedDamage` 列中的异常值（'-'），将其转换为数值类型。



3\.  \*\*模型融合 (Model Ensemble)：\*\*

&nbsp;   \* 分别训练了 \*\*LightGBM\*\* 和 \*\*XGBoost\*\* 两个强力树模型。

&nbsp;   \* 采用 \*\*加权融合\*\* 策略 (0.6 \* LGB + 0.4 \* XGB)，利用不同模型的优势互补，进一步提升了泛化能力。



\## 结果展示

\* \*\*线上得分 (MAE)：\*\* 523.0399

\* \*\*本地验证集 MAE：\*\* 约 693.47



\##  如何运行

1\.  \*\*克隆仓库：\*\*

&nbsp;   ```bash

&nbsp;   git clone \[https://github.com/你的用户名/used-car-price-prediction.git](https:/你的用户名/github.com//used-car-price-prediction.git)

&nbsp;   ```

2\.  \*\*安装依赖：\*\*

&nbsp;   ```bash

&nbsp;   pip install pandas lightgbm xgboost scikit-learn matplotlib seaborn

&nbsp;   ```

3\.  \*\*准备数据：\*\*

&nbsp;   请从天池官网下载 `used\_car\_train\_20200313.csv` 和 `used\_car\_testB\_20200421.csv`，放入 `data/` 文件夹。

4\.  \*\*运行代码：\*\*

&nbsp;   直接运行 `main\_score\_boost.py` 即可生成预测结果。



---

\*Created by \[泽]\*

