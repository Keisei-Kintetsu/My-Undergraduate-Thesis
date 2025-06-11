## 4 广东省森林地上生物量时空动态变化分析
### 4.1 广东省森林地上生物量反演结果及其描述性统计

将 2017-2024 年各年的预测结果分别用该年的 CLCD（China Land Cover Dataset）数据集的森林像元掩膜，得到 8 年广东省森林 AGB 制图结果。

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/b220e64a88891f6ecdd77ad7c41b5e290e87c45c/figure/%E5%90%88%E5%B9%B6%E9%A2%84%E6%B5%8B%E5%87%BA%E5%9B%BE-%E5%B8%A6%E6%A0%87%E7%AD%BE.svg">
</div>

<p align="center">
图 4.1&ensp;30m 空间分辨率的广东省 2017-2024 年森林 AGB 反演结果
</p>


制图结果细节展示图中选取肇庆羚羊峡、清远笔架山、阳江阳西县三个广东省典型森林分布区，每行依次给出 1km、5km、10km 边长正方形视窗的放大效果；列方向展示 2017–2024 年 30m 分辨率 AGB 预测结果。制图结果反应了多尺度下时序变化与空间细节的保真度。


<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/f1b6fd1cfe48b7643ae82bd05d0ade021747cded/figure/%E6%8C%91%E5%9B%BE.svg"  style="width:95%;">
</div>

<p align="center">
图 4.2&ensp;30m 空间分辨率的广东省 2017-2024 年森林 AGB 反演结果细节展示
</p>

对反演结果进行描述性统计分析。如小提琴图及箱线图、描述性统计表所示，各年份森林 AGB 像元的分布范围较宽，最小值约 9–10 Mg/ha，最大值可达 425–459 Mg/ha。每年均值与中值接近（差值 ≤2 Mg/ha），表明分布大体对称；标准差稳定在 27–30 Mg/ha，显示总体离散程度适中。小提琴图主体区域与表中第 25 和 75 百分位数（约 68–118 Mg/ha）一致，密度最高区间集中于 70-110Mg/ha。


<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/eba0ed0d9375063db602ba26d2dcf426d2b7c96d/figure/%E5%B9%BF%E4%B8%9C%E7%9C%812017-2024%E5%B9%B4%E6%A3%AE%E6%9E%97AGB%E5%B0%8F%E6%8F%90%E7%90%B4%E5%8F%8A%E7%AE%B1%E7%BA%BF%E5%9B%BE.svg" style="width:95%;">
</div>

<p align="center">
图 4.3&ensp;广东省 2017-2024 年森林 AGB 小提琴及箱线图
</p>


所有年度的偏度介于 0.27–0.38，呈轻微右偏，长尾主要由少量高 AGB 像元贡献；峰度接近 0，略呈轻微平顶特征，说明分布尖陡程度与正态分布相近。1\% 与99\%百分位数分别位于 35–39 Mg/ha 与 157–171 Mg/ha，两侧尾部占比极小，印证图中须线以外异常值的稀疏性。总体来看，AGB 像元在中低区间分布最为密集，高值像元数量有限但对最大值和右尾拉伸作用显著。

