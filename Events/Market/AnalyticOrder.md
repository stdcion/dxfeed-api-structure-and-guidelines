# Analytic Order

* Type: Task
* Epic: Events/Market
* Required: Mandatory
* Functional: Base
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/AnalyticOrder.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Market/AnalyticOrder.cs

## Description

Represents an extension of Order introducing analytic information, e.g. adding to this order iceberg related
information icebergPeakSize, icebergHiddenSize, icebergExecutedSize.
The collection of analytic order events of a symbol represents the most recent analytic information
that is available about orders on the market at any given moment of time.
