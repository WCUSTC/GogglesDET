<div align="center">

# GogglesDet: Goggles Detection with Clustering Transformer and A New Dataset

</div>


Pytorch implementation of the paper "[GogglesDet: Goggles Detection with Clustering Transformer and A New Dataset]()" .

## Introduction
* The first work on goggles detection. 

* It alleviates the generalization problem suffered by general object detection models on goggles detection tasks.
## Installation
The installation is exactly the same as [open-mmlab/mmdetection](https://github.com/open-mmlab/mmdetection)

We just have replaced or added the following files:
```
mmdetection-master
├── mmdet
│   ├── datasets
│   │   ├── __init__.py
│   │   ├── coco_goggle.py
│   ├── models
│   │   ├── dense_heads
│   │   │   ├── __init__.py
│   │   │   ├── deformable_detr_base_head.py
│   │   │   ├── yolox_base_head.py
│   │   ├── roi_heads
│   │   │   ├── bbox_heads
│   │   │   │   ├── __init__.py
│   │   │   │   ├── convfc_bbox_base_head.py
```

## Data preparation

### GogglesDET2023

Download [GogglesDET2023]( ). The link will not be available until after the review phase.


For GogglesDET2023, you should have structure like this:
```
GogglesDET2023
├── train
│   ├── JPEGImages
│   ├── Annotations
├── test
│   ├── JPEGImages
│   ├── Annotations
├── goggles_train.json
├── goggles_test.json

```

## Getting Started

### Training
For training, run
```Shell
python tools/train.py [path_to_your_config] 
```

For example, run
```Shell
python tools/train.py configGoggles/yolox_s_base_loss2_r08_clsconv.py
```

### Validation
For testing, run
```Shell
python tools/test.py [path_to_your_config]  [path_to_your_checkpoint] [path_to_your_checkpoint]  --work-dir  [path_to_your_workdir] --eval bbox
```

For example, run
```Shell
python tools/test.py configGoggles/yolox_s_base_loss2_r08_clsconv.py work_dirs/yolox_s_base_loss2_r08_clsconv/epoch_300.pth  --work-dir work_dirs/yolox_s_base_loss2_r08_clsconv/  --eval bbox
```

## Pretrained Models
We use the pretrained models provided by [open-mmlab/mmdetection](https://github.com/open-mmlab/mmdetection)

| Model           | Download |
|-----------------|----------|
| YOLOX-S         |[download](https://download.openmmlab.com/mmdetection/v2.0/yolox/yolox_s_8x8_300e_coco/yolox_s_8x8_300e_coco_20211121_095711-4592a793.pth)       |
| Faster RCNN     |[download](https://download.openmmlab.com/mmdetection/v2.0/faster_rcnn/faster_rcnn_r50_fpn_2x_coco/faster_rcnn_r50_fpn_2x_coco_bbox_mAP-0.384_20200504_210434-a5d8aa15.pth)    |
| Deformable-DETR |[download](https://download.openmmlab.com/mmdetection/v2.0/deformable_detr/deformable_detr_r50_16x2_50e_coco/deformable_detr_r50_16x2_50e_coco_20210419_220030-a12b9512.pth)            |


## Finetuned Models
We will provide the Finetuned Model Links after the review phase

| Model                 | Download     |
|-----------------------|--------------|
| YOLOX-S               | [download]() |
| YOLOX-S + CTM         |[download]()              |
| Faster RCNN           |[download]()              |
| Faster RCNN + CTM     | [download]()             |
| Deformable-DETR       | [download]()             |
| Deformable-DETR + CTM | [download]()             |


## Results
 All results were evaluated on a single NVIDIA RTX 3080Ti GPU 

|   Method  | AP(IoU=.5)(\%) |   Cr (\%) | FPS   |
|-----|----------------|-----|-------|
|  YOLOX   | 90.1           | 4.69    | 155.8 |
|YOLOX + CTM      | 91.0           | 3.44    | 150.9 |
|Faster RCNN     | 83.9               |5.23     | 35.2  |
|Faster RCNN + CTM     | 85.1               |4.27     | 34.4  |
|Deformable-DETR     | 89.2               | 2.61    | 25.2  |
|Deformable-DETR + CTM     |  91.1              |2.46     | 25.2  |


## Citation

If our paper and code are beneficial to your work, please consider citing:
```





```

## Acknowledgement
<!--ts-->
* [open-mmlab/mmdetection](https://github.com/open-mmlab/mmdetection)
* [pytorch/vision](https://github.com/pytorch/vision)
<!--te-->