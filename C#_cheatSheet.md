# C# Cheat Sheet (For Python/Java/C++ Developers)

---

## The Basics — Familiar but Different

C# is strongly typed like Java, but with cleaner syntax. `var` lets C# infer the type (like Python, but still strongly typed).

```csharp
int x = 10;
double d = 3.14;
string name = "Slavko";
bool flag = true;

// var — compiler infers the type
var message = "Hello!";  // still a string
```

---

## Console I/O

```csharp
// Output
Console.WriteLine("Hello");        // prints with newline
Console.Write("Hello");            // prints without newline

// Input (everything comes in as string)
string line = Console.ReadLine();
int x = int.Parse(Console.ReadLine());
double d = double.Parse(Console.ReadLine());

// Multiple values on one line (like Python's split())
var parts = Console.ReadLine().Split();
int a = int.Parse(parts[0]);
int b = int.Parse(parts[1]);
```

---

## Data Types

| C#     | Python Equivalent | Notes                              |
|--------|-------------------|------------------------------------|
| int    | int               | 32-bit                             |
| long   | int               | 64-bit, use for big numbers        |
| double | float             | 64-bit decimal                     |
| string | str               | immutable                          |
| bool   | bool              | `true` / `false` (lowercase)       |
| char   | str[0]            | single character, use single quotes `'a'` |

---

## String Operations

```csharp
string s = "Hello World";

s.Length          // len(s) in Python
s.ToUpper()       // s.upper()
s.ToLower()       // s.lower()
s.Contains("lo")  // "lo" in s
s.Replace("Hello", "Hi")
s.Split(' ')      // s.split(' ') — returns array
s.Trim()          // s.strip()
s[0]              // first character

// String interpolation (like f-strings in Python)
string name = "Mirko";
int age = 20;
Console.WriteLine($"Name: {name}, Age: {age}");  // f"Name: {name}"
```

---

## Arrays vs Lists

```csharp
// Array — fixed size (like C arrays)
int[] arr = new int[5];
int[] arr2 = { 1, 2, 3, 4, 5 };
arr.Length;   // len(arr)

// List — dynamic size (like Python lists)
List<int> list = new List<int>();
list.Add(10);           // list.append(10)
list.Remove(10);        // list.remove(10)
list.Count;             // len(list)
list.Contains(10);      // 10 in list
list.Sort();            // list.sort()

// Loop through either
foreach (int item in list)
{
    Console.WriteLine(item);
}
```

---

## Dictionary & HashSet

```csharp
// Dictionary (like Python dict)
Dictionary<string, int> dict = new Dictionary<string, int>();
dict["key"] = 5;
dict.ContainsKey("key");
dict.ContainsValue(5);

foreach (var pair in dict)
{
    Console.WriteLine($"{pair.Key} = {pair.Value}");
}

// HashSet (like Python set)
HashSet<int> set = new HashSet<int>();
set.Add(1);
set.Contains(1);
set.Count;
```

---

## Control Flow

```csharp
// if-else (same as Java/C++)
if (x > 0)
{
    Console.WriteLine("Positive");
}
else if (x < 0)
{
    Console.WriteLine("Negative");
}
else
{
    Console.WriteLine("Zero");
}

// for loop
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
}

// while loop
while (x > 0)
{
    x--;
}

// foreach (like Python's for x in list)
foreach (var item in list)
{
    Console.WriteLine(item);
}
```

---

## Methods / Functions

```csharp
// Basic method
static int Add(int a, int b)
{
    return a + b;
}

// Void method (no return)
static void PrintHello()
{
    Console.WriteLine("Hello");
}

// Default parameters (like Python)
static void Greet(string name = "World")
{
    Console.WriteLine($"Hello {name}");
}
```

---

## Math Operations

```csharp
using System;

Math.Abs(-5)        // abs(-5)
Math.Max(3, 7)      // max(3, 7)
Math.Min(3, 7)      // min(3, 7)
Math.Pow(2, 10)     // 2 ** 10  — returns double
Math.Sqrt(25)       // returns double
Math.Floor(3.9)     // math.floor()
Math.Ceiling(3.1)   // math.ceil()

int x = 10 % 3;    // modulo, same as Python
```

