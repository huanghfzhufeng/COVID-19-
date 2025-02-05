# COVID-19 与在线数字教育

## 一、项目背景
COVID-19 疫情期间，线上教育成为重要的教学方式。本项目旨在研究疫情对美国某些学区学生使用数字教育平台的影响，通过分析确诊病例、死亡人数与学生使用教育平台的访问率和交互指数之间的关系，探讨疫情下数字学习的趋势。

## 二、数据加载与处理

### 数据集介绍
- **districts_info.csv**：包含学区的基本信息，如学区唯一标识、所属州、区域类型、学生种族比例、午餐计划参与比例、网络连接情况和国家总支出等。
- **products_info.csv**：提供产品的详细信息，包括产品唯一标识、网站链接、产品名称、提供商名称、使用部门和基本功能等。
- **us_counties.csv**：记录美国各县的疫情数据，如日期、州、累计确诊病例和累计死亡人数等。
- **以学区编号命名的 CSV 文件（如8815.csv）**：存储学区级别的汇总数据，包括日期、产品唯一标识、学生访问比例和交互指数等。

### 数据处理步骤
1. 导入必要的库，如 `numpy`、`pandas`、`matplotlib` 等，并进行相关设置，如忽略警告、设置中文字体等。
2. 读取 `districts_info.csv` 文件，处理缺失值，解析相关列的数据，如学生比例、午餐计划比例、网络连接比例和国家总支出等，并选择所需列。
3. 读取 `products_info.csv` 文件，处理缺失值，提取产品基本功能的主要分类和子分类。
4. 定义函数 `read_engagement` 读取学区数据文件，处理缺失值并添加学区唯一标识。
5. 读取 `us_counties.csv` 文件，删除不必要的列，按日期和州汇总病例数和死亡数。
6. 定义函数 `district_product_covid`，将学区的产品参与数据、学区属性数据和新冠疫情数据进行合并，生成综合数据框。

## 三、数据可视化分析

### 绘制工具
- **bar_plot 函数**：用于绘制柱状图，可展示不同维度数据的分布，如各州学区数量、不同区域类型学区数量、各类学生比例区间内学区数量等。
- **line_plot 函数**：绘制折线图，用于展示产品访问率或交互指数随时间的变化，并与同期疫情数据（确诊病例和死亡人数）进行对比。

### 学区表数据可视化
- **各州学区数量**：通过柱状图展示各州学区数量分布，可看出不同州学区规模差异，如伊利诺伊州、加利福尼亚州等学区数量较多。
- **区域类型分布**：分析不同区域类型（郊区、城市、城镇、农村）的学区数量，发现郊区学区数量明显多于其他类型区域。
- **学生比例相关分析**
  - **黑人学生比例**：绘制黑人学生比例区间内学区数量柱状图，多数学区黑人学生比例在 0 - 20% 和 20% - 40% 区间。
  - **西班牙裔学生比例**：展示西班牙裔学生比例区间内学区数量，20% - 40% 区间内学区数量较多。
- **午餐计划相关比例**
  - **免费午餐学生比例**：多数学区免费午餐学生比例在 20% - 40%，反映部分学区学生经济情况较好。
  - **减价午餐学生比例**：40% - 60% 区间内学区较多，说明有相当比例学生符合减价午餐资格。
  - **网络连接比例**：所有学区网络连接方向比例数据一致，均为 18%；网络连接住户比例均为 100%，表明各学区网络连接情况无显著差异，且家庭网络覆盖完全。

### 产品表数据可视化
- **产品提供商分析**：Google LLC 提供的产品数量最多，Houghton Mifflin Harcourt、Microsoft、PBS 等公司提供的产品数量在 5 - 10 个左右。
- **教育部门使用情况**：PreK - 12 领域使用的产品最多，纯企业使用的产品数量远少于其他领域，表明小学至高中领域对教育技术产品需求最大。
- **产品主要功能分类**：LC（学习与课程）类别的产品数量明显占主导地位，课堂管理和学校运营的产品数量较少。

### 统计数据表数据可视化（以学区 8815 为例）
- **产品访问率分布**：产品 32213 访问比例最高，部分产品访问比例也相对较高，其余产品访问比例较低。
- **交互指数分布**：产品 32213 的交互指数远高于其他产品，表明其在学区中被频繁使用，功能性或吸引力强。

### 整合数据可视化
- **学生对数字平台使用情况与疫情发展关系**
  - 2020 年 3 月后确诊病例缓慢上升，访问比例波动；9 月后访问比例明显增加并保持较高水平，确诊病例也大幅增长。死亡人数增长轨迹与确诊病例相似，访问比例随死亡人数增加而上升。
- **学生使用数字平台交互指数与疫情发展关系**
  - 疫情初期交互指数波动，疫情高峰期间显著上升；确诊病例数增长与交互指数增长不完全同步。死亡人数在疫情初期至中期缓慢增加，高峰期大幅增长，与交互指数波动吻合，整体上交互指数随死亡人数上升而上升。

## 四、可视化结果分析
- **访问率与确诊病例数关系**：疫情初期访问率波动，确诊病例增多时总体上升，疫情爆发期间急剧上升，表明学校转向线上教育，学生依赖数字学习平台。
- **交互指数与确诊病例数关系**：交互指数随确诊病例数波动，高峰期间显著上升，因远程学习和作业活动增加，学生互动更频繁。
- **访问率与死亡人数关系**：死亡人数增加与访问率呈正相关，疫情初期访问率波动，死亡人数增长时访问率上升，反映线上学习需求增加。
- **交互指数与死亡人数关系**：死亡人数急剧上升期间交互指数增长，表明疫情严重时学生在数字平台学习和互动更频繁。

## 五、实验总结
- **实验结果**：COVID-19 疫情显著影响学区学生使用数字教育平台，确诊病例和死亡人数增加时，学生访问频率和互动指数上升，远程数字学习成为常态，疫情高峰时学校更依赖线上教育平台。
- **不同地区数字教育平台使用差异与网络接入比例、学区经济条件等因素密切相关，推动远程学习需改善网络基础设施和提供更多教育资源支持。**
- **不足之处**：未进行关联挖掘，未对 4921、5987、3710、7177 等学区进行数据可视化分析。未来可进一步深入挖掘数据关系，对更多学区进行分析，以全面了解疫情对不同学区数字教育的影响。