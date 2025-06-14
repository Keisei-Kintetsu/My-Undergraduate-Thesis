##  中山大学本科毕业论文 <br>  Sun Yat-sen University Undergraduate Thesis 

# 基于多源遥感数据的广东省 2017-2024 年森林地上生物量反演 <br> Retrieval of forest aboveground biomass in Guangdong Province from 2017 to 2024 based on multi-source remote sensing data


<div align="center">
  <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/4848e7e6e791297fe9d241b20c0738554ea15699/figure/%E5%B9%B3%E5%9D%87%E5%80%BC%E7%BB%98%E5%9B%BE%E6%80%BB%E5%9B%BE3.svg"  style="width:100%;">
</div>

- 作者：梁而正
- Author: Erzheng Liang
- 专业：地理信息科学
- Major: Geographic Information Science
- 2025.5 
- [论文原文 Original Paper](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/f4bff9cdda3902361add234aaa9da07fb74f0cb4/%E5%9F%BA%E4%BA%8E%E5%A4%9A%E6%BA%90%E9%81%A5%E6%84%9F%E6%95%B0%E6%8D%AE%E7%9A%84%E5%B9%BF%E4%B8%9C%E7%9C%812017-2024%E5%B9%B4%E6%A3%AE%E6%9E%97%E5%9C%B0%E4%B8%8A%E7%94%9F%E7%89%A9%E9%87%8F%E5%8F%8D%E6%BC%94-%E7%BB%88%E7%A8%BF.pdf)




## 摘要

森林地上生物量（Aboveground Biomass, AGB）是反映森林生态系统结构与碳储量的重要指标，对碳达峰、碳中和背景下的资源监测与气候治理具有重要意义。以往基于样方清查的 AGB 估算方法在局地具有较高精度，但在大尺度、空间连续建图方面受限显著。随着遥感技术发展，多源数据融合与机器学习方法为实现高分辨率、连续、多时相 AGB 反演提供了可行路径。

本研究以广东省为研究区，选取 2019–2023 年 GEDI L4A 足迹级 AGB 作为目标变量，整合 Sentinel-2 光学影像、Sentinel-1 雷达影像及 Copernicus 30m DEM 数据，构建多源遥感特征数据集。共提取 5 类共 67 个候选变量，包括 12 个表观反射率波段、11 种植被指数、24 个 NDVI 纹理特征、15 个雷达与雷达纹理特征、3 个地形因子。通过 XGBoost 回归模型对 30m 分辨率像元进行建模外推，并开展多组对比实验与时空动态分析，最终形成 2017–2024 年广东省森林 AGB “墙对墙”制图结果。

将筛选后的 20 个关键特征（如 Slope、NDVI8A5、MNDWI、VV\_diss 等）输入 XGBoost 模型后，十折交叉验证结果显示其反演精度优于传统回归与随机森林模型，达到 R<sup>2</sup> = 0.607，RMSE = 36.51 Mg/ha，MAE = 22.51 Mg/ha。SHAP 解释方法进一步揭示了模型机制，发现多数变量对 AGB 的影响呈现非线性关系，其中 Slope 在 14°为关键阈值，NDVI8A5 在 0.6 附近由负转正，VV\_diss、MNDWI 等存在多段效应。

为进一步验证建模策略的稳健性，设计了三类共计 30 余组对比实验，系统评估不同激光波束类型（覆盖/全功率）、灵敏度阈值（0.95-0.98）、昼夜时段、空间分辨率（30m–500m）与变量组合对模型精度的影响。结果表明，夜间全功率波束、灵敏度阈值大于 0.98 的足迹点组合可获得最优精度；而 30m 分辨率虽非精度最高，但空间表达更精细，在实用性与表达能力之间取得良好平衡。

