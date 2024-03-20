## Technical Report

See [`data_deliverable/data/sample.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/sample.json) for sample data (100 rows).

See [`data_deliverable/data/preprocessed_items.json`](https://github.com/csci1951a-spring-2024/final-project-price-predictor/blob/main/data_deliverable/data/preprocessed_items.json) for full data.

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
  - **Date**: String (mm/dd)
  - **Link**: Included as a unique identifier.
- **Data Exclusion**: We might consider excluding the link and metadata attributes because we have extracted the important information (category, date, location, and mileage) from those attributes.

### Challenges and Next Steps

Some attributes that we found could pose a challenge during our analysis is the uneven distribution of categories and the fact that our data only sampled a very small time window (4 days). This could mean that our dataset would not be fully representative of the price distribution in the long term.

For next steps, depending on the type of analysis that we'll pursue, we may process the item title into SpaCy embedding, image into image embedding, and date, location, and category features into dummy variables. The analyses that we plan to pursue are the following:

#### Hypothesis Testing

##### 1. Difference in Mean Price Across Locations
- **Null Hypothesis (H0):** There is no significant difference in the mean price of items across different locations.  
- **Alternate Hypothesis (H1):** There is a significant difference in the mean price of items across different locations.  
- **Statistical Test:** Kruskal-Wallis test

##### 2. Difference in Mean Price Across Categories
- **Null Hypothesis (H0):** There is no significant difference in the mean price of items across all categories.  
- **Alternate Hypothesis (H1):** There is a significant difference in the mean price of items across all categories.  
- **Statistical Test:** Kruskal-Wallis test
##### 3. Linear Relationship Between Mileage and Price in Vehicle Listings
- **Null Hypothesis (H0):** There is no linear relationship between the mileage and price in vehicle listings.  
- **Alternate Hypothesis (H1):** There is a linear relationship between the mileage and price in vehicle listings.  
- **Statistical Test:** Simple linear regression

##### 4. Price Difference Based on Item Condition
- **Null Hypothesis (H0):** Items listed with a condition labeled as "like new" or "new" do not have significantly higher prices than those listed as "good."  
- **Alternate Hypothesis (H1):** Items listed with a condition labeled as "like new" or "new" have significantly higher prices than those listed as "good."  
- **Statistical Test:** a T-test


#### Machine Learning
  - Unsupervised clustering to find distinct groups
  - Supervised regression to predict item prices
