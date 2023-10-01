# MAM-SORT
基于监控视频的车辆跟踪<br>
方法：基于检测的跟踪<br>
1.车辆检测使用YOLOv7；<br>
2.重识别网络使用CA-OSNet；<br>
3.关联匹配算法使用运动特征优为主，外观特征为辅的关联匹配算法（MAM）。<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/MVI-39311.gif)<br>
# 数据集
## 车辆检测与跟踪数据集
车辆检测与跟踪的数据集使用UA-DETRAC数据集，该数据集分为训练集60个视频的82085张图片，测试集40个视频的56167张图片。视频以每秒 25 帧 (fps) 的速度录制，分辨率为 960×540 像素。车辆种类分为轿车、公共汽车、面包车和其他。<br>
UA-DETRAC数据集虽然包含了晴天、小雨、夜晚场景的数据，但缺乏大雾、大雨等恶劣天气场景数据。为了YOLOv7能更好的应对恶劣天气场景下车辆的检测，提高其在现实场景的交通视频图像有更好的泛化能力。在训练集和测试集中都分别取1/10的照片进行大雾天和大雨天的数据增强。增强前和增强后的效果如图所示。
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/rain.jpg)<br>
