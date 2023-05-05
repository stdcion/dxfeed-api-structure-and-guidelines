# Time Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxlib/src/main/java/com/devexperts/util/TimeUtil.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/TimeUtil.cs

## Description

A collection of static utility methods for manipulation of time measured in milliseconds since Unix epoch. Necessary for
implementation of getters/setters methods in event classes. The idea is to be able to extract separately seconds and
milliseconds from time measured in milliseconds since the Unix epoch.

Possible interfaces:

```csharp
/// <summary>
/// Returns correct number of seconds with proper handling negative values and overflows.
/// Idea is that number of milliseconds shall be within [0..999] interval
/// so that the following equation always holds:
/// <code>GetSecondsFromTime(timeMillis) * 1000L + GetMillisFromTime(timeMillis) == timeMillis</code>
/// as as long the time in seconds fits into <see cref="int"/>.
/// <seealso cref="GetMillisFromTime(long)"/>
/// </summary>
/// <param name="timeMillis">The time measured in milliseconds since Unix epoch.</param>
/// <returns>The number of seconds.</returns>
public static int GetSecondsFromTime(long timeMillis);
```

```csharp
/// <summary>
/// Returns correct number of milliseconds with proper handling negative values.
/// Idea is that number of milliseconds shall be within [0..999] interval
/// so that the following equation always holds:
/// <code>GetSecondsFromTime(timeMillis) * 1000L + GetMillisFromTime(timeMillis) == timeMillis</code>
/// as as long the time in seconds fits into <see cref="int"/>.
/// <seealso cref="GetSecondsFromTime(long)"/>
/// </summary>
/// <param name="timeMillis">The time measured in milliseconds since Unix epoch.</param>
/// <returns>The number of milliseconds.</returns>
public static int GetMillisFromTime(long timeMillis)
```
