# Time and Sale

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/TimeAndSale.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/TimeAndSale.cs

## Description

Time and Sale represents a trade or other market event with price, like market open/close price, etc.
Time and Sales are intended to provide information about trades in a continuous time slice
(unlike Trade events which are supposed to provide snapshot about the current last trade).
