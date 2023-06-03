# 第一次作业：基于RTMPose的耳朵穴位关键点检测

## 目标检测模型的测试结果

```bash
# 训练模型
python /home/shiyiming/mm2/mmdetection/tools/train.py \
	/home/shiyiming/projects/mmpose/configs/rtmdet_tiny_ear.py \
	--work-dir /home/shiyiming/projects/mmpose/work_dirs/rtmdet_tiny_ear

# 测试模型
python /home/shiyiming/mm2/mmdetection/tools/test.py \
	/home/shiyiming/projects/mmpose/configs/rtmdet_tiny_ear.py \
	/home/shiyiming/projects/mmpose/work_dirs/rtmdet_tiny_ear/epoch_200.pth \
	--work-dir /home/shiyiming/projects/mmpose/work_dirs/rtmdet_tiny_ear

# 测试结果1
# Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.745
# Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets=100 ] = 0.961
# Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets=100 ] = 0.926
# Average Precision  (AP) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = -1.000
# Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = -1.000
# Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.745
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=  1 ] = 0.771
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 10 ] = 0.786
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets=100 ] = 0.786
# Average Recall     (AR) @[ IoU=0.50:0.95 | area= small | maxDets=100 ] = -1.000
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets=100 ] = -1.000
# Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets=100 ] = 0.786

# 测试结果2
# {
#   "coco/bbox_mAP": 0.745,
#   "coco/bbox_mAP_50": 0.961,
#   "coco/bbox_mAP_75": 0.926,
#   "coco/bbox_mAP_s": -1.0,
#   "coco/bbox_mAP_m": -1.0,
#   "coco/bbox_mAP_l": 0.745,
#   "data_time": 0.3224326263774525,
#   "time": 0.4866764111952348
# }
```

## 关键点检测模型的测试结果

```bash
# 训练模型
python /home/shiyiming/mm2/mmpose/tools/train.py \
	/home/shiyiming/projects/mmpose/configs/rtmpose-s-ear.py \
	--work-dir /home/shiyiming/projects/mmpose/work_dirs/rtmpose-s-ear

# 测试模型
python /home/shiyiming/mm2/mmpose/tools/test.py \
	/home/shiyiming/projects/mmpose/configs/rtmpose-s-ear.py \
	/home/shiyiming/projects/mmpose/work_dirs/rtmpose-s-ear/epoch_300.pth \
	--work-dir /home/shiyiming/projects/mmpose/work_dirs/rtmpose-s-ear

# 测试结果1
# Average Precision  (AP) @[ IoU=0.50:0.95 | area=   all | maxDets= 20 ] =  0.771
# Average Precision  (AP) @[ IoU=0.50      | area=   all | maxDets= 20 ] =  1.000
# Average Precision  (AP) @[ IoU=0.75      | area=   all | maxDets= 20 ] =  0.945
# Average Precision  (AP) @[ IoU=0.50:0.95 | area=medium | maxDets= 20 ] = -1.000
# Average Precision  (AP) @[ IoU=0.50:0.95 | area= large | maxDets= 20 ] =  0.771
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=   all | maxDets= 20 ] =  0.783
# Average Recall     (AR) @[ IoU=0.50      | area=   all | maxDets= 20 ] =  1.000
# Average Recall     (AR) @[ IoU=0.75      | area=   all | maxDets= 20 ] =  0.952
# Average Recall     (AR) @[ IoU=0.50:0.95 | area=medium | maxDets= 20 ] = -1.000
# Average Recall     (AR) @[ IoU=0.50:0.95 | area= large | maxDets= 20 ] =  0.783

# 测试结果2
# {
#   "coco/AP": 0.770518051286034,
#   "coco/AP .5": 1.0,
#   "coco/AP .75": 0.94518232311036,
#   "coco/AP (M)": -1.0,
#   "coco/AP (L)": 0.770518051286034,
#   "coco/AR": 0.7833333333333334,
#   "coco/AR .5": 1.0,
#   "coco/AR .75": 0.9523809523809523,
#   "coco/AR (M)": -1.0,
#   "coco/AR (L)": 0.7833333333333334,
#   "PCK": 0.9739229024943309,
#   "AUC": 0.12448979591836734,
#   "NME": 0.04024207186536724,
#   "data_time": 1.1233302752176921,
#   "time": 1.3870359659194946
# }
```
