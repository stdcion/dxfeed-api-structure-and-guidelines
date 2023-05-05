# Order Source

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/OrderSource.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/OrderSource.cs

## Description

Identifies source of Order, AnalyticOrder and SpreadOrder. Сonverts order source id to string representation and back,
it is desirable to implement caching.
