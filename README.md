## Tesla and GameStop Stock Analysis
### Aim
The aim of this project is to analyze the stock performance of Tesla (TSLA) and GameStop (GME) by extracting historical stock data using the yfinance library and revenue data through web scraping. The analysis includes plotting the stock prices for both companies to visualize trends and performance over time.
### Procedure
### 1.Extract Tesla Stock Data:
Use the yfinance library to download historical stock data for Tesla from January 1, 2020, to January 1, 2024.
Reset the index of the resulting DataFrame for easier manipulation.
### 2.Extract Tesla Revenue Data:

Use web scraping techniques to extract the revenue data of Tesla from a reliable financial website.
Store the revenue data in a DataFrame and view the last five entries.
### 3.Extract GameStop Stock Data:

Use the yfinance library to download historical stock data for GameStop within the same date range.
Reset the index of the DataFrame for better accessibility.
### 4.Extract GameStop Revenue Data:

Scrape the revenue data for GameStop from a financial website and store it in a DataFrame.
Display the last five entries of the revenue data.
### 5.Visualize Tesla Stock Data:

Create a function to plot the Tesla stock price data over time using matplotlib.
Provide a title for the graph for better context.
### 6.Visualize GameStop Stock Data:

Utilize the same plotting function to visualize GameStop stock price data and give it an appropriate title.

## CODE
Step 1: Extract Tesla Stock Data
```
import yfinance as yf
import pandas as pd

# Download Tesla stock data
tesla_data = yf.download('TSLA', start='2020-01-01', end='2024-01-01')

# Reset index
tesla_data.reset_index(inplace=True)

# Save and display the first five rows
tesla_data.head()

```
Step 2: Extract Tesla Revenue Data
```
import requests
from bs4 import BeautifulSoup

# URL of the page with revenue data
url = 'https://www.example.com/tesla-revenue-data'
response = requests.get(url)

# Parse the HTML content
soup = BeautifulSoup(response.text, 'html.parser')

# Extract revenue data (adjust according to the actual HTML structure)
tables = soup.find_all('table')
tesla_revenue = pd.read_html(str(tables))[0]

# Display the last five rows
tesla_revenue.tail()
```
Step 3: Extract GameStop Stock Data
```
# Download GameStop stock data
gme_data = yf.download('GME', start='2020-01-01', end='2024-01-01')

# Reset index
gme_data.reset_index(inplace=True)

# Save and display the first five rows
gme_data.head()

```
Step 4: Extract GameStop Revenue Data
```
# URL of the page with revenue data
url = 'https://www.example.com/gamestop-revenue-data'
response = requests.get(url)

# Parse the HTML content
soup = BeautifulSoup(response.text, 'html.parser')

# Extract revenue data
tables = soup.find_all('table')
gme_revenue = pd.read_html(str(tables))[0]

# Display the last five rows
gme_revenue.tail()

```
Step 5: Visualize Tesla Stock Data
```
import matplotlib.pyplot as plt

def make_graph(data, title):
    plt.figure(figsize=(10, 5))
    plt.plot(data['Date'], data['Close'], label='Close Price')
    plt.title(title)
    plt.xlabel('Date')
    plt.ylabel('Price')
    plt.legend()
    plt.grid()
    plt.show()

# Plot Tesla Stock Data
make_graph(tesla_data, 'Tesla Stock Price')
```
Step 6: Visualize GameStop Stock Data
```
# Plot GameStop Stock Data
make_graph(gme_data, 'GameStop Stock Price')
```
## Conclusion
The analysis provides insights into the stock performance of Tesla and GameStop over the selected timeframe. The visualizations allow for a better understanding of trends and patterns in stock prices, which can assist investors and analysts in decision-making processes.
