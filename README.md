# Deformable Mixer Transformer with Gating for Multi-Task Learning of Dense Prediction

This repo is the official implementation of ["DeMTG"](https://arxiv.org/abs/2301.03461) as well as the follow-ups. It currently includes code and models for the following tasks:



## Updates

***07/07/2023***
We release the models and code of DeMTG.


## Introduction

**DeMTG** (the name `DeMTG` stands for **De**formable **M**ixer **T**ransformer with **G**ating for Multi-Task Learning of Dense
Prediction) is initially described in [arxiv](https://arxiv.org/pdf/2301.03461.pdf), which is an extension to our previous AAAI 2023.
We introduce deformable mixer Transformer with gating (DeMTG), a simple and effective encoder-decoder architecture up-to-date that incorporates the convolution and attention mechanism in a unified network for MTL.
DeMTG achieves strong performance on PASCAL-Context (`75.33 mIoU semantic segmentation` and `63.11 mIoU Human Segmentation` on test) and
 and NYUD-v2 semantic segmentation (`54.34 mIoU` on test), surpassing previous models by a large margin.

![DeMTG](figures/overflow.png)

## Main Results on ImageNet with Pretrained Models

**DeMTG on NYUD-v2 dataset**

| model|backbone|#params| FLOPs | SemSeg| Depth | Noemal|Boundary| model checkpopint | log |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |:---: |:---: |
| DeMTG | Swin-T | 32.07M | 100.70G | 46.36 | 0.5871 | 20.60| 76.9 | [Google Drive](https://drive.google.com/file/d/1IfQRVyvaVkEfybzh4QAz9Vq_0U38Hngq/view?usp=share_link) | [log](https://drive.google.com/file/d/1eAtQVJLcvIOMwAfKyl2NmYfe3hPne_WK/view?usp=share_link)  |
| DeMTG(xd=2) | Swin-T | 36.6M| - | 47.45 | 0.5563| 19.90| 77.0 | [Google Drive](https://drive.google.com/file/d/1Rz4R9vu8bGtskpJDlVfgexYZoHtz8j8k/view?usp=share_link) | [log](https://drive.google.com/file/d/1TPo4pMjbhPAn3gxKOt4P7hVSPJe1Lpsn/view?usp=share_link)  |
| DeMTG | Swin-S | 53.03M | 121.05G | 51.50 | 0.5474 | 20.02 | 78.1 | [Google Drive](https://drive.google.com/drive/folders/1jINF9WOyILqrPcsprWbM5VSCEWozsc1c) | [log](https://drive.google.com/drive/folders/1jINF9WOyILqrPcsprWbM5VSCEWozsc1c)|
| DeMTG | Swin-B | 90.9M | 153.65G | 54.34 | 0.5209 | 19.21 | 78.5 | [Google Drive]() | [log]() |
| DeMTG | Swin-L | 201.64M | -G | 56.94 | 0.5007 | 19.14 | 78.8 | [Google Drive]() | [log]() |

**DeMTG on PASCAL-Contex dataset**

| model | backbone |  SemSeg | PartSeg | Sal | Normal| Boundary| 
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| DeMTG |HRNet-18| 59.23 | 57.93 | 83.93| 14.02 | 69.80 |
| DeMTG | Swin-T | 69.71 | 57.18 | 82.63| 14.56 | 71.20 |
| DeMTG | Swin-S | 72.01 | 58.96 | 83.20| 14.57 | 72.10 | 
| DeMTG | Swin-B | 75.33 | 63.11 | 83.42| 14.54 | 73.20 |



## Citing DeMTG multi-task method

```
@inproceedings{xyy2023DeMT,
  title={DeMT: Deformable Mixer Transformer for Multi-Task Learning of Dense Prediction},
  author={Xu, Yangyang and Yang, Yibo and Zhang, Lefei },
  booktitle={Proceedings of the The Thirty-Seventh Conference on Artificial Intelligence (AAAI)},
  year={2023}
}

@inproceedings{xyy2023DeMTG,
  title={Deformable Mixer Transformer with Gating for Multi-Task Learning of Dense Prediction},
  author={Xu, Yangyang and Yang, Yibo and Zhang, Lefei },
  booktitle={arxiv},
  year={2023}
}
```


## Getting Started
**Install and Data Prepare**

```
Please reference to [DeMT](https://github.com/yangyangxu0/DeMT)
```



**Train**

To train DeMTG model:
```
python ./src/main.py --cfg ./config/t-nyud/swin/siwn_t_DeMTG.yaml --datamodule.data_dir $DATA_DIR --trainer.gpus 8
```

**Evaluation**

- When the training is finished, the boundary predictions are saved in the following directory: ./logger/NYUD_xxx/version_x/edge_preds/ .
- The evaluation of boundary detection use the MATLAB-based [SEISM](https://github.com/jponttuset/seism) repository to obtain the optimal-dataset-scale-F-measure (odsF) scores.


## Acknowledgement
This repository is based [ATRC](https://github.com/brdav/atrc). Thanks to [ATRC](https://github.com/brdav/atrc)!

