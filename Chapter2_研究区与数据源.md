## 2 研究区与数据源

### 2.1 研究区概况
#### 2.1.1 地理位置和行政区划

如图所示，本研究以广东省（北纬 20°19′-25°31′，东经 109°45′-117°20′）为研究范围。广东省位于中国南部，西与广西壮族自治区接壤，北部与湖南、江西省相邻，与福建交界于东北，总面积 177,900 km<sup>2</sup> 。广东省横跨北回归线，受夏季风和热带气旋的影响，降雨丰富，属亚热带、热带季风气候地区，平均气温为 21.9&deg;C ，年平均降水量 1789.3 mm。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/f4069dd7d17ede229ed9225db70ed1e759413ec5/figure/%E7%A0%94%E7%A9%B6%E5%8C%BA2.svg)

<p align="center">
图 2.1&ensp;研究区位图 (a) 广东省在中国的位置；(b) 广东省高程图；(c) 广东省行政区划图
注：基于自然资源部标准地图服务系统审图号为 GS(2020)4619 号的标准地图制作，底图边界无修改。下同。
</p>


广东省现辖 21 个地级市，其中广州、深圳两市行政级别为副省级。全省合共有 122 个县级行政区，包括 65 个市辖区、20 个县级市、34 个县、3 个自治县。按照地理位置和经济特点划分，全省可分为粤北地区、粤西地区、粤东地区以及珠三角地区。

#### 2.1.2 地形地貌

广东地貌类型复杂多样，以山地、丘陵为主，分别占全省土地总面积的 33.7\%、24.9\%，台地和平原仅占 14.2\% 和 21.7\%，山脉多以北东―南西走向，总体地势北高南低，北部多为山地和丘陵，海拔最高处为 1902 米，位于清远阳山县与湖南省的交界处的石坑崆。珠江三角洲地势平坦，其余平原分布在潮汕、茂名、湛江。此外还有罗定盆地、英德盆地、韶关盆地等小型盆地。

#### 2.1.3 森林资源状况
广东省森林资源丰富，分布有大量原始森林。根据 2023 年 CLCD 土地分类数据，森林覆盖面积 1.43 亿亩，森林覆盖率达 53.03\%，以亚热带常绿针叶林及常绿阔叶林为主要林种。其中广州、惠州、东莞、珠海、肇庆、佛山、江门、深圳、中山、汕头、梅州、韶关和阳江共 13 个城市于 2008 年至 2022 年陆续被评为“国家森林城市”称号。广东省建设有多个森林公园，如小坑国家森林公园、韶关国家森林公园、流溪河国家森林公园、鼎湖山森林公园等。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/aa15264dc7826346ce410867c5f1d82da7002a5a/figure/%E5%B9%BF%E4%B8%9C%E6%A0%91%E7%A7%8D%E7%BB%98%E5%9B%BE.svg)

<p align="center">
图 2.2&ensp;广东省植被分布图
</p>


### 2.2 数据源
#### 2.2.1 GEDI 数据

GEDI 是在 2018 年 12 月 5 日搭载于国际空间站（International Space Station, ISS）日本实验舱外设施的星载激光雷达系统，原计划运行两年，后延长至 2023 年 3 月，持续提供全球森林动态监测数据。GEDI 仪器同时发射三束激光。其中一束分成两束覆盖光束（Coverage Laser），另外两束激光为全功率光束（Full Power Laser）。这四束激光中，通过每一束都会通过光束摆动单元（Beam Dithering Units, BDUs）进行抖动分束，以产生八条地面轨迹，在约 4.2 公里的幅宽内沿飞行轨迹方向相隔约 600 米。星下轨道左侧的四束覆盖光束均来自上述第一台激光器，而右侧的四束功率光束则来自两台激光器）。每条地面轨道的激光光束覆盖面积直径为 25 米，沿轨道间距为 60 米。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/864d045f7c92cea96a111013258b4f82c0c64692/figure/GEDI%E8%BD%A8%E9%81%93%E7%A4%BA%E6%84%8F%E5%9B%BE%E6%B5%8B%E8%AF%95.svg)

<p align="center">
图 2.3&ensp;GEDI 地面采样模式示意图
</p>

