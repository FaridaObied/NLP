# CAI4201 NLP Assignment

This project compares five named-entity recognition approaches on the supplied
CoNLL-2003 data:

1. N-gram features with POS, chunk, capitalization, and an SGD classifier;
2. training-data Word2Vec context vectors with an SGD classifier;
3. pretrained GloVe context vectors with the same classifier design;
4. an LSTM using combined Word2Vec and GloVe features; and
5. an LSTM with a trainable embedding layer.

## Project structure

```text
NLP assignment/
├── NLP_7th_Assignment.ipynb
├── data/
│   ├── train.txt
│   ├── valid.txt
│   └── test.txt
├── results/
│   ├── results.csv
│   └── visualizations/
├── requirements.txt
└── README.md
```

## Running the notebook

From the project folder on Windows, use Python 3.11 to set up and launch JupyterLab:

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\jupyter-lab.exe NLP_7th_Assignment.ipynb
```

Run the notebook from top to bottom with `RUN_EXPERIMENTS = True` to train
all five models. The LSTMs can take several minutes on a CPU. In **Try your
own text**, replace the example in `text_to_tag` with English text and run
that cell. It shows one BIO tag per token from each of the five models. You
can rerun the text cell with new input throughout the same kernel session.
After a kernel restart, run the training cells again.

The train split is used for learning, validation is used for model selection
and early stopping, and the test split is reserved for final evaluation.
Evaluation reconstructs BIO spans and requires exact boundary and entity-type
matching. Token accuracy is not used as a replacement for entity-level F1.

GloVe is downloaded by gensim the first time the GloVe cells run:
`glove-wiki-gigaword-100`. Internet access is therefore required for
Experiments 3 and 4 unless the gensim model is already cached.
The first raw-text run also downloads NLTK's English sentence tokenizer and
POS tagger data if they are missing. The N-gram model uses generated POS and
rule-based chunk tags for raw text and the supplied tags for benchmark data.

## Results

Running all five experiments regenerates `results/results.csv`,
`results/per_class_results.csv`, and the plots in `results/visualizations/`.

The assignment report and presentation should be written in the student's own
words. The notebook is implementation and experimental evidence, not a
replacement for the required report or video.

The original archive and source snapshot are preserved outside this submission
folder in `NLP assignment_original_backup`.
