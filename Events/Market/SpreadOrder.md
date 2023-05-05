# Spread Order

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/SpreadOrder.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/SpreadOrder.cs

## Description

Spread order event is a snapshot for a full available market depth for all spreads
on a given underlying symbol. The collection of spread order events of a symbol
represents the most recent information that is available about spread orders on
the market at any given moment of time.