为展示 GEDI 观测在广东省内的空间覆盖情况，将研究区划分为 1km &times; 1km 的栅格单元，并统计每个栅格内的 GEDI 足迹数量，生成足迹密度图（单位：个/km<sup>2</sup>）。从数值上看，2022年为观测密度最高的一年，平均密度达 108813.38 个/km<sup>2</sup>，最大值达到 1354648.88 个/km<sup>2</sup>。2023 年因 GEDI 任务于 3 月退役，足迹数量减少，平均值降至 17688.98 个/km<sup>2</sup>。五年合并后的足迹密度平均值达 355393.19 个/km<sup>2</sup>。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/4dd21984350a334277dd06247f17a37178056a02/figure/%E5%AF%86%E5%BA%A6%E4%BD%9C%E5%9B%BE-%E6%8B%BC%E5%9B%BE-%E5%B8%A6%E6%A0%87%E7%AD%BE.svg)

<p align="center">
图 2.4&ensp;广东省 GEDI 足迹密度
</p>

GEDI 数据产品具有不同的形式。1 级和 2 级为较低级数据，由 LPDAAC 团队提供，提供地理定位波形（L1B），足迹级地面高程、冠层高度、相对高度（L2A）；3、4级较高级由 ORNLDAAC 负责，包括格网树冠高度指标（L3），足迹级地上生物量指标（L4A）、格网地上生物量密度（L4B）、足迹级波形结构复杂性指数（L4C）。

<p align="center">
表 2.1&ensp;GEDI 各级数据
</p>

<div align="center">
<table>
    <tr>
        <th>级别名</th>
        <th>数据形式</th>
        <th>数据产品</th>
        <th>分辨率</th>
        <th>数据负责团队</th>
    </tr>
    <tr>
        <td>L1B</td>
        <td>足迹级</td>
        <td>地理定位波形</td>
        <td>25m 直径</td>
        <td>LPDAAC</td>
    </tr>
    <tr>
        <td>L2A</td>
        <td>足迹级</td>
        <td>地面高程、冠层高度、相对高度</td>
        <td>25m 直径</td>
        <td>LPDAAC</td>
    </tr>
    <tr>
        <td>L2B</td>
        <td>足迹级</td>
        <td>冠层覆盖度及其剖面、叶面积指数及其剖面</td>
        <td>25m 直径</td>
        <td>LPDAAC</td>
    </tr>
    <tr>
        <td>L3</td>
        <td>格网</td>
        <td>树冠高度指标</td>
        <td>1km 格网</td>
        <td>ORNLDAAC</td>
    </tr>
    <tr>
        <td>L4A</td>
        <td>足迹级</td>
        <td>地上生物量相关指标</td>
        <td>25m 直径</td>
        <td>ORNLDAAC</td>
    </tr>
    <tr>
        <td>L4B</td>
        <td>格网</td>
        <td>地上生物量密度</td>
        <td>1km 格网</td>
        <td>ORNLDAAC</td>
    </tr>
    <tr>
        <td>L4C</td>
        <td>足迹级</td>
        <td>波形结构复杂性指数</td>
        <td>25m 直径</td>
        <td>ORNLDAAC</td>
    </tr>
</table>
</div>


GEDI L4A 数据是目前全球唯一在足迹尺度上，结合参数建模与严格误差控制框架，对地上生物量（密度）进行高精度估算的全球尺度卫星产品。于 2022 年由马里兰大学 Duncanson 团队开发。该数据在全球 13,989 个样地中，用机载激光雷达（ALS）数据模拟 GEDI 波形，并结合已有的地面样地 AGB 数据，建立校准数据库。以普通最小二乘回归（Ordinary Least Squares，OLS）为基础的参数化模型形式，引入对 RH（Relative Height）指标和 AGB 的变换（对数或平方根变换），即

$$h(\text{AGB})=\sum_{j=1}^{p} B_{j} f\left(x_{j}\right)+\varepsilon $$

$$\widehat{\text{AGB}}=h \left(\sum_{j=1}^{p} \hat{B_{j}} f\left(x_{j}\right)+\varepsilon\right)$$

