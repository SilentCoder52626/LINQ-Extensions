# PLINQ Extension Methods in C#

Parallel LINQ (PLINQ) is an extension of LINQ that enables parallel processing of queries to improve performance by utilizing multiple cores of a processor. Below is a list of PLINQ extension methods along with code snippets demonstrating their usage.

---

## 1. AsParallel
Converts an `IEnumerable` to a parallel query, enabling parallel execution.

```csharp
var numbers = Enumerable.Range(1, 10);
var parallelQuery = numbers.AsParallel().Where(n => n % 2 == 0);
foreach (var num in parallelQuery)
{
    Console.WriteLine(num);
}
```

---

## 2. WithDegreeOfParallelism
Limits the number of processor cores used for the query execution.

```csharp
var numbers = Enumerable.Range(1, 20);
var parallelQuery = numbers.AsParallel()
                           .WithDegreeOfParallelism(2) // Limits to 2 cores
                           .Where(n => n % 2 == 0);
foreach (var num in parallelQuery)
{
    Console.WriteLine(num);
}
```

---

## 3. ParallelEnumerable.Range
Generates a range of numbers in parallel.

```csharp
var parallelRange = ParallelEnumerable.Range(1, 10);
parallelRange.ForAll(Console.WriteLine);
```

---

## 4. ParallelEnumerable.Repeat
Generates a sequence where a specified value is repeated multiple times in parallel.

```csharp
var repeatedValues = ParallelEnumerable.Repeat("Hello", 5);
repeatedValues.ForAll(Console.WriteLine);
```

---

## 5. ParallelEnumerable.Empty
Returns an empty parallel sequence.

```csharp
var emptySequence = ParallelEnumerable.Empty<int>();
Console.WriteLine("Count: " + emptySequence.Count());
```

---

## 6. AsSequential
Forces a PLINQ query to process sequentially instead of in parallel.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel();
var sequentialQuery = numbers.AsSequential().Where(n => n % 2 == 0);
foreach (var num in sequentialQuery)
{
    Console.WriteLine(num);
}
```

---

## 7. AsOrdered
Preserves the ordering of the original sequence in a PLINQ query.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel().AsOrdered();
foreach (var num in numbers)
{
    Console.WriteLine(num);
}
```

---

## 8. AsUnordered
Removes ordering constraints for better parallel performance.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel().AsUnordered();
numbers.ForAll(Console.WriteLine);
```

---

## 9. WithCancellation
Enables cancellation of a PLINQ query using a `CancellationToken`.

```csharp
var cts = new CancellationTokenSource();
var numbers = Enumerable.Range(1, 100).AsParallel().WithCancellation(cts.Token);
Task.Run(() => cts.Cancel());
try
{
    foreach (var num in numbers)
    {
        Console.WriteLine(num);
    }
}
catch (OperationCanceledException)
{
    Console.WriteLine("Query was canceled.");
}
```

---

## 10. WithMergeOptions
Specifies how results should be merged after parallel execution.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel()
                        .WithMergeOptions(ParallelMergeOptions.NotBuffered);
numbers.ForAll(Console.WriteLine);
```

---

## 11. WithExecutionMode
Forces a query to run in parallel or sequential mode.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel()
                        .WithExecutionMode(ParallelExecutionMode.ForceParallelism);
numbers.ForAll(Console.WriteLine);
```

---

## 12. ForAll
Executes a parallel query and applies an action to each element.

```csharp
var numbers = Enumerable.Range(1, 10).AsParallel();
numbers.ForAll(Console.WriteLine);
```

---

## Conclusion
PLINQ provides powerful methods to enable efficient parallel processing in C#. Understanding these methods can help improve performance in applications that handle large data processing tasks.

---

### References
- [Microsoft Docs: PLINQ Overview](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/parallel-linq-plinq)

---

