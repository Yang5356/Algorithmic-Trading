# 基于机器学习的算法交易策略研究

本项目基于技术指标与机器学习模型构建价格预测与交易策略，并评估其在不同市场环境下的表现。

## 项目背景

目标是：

- 预测下一交易日价格
- 将预测结果转化为交易策略（Buy / Sell / Hold）
- 在考虑交易成本与约束条件下评估策略收益

项目包含：

- Stage 1：样本内（In-sample）
- Stage 2：样本外（Out-of-time）验证

## 数据集

- 时间区间：2022/01 – 2024/10
- 样本量：约 1035 条日频数据（Stage 1）
- Stage 2：新增数据用于 out-of-time 测试

## 特征工程

构建多类技术指标，包括：

- 趋势类：SMA、EMA
- 动量类：RSI、MACD
- 波动率：Bollinger Bands、ATR、GARCH
- 其他：ROC、EWMA、Log Return 等

用于刻画价格变化驱动因素。

## 模型方法

使用多种模型进行预测：

- Random Forest
- Support Vector Machine
- Gradient Boosting
- XGBoost
- Multilayer Perceptron
- RNN

并构建：

- Ensemble 模型（简单平均）

## 训练方式

- Rolling window：5 日
- 80/20 动态划分
- 预测下一期价格

评估指标：

- MSE
- RMSE
- R²

## 交易策略

基于预测结果构建交易规则：

- Buy：预测价格显著上涨
- Sell：预测价格显著下跌
- Hold：变化不明显

约束条件：

- 连续同一操作不超过 5 次
- 每次交易单位限制
- 交易成本：1%
- 初始资金：10000 USD + 100 单位资产

## 实验设置

### Task 1：无杠杆

- 单位交易
- 标准成本与约束

### Task 2：有杠杆

- 满足条件时允许 2 单位交易
- 同样规则下测试杠杆效果

## 核心结果

- GBM 在预测上表现较强（R²≈0.99）
- 多数模型在预测层面拟合度较高
- Ensemble 模型在收益稳定性与回撤控制方面优于单模型
- 在考虑交易成本后，策略仍可实现正收益

## 关键结论

- 技术指标可提供短期预测信号
- 高预测精度不等于高交易收益
- 交易成本与约束对策略影响显著
- 模型集成有助于提升稳定性
- Out-of-time 验证是策略有效性的关键

## 文件说明

- main.ipynb：主模型与回测
- main.html：Notebook 导出版本
- final_project.pdf：项目展示
- Pro3_Stage1.xlsx：训练数据
- Pro3_Stage2.xlsx：测试数据

## 说明

本项目为研究性质回测，不构成实际交易建议。
