## 3 广东省森林地上生物量反演模型构建与评价
### 3.1 模型构建与评价

本研究的建模样本来源于经过筛选的GEDI L4A足迹级AGB观测。筛选后共得到475720个有效足迹，为保证计算效率并避免类别不平衡带来的偏差，采用分层随机抽样的方式中抽取15000个样本用于模型训练与验证。


本研究采用XGBoost进行建模。XGBoost（Extreme Gradient Boosting）在传统 GBDT 的基础上引入二阶梯度信息、正则化项和并行计算框架，能够在抑制过拟合的同时提升运算效率，适合处理高维、多源遥感特征\cite{li2023county}。模型超参数通过 10 折交叉验证自动搜索：将15000条样本均分为十折，轮流以一折为验证集、其余九折为训练集，记录平均训练损失和验证损失，最终确定学习率、子采样率、最大树深等最优组合。

初步构建的特征集包括67个变量。为提高模型效率、减少冗余特征带来的过拟合风险，本研究基于XGBoost模型内部的基尼重要性排序（feature importance by gain），筛选出排名前20的特征用于建模。筛选后的变量包括 'B2',
'B3',
'MNDWI',
'NDVI8A5',
'NDVI8A6',
'NDVI8A7', 
'NDVI8A5\_ent', 
'NDVI87\_var', 
'NDVI8A4\_var', 
'NDVI87\_contrast',
'S1\_RVI',
'S1\_sum', 
'S1\_diff',
'S1\_rept', 
'VH\_contrast',
'VV\_contrast', 
'VV\_diss',
'VV\_corr',
'Elevation',
'Slope'。

本研究采用10折交叉验证（10-fold cross-validation）对模型进行训练与评估。将15000条样本均分为十折，轮流以一折为验证集、其余九折为训练集，记录各折的评估指标，最终以10折平均结果作为模型精度。模型预测精度通过决定系数R<sup>2</sup>、均方根误差(RMSE) 和平均绝对误差(MAE) 进行衡量：

$$R^2 = 1 - \frac{\sum_{i=1}^{n}{(y_i - \hat{y}_i)}^2}{\sum_{i=1}^{n}(y_i - \bar{y})^2}$$

$$ \text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2} $$

$$ \text{MAE} = \frac{1}{n}\sum_{i=1}^{n}|y_i - \hat{y}_i| $$

为验证 XGBoost 的优势，选取多元线性回归 (MLR)、支持向量机回归 (SVM) 与随机森林 (RF) 三种常用算法，在相同的15000条样本和同一组20个自变量上独立训练。

<p align="center">
表3.1 不同算法精度对比
</p>

<div align="center">
<table>
    <tr>
        <th>方法</th>
        <th>R<sup>2</sup></th>
        <th>RMSE (Mg/ha)</th>
        <th>MAE (Mg/ha)</th>
    </tr>
    <tr>
        <td>MLR</td>
        <td>0.091</td>
        <td>58.93</td>
        <td>44.41</td>
    </tr>
    <tr>
        <td>SVM</td>
        <td>0.147</td>
        <td>57.10</td>
        <td>40.35</td>
    </tr>
    <tr>
        <td>RF</td>
        <td>0.478</td>
        <td>47.19</td>
        <td>36.87</td>
    </tr>
    <tr>
        <td>XGBoost</td>
        <td>0.607</td>
        <td>36.51</td>
        <td>22.51</td>
    </tr>
</table>
</div>


对比结果如表所示，XGBoost 以R<sup>2</sup>=0.607、RMSE=36.51 Mg/ha、MAE = 22.51Mg/ha的表现优于其他模型。因此本文后续建模分析均以XGBoost为基准模型开展。

### 3.2 模型机理解释

为进一步解释模型内部机制与关键因子作用规律，本文引入SHAP方法对XGBoost反演模型进行解释性分析。SHAP（SHapley Additive exPlanations）模型解释方法来源于合作博弈论中的Shapley值，通过构建一个加性的解释模型，几乎可以适用于解释任何机器学习或深度学习模型的输出。SHAP框架通过量化每个输入变量对目标变量的贡献，来解释模型输出。在该框架中，所有特征均被视为“贡献者”。特征的SHAP值是其对模型预测的边际贡献，该贡献是对所有具有不同特征组合的可能模型的平均值。模型中特征 $X_j$ 的 Shapley 值由下式计算

$$ \operatorname{Shapley}\left(X_{j}\right)=\sum_{S \subseteq N \backslash\{j\}} \frac{k!(p-k-1)!}{p!}(f(S \cup\{j\})-f(S)) $$ 

其中 $p$ 是特征的总数, $N\backslash\{j\}$ 是除 $X_j$ 之外的所有可能特征组合的集合， $S$ 是 $N\backslash\{j\}$ 中的特征集， $f(S)$ 是使用 $S$ 中的特征进行的模型预测， $f(S \cup\{j\}$ 是使用 $S$ 中的特征加上特征$X_j$进行的模型预测。在评估特征重要性时，通常取每个特征SHAP值绝对值的平均值，作为该特征在全局范围内的重要性指标。本研究试用SHAP模型解释XGBoost方法广东省森林AGB反演模型。