其中， $B_{j}$ 是回归系数和 $p$ 个预测因子 $x_j$ （如 RH98、RH50）， $f()$ 是变换函数（恒等式、对数或平方根）， $h()$ 是反变换函数（恒等式、指数函数或二次幂）， $\varepsilon$ 是均值为零的正态分布误差项。

模型开发者考虑了 1 至 4 个 RH 指标及其两两交互项的组合，最终筛选出最具解释力且具泛化能力的变量子集。为了进一步提升模型的适用性与准确性，产品在全球范围内引入了“地理分层”的策略，即依据EBT（Evergreen Broadleaf Trees，常绿阔叶树）、ENT（Evergreen Needleleaf Trees，常绿针叶树）、DBT（Deciduous Broadleaf Trees，落叶阔叶树）、GSW（Grasslands/Shrublands/Woodlands，草地/灌木丛/林地）4 种植被功能类型（Plant Functional Type, PFT）与地理区域划分建模单元。层次化建模思想极大提升了模型的空间适应性与预测精度。


![这是图片](https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/gedi_agbd_%E6%8B%BC%E5%9B%BE-%E5%B8%A6%E6%A0%87%E7%AD%BE.png?raw=true)

<p align="center">
图 2.5&ensp;GEDI L4A 数据：足迹级地上生物量密度(a) 2019 年; (b) 2020 年; (c) 2021 年; (d) 2022年; (e) 2023 年
</p>

<p align="center">
表 2.2&ensp;L4A 数据重要字段说明
</p>


<div align="center">
<table>
    <tr>
        <th>字段名称</th>
        <th>字段含义</th>
        <th>单位/取值</th>
    </tr>
    <tr>
        <td>shot_number</td>
        <td>激光点号</td>
        <td></td>
    </tr>
    <tr>
        <td>lat_lowestmode</td>
        <td>最低模式中心的纬度</td>
        <td>度</td>
    </tr>
    <tr>
        <td>lon_lowestmode</td>
        <td>最低模式中心的经度</td>
        <td>度</td>
    </tr>
    <tr>
        <td>agbd</td>
        <td>地上生物量密度</td>
        <td>Mg/ha</td>
    </tr>
    <tr>
        <td>agbd_pi_lower</td>
        <td>地上生物量密度下限预测区间</td>
        <td>Mg/ha</td>
    </tr>
    <tr>
        <td>agbd_pi_upper</td>
        <td>地上生物量密度上限预测区间</td>
        <td>Mg/ha</td>
    </tr>
    <tr>
        <td>l2_quality_flag</td>
        <td>标记识别对生物量预测最有用的L2数据</td>
        <td>0或1</td>
    </tr>
    <tr>
        <td>l4_quality_flag</td>
        <td>标记最有用的生物量预测的选择</td>
        <td>0或1</td>
    </tr>
    <tr>
        <td>sensitivity</td>
        <td>激光光束灵敏度</td>
        <td>0.90-1.00</td>
    </tr>
    <tr>
        <td>beam</td>
        <td>激光（器）编号</td>
        <td>整数，0-11</td>
    </tr>
</table>
</div>



在 GEDI 数据处理过程中，通过筛选‘Degradation flag’等于 0 和‘l4\_quality\_flag’为 1 的数据。接着，在波束选择过程中，仅保留全功率波束（即 Beams 编号为 0101、0110、1000 或 1011）并设定波束灵敏度阈值为 0.98（‘Sensitivity’大于 0.98）。此外，为减少太阳背景光的影响，采用了太阳高度角控制，仅选择夜间（‘solar\_elevation’小于 0）的数据。为了应对地形因素对 GEDI 足迹的干扰，选取坡度低于 30&deg; 的足迹。同时，通过参考椭球偏离控制，即要求 GEDI 高程与哥白尼数字高程模型计算出的高程差绝对值小于 50m。最后，为降低空间异质性带来的不确定性，将 GEDI L4A 数据与 Sentinel-2 数据中的 NDVI84 进行比值运算，并要求标准差小于 1。


<p align="center">
表 2.3&ensp;GEDI 数据处理过程
</p>

