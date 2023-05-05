# Market Event

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/MarketEvent.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/MarketEvent.cs

## Description

Abstract base class for all market events. All market events are plain java objects that
extend this class. Market event classes are simple beans with setter and getter methods for their
properties and minimal business logic. All market events have eventSymbol property that is
defined by this class.
