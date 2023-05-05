# Time Period

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Advanced
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxlib/src/main/java/com/devexperts/util/TimePeriod.java

## Description

Value class for period of time with support for [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) duration format,
like `P3Y6M4DT12H30M5S`. Depending on the programming language, you can use a conversion to a convenient class from
standard library, such as `TimeSpan` or `std::chrono::duration`. Very useful to handle user input, e.g. transfer `-P5D`
at from-time arguments, which means to set the from-time as minus 5 days from the current date.

The general format for time periods is based on ISO8601 duration format: "PdDThHmMsS" (which means a period of
d - days, h - hours, m - minutes, s - seconds) Also little simplifications and modifications available:

* Letters are case insensitive.
* Letters 'P' and 'T' can be omitted.
* Letter 'S' can be also omitted. In this case last number will be supposed to be seconds.
* Number of seconds can be fractional. So it is possible to define duration accurate within milliseconds.
* Every part can be omitted. In this case it is supposed that it's value is zero.