<div align="center">
<table>
    <tr>
        <th>过滤方式</th>
        <th>数据</th>
        <th>准则</th>
        <th>参考文献</th>
    </tr>
    <tr>
        <td>质量控制</td>
        <td>GEDI L4A</td>
        <td>‘Degradation_flag’=0</td>
        <td></td>
    </tr>
    <tr>
        <td>质量控制</td>
        <td>GEDI L4A</td>
        <td>‘l4_quality_flag’=1</td>
        <td></td>
    </tr>
    <tr>
        <td>激光器筛选</td>
        <td>GEDI L4A</td>
        <td>仅全功率波束 <br> Beams=0101, 0110,1000 or 1011</td>
        <td></td>
    </tr>
    <tr>
        <td>波束灵敏度筛选</td>
        <td>GEDI L4A</td>
        <td>‘Sensitivity’&gt;0.98</td>
        <td></td>
    </tr>
    <tr>
        <td>太阳高度角筛选</td>
        <td>GEDI L4A</td>
        <td>仅夜间 ‘solar_elevation’&lt; 0</td>
        <td></td>
    </tr>
    <tr>
        <td>坡度筛选</td>
        <td>GEDI L4A, Glo 30</td>
        <td>取在‘slope’&lt;30&deg; 的 GEDI 足迹</td>
        <td></td>
    </tr>
    <tr>
        <td>参考椭球偏离筛选</td>
        <td>GEDI L4A, Glo 30</td>
        <td>|  GEDI elevation - DEM  | &lt;  50m</td>
        <td></td>
    </tr>
    <tr>
        <td>空间异质性筛选</td>
        <td>GEDI L4A, Sentinel-2</td>
        <td>L4A 与 NDVI84 相除，标准差&lt;1</td>
        <td></td>
    </tr>
</table>
</div>

#### 2.2.2 Sentinel-2 数据
Sentinel-2 卫星群由两颗同步卫星 Sentinel-2A 和 2B 组成，是目前最常用的高分辨率多光谱遥感影像之一。Sentinel-2 含有 13 个波段，涵盖从可见光到近红外和短波红外波长的光谱波段，空间分辨率为 10 至 60 米不等，重访周期为 5 天。

<p align="center">
表 2.4&ensp;Sentinel-2 各波段信息
</p>


<div align="center">
<table>
    <tr>
        <th></th>
        <th>波段内容</th>
        <th>中心波长(nm)</th>
        <th>波段宽度(nm)</th>
        <th>空间分辨率(m)</th>
    </tr>
    <tr>
        <td>波段1</td>
        <td>浅水、气溶胶</td>
        <td>442.7</td>
        <td>21</td>
        <td>60</td>
    </tr>
    <tr>
        <td>波段2</td>
        <td>蓝光</td>
        <td>492.4</td>
        <td>66</td>
        <td>10</td>
    </tr>
    <tr>
        <td>波段3</td>
        <td>绿光</td>
        <td>559.8</td>
        <td>36</td>
        <td>10</td>
    </tr>
    <tr>
        <td>波段4</td>
        <td>红光</td>
        <td>664.6</td>
        <td>31</td>
        <td>10</td>
    </tr>
    <tr>
        <td>波段5</td>
        <td>植被红边</td>
        <td>704.1</td>
        <td>15</td>
        <td>20</td>
    </tr>
    <tr>
        <td>波段6</td>
        <td>植被红边</td>
        <td>740.5</td>
        <td>15</td>
        <td>20</td>
    </tr>
    <tr>
        <td>波段7</td>
        <td>植被红边</td>
        <td>782.8</td>
        <td>20</td>
        <td>20</td>
    </tr>
    <tr>
        <td>波段8</td>
        <td>近红外光</td>
        <td>832.8</td>
        <td>106</td>
        <td>10</td>
    </tr>
    <tr>
        <td>波段8A</td>
        <td>近红外光（窄段）</td>
        <td>864.7</td>
        <td>21</td>
        <td>20</td>
    </tr>
    <tr>
        <td>波段9</td>
        <td>水蒸气</td>
        <td>945.1</td>
        <td>20</td>
        <td>60</td>
    </tr>
    <tr>
        <td>波段10</td>
        <td>短波长红外光；卷云</td>
        <td>1373.5</td>
        <td>31</td>
        <td>60</td>
    </tr>
    <tr>
        <td>波段11</td>
        <td>短波长红外光</td>
        <td>1613.7</td>
        <td>91</td>
        <td>20</td>
    </tr>
    <tr>
        <td>波段12</td>
        <td>短波长红外光</td>
        <td>2202.4</td>
        <td>175</td>
        <td>20</td>
    </tr>
