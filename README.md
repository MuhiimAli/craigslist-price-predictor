# Craigslist Item Price Predictor

TODO: Description

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

# Data Deliverable
## Data Specification



## Technical Report

### Total Data Points
There are approximately 3,000 entries in our dataset. We believe this data size is sufficient for our analysis. Should we discover the need for more data, we can easily increase our dataset, as we have access to 10,000 Craigslist items.

### Identifying Attributes
For each listing, our dataset includes the following identifying attributes:
- **Title**: The title of the item.
- **Price**: The asking price of the item.
- **Location**: Where the item is located.
- **URL**: The link to the Craigslist listing, serving as a unique identifier.

### Data Collection
- **Source**: We scraped our data from Craigslist’s Providence section, focusing on items listed for sale by owners. Here is the URL: [Craigslist](https://providence.craigslist.org/search/sss?purveyor=owner#search=1~gallery~0~0).

- **Source Repeatability**: 
--come back

- **Generating Samples**:

- **Considerations**: Our dataset consists of publicly available information. We ensure all data used respects the privacy and consent of the individuals involved.

### Data Cleanliness
- **Cleaning Methods**:
- **Missing Values**: Currently, our dataset does not include images of the items, although we have access to them. 
- **Duplicates**: We don't have duplicates in our dataset; each item has a unique URL, ensuring uniqueness.
-**Data Distribution**: It seems like there is a large number of low-priced items and fewer high-priced items within our dataset.
- **Data Type Issues**:
    - **Title**: String
    - **Location**: String
    - **Price**: Numeric, allowing for quantitative analysis.
    - **Link**: Included as a unique identifier.
- **Data Exclusion**: We might consider excluding the link attribute and replace it with the item images. 

