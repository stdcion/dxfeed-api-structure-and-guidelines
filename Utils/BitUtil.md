# Bit Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Base
* Complexity: Low/High (language specific)

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/market/Util.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/BitUtil.cs

## Description

A collection of utility methods for bitwise operations.\
The set of methods may vary depending on the capabilities of the
programming language and the standard library.\
For example, C++ also requires the implementation of arithmetic bit
shifts, and bitwise operations on signed variables.\
Can be divided into whatever classes/macros/etc you like.

The minimum recommendation is to add methods for reading and writing bits by mask, extremely useful in market event
getters/setters:

```csharp
/// <summary>
/// Extracts bits from the specified value.
/// </summary>
/// <param name="value">The specified value.</param>
/// <param name="mask">The bit mask.</param>
/// <param name="shift">The bit shift.</param>
/// <returns>The extracted bits.</returns>
public static int GetBits(int value, int mask, int shift);
```

```csharp
/// <summary>
/// Sets bits to the specified value.
/// </summary>
/// <param name="value">The specified value.</param>
/// <param name="mask">The bit mask.</param>
/// <param name="shift">The bit shift.</param>
/// <param name="bits">The bits set.</param>
/// <returns>Returns a value with bits set.</returns>
public static int SetBits(int value, int mask, int shift, int bits);
```
