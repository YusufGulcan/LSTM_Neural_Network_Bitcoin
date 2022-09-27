# LSTM_Neural_Network_Bitcoin
## Introduction
In this project, I gathered tweets from Twitter, search trends from Google and historical prices form Binance to predict Bitcoin price using LSTM Neural Network.

The tweets are processed with the VADER sentiment analysis model and converted into numerical sentiment values. 
Sentiment analysis results,Google search trends values and Bitcoin historical price data are merged into one data frame and used as input. 

I used APIs and created pipelines to keep both the data and predictions up to date. The data is consisted 1500 rows, each representing 1 day. The features are 

## Libraries and Dependencies
- python-binance  - Bitcoin Prices 
- Pytrends -  Google Search Trends
- snscrape - Tweets about Bitcoin
- vaderSentiment -  Sentiment Analysis
- sklearn - metrics
- tensorflow.keras - LSTM Neural Network
- seaborn - Visualization
- matplot - Visualization 

## Roadmap 
![1_ExPBFmE3cvOSynz9MIG9ug](https://user-images.githubusercontent.com/105684729/192462618-66757c89-dbc2-45b1-909c-8035ddad10a0.png)

- Collect Data From Different Sources
- Prepare the Collected Data For Merge
- Merge the Data Frames and Optimize for Modeling
- Create an LSTM Neural Network Model and Tune 
- Evaluate the Model

### Collect Data From Different Sources:
**Google Trends:**
I used the pytrends library for this task. The data is collected for each day. 
The range of ratings is 0-100. 
![image](https://user-images.githubusercontent.com/105684729/192492631-238b06b0-b0ed-4b00-850b-11baffff55a0.png)


**Twitter**
There are infinite number of spam tweets about Bitcoin, I had to filter them by the like counts. I only collected the tweets with
supporters. This helped me increase the quality level of data and lower the time spent for the process.
The tweets ranging from 1500 days before to the current date is collected.

**Binance**
Binance API provides a broad range of data but requires API key and secret key. The API offers data for different time intervals(1hour-4hours-1day,etc.)
I collected daily data for the same date range as others.

### Preprocess
The dataframes were collected on the same date range, so the data was mostly matching. Some duplicated rows are removed and data types are optimized.

Tweets are processed by using Vader Sentiment analysis algorithm and converted into numerical value. 

![image](https://user-images.githubusercontent.com/105684729/192493471-35c81875-fc32-4e21-b412-8c71101b4b0a.png)

Date columns are synced and the data frames are merged. 

### Pre-Modelling

The data is prepared for LSTM layer. The structure is as following;
The distinct feature number is 3. Each row consists of a data matrix which includes inputs of the previous 7 days.
There are 14 * 3 pieces of info per row.

After defining the matrix shape, the data frame is split into 3 as train,validation and test. Size for each partition

- Train data = 1200 rows
- Validation data = 150 rows
- Test data = 150 rows

### Model
The task is time-series forecast, so I used a compatible node type, Long Short Term Memory(LSTM). After experimenting different
combinations of node and layer numbers, finally the structure is created.
 
 Number of nodes: 7--> LSTM(40)--> Dense(20)--> Dense(10)--> Dense(1) 

![rsz_11_ihe5e2t3ethxhgej8_ovzw](https://user-images.githubusercontent.com/105684729/192506217-516ad8b4-1d68-4452-bbee-0903620f6d92.png)

### Evaluation 

The resulst were promising, the several metric scores on test data; 

- Mean Squared Error = 1662883.3744117657
- Root Mean Squared Error = 1289.5283534733796
- Mean Absolute Error = 963.5478927083333
- Mean Absolute Percentage Error = 0.037823230303446066
- R2 Score = 0.9482121547584226

### Further Improvements

Model parameters could be tuned better with more sensitivity.
Data could be extended by adding economic variables like FED interest rates, money supply and consumer trus index. 

