在 8 年时序建图基础上，开展了广东省森林 AGB 的动态演变分析。总体来看，广东省 2017–2024 年森林 AGB 年均增长 1.12 Mg/ha，全省平均值由 89.2 Mg/ha 增长至 97.7 Mg/ha，表现出持续增长的良好趋势。区域上，粤北与珠三角为 AGB 高值聚集区，湛江、汕头等沿海地区 AGB 相对较低。Sen 斜率与 Mann-Kendall 联合检验结果显示，80.62\% 的像元无显著变化，10.6\% 为显著及极显著增长，揭阳、汕尾、潮州等地趋势最强。Hurst 指数整体均值为 0.609，说明广东森林生态系统 AGB 变化具有一定程度的持续性。

本研究在不依赖地面样方数据的前提下，构建了具备可解释性、可复制性、空间分辨率较高、时间连续的森林 AGB 建模框架，为大尺度遥感生态监测提供了可行思路。研究结果为广东省森林资源管理、碳储量核算与可持续发展战略制定提供了数据支持与决策参考。


## Abstract

Forest aboveground biomass (AGB) is an important indicator reflecting the structure and carbon storage of forest ecosystems, and is of great significance for resource monitoring and climate governance under the background of carbon peak and carbon neutrality. The previous AGB estimation method based on sample inventory has high accuracy locally, but is significantly limited in large-scale and spatial continuous mapping. With the development of remote sensing technology, multi-source data fusion and machine learning methods provide a feasible path for achieving high-resolution, continuous, and multi-temporal AGB inversion.

This study takes Guangdong Province as the study area, selects GEDI L4A footprint-level AGB from 2019 to 2023 as the target variable, integrates Sentinel-2 optical images, Sentinel-1 radar images, and Copernicus 30m DEM data, and constructs a multi-source remote sensing feature dataset. A total of 67 candidate variables in 5 categories were extracted, including 12 apparent reflectance bands, 11 vegetation indices, 24 NDVI texture features, 15 radar and radar texture features, and 3 terrain factors. The XGBoost regression model was used to model and extrapolate the 30m resolution pixels, and multiple groups of comparative experiments and spatiotemporal dynamic analysis were carried out, and finally the "wall-to-wall" mapping results of forest AGB in Guangdong Province from 2017 to 2024 were formed.

After the 20 selected key variables (such as Slope, NDVI8A5, MNDWI, VV\_diss, etc.) were input into the XGBoost model, the ten-fold cross-validation results showed that its inversion accuracy was better than that of the traditional regression and random forest models, reaching R<sup>2</sup> = 0.607, RMSE = 36.51 Mg/ha, and MAE = 22.51 Mg/ha. The SHAP interpretation method further revealed the model mechanism and found that the influence of most variables on AGB showed a nonlinear relationship, among which Slope was the key threshold at 14°, NDVI8A5 turned from negative to positive near 0.6, and VV\_diss, MNDWI, etc. had multi-segment effects.

To further verify the robustness of the modeling strategy, three types of more than 30 comparative experiments were designed to systematically evaluate the effects of different laser beam types (coverage/full power), sensitivity thresholds (0.95-0.98), day and night time periods, spatial resolutions (30m–500m) and variable combinations on model accuracy. The results show that the combination of full-power beam at night and footprint points with a sensitivity threshold greater than 0.98 can achieve the best accuracy; although the 30m resolution is not the most accurate, the spatial expression is more refined, achieving a good balance between practicality and expression ability.

Based on the 8-year time series mapping, the dynamic evolution analysis of forest AGB in Guangdong Province was carried out. Overall, the average annual growth rate of forest AGB in Guangdong Province from 2017 to 2024 was 1.12 Mg/ha, and the provincial average value increased from 89.2 Mg/ha to 97.7 Mg/ha, showing a good trend of sustained growth. Regionally, northern Guangdong and the Pearl River Delta are high-value AGB clusters, while coastal areas such as Zhanjiang and Shantou have relatively low AGB. The results of the joint test of Sen slope and Mann-Kendall showed that 80.62\% of the pixels had no significant change, 10.6\% showed significant and extremely significant growth, and the strongest trend was seen in Jieyang, Shanwei, Chaozhou and other places. The overall mean of the Hurst index was 0.609, indicating that the AGB change of Guangdong's forest ecosystem had a certain degree of continuity.

