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

Install the packages listed in `requirements.txt`, open
`NLP_7th_Assignment.ipynb`, and run the cells from top to bottom. The notebook
is self-contained and does not depend on helper modules outside this folder.
Training is opt-in through `RUN_EXPERIMENTS = False`; enable it only when you
are ready to run the five experiments.

The train split is used for learning, validation is used for model selection
and early stopping, and the test split is reserved for final evaluation.
Evaluation reconstructs BIO spans and requires exact boundary and entity-type
matching. Token accuracy is not used as a replacement for entity-level F1.

GloVe is downloaded by gensim the first time the GloVe cells run:
`glove-wiki-gigaword-100`. Internet access is therefore required for
Experiments 3 and 4 unless the gensim model is already cached.

## Results

`results/results.csv` contains the current measured preliminary results.
The current CSV contains the three completed classical experiments; it must be
regenerated after Experiments 4 and 5 are run so that it contains all five
models. The files in `results/visualizations/` are generated from CSV values,
not invented sample values.

The assignment report and presentation should be written in the student's own
words. The notebook is implementation and experimental evidence, not a
replacement for the required report or video.

The original archive and source snapshot are preserved outside this submission
folder in `NLP assignment_original_backup`.
