# String Util

* Type: Task
* Epic: Utils
* Required: Optional
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/StringUtils.cs

## Description

Provides utility methods for working with strings. The implementation is highly dependent on the programming language.
Could be implemented as extension methods, or something like that. This class is mainly used to implement the `ToString`
method of various objects. The main requirements, printing a string containing null should not raise an exception, but
output "null", and special output characters (print only ASCII, everything else as a UTF code point).

Possible interface:

```csharp
/// <summary>
/// Encodes specified nullable string.
/// If string equals null, returns <c>"null"</c> string; otherwise returns specified string.
/// </summary>
/// <param name="s">The specified string.</param>
/// <returns>Return specified string or <c>"null"</c> string.</returns>
public static string EncodeNullableString(string? s);
```

```csharp
/// <summary>
/// Encodes char to string.
/// If the value of char falls within the range of printable ASCII characters [32-126],
/// then returns a string containing that character, otherwise return unicode number <c>"(\uffff)"</c>.
/// For zero char returns <c>"\0"</c>.
/// </summary>
/// <param name="c">The char.</param>
/// <returns>Returns the encoded string.</returns>
public static string EncodeChar(char c);
```

```csharp
/// <summary>
/// Check that the specified char fits in the bit mask.
/// </summary>
/// <param name="c">The char.</param>
/// <param name="mask">The bit mask.</param>
/// <param name="name">The char name. Used in the exception message.</param>
/// <exception cref="ArgumentException">If the specified char dont fits in the mask.</exception>
public static void CheckChar(char c, int mask, string name);
```
