# LINQ Extension Methods with Examples

## 1. Filtering Methods
### `Where(predicate)`
```csharp
var numbers = new[] { 1, 2, 3, 4, 5 };
var evenNumbers = numbers.Where(n => n % 2 == 0);
Console.WriteLine(string.Join(", ", evenNumbers)); // Output: 2, 4
```

### `OfType<TResult>()`
```csharp
var mixedList = new object[] { 1, "Hello", 2, "World", 3 };
var intValues = mixedList.OfType<int>();
Console.WriteLine(string.Join(", ", intValues)); // Output: 1, 2, 3
```

## 2. Projection Methods
### `Select(selector)`
```csharp
var numbers = new[] { 1, 2, 3 };
var squares = numbers.Select(n => n * n);
Console.WriteLine(string.Join(", ", squares)); // Output: 1, 4, 9
```

### `SelectMany(selector)`
```csharp
var words = new[] { "Hello", "World" };
var characters = words.SelectMany(w => w.ToCharArray());
Console.WriteLine(string.Join(", ", characters)); // Output: H, e, l, l, o, W, o, r, l, d
```
## 3. Sorting Methods

### `OrderBy(keySelector)`
```csharp
var numbers = new[] { 5, 2, 8, 3 };
var sorted = numbers.OrderBy(n => n);
Console.WriteLine(string.Join(", ", sorted)); // Output: 2, 3, 5, 8
```

### `OrderByDescending(keySelector)`
```csharp
var numbers = new[] { 5, 2, 8, 3 };
var sorted = numbers.OrderByDescending(n => n);
Console.WriteLine(string.Join(", ", sorted)); // Output: 8, 5, 3, 2
```

### `ThenBy(keySelector)`
```csharp
var people = new[] {
    new { Name = "John", Age = 30 },
    new { Name = "Alice", Age = 25 },
    new { Name = "Bob", Age = 25 }
};
var sorted = people.OrderBy(p => p.Age).ThenBy(p => p.Name);
foreach (var p in sorted)
    Console.WriteLine($"{p.Name} - {p.Age}");
// Output:
// Alice - 25
// Bob - 25
// John - 30
```

### `ThenByDescending(keySelector)`
```csharp
var people = new[] {
    new { Name = "John", Age = 30 },
    new { Name = "Alice", Age = 25 },
    new { Name = "Bob", Age = 25 }
};
var sorted = people.OrderBy(p => p.Age).ThenByDescending(p => p.Name);
foreach (var p in sorted)
    Console.WriteLine($"{p.Name} - {p.Age}");
// Output:
// Bob - 25
// Alice - 25
// John - 30
```

### `Reverse()`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
var reversed = numbers.Reverse();
Console.WriteLine(string.Join(", ", reversed)); // Output: 4, 3, 2, 1
```

## 4. Aggregation Methods

### `Aggregate(func)`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
var result = numbers.Aggregate((acc, n) => acc + n);
Console.WriteLine(result); // Output: 10
```

### `Average(selector)`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
var avg = numbers.Average();
Console.WriteLine(avg); // Output: 2.5
```

### `Count(predicate)`
```csharp
var numbers = new[] { 1, 2, 3, 4, 5 };
var count = numbers.Count(n => n % 2 == 0);
Console.WriteLine(count); // Output: 2
```

### `LongCount(predicate)`
```csharp
var numbers = Enumerable.Range(1, int.MaxValue);
var count = numbers.LongCount(n => n % 2 == 0);
Console.WriteLine(count);
```

### `Max(selector)`
```csharp
var numbers = new[] { 1, 5, 3, 9 };
var max = numbers.Max();
Console.WriteLine(max); // Output: 9
```

### `Min(selector)`
```csharp
var numbers = new[] { 1, 5, 3, 9 };
var min = numbers.Min();
Console.WriteLine(min); // Output: 1
```

### `Sum(selector)`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
var sum = numbers.Sum();
Console.WriteLine(sum); // Output: 10
```

## 5. Quantifier Methods

### `All(predicate)`
```csharp
var numbers = new[] { 2, 4, 6, 8 };
bool allEven = numbers.All(n => n % 2 == 0);
Console.WriteLine(allEven); // Output: True
```

