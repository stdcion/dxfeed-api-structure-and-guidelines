# Time Format

* Type: Task
* Epic: Utils
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: High

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxlib/src/main/java/com/devexperts/util/TimeFormat.java

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/TimeFormat.cs

## Description

Utility class for parsing and formatting dates and times in ISO-compatible format. Quite a complex module, which can
have different implementations.

The functionality consists of two parts, the first part is the date output in a
configurable format (with or without milliseconds, with or without time zone), must have the functionality to set the
time zone in which to output the date. The second part is parsing the date in different formats (both text and
milliseconds after the UTC epoch). The second part of the functionality can be deferred for later.

The implementation that is used in Java is quite complex but performance at the same time, it seems that there is no
point in trying to replicate it one-to-one.

### Output and formatting

> An implementation may contain three lazy singletons for predefined time zones, Local, UTC and Default (is configured
> using the properties, by default is Local). The choice of time zone determines in which time zone the date format will
> be displayed, and in which time zone the date will be parsed.

```csharp
/// <summary>
/// Gets instance <see cref="TimeFormat"/> with <see cref="TimeZoneInfo"/>.<see cref="TimeZoneInfo.Local"/>.
/// </summary>
public static TimeFormat Local;
```

```csharp
/// <summary>
/// Gets instance <see cref="TimeFormat"/> with <see cref="TimeZoneInfo"/>.<see cref="TimeZoneInfo.Utc"/>.
/// </summary>
public static TimeFormat Utc;
```

```csharp
/// <summary>
/// Gets instance <see cref="TimeFormat"/> with customizable time zone(<see cref="TimeZoneInfo.Local"/> by default).
/// </summary>
public static TimeFormat Default;
```

> The user can create his own instance with a specified time zone.

```csharp
/// <summary>
/// Creates a new instance of <see cref="TimeFormat"/>
/// with a specified <see cref="TimeZoneInfo"/> and <see cref="DefaultFormat"/>.
/// </summary>
/// <param name="timeZone"> The specified <see cref="TimeZoneInfo"/>. </param>
/// <returns>Returns new instance <see cref="TimeFormat"/>.</returns>
public static TimeFormat Create(TimeZoneInfo timeZone);
```

```csharp
/// <summary>
/// Creates a new instance of <see cref="TimeFormat"/>
/// with a specified <see cref="TimeZoneInfo"/> encapsulates
/// in <see cref="Func{TResult}"/> and <see cref="DefaultFormat"/>.
/// The <see cref="TimeZoneInfo"/>  is made as a func because, you should always access
/// the local time zone through the TimeZoneInfo.Local (same for TimeZoneInfo.Utc) property rather
/// than assigning the local time zone to a TimeZoneInfo object variable.
/// </summary>
/// <param name="timeZone">
/// The specified <see cref="TimeZoneInfo"/> encapsulates in <see cref="Func{TResult}"/>.
/// </param>
/// <returns>Returns new instance <see cref="TimeFormat"/>.</returns>
public static TimeFormat Create(Func<TimeZoneInfo> timeZone)
```

> The output of the string representation of the date, can be configured separately.

```csharp
/// <summary>
/// Adds milliseconds to the current format string.
/// </summary>
/// <returns>Returns <see cref="TimeFormat"/>.</returns>
/// <example>19700101-000000.000.</example>
public TimeFormat WithMillis();
```

```csharp
/// <summary>
/// Adds Time Zone to the current format string.
/// </summary>
/// <returns>Returns <see cref="TimeFormat"/>.</returns>
/// <example>19700101-000000+00:00.</example>
public TimeFormat WithTimeZone();
```

```csharp
/// <summary>
/// Sets the current format as Only Date.
/// </summary>
/// <returns>Returns <see cref="TimeFormat"/>.</returns>
/// <example>19700101.</example>
public TimeFormat AsOnlyDate();
```

```csharp
/// <summary>
/// Sets the current format as Full Iso.
/// </summary>
/// <returns>Returns <see cref="TimeFormat"/>.</returns>
/// <example>1970-01-01T00:00:00.0000000+00:00.</example>
public TimeFormat AsFullIso();
```

