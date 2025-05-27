# 🕰️ TimeBase: The Power of Minimalism in Efficient Long-Term Time Series Forecasting

Welcome to the official repository for **TimeBase**, a **Spotlight paper** at **ICML 2025**. 
This repository provides all necessary code, datasets, and scripts to reproduce our results in a fully transparent and reproducible manner.

------

## 📦 Overview

 This repository includes:

- 🔧 Scripts for training and evaluation
- 📊 Preprocessed datasets and download links
- 📉 Plug-and-play complexity reducer for PatchTST
- 📝 Detailed instructions for reproducibility

------

## 📁 Dataset Preparation

🔹 **Benchmark Datasets (17 total)**

We support the following public datasets:

```
ETTh1, ETTh2, ETTm1, ETTm2, Weather, Electricity, Traffic, Solar-Energy, Wind,
Exchange-Rate, METR-LA, ZafNoo, CzeLan, AQShunyi, AQWan, PM2.5, Temp
```

📥 Download from [Google Drive](https://drive.google.com/file/d/1ypgCc6iQ2Z8IB_9CY3If_KMRNQKBsI3J/view?usp=sharing), then unzip to the `./dataset/` directory.

🔹 **Large-Scale Datasets**

TimeBase is also evaluated on four large-scale real-world datasets:

- **CA** (4.52B records)
- **GLA** (2.02B)
- **GBA** (1.24B)
- **SD** (0.38B)

For these, please refer to the official preprocessing instructions from [LargeST GitHub](https://github.com/liuxu77/LargeST).

------

## ⚙️ Implementation Details

- **Regularization coefficient**:
   We perform grid search over
   `λ_orth ∈ [0.00, 0.04, 0.08, 0.12, 0.16, 0.20]`.
- **Learning rate**:
   Searched in range `[0.01, 0.5]`.
- **Period settings**:
   For datasets with a period length shorter than input length (e.g., ETTh1, ETTh2, Traffic, Electricity),
   we use `P = 24` and `#Basis R = 6`.
- **Loss function**:
   Mean Squared Error (MSE)

------

## 🔌 Plug-and-Play Reducer for PatchTST

TimeBase can be used as a **plug-in complexity reducer** for patch-based models like PatchTST.

```bash
cd plug-and-play_for_patchtst
sh ./run_all.sh
```

------

## 🚀 Running TimeBase

To train and evaluate TimeBase on a given dataset:

```bash
sh ./scripts/$DATA_NAME.sh
```

Replace `$DATA_NAME` with one of the dataset names (e.g., ETTh1, Weather, etc.).

------

## 📄 Citation

If you find this project helpful, please cite us:

```bibtex
@inproceedings{huang2025time,
  title     = {TimeBase: The Power of Minimalism in Long-term Time Series Forecasting},
  author    = {Qihe Huang and Zhengyang Zhou and Kuo Yang and Zhongchao Yi and Xu Wang and Yang Wang},
  booktitle = {Proceedings of the Forty-Second International Conference on Machine Learning (ICML)},
  year      = {2025}
}
```



------

## Acknowledgements

We would like to thank the authors of the following open-source projects for their valuable contributions, which provides significant help for our work:

- [**SparseTSF** (ICML 2024)](https://github.com/lss-1138/SparseTSF)
- [**PatchTST** (ICLR 2023)](https://github.com/yuqinie98/PatchTST)
- [**TFB** (VLDB 2024)](https://github.com/decisionintelligence/TFB)
- [**Time-Series-Library** (THUML)](https://github.com/thuml/Time-Series-Library)

We gratefully acknowledge their contributions to the time series forecasting community.
