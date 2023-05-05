# TheoPrice

* Type: Task
* Epic: Events/Options
* Required: Mandatory
* Functional: Base
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/option/TheoPrice.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/Option/TheoPrice.cs

## Description

Theo price is a snapshot of the theoretical option price computation that is
periodically performed by [dxPrice](http://www.devexperts.com/en/products/price.html) model-free computation.
It represents the most recent information that is available about the corresponding
values at any given moment of time.
The values include first and second order derivative of the price curve by price, so that
the real-time theoretical option price can be estimated on real-time changes of the underlying
price in the vicinity.