### `Any(predicate)`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
bool hasEven = numbers.Any(n => n % 2 == 0);
Console.WriteLine(hasEven); // Output: True
```

### `Contains(value)`
```csharp
var numbers = new[] { 1, 2, 3, 4 };
bool containsThree = numbers.Contains(3);
Console.WriteLine(containsThree); // Output: True
```
## 6. Element Methods

### `ElementAt(index)`
```csharp
var numbers = new[] { 10, 20, 30, 40 };
var element = numbers.ElementAt(2);
Console.WriteLine(element); // Output: 30
```

### `ElementAtOrDefault(index)`
```csharp
var numbers = new[] { 10, 20, 30, 40 };
var element = numbers.ElementAtOrDefault(5);
Console.WriteLine(element); // Output: 0 (default int value)
```

### `First(predicate)`
```csharp
var numbers = new[] { 10, 20, 30, 40 };
var first = numbers.First(n => n > 15);
Console.WriteLine(first); // Output: 20
```

### `FirstOrDefault(predicate)`
```csharp
var numbers = new int[] {};
var first = numbers.FirstOrDefault();
Console.WriteLine(first); // Output: 0 (default int value)
```

### `Last(predicate)`
```csharp
var numbers = new[] { 10, 20, 30, 40 };
var last = numbers.Last(n => n < 35);
Console.WriteLine(last); // Output: 30
```

### `LastOrDefault(predicate)`
```csharp
var numbers = new int[] {};
var last = numbers.LastOrDefault();
Console.WriteLine(last); // Output: 0 (default int value)
```

### `Single(predicate)`
```csharp
var numbers = new[] { 10 };
var single = numbers.Single();
Console.WriteLine(single); // Output: 10
```

### `SingleOrDefault(predicate)`
```csharp
var numbers = new int[] {};
var single = numbers.SingleOrDefault();
Console.WriteLine(single); // Output: 0 (default int value)
```

### `DefaultIfEmpty(defaultValue)`
```csharp
var numbers = new int[] {};
var result = numbers.DefaultIfEmpty(100);
Console.WriteLine(string.Join(", ", result)); // Output: 100
```

## 7. Set Methods

### `Distinct()`
```csharp
var numbers = new[] { 1, 2, 2, 3, 4, 4 };
var distinctNumbers = numbers.Distinct();
Console.WriteLine(string.Join(", ", distinctNumbers)); // Output: 1, 2, 3, 4
```

### `Except(secondCollection)`
```csharp
var numbers1 = new[] { 1, 2, 3, 4 };
var numbers2 = new[] { 2, 4 };
var result = numbers1.Except(numbers2);
Console.WriteLine(string.Join(", ", result)); // Output: 1, 3
```

### `Intersect(secondCollection)`
```csharp
var numbers1 = new[] { 1, 2, 3, 4 };
var numbers2 = new[] { 2, 4, 6 };
var result = numbers1.Intersect(numbers2);
Console.WriteLine(string.Join(", ", result)); // Output: 2, 4
```

### `Union(secondCollection)`
```csharp
var numbers1 = new[] { 1, 2, 3 };
var numbers2 = new[] { 3, 4, 5 };
var result = numbers1.Union(numbers2);
Console.WriteLine(string.Join(", ", result)); // Output: 1, 2, 3, 4, 5
```

## 8. Join Methods

### `Join(innerCollection, outerKeySelector, innerKeySelector, resultSelector)`
```csharp
var employees = new[] { new { Id = 1, Name = "Alice" }, new { Id = 2, Name = "Bob" } };
var departments = new[] { new { Id = 1, Department = "HR" }, new { Id = 2, Department = "IT" } };
var result = employees.Join(departments, e => e.Id, d => d.Id, (e, d) => new { e.Name, d.Department });
foreach (var item in result)
    Console.WriteLine($"{item.Name} - {item.Department}");
