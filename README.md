# 英文论文阅读笔记记录


论文研究笔记

## 目录

1. [A unified dataset for the city-scale traffic assignment model](#A-unified-dataset-for-the-city-scale-traffic-assignment-model)
2. [使用说明](#使用说明)
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
