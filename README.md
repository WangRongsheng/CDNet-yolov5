# CDNet-yolov5

《CDNet：一个基于YOLOv5的在Jetson Nano上实时、鲁棒的斑马线检测网络》论文的原生（ultralytics）yolov5训练、推理仓库，CDNet (Crosswalk Detection Network) 是车载摄像头视野下检测斑马线（人行横道）和分析车辆过线行为的具体实现。

- 原始CDNet论文Paper：[https://rdcu.be/cHuc8](https://rdcu.be/cHuc8)
- 原始CDNet论文Code：[https://github.com/zhangzhengde0225/CDNet](https://github.com/zhangzhengde0225/CDNet)
- 原始CDNet演示Video：[https://www.bilibili.com/video/BV1qf4y1B7BA](https://www.bilibili.com/video/BV1qf4y1B7BA)
- 原始CDNet中文文档：[https://github.com/zhangzhengde0225/CDNet/blob/master/docs/README_zh_cn.md](https://github.com/zhangzhengde0225/CDNet/blob/master/docs/README_zh_cn.md)

# 版本Version

[当前使用的Yolov5版本：V6.1](https://github.com/ultralytics/yolov5/tree/v6.1)


# 数据集Datasets

- 训练集及验证集：3880
- 测试集：1770
- 类别：crosswalk, guide_arrows

[more](https://github.com/zhangzhengde0225/CDNet/blob/master/docs/DATASETS.md)


# 安装Installation

Clone repo and install requirements.txt in a Python>=3.7.0 environment, including PyTorch>=1.7.
```python
git clone https://github.com/ultralytics/yolov5  # clone
cd yolov5
pip install -r requirements.txt  # install
```

# 训练Train

```python
python train.py --data datasets/data.yaml --cfg models/yolov5n.yaml --weights weights/yolov5n.pt --batch-size 128 --img 640 --epochs 100
                                                       yolov5s                        yolov5s.pt              64                     150
                                                       yolov5m                        yolov5m.pt              40                     300
                                                       yolov5l                        yolov5l.pt              24
                                                       yolov5x                        yolov5x.pt              16
```

# 推理Inference

```python
# 【x】是第几次训练的权重
python detect.py --data dataset/data.yaml --weights runs/train/exp【x】/weights/best.pt --device 0 --source 0  # 摄像头
                                                                                                        img.jpg  # 图片
                                                                                                        vid.mp4  # 视频
                                                                                                        path/  # directory
                                                                                                        path/*.jpg  # glob
                                                                                                        'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                                                                                                        'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```