<p align="center">
表 4.1&ensp;2017-2024 年各年广东省森林 AGB 的描述性统计表（除偏度和峰度外，单位：Mg/ha）
</p>
<div align="center">
<table>
    <tr>
        <th>年份</th>
        <th>最小值</th>
        <th>最大值</th>
        <th>平均值</th>
        <th>中值</th>
        <th>标准差</th>
        <th>第 1 百分位数</th>
        <th>第 99 百分位数</th>
        <th>偏度</th>
        <th>峰度</th>
    </tr>
    <tr>
        <td>2017</td>
        <td>9.31</td>
        <td>429.76</td>
        <td>89.20</td>
        <td>87.87</td>
        <td>28.20</td>
        <td>34.98</td>
        <td>156.93</td>
        <td>0.3413</td>
        <td>0.1837</td>
    </tr>
    <tr>
        <td>2018</td>
        <td>9.39</td>
        <td>454.14</td>
        <td>89.44</td>
        <td>88.06</td>
        <td>28.08</td>
        <td>35.50</td>
        <td>157.16</td>
        <td>0.3513</td>
        <td>0.2140</td>
    </tr>
    <tr>
        <td>2019</td>
        <td>9.22</td>
        <td>458.99</td>
        <td>89.25</td>
        <td>87.78</td>
        <td>28.11</td>
        <td>35.57</td>
        <td>157.44</td>
        <td>0.3666</td>
        <td>0.2356</td>
    </tr>
    <tr>
        <td>2020</td>
        <td>9.57</td>
        <td>458.99</td>
        <td>91.80</td>
        <td>89.95</td>
        <td>29.48</td>
        <td>35.81</td>
        <td>165.72</td>
        <td>0.3761</td>
        <td>-0.0280</td>
    </tr>
    <tr>
        <td>2021</td>
        <td>10.14</td>
        <td>426.32</td>
        <td>90.00</td>
        <td>88.50</td>
        <td>27.59</td>
        <td>36.20</td>
        <td>158.64</td>
        <td>0.3392</td>
        <td>-0.0203</td>
    </tr>
    <tr>
        <td>2022</td>
        <td>9.57</td>
        <td>425.23</td>
        <td>92.44</td>
        <td>91.17</td>
        <td>28.31</td>
        <td>37.38</td>
        <td>160.73</td>
        <td>0.2800</td>
        <td>-0.2077</td>
    </tr>
    <tr>
        <td>2023</td>
        <td>9.22</td>
        <td>428.12</td>
        <td>94.73</td>
        <td>93.24</td>
        <td>29.58</td>
        <td>37.33</td>
        <td>168.39</td>
        <td>0.3446</td>
        <td>0.0272</td>
    </tr>
    <tr>
        <td>2024</td>
        <td>9.22</td>
        <td>432.16</td>
        <td>97.73</td>
        <td>96.74</td>
        <td>29.94</td>
        <td>38.28</td>
        <td>170.99</td>
        <td>0.2731</td>
        <td>-0.0800</td>
    </tr>
    <tr>
        <td>平均</td>
        <td>10.49</td>
        <td>415.27</td>
        <td>92.23</td>
        <td>91.83</td>
        <td>26.40</td>
        <td>39.23</td>
        <td>153.71</td>
        <td>0.1741</td>
        <td>-0.3044</td>
    </tr>
</table>
</div>



### 4.2 广东省森林地上生物量的空间分布

广东省 2017-2024 年平均森林 AGB 空间分布图展示出森林 AGB 空间格局整体呈现区域差异。珠三角与粤北的均值分别为 95.36 Mg/ha 与 94.42 Mg/ha，在四大分区中处于最高水平；粤西与粤东平均值分别为 83.00 Mg/ha 和 80.93 Mg/ha，明显低于前两区。四区中位数与均值差距均小于 1.5 Mg/ha，说明像元分布大体对称。标准差范围 24.70–28.05 Mg/ha，反映内部离散度相近；珠三角虽最高值可达 415.27 Mg/ha，但偏度仅 0.07，分布最接近对称，而粤东与粤西偏度约 0.46，右尾像元比例更高。各区第 1 与 99 百分位数间距在 110 Mg/ha 左右，表明极端低、高值像元占比均较小。

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/4848e7e6e791297fe9d241b20c0738554ea15699/figure/%E5%B9%B3%E5%9D%87%E5%80%BC%E7%BB%98%E5%9B%BE%E6%80%BB%E5%9B%BE3.svg">
<div>

<p align="center">
图 4.4&ensp;广东省 2017-2024 年平均森林 AGB 空间分布图
</p>

<p align="center">
表 4.2&ensp;广东省各地区 2017-2024 年各年平均森林 AGB 描述性统计表（除偏度和峰度外，单位：Mg/ha）
</p>

<div align="center">
    <table>
        <tr>
            <th>地区</th>
            <th>最小值</th>
            <th>最大值</th>
            <th>平均值</th>
            <th>中值</th>
            <th>标准差</th>
            <th>第 1 百分位数</th>
            <th>第 99 百分位数</th>
            <th>偏度</th>
            <th>峰度</th>
        </tr>
        <tr>
            <td>粤东</td>
            <td>11.47</td>
            <td>292.56</td>
            <td>80.93</td>
            <td>78.71</td>
            <td>24.70</td>
            <td>34.75</td>
            <td>144.89</td>
            <td>0.4555</td>
            <td>-0.0103</td>
        </tr>
        <tr>
            <td>粤北</td>
            <td>18.05</td>
            <td>373.41</td>
            <td>94.42</td>
            <td>94.07</td>
            <td>25.71</td>
            <td>41.97</td>
            <td>154.56</td>
            <td>0.1752</td>
            <td>-0.2204</td>
        </tr>
        <tr>
            <td>粤西</td>
            <td>11.70</td>
            <td>324.69</td>
            <td>83.00</td>
            <td>79.98</td>
            <td>28.05</td>
            <td>34.87</td>
            <td>152.88</td>
            <td>0.4701</td>
            <td>-0.3168</td>
        </tr>
        <tr>
            <td>珠三角</td>
            <td>10.49</td>
            <td>415.27</td>
            <td>95.36</td>
            <td>95.54</td>
            <td>25.53</td>
            <td>40.78</td>
            <td>153.77</td>
            <td>0.0700</td>
            <td>-0.2416</td>
        </tr>
    </table>