---

## Key Differences from Python

| Python                   | C#                        |
|--------------------------|---------------------------|
| `print()`                | `Console.WriteLine()`     |
| `input()`                | `Console.ReadLine()`      |
| `len(x)`                 | `x.Length` or `x.Count`  |
| `True` / `False`         | `true` / `false`          |
| `and` / `or` / `not`     | `&&` / `\|\|` / `!`      |
| `elif`                   | `else if`                 |
| No semicolons            | Semicolons required `;`   |
| Indentation = structure  | Curly braces `{}` = structure |
| `def`                    | return type + method name |
| `None`                   | `null`                    |
| `f"text {var}"`          | `$"text {var}"`           |

---

## Key Differences from Java

C# is very similar to Java but cleaner:

- `var` for type inference
- `$""` string interpolation instead of `String.format()`
- `Console.WriteLine` instead of `System.out.println`
- Properties instead of getters/setters
- `List<T>` works the same way

---

## Typical DSA Problem Template

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // Read input
        int n = int.Parse(Console.ReadLine());

        // Read array on one line
        var parts = Console.ReadLine().Split();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++)
        {
            arr[i] = int.Parse(parts[i]);
        }

        // Solve and output
        Console.WriteLine(Solve(arr));
    }

    static int Solve(int[] arr)
    {
        // your logic here
        return 0;
    }
}
```

> **Tips:**
> - When in doubt, use `long` instead of `int` to avoid overflow
> - Use `var` to save typing when the type is obvious
> - `foreach` is your best friend for clean loops
> - C# is very close to Java — if you know Java, you're 80% there

---

# Common C# Programming Patterns for DSA & General Use

---

## 1. Reading Input Patterns

```csharp
// Single number
int n = int.Parse(Console.ReadLine());

// Multiple numbers on one line
var parts = Console.ReadLine().Split();

// Multiple numbers on one line directly into array
int[] arr = Array.ConvertAll(Console.ReadLine().Split(), int.Parse);

// Reading n lines of numbers
int[] arr = new int[n];
for (int i = 0; i < n; i++)
    arr[i] = int.Parse(Console.ReadLine());

// Reading a grid / 2D input
int[][] grid = new int[n][];
for (int i = 0; i < n; i++)
    grid[i] = Array.ConvertAll(Console.ReadLine().Split(), int.Parse);
```

---

## 2. Sorting Patterns

```csharp
int[] arr = { 5, 3, 1, 4, 2 };

// Sort ascending
Array.Sort(arr);

// Sort descending
Array.Sort(arr);
Array.Reverse(arr);

// Sort a List
List<int> list = new List<int> { 5, 3, 1 };
list.Sort();

// Sort by custom rule (like Python's key=)
list.Sort((a, b) => a.CompareTo(b));   // ascending
list.Sort((a, b) => b.CompareTo(a));   // descending

// Sort array of strings by length
string[] words = { "banana", "apple", "kiwi" };
Array.Sort(words, (a, b) => a.Length.CompareTo(b.Length));
```

---

## 3. Dictionary Patterns

```csharp
// Frequency counter (very common in DSA)
string s = "hello";
Dictionary<char, int> freq = new Dictionary<char, int>();

foreach (char c in s)
{
    if (freq.ContainsKey(c))
        freq[c]++;
    else
        freq[c] = 1;
}

// Cleaner way using TryGetValue
foreach (char c in s)
{
    freq.TryGetValue(c, out int count);
    freq[c] = count + 1;
}

// Get value or default
int val = freq.GetValueOrDefault('z', 0);
```

---

## 4. Two Pointer Pattern

Common for sorted arrays, finding pairs, etc.

```csharp
int[] arr = { 1, 2, 3, 4, 5 };
int left = 0;
int right = arr.Length - 1;

