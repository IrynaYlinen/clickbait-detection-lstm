# Clickbait Detection using LSTM

![Clickbait Detection using LSTM](lstm_thumbnail.png)

## Project Overview

A Natural Language Processing (NLP) project focused on
binary classification of clickbait and non-clickbait
headlines using a Long Short-Term Memory (LSTM)
neural network.

The project covers the complete deep learning workflow,
from data quality assessment and text preprocessing
to model training, evaluation and inference.

## Key Results

| Metric | Result |
|---|---:|
| Dataset size | 32,000 headlines |
| Test samples | 8,000 |
| Test accuracy | 97.78% |
| Weighted F1-score | 97.77% |
| Test loss | 0.0634 |
| Correct predictions | 7,822 |
| Misclassified headlines | 178 |
| Training epochs | 4 |
| Selected model epoch | 1 |

## Dataset

The dataset contains 32,000 English-language headlines:

- Clickbait: 15,999 samples
- Non-clickbait: 16,001 samples

**Dataset source:**
[Clickbait Dataset](https://github.com/bhargaviparanjape/clickbait/tree/master/dataset)

The dataset is not duplicated in this repository.
To reproduce model training, download the following
files from the original source and place them in
a local `data/` directory:

- `clickbait_data.txt`
- `non_clickbait_data.txt`

## Methodology

1. Data loading and quality assessment
2. Exploratory data analysis
3. Stratified train-validation-test splitting (60/15/25)
4. Text tokenisation and sequence padding
5. LSTM model development
6. Model training with early stopping
7. Performance evaluation
8. Misclassification analysis
9. Model inference and saving

The tokeniser was fitted exclusively on the training
set to prevent data leakage during preprocessing.

## Model Architecture

| Layer | Configuration |
|---|---|
| Embedding | 64 dimensions |
| LSTM | 128 units |
| Dense | 64 units, ReLU |
| Dropout | 0.3 |
| Output | 1 unit, Sigmoid |

- Maximum sequence length: 32 tokens
- Optimiser: Adam
- Loss function: Binary Crossentropy
- Total trainable parameters: 1,387,137

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Repository Structure

```text
clickbait-detection-lstm/
├── artifacts/
│   ├── clickbait_lstm.keras
│   ├── tokenizer.json
│   └── config.json
├── clickbait_detection_lstm.ipynb
├── test_inference.ipynb
├── lstm_thumbnail.png
├── requirements.txt
├── .gitignore
└── README.md
```

## Installation and Usage

Clone the repository:

```bash
git clone https://github.com/IrynaYlinen/clickbait-detection-lstm.git
cd clickbait-detection-lstm
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebooks using Jupyter.

### Model Training

Download the dataset as described above and run
`clickbait_detection_lstm.ipynb`.

### Inference Without Retraining

Open `test_inference.ipynb` to load the pretrained
model and classify new headlines.

The original dataset is not required for inference.

## Example Predictions

| Headline | Clickbait Probability | Prediction |
|---|---:|---|
| You Won't Believe What Happened Next | 99.95% | Clickbait |
| Central Bank Keeps Interest Rates Unchanged | 0.40% | Non-clickbait |

## Limitations

- Classification relies exclusively on headline text.
- Ambiguous headlines may be misclassified.
- Generalisation to external datasets and recent
  headlines has not been independently validated.
- The model detects clickbait, not factual accuracy
  or misinformation.

## Future Improvements

- Comparison with traditional machine learning models
- Transformer-based text classification
- Evaluation on external datasets
- Interactive Streamlit application

## Acknowledgements

This project was developed as part of academic studies
in Data Analytics and Artificial Intelligence at
JAMK University of Applied Sciences and subsequently
refined for a Data Science portfolio.

Dataset credit: *Stop Clickbait: Detecting and
Preventing Clickbaits in Online News Media* (2016).
