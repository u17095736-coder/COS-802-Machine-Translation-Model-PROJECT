# COS-802-Machine-Translation-Model-PROJECT
# Project Overview 
Machine translation models for low-resource African languages are often evaluated against benchmarks that contain significant errors. This project investigates the impact of dataset corrections on the FLORES-200 benchmark for four African languages: Hausa (hau), Sepedi (nso), Xitsonga (tso), and isiZulu (zul).

Using a "before-and-after" comparative methodology, this study evaluates two state-of-the-art models (NLLB-200 and M2M-100) to determine how fixing the test data influences:
* Translation Quality Scores (BLEU, ChrF, BERTScore, COMET).
* Model Preformance Ranking.
* Interpretability and Error Diagnosis.
  
# Repository Structure
```text
COS-802-Machine-Translation-Model
 ┣ Machine_Translation_model_for_African_language.ipynb
 ┣ README.md
```
# Technologies Used
* Python
* PyTorch
* Hugging Face Transformers
* Google Colab
* Torch GPU acceleration
* NLLB-200 and M2M-100 multilingual models
# Installation
Before running the notebook, install the dependencies using:
``` text 
!pip install -r requirements.txt
````
* Key libraries include torch, transformers, sentencepiece, and datasets.
* Using GPU acceleration is recommended.
# Dataset Loading and Preprocessing 
The notebook loads dataset files directly from the authoritative GitHub source (dsfsi/flores-fix-4-africa) to ensure we have the exact "Uncorrected" (flawed) and "Corrected" (validated) files used by the original researchers.
# Models Used
*  NLLB-200  (facebook/nllb-200-distilled-600M)
A multilingual model that supports more than 200 languages. It is known for strong performance on African languages. The project uses language codes such as zul_Latn for isiZulu.
*  M2M-100  (facebook/m2m100_418M)
A multilingual translation model trained directly on many language pairs. It supports over 100 languages and serves as a comparison to NLLB-200 for translation quality.

# Inference Pipeline

The core inference function (run_inference) performs model loading, tokenization, GPU-accelerated translation, text decoding, and storage of translated outputs. The hypotheses are saved in two dictionaries: all_hypotheses_nllb and all_hypotheses_m2m.

# Evaluation

The notebook performs a comparative evaluation using the evaluation_results dictionary. It calculates BLEU, ChrF, BERTScore, and COMET for every hypothesis against both the Corrected and Uncorrected reference sets.

# How to Run

Open the notebook in Google Colab and enable GPU by selecting “Runtime → Change runtime type → GPU.” Run all cells in sequence to install dependencies, load models, load the dataset, perform inference, and generate hypotheses for evaluation.

#  Key Findings
* Ranking Stability: The dataset corrections did not change the state-of-the-art ranking. NLLB-200 remained the superior model across all languages (Rank #1) compared to M2M-100 (Rank #2).
* Interpretability Crisis: The qualitative analysis revealed that the original dataset caused a misdiagnosis of model performance. Correct translations were penalized because the "answer key" was wrong (e.g., 22% error rate in isiZulu).

# Conclusion
* Corrected data is essential for interpretability and understanding why models fail, even if the leaderboard ranking remains stable. Without accurate evaluation data, researchers cannot distinguish between model errors and dataset errors

#  Data Source
All data is sourced from the official repository for the correction paper:
* Repository: dsfsi/flores-fix-4-africa
* Paper: Abdulmumin et al. (2024), "Correcting FLORES Evaluation Dataset for Four African Languages."

# Author
Merhawi Hailu
u17095736
COS-802 |  Machine Translation Project
University of Pretoria 

