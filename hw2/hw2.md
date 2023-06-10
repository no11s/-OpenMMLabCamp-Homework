# 第二次作业：基于 ResNet50 的水果分类

## 划分训练集和验证集

```python
import random
import os

labels = os.listdir('~/data/fruit30/train')

for label in labels:
    path_train = os.path.join('~/data/fruit30/train', label)
    path_val = os.path.join('~/data/fruit30/val', label)
    imgs = os.listdir(path_train)
    print(label, len(imgs))
    for img in imgs:
        if random.random() < 0.7:
            path = os.path.join(path_val, img)
        else:
            path = os.path.join(path_train, img)
        os.remove(path)
```

## 训练&测试

```bash
# 训练模型
CUDA_VISIBLE_DEVICES=2 mim train mmpretrain configs/resnet50_8xb32_in1k.py --work-dir=./work_dirs/resnet50

# 测试模型
CUDA_VISIBLE_DEVICES=2 mim test mmpretrain configs/resnet50_8xb32_in1k.py --checkpoint work_dirs/resnet50/epoch_5.pth --work-dir=./work_dirs/resnet50

# 测试结果
# accuracy/top1: 77.2255  accuracy/top5: 96.8843  data_time: 0.0067  time: 0.0779
```

## 推理

```python
from mmpretrain import ImageClassificationInferencer

inferencer = ImageClassificationInferencer('configs/resnet50_8xb32_in1k.py', pretrained='work_dirs/resnet50/epoch_5.pth')
print(inferencer('banana.jpg', show_dir='visualize'))

# 推理结果
# [{'pred_scores': array([4.9118896e-08, 1.8373109e-14, 3.6641939e-11, 1.3444221e-12,
#        3.7344957e-08, 6.9883863e-11, 9.4633589e-13, 6.4355138e-10,
#        5.8548630e-07, 2.7704485e-09, 5.3786660e-09, 1.0445367e-10,
#        4.5692719e-10, 2.0973236e-13, 8.1774892e-10, 1.9634779e-13,
#        5.6124509e-09, 4.1148296e-12, 8.6040133e-15, 3.0025816e-13,
#        9.9416765e-14, 5.0735414e-13, 2.1784198e-12, 6.5851435e-12,
#        2.5775779e-13, 3.2304461e-11, 8.9568235e-13, 1.6037862e-12,
#        9.9999940e-01, 3.7036544e-11], dtype=float32), 'pred_label': 28, 'pred_score': 0.9999994039535522, 'pred_class': '香蕉'}]
```
