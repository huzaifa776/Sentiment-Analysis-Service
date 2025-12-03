# Sentiment Analysis Service

Lightweight sentiment analysis pipeline built on Amazon product reviews.

Dataset
- Kaggle: https://www.kaggle.com/datasets/lazylad99/amazon-e-commerce-product-and-review-dataset?resource=download
- Raw CSV in repo: [data/raw/reviews.csv](data/raw/reviews.csv)

Quickstart
1. Install minimal dependencies:
   pip install pandas scikit-learn matplotlib seaborn wordcloud joblib
2. Run preprocessing notebook to produce cleaned CSVs:
   - Open and run [pre-processing.ipynb](pre-processing.ipynb). This creates:
     - [data/processed/preprocessed_train.csv](data/processed/preprocessed_train.csv)
     - [data/processed/preprocessed_test.csv](data/processed/preprocessed_test.csv)
     - [data/processed/preprocessed_full.csv](data/processed/preprocessed_full.csv)
3. Train models:
   - Open and run [modelling.ipynb](modelling.ipynb). The training loop compares models defined in [`modelling.models`](modelling.ipynb) and saves the chosen model (see [`modelling.final_model`](modelling.ipynb)).
4. Explore data:
   - Use [eda.ipynb](eda.ipynb) for visualizations and basic statistics.

Key code references
- Text cleaning transformer: [`pre_processing.TextCleaner`](pre-processing.ipynb)
- Preprocessing pipeline (cleaner + TF-IDF): [`pre_processing.preprocessing_pipeline`](pre-processing.ipynb)
- Model selection container: [`modelling.models`](modelling.ipynb)
- Final model variable and saved artifact: [`modelling.final_model`](modelling.ipynb) (saved as `sentiment_model.pkl` by the notebook)

Repository layout (relevant)
- [eda.ipynb](eda.ipynb) — exploratory data analysis and visualizations
- [pre-processing.ipynb](pre-processing.ipynb) — cleaning, TextCleaner, preprocessing pipeline, creates processed CSVs
- [modelling.ipynb](modelling.ipynb) — model training, evaluation, and serialization
- data/raw/reviews.csv — raw dataset
- data/processed/ — processed CSVs produced by preprocessing notebooks

Notes
- The notebooks expect the raw CSV at [data/raw/reviews.csv](data/raw/reviews.csv).
- Processed outputs are written to [data/processed/](data/processed/).
- The modelling notebook attempts a dynamic import of a preprocessing module; if not present it falls back to an inline TF-IDF pipeline.
