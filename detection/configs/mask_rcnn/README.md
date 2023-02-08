# Mask R-CNN

> [Mask R-CNN](https://arxiv.org/abs/1703.06870)

<!-- [ALGORITHM] -->

## Introduction

Mask R-CNN is a conceptually simple, flexible, and general framework for object instance segmentation. It efficiently detects objects in an image while simultaneously generating a high-quality segmentation mask for each instance. And it extends Faster R-CNN by adding a branch for predicting an object mask in parallel with the existing branch for bounding box recognition. Mask R-CNN is simple to train and adds only a small overhead to Faster R-CNN, running at 5 fps. Moreover, Mask R-CNN is easy to generalize to other tasks, e.g., allowing us to estimate human poses in the same framework. Without bells and whistles, Mask R-CNN outperforms all existing, single-model entries on every task, including the COCO 2016 challenge winners. 

<div align=center>
<img src="https://user-images.githubusercontent.com/40661020/143967081-c2552bed-9af2-46c4-ae44-5b3b74e5679f.png"/>
</div>

## Results and Models

| Backbone      | Pre-train                                                                                                                                                          | Lr schd | box AP      | mask AP     | #Param | Config                                                         | Download                                                                                                                 |
|:-------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------:|:-----------:|:-----------:|:------:|:--------------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
| ViT-T         | [DeiT-T](https://dl.fbaipublicfiles.com/deit/deit_tiny_patch16_224-a1311bcf.pth)                                                                                   | 3x+MS   | 40.2        | 37.0        | 26M    | [config](./mask_rcnn_deit_tiny_fpn_3x_coco.py)                 | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_deit_tiny_fpn_3x_coco.pth.tar)          |
| ViT-Adapter-T | [DeiT-T](https://dl.fbaipublicfiles.com/deit/deit_tiny_patch16_224-a1311bcf.pth)                                                                                   | 3x+MS   | 46.0 (+5.8) | 41.0 (+4.0) | 28M    | [config](./mask_rcnn_deit_adapter_tiny_fpn_3x_coco.py)         | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.1.2/mask_rcnn_deit_adapter_tiny_fpn_3x_coco.pth.tar)  |
| ViT-S         | [DeiT-S](https://dl.fbaipublicfiles.com/deit/deit_small_patch16_224-cd65a155.pth)                                                                                  | 3x+MS   | 44.0        | 39.9        | 42M    | [config](./mask_rcnn_deit_small_fpn_3x_coco.py)                | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_deit_small_fpn_3x_coco.pth.tar)         |
| ViT-Adapter-S | [DeiT-S](https://dl.fbaipublicfiles.com/deit/deit_small_patch16_224-cd65a155.pth)                                                                                  | 3x+MS   | 48.2 (+4.2) | 42.8 (+2.9) | 48M    | [config](./mask_rcnn_deit_adapter_small_fpn_3x_coco.py)        | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.1.2/mask_rcnn_deit_adapter_small_fpn_3x_coco.pth.tar) |
| ViT-B         | [DeiT-B](https://dl.fbaipublicfiles.com/deit/deit_base_patch16_224-b5f2ef4d.pth)                                                                                   | 3x+MS   | 45.8        | 41.3        | 114M   | [config](./mask_rcnn_deit_base_fpn_3x_coco.py)                 | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_deit_base_fpn_3x_coco.pth.tar)          |
| ViT-Adapter-B | [DeiT-B](https://dl.fbaipublicfiles.com/deit/deit_base_patch16_224-b5f2ef4d.pth)                                                                                   | 3x+MS   | 49.6 (+3.8) | 43.6 (+2.3) | 120M   | [config](./mask_rcnn_deit_adapter_base_fpn_3x_coco.py)         | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.1.6/mask_rcnn_deit_adapter_base_fpn_3x_coco.pth.tar)  |
| ViT-Adapter-B | [Uni-Perceiver-B](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/uni-perceiver-base-L12-H768-224size-torch-pretrained_converted.pth)               | 3x+MS   | 51.2        | 45.3        | 120M   | [config](./mask_rcnn_uniperceiver_adapter_base_fpn_3x_coco.py) | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_uniperceiver_adapter_base_fpn_3x_coco.pth) \| [log](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/20220922_092016.log)                                                                                                                     |
| ViT-L         | [AugReg-L](https://storage.googleapis.com/vit_models/augreg/L_16-i21k-300ep-lr_0.001-aug_medium1-wd_0.1-do_0.1-sd_0.1--imagenet2012-steps_20k-lr_0.01-res_384.npz) | 3x+MS   | 48.3        | 43.3        | 337M   | [config](./mask_rcnn_augreg_large_fpn_3x_coco.py)              | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_augreg_large_fpn_3x_coco.pth.tar)       |
| ViT-Adapter-L | [AugReg-L](https://storage.googleapis.com/vit_models/augreg/L_16-i21k-300ep-lr_0.001-aug_medium1-wd_0.1-do_0.1-sd_0.1--imagenet2012-steps_20k-lr_0.01-res_384.npz) | 3x+MS   | 52.1 (+3.8) | 46.0 (+2.7) | 348M   | [config](./mask_rcnn_augreg_adapter_large_fpn_3x_coco.py)      | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/mask_rcnn_augreg_adapter_large_fpn_3x_coco.pth) \| [log](https://github.com/czczup/ViT-Adapter/releases/download/v0.3.1/20220922_091952.log)                                                                                                                     |

In addition, we found that FPN could be removed when using ViT-Adapter as backbone.

| Backbone      | Pre-train                                                                         | FPN | Lr schd | box AP | mask AP | #Param | Config                                                  | Download                                                                                                                 |
|:-------------:|:---------------------------------------------------------------------------------:|:---:|:-------:|:------:|:-------:|:------:|:-------------------------------------------------------:|:------------------------------------------------------------------------------------------------------------------------:|
| ViT-Adapter-S | [DeiT-S](https://dl.fbaipublicfiles.com/deit/deit_small_patch16_224-cd65a155.pth) | Yes | 3x+MS   | 48.2   | 42.8    | 48M    | [config](./mask_rcnn_deit_adapter_small_fpn_3x_coco.py) | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.1.2/mask_rcnn_deit_adapter_small_fpn_3x_coco.pth.tar) |
| ViT-Adapter-S | [DeiT-S](https://dl.fbaipublicfiles.com/deit/deit_small_patch16_224-cd65a155.pth) | No  | 3x+MS   | 48.2   | 42.7    | 45M    | [config](./mask_rcnn_deit_adapter_small_3x_coco.py)     | [model](https://github.com/czczup/ViT-Adapter/releases/download/v0.1.6/mask_rcnn_deit_adapter_small_3x_coco.pth.tar)     |