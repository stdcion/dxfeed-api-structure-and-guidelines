# Option Sale

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/OptionSale.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/OptionSale.cs

## Description

Option Sale event represents a trade or another market event with the price
(for example, market open/close price, etc.) for each option symbol listed under the specified Underlying.
Option Sales are intended to provide information about option trades in a continuous time slice with
the additional metrics, like Option Volatility, Option Delta, and Underlying Price.
