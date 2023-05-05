# Day Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxlib/src/main/java/com/devexperts/util/DayUtil.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/DayUtil.cs

## Description

A collection of static utility methods for manipulation of integer day id,
that is the number of days since Unix epoch of January 1, 1970. You can simply port the Java code.

Possible interfaces:

```csharp
/// <summary>
/// Returns day identifier for specified year, month and day in Gregorian calendar.
/// The day identifier is defined as the number of days since Unix epoch of January 1, 1970.
/// Month must be between 1 and 12 inclusive.
/// Year and day might take arbitrary values assuming proleptic Gregorian calendar.
/// The value returned by this method for an arbitrary day value always satisfies the following equality:
/// <code>
/// GetDayIdByYearMonthDay(year, month, day) == GetDayIdByYearMonthDay(year, month, 0) + day
/// </code>
/// </summary>
/// <param name="year">The year.</param>
/// <param name="month">The month between 1 and 12 inclusive.</param>
/// <param name="day">The dat.</param>
/// <returns>The day id.</returns>
/// <exception cref="ArgumentException">f the month is less than 1 or greater than 12.</exception>
public static int GetDayIdByYearMonthDay(int year, int month, int day);
```

```csharp
/// <summary>
/// Returns day identifier for specified <c>yyyymmdd</c>  integer in Gregorian calendar.
/// The day identifier is defined as the number of days since Unix epoch of January 1, 1970.
/// The <c>yyyymmdd</c>  integer is equal to <c>yearSign * (abs(year) * 10000 + month * 100 + day)</c>,
/// where year, month, and day are in Gregorian calendar,
/// month is between 1 and 12 inclusive, and day is counted from 1.
/// </summary>
/// <param name="yyyymmdd">The <c>yyyymmdd</c> integer in Gregorian calendar.</param>
/// <returns>The day id.</returns>
/// <seealso cref="GetDayIdByYearMonthDay(int,int,int)"/>
/// <example>
/// <code>
/// DayUtil.GetDayIdByYearMonthDay(19691231) == -1
/// DayUtil.GetDayIdByYearMonthDay(19700101) ==  0
/// DayUtil.GetDayIdByYearMonthDay(19700102) ==  1
/// </code>
/// </example>
public static int GetDayIdByYearMonthDay(int yyyymmdd);
```

```csharp
/// <summary>
/// Gets <c>yyyymmdd</c> integer in Gregorian calendar for a specified day identifier.
/// The day identifier is defined as the number of days since Unix epoch of January 1, 1970.
/// The result is equal to:
/// <code>yearSign * (abs(year) * 10000 + month * 100 + day)</code>
/// where year, month, and day are in Gregorian calendar,
/// month is between 1 and 12 inclusive, and day is counted from 1.
/// </summary>
/// <param name="dayId">A number of whole days since Unix epoch of January 1, 1970.</param>
/// <returns>The <c>yyyymmdd</c> integer in Gregorian calendar.</returns>
/// <example>
/// <code>
/// DayUtil.GetYearMonthDayByDayId(-1) == 19691231
/// DayUtil.GetYearMonthDayByDayId(0)  == 19700101
/// DayUtil.GetYearMonthDayByDayId(1)  == 19700102
/// </code>
/// </example>
public static int GetYearMonthDayByDayId(int dayId)
```
