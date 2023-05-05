# CandleSymbol

* Type: Task
* Epic: Events/Candles
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: High

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Candles/CandleSymbol.cs

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/candle/CandleSymbol.java

## Description

Symbol that should be used with DXFeedSubscription class to subscribe for Candle events. DXFeedSubscription also accepts
a string representation of the candle symbol for subscription.

To implement this class, you will need to implement all of the following parts:
* CandleAlignment
* CandleExchange
* CandlePeriod
* CandlePrice
* CandlePriceLevel
* CandleSession
* CandleSymbolAttribute
* CandleType
* MarketEventSymbol
