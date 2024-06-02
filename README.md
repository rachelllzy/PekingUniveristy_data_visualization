# Flight Data Visualization Analysis

This repository contains a Jupyter Notebook that performs a comprehensive analysis and visualization of flight data. The primary focus is on data cleaning, preprocessing, and visualization to derive insights about flight prices, schedules, and airline performance.

## Table of Contents

- [Visualization](#Visualization)
- [Installation](#installation)
- [Usage](#usage)
- [Data Preprocessing](#data-preprocessing)
  - [Handling Time Data](#handling-time-data)
  - [Handling Price Data](#handling-price-data)
- [Visualization](#visualization)
  - [Route Analysis](#route-analysis)
  - [Airline Market Share](#airline-market-share)
  - [Price Distribution](#price-distribution)
  - [Departure Time Analysis](#departure-time-analysis)
  - [Price Analysis by Airline](#price-analysis-by-airline)
  - [Destination Price Analysis](#destination-price-analysis)
- [Conclusion](#conclusion)

## Visualization

### 文献类型的时间变化
![文献类型的时间变化](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%201.png?raw=true)

### 期刊种类的时间变化趋势
![期刊种类的时间变化趋势](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%202.png?raw=true)

### 期刊类型分段堆叠折线图
![期刊类型分段堆叠折线图](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%203.png?raw=true)

### 文献页数类型与发表时间的关系
![文献页数类型与发表时间的关系](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%204.png?raw=true)
![文献页数类型与发表时间的关系2](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%205.png?raw=true)

### 全球文献数量的地理分布
![全球文献数量的地理分布](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%206.png?raw=true)

### 文献作者词云
![文献作者词云](https://github.com/rachelllzy/PekingUniveristy_data_visualization/blob/main/img/%E5%9B%BE%E7%89%87%207.png?raw=true)

## Installation

To run the notebook, you need to have Python and Jupyter Notebook installed. Additionally, you need to install the following Python libraries:

```bash
pip install pandas numpy seaborn matplotlib pyecharts
```

## Usage

Open the Jupyter Notebook and run the cells sequentially to reproduce the analysis. The notebook includes comments and markdown cells to guide you through each step of the analysis.

## Data Preprocessing

### Handling Time Data

1. **Remove "+1 day" from Arrival Time:**
    ```python
    arrivetime_list = []
    for arrivetime in df["抵达时间"]:
        arrivetime_list.append(arrivetime.split(' ')[0])
    df['抵达时间'] = arrivetime_list
    ```

2. **Convert Departure and Arrival Time to datetime type:**
    ```python
    df["出发时间"] = pd.to_datetime(df["出发时间"])
    df["抵达时间"] = pd.to_datetime(df["抵达时间"])
    ```

### Handling Price Data

1. **Remove currency symbol (￥) from prices:**
    ```python
    price_list = []
    for price in df["机票价格"]:
        price_list.append(re.sub('[￥]', '', price))
    df['机票价格'] = price_list
    ```

2. **Retain only numeric part and convert to int:**
    ```python
    price_list2 = []
    for price in df["机票价格"]:
        price_list2.append(re.sub("\\D", "", price))
    df['机票价格'] = price_list2
    df['机票价格'] = df['机票价格'].astype('int')
    ```

## Visualization

### Route Analysis

- Analyze the number of flights for different routes using bar charts.
- Determine the busiest routes.

### Airline Market Share

- Visualize the market share of different airlines using pie charts.
- Compare the proportion of flights operated by each airline.

### Price Distribution

- Use histograms to analyze the distribution of flight prices.
- Identify price ranges and outliers.

### Departure Time Analysis

- Plot the relationship between departure times and flight prices using scatter plots.
- Determine the impact of departure time on ticket prices.

### Price Analysis by Airline

- Use box plots to compare ticket prices across different airlines.
- Identify airlines with higher or more variable pricing.

### Destination Price Analysis

- Create maps to visualize the average flight prices to different destinations.
- Identify regions with higher or lower average prices.

## Conclusion

This notebook provides a detailed analysis of flight data over a certain period. The key findings are:

1. **Flight Frequency:**
    - Major cities like Beijing, Chengdu, and Shenzhen serve as major air traffic hubs.
  
2. **Price Factors:**
    - Flight prices are influenced by departure time and destination, with early or late flights being cheaper and popular destinations being more expensive.
  
3. **Airline Comparison:**
    - Southern Airlines, China Airlines, Eastern Airlines, Xiamen Airlines, and Sichuan Airlines have significant market shares. Sichuan Airlines tends to have the highest ticket prices, while other airlines show less price variation.

This analysis helps in understanding the factors affecting flight prices and the market dynamics of different airlines.
