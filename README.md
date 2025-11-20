# COS-802-Machine-Translation-Model-PROJECT
# Project Overview 
Machine translation models for low-resource African languages are often evaluated against benchmarks that contain significant errors. This project investigates the impact of dataset corrections on the FLORES-200 benchmark for four African languages: Hausa (hau), Sepedi (nso), Xitsonga (tso), and isiZulu (zul).

Using a "before-and-after" comparative methodology, this study evaluates two state-of-the-art models (NLLB-200 and M2M-100) to determine how fixing the test data influences:

* Translation Quality Scores (BLEU, ChrF, BERTScore, COMET).
* Model Preformance Ranking.
* Interpretability and Error Diagnosis.
# Project Overview
# 📂Repository Structure
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
The notebook loads dataset files directly from GitHub using a custom Python function called load_data_from_github. This function reads source and target text files, removes empty lines, cleans formatting issues, and stores samples in Python lists for translation.
# Models Used
* # NLLB-200
A multilingual model that supports more than 200 languages. It is known for strong performance on African languages. The project uses language codes such as zul_Latn for isiZulu.
* # M2M-100
A multilingual translation model trained directly on many language pairs. It supports over 100 languages and serves as a comparison to NLLB-200 for translation quality.

# Inference Pipeline

The core inference function (run_inference) performs model loading, tokenization, GPU-accelerated translation, text decoding, and storage of translated outputs. The hypotheses are saved in two dictionaries: all_hypotheses_nllb and all_hypotheses_m2m.

# Evaluation

The notebook prepares an evaluation_results dictionary, which stores model outputs, references, and space for evaluation metrics such as BLEU, ChrF, or COMET. 

# How to Run

Open the notebook in Google Colab and enable GPU by selecting “Runtime → Change runtime type → GPU.” Run all cells in sequence to install dependencies, load models, load the dataset, perform inference, and generate hypotheses for evaluation.

#  Key Findings
* Ranking Stability: The dataset corrections did not change the state-of-the-art ranking. NLLB-200 remained the superior model across all languages.

* Interpretability Crisis: The qualitative analysis revealed that the original dataset caused a misdiagnosis of model performance. Correct translations were penalized because the "answer key" was wrong (e.g., 22% error rate in isiZulu).

# Conclusion
* Corrected data is essential for interpretability and understanding why models fail, even if the leaderboard ranking remains stable.

# Author

Merrhawi Hailu
COS-802 Machine Translation Project

