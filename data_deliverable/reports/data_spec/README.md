## Data Specification

See [`data_deliverable/data/sample.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/sample.json) for sample data (100 rows).

See [`data_deliverable/data/preprocessed_items.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/preprocessed_items.json) for full data.

- **title** (type String) required
  - Default: Not applicable
  - Range: string length between 4 and 80
  - Distribution of string length:
    - Mean: 34
    - Standard Deviation: 17
    - Null: 0
  - Unique: No
  - Sensitive: None
  - Usage: We will encode the title into semantic embeddings with SpaCy and use the embedding values to predict item prices.
- **Price** (type Float) required
  - Default: Not applicable
  - Range: 1.0 to 99999.0
  - Distribution:
    - Mean: 1157.0
    - Standard Deviation: 4529.24
    - Null: 0
  - Unique: No
  - Sensitive: None
  - Usage: We will use this variable as our target variable for training and testing.
- **Location** (type String) optional
  - Default: ""
  - Range: 293 unique locations including physical transaction locations and online website locations
  - Distribution of number of items per location:
    - Mean: 11
    - Standard Deviation: 29
    - Null: 12
  - Unique: No
  - Sensitive: None
  - Usage: We will encode this variable into dummy variables to be used to predict item prices.
- **Link** (type String) required
  - Default: Not applicable
  - Range: links to item pages with 60 to 96 characters
  - Distribution of url length:
    - Mean: 89
    - Standard Deviation: 5.8
    - Null: 0
  - Unique: Yes
  - Sensitive: None
  - Usage: We will use this attribute to ensure that we do not have duplicate entries in our dataset.
- **Images** (type List of String) required
  - Default: Not applicable
  - Range: 1 to 2 image urls
  - Distribution of number of images:
    - Mean: 1
    - Standard Deviation: 0.35
    - Null: 0
  - Unique: Yes
  - Sensitive: None
  - Usage: We will encode the first image of every listing with pre-trained image encoders and use it to predict the item price.
- **Category** (type String) required
  - Default: Not applicable
  - Range: 59 categories created by Craigslist
  - Distribution of number of items per category:
    - Mean: 55
    - Standard Deviation: 76
    - Null: 0
  - Unique: No
  - Sensitive: None
  - Usage: We will encode this variable into dummy variables to be used to predict item prices.
- **Date** (type String) required
  - Default: Not applicable
  - Range: 3/11, 3/12, 3/13, 3/14
  - Distribution of number of items per date:
    - Mean: 650
    - Standard Deviation: 719
    - Null: 0
  - Unique: No
  - Sensitive: None
  - Usage: We will encode this variable into dummy variables to be used to predict item prices.
- **Mileage** (type Float) optional
  - Default: 0.0
  - Range: 10 to 344,000
  - Distribution:
    - Mean: 92998.6
    - Standard Deviation: 71585.1
    - Null: 3054
  - Unique: No
  - Sensitive: None
  - Usage: We will use this variable as an attribute to predict the item price.
