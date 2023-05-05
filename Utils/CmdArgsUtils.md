# Command Args Util

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: Medium

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/CmdArgUtil.cs

## Description

A collection of static helper methods for parses command-line arguments. A very useful class, it should contain the
logic for parsing user input, and then be used in all examples and/or tools. In the old API, this logic was constantly
duplicated in all examples, which was quite inconvenient.

Possible interfaces:

> Should be able to correctly parse strings like ` ,IBM,,AAPL{=d,tho=true}, ,MSFT{},`

```csharp
/// <summary>
/// Parses an input string and returns a set of symbols.
/// </summary>
/// <param name="symbols">The coma-separated list of symbols.</param>
/// <returns>Returns created a set of parsed symbols.</returns>
public static IEnumerable<string> ParseSymbols(string symbols);
```

> Should be able to correctly parse a comma-separated string, and check the existence of specified
> types (`Quote,Trade`).

```csharp
/// <summary>
/// Parses an input string and returns a set of event types.
/// </summary>
/// <param name="types">The coma-separated list of event types.</param>
/// <returns>Returns a set of parsed types.</returns>
/// <exception cref="ArgumentException">If the passed type is not available.</exception>
public static IEnumerable<Type> ParseTypes(string types);
```

> See [TimeFormat](TimeFormat.md).

```csharp
/// <inheritdoc cref="TimeFormat.Parse"/>
public static DateTimeOffset ParseFromTime(string fromTime);
```

> Useful for parsing key-value pairs. For example to set SystemProperties.

```csharp
/// <summary>
/// Parses the input collection of strings and returns a collection of key-value properties.
/// The input strings should look like comma-separated: "key=value".
/// </summary>
/// <param name="properties">The input comma-separated key-value pairs.</param>
/// <returns>Returns collection of key-value properties.</returns>
/// <exception cref="ArgumentException">If string has wrong format.</exception>
public static IReadOnlyDictionary<string, string> ParseProperties(string properties);
```