</div>

<p align="left">
市域尺度进一步揭示空间差异：最高均值出现在肇庆（101.02 Mg/ha）与韶关（99.91 Mg/ha），其次为云浮、清远、广州等市（约为 95–98 Mg/ha）。湛江均值最低，仅 56.69 Mg/ha，且偏度 0.82，显示少数高值像元对总体右尾拉伸显著。除湛江外，多数城市标准差 20–26 Mg/ha，部分城市最大值可至 370 Mg/ha 以上（云浮、清远、韶关等），而第 1 与 99 百分位数像元大体落在 30–160 Mg/ha 范围，说明大部分地区森林 AGB 集中于中低水平，局部高值像元数量有限。
</p>

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/1c7f01129a49894eef9fc4a771e5b148b2cb0b20/figure/%E7%8E%AF%E5%BD%A2%E5%8D%8A%E5%B0%8F%E6%8F%90%E7%90%B4%E5%9B%BE_427.svg" style="width:90%;">
</div>

<p align="center">
图 4.5&ensp;广东省各市 2017-2024 年各年平均 AGB 小提琴图与箱线图
</p>

<p align="left">
将 30m 像元累积后（1 像元 = 0.09 ha），各市森林 AGB 以百万 Mg 计差异显著。韶关总量 164 Mt，高居全省首位；清远 158 Mt、肇庆 130 Mt、河源和梅州均约 127 Mt，列第二梯队，这些市林地面积均在 1.1–1.5 万km<sup>2</sup> 且森林覆盖率不低于 77%。云浮、惠州、茂名、阳江介于 50–75 Mt，对应 0.6–0.8 万km<sup>2</sup> 林地。江门与广州分别 44 Mt 和 34 Mt，虽覆盖率达 43–46%，但森林面积不足 5000 km<sup>2</sup>。湛江、潮州、揭阳、汕尾分布于 17–25 Mt 区间；深圳、佛山、东莞、珠海、汕头总量 4–7 Mt；中山最低，仅 2.9 Mt，森林覆盖率 16%。
</p>

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/1c7f01129a49894eef9fc4a771e5b148b2cb0b20/figure/%E6%80%BB%E9%87%8F%E7%BB%9F%E8%AE%A1.svg" style="width:90%;">
</div>

<p align="center">
图 4.6&ensp;广东省各市 AGB 总量统计
</p>


<h3 align="left">4.3 与现有森林地上生物量产品比较</h3>

<p align="left">
为进一步验证本研究森林 AGB 反演结果的精度与可靠性，选取了三个具代表性且空间覆盖广东省的现有 AGB 数据集进行对比分析，分别为：Yang 等人发布的全国 2019 年 30m 分辨率 AGB 产品、欧空局（ESA）提供的 100m 分辨率全球 AGB 产品，以及 Cai 等人的 CFATD 长时序 30m 分辨率中国 AGB 产品。
</p>

<p align="center">
表 4.3&ensp;现有森林地上生物量产品
</p>

<div align="center">
<table>
    <tr>
        <th>产品名称</th>
        <th>覆盖区域</th>
        <th>时间范围</th>
        <th>空间分辨率（m）</th>
        <th>参考文献</th>
    </tr>
    <tr>
        <td>Yang Map</td>
        <td>中国</td>
        <td>2019 年</td>
        <td>30</td>
        <td>Yang 等</td>
    </tr>
    <tr>
        <td>Cai (CFATD)</td>
        <td>中国</td>
        <td>1985–2023 年</td>
        <td>30</td>
        <td>Cai 等</td>
    </tr>
    <tr>
        <td>Santoro Map</td>
        <td>全球</td>
        <td>2010 年，2015-2021 年</td>
        <td>100</td>
        <td>Santoro 等</td>
    </tr>
