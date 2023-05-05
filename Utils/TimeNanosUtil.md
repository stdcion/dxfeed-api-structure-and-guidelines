# Time Nanos Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/impl/TimeNanosUtil.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/TimeNanosUtil.cs

## Description

A collection of static utility methods for manipulation of time measured in nanoseconds since Unix epoch. Necessary for
implementation of getters/setters methods in event classes. The idea is to be able to extract nano part from time.

Possible interfaces:

```csharp
/// <summary>
/// Returns time measured in nanoseconds since Unix epoch from the time in milliseconds and its nano part.
/// The result of this method is <c>timeMillis * 1_000_000 + timeNanoPart</c>.
/// </summary>
/// <param name="timeMillis">The time in milliseconds since Unix epoch.</param>
/// <param name="timeNanoPart">The nanoseconds part that shall lie within [0..999999] interval.</param>
/// <returns>The time measured in nanoseconds since Unix epoch.</returns>
public static long GetNanosFromMillisAndNanoPart(long timeMillis, int timeNanoPart);
```

```csharp
/// <summary>
/// Returns time measured in milliseconds since Unix epoch from the time in nanoseconds.
/// Idea is that nano part of time shall be within [0..999999] interval
/// so that the following equation always holds:
/// <code>GetMillisFromNanos(timeNanos) * 1_000_000 + GetNanoPartFromNanos(timeNanos) == timeNanos</code>
/// <seealso cref="GetNanoPartFromNanos(long)"/>
/// </summary>
/// <param name="timeNanos">The time measured in nanoseconds since Unix epoch.</param>
/// <returns>The time measured in milliseconds since Unix epoch.</returns>
public static long GetMillisFromNanos(long timeNanos);
```

```csharp
/// <summary>
/// Returns nano part of time.
/// Idea is that nano part of time shall be within [0..999999] interval
/// so that the following equation always holds:
/// <code>GetMillisFromNanos(timeNanos) * 1_000_000 + GetNanoPartFromNanos(timeNanos) == timeNanos</code>
/// <seealso cref="GetMillisFromNanos(long)"/>
/// </summary>
/// <param name="timeNanos">The time measured in nanoseconds since Unix epoch.</param>
/// <returns>The time measured in milliseconds since Unix epoch.</returns>
public static int GetNanoPartFromNanos(long timeNanos);
```
