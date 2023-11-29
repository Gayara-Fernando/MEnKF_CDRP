# MEnKF_CDRP

## Introduction

This GitHub repository consists of codes used in "A Multi-arm ANN to combine information from multiple deep learners and attach uncertainty" by authors Ved Piyush, Gayara Demini Fernando, Ruibo Zhang, M. Ryan Weil, Ranadip Pal, and Souparno Ghosh. 

## Data and Run help

## 1. MEnKF

The original codes for the MEnKF come from the repository https://github.com/Ved-Piyush/MEnKF_Ensembler_DualGCN_DeepCDR. 

### Training DeepCDR and DualGCN

To train the DeepCDR model, use the script [DeepCDR_Train](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DeepCDR_Train.ipynb), and to train the DualGCN model, use the script [DualGCN_train](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DualGCN_Train.ipynb). These codes are modified versions of the original codes at https://github.com/kimmo1019/DeepCDR and https://github.com/horsedayday/DualGCN by the original authors of the models. For training these models, some previously preprocessed data and models are required, and these are stored at "https://drive.google.com/drive/folders/1QzpBAR6LfsXLKZlwQRbD53VdvWAycvTJ?usp=drive_link". Please download the files and have the data, model, and saved_output_data (for later) directories in the same folder as the scripts. The trained models should also be saved in the same models folder after training the models.

### Extracting Features

Once the models are trained, these are used to extract embeddings for drug and omic features, which are later used as inputs into the MEnKF algorithm. You can save the extracted features in the saved_output_data folder, which can later be used for training the MEnKF algorithm. The script for extracting features for the DeepCDR is in [DeepCDR_ExtractFeatures](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DeepCDR_%20ExtractFeatures.ipynb) and for DualGCN is in [DualGCN_ExtractFeatures](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DualGCN_ExtractFeatures.ipynb).

### Training MEnKF

The extracted features from the two models are then used to train the MEnKF algorithm. [MEnKF_AllFeatures](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/MEnKF_AllFeatures.ipynb) trains MEnKF with all features, and [MEnKF_Ablations](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/MEnKF_Ablations.ipynb) trains MEnKF with only a subset of features. The codes for creating the plots included in the manuscript are also included in these scripts.

## 2. Conventional Stacker

### Fine-tuning DeepCDR and DualGCN

Fine-tuning the trained DeepCDR and DualGCN for all features can be found in the scripts [DeepCDR_FineTune_Stacker_AllF](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DeepCDR_FineTune_Stacker_AllF.ipynb) and [DualGCN_FineTune_Stacker_AllF](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DualGCN_FineTune_Stacker_AllF.ipynb), respectively. Fine-tuning the DeepCDR and DualGCN for a subset of features can be found in the scripts [DeepCDR_FineTune_Stacker_Ablation](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DeepCDR_FineTune_Stacker_Ablation.ipynb) and [DualGCN_FineTune_Stacker_Ablation](https://github.com/Gayara-Fernando/MEnKF_CDRP/blob/main/DualGCN_FineTune_Stacker_Ablation.ipynb), respectively. These notebooks also give the predicted responses from the two models, which need to be saved to complete the stacking model. 