</table>
</div>



<h4 align="left">4.3.1 与 Yang 等人的森林地上生物量产品对比</h3>


<p align="left">
Yang 等人提出基于多源遥感与森林清查数据融合的回归模型，实现了中国 30m 分辨率的 AGB 高精度空间估算。在广东地区，其反演结果在整体均值上与本研究相近（89.2 vs. 89.3 Mg/ha），但其像元值主要集中于 80–100 Mg/ha 的中间区域，缺乏明显的长尾特征，表现出较低的标准差（仅 8.5 Mg/ha）。与本研究的偏态分布相比，Yang 数据展现出较强的“压缩性”，导致在高值森林区域（如粤北山区）与低值地带（如湛江）存在显著低估与高估。
</p>

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/efc20b2aa63bd99abf5adcd45b9eff0e7d3b2ff1/figure/%E9%83%AD%E8%80%81%E5%B8%88%E7%A0%94%E7%A9%B6.svg">
<div>

<p align="center">
图 4.7&ensp;与 Yang 等人森林 AGB 产品的比较结果：(a) Yang 原始 AGB 图，(b) 与本研究作差图，(c) 像元尺度相关性图，(d) Bland–Altman 分析图
</p>

<p align="left">
Yang 等的 AGB 产品的空间分布图较为均匀，森林空间异质性被显著削弱。在像元尺度上的 Pearson 相关系数为 0.306，表明其与本研究估算结果的线性一致性较低。Bland–Altman 分析显示，两者存在一定正偏差（Bias = 4.95 Mg/ha），但 LoA 范围较宽（-42.57 至 52.46 Mg/ha），表明在个体像元尺度上波动较大。
</p>

<h4 align="left">4.3.2 与 ESA CCI 森林地上生物量产品对比</h4>

<p align="left">
ESA CCI AGB 是当前主流的全球尺度 AGB 产品之一，基于 ENVISAT ASAR 和 Sentinel-1 数据反演得到，时间序列覆盖较广，为全球森林碳储量监测提供了基础支持。然而，该产品分辨率为 100m，显著低于本研究的 30m 空间分辨率，且其训练样地严重不均衡——亚洲区域仅包含 24 个样地，且主要位于印度尼西亚等地，中国地区缺乏足够支撑。
</p>

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/9e163bc2e8448a7601ca2086d818d27948695a13/figure/ESA%E6%8B%BC%E5%9B%BE1.svg">
</div>

<p align="center">
图 4.8&ensp;2017–2021 年ESA CCI AGB 产品与本研究结果的对比图：左列为原始 AGB 图(a, c, e,g, i)，右列为对应作差图(b, d, f, h, j)
</p>

<p align="left">
如图所示，其 AGB 空间分布呈现出高值与低值同时大量存在的特征，显著不同于实际森林格局。这种双偏分布也体现在频率直方图中，大量低值像元可能源于非森林区域被纳入统计，高值异常像元则可能来自模型外推误差。与本研究结果对比，ESA CCI AGB 在广东整体呈现大幅低估的趋势，其均值普遍在 76–78 Mg/ha 左右，相关系数仅为 0.237–0.331。Bland–Altman 分析显示其系统性偏差极为显著，平均 Bias 在 97–103 Mg/ha 之间，LoA 范围普遍在 -25 至 230 Mg/ha 之间，属于三组对比数据中误差最广、系统性最强的一组。
</p>

<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/ESA%E7%9B%B8%E5%85%B3ba.png?raw=true">
</div>

<p align="center">
图 4.9&ensp;2017–2021 年 ESA CCI AGB 产品与本研究估算结果的统计对比：(a–e) 为相关性分析图，(f–j) 为 Bland–Altman 分析图
</p>


<h4 align="left">4.3.3 与 CFATD 森林地上生物量产品对比</h4>

<p align="left">
Cai 等人构建的 CFATD 数据集（China Forest Aboveground Biomass Time-series Dataset）融合 GEDI 样本与 Landsat 时间序列，采用残差神经网络 ResNet 反演 1985–2023 年 AGB，是目前中国国内精度较高、覆盖时间最完整的高分辨率 AGB 产品。其与本研究采用相近数据源和模型结构，因此具有较高的可比性。
</p>

<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/CFATD%E5%8E%9F%E5%9B%BE%E7%BB%98%E5%9B%BE%E4%B8%8E%E5%B7%AE%E5%80%BC%E7%BB%98%E5%9B%BE.png?raw=true">
</div>

