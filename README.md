# C# coding guideline

## Variables

- Use var in most cases
- Give the variable a meaningful name
- Do not use abbreviations
- The name should not contain type information
```csharp
// Yes
var numberOfWheels = 3;

// No
var intNumberOfWheels = 3;

// No
int numberOfWheels = 3;

// No
var foo = 3;

// No
var noWheels = 3;
```