while (left < right)
{
    int sum = arr[left] + arr[right];
    if (sum == target)
    {
        // found pair
        break;
    }
    else if (sum < target)
        left++;
    else
        right--;
}
```

---

## 5. Sliding Window Pattern

```csharp
// Fixed window of size k
int k = 3;
int windowSum = 0;

// Build first window
for (int i = 0; i < k; i++)
    windowSum += arr[i];

int maxSum = windowSum;

// Slide the window
for (int i = k; i < arr.Length; i++)
{
    windowSum += arr[i];        // add new element
    windowSum -= arr[i - k];   // remove old element
    maxSum = Math.Max(maxSum, windowSum);
}
```

---

## 6. Stack & Queue Patterns

```csharp
// Stack — LIFO (Last In First Out)
Stack<int> stack = new Stack<int>();
stack.Push(1);
stack.Push(2);
int top = stack.Peek();   // look at top
int val = stack.Pop();    // remove top
bool empty = stack.Count == 0;

// Queue — FIFO (First In First Out)
Queue<int> queue = new Queue<int>();
queue.Enqueue(1);
queue.Enqueue(2);
int front = queue.Peek();    // look at front
int val2 = queue.Dequeue();  // remove front
```

---

## 7. String Building Pattern

Never concatenate strings in a loop — use `StringBuilder`.

```csharp
// Bad — slow, creates a new string every iteration
string result = "";
for (int i = 0; i < 1000; i++)
    result += i;

// Good — efficient
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++)
    sb.Append(i);

string result = sb.ToString();
```

---

## 8. Min/Max Tracking Pattern

```csharp
int max = int.MinValue;
int min = int.MaxValue;

foreach (int num in arr)
{
    if (num > max) max = num;
    if (num < min) min = num;
}

// Or simply with LINQ
int max = arr.Max();
int min = arr.Min();
```

---

## 9. Prefix Sum Pattern

Useful for range sum queries.

```csharp
int[] arr = { 1, 2, 3, 4, 5 };
int[] prefix = new int[arr.Length + 1];

for (int i = 0; i < arr.Length; i++)
    prefix[i + 1] = prefix[i] + arr[i];

// Sum from index l to r (inclusive)
int l = 1, r = 3;
int rangeSum = prefix[r + 1] - prefix[l];
```

---

## 10. Modulo Pattern (Avoid Overflow)

When the problem says "output mod 1e9+7":

```csharp
long MOD = 1_000_000_007;

long result = 0;
for (int i = 0; i < n; i++)
{
    result = (result + arr[i]) % MOD;
}
```

---

## 11. Checking Visited / Seen (Boolean Array)

```csharp
// Instead of HashSet for index-based visited tracking
bool[] visited = new bool[n];  // all false by default

visited[0] = true;

if (!visited[i])
{
    // process node i
    visited[i] = true;
}
```

---

## 12. LINQ (Powerful One-Liners)

```csharp
using System.Linq;

int[] arr = { 1, 2, 3, 4, 5 };

arr.Sum()              // sum of all
arr.Max()              // max value
arr.Min()              // min value
arr.Average()          // average
arr.Length             // count

// Filter (like Python list comprehension)
var evens = arr.Where(x => x % 2 == 0).ToArray();

// Transform (like Python map)
var doubled = arr.Select(x => x * 2).ToArray();

// Sort
var sorted = arr.OrderBy(x => x).ToArray();
var descending = arr.OrderByDescending(x => x).ToArray();

// Check conditions
bool anyNegative = arr.Any(x => x < 0);
bool allPositive = arr.All(x => x > 0);
```

---

## Quick Reference — When to Use What

| Situation                    | Use                     |
|------------------------------|-------------------------|
| Need unique values           | `HashSet<T>`            |
| Key-value pairs / counting   | `Dictionary<T, T>`      |
| LIFO / undo operations       | `Stack<T>`              |
| FIFO / BFS                   | `Queue<T>`              |
| Fast range sums              | Prefix Sum array        |
| Building strings in a loop   | `StringBuilder`         |
| Big numbers                  | `long` + modulo         |
| Sorted + two pointer         | Sort first, then two pointers |
