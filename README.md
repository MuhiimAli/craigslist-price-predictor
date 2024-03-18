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

There are 3,254 entries in our dataset. We believe this data size is sufficient for our analysis. Should we discover the need for more data, we can easily increase our dataset, as we have access to 10,000 Craigslist items.

### Identifying Attributes

For each listing, our dataset includes the following identifying attributes:

- **Title**: The title of the item.
- **Price**: The asking price of the item.
- **Location**: Where the item is located, can be null.
- **Metadata**: Unprocessed date, location, and/or mileage.
- **Link**: The link to the Craigslist listing, serving as a unique identifier.
- **Images**: The images associated with the listing.
- **Num_images**: Number of images for the listing.
- **Category**: The Craigslist category shorthand that the item is listed under.
- **Metadata_length**: The number of attributes in the metadata.
- **Date**: Date posted.
- **Mileage**: The mileage of vehicle listings (car, motorcycle, snow-mobile), null for other listings.

### Data Collection

- **Source**: We scraped our data from Craigslist’s Providence section, focusing on items listed for sale by owners. Here is the URL: [Craigslist](https://providence.craigslist.org/search/sss?purveyor=owner#search=1~gallery~0~0).

- **Source Reputability**: We believe that Craigslist is an active second-hand item community and therefore is reputable for our task of predicting the prices of second-hand items.

- **Generating Samples**: We generate samples by webscraping Craigslist for the most recent listings in the Providence area. With around 3,000 items, we scraped 4 days of items (3/11 - 3/14). We also filtered to only scrape items with at least one image. These restrictions could introduce some underlying biases to our dataset but we believe that it is representative for our task of predicting prices for recent listings based on image and title.

- **Considerations**: Our dataset consists of publicly available information. We ensure all data used respects the privacy and consent of the individuals involved.

### Data Cleanliness

- **Cleaning Methods**: We check for data cleanliness using Pandas and Matplotlib by ensuring that item attributes are consistent within their category.
- **Missing Values**: Items that are not vehicles have a missing value in the "mileage" attribute, and there are some missing values for "location" based on whether the user inputted the information.
- **Duplicates**: We don't have duplicates in our dataset; each item has a unique URL, ensuring uniqueness.
- **Data Distribution**: It seems like there is a large number of low-priced items and fewer high-priced items within our dataset. Additionally, the number of items in each category is not evenly distributed.
- **Data Type Issues**:
  - **Title**: String
  - **Location**: String
  - **Price**: Numeric, allowing for quantitative analysis.
  - **Link**: Included as a unique identifier.
- **Data Exclusion**: We might consider excluding the link and metadata attributes because we have extracted the important information (category, date, location, and mileage) from those attributes.
