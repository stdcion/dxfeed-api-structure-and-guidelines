# TradeETH

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/TradeETH.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/TradeETH.cs

## Description

TradeETH event is a snapshot of the price and size of the last trade during
extended trading hours and the extended trading hours day volume and day turnover.
This event is defined only for symbols (typically stocks and ETFs) with a designated
extended trading hours (ETH, pre market and post market trading sessions).
It represents the most recent information that is available about
ETH last trade on the market at any given moment of time.