<p align="center">
图 4.10&ensp;2019–2023 年 CFATD 产品与本研究结果的像元级对比图：左列为 CFATD 原始 AGB 图，右列为与本研究结果的作差图
</p>


<p align="left">
从空间分布图像上看，其结果在整体趋势上与本研究相对接近：粤北为高值区，粤西次之，粤东与湛江地区相对较低。其平均值整体略高于本研究，偏高幅度在 10–15 Mg/ha 之间，与本研究结果作差后的像元平均值大约为 20 Mg/ha 。但从直方图可见其值域与分布形态高度相似，呈偏态正分布，标准差亦与本研究接近。Bland–Altman 分析中偏差在 -19 至 -23 Mg/ha 之间，LoA范围普遍在 -105 至 60 Mg/ha 之间，说明与本研究结果相对接近。
</p>

<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/CFATD_%E7%9B%B8%E5%85%B3%E5%9B%BE%E4%B8%8Eba%E5%9B%BE.png?raw=true">
</div>

<p align="center">
图 4.12&ensp;2017–2023 年 CFATD 产品与本研究结果的统计对比图：(a–g) 为相关性分析图，(h–n) 为 Bland–Altman 分析图
</p>


<h3 align="left">4.4 2017-2024 年广东省森林地上生物量的变化趋势分析</h4>
<p align="left">
变异系数（Coefficient of Variation, CV）作为衡量时间序列数据相对离散程度的标准化指标，在生态遥感研究中常用于评估生态系统参数的稳定性。其定义为标准差与均值的比值，计算公式为：
</p>

```math
\text{CV} = \dfrac{\sigma}{\mu} = \dfrac{\sqrt{\frac{1}{N}\sum_{t=1}^{N}(X_t-\bar{X})^2}}{\frac{1}{N}\sum_{t=1}^{N}X_t} \times 100\%
```

<p align="left">
式中 $\bar{X}$ 为时间序列 $X_t$ 的算术均值，表征区域森林 AGB 的平均水平； $\sigma$ 为时间序列标准差，反映观测值的离散程度； $N$ 代表时间序列长度（本研究 $N=8$ ）。该指标通过消除量纲影响，实现跨像元、跨区域的可比性分析。当 CV 值大于 30\% 时，通常认为生态系统存在显著波动。
</p>


<div align="center">
    <img src="https://github.com/Keisei-Kintetsu/My-Undergraduate-Thesis/blob/main/figure/%E7%BB%98%E5%88%B6CV_%E5%B8%A6%E5%89%96%E9%9D%A2.png?raw=true">
</div>

<p align="center">
图 4.13&ensp;广东省森林 AGB 变异系数空间分布图
</p>

<p align="left">
结果显示，广东省森林 AGB 变异系数最大值为 0.847，整体均值为 0.120，中位数 0.110，标准差 0.055，99\% 分位数 0.298，经度剖面线的平均数为 0.123，纬度剖面线的平均数为 0.132。粤北地区 CV 数值较低，江门、汕尾、惠州东部、河源南部、茂名、湛江存在较高变异系数的像元。由于全广东 CV 值的第 99 百分位数没有超过0.3，可以认为广东省森林 AGB 绝大部分处于稳定状态。
</p>


<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/0c82798cc02c12ebe88e4363170b0e6c2f49da8a/figure/%E5%90%84%E5%B8%82CV%E6%8C%87%E6%95%B0%E7%AE%B1%E7%BA%BF%E5%9B%BE.svg">
</div>

<p align="center">
图 4.14&ensp;广东省 21 个城市变异系数箱线图
</p>

<h4 align="left">线性回归分析</h4>

<p align="left">
用 Slope 线性趋势模型（即斜率线性趋势模型），分析研究区 2017-2024 年广东省森林 AGB 的时间动态变化。设 $n$ 为时间序列长度（ $n=8$ ）；AGB<sub>i</sub>为 2017-2024 年中的第 $i$ 年的 AGB，则 Slope 为
</p>

```math
    \text{Slope}=\frac{n \times \sum_{i=1}^{n} i \times \text{AGB}_{i}-\sum_{i=1}^{n} i \sum_{i=1}^{n} \text{AGB}_{i}}{n \times \sum_{i=1}^{n} i^{2}-\left(\sum_{i=1}^{n} i\right)^{2}}
```