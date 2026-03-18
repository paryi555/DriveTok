<div align="center">
<h1>DriveTok: 3D Driving Scene Tokenization for Unified Multi-View Reconstruction and Understanding</h1>
</div>

### [Paper](https://arxiv.org/abs/2507.02863)  | [Project Page](https://wzzheng.net/) 

>DriveTok: 3D Driving Scene Tokenization for Unified Multi-View Reconstruction and Understanding

>Dong Zhuo, [Wenzhao Zheng](https://wzzheng.net/),  Sicheng Zuo, Siming Yan, Lu Hou, [Jie Zhou](https://scholar.google.com/citations?user=6a79aPwAAAAJ&hl=en&authuser=1), [Jiwen Lu](http://ivg.au.tsinghua.edu.cn/Jiwen_Lu/)

**DriveTok**, an efficient **3D driving scene tokenizer for unified multi-view reconstruction and understanding**, transforms surround-view images into unified scene tokens that jointly encode textural, semantic, and geometric information, enabling **high-quality reconstruction and scene understanding for autonomous driving**.

<img src="./assets/demo.gif" alt="overview" style="width: 100%;" />

## Overview
We propose our DriveTok for multi-view scene reconstruction and understanding. Vision-only surround-view images are processed by a 3D scene encoder to produce unified scene tokens on a BEV grid, independent of camera layout and resolution. A spatial-aware multi-view decoder renders predictions in both image and occ spaces. Through joint multi-task training, our scene tokens encode rich textural, semantic, and geometric information.

<img src="./assets/teaser_01.png" alt="overview" style="width: 100%;" />

### Unified 3D Scene Tokenization for Multi-View Reconstruction and Understanding

<img src="./assets/overview_01.png" alt="overview" style="width: 100%;" />

## Installation

1. Clone DriveTok
```bash
git clone https://github.com/paryi555/DriveTok.git
cd DriveTok
``` 
2. Create conda environment
```bash
conda create -n drivetok python=3.11 cmake=3.14.0
conda activate drivetok 
```

3. Install requirements
```bash
# We use CUDA 12.1 and PyTorch 2.1.0 for our development
pip install -r requirements.txt
pip install mmcv==2.1.0 -f https://download.openmmlab.com/mmcv/dist/cu121/torch2.1.0/index.html
```

### Download Checkpoints
Please download the checkpoint of our DriveTok from [HERE](https://cloud.tsinghua.edu.cn/f/dbb864bbf9ac4c34bfaa/).

## Data Preparation
1. Download nuScenes V1.0 full dataset data [HERE](https://www.nuscenes.org/download).
2. Download the occupancy annotations from SurroundOcc [HERE](https://github.com/weiyithu/SurroundOcc) and unzip it.
3. Download pkl files [HERE](https://cloud.tsinghua.edu.cn/d/095a624d621b4aa98cf9/).
4. Follow instructions [HERE](./scripts/README.md) to prepare the depth and semantic annotations.
5. Please download the DINOv3 pretrained weights from [HERE](https://github.com/facebookresearch/dinov3).

## Folder Structure
The overall folder structure should be organized as follow：
```
DriveTok
├── config/
|   ├── eval_nusc_drivetok.py
|   └── nusc_drivetok.py
├── data/
│   ├── nuscenes/
|   |   ├── ...
|   |   ├── lidarseg
|   |   ├── maps
|   |   ├── samples
|   |   |   ├── CAM_BACK
|   |   |   ├── ...
|   |   |   ├── DEPTH_BACK
|   |   |   ├── ...
|   |   |   ├── SEM_BACK
|   |   |   ├── ...
|   |   ├── sweeps
|   |   ├── v1.0-trainval
|   |   ├── ...
|   |   ├── nuscenes_temporal_infos_train.pkl
|   |   └── nuscenes_temporal_infos_val.pkl
│   ├── surroundocc/
│   │   └── nuscenes_occ
|   |       └── samples
├── dataset/
|   ├── dataset_nusc.py
|   ├── ...
├── loss/
├── model/
├── pretrain/
|    ├── dinov3_vitb16_pretrain_lvd1689m-73cec8be.pth
├── ...   
├── train.py
└── vis_recon.py
```

## Training
We provide the following commands for training.

```bash
OMP_NUM_THREADS=8 torchrun --nproc_per_node=8 --master_port=29622 train.py --py-config config/nusc_drivetok.py --work-dir ./work_dir/drivetok
```

## Visualize
We also provide the following commands for visualization, which require only image data without any additional annotations.
```bash
python vis_recon.py --py-config config/eval_nusc_drivetok.py --checkpoint path/to/checkpoint.pth --work-dir vis_results/ --num-samples 5
```

## Acknowledgements
Our code is based on the following brilliant repositories:

[DINOv3](https://github.com/facebookresearch/dinov3)
[MoGe-2](https://github.com/microsoft/MoGe)

Many thanks to these authors!

## Citation

If you find this project helpful, please consider citing the following paper:
```
@article{streamVGGT,
      title={Streaming 4D Visual Geometry Transformer}, 
      author={Dong Zhuo and Wenzhao Zheng and Jiahe Guo and Yuqi Wu and Jie Zhou and Jiwen Lu},
      journal={arXiv preprint arXiv:2507.},
      year={2025}
}
```


