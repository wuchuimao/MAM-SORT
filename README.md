# MAM-SORT
基于监控视频的车辆跟踪<br>
方法：基于检测的跟踪<br>
1.车辆检测使用YOLOv7；<br>
2.重识别网络使用CA-OSNet；<br>
3.关联匹配算法使用运动特征优为主，外观特征为辅的关联匹配算法（MAM）。<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/MVI-39311.gif)<br>
# 数据集
======
## 车辆检测与跟踪数据集
-----
车辆检测与跟踪的数据集使用UA-DETRAC数据集，该数据集分为训练集60个视频的82085张图片，测试集40个视频的56167张图片。视频以每秒 25 帧 (fps) 的速度录制，分辨率为 960×540 像素。车辆种类分为轿车、公共汽车、面包车和其他。<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/UA-DETRAC.jpg)<br>
UA-DETRAC数据集虽然包含了晴天、小雨、夜晚场景的数据，但缺乏大雾、大雨等恶劣天气场景数据。为了YOLOv7能更好的应对恶劣天气场景下车辆的检测，提高其在现实场景的交通视频图像有更好的泛化能力。在训练集和测试集中都分别取1/10的照片进行大雾天和大雨天的数据增强。增强前和增强后的效果如图所示。<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/rain.jpg)<br>
UA-DETRAC数据集不仅标注了车辆的位置信息，还标注了道路中的忽略区域。由于忽略区域中也存在车辆但是却没有对应的车辆标注信息，这会给车辆检测的训练造成影响，最终导致检测网络的准确率减低，所以本文将对忽视区域的图像进行黑化处理，降低该部分图像对检测网络的影响，黑化处理后的图像如下图所示。对于忽视区域中有少量车辆给了标注信息，在黑化过程中会将该标注信息从对应的标签文件中删。<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/ignore.jpg)<br>
## 车辆重识别数据集
-------
车辆重识别数据集是使用VeRi776。与车辆检测网络一样，为了提升整个跟踪算法在大雪、大雾等恶劣交通视频场景下的跟踪泛化性，本文也会对训练CA-OSNet的数据集进行大雨和大雾的数据增强。除此之外，为了减少跟踪过程中车辆的尺度变化和遮挡问题对外观特征辨识度的影响，在训练CA-OSNet时还会对VeRi776数据集进行随机翻转，随机裁剪，随机擦除等数据增强。
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/flip.jpg)<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/crop.jpg)<br>
![](https://github.com/wuchuimao/MAM-SORT/raw/main/images/patch.jpg)<br>