// Output:
// Alice - HR
// Bob - IT
```

### `GroupJoin(innerCollection, outerKeySelector, innerKeySelector, resultSelector)`
```csharp
var categories = new[] { new { Id = 1, Name = "Electronics" }, new { Id = 2, Name = "Clothing" } };
var products = new[] { new { CategoryId = 1, Product = "Laptop" }, new { CategoryId = 1, Product = "Phone" } };
var result = categories.GroupJoin(products, c => c.Id, p => p.CategoryId, (c, p) => new { c.Name, Products = p });
foreach (var item in result)
{
    Console.WriteLine($"{item.Name}: {string.Join(", ", item.Products.Select(p => p.Product))}");
}
// Output:
// Electronics: Laptop, Phone
// Clothing:
```

## 9. Grouping Methods

### `GroupBy(keySelector)`
```csharp
var numbers = new[] { 1, 2, 2, 3, 3, 3 };
var grouped = numbers.GroupBy(n => n);
foreach (var group in grouped)
    Console.WriteLine($"{group.Key}: {group.Count()}");
// Output:
// 1: 1
// 2: 2
// 3: 3
```

## 10. Concatenation Methods

### `Concat(secondCollection)`
```csharp
var numbers1 = new[] { 1, 2 };
var numbers2 = new[] { 3, 4 };
var result = numbers1.Concat(numbers2);
Console.WriteLine(string.Join(", ", result)); // Output: 1, 2, 3, 4
```
Here's the complete markdown content in a single canvas:


## 11. Conversion Methods

### `ToArray()`
```csharp
var numbers = new List<int> { 1, 2, 3, 4 };
var array = numbers.ToArray();
Console.WriteLine(string.Join(", ", array)); // Output: 1, 2, 3, 4

```

### `ToList()`

```csharp
var numbers = new int[] { 1, 2, 3, 4 };
var list = numbers.ToList();
Console.WriteLine(string.Join(", ", list)); // Output: 1, 2, 3, 4

```

### `ToDictionary(keySelector, valueSelector)`

```csharp
var students = new[] 
{
    new { Id = 1, Name = "John" },
    new { Id = 2, Name = "Alice" }
};
var dictionary = students.ToDictionary(student => student.Id, student => student.Name);
Console.WriteLine(dictionary[1]); // Output: John

```

### `ToLookup(keySelector)`

```csharp
var students = new[] 
{
    new { Id = 1, Name = "John" },
    new { Id = 2, Name = "Alice" },
    new { Id = 1, Name = "Tom" }
};
var lookup = students.ToLookup(student => student.Id);
foreach (var group in lookup)
{
    Console.WriteLine($"{group.Key}: {string.Join(", ", group.Select(s => s.Name))}");
}
// Output:
// 1: John, Tom
// 2: Alice

```

### `Cast<TResult>()`

```csharp
IEnumerable<object> items = new object[] { 1, "Hello", 3.14 };
var integers = items.Cast<int>().ToList(); // Throws InvalidCastException

```

### `AsEnumerable()`

```csharp
IQueryable<int> numbers = new List<int> { 1, 2, 3 }.AsQueryable();
var enumerable = numbers.AsEnumerable();
Console.WriteLine(enumerable.Count()); // Output: 3

```

### `AsQueryable()`

```csharp
IEnumerable<int> numbers = new List<int> { 1, 2, 3 };
var queryable = numbers.AsQueryable();
Console.WriteLine(queryable.ElementAt(1)); // Output: 2

```

## 12. Partitioning Methods

### `Skip(count)`

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.Skip(2);
Console.WriteLine(string.Join(", ", result)); // Output: 3, 4, 5

```

### `SkipWhile(predicate)`

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.SkipWhile(n => n < 3);
Console.WriteLine(string.Join(", ", result)); // Output: 3, 4, 5

```

### `Take(count)`

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.Take(3);
Console.WriteLine(string.Join(", ", result)); // Output: 1, 2, 3

```

### `TakeWhile(predicate)`

```csharp
var numbers = new List<int> { 1, 2, 3, 4, 5 };
var result = numbers.TakeWhile(n => n < 4);
Console.WriteLine(string.Join(", ", result)); // Output: 1, 2, 3

```

## 13. Zip Method

### `Zip(secondCollection, resultSelector)`

```csharp
var numbers1 = new[] { 1, 2, 3 };
var numbers2 = new[] { 4, 5, 6 };
var result = numbers1.Zip(numbers2, (first, second) => first + second);
Console.WriteLine(string.Join(", ", result)); // Output: 5, 7, 9
```
