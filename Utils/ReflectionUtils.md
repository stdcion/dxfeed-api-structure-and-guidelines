# Reflection Util

* Type: Task
* Epic: Utils
* Required: Optional
* Functional: Pre-Advanced
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net/Utils/ReflectionUtil.cs

## Description

A simple utility class for working with the reflection API. Used to manipulate types. The need depends on the
programming language. Can be very useful, e.g. to get all interface implementations (find all available market event
implementations), to process user input (find market event class by input string) etc.

Possible interface:

```csharp
/// <summary>
/// Gets all inherited types form the specified type,
/// and creates a coma-separated string with types names.
/// Abstract classes and interfaces ignored.
/// </summary>
/// <param name="type">The specified type.</param>
/// <returns>Returns comma-separated string with inherited types.</returns>
/// <exception cref="NullReferenceException">If cannot find specified type.</exception>
public static string GetInheritedTypesString(Type type);

/// <summary>
/// Creates a coma-separated string with types names from types enumerable.
/// </summary>
/// <param name="types">The specified types.</param>
/// <returns>Returns comma-separated string with inherited types.</returns>
public static string CreateTypesString(IEnumerable<Type> types);

/// <summary>
/// Creates a coma-separated string with types names from types dictionary.
/// </summary>
/// <param name="types">The specified types.</param>
/// <returns>Returns comma-separated string with inherited types.</returns>
public static string CreateTypesString(IDictionary<string, Type> types);

/// <summary>
/// Gets all inherited types form the specified type,
/// and creates a dictionary where the key is the type name and value is the type.
/// Abstract classes and interfaces ignored.
/// </summary>
/// <param name="type">The specified type.</param>
/// <returns>Returns dictionary with inherited types.</returns>
/// <exception cref="NullReferenceException">If cannot find specified type.</exception>
public static IDictionary<string, Type> GetInheritedTypesDictionary(Type type);

/// <summary>
/// Creates a dictionary from specified types where the key is the type name and value is the type.
/// </summary>
/// <param name="types">The specified types.</param>
/// <returns>Returns dictionary with inherited types.</returns>
public static IDictionary<string, Type> CreateTypesDictionary(IEnumerable<Type> types);

/// <summary>
/// Gets all inherited types form the specified type.
/// Abstract classes and interfaces ignored.
/// </summary>
/// <param name="type">The specified type.</param>
/// <returns>Returns enumerable with inherited types.</returns>
/// <exception cref="NullReferenceException">If cannot find specified type.</exception>
public static IEnumerable<Type> GetInheritedTypes(Type type);
```