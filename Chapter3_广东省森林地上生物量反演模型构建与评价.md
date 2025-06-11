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

$$ \text{Shapley}\left(X_{j}\right)=\sum_{S \subseteq N \backslash\{j\}} \frac{k!(p-k-1)!}{p!}(f(S \cup\{j\})-f(S)) $$ 

其中 $p$ 是特征的总数, $N\backslash\{j\}$ 是除 $X_j$ 之外的所有可能特征组合的集合， $S$ 是 $N\backslash\{j\}$ 中的特征集， $f(S)$ 是使用 $S$ 中的特征进行的模型预测， $f(S \cup\{j\}$ 是使用 $S$ 中的特征加上特征$X_j$进行的模型预测。在评估特征重要性时，通常取每个特征SHAP值绝对值的平均值，作为该特征在全局范围内的重要性指标。本研究试用SHAP模型解释XGBoost方法广东省森林AGB反演模型。


#### 3.2.1 总体分析
使用SHAP方法评估各个特征在AGB预测中的相对重要性。从圆环图可以看出，坡度（Slope）所占比例最高（22.3\%），其次是NDVI8A5（8.8\%）、MNDWI（6.0\%）、VV\_diss（5.6\%）等特征，说明这些特征对模型贡献较大。结合蜂窝图与条形图同样观察到，Slope 的 SHAP 值分布范围较大（-100至150），而其平均SHAP值绝对值明显高于其他特征（平均SHAP值绝对值 = 14.39，远高于NDVI8A5的5.69），NDVI8A5、MNDWI 以及 VV\_diss、B3、NDVI87\_contrast 等也展现了较大的影响力，而一些特征（如 NDVI8A5\_ent、VV\_corr）的平均SHAP值绝对值及占比相对较低，表明它们在 AGB 预测中的作用相对有限。



![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/8a64fe58faa4ebf855f74fcce0a9e3e7c15528bd/figure/%E8%9C%82%E7%AA%9D%E4%B8%8Ebar_%E5%B8%A6%E6%A0%87%E7%AD%BE.svg)

<p align="center">
图3.2 SHAP 模型解释各特征(a) 蜂窝图; (b) 各特征平均SHAP 值绝对值
</p>


#### 3.2.2 各特征依赖图分析

SHAP依赖图以特定特征的实际取值为 $X$ 轴，该特征对应的SHAP值为 $Y$ 轴，揭示了SHAP值随特征值变化的规律。若SHAP值随特征值的增加而增加，说明该特征值越大，模型预测的输出也越高；反之，若SHAP值随着特征值的增加而减少，则说明该特征对模型输出的贡献随其取值增加而减小，甚至可能产生负向影响。图中若呈现出非线性变化趋势，则说明该特征与模型输出之间存在较为复杂的非线性关系。

为避免原始 SHAP 散点过于离散、难以直观解读，本研究采用广义加性模型（GAM）对每个特征的 SHAP值–特征值关系进行光滑拟合；GAM 具有无需预设函数形式、可灵活捕捉复杂非线性趋势的优势。随后以拟合曲线与SHAP值=0的交点作为“临界点”，并在图中绘制垂直分界线，展示不同取值区间对模型输出由负向到正向（或反向）转换的阈值和趋势。

![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM%E6%8B%BC%E5%9B%BE1-4-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.3 特征依赖图(a) Slope; (b) NDVI8A5; (c) MNDWI; (d) VV_diss
</p>


坡度为 AGB 的关键地形驱动因子之一。GAM 拟合显示坡度对地上生物量具有显著的非线性正向影响（R<sup>2</sup> = 0.912， $p$ < 0.001）。在坡度小于约 14° 时，SHAP 值整体偏低，此区间的地形主要为平原和缓坡地区，受城市建设等人类活动影响，AGB 较低。坡度超过 15° 后，SHAP 值快速升高，说明坡度增加促进了 AGB 的积累。

NDVI8A5 与 SHAP 值之间存在明显的分段特征（R<sup>2</sup> = 0.735， $p$  < 0.001）。在 NDVI 低于 0.6 时，SHAP 值整体为负，对 AGB 预测有负向贡献。超过该阈值后，SHAP 值快速跃升至正区间，显示密集的绿色植被对 AGB 起到显著正向作用。

MNDWI 拟合关系显示，当 MNDWI 小于约 –0.55 时 SHAP 值为正，随后下降并转为负向（R<sup>2</sup> = 0.742， $p$  < 0.001）。这可能反映的是由“高反射水体”向“非水体地表”（如裸地或建筑）的过渡。由于水体本身不具有 AGB，因此大部分非负 SHAP 值可能来源于水边林地的混合像元，而 MNDWI 稍高区域（–0.5 至 0.1）则更可能对应城区或裸土，抑制了地上生物量的形成。

VV\_diss 是基于雷达 VV 极化通道计算的纹理指标，衡量局部地表后向散射的异质性。GAM 拟合结果表明其与 SHAP 值之间呈现较为复杂的非线性关系（R<sup>2</sup> = 0.796， $p$ < 0.001），存在3个转折点。超过 25000 后 SHAP 值继续上升，可能表明复杂纹理是 AGB 高值的信号。


![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM%E6%8B%BC%E5%9B%BE5-8-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.4 特征依赖图(a) B3; (b) NDVI87_contrast; (c) VV_contrast; (d) Elevation
</p>

![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM9-16-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.5 特征依赖图(a) NDVI87_var; (b) NDVI8A7; (c) S1_rept; (d) VH_contrast; (e) B2; (f) S1_RVI; (g) S1_sum; (h) S1_diff
</p>

![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM%E6%8B%BC%E5%9B%BE17-20-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.6 特征依赖图(a) NDVI8A6; (b) NDVI8A4_var; (c) VV_corr; (d) NDVI8A5_ent
</p>