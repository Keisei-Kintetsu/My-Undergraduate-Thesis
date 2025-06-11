## 3 广东省森林地上生物量反演模型构建与评价
### 3.1 模型构建与评价

本研究的建模样本来源于经过筛选的 GEDI L4A 足迹级 AGB 观测。筛选后共得到 475720 个有效足迹，为保证计算效率并避免类别不平衡带来的偏差，采用分层随机抽样的方式中抽取 15000 个样本用于模型训练与验证。


本研究采用 XGBoost 进行建模。XGBoost（Extreme Gradient Boosting）在传统 GBDT 的基础上引入二阶梯度信息、正则化项和并行计算框架，能够在抑制过拟合的同时提升运算效率，适合处理高维、多源遥感特征。模型超参数通过 10 折交叉验证自动搜索：将 15000 条样本均分为十折，轮流以一折为验证集、其余九折为训练集，记录平均训练损失和验证损失，最终确定学习率、子采样率、最大树深等最优组合。

初步构建的特征集包括 67 个变量。为提高模型效率、减少冗余特征带来的过拟合风险，本研究基于 XGBoost 模型内部的基尼重要性排序，筛选出排名前 20 的特征用于建模。筛选后的变量包括 'B2',
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

本研究采用 10 折交叉验证（10-fold cross-validation）对模型进行训练与评估。将 15000 条样本均分为十折，轮流以一折为验证集、其余九折为训练集，记录各折的评估指标，最终以 10 折平均结果作为模型精度。模型预测精度通过决定系数R<sup>2</sup>、均方根误差(RMSE) 和平均绝对误差(MAE) 进行衡量：


```math
R^2 = 1 - \dfrac{\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}{\sum_{i=1}^{n}(y_i - \bar{y})^2} 
```

$$ \text{RMSE} = \sqrt{\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2} $$

$$ \text{MAE} = \frac{1}{n}\sum_{i=1}^{n}|y_i - \hat{y}_i| $$

其中 $y_{i}$ 为观测值， $\hat{y}_{i}$ 为预测值， $\bar{y}$ 为观测均值， $n$ 为样本数。

为验证 XGBoost 的优势，选取多元线性回归 (MLR)、支持向量机回归 (SVM) 与随机森林 (RF) 三种常用算法，在相同的 15000 条样本和同一组 20 个自变量上独立训练。

<p align="center">
表 3.1&ensp;不同算法精度对比
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


对比结果如表所示，XGBoost 以 R<sup>2</sup> = 0.607、RMSE = 36.51 Mg/ha、MAE = 22.51 Mg/ha 的表现优于其他模型。因此本文后续建模分析均以 XGBoost 为基准模型开展。

### 3.2 模型机理解释

为进一步解释模型内部机制与关键因子作用规律，本文引入 SHAP 方法对 XGBoost 反演模型进行解释性分析。SHAP（SHapley Additive exPlanations）模型解释方法来源于合作博弈论中的 Shapley 值，通过构建一个加性的解释模型，几乎可以适用于解释任何机器学习或深度学习模型的输出。SHAP 框架通过量化每个输入变量对目标变量的贡献，来解释模型输出。在该框架中，所有特征均被视为“贡献者”。特征的 SHAP 值是其对模型预测的边际贡献，该贡献是对所有具有不同特征组合的可能模型的平均值。模型中特征 $X_j$ 的 Shapley 值由下式计算

$$ \text{Shapley}\left(X_{j}\right)=\sum_{S \subseteq N \backslash\{j\}} \frac{k!(p-k-1)!}{p!}(f(S \cup\{j\})-f(S)) $$ 

其中 $p$ 是特征的总数, $N\backslash\{j\}$ 是除 $X_j$ 之外的所有可能特征组合的集合， $S$ 是 $N\backslash\{j\}$ 中的特征集， $f(S)$ 是使用 $S$ 中的特征进行的模型预测， $f(S \cup\{j\}$ 是使用 $S$ 中的特征加上特征$X_j$进行的模型预测。在评估特征重要性时，通常取每个特征 SHAP 值绝对值的平均值，作为该特征在全局范围内的重要性指标。本研究试用 SHAP 模型解释 XGBoost 方法广东省森林 AGB 反演模型。


#### 3.2.1 总体分析
使用SHAP方法评估各个特征在AGB预测中的相对重要性。从圆环图可以看出，坡度（Slope）所占比例最高（22.3\%），其次是NDVI8A5（8.8\%）、MNDWI（6.0\%）、VV\_diss（5.6\%）等特征，说明这些特征对模型贡献较大。结合蜂窝图与条形图同样观察到，Slope 的 SHAP 值分布范围较大（-100至150），而其平均SHAP值绝对值明显高于其他特征（平均SHAP值绝对值 = 14.39，远高于NDVI8A5的5.69），NDVI8A5、MNDWI 以及 VV\_diss、B3、NDVI87\_contrast 等也展现了较大的影响力，而一些特征（如 NDVI8A5\_ent、VV\_corr）的平均SHAP值绝对值及占比相对较低，表明它们在 AGB 预测中的作用相对有限。



<div align="center">
  <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/SHAP%E9%A5%BC%E7%8A%B6%E5%9B%BE_00.png?raw=true" style="width:60%;">
</div>


<p align="center">
图3.1 SHAP 模型解释各特征重要性占比
</p>


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


坡度为 AGB 的关键地形驱动因子之一。GAM 拟合显示坡度对地上生物量具有显著的非线性正向影响（ $R^2$ = 0.912， $p$ < 0.001）。在坡度小于约 14° 时，SHAP 值整体偏低，此区间的地形主要为平原和缓坡地区，受城市建设等人类活动影响，AGB 较低。坡度超过 15° 后，SHAP 值快速升高，说明坡度增加促进了 AGB 的积累。

NDVI8A5 与 SHAP 值之间存在明显的分段特征（ $R^2$ = 0.735， $p$  < 0.001）。在 NDVI 低于 0.6 时，SHAP 值整体为负，对 AGB 预测有负向贡献。超过该阈值后，SHAP 值快速跃升至正区间，显示密集的绿色植被对 AGB 起到显著正向作用。

MNDWI 拟合关系显示，当 MNDWI 小于约 –0.55 时 SHAP 值为正，随后下降并转为负向（ $R^2$ = 0.742， $p$  < 0.001）。这可能反映的是由“高反射水体”向“非水体地表”（如裸地或建筑）的过渡。由于水体本身不具有 AGB，因此大部分非负 SHAP 值可能来源于水边林地的混合像元，而 MNDWI 稍高区域（–0.5 至 0.1）则更可能对应城区或裸土，抑制了地上生物量的形成。

VV\_diss 是基于雷达 VV 极化通道计算的纹理指标，衡量局部地表后向散射的异质性。GAM 拟合结果表明其与 SHAP 值之间呈现较为复杂的非线性关系（ $R^2$ = 0.796， $p$ < 0.001），存在3个转折点。超过 25000 后 SHAP 值继续上升，可能表明复杂纹理是 AGB 高值的信号。


![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM%E6%8B%BC%E5%9B%BE5-8-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.4 特征依赖图(a) B3; (b) NDVI87_contrast; (c) VV_contrast; (d) Elevation
</p>


在绿波段（B3）反射率分析中，模型显示其在低反射区（<0.05）对 AGB 有正向影响，而在高反射区则转为轻微的负向影响，可能源于草本植物的反射特性强于木本植物，但其地上生物量较低。 单独的 B3 值不足以判断地物类型，其贡献需要结合近红外、红波段共同评估植被状态。此外，B3 在 AGB 建模中的边际作用有限。

高程的SHAP值在0-200m间在0值附近波动，两次穿越SHAP=0值，在 250–600 m 区间对 AGB 有积极贡献，超过约 750 m 后转为负向影响（$R^2$ = 0.657，$p$ < 0.001）。这说明广东省森林在适宜海拔范围内发育良好，过高海拔可能受到气温、土壤湿度等导致森林地上生物量受限。

从第9到第20个特征的 SHAP 依赖图整体呈现“重要性较低、形态高度非线性”的共同特征，但各自仍可识别出若干典型的分段模式与临界点。


![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM9-16-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.5 特征依赖图(a) NDVI87_var; (b) NDVI8A7; (c) S1_rept; (d) VH_contrast; (e) B2; (f) S1_RVI; (g) S1_sum; (h) S1_diff
</p>


（1）光学特征类：NDVI8A6 的拐点落在0.13，低于该值时抑制 AGB，超过后显著增益；B2在0.05附近处由负向快速跃升至正向，随后影响趋于平缓。 

（2）光学纹理特征类：NDVI87\_var 在约 值为 9 附近处出现唯一临界点，取值较低时对 AGB 多为负向贡献，跨过该阈值后转为正向且随数值上升而缓慢增强；NDVI8A7 在0.03附近由负转正，随后曲线趋于饱和；NDVI8A4\_var整体保持正向，但在极高区间（> 6000）出现轻微回落；而 NDVI8A5\_ent 则有两个明显阈值（约为3.1和3.9），分别对应负到正及正到负的两次翻转。  

![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/GAM%E6%8B%BC%E5%9B%BE17-20-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)
<p align="center">
图3.6 特征依赖图(a) NDVI8A6; (b) NDVI8A4_var; (c) VV_corr; (d) NDVI8A5_ent
</p>

（3）雷达特征及纹理：S1\_diff 于 –20dB 左右完成负到正转换；S1\_rept 在0.10–0.60之间几乎每隔0.05就出现一次零值穿越，共记录到6个临界点，曲线呈锯齿式波动；S1\_sum 在 –25dB 左右由负转正后保持缓升；S1\_RVI 于 3.0–4.3 区间连现 5 个切换点，整体振幅有限；VH\_contrast 的曲线更为剧烈，在 (0.5–1.6 $\times$ 10<sup>9</sup>) 区间出现 8次正负互换并于高端 (1.5 $\times$ 10<sup>9</sup>) 强烈上扬；VV\_corr则在0.45 附近处完成正到负翻转并随相关性升高而持续降低。  

由于这些特征在全局重要性排序中位列后段，且对 AGB 的作用呈现多次正负切换与显著局部性，本文仅对其主要阈值位置与基本趋势加以概述，不再深入讨论其生态机理与交互影响。

### 3.3 不同变量组合对反演模型的影响

为系统评估不同变量组合对AGB反演精度的影响，基于XGBoost模型对8组变量方案进行了对比分析，结果如表所示。在仅使用光学特征（变量组1）时，模型的R<sup>2</sup>为0.518，RMSE为39.05 Mg/ha，MAE为25.65 Mg/ha；引入光学纹理特征（变量组2）后，模型精度略有提升，R<sup>2</sup>增至0.527，MAE略降至25.58 Mg/ha，表明纹理信息对模型具有一定的补充作用。

<p align="center">
表3.2 不同变量组合对反演模型的影响
</p>


<div align="center">
<table>
    <tr>
        <th></th>
        <th>变量选择</th>
        <th>变量个数</th>
        <th>R<sup>2</sup></th>
        <th>RMSE<br>(Mg/ha)</th>
        <th>MAE<br>(Mg/ha)</th>
    </tr>
    <tr>
        <td>变量组1</td>
        <td>光学特征</td>
        <td>25</td>
        <td>0.518</td>
        <td>39.05</td>
        <td>25.65</td>
    </tr>
    <tr>
        <td>变量组2</td>
        <td>光学特征+光学纹理特征</td>
        <td>49</td>
        <td>0.527</td>
        <td>39.08</td>
        <td>25.58</td>
    </tr>
    <tr>
        <td>变量组3</td>
        <td>雷达特征</td>
        <td>7</td>
        <td>0.404</td>
        <td>45.44</td>
        <td>29.43</td>
    </tr>
    <tr>
        <td>变量组4</td>
        <td>雷达特征+雷达纹理特征</td>
        <td>15</td>
        <td>0.485</td>
        <td>42.43</td>
        <td>25.67</td>
    </tr>
    <tr>
        <td>变量组5</td>
        <td>光学特征+雷达特征</td>
        <td>33</td>
        <td>0.497</td>
        <td>44.36</td>
        <td>26.63</td>
    </tr>
    <tr>
        <td>变量组6</td>
        <td>变量组2+变量组4</td>
        <td>64</td>
        <td>0.512</td>
        <td>43.08</td>
        <td>25.91</td>
    </tr>
    <tr>
        <td>变量组7</td>
        <td>光学特征+光学纹理特征+雷达特征+雷达纹理特征+地形特征</td>
        <td>67</td>
        <td>0.559</td>
        <td>38.76</td>
        <td>23.69</td>
    </tr>
    <tr>
        <td>变量组8</td>
        <td>筛选后的20个变量</td>
        <td>20</td>
        <td>0.607</td>
        <td>36.51</td>
        <td>22.51</td>
    </tr>
</table>
</div>

相比之下，雷达变量（变量组3和4）的表现相对逊色。即使在引入雷达纹理特征后（变量组4），模型R<sup>2</sup>亦仅为0.485，说明在本研究区，雷达信息对AGB的解释力较为有限。而当融合光学和雷达特征（变量组5）后，模型精度介于光学和雷达单独建模之间，未表现出显著的协同增强作用。、


在整合光学与雷达的所有特征及其纹理特征（变量组6）时，模型精度略有下降（R<sup>2</sup>=0.512），可能是由于高维冗余特征干扰模型训练。进一步在变量组7中加入地形特征后，模型精度有所改善（R<sup>2</sup>=0.559，RMSE下降至38.76 Mg/ha），显示地形因子对AGB具有一定的调节效应。

基于变量组7的基尼重要性排序提取前20个关键变量（变量组8），构建精简模型后，其性能反而达到最优，R<sup>2</sup>提升至0.607，RMSE与MAE分别下降至36.51 Mg/ha与22.51 Mg/ha。该结果表明，适度的特征选择不仅可减少模型复杂度，还能有效提升预测精度。


<div align="center">
  <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/%E4%B8%8D%E5%90%8C%E5%8F%98%E9%87%8F%E7%BB%84%E5%90%88%E6%95%A3%E7%82%B9%E5%9B%BE-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true" style="width:90%;">
</div>

<p align="center">
图3.7 不同变量组合对反演模型的影响
</p>

### 3.4 不同激光波束选择对反演模型的影响

GEDI有覆盖激光器与全功率激光器两种激光器。 GEDI的功率光束在激光能量方面是覆盖光束的约两倍，直接影响密集树冠的穿透力。全功率光束发射功率更高的集中信号，使其能够穿透茂密的树冠并捕获来自树冠更低高度处的回波，有效增强了有关植被垂直结构的信息。图 3.8 显示了两种激光光束的对比，全功率激光具有比覆盖光束更高的光束灵敏度。此外，有学者提出会影响背景太阳光照对 GEDI 波形质量会产生负面影响。

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/8a5b8501de5b756a5c8f22a4e6aa7c6c129f0fa1/figure/%E6%BF%80%E5%85%89%E5%AF%B9%E6%AF%942.svg" >
</div>


<p align="center">
图3.8 覆盖激光与全功率激光的灵敏度对比
</p>


为探究不同类型激光器（全功率激光器与覆盖激光器）及不同光束灵敏度和太阳照射条件对AGB反演精度的影响，基于XGBoost模型，以变量组8（即前20个最重要变量）为输入变量，构建了共16组对比实验。各实验结果如表所示。
<div align="center">
<table>
    <tr>
        <th></th>
        <th>灵敏度</th>
        <th>激光器选择</th>
        <th>时间</th>
        <th>R<sup>2</sup></th>
        <th>RMSE<br>(Mg/ha)</th>
        <th>MAE<br>(Mg/ha)</th>
    </tr>
    <tr>
        <td>激光组1</td>
        <td>&gt;0.95</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>全天</td>
        <td>0.549</td>
        <td>43.32</td>
        <td>24.13</td>
    </tr>
    <tr>
        <td>激光组1N</td>
        <td>&gt;0.95</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>夜间</td>
        <td>0.566</td>
        <td>46.29</td>
        <td>30.88</td>
    </tr>
    <tr>
        <td>激光组2</td>
        <td>&gt;0.96</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>全天</td>
        <td>0.554</td>
        <td>41.71</td>
        <td>22.40</td>
    </tr>
    <tr>
        <td>激光组2N</td>
        <td>&gt;0.96</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>夜间</td>
        <td>0.571</td>
        <td>46.13</td>
        <td>28.52</td>
    </tr>
    <tr>
        <td>激光组3</td>
        <td>&gt;0.97</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>全天</td>
        <td>0.579</td>
        <td>40.57</td>
        <td>23.91</td>
    </tr>
    <tr>
        <td>激光组3N</td>
        <td>&gt;0.97</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>夜间</td>
        <td>0.556</td>
        <td>46.98</td>
        <td>28.49</td>
    </tr>
    <tr>
        <td>激光组4</td>
        <td>&gt;0.98</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>全天</td>
        <td>0.580</td>
        <td>45.43</td>
        <td>30.92</td>
    </tr>
    <tr>
        <td>激光组4N</td>
        <td>&gt;0.98</td>
        <td>覆盖激光器+全功率激光器</td>
        <td>夜间</td>
        <td>0.597</td>
        <td>35.45</td>
        <td>35.45</td>
    </tr>
    <tr>
        <td>激光组5</td>
        <td>&gt;0.95</td>
        <td>仅全功率激光器</td>
        <td>全天</td>
        <td>0.550</td>
        <td>46.63</td>
        <td>29.88</td>
    </tr>
    <tr>
        <td>激光组5N</td>
        <td>&gt;0.95</td>
        <td>仅全功率激光器</td>
        <td>夜间</td>
        <td>0.566</td>
        <td>45.21</td>
        <td>29.56</td>
    </tr>
    <tr>
        <td>激光组6</td>
        <td>&gt;0.96</td>
        <td>仅全功率激光器</td>
        <td>全天</td>
        <td>0.579</td>
        <td>41.59</td>
        <td>28.28</td>
    </tr>
    <tr>
        <td>激光组6N</td>
        <td>&gt;0.96</td>
        <td>仅全功率激光器</td>
        <td>夜间</td>
        <td>0.577</td>
        <td>43.10</td>
        <td>26.27</td>
    </tr>
    <tr>
        <td>激光组7</td>
        <td>&gt;0.97</td>
        <td>仅全功率激光器</td>
        <td>全天</td>
        <td>0.605</td>
        <td>35.40</td>
        <td>21.58</td>
    </tr>
    <tr>
        <td>激光组7N</td>
        <td>&gt;0.97</td>
        <td>仅全功率激光器</td>
        <td>夜间</td>
        <td>0.606</td>
        <td>35.04</td>
        <td>21.88</td>
    </tr>
    <tr>
        <td>激光组8</td>
        <td>&gt;0.98</td>
        <td>仅全功率激光器</td>
        <td>全天</td>
        <td>0.593</td>
        <td>38.20</td>
        <td>22.73</td>
    </tr>
    <tr>
        <td>激光组8N</td>
        <td>&gt;0.98</td>
        <td>仅全功率激光器</td>
        <td>夜间</td>
        <td>0.607</td>
        <td>36.31</td>
        <td>22.51</td>
    </tr>
</table>
</div>

从激光器类型来看，使用仅全功率激光器的模型整体优于覆盖激光器+全功率激光器组合。在相同光束灵敏度条件下，例如在灵敏度大于0.97的全天样本中，激光组7（全功率激光器）达到$R^2=0.605$、RMSE为35.40 Mg/ha、MAE为21.58 Mg/ha，明显优于激光组3（覆盖+全功率，$R^2=0.579$）。这表明高能量全功率激光器具有更强的穿透力与植被结构捕捉能力，对反演模型贡献更大。

从光束灵敏度分析，在固定激光器类型下，模型性能随灵敏度的提高呈现上升趋势。例如，全天全功率激光器组中，$R^2$从激光组5（>0.95，$R^2=0.550$）逐步提升至激光组7（>0.97，$R^2=0.605$），而RMSE亦从46.63 Mg/ha降至35.40 Mg/ha。这说明高灵敏度波束在信号质量与结构识别方面具有更显著优势。

<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/%E6%BF%80%E5%85%89%E7%BB%841-4-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true" style="width:90%;">
</div>

<p align="center">
图3.9 不同激光波束选择对反演模型的影响（激光组1-4N）
</p>

太阳照射条件方面，考虑夜间（太阳高度角<0）与全天数据的对比，可观察到夜间波束并不总是优于全天波束。例如，在覆盖+全功率激光器组中，夜间数据在低灵敏度（激光组1N）下的$R^2$为0.566，略高于对应全天的0.549，但RMSE反而更高（46.29 vs 43.32 Mg/ha）。在灵敏度>0.97的全功率激光器组中，夜间样本（激光组7N）的表现略优于全天（激光组7），分别为$R^2=0.606$与0.605，RMSE分别为35.04与35.40 Mg/ha，差异较小。这说明虽然夜间背景光照更弱，有利于波形采集质量，但其对最终反演结果的提升有限，可能受到样本数量变化等因素影响。


<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/%E6%BF%80%E5%85%89%E7%BB%845-8-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true" style="width:90%;">
</div>

<p align="center">
图3.10 不同激光波束选择对反演模型的影响（激光组5-8N）
</p>

综合来看，选择高灵敏度且来源于全功率激光器的波束能够显著提升地上生物量反演模型的精度，夜间波束在某些情形下可略有补充效果，但提升幅度相对有限。

### 3.5 不同空间分辨率对反演模型的影响

GEDI 产品的第一个版本（R01）中，50.5％ 的光束的地理定位误差超过 20 m，在某些采集条件下误差甚至可能超过 30 米。这种系统性的误差可能对冠层高度和生物量的反演精度带来显著影响。相比之下，第二版本 GEDI 产品（R02）显著提升了定位精度，仅有 0.2\% 的光束地理定位误差大于 20 米， 80.8\% 的光束定位误差小于 10 米，已能满足对中等地理定位精度容忍度较高的科学应用需求。



<p align="center">
表3.4 不同空间尺度对模型的影响（XGBoost 模型，变量组8，激光组8N）
</p>

<div align="center">
<table>
    <tr>
        <th>空间尺度选择</th>
        <th>R<sub>2</sub></th>
        <th>RMSE<br>(Mg/ha)</th>
        <th>MAE<br>(Mg/ha)</th>
    </tr>
    <tr>
        <td>30m</td>
        <td>0.607</td>
        <td>36.31</td>
        <td>22.51</td>
    </tr>
    <tr>
        <td>50m</td>
        <td>0.641</td>
        <td>37.75</td>
        <td>20.86</td>
    </tr>
    <tr>
        <td>100m</td>
        <td>0.612</td>
        <td>36.50</td>
        <td>22.76</td>
    </tr>
    <tr>
        <td>150m</td>
        <td>0.590</td>
        <td>40.35</td>
        <td>21.50</td>
    </tr>
    <tr>
        <td>200m</td>
        <td>0.594</td>
        <td>38.16</td>
        <td>22.99</td>
    </tr>
    <tr>
        <td>500m</td>
        <td>0.502</td>
        <td>44.44</td>
        <td>26.30</td>
    </tr>
</table>
</div>

为探讨空间分辨率与潜在的 GEDI 的光束地理定位误差对模型性能的影响，本文选取了30m、50m、100m、150m、200m 和 500m 六种空间尺度进行比较。表格显示了在不同空间分辨率下反演模型的性能指标。

<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/%E7%A9%BA%E9%97%B4%E5%B0%BA%E5%BA%A6_%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true" style="width:90%;">
</div>

<p align="center">
图3.11 不同空间尺度对模型的影响（XGBoost 模型，变量组8，激光组8N）
</p>


从结果来看，随着空间分辨率的增大，模型性能并非线性提升或下降。在50m分辨率下，模型表现出最高的R<sup>2</sup>（0.641）和最低的 MAE（20.86 Mg/ha），看似性能最优；但30m分辨率下，R<sup>2</sup>也达到了 0.607，RMSE 和 MAE 分别为 36.31 和 22.51 Mg/ha，依然保持较好的预测能力，且空间信息更为精细。因此，在保证合理精度的前提下，30m 分辨率的反演结果具备更高的应用价值和空间表达能力，尤其适合中高分辨率土地覆盖或生态监测应用场景。