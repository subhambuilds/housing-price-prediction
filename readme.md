# California Housing Price Prediction 🏠📉

## Repository Structure
```text
housing-price-prediction/
│
├── notebooks/                     # Chronological development steps
│   ├── 01_analyzing_the_data.ipynb
│   ├── 02_creating_a_testset.ipynb
│   ├── 03_visualizing_the_data.ipynb
│   ├── 04_further_preprocessing.ipynb
│   ├── 05_handling_categorical_values.ipynb
│   ├── 06_feature_scaling.ipynb
│   └── 07_sklearn_pipelines.ipynb
│
├── src/                           # Production executable scripts
│   ├── main.py                    # Main pipeline for training & inference
│   └── main_old.py                # Cross-validation & modeling records
│
├── .gitignore                     # Hides datasets, local caches, and binaries
├── README.md                      # Documentation homepage (This file)
└── requirements.txt               # Project library dependencies
```
## Project Overview
The goal of this project is to build a machine learning model that predicts the median housing prices in various California districts. By examining features such as geography (latitude and longitude), population, total rooms, households, and median income, the model learns complex patterns to accurately estimate property values. This is a classic regression problem solved using data science best practices.

## Dataset
The project utilizes the **California Housing Dataset** (originally sourced from the US Census Bureau). The data contains information regarding blocks of houses in California, providing essential metrics for exploratory data analysis, data visualization, and model training.

## Methodology
The project follows a structured, chronological lifecycle divided into clear execution phases:

1. **Exploratory Data Analysis (EDA):** Analyzed data types, statistical distributions, and checked for missing records (`01_analyzing_the_data.ipynb`).
2. **Stratified Sampling:** Implemented `StratifiedShuffleSplit` based on income categories to create a robust, statistically representative test set, preventing *data snooping bias* (`02_creating_a_testset.ipynb`).
3. **Geographical Visualization:** Created advanced scatter plots mapping coordinates to housing prices and density alongside a feature correlation analysis (`03_visualizing_the_data.ipynb`).
4. **Data Cleaning & Preprocessing:** Handled missing data via median imputation (`04_further_preprocessing.ipynb`) and applied `OneHotEncoder` to handle categorical text attributes like ocean proximity (`05_handling_categorical_values.ipynb`).
5. **Feature Scaling:** Applied standardization using `StandardScaler` to ensure uniform numerical feature weighting (`06_feature_scaling.ipynb`).
6. **Scikit-Learn Pipelines:** Unified the entire workflow into a clean, automated, and production-ready `ColumnTransformer` pipeline architecture to eliminate data leakage (`07_sklearn_pipelines.ipynb` and `src/main.py`).

## Results
During model development (`src/main_old.py`), multiple regression models were evaluated using **10-Fold Cross-Validation** to measure performance and ensure generalization:
* **Linear Regression:** Acted as our baseline; suffered from structural underfitting.
* **Decision Tree Regressor:** Suffered heavily from overfitting on the training set.
* **Random Forest Regressor:** Our **Top Performing Model**. It minimized validation error significantly and demonstrated the best predictive performance.

The production script (`src/main.py`) utilizes the finalized Random Forest model architecture for automated training and live predictions.

## How to Run It

### 1. Clone the Repo
```bash
git clone [https://github.com/YOUR_USERNAME/housing-price-prediction.git](https://github.com/YOUR_USERNAME/housing-price-prediction.git)
cd housing-price-prediction
```
### 2. Install Dependencies
Set up your python environment by installing the exact package requirements:
```bash
pip install -r requirements.txt
```
### 3. Run the Production Pipeline
Run the main script. If the trained model binaries (model.pkl and pipeline.pkl) are not present, it will automatically handle stratified splitting, train the pipeline, and serialize the models. If they already exist, it instantly skips training to perform inference predictions:
```bash
python src/main.py
```
***

### 💻 How to Copy and Paste It in One Go

#### Option A: On GitHub (Directly in your Browser)
1. Go to your repository page on **GitHub**.
2. Click **Add file** (near the top right) $\rightarrow$ **Create new file**.
3. In the filename box, type **`README.md`**.
4. Hover over the large markdown code box above, click the **Copy** icon in the top right corner of the box, click into the GitHub text editor area, and press **Ctrl + V** (or **Cmd + V** on Mac) to paste it all at once.
5. Scroll to the bottom and click the green **Commit changes** button.

#### Option B: In VS Code (Locally)
1. Open your project folder in **VS Code**.
2. Create a new file named exactly **`README.md`**.
3. Copy the entire box above and paste it directly into the file.
4. Save the file (**Ctrl + S**).
5. Open your terminal window and push it to GitHub using these commands:
   ```bash
   git add README.md
   git commit -m "Add final complete README documentation"
   git push origin main