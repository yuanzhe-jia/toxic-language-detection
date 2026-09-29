# Toxic Language Detection

**Abstract.**
In-game toxic language has emerged as a critical concern in the gaming industry and community. 
While several frameworks and models for online game toxicity analysis have been proposed, detecting toxicity in player chat utterances remains a formidable challenge: stemming not only from the extremely short length of such utterances but also from the heavy reliance on game slang, abbreviations, and domain-specific jargon, which generic language models are poorly suited to recognize. 
This project introduces the best-preforming model for the in-game toxic language detection from the real-world in-game chat data. 
![BRAR Architecture](image/brar.png)

## Model

**BRAR (Bi-directional Representations with Attention Residuals)** integrates:
- **BiLSTM** performs feature extraction on the input data in sequence.
- **Attention Residual** aims to understand the global information and find the main ideas of the input utterance. 
- **Label Forcing** enhances the feature representation to form the emission scores of the CRF layer.
- **CRF** enables the model to enforce valid tag transitions and prevents locally optimal but globally inconsistent predictions.

## Dataset

The CONDA dataset used in this project comprises 44,869 player chat utterances, derived from chat logs of 1,921 Dota 2 matches and annotated with the following six distinct slot labels:
- **T**: Toxicity
- **C**: Character
- **D**: Dota-specific
- **S**: Game Slang
- **P**: Pronoun
- **O**: Other

## Usage

```bash
python src/brar.py
```

## Project Structure

```
toxic-language-detection/
├── data/              # CONDA dataset
│   ├── train.csv
│   ├── val.csv
│   └── CONDA_test_original.csv
├── image/             # Model architecture diagram
│   └── brar.png
├── src/
│   └── brar.py        # BRAR model implementation
├── requirements.txt   # Python dependencies
├── .gitignore
└── README.md
```
