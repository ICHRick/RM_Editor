## Problem Statement

You're given the history price data for several crypto currencies.
The data indicate the prices of the currency for a given time.

Given a crypto currency and a time window, if you can only buy/sell it one time,
find the best timing for the buy/sell within the time window so that we can make the greatest profit.

For example, if we have the following data for a certain currency:

```
t1, 35.3
t2, 32.5
t3, 33.8
t4, 38.2
t5, 31.0
t6, 40.5
t7, 42.9
t8, 41.0
```

Given the time window `t1` to `t8`, the best timing would be `t5 to t7`

## Algorithm 

1. For the given parameters (currency name), the program read data with `Unix Timestamp`, `Date`, and `Close` corresponding to time and price.

2. According to the given time (start and end time), we select data in the valid time period in the form of the example of the problem.

3. To find the best two trade time (buy/sell) for the maximum profit, we need to find an increasing trend with a maximum difference. If we find that a point starts from a lower price and the price is increasing, we can compare the profit for each point and the past one. Therefore, we only need to set two variables `min_price` and `max_profit` to record the new low-price point and check if the profit is higher in the following timestamps.

4. After we check each timestamp, we return `max_profit`, start/end time point corresponding to `max_profit` as the buy/sell time.

## Complexity Analysis

Time complexity: 

The valid timestamp would be check once, and the time complexity is O(n).

Space complexity: 

We storage `min_price`, `max_profit`, and the corresponding timestamps, only constant-number variables are used. That is O(1).

## Development Environment
The algorithm is implemented by Python3.6 with requirements: 

  * dask==2021.1.1

  * numpy==1.19.5

  * pandas==1.1.5

  * pyinstaller==4.2

The usage of the scipt `suggest-time.py` is like follows:
```
python suggest-time.py <window-start-time> <window-end-time> <currency-name>
```

To pack the script and some dependencies, the module `pyinstaller` can build `suggest-time.py` as an executable file.
```
pyinstaller -F suggest-time.py
```

Besides the `suggest-time.py`, the files in the folder `source code` are log and debug files for `pyinstaller`.

Note that the folder 'suggest-time' is the unpacked version of the program including the main program `suggest-time` and dependencies.
