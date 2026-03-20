<div align="center">
<h1>DriveTok: 3D Driving Scene Tokenization for Unified Multi-View Reconstruction and Understanding</h1>
</div>

### [Paper](https://arxiv.org/abs/2603.19219)  | [Project Page](https://paryi555.github.io/DriveTok/) 

>DriveTok: 3D Driving Scene Tokenization for Unified Multi-View Reconstruction and Understanding

>Dong Zhuo<sup>\*</sup>, [Wenzhao Zheng](https://wzzheng.net/)<sup>*</sup>$\dagger$,  Sicheng Zuo, Siming Yan, Lu Hou, [Jie Zhou](https://scholar.google.com/citations?user=6a79aPwAAAAJ&hl=en&authuser=1), [Jiwen Lu](http://ivg.au.tsinghua.edu.cn/Jiwen_Lu/)

<sup>*</sup> Equal contribution. $\dagger$ Project leader.

**DriveTok**, an efficient **3D driving scene tokenizer for unified multi-view reconstruction and understanding**, transforms surround-view images into unified scene tokens that jointly encode textural, semantic, and geometric information, enabling **high-quality reconstruction and scene understanding for autonomous driving**.

<img src="./assets/demo.gif" alt="overview" style="width: 100%;" />

## Overview
We propose our DriveTok for multi-view scene reconstruction and understanding. Vision-only surround-view images are processed by a 3D scene encoder to produce unified scene tokens on a BEV grid, independent of camera layout and resolution. A spatial-aware multi-view decoder renders predictions in both image and occ spaces. Through joint multi-task training, our scene tokens encode rich textural, semantic, and geometric information.

<img src="./assets/teaser_01.png" alt="overview" style="width: 100%;" />

### Unified 3D Scene Tokenization for Multi-View Reconstruction and Understanding

<img src="./assets/overview_01.png" alt="overview" style="width: 100%;" />

## Citation

If you find this project helpful, please consider citing the following paper:
```
@article{drivetok,
      title={DriveTok: 3D Driving Scene Tokenization for Unified Multi-View Reconstruction and Understanding}, 
      author={Dong Zhuo and Wenzhao Zheng and Sicheng Zuo and Siming Yan and Lu Hou and Jie Zhou and Jiwen Lu},
      journal={arXiv preprint arXiv:2603.19219},
      year={2026}
}
```


