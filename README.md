# 米酒科技 BCIkit 开发板技术文档

## 1. 简介（Overview）

**BCIkit** 是米酒科技推出的一款专为脑机接口① （Brain-Computer Interface, BCI）研究与开发打造的高性价比开发板。它集成了神经信号采集、实时信号处理、无线传输和多种编程语言控制能力，适合教育科研机构、神经工程团队以及创新创业者进行脑电采集、脑控实验及智能人机互动的快速开发。

**核心特性：**

- 集成多通道 EEG 信号采集模块
- 支持WiFi/USB串口 数据传输
- 支持脑波特征可视化
- 可使用ArduinoIDE 二次开发

## 2. 硬件规格（Hardware Specifications）

| 模块         | 参数                                        |
| ------------ | ------------------------------------------- |
| 主控芯片     | ESP32（双核 240MHz，内置 WiFi & Bluetooth） |
| EEG 采集芯片 | ADS1299（8通道，24位 ADC）                  |
| 电源输入     | ph2.0 5V 锂电池 / USB 5V                    |
| 存储         | 8MB PSRAM，4MB Flash                        |
| 通信接口     | WIFI / micro-USB                            |
| 模拟通道数   | 最多支持 8 通道 EEG 输入                    |
| 尺寸         | 50mm x 50mm x 31mm                          |
| 板载功能     | 电池管理、开关按钮、SD卡槽                  |

## 3. 原理图与结构设计

![48ddfd789ad6065069ca310f81addbcc](img\48ddfd789ad6065069ca310f81addbcc.jpg)

![ea7a037fbef0d0b832697b170c196783](img\ea7a037fbef0d0b832697b170c196783.jpg)

![ef12a32aa826c1bf998231f0c6d1883d](img\ef12a32aa826c1bf998231f0c6d1883d.png)

![4a4402503b6377092d84536765984aa3](img\4a4402503b6377092d84536765984aa3.png)

## 4. 软件支持（Software Support）

- 提供软件资源：
  - OpenBCI GUI
  - Python 上位机采集工具
  - Brainflow（脑电信号处理库）

## 5. 开发环境配置（Development Setup）

![img](https://i-blog.csdnimg.cn/direct/2d8b6c8ef12f442995365cddf62e2417.jpeg)

电极与开发板连接，接在最下面一排的位置，最左右两边是耳夹电极（参考电极），从左到右1-8通道

### 5.1 可视化数据

1. 下载OpenBCI GUI
2. 打开电脑的WLAN，选择OpenBCI WiFi进行连接（这里相当于esp32启动了一个网络）![img](https://i-blog.csdnimg.cn/direct/80c8e31cf2a344b99767f09d0064554b.png)
3. 启动OpenBCI GUI，选择设备类型为Cyton，选择WIFI，static IP，250Hz采样率![img](https://i-blog.csdnimg.cn/direct/8c1cadf5036243529aeddc4ce7ecfb25.png)
4. 点击start session开启采集，再点击绿色按钮startdata stream显示数据

### 5.2 Python获取数据

1. 安装brainflow库

   BrainFlow 是一个用于获取、解析和分析来自生物传感器的 EEG、EMG、ECG 和其他类型数据的库（官网：[BrainFlow](https://brainflow.org/)）。其主要特点为：支持设备种类多、支持9种编程语言、包含信号处理功能

   通过pip安装

   `pip install brainflow`

2. 运行代码

