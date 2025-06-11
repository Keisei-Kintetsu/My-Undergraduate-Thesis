## 4 广东省森林地上生物量时空动态变化分析
### 4.1 广东省森林地上生物量反演结果及其描述性统计

将 2017-2024 年各年的预测结果分别用该年的 CLCD（China Land Cover Dataset）数据集的森林像元掩膜，得到 8 年广东省森林 AGB 制图结果。

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/b220e64a88891f6ecdd77ad7c41b5e290e87c45c/figure/%E5%90%88%E5%B9%B6%E9%A2%84%E6%B5%8B%E5%87%BA%E5%9B%BE-%E5%B8%A6%E6%A0%87%E7%AD%BE.svg">
</div>

<p align="center">
图 4.1 30m 空间分辨率的广东省 2017-2024 年森林 AGB 反演结果
</p>


制图结果细节展示图中选取肇庆羚羊峡、清远笔架山、阳江阳西县三个广东省典型森林分布区，每行依次给出 1km、5km、10km 边长正方形视窗的放大效果；列方向展示 2017–2024 年 30m 分辨率 AGB 预测结果。制图结果反应了多尺度下时序变化与空间细节的保真度。


<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/f1b6fd1cfe48b7643ae82bd05d0ade021747cded/figure/%E6%8C%91%E5%9B%BE.svg"  style="width:95%;">
</div>

<p align="center">
图 4.2 30m 空间分辨率的广东省 2017-2024 年森林 AGB 反演结果细节展示
</p>

对反演结果进行描述性统计分析。如小提琴图及箱线图、描述性统计表所示，各年份森林 AGB 像元的分布范围较宽，最小值约 9–10 Mg/ha，最大值可达 425–459 Mg/ha。每年均值与中值接近（差值 ≤2 Mg/ha），表明分布大体对称；标准差稳定在 27–30 Mg/ha，显示总体离散程度适中。小提琴图主体区域与表中第 25 和 75 百分位数（约 68–118 Mg/ha）一致，密度最高区间集中于 70-110Mg/ha。


<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/eba0ed0d9375063db602ba26d2dcf426d2b7c96d/figure/%E5%B9%BF%E4%B8%9C%E7%9C%812017-2024%E5%B9%B4%E6%A3%AE%E6%9E%97AGB%E5%B0%8F%E6%8F%90%E7%90%B4%E5%8F%8A%E7%AE%B1%E7%BA%BF%E5%9B%BE.svg" style="width:95%;">
</div>

<p align="center">
图4.3 广东省 2017-2024 年森林 AGB 小提琴及箱线图
</p>


所有年度的偏度介于 0.27–0.38，呈轻微右偏，长尾主要由少量高 AGB 像元贡献；峰度接近 0，略呈轻微平顶特征，说明分布尖陡程度与正态分布相近。1\% 与99\%百分位数分别位于 35–39 Mg/ha 与 157–171 Mg/ha，两侧尾部占比极小，印证图中须线以外异常值的稀疏性。总体来看，AGB像元在中低区间分布最为密集，高值像元数量有限但对最大值和右尾拉伸作用显著。

<p align="center">
表4.1 2017-2024 年各年广东省森林 AGB 的描述性统计表（除偏度和峰度外，单位：Mg/ha）
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
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/65cc8820fcc0816b8ad139f84694f56feb388e41/figure/%E5%B9%B3%E5%9D%87%E5%80%BC%E7%BB%98%E5%9B%BE%E6%80%BB%E5%9B%BE3.svg">
<div>

<p align="center">
图4.4 广东省 2017-2024 年平均森林 AGB 空间分布图
</p>

<p align="center">
表4.2 广东省各地区 2017-2024 年各年平均森林 AGB 描述性统计表（除偏度和峰度外，单位：Mg/ha）
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
图4.5 广东省各市 2017-2024 年各年平均 AGB 小提琴图与箱线图
</p>

<div align="center">
    <img src="https://raw.githubusercontent.com/Keisei-Kintetsu/My-Undergraduate-Thesis/1c7f01129a49894eef9fc4a771e5b148b2cb0b20/figure/%E6%80%BB%E9%87%8F%E7%BB%9F%E8%AE%A1.svg" style="width:90%;">
</div>

<p align="center">
图4.6 广东省各市 AGB 总量统计
</p>

