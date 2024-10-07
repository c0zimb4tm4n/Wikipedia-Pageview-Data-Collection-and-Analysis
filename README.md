# DATA-512 Homework 1: Wikipedia Pageview Data Collection and Analysis

## Project Goal

The goal of this project is to collect, analyze, and publish a dataset of monthly pageviews for a selected set of Wikipedia articles related to rare diseases. The data covers the period from July 1, 2015, to September 30, 2024, and is collected from the Wikimedia Pageviews API. The project aims to promote open and reproducible scientific research by following best practices for data acquisition, processing, and visualization. The final deliverables include JSON data files and time series visualizations of pageviews across different access types (desktop and mobile).

## License

This project is based on data obtained from the Wikimedia Foundation, which is licensed under the [Creative Commons Attribution-ShareAlike 3.0 Unported (CC BY-SA 3.0)](https://creativecommons.org/licenses/by-sa/3.0/). Per Wikimedia's [Terms of Use](https://foundation.wikimedia.org/wiki/Terms_of_Use), the data collected in this project can be freely used for research and analysis, provided that proper attribution is given to the source. The project itself is licensed under the [MIT License](LICENSE), allowing for open access and use of the code.

## Relevant API Documentation

The data collection process relies on the Wikimedia Pageviews API. Documentation and guidelines for the API can be found here:
- [Wikimedia REST API Documentation](https://wikimedia.org/api/rest_v1/#/Pageviews%20data/get_metrics_pageviews_per_article__project___access___agent___article___granularity___start___end_)

The Pageviews API allows access to traffic data for desktop, mobile web, and mobile app traffic starting from July 2015. The API was used to fetch pageviews for the list of Wikipedia articles related to rare diseases.

## Project Structure

The project includes the following files:

### Data Files

1. **`rare-disease_monthly_desktop_201507-202409.json`**:
   - Contains monthly pageviews for all articles from desktop access, covering the period from July 2015 to September 2024.
   - **Schema**: 
     - `article_title` (string): The title of the Wikipedia article.
     - `timestamp` (string): The month for which pageviews were recorded (in `YYYYMMDD00` format).
     - `views` (integer): The number of pageviews for the given month.

2. **`rare-disease_monthly_mobile_201507-202409.json`**:
   - Contains combined monthly pageviews for all articles from mobile access (web and app), covering the period from July 2015 to September 2024.
   - **Schema**: 
     - `article_title` (string): The title of the Wikipedia article.
     - `timestamp` (string): The month for which pageviews were recorded (in `YYYYMMDD00` format).
     - `views` (integer): The number of pageviews for the given month (sum of mobile web and mobile app views).

3. **`rare-disease_monthly_cumulative_201507-202409.json`**:
   - Contains cumulative monthly pageviews for all articles (desktop, mobile-web, and mobile-app) from July 2015 to September 2024.
   - **Schema**: 
     - `article_title` (string): The title of the Wikipedia article.
     - `timestamp` (string): The month for which pageviews were recorded (in `YYYYMMDD00` format).
     - `views` (integer): The total number of pageviews for the given month across all access types.

### Notebook Files

1. **`data_acquisition.ipynb`**:
   - This notebook contains the code to request and collect Wikipedia pageview data using the Wikimedia Pageviews API. It includes functions for fetching data for desktop, mobile (web and app), and cumulative pageviews. The data is saved as JSON files.
   - **Steps in the Notebook**:
     1. Data Acquisition: Fetch pageview data using the Wikimedia API.
     2. Data Processing: Combine mobile web and mobile app views for mobile data and aggregate all access types for cumulative data.
     3. Data Saving: Save the processed data as JSON files.

2. **`data_analysis.ipynb`**:
   - This notebook performs the visual analysis of the collected data. It includes the following graphs:
     - **Max and Min Average Pageviews**: Displays the articles with the highest and lowest average pageviews for both desktop and mobile access.
     - **Top 10 Peak Pageviews**: Shows the top 10 articles by peak pageviews for desktop and mobile access.
     - **Fewest Months of Data**: Highlights the 10 articles with the fewest months of available data for desktop and mobile access.
   - The visualizations are saved as PNG files.

### Visualization Files

1. **`Max_and_Min_Average_Page_Requests_Over_Time.png`**: A time series plot showing the articles with the highest and lowest average page requests for both desktop and mobile access types.
2. **`Top_10_Peak_Page_Views.png`**: A time series plot displaying the top 10 articles by peak pageviews for desktop and mobile access.
3. **`Articles_with_Fewest_Months_of_Data_Right_Legend.png`**: A plot showing the 10 articles with the fewest months of data, for both desktop and mobile access types.

### LICENSE File

The project is licensed under the [MIT License](LICENSE). This allows for open access to the code and the ability to reuse it with proper attribution.

## Known Issues or Special Considerations

- **Data Gaps**: Some articles have incomplete pageview data, likely due to article creation dates or low traffic. These articles are analyzed in the "Fewest Months of Data" graph.
- **Mobile Data Summation**: The Wikimedia API provides separate data for mobile web and mobile app access, which were combined to produce a unified mobile pageviews dataset.
- **API Rate Limits**: Wikimedia enforces a rate limit of 100 requests per second. To comply, the code introduces a small delay between API requests, which may increase the total time required for data collection.

## How to Reproduce

1. **Set Up Environment**:
   - Install the required packages using `pip`:
     ```
     pip install requests pandas matplotlib
     ```
   - Ensure you have Jupyter Notebook or Jupyter Lab installed to run the `.ipynb` files.

2. **Run Data Collection**:
   - Open the `data_acquisition.ipynb` notebook.
   - Execute all the cells to fetch the pageview data and save the resulting JSON files.

3. **Run Data Analysis**:
   - Open the `data_analysis.ipynb` notebook.
   - Execute the cells to generate the visualizations based on the collected data.

4. **Review Outputs**:
   - The JSON files will be saved in the `data/` directory.
   - Visualizations will be saved as PNG files for further use or publication.

## Contact

For any questions or issues, please contact `<Your Email>`.

