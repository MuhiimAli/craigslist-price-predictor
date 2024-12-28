# Craigslist Item Price Predictor
## Objective 
This project uses supervised regression to predict item prices. 

## Dataset
### Data Collection
- We webscrape from Providence's Craigslist all-category gallery [https://providence.craigslist.org/]
- For each item listing, we collect:
  - Images
  - Title
  - Price
  - Mileage (for vehicle listings)
  - Post date
  - Location
- Dataset size: 3,254 items
- Temporal coverage: 4 unique days between 3/11 and 3/14
- Note: Our dataset contains only publicly available information

### Methodology
#### Feature Engineering

1. Image Features
   - Preprocessed using pretrained VGG16 Keras model
   - Applied PCA for dimensionality reduction
   - Final representation: 210-dimensional feature vectors

2. Text Features
   - Extracted from item titles
   - Used spaCy's small text embedding model
   - Generated compact numerical representations of textual content

3. Statistical Analysis
   - Applied Kruskal-Wallis test
   - Purpose: Identify significant differences in mean prices across:
     - Different categories
     - Different locations

#### Price Prediction
- Model: Linear Regression
- Input features:
  - Image features
  - Text embeddings
  - Categorical variables (location, category)
  - Numerical attributes (mileage)
- Objective: Predict item prices using all available attributes

## Deliverables
### Final Deliverables

Visualizations: [`analysis_deliverable/visualizations`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/analysis_deliverable/visualizations)

Poster: [`final_deliverable/poster.pdf`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/final_deliverable/poster.pdf)

Abstract: [`final_deliverable/abstract.pdf`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/final_deliverable/abstract.pdf)

Socio-historical Context and Impact Report: [`final_deliverable/impact.pdf`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/final_deliverable/impact.pdf)

Presentation: [`final_deliverable/presentation.mp4`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/final_deliverable/presentation.mp4)

### Data Deliverables

Techincal Report: [`data_deliverable/reports/technical_report`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/data_deliverable/reports/technical_report)

Data Spec: [`data_deliverable/reports/data_spec`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/tree/main/data_deliverable/reports/data_spec)

Full Data: [`data_deliverable/data/preprocessed_items.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/preprocessed_items.json)

Sample (100 rows): [`data_deliverable/data/sample.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/sample.json)

### Environment setup

After cloning the repo, please navigate to the current directory and run the following commands in the terminal.

`python3 -m venv cs1951a_project_venv`

`source cs1951a_project_venv/bin/activate`

`pip3 install -r requirements.txt`

`python3 -m ipykernel install --user --name=cs1951a_project_venv`

To run Jupyter Notebook, activate your virtual environment and then run this command:

`jupyter notebook`

To activate/deactivate environment in the future:

- `source cs1951a_project_venv/bin/activate`
- `deactivate`

# limitations
The nature of the data:


Second-hand goods prices are inherently subjective
Individual sellers might price items inconsistently
Market conditions during the data collection period (March 11-16) might vary
Local variations in supply and demand


Looking at our features:


Numeric: mileage, number of images, date
Categorical: location, category
Image features: reduced VGG16 representations
Text features: from titles