</table>
</div>


本研究所涉及的 Sentinel-2 影像共有 35110 张，其中 2018-2024 年各年影像数量在 4500 张左右，而 2017 年由于 Sentinel-2 卫星重访周期较长，影像张数约为 2300 张。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/8b742c4c8ef8e291162abcaf28241c5509218c5d/figure/S2_new.svg)

<p align="center">
图 2.6&ensp;(a) Sentinel-2 影像图幅在广东省的分布; (b) 本研究涉及的 Sentinel-2 影像张数
</p>



本研究使用 S2cloudless 算法对 Sentinel2 数据进行去云处理。S2cloudless 是由 Sinergise 公司 EO 研究团队开发的高效云检测算法，基于梯度提升机器学习框架，生成的 0-1 连续型云概率图可通过设定阈值转换为二值云掩膜。

#### 2.2.3 Sentinel-1 数据

合成孔径雷达（Synthetic Aperture Radar, SAR）不同于传统光学遥感，具有全天候、全天时成像能力，能够克服多云、多雾等复杂天气条件的限制。SAR 对森林冠层的面状结构和垂直结构具有较强的穿透和响应能力，因而被广泛认为是具有较大潜力的森林 AGB 反演遥感数据源。



<p align="center">
表 2.5&ensp;Sentinel-1 不同极化方式的参数特征
</p>

<div align="center">
<table>
    <tr>
        <th>极化方式</th>
        <th>空间分辨率 (m)</th>
        <th>波段类型</th>
        <th>极化描述</th>
    </tr>
    <tr>
        <td>HH</td>
        <td>10</td>
        <td>C 波段（5.405 GHz）</td>
        <td>单极化，同向 - 水平发射/水平接收</td>
    </tr>
    <tr>
        <td>HV</td>
        <td>10</td>
        <td>C 波段（5.405 GHz）</td>
        <td>双极化，交叉 - 水平发射/垂直接收</td>
    </tr>
    <tr>
        <td>VV</td>
        <td>10</td>
        <td>C 波段（5.405 GHz）</td>
        <td>单极化，同向 - 垂直发射/垂直接收</td>
    </tr>
    <tr>
        <td>VH</td>
        <td>10</td>
        <td>C 波段（5.405 GHz）</td>
        <td>双极化，交叉 - 垂直发射/水平接收</td>
    </tr>
</table>
</div>

Sentinel-1 卫星工作于 C 波段，提供了单极化（HH 或 VV）和双极化（HH+HV 或 VV+VH）观测模式。其中，VV 和 VH 极化组合对地表的散射机制更为敏感，尤其在植被结构识别和森林参数反演方面显示出更大优势。本研究所涉及的 Sentinel-1 影像共有 3458 张。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/8b742c4c8ef8e291162abcaf28241c5509218c5d/figure/S1_new.svg)

<p align="center">
图 2.7&ensp;(a) Sentinel-1 影像在广东省的分布; (b) 本研究涉及的 Sentinel-1 影像张数
</p>


### 2.2.4 地形数据

地形与森林植被获取光照以及其生长所需的土壤条件直接相关。广东省地形差异较大，地形特征对于预测森林 AGB 至关重要。本文使用欧洲航天局 30m 空间分辨率的哥白尼数字高程模型（Copernicus DEM）。并计算了坡度和坡向。如图为广东省坡度及坡向。


![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/9bf218f2f1c2049678e63e654b58354d24466260/figure/%E5%9D%A1%E5%BA%A6%E5%9D%A1%E5%90%91%E5%87%BA%E5%9B%BE%E5%8A%A0%E7%BC%96%E5%8F%B7.svg)

<p align="center">
图 2.8&ensp;(a) 广东省坡度;(b) 广东省坡向
</p>


## 2.3 特征因子提取

光学特征方面，利用 2017-2024 年逐年中值合成的 Sentinel-2 多光谱数据，提取 12 个原始波段（B2-B8、B8A、B11-B12）的表观反射率。为增强植被信息表征能力，计算了 11 种指数，包括增强型植被指数（EVI）、土壤调节植被指数（SAVI）、大气抗阻植被指数（ARVI）等经典指数。特别地，针对 Sentinel-2 特有的红边波段优势，构建 8 种归一化植被指数变体（NDVI84、NDVI85、NDVI86、NDVI87、NDVI8A4、NDVI8A5、NDVI8A6、NDVI8A7），充分挖掘红边波段对植被生理参数的敏感特性。


<p align="center">
表 2.6&ensp;光学特征、光学纹理特征
</p>


<div align="center">
<table>
    <tr>
        <th></th>
        <th>缩写</th>
        <th>特征</th>
        <th>计算方式</th>
    </tr>
    <tr>
        <td>光学特征</td>
        <td>B2 - B8,</td>
        <td>Sentinel-2 各波段反射率</td>
        <td></td>
    </tr>
    <tr>
        <td>(共25个)</td>
        <td>B8A,B11,B12</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td>EVI</td>
        <td>增强植被指数</td>
        <td>$\text{EVI} = 2.5\dfrac{\text{B8} - \text{B4}}{\text{B8} + 6 \text{B4} - 7.5  \text{B2} + 1}$</td>
    </tr>
    <tr>
        <td></td>
        <td>SAVI</td>
        <td>土壤调节植被指数</td>
        <td>$\text{SAVI} = \dfrac{\text{B8} - \text{B4}}{\text{B8} + \text{B4} + 0.5} \times (1 + 0.5)$</td>
    </tr>
    <tr>
        <td></td>
        <td>ARVI</td>
        <td>大气校正植被指数</td>
        <td>$\text{ARVI} = \dfrac{\text{B8} - (2 \times \text{B4} - \text{B2})}{\text{B8} + (2 \times \text{B4} - \text{B2})}$</td>
    </tr>
    <tr>
        <td></td>
        <td>GRVI</td>
        <td>绿色归一化植被指数</td>
        <td>$\text{GRVI} = \dfrac{\text{B3} - \text{B4}}{\text{B3} + \text{B4}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>GNDVI</td>
        <td>绿色归一化差异植被指数</td>
        <td>$\text{GNDVI} = \dfrac{\text{B8} - \text{B3}}{\text{B8} + \text{B3}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>MNDWI</td>
        <td>改进的归一化差异水体指数</td>
        <td>$\text{MSRVI} = \dfrac{\text{B3} - \text{B11}}{\text{B3} + \text{B11}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>MSRVI</td>
        <td>改进型简单比值植被指数</td>
        <td>$\text{MSRVI} = \dfrac{\text{B8}/\text{B4} - 1}{\sqrt{\text{B8}/\text{B4}} + 1}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDBI</td>
        <td>归一化建筑指数</td>
        <td>$\text{NDBI} = \dfrac{\text{B11} - \text{B8}}{\text{B11} + \text{B8}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>OSAVI</td>
        <td>优化土壤调节植被指数</td>
        <td>$\text{OSAVI} = \dfrac{\text{B8} - \text{B4}}{\text{B8} + \text{B4} + 0.16}$</td>
    </tr>
    <tr>
        <td></td>
        <td>RDVI</td>
        <td>比值差植被指数</td>
        <td>$\text{RDVI} = \dfrac{\text{B8} - \text{B4}}{\sqrt{\text{B8} + \text{B4}}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>TDVI</td>
        <td>变形植被指数</td>
        <td>$\text{TDVI} = 1.5 \times \dfrac{\text{B8} - \text{B4}}{\text{B8}^2 + \text{B4} + 1}$</td>
    </tr>
    <tr>
        <td></td>
        <td>GVI</td>
        <td>绿色植被指数</td>
        <td>$\text{TDVI} = \dfrac{\text{B8}}{\text{B3}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI84</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI84} = \dfrac{\text{B8} - \text{B4}}{\text{B8} + \text{B4}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI85</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI85} = \dfrac{\text{B8} - \text{B5}}{\text{B8} + \text{B5}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI86</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI86} = \dfrac{\text{B8} - \text{B6}}{\text{B8} + \text{B6}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI87</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI87} = \dfrac{\text{B8} - \text{B7}}{\text{B8} + \text{B7}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A4</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI8A4} = \dfrac{\text{B8A} - \text{B4}}{\text{B8A} + \text{B4}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A5</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI8A5} = \dfrac{\text{B8A} - \text{B5}}{\text{B8A} + \text{B5}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A6</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI8A6} = \dfrac{\text{B8A} - \text{B6}}{\text{B8A} + \text{B6}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A7</td>
        <td>归一化植被指数</td>
        <td>$\text{NDVI8A7} = \dfrac{\text{B8A} - \text{B7}}{\text{B8A} + \text{B7}}$</td>
    </tr>
    <tr>
        <td>光学纹理特征</td>
        <td>NDVI84_ent</td>
        <td>NDVI84信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td>(共24个)</td>
        <td>NDVI85_ent</td>
        <td>NDVI85信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI86_ent</td>
        <td>NDVI86信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI87_ent</td>
        <td>NDVI87信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A4_ent</td>
        <td>NDVI8A4信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A5_ent</td>
        <td>NDVI8A5信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A6_ent</td>
        <td>NDVI8A6信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A7_ent</td>
        <td>NDVI8A7信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
</table>

</div>

为提取空间纹理信息，采用灰度共生矩阵（Gray Level Co-occurrence Matrix, GLCM）方法对 8 种 NDVI 数据进行了纹理特征计算。设置 5&times;5 像元窗口尺寸，分别计算了信息熵（Entropy）、对比度（Contrast）和方差（Variance）三类纹理指标。其中，信息熵（ent）量化图像信息的不确定性；对比度（const）反映图像局部灰度变化程度；方差（var）描述像元值的离散程度。最终获得 24 个纹理特征（8 种 NDVI &times; 3 个指标）。设 $P_{ij}$ 表示灰度共生矩阵中灰度级 $(i, j)$ 的归一化概率值，$N$ 为灰度级总数（如 8-bit 图像时 $N=256$ ），则三种纹理特征的计算公式如下：

$$ \text{ent} = -\sum_{i=1}^{N} \sum_{j=1}^{N} P_{ij} \log P_{ij} $$

$$ \text{const} = \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij} $$

$$ \text{var} = \sum_{i=1}^{N} \sum_{j=1}^{N} (i - \mu)^2 P_{ij}, \quad \text{其中 } \mu = \sum_{i=1}^{N} i \sum_{j=1}^{N} P_{ij} $$


在雷达特征方面，基于 2017-2024 年逐年中值合成的 Sentinel-1 数据提取了 VV 和 VH极 化方式的后向散射系数。通过极化组合运算衍生出 4 个特征参数：和值（VV+VH）反映总体散射强度，差值（VV-VH）表征极化差异，乘积（VV&times;VH）增强交互信息，比值（VV/VH）描述极化比例关系。同时计算了雷达植被指数（RVI）以量化植被散射特性。在此基础上，采用 GLCM 方法对 VV/VH 波段分别提取了信息熵、对比度、方差和不相似度（diss）纹理特征，获得 8 个雷达纹理指标。不相似度的计算公式如下：

$$ \text{diss} = \sum_{i,j} P_{ij} |i - j| $$

地形特征则基于哥白尼数字高程模型数据，提取了高程（Elevation）、坡度（Slope）和坡向（Aspect）三个地形参数。


<p align="center">
表 2.7&ensp;雷达特征、雷达纹理特征、地形特征
</p>


<div align="center">
<table>
    <tr>
        <th></th>
        <th>缩写</th>
        <th>特征</th>
        <th>计算方式</th>
    </tr>
    <tr>
        <td></td>
        <td>NDVI84_const</td>
        <td>NDVI84对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI85_const</td>
        <td>NDVI85对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI86_const</td>
        <td>NDVI86对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI87_const</td>
        <td>NDVI87对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A4_const</td>
        <td>NDVI8A4对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A5_const</td>
        <td>NDVI8A5对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A6_const</td>
        <td>NDVI8A6对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A7_const</td>
        <td>NDVI8A7对比度</td>
        <td>$\text{const}= \sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI84_var</td>
        <td>NDVI84方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI85_var</td>
        <td>NDVI85方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI86_var</td>
        <td>NDVI86方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI87_var</td>
        <td>NDVI87方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A4_var</td>
        <td>NDVI8A4方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A5_var</td>
        <td>NDVI8A5方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A6_var</td>
        <td>NDVI8A6方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>NDVI8A7_var</td>
        <td>NDVI8A7方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td>雷达特征</td>
        <td>VV</td>
        <td>垂直-垂直极化</td>
        <td></td>
    </tr>
    <tr>
        <td>(共7个)</td>
        <td>VH</td>
        <td>垂直-水平极化</td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td>S1_RVI</td>
        <td>雷达植被指数</td>
        <td>$\text{RVI} = \dfrac{4 \text{VH}}{\text{VH} +\text{VV}}$</td>
    </tr>
    <tr>
        <td></td>
        <td>S1_sum</td>
        <td>VV与VH相加</td>
        <td>VV+VH</td>
    </tr>
    <tr>
        <td></td>
        <td>S1_diff</td>
        <td>VV与VH相减</td>
        <td>VV-VH</td>
    </tr>
    <tr>
        <td></td>
        <td>S1_prod</td>
        <td>VV与VH相乘</td>
        <td>VV $\times$ VH</td>
    </tr>
    <tr>
        <td></td>
        <td>S1_rept</td>
        <td>VV与VH相除</td>
        <td>VV/VH</td>
    </tr>
    <tr>
        <td>雷达纹理</td>
        <td>VV_ent</td>
        <td>VV信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td>特征 (共8个)</td>
        <td>VH_ent</td>
        <td>VH信息熵</td>
        <td>$\text{ent}=-\sum_{i=1}^{N} \sum_{j=1}^{N} P_{i j} \log P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>VV_const</td>
        <td>VV对比度</td>
        <td>$\text{const}=\sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>VH_const</td>
        <td>VH对比度</td>
        <td>$\text{const}=\sum_{i=1}^{N} \sum_{j=1}^{N} (i - j)^2 P_{ij}$</td>
    </tr>
    <tr>
        <td></td>
        <td>VV_var</td>
        <td>VV方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>VH_var</td>
        <td>VH方差</td>
        <td>$\text{var}=\sum_{i=1}^{N} \sum_{j=1}^{N}(i-\mu)^{2} P_{i j}$</td>
    </tr>
    <tr>
        <td></td>
        <td>VV_diss</td>
        <td>VV不相似度</td>
        <td>$\text{diss}=\sum{i,j}P_{i,j}|i-j|$</td>
    </tr>
    <tr>
        <td></td>
        <td>VH_diss</td>
        <td>VH不相似度</td>
        <td>$\text{diss}=\sum{i,j}P_{i,j}|i-j|$</td>
    </tr>
    <tr>
        <td>地形特征</td>
        <td>Elevation</td>
        <td>高程</td>
        <td></td>
    </tr>
    <tr>
        <td>(共3个)</td>
        <td>Slope</td>
        <td>坡度</td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td>Aspect</td>
        <td>坡向</td>
        <td></td>
    </tr>
</table>
</div>


利用 Person 相关系数矩阵展示光学、光学纹理、雷达、雷达纹理和地形特征 5 大类因素之间及其与 GEDI L4A 足迹 AGB 的线性相关关系。同一类因素由于高度的同源性，同一类变量间往往有较强的相关关系，其中光学特征、光学纹理特征之间的相关系数整体最高，此外雷达遥感特征之间也存在较强的相关性，有些甚至达到 0.95 以上，变量两两之间可能存在严重的共线性。因此后续需要通过变量筛选，能够减少特征数量、降维，使模型泛化能力更强，减少过拟合。

![这是图片](https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/a6cadd3b2bc58e163b4d3dc6e5e24394ee76cf11/figure/%E7%9B%B8%E5%85%B3%E7%83%AD%E5%9B%BE-%E4%B8%AD%E6%96%87.svg)

<p align="center">
图 2.9&ensp;候选特征集与 AGB 的相关性热图
</p>