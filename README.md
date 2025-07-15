# PUSSM: Point Cloud Upsampling as Statistical Shape Model

This repository provides the official framework implementation for our paper:

**"PUSSM: Point Cloud Upsampling as Statistical Shape Model"**

PUSSM proposes a novel framework for high-fidelity anatomical reconstruction of pelvic structures by integrating medical image segmentation with point cloud upsampling. Instead of relying on landmarks or PCA for classical Statistical Shape Models (SSMs), PUSSM implicitly learns anatomical priors through deep neural networks trained on real medical data.

## 🚀 Project Overview

- **Framework only:** This repository focuses on the pipeline integration and experimental setup of PUSSM.  
- **No model code included:** Due to licensing and organizational policies, we do not release training/inference code for third-party models (e.g., Grad-PU, PUCRN).
- **Pretrained models available:** We provide pretrained weights for Grad-PU and PUCRN for reproducibility.
- **Dataset used:** MedShapePelvic and Pelvic1k are used to train and evaluate upsampling performance. See below for download links.

## 📦 Dataset

You can download the preprocessed pelvic point cloud dataset used in our experiments here:

🔗 [Google Drive - Pelvic Point Cloud Dataset](https://drive.google.com/file/d/1UBheR2SPZ7sXDOUpO2b8WqLYXGWStC_B/view?usp=sharing)

This dataset includes:
- Upsampling train and test samples from MedShapePelvic (based on MedShapeNet)

Besides, test samples for reconstrucion in the 🔗[Pelvic1k](https://github.com/MIRACLE-Center/CTPelvic1K) subdatasets (3, 4, and 6) 

## 📂 Pretrained Models

We release the pretrained weights for two point cloud upsampling models used in our paper:

- **Grad-PU**
- **PUCRN**


## 🧠 Method Summary

The PUSSM framework consists of two main stages:

1. **Medical Image Segmentation**  
   Using SAM-Med3D, we obtain voxel-based segmentation masks from pelvic CT images, which are then converted into sparse point clouds.

2. **Point Cloud Upsampling**  
   Sparse point clouds are input into a pretrained upsampling model (e.g., PUCRN), which reconstructs dense, anatomically plausible shapes without explicit shape modeling (no PCA or landmarks).

This results in a learned, implicit statistical shape model embedded in the network parameters.

## 📊 Results Overview

Our experiments demonstrate:
- Improved Chamfer Distance (CD), Hausdorff Distance (HD), and Point-to-Surface Distance (P2F)
- Enhanced mesh quality (ALR, Manifoldness Rate, CC Discrepancy)
- Superior reconstruction accuracy (F1 score, Normal Consistency, etc.) compared to raw segmentation or baseline upsampling methods

Refer to the paper for detailed results and visual comparisons.

## 🙏 Acknowledgements

We sincerely thank the following open-source projects and datasets that made this work possible:

- [CTPelvic1K](https://github.com/MIRACLE-Center/CTPelvic1K): The pelvic CT segmentation dataset used for evaluation.
- [SAM-Med3D](https://github.com/uni-medical/SAM-Med3D): A general-purpose medical image segmentation model.
- [PUCRN](https://github.com/hikvision-research/3DVision): A cascaded refinement network for point cloud upsampling.
- [Grad-PU](https://github.com/yunhe20/Grad-PU): A gradient-descent-based arbitrary-scale point cloud upsampling method.
- [MedShapeNet](https://github.com/Jianningli/medshapenet-feedback): A large-scale 3D anatomical mesh dataset used as shape prior.

We are grateful for their contributions to the research community.

## 📄 Citation

If you find this work useful, please consider citing:

```bibtex
@article{zhang2025pussm,
  title={PUSSM: Point Cloud Upsampling as Implicit Statistical Shape Model},
  author={Zhang, Tongxu and Wang, Bei},
  journal={arXiv preprint arXiv:2501.16716},
  year={2025}
}
