# ShapeICP: Iterative Category-level Object Pose and Shape Estimation from Depth

## Overview
This repository contains the Python implementation of "ShapeICP: Iterative Category-level Object Pose and Shape Estimation from Depth"
([arXiv](https://arxiv.org/abs/2408.13147)).
The approach estimates the pose and shape of an object from a known category given a single depth image. The entire pipeline can be run without learning or with an optional shape classification module. The approach works especially well when the pose and shape of the object can be determined without fine geometric details. For example, boxes, bowls, cans and bottles.

## Dependencies
* Python 3.7.9
* conda env create -f env.yml
* conda activate shapeicp


## Preparation
- [NOCS](https://github.com/hughw19/NOCS_CVPR2019)
  - The evaluation is based on the NOCS dataset. Only REAL data are used.
  - To ensure our code runs, please have the NOCS dataset in the following structure:
    ```
      NOCS
      ├── Real
      │   ├── train
      │   └── test
      ├── gts
      │   └── real_test
      └── obj_models
          ├── train
          ├── val
          ├── real_train
          └── real_test
    ```
- [ShapeNet](https://huggingface.co/ShapeNet)
  - We provide intermediate results so ShapeNet is not directly needed for NOCS evaluation.
  - Good to have if you need to build your own active shape model.
- Download the intermediate results for the [PCA of the active shape model](https://dummy), the optional [shape classification](https://dummy), and [Mask R-CNN results](https://dummy) from [Shape Prior](https://github.com/mtiandev/object-deformnet). Arrange them in the following structure:
  ```
  .
  ├── nocs_shape_classification
  │   ├── 20231026_shapeClassificationLumped_normalRealOnReal
  │   └── classification_normal
  ├── nocs_third_party_results
  │   └── shapeprior_deformnet
  │       └── mrcnn_results
  │           └── real_test
  └── pca
      └── shapenetv2
  ```

## Evaluation
Please run `ShapeICP.ipynb` and follow the instructions inside. The pre-set settings in the notebook should reproduce the paper results. We have cleaned up the code from our original research code that has many stale configurations. If you find any left, please disregard them. If you find any issues, it could be very likely from this clean-up process. However, we do not expect any. We also do not guarantee the comments in the code are up-to-date or correct. We leave them for your reference.

Note that a bug in the evaluation code of NOCS is pointed out by [SAR-Net](https://github.com/hetolin/SAR-Net). We show results from both the original code and the debugged code.

## Citation
If you find our work helpful, please consider citing:
```
@article{zhang2025shapeicp,
  title={ShapeICP: Iterative category-level object pose and shape estimation from depth},
  author={Zhang, Yihao and Sawhney, Harpreet S and Leonard, John J},
  journal={IEEE Robotics and Automation Letters},
  year={2025},
  publisher={IEEE}
}
```

## Acknowledgment
The evaluation protocol is from [NOCS](https://github.com/hughw19/NOCS_CVPR2019) and [Shape Prior](https://github.com/mtiandev/object-deformnet).