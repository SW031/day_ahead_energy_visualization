# ENTSO-E API Access and Data Retrieval Guide

Python client for the ENTSO-E API (european network of transmission system operators for electricity).

This guide provides step-by-step instructions on accessing the ENTSO-E Transparency Portal, obtaining an API key, using the EntsoePandas client, and fetching actual generation data per production type.

## Table of Contents

1. [Accessing the ENTSO-E Transparency Portal](#accessing-the-entso-e-transparency-portal)
2. [Obtaining the API Key](#obtaining-the-api-key)
3. [Setting Up the EntsoePandas Client](#setting-up-the-entsoepandas-client)
4. [Fetching Data from the ENTSO-E API](#fetching-data-from-the-entso-e-api)

## Accessing the ENTSO-E Transparency Portal

1. Visit the [ENTSO-E Transparency Portal](https://transparency.entsoe.eu/).
2. Click on **Sign Up** to create an account if you don’t have one. Fill in the required details and verify your email address.
3. Log in to your account.

## Obtaining the API Key

1. After logging in, navigate to your **profile** or **account settings** (typically found in the upper right corner).
2. Look for an option labeled **API Key** or **Request API Access**.
3. If an API key is not already issued, follow the on-screen instructions to request one. 
4. You can also directly contact ENTSO-E support at **support@entsoe.eu** to request an API key or for any issues related to access.
5. Check your email (including the spam folder) for the API key confirmation.

## Setting Up the EntsoePandas Client

1. Install the **EntsoePandas** library if you haven't done so yet. You can install it using pip:

   ```bash
   pip install entsoe-py
2. Import the necessary libraries and set up the client:

   ```bash
   import pandas as pd
   from entsoe import EntsoePandasClient

   # Replace 'YOUR_API_KEY' with your actual API key
   client = EntsoePandasClient(api_key='YOUR_API_KEY')
## Fetching Data from the ENTSO-E API

- You can fetch various types of data using the EntsoePandas client. Below is an example of how to retrieve actual generation data for specific countries over a specified date range.

  ```bash
  # Import necessary libraries
  import pandas as pd
  from entsoe import EntsoePandasClient

  # Initialize the client with your API key
  client = EntsoePandasClient(api_key='YOUR_API_KEY')

  # Define time period for data retrieval
  start = pd.Timestamp('2023-01-01', tz='UTC')  # Start date
  end = pd.Timestamp('2023-12-31', tz='UTC')    # End date
  country_code_at = 'AT'  # Austria
  country_code_de = 'DE_LU'  # Germany and Luxembourg

  # Fetch actual generation data
  generation_data_at = client.query_generation(country_code_at, start=start, end=end)
  generation_data_de = client.query_generation(country_code_de, start=start, end=end)

  # Display the data
  print("Austria Generation Data:\n", generation_data_at)
  print("Germany and Luxembourg Generation Data:\n", generation_data_de)

  # Display the data
  print("Austria Generation Data:\n", generation_data_at)
  print("Germany and Luxembourg Generation Data:\n", generation_data_de)

## Supported Queries

- **Actual Generation**: *client.query_generation(country_code, start, end)*
- **Generation Forecast**: *client.query_generation_forecast(country_code, start, end)*
- **Load Data**: *client.query_load(country_code, start, end)*
- **Cross-border Flows**: *client.query_crossborder_flows(country_code_1, country_code_2, start, end)*

## Additional Notes

- Ensure that your API key is kept confidential.
- Refer to the official [ENTSO-E API documentation](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html) for more details on available queries and parameters.
- For more information, refer [this repository](https://github.com/EnergieID/entsoe-py)

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.