> And a set of methods to format the date. Can be expanded.

```csharp
/// <summary>
/// Converts the value in seconds since Unix epoch
/// to its equivalent string representation using the current format <see cref="CreateFormatString()"/>,
/// current <see cref="TimeZoneInfo"/> and <see cref="InvariantCulture"/>.
/// </summary>
/// <param name="timeSeconds">The time measured in seconds since Unix epoch.</param>
/// <returns>The string representation of the date, or <c>"0"</c> if timeSeconds is <c>0</c>.</returns>
public string FormatFromSeconds(long timeSeconds);
```

```csharp
/// <summary>
/// Converts the value in milliseconds since Unix epoch
/// to its equivalent string representation using the current format <see cref="CreateFormatString()"/>,
/// current <see cref="TimeZoneInfo"/> and <see cref="InvariantCulture"/>.
/// </summary>
/// <param name="timeMillis">The time measured in milliseconds since Unix epoch.</param>
/// <returns>The string representation of the date, or <c>"0"</c> if timeMillis is <c>0</c>.</returns>
public string FormatFromMillis(long timeMillis);
```

```csharp
/// <summary>
/// Converts the value of the specified <see cref="DateTimeOffset"/> object
/// to its equivalent string representation using the current format <see cref="CreateFormatString()"/>,
/// current <see cref="TimeZoneInfo"/> and <see cref="InvariantCulture"/>.
/// </summary>
/// <param name="dateTimeOffset">The <see cref="DateTimeOffset"/> object.</param>
/// <returns>The string representation.</returns>
public string Format(DateTimeOffset dateTimeOffset);
```

### Parsing date

> Is mainly used for parsing data that has been entered by the user. It has great flexibility and can try to parse data
> in different formats, including milliseconds since the UTC epoch or period in ISO8601.

```csharp
/// <summary>
/// Converts the specified string representation of a date and time
/// to its <see cref="DateTimeOffset"/> in current <see cref="TimeZoneInfo"/>
/// and <see cref="InvariantCulture"/>.
/// If no time zone is specified in the parsed string, the string is assumed to denote a local time,
/// and converted to current <see cref="TimeZoneInfo"/>.
/// <br/>
/// It accepts the following formats.
/// <br/>
/// <ul>
///     <li>
///         <b><tt>0</tt></b> is parsed as zero time in UTC.
///     </li>
///     <li>
///         <b><tt>&lt;long-value-in-milliseconds&gt;</tt></b>
///         The value in milliseconds since Unix epoch since Unix epoch.
///         It should be positive and have at least 9 digits
///         (otherwise it could not be distinguished from date in format <tt>'yyyymmdd'</tt>).
///         Each date since 1970-01-03 can be represented in this form.
///     </li>
///     <li>
///         <b><tt>&lt;date&gt;[&lt;time&gt;][&lt;timezone&gt;]</tt></b>
///         If time is missing it is supposed to be <tt>'00:00:00'</tt>.
///     </li>
/// </ul>
///  <ul>
///     <li>
///         <b>&lt;date&gt;</b> is one of:
///         <ul>
///             <li><b><tt>yyyy-MM-dd</tt></b></li>
///             <li><b><tt>yyyyMMdd</tt></b></li>
///         </ul>
///     </li>
///     <li>
///         <b>&lt;time&gt;</b> is one of:
///         <ul>
///             <li><b><tt>HH:mm:ss[.sss]</tt></b></li>
///             <li><b><tt>HHmmss[.sss]</tt></b></li>
///         </ul>
///     </li>
///     <li>
///         <b>&lt;timezone&gt;</b> is one of:
///         <ul>
///             <li><b><tt>[+-]HH:mm</tt></b></li>
///             <li><b><tt>[+-]HHmm</tt></b></li>
///             <li><b><tt>Z</tt></b> for UTC.</li>
///         </ul>
///     </li>
/// </ul>
/// </summary>
/// <param name="value">The input value for parse.</param>
/// <returns>Returns <see cref="DateTimeOffset"/> parsed from input value.</returns>
/// <exception cref="ArgumentException">If input value has wrong format.</exception>
public DateTimeOffset Parse(string value)
```
