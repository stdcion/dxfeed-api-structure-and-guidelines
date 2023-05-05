# Math Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/MathUtil.cs

## Description

A collection of static utility methods for mathematics. Used in mathematical calculations throughout the project. The
set of methods may vary depending on the capabilities of the programming language and the standard library. Additional
math is recommended to be put here.

Possible interfaces:

> Note, overflow is allowed in Abs method.

```csharp
/// <summary>
/// Method like a <see cref="Math.Abs(int)"/>, but not throws <see cref="OverflowException"/> exception,
/// when argument the argument is equal to the value of <see cref="int.MinValue"/>.
/// Returns the absolute value of an int value.
/// If the argument is not negative, the argument is returned.
/// If the argument is negative, the negation of the argument is returned.
/// Note that if the argument is equal to the value of <see cref="int.MinValue"/>,
/// the most negative representable int value, the result is that same value, which is negative.
/// </summary>
/// <param name="a">The argument whose absolute value is to be determined.</param>
/// <returns>The absolute value of the argument.</returns>
public static int Abs(int a);
```

```csharp
/// <summary>
/// Returns quotient according to number theory - i.e. when remainder is zero or positive.
/// </summary>
/// <param name="a">The dividend.</param>
/// <param name="b">The divisor.</param>
/// <returns>The quotient according to number theory.</returns>
public static int Div(int a, int b);
```

```csharp
/// <summary>
/// Returns the largest (closest to positive infinity) <see cref="long"/> value that is less than
/// or equal to the algebraic quotient.
/// There is one special case, if the dividend is the <see cref="long"/>.<see cref="long.MinValue"/>
/// and the divisor is <c>-1</c>,
/// then integer overflow occurs and the result is equal to the <see cref="long"/>.<see cref="long.MinValue"/>.
/// Normal integer division operates under the round to zero rounding mode (truncation).
/// This operation instead acts under the round toward negative infinity (floor) rounding mode.
/// The floor rounding mode gives different results than truncation when the exact result is negative.
/// </summary>
/// <param name="x">The dividend.</param>
/// <param name="y">The divisor.</param>
/// <returns>
/// The largest (closest to positive infinity) <see cref="long"/> value that is less than
/// or equal to the algebraic quotient.
/// </returns>
public static long FloorDiv(long x, long y);
```

```csharp
/// <summary>
/// Returns the floor modulus of the int arguments.
/// </summary>
/// <param name="x">The dividend.</param>
/// <param name="y">The divisor.</param>
/// <returns>
/// The floor modulus: <code>x - (FloorDiv(x, y) * y)</code>
/// </returns>
public static long FloorMod(long x, long y);
```

May come in handy:

```csharp
/// <summary>
/// Checks if the specified number is a power of two.
/// </summary>
/// <param name="x">The specified number.</param>
/// <returns>Returns <c>true</c> if x represents a power of two.</returns>
public static bool IsPowerOfTwo(long x);
```

```csharp
/// <summary>
/// Checks if the specified number is a -0.0 (negative zero).
/// </summary>
/// <param name="x">The specified number.</param>
/// <returns>Returns <c>true</c> if x is equals -0.0.</returns>
public static bool IsNegativeZero(double x);
```
