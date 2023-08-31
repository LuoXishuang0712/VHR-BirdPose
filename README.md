# VHR-BirdPose

About this repo: [paper](https://doi.org/10.3390/electronics12173643) | [HRNet_readme](./README_HRNet.md)

What we use: [HRNet](https://github.com/leoxiaobin/deep-high-resolution-net.pytorch) | [Animal Kingdom](https://github.com/sutdcv/Animal-Kingdom) | [ViTPose](https://github.com/ViTAE-Transformer/ViTPose) | [Timm](https://github.com/huggingface/pytorch-image-models)

## Environment

This code has been validated on:
* NVIDIA Geforce RTX 3090Ti (CUDA11.0, PyTorch1.7.0+cu110, Ubuntu20.04)
* NVIDIA Tesla V100-PCIE 32GB (CUDA10.2, PyTorch1.10.0, Ubuntu18.04)

## Installation

1. Require a copy of Animal Kingdom and prepare the data alone with the code according to [the readme of pose estimation task](https://github.com/sutdcv/Animal-Kingdom/blob/master/Animal_Kingdom/pose_estimation/README_pose_estimation.md), you can stop after finish the Step3 of the section "Instructions to run Pose Estimation models".
1. Clone this project and execute `cp $OUR_REPO/lib/models/pose_vhr.py $OUR_REPO/lib/models/cross_attn.py $OUR_REPO/lib/models/vit.py $OUR_REPO/lib/models/base_backbone.py $AK_PE/code/hrnet/lib/models/`, `cp -r $OUR_REPO/experiments/mpii/vhrbirdpose $AK_PE/code/hrnet/experiments/mpii/`, and `cp -f $OUR_REPO/lib/utils/utils.py $AK_PE/code/hrnet/lib/utils/`, you may need specified the paths to out reporistory and pose estimation folder of Animal Kingdom by executing `export OUT_REPO={PATH TO THIS PROJECT}` and `export AK_PE={PATH TO POSE ESTIMATION}`.
    > For Windows, just simply copy the lib/models and experiments/mpii/vhr to the appearently same place in the %ANIMAL_KINGDOM_ROOT%/pose_estimation/code/hrnet by using GUI or use PowerShell/Cygwin or others posix compact shell to execute the shell code above.
1. Append `import models.pose_vhr` to the end of the file `$AK_PE%/lib/models/__init__.py`.
1. Install [Timm](https://github.com/huggingface/pytorch-image-models)==0.4.9 and einops by `python -m pip install timm==0.4.9 einops`

## Testing

Change current diectory to `$AK_PE$/code/hrnet`, run `python tools/train.py --cfg experiments/mpii/vhrbirdpose/w32_256x256_adam_lr1e-3_ak_vhr_b.yaml`.

## Pretrained

The pretrained weight can be download from [Google Drive]() | [Baidu Netdisk]()

## Citing

```
@Article{
    he2023vhrbirdpose,
    AUTHOR = {He, Runang and Wang, Xiaomin and Chen, Huazhen and Liu, Chang},
    TITLE = {VHR-BirdPose: Vision Transformer-Based HRNet for Bird Pose Estimation with Attention Mechanism},
    JOURNAL = {Electronics},
    VOLUME = {12},
    YEAR = {2023},
    NUMBER = {17},
    ARTICLE-NUMBER = {3643},
}
```
