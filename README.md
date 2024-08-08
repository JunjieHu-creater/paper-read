# 英文论文阅读笔记记录


论文研究笔记

## 目录

1. [A unified dataset for the city-scale traffic assignment model](#A-unified-dataset-for-the-city-scale-traffic-assignment-model)
2. [City-scale Vehicle Trajectory Data from Traffic Camera Videos](#City-scale-Vehicle-Trajectory-Data-from-Traffic-Camera-Videos)
3. [Counterfactual explanations and how to find them: literature review and benchmarking](#Counterfactual-explanations-and-how-to-find-them)
4. [City-level urban form and traffic safety](#City-level-urban-form-and-traffic-safety)

## A unified dataset for the city-scale traffic assignment model

[Paper link](https://www.nature.com/articles/s41597-024-03149-8#Sec16)

点击这里返回到[目录](#目录)。

### 研究局限
* 传感器数量有限，难以获取城市规模的数据
* 流量分配模型中使用的数据由各个机构负责，在结构、粒度和输出格式方面缺乏标准化
目前还没有一个统一的、经过充分验证的多城市交通数据集，覆盖了全市范围内的整个城市道路网络，这阻碍了跨城市进行综合城市研究以发掘新发现的可行性!
### 具体工作及贡献

![Framework](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41597-024-03149-8/MediaObjects/41597_2024_3149_Fig1_HTML.png?as=webp)

1. 输入数据:道路网络数据，旅行需求数据，旅行时间和速度
2. 数据融合: OD与网络数据合并，通过TAZ中心与网络节点链路，确定路径
3.流量分配：校准流量分配模型来生成基于用户均衡的数据集（利用真实的旅行时间和速度）
### 数据集
* [National Household Travel Survey](https://nhts.ornl.gov/od/)
* [travel time](https://www.tomtom.com/traffic-index/ranking/)
* [average speed](https://www.waze.com/live-map/)
* [The LODES dataset includes commuting data for the workforce in all states across the United States over multiple years, which have been widely used in existing studies](https://lehd.ces.census.gov/data/lodes/)
* [作者项目的开源数据](https://github.com/xuxiaotong/A_unified_and_validated_traffic_dataset_for_20_U.S._cities )

## City-scale Vehicle Trajectory Data from Traffic Camera Videos
[Paper link](https://www.nature.com/articles/s41597-023-02589-y)

点击这里返回到[目录](#目录)。
### 研究局限
* 由GPS设备或单个摄像头记录的传统车辆轨迹数据集通常偏向于特定车辆（例如出租车）或不完整（通常<1公里），这限制了其在下游应用中的可靠性。
* 数据集都假设所有道路交叉口的交通摄像头几乎完全覆盖，并且基于光学字符识别 （OCR） 的车牌识别系统运行完美。实际上，这些条件在当今的大多数城市中往往得不到满足25,26，这给车辆重新识别和轨迹恢复带来了挑战，可能超出这些研究中的说法。
### 相关工作
随着交通摄像头在现代城市中的广泛部署，捕捉车辆完整轨迹的机会越来越多。交通摄像头视频忠实地记录所有经过的车辆，提供了一个有希望且公正的车辆轨迹来源。如果有足够的摄像头覆盖，这些视频有可能捕捉到几乎全部的车辆轨迹。通过在城市交通摄像头系统中的不同摄像头中利用车辆重新识别技术21,22，可以重建车辆在道路网络上的完整行程。现有数据集23,24由交通摄像头生成的是从聚合的交通信息或轨迹分布得出的合成车辆轨迹。来自Wang等人的数据集。23专注于聚合的流速数据，并利用重采样技术来生成全息轨迹。相比之下，Li et al.24根据统计频率生成合成的个人层面出行数据，提供出发地、出发时间、目的地、路径等信息。然而，需要注意的是，这两个数据集都假设所有道路交叉口的交通摄像头几乎完全覆盖，并且基于光学字符识别 （OCR） 的车牌识别系统运行完美。实际上，这些条件在当今的大多数城市中往往得不到满足25,26，这给车辆重新识别和轨迹恢复带来了挑战，可能超出这些研究中的说法。
### 具体工作及贡献
![Framework](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41597-023-02589-y/MediaObjects/41597_2023_2589_Fig1_HTML.png?as=webp)
1. 输入数据:道路网络数据，摄像头数据，历史轨迹数据
2. 识别车辆：预训练CNN+车辆重识别与特征提取
3. 车辆轨迹恢复：通过车辆重识别，将多个空间-时间观察点聚类，生成初步轨迹。——————》概率空间-时间恢复模型（采用概率模型计算任意路径的概率，利用历史轨迹数据提高轨迹恢复的精度。）
4. 数据优化与验证：利用历史轨迹数据估计道路转移概率以及补全道路速度
![image](https://github.com/user-attachments/assets/4bdf1735-5d99-4e45-93b1-800c2c7b3c96)

![image](https://github.com/user-attachments/assets/1d6ccf51-0434-49b3-bd2d-abca799c739a)

### 数据集
* [城区级别轨迹（深圳济南）](https://springernature.figshare.com/collections/City-scale_Vehicle_Trajectory_Data_from_Traffic_Camera_Videos/6676199/1)
## Counterfactual explanations and how to find them
[Paper link](https://link.springer.com/article/10.1007/s10618-022-00831-6)

点击这里返回到[目录](#目录)。
### 背景
* 可解释机器学习旨在揭示不可解释分类器返回的预测背后的原因。最有价值的解释类型之一由反事实组成。
* 反事实者处于 Pearl 可解释性量表的最高水平（Pearl et al. 2009），因为它们通过强调输入中的哪些变化会导致不同的结果来回答为什么做出决定。从反事实的角度思考需要想象一个与观察到的事实相矛盾的现实，因此得名“反事实”（Molnar 2020）
* 反事实解释的研究主要集中在解决寻找反事实例子的问题上，这些例子保证了一些可取的属性。在下文中，我们将最广泛使用和共享的理想属性正式化，即有效性、最小性、相似性、合理性、判别力、可操作性、因果性和多样性。

### 反事实解释的方法
针对“解释器（分类器）而言”，找到反事实案例的方法有：
1. 优化：定义一个损失函数，使用优化式算法最小化之前提到的反事实解释所有属性损失
2. 启发式搜索：通过局部和启发式选择找到反事实，这些选择在每次迭代中都最小化了一定的成本函数
3. 基于实例：通过从数据集中选择最相似的示例来检索反事实
4. 决策树：使用决策树来近似黑匣子的行为，然后利用树结构来识别反事实解释
还可以分成内生解释器（利用已有的实例）和外生解释器（主动生成的实例）

事实上，在做反事实解释的时候，要考虑到特征之间是存在因果关系的，改变某一个特征，其他特征可能也会随之改变
### 结论
我们的文献综述显示，在过去两年中，反事实解释方法的发展取得了令人难以置信的进步。大多数反事实解释器采用优化算法，并尝试在损失函数中插入越来越多的惩罚项，以控制返回的反事实的不同期望属性。此外，这些术语中的大多数都是为了考虑合理性而设计的，并且通常依赖于预先训练的自动编码器来评估生成的示例。这些方法的主要局限性在于，它们通常是特定于模型的，并且专注于返回单个反事实。另一方面，使用其他技术的反事实解释器通常与模型无关，并返回一组不同的反事实。几乎所有的解释器都保证有效性，并且当独热编码格式被接受并得到充分管理时，可以处理分类属性。或多或少有一半的审查方法考虑了可操作性，而只有六个模型还考虑了因果关系。基于实例的解释者保证了内生反事实的合理性，而所有其他的解释者都是外生的，并采用不同形式的惩罚来解释它。从实验中可以看出，理论上保证更多属性的反事实解释者是那些通常返回单一反事实并需要最高计算时间的解释者。此外，解释者要么提供非常相似的反事实，要么提供一组不同的反事实，这些反事实必然与所分析的实例不太相似。基于优化策略的解释器通常比基于启发式、实例和决策树的解释器慢一到两个数量级。此外，运行时间并不是支持不基于优化策略的解释者的唯一指标。最后，我们观察到，不同的距离函数可以增强更关注相似性或更关注多样性的反事实搜索。作为一般性的建议，也许，我们可以建议读者首先尝试使用内生的反事实解释器，这些解释器似乎在我们工作中基准的所有礼仪方面都处于最佳表现者的交叉点上。


## City-level urban form and traffic safety

[Paper link](https://www.sciencedirect.com/science/article/pii/S0966692317307469)

点击这里返回到[目录](#目录)。

### 研究局限
* 虽然现有的研究大多考察了社区和街道建设环境对交通安全的影响，但很少有研究提供城市形态特征与城市交通安全之间关系的实证证据。
* 流量分配模型中使用的数据由各个机构负责，在结构、粒度和输出格式方面缺乏标准化
城市级城市形态特征的安全影响最常被忽视;这将包括城市的形状和土地利用模式以及社会人口构成要素在全市范围内的空间分布，这些是城市交通网络布局和出行需求的主要决定因素。此外，大量实证证据表明，出行行为（例如，模式选择和车辆行驶里程，VMT）在具有不同城市形态特征的城市中存在差异交通风险在很大程度上与出行行为决策和结果有关。因此，研究城市形态与交通安全后果之间的直接关系和间接关系具有重要意义。

### 具体工作及贡献

![Framework](https://media.springernature.com/full/springer-static/image/art%3A10.1038%2Fs41597-024-03149-8/MediaObjects/41597_2024_3149_Fig1_HTML.png?as=webp)

1. 创建了一个包含23个变量的详细列表，以衡量美国100个主要城市区域（UAs）的城市级城市形态
2. 应用因子分析构建了描述城市形态的5个潜在变量。因子分析还用于定义反映全市交通网络特征的中介变量和交通安全的因变量。
3. 利用结构方程建模（SEM）研究城市级城市形态如何直接和间接地（通过交通网络特征的中介）影响交通安全。
### 结论
* UA的城市交通更安全，不同区域之间的工作-住房平衡更均匀，多中心设计更丰富，低密度蔓延更少。
* 除了就业和城市密度的空间差异对交通安全有显著的直接影响外，提高交通网络连通性、增加公共交通设施和上层交通基础设施的供给，可以通过鼓励使用非驾驶交通方式，间接减少交通死亡人数。据估计，城市密度增加10%，就业空间分布均匀增加10%，可以使致命车祸率平均降低>15%。


