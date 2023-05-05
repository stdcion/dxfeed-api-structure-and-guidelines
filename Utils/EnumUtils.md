# Enum Util

* Type: Task
* Epic: Utils
* Required: Optional
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/EnumUtils.cs

## Description

Provides utility methods for manipulating `Enum`. The need depends on the programming language. Can be useful to safely
convert an integer to an enumeration, or to construct an array containing all enumeration values, to increase conversion
performance. 

Possible interface:

```csharp
/// <summary>
/// Returns an enum constant of the specified enum type with the specified value,
/// or throws <see cref="ArgumentException"/> if the specified enum type does not have
/// a constant with the specified value.
/// </summary>
/// <param name="value">The specified value.</param>
/// <typeparam name="T">The specified enum type.</typeparam>
/// <returns>An enum constant of the specified enum type with the specified value.</returns>
/// <exception cref="ArgumentException">
/// If the specified enum type does not have a constant with the specified value.
/// </exception>
public static T ValueOf<T>(T value);

/// <summary>
/// Returns an enum constant of the specified enum type with the specified value,
/// or a default value if the specified enum type does not have
/// a constant with the specified value.
/// </summary>
/// <param name="value">The specified value.</param>
/// <param name="defaultValue">The default enum value.</param>
/// <typeparam name="T">The specified enum type.</typeparam>
/// <returns>
/// The enum constant of the specified enum type with the specified value
/// or default value, if specified enum type has no constant with the specified value.
/// </returns>
public static T ValueOf<T>(T value, T defaultValue);

/// <summary>
/// Gets the number of values for the specified enum type.
/// </summary>
/// <typeparam name="T">The specified enum type.</typeparam>
/// <returns>Returns the number of values of the specified enum type.</returns>
public static int GetCountValues<T>();

/// <summary>
/// Creates an array containing elements of the specified enum type T,
/// where the length of the array is rounded to the nearest power of two,
/// which is greater than or equal to the number of enum values.
/// If the calculated length is greater than the number of enum values,
/// the remaining elements are filled with a default value.
/// The idea is to quickly convert an <c>int</c> value to an enum value, simply by array index.
/// But the size of the array is limited by a bit mask, so if the number of enum values
/// is not a multiple of a power of two, you need to expand the array and fill in new elements with a default value.
/// </summary>
/// <param name="defaultValue">
/// The default value that will fill the elements of an array
/// if its size is greater than the number of enum values.
/// </param>
/// <typeparam name="T">The specified enum type.</typeparam>
/// <returns>The created array.</returns>
/// <remarks>
/// The elements of the array are sorted by the binary values of the enumeration constants
/// (that is, by their unsigned magnitude).
/// </remarks>
/// <seealso cref="CreateEnumArrayByValue{T}"/>
public static T[] CreateEnumBitMaskArrayByValue<T>(T defaultValue);

/// <summary>
/// Creates an array containing elements of the specified enum type T, of the specified length.
/// If the length is greater than the number of enum values,
/// the remaining elements are filled with a default value, otherwise array are truncated.
/// </summary>
/// <param name="defaultValue">
/// The default value that will fill the elements of an array if its size is greater than the number of enum values.
/// </param>
/// <param name="length">The length of result array.</param>
/// <typeparam name="T">The specified enum type.</typeparam>
/// <returns>The created array.</returns>
/// <exception cref="ArgumentException">If length is less than zero.</exception>
/// <remarks>
/// The elements of the array are sorted by the binary values of the enumeration constants
/// (that is, by their unsigned magnitude).
/// </remarks>
public static T[] CreateEnumArrayByValue<T>(T defaultValue, int length);
```
