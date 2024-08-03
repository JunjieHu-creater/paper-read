# 英文论文阅读笔记记录


论文研究笔记

## 目录

1. [A unified dataset for the city-scale traffic assignment model](#A-unified-dataset-for-the-city-scale-traffic-assignment-model)
2. [City-scale Vehicle Trajectory Data from Traffic Camera Videos](#City-scale-Vehicle-Trajectory-Data-from-Traffic-Camera-Videos)
3. [结论](#结论)

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