This study constructed a forest AGB modeling framework that is interpretable, replicable, with high spatial resolution and time continuity without relying on ground sample data, providing a feasible idea for large-scale remote sensing ecological monitoring. The research results provide data support and decision-making reference for forest resource management, carbon stock accounting and sustainable development strategy formulation in Guangdong Province.


### 关键词

森林地上生物量，多源遥感，GEDI，XGBoost 建模，时空变化分析

###  Keywords

Forest Aboveground Biomass, Multi-source Remote Sensing, GEDI, XGBoost Modeling, Spatiotemporal Analysis

## 目录

### [1 绪论](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/Chapter1_%E7%BB%AA%E8%AE%BA.md)
- 1.1 研究背景与意义
- 1.2 国内外研究现状
  - 1.2.1 基于样方清查与异速生长方程的森林 AGB 估算现状与分析
  - 1.2.2 基于光学影像和 SAR 数据的森林 AGB 反演现状与分析 
  - 1.2.3 基于 LiDAR 联合光学影像和 SAR 的森林 AGB 反演现状与分析
- 1.3 研究内容
- 1.4 技术路线

### [2 研究区与数据源](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/Chapter2_%E7%A0%94%E7%A9%B6%E5%8C%BA%E4%B8%8E%E6%95%B0%E6%8D%AE%E6%BA%90.md)
- 2.1 研究区概况
  - 2.1.1 地理位置和行政区划
  - 2.1.2 地形地貌
  - 2.1.3 森林资源状况
- 2.2 数据源
  - 2.2.1 GEDI 数据
  - 2.2.2 Sentinel-2 数据
  - 2.2.3 Sentinel-1 数据
  - 2.2.4 地形数据
- 2.3 特征因子提取
### [3 广东省森林地上生物量反演模型构建与评价](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/Chapter3_%E5%B9%BF%E4%B8%9C%E7%9C%81%E6%A3%AE%E6%9E%97%E5%9C%B0%E4%B8%8A%E7%94%9F%E7%89%A9%E9%87%8F%E5%8F%8D%E6%BC%94%E6%A8%A1%E5%9E%8B%E6%9E%84%E5%BB%BA%E4%B8%8E%E8%AF%84%E4%BB%B7.md)
- 3.1 模型构建与评价
- 3.2 模型机理解释
  - 3.2.1 总体分析
  - 3.2.2 各特征依赖图分析
- 3.3 不同变量组合对反演模型的影响
- 3.4 不同激光波束选择对反演模型的影响
- 3.5 不同空间分辨率对反演模型的影响

### [4 广东省森林地上生物量时空动态变化分析](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/Chapter4_%E5%B9%BF%E4%B8%9C%E7%9C%81%E6%A3%AE%E6%9E%97%E5%9C%B0%E4%B8%8A%E7%94%9F%E7%89%A9%E9%87%8F%E6%97%B6%E7%A9%BA%E5%8A%A8%E6%80%81%E5%8F%98%E5%8C%96%E5%88%86%E6%9E%90.md)
- 4.1 广东省森林地上生物量反演结果及其描述性统计
- 4.2 广东省森林地上生物量的空间分布
- 4.3 与现有森林地上生物量产品比较
  - 4.3.1 与 Yang 等人的森林地上生物量产品对比
  - 4.3.2 与 ESA CCI 森林地上生物量产品对比
  - 4.3.3 与 CFATD 森林地上生物量产品对比
- 4.4 2017-2024 年广东省森林地上生物量的变化趋势分析
  - 4.4.1 变异系数分析
  - 4.4.2 线性回归分析
  - 4.4.3 基于 Theil-Sen 方法与 Mann-Kendall 检验的趋势分析
- 4.5 广东省森林地上生物量可能的未来变化趋势分析
### [5 总结与展望](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/Chapter5_%E6%80%BB%E7%BB%93.md)
- 5.1 主要结论
- 5.2 存在的不足与研究展望
