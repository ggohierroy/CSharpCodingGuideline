# C# coding guideline

## Variables

- Use var in most cases.

> Why? Cleaner. Shorter.

```csharp
// Yes
var provincesByCountry = new Dictionary<string, List<string>>();

// No
Dictionary<string, List<string>> provincesByCountry = new Dictionary<string, List<string>>();
```

- Give the variable a meaningful name.
- Do not use abbreviations.

> Why? To **easily** determine what the variable represents by looking at the name.

```csharp
// Yes
var numberOfWheels = 3;

// No
var foo = 3;

// No
var noWheels = 3;
```

- Do not rely on the variable name to specify the type of the variable.

> Why? The type should be changeable without having to rename the variable since the type is an implementation detail.

```csharp
// Yes
var numberOfWheels = 3;

// No
var intNumberOfWheels = 3;
```

## Methods

- Return the most specific types and accept the most generic ones.

> Why? To make the method usable for a larger number of input parameters, and to easily determine the exact return type.

```csharp
// Yes
public List<int> GetNumbers(IEnumerable idList)
{
  ...
}

// No
public IEnumerable GetNumbers(List<int> idList)
{
  ...
}
```

## Comments

- Place the comment on a separate line, not at the end of a line of code.
- Begin comment text with an uppercase letter.
- End comment text with a period.
- Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.

```csharp
// Yes
// The following declaration creates a query. It does not run
// the query.

// No
//teh following iz comment
```

## Packages

- Always manage packages using Nuget at the solution level.

> Why? To make sure all projects use the same version of the package.

- Never check-in packages into TFS.

> Why? To save space on TFS.

## Configuration Files

- Always use custom configuration sections
- Do not use AppSettings

> Why? To be able to use strongly-typed settings, as well as default values and required settings.

## Entity Framework

- Filtering out deleted records

```csharp
// Yes
var car = db.Cars.FirstOrDefault(c => c.Deleted == false);

// No
var car = db.Cars.FirstOrDefault(c => !c.Deleted);
```

- Filtering pattern

```csharp
public void Filter(IQueryable<Car> cars, SearchCriteria criteria)
{
  if(criteria.NumberOfWheels.HasValue)
    cars = cars.Where(c => c.NumberOfWheels == (int) criteria.NumberOfWheels);
}
```
