# COSC2753_A2_Group8

Fashion Intelligence System — COSC2753 Machine Learning, Assignment 2.

## Requirements

- Python 3.12
- ~1 GB free disk space for the dataset, plus space for trained model files

## Setup

1. Clone the repository and move into it.

2. Create and activate a virtual environment:

   ```
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Install dependencies:

   ```
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

## Dataset

The dataset is not included in this repository (see `.gitignore`) and must be downloaded manually.

1. Download `A2_Fashion.zip` from the course Canvas page (Assignment 2 section).
2. Extract it and place the contents into the `data/` folder so the structure looks like this:

   ```
   data/
   ├── train/
   │   ├── images_train/          (~38,600 .jpg files)
   │   └── styles_train.csv
   └── test/
       ├── images_test/           (~5,800 .jpg files)
       └── styles_prediction.csv
   ```

3. Do not rename or reformat `styles_prediction.csv` — it is the required submission format.

## Running the project

1. `prepare.py` — run once to build the train/validation split and label encoders. This populates `splits/split.csv` and files in `models/`.
2. Notebooks in `notebooks/`, run in order:
   - `01_EDA.ipynb` — exploratory data analysis
   - `02_task1_articleType.ipynb` — Task 1: item type classification
   - `03_task2_season.ipynb` — Task 2: season classification
   - `04_task3_gender_usage.ipynb` — Task 3: gender and usage/occasion classification
   - `05_task4_visual_search.ipynb` — Task 4: visual search system
   - `06_comparison.ipynb` — model comparison and ultimate judgement
3. `predict.py` — run last to generate the final submission CSV using the chosen models.

Trained models are written to and read from `models/` (see that folder for the expected file layout per task).

## Project structure

```
app/            Flask API and frontend for serving the trained models
data/           Dataset (not tracked in git — see Dataset section above)
models/         Trained model artifacts and label encoders (not tracked in git, except labels.json)
notebooks/      Jupyter notebooks for each task
splits/         Train/validation split definition
src/            Shared code: config, data loading, model architectures, metrics
prepare.py      One-time data preparation script
predict.py      Final prediction/submission script
```
