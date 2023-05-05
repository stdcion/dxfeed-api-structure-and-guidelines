# Event Code Attribute

* Type: Task
* Epic: Annotations
* Required: Optional
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Events/EventCodeAttribute.cs

## Description

Indicates that the attributed class contains event code native. Uses to map the corresponding event class (Quote, Trade,
etc.), to a event code native (a numeric representation). Can use caching to increase performance.

Possible interface:

```csharp
/// <summary>
/// Gets native event code.
/// </summary>
public EventCodeNative EventCode { get; }

/// <summary>
/// Gets native event codes from specified types.
/// </summary>
/// <param name="types">The specified types.</param>
/// <returns>Returns set containing native event codes.</returns>
/// <exception cref="ArgumentException">
/// If one on the specified type has no <see cref="EventCodeAttribute"/>.
/// </exception>
public static IEnumerable<EventCodeNative> GetEventCodes(params Type[] types);

/// <summary>
/// Gets native event code from specified type.
/// </summary>
/// <param name="type">The specified type.</param>
/// <returns>Returns native event code.</returns>
/// <exception cref="ArgumentException">If specified type has no <see cref="EventCodeAttribute"/>.</exception>
public static EventCodeNative GetEventCode(Type type);
```
