# CSharp Boilerplate Code Snippets: Generic Examples for Common Code Blocks

Code snippets and important syntax for important code blocks in C#.

> Check the other markdown files for more examples.

<div id="back-to-top"></div>

## Table of contents

1. [Shell commands](#shell-commands)
1. [Miscellaneous](#miscellaneous)
1. [Parse, Convert, and Cast](#parse-convert-and-cast)
1. [Loop examples](#loop-examples)
1. [Conditionals](#conditionals)
1. [String methods](#string-methods)
1. [Array syntax](#array-syntax)
1. [Exceptions and errors](#exceptions-and-errors)
1. [Methods](#methods)
1. [Classes](#classes)
1. [OOP examples](#oop-examples)
1. [File IO](#file-io)
1. [JsonSerializer](#jsonserializer)
1. [Dates and times](#dates-and-times)
1. [List and HashSet and Dictionary](#list-and-hashset-and-dictionary)
1. [Enum and struct and record](#enum-and-struct-and-record)
1. [Generics and anonymous types](#generics-and-anonymous-types)
1. [Asynchronous programming](#asynchronous-programming)
1. [Terms or Keywords to learn](#terms-or-keywords-to-learn)
1. [](#)

<br>

## Shell commands

Here are the most common/useful in the beginning of learning C#

```sh
# 1. Create a new console project from within your project directory
dotnet new console

# 1. OR: Create the project folder and files
dotnet new console -o MyProjectName

# 2. Move into the project folder
cd MyProjectName

# 3. Create a solution file
dotnet new sln

# 4. Link the project to the solution
dotnet sln add MyProjectName.csproj

# 5. Add a professional gitignore
dotnet new gitignore
```

<br>

## Miscellaneous

```cs
// Option 1: nullable reference type / nullable annotation
string? name = Console.ReadLine();
if (name is null) // Input stream ends (EOF = End Of File)

// Option 2: null-coalescing operator
string name = Console.ReadLine() ?? "";

// null-forgiving operator = "Yeah, I know"
// Console.ReadLine()!
int divisor = int.Parse(Console.ReadLine()!);

// decimal
decimal temp = 34.4m;
decimal decimalQuotient = 7.0m / 5;

// need a float example
float money = 1234.85f; // weak!

Console.ReadLine()
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Parse, Convert, and Cast

```cs
// Convert.ToInt32, int.Parse vs int.TryParse(strVar, out numVar)
```

<br>

## Loop examples

```cs
foreach (dataType name in names) {
  // code here
}

for (int i = 0; i <= someArray.Length; i++) {
  // code here
}

for (const str of myStrings) {
  const sentences = str.split('.');

  for (let sentence of sentences) {
    sentence = sentence.trim();
    if (sentence) console.log(sentence);
  }
}

// While Loop
int i = 0;
while (i < 5)
{
  Console.WriteLine(i);
  i++;
}

// Do-While Loop
int i = 0;
do
{
  Console.WriteLine(i);
  i++;
}
while (i < 5);
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Conditionals

```cs
// basic
if (condition) {
    // code here
} else if (condition) {
    // different code
} else {
    // final code
}

// without {}
if (condition)
    // code here

// Conditional operator
// if true ? do this : else do this
Console.WriteLine(1 > 0 ? true : false);

// switch
switch (product[1])
{
    case "BL":
        color = "Black";
        break;
    case "MN":
        color = "Maroon";
        break;
    default:
        color = "White";
        break;
}
```

<br>

## String methods

```cs
// Split a string by each character
char[] chars = someString.ToCharArray();

// Split a string but not by character
string[] words = someString.Split(' ');

// other methods
someStr.Remove("sub")
someStr.Substring("sub")
someStr.TrimStart()
someStr.IndexOf(i)
someStr.Trim()
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Array syntax

```cs
datatype[] varName = new datatype[3];
datatype[] varName = [val1, val2, val3];
datatype[] varName = {val1, val2, val3}

int[] data = new int[3];

int[] times = {800, 1200, 1600, 2000};

// 2D, Multi-dimensional
int[,] result = { {-1,-1},{-1,-1},{-1,-1},{-1,-1},{-1,-1} };

// Jagged

// methods
Array.sort(someArray);
Array.Reverse(someArray);

// Join array elements into a string
String.Join("delimiter", someArray);
```

<br>

## Exceptions and errors

### try/catch

See [csharp-exception-object-demo](https://github.com/Kernix13/csharp-exception-object-demo) for a specific example.

```cs
// Generic Exception
try
{
    // code here that may cause an exception
}
catch (Exception ex)
{
    // code to run in the event of an exception
}

// Specific exception example
try
{
    // code here that may cause an exception
}
catch (DivideByZeroException ex)
{
    // code to run in the event of an exception
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Methods

```cs
returnType MethodName() {
    /* logic here */
}

int MethodName(int paramName) {
    /* logic here */
    return paramName;
}

void MethodName(string paramName, string param2 = "Hello") {
    /* logic here */
}
```

<br>

## Classes

```cs
// remember to add namespace
namespace ProjectName;
// in Program.cs:
using ProjectName;

// Constructor expression body definition (single line):
public Car(string model) => modelName = model;

// field as an instance of another class:
public Pet AdoptedPet { get; set; }

// properties
public int Name { get; set; }
// or:
private string? _name;
public int Name {
    get { return age; }
    set { age = value; }
}

// initialize automatically implemented properties similarly to fields
public string FirstName { get; set; } = "FirstName";

// restrict the accessibility of the set accessor
public static int TotalPets { get; private set; }

// public class
public class MyClass
{
    public string Name { get; set; }
    // instance constructor
    public MyClass(string name) {
        Name = name;
    }
}

// method (FullAddress) from another class (Address)
public Address HomeAddress { get; set; }
public string FullAddress => HomeAddress.FormatAddress();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## OOP examples

See [csharp-oop-interface-inheritance](https://github.com/Kernix13/csharp-oop-interface-inheritance) for detailed notes.

```cs
namespace ProjectName;

// interface
public interface IPerson
{
    // Name & Age properties, DisplayInfo method signature
    string Name { get; set; }
    int Age { get; set; }

    // interface method
    string DisplayInfo();
}

// Class implementing an interface
public class MyClass : IPerson
{
    string Name { get; set; }
    int Age { get; set; }

    public MyClass(string name, int age) {
        // property = parameter
        Name = name;
        Age = age
    }

    // use abstract or virtual in the base class
    public virtual string DisplayInfo() {
        return $"{Name}, {Age}";
    }
}

// inherit a class
public class DerivedClass : MyClass
{
    public DerivedClass(string name, int age) : base(Name, Age)
    {
        // You don't need to write any code inside the brackets { }
        // because the base constructor already handled it!
    }

    // use override to do your owm version
    public override string DisplayInfo()
    {
        return $"My name is {Name} & I am {Age} years old";
    }
}

/* in Program.cs */
using ProjectName;

// Polymorphism via interface
IPerson person1 = new DerivedClass("Luna", 12);
Console.WriteLine(person1.DisplayInfo());

// Polymorphism via inheritance
MyClass person2 = new DerivedClass("Buddy", 10);
Console.WriteLine(person2.DisplayInfo());
```

Use the following access modifiers to specify the accessibility of a type or member when you declare it:

- `public`: Public members are accessible from any code that has access to the class.
- `private`: Only code declared in the same class or struct can access this member.
- `protected`: Only code in the same class or in a derived class can access this type or member.
- `internal`: Only code in the same assembly can access this type or member.
- `protected internal`: Only code in the same assembly or in a derived class in another assembly can access this type or member.
- `private protected`: Only code in the same assembly and in the same class or a derived class can access the type or member.
- `file`: Only code in the same file can access the type or member.
- The `record` modifier on a type causes the compiler to synthesize extra members.
- The `record` modifier doesn't affect the default accessibility for either a `record class` or a `record struct`.
- The `abstract` keyword: members are incomplete and must be implemented in derived classes
- The `virtual` keyword: to define methods and properties that can be overridden in derived classes
- The `override` keyword: to override properties and methods that are inherited from the base class
- Use the `base` keyword to access the base class implementation from the overridden member in the derived class

NOTE: **The static member is always accessed by the class name, not the instance name**

### Object casting

Cast objects by using the `is` and `as` keywords (only `is` cast example)

```cs
if (account is CheckingAccount checkingAccount) {
    // Use checkingAccount as a CheckingAccount type
}

if (user is NewUser CurrentUser) {
    // Use CurrentUser as a NewUser type
}
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## File IO

See [csharp-system-io-classes](https://github.com/Kernix13/csharp-system-io-classes) for examples of Path, Directory, FileInfo, and File examples in `Program.cs` and in `README.md`.

```cs
// Add examples for StreamReader and StreamWriter later

// Add examples for things like File.ReadAllText & File.WriteAllText
```

<br>

## JsonSerializer

See [csharp-JsonSerializer-example](https://github.com/Kernix13/csharp-JsonSerializer-example) for an example of many of the OOP and File examples above.

<br>

<p align="center">.............. <strong>MODULE 3 STARTS HERE</strong> ..............</p>

## Dates and times

```cs
// TimeOnly(hh, mm)
TimeOnly meetingTime = new TimeOnly(14, 30); // 2:30 PM
Console.WriteLine($"Meeting Time: {meetingTime}"); // Meeting Time: 14:30

TimeSpan duration = new TimeSpan(2, 0, 0); // 2 hours
Console.WriteLine($"Event Duration: {duration}"); // Event Duration: 02:00:00

DayOfWeek today = DateTime.Now.DayOfWeek;
Console.WriteLine($"Today is: {today}"); // Today is: [DayOfWeek]

// Get the current date and time with offset
DateTimeOffset now = DateTimeOffset.Now;
Console.WriteLine($"Current date and time with offset: {now}");

// Get the current UTC date and time with offset
DateTimeOffset utcNow = DateTimeOffset.UtcNow;
Console.WriteLine($"Current UTC date and time with offset: {utcNow}");

// Add 10 days to the current date and time
DateTimeOffset futureDate = now.AddDays(10);
Console.WriteLine($"Date 10 days from now: {futureDate}");

// Subtract 5 hours from the current date and time
DateTimeOffset pastDate = now.AddHours(-5);
Console.WriteLine($"Date 5 hours ago: {pastDate}");

// Calculate the time difference between two dates
TimeSpan difference = futureDate - now;
Console.WriteLine($"Difference between now and future date: {difference}");

// Get current UTC time
DateTime utcNow = DateTime.UtcNow;
Console.WriteLine($"UTC Now: {utcNow}");

// Convert UTC to EST
DateTime estNow = TimeZoneInfo.ConvertTimeBySystemTimeZoneId(utcNow, "Eastern Standard Time");
Console.WriteLine($"EST Now: {estNow}");

// Get local time zone
TimeZoneInfo localZone = TimeZoneInfo.Local;
Console.WriteLine($"Local Time Zone: {localZone.DisplayName}");

// Convert UTC to local time
DateTime localTime = TimeZoneInfo.ConvertTimeFromUtc(utcNow, localZone);
Console.WriteLine($"Local Time: {localTime}");

// Find PST time zone
TimeZoneInfo pstZone = TimeZoneInfo.FindSystemTimeZoneById("Pacific Standard Time");

// Convert UTC to PST
DateTime pstTime = TimeZoneInfo.ConvertTime(utcNow, pstZone);
Console.WriteLine($"PST Time: {pstTime}");

// 2 hours, 14 minutes, 18 seconds
TimeSpan duration = new TimeSpan(2, 14, 18);
Console.WriteLine($"Duration: {duration}");

// Create TimeSpan from 1.5 days (?)
TimeSpan fromDays = TimeSpan.FromDays(1.5);
Console.WriteLine($"From Days: {fromDays}");

DateTime today = DateTime.Now; // Get the current date and time
DayOfWeek day = today.DayOfWeek; // Retrieve the current day of the week
Console.WriteLine("Today is: " + day); // DateTime.Now.DayOfWeek

/* Skip current culture and UI culture */

// Create a calendar instance
Calendar calendar = CultureInfo.InvariantCulture.Calendar;

// Get the number of days in February 2023
int daysInMonth = calendar.GetDaysInMonth(2023, 2);
Console.WriteLine("Days in February 2023: " + daysInMonth);

// Determine the week of the year for December 31, 2023
DateTime date = new DateTime(2023, 12, 31);
CalendarWeekRule rule = CalendarWeekRule.FirstDay;
DayOfWeek firstDayOfWeek = DayOfWeek.Sunday;
int weekOfYear = calendar.GetWeekOfYear(date, rule, firstDayOfWeek);
Console.WriteLine("Week of the year for December 31, 2023: " + weekOfYear);
```

- `DateTime`: The most versatile structure, combining both date and time, suitable for general scheduling tasks.
- Use `TimeZoneInfo` to convert times between different time zones
- Use `TimeSpan` to calculate the difference between two `DateTime` values or to measure elapsed time with the `Stopwatch.Elapsed` property.
- use `DateTimeOffset` to log times with UTC offsets, `TimeZoneInfo` to convert between time zones, and `TimeSpan` to work with time intervals

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## List and HashSet and Dictionary

### `List<T>`

```cs
List<string> books = new List<string>(); // T is string
books.Add("Book A"); // Add a string to the list
books.Add("Book B");
books.Add("Book C");
books.Remove("Book A"); // Remove a specific string from the list

foreach (string book in books) // Iterate through the list
{
    Console.WriteLine(book);
}
// Book B
// Book C

// With classes
public class Student
{
    public string Name { get; set; }
    public int Age { get; set; }
}

List<Student> students = new List<Student>
{
    new Student { Name = "Haneul", Age = 20 },
    new Student { Name = "Magda", Age = 22 }
};

students.Add(new Student { Name = "Dale", Age = 23 });
students.RemoveAt(0); // follow this with a foreach block
```

### `Dictionary<T>`

```cs
var students = new Dictionary<int, string>
{
    { 101, "Ji-min Jo" },
    { 102, "Catalina Blaga" }
};

students.Add(103, "Milan Golob"); // Add a new key-value pair

foreach (var kvp in students)
{
    Console.WriteLine($"Key: {kvp.Key}, Value: {kvp.Value}");
}
// Expected output:
// Key: 101, Value: Ji-min Jo
// Key: 102, Value: Catalina Blaga
// Key: 103, Value: Milan Golob

// Retrieving values: Access values using the key
var students = new Dictionary<int, string>
{
    { 101, "Ji-min Jo" },
    { 102, "Catalina Blaga" }
};

var student = students[101];
Console.WriteLine(student); // Outputs "Ji-min Jo"

// Use a foreach loop to iterate through the dictionary
var students = new Dictionary<int, string>
{
    { 101, "Ji-min Jo" },
    { 102, "Catalina Blaga" },
    { 103, "Milan Golob" }
};

foreach (var kvp in students)
{
    Console.WriteLine($"Key: {kvp.Key}, Value: {kvp.Value}");
}
```

- `Dictionary<TKey, TValue>`: ideal for scenarios requiring fast lookups based on unique identifiers
  - is part of the System.Collections.Generic namespace
  - Keys must be unique within the dictionary.
  - Values can be of any type, including custom objects.

### `HashSet<T>`

```cs
HashSet<string> names = new HashSet<string>();
names.Add("Haneul");
names.Add("Magda");
names.Add("Mia");
names.Add("Mia"); // Duplicate, won't be added

foreach (string name in names) {
    Console.WriteLine(name);
}
// Output (order may vary):
// Haneul
// Magda
// Mia

// To check if an item exists in the collection, use the `Contains` method
HashSet<string> names = new HashSet<string>();
names.Add("Haneul");
names.Add("Magda");

if (names.Contains("Haneul")) {
    Console.WriteLine("Haneul is in the collection.");
}

// 1. Initialization
HashSet<string> uniqueTags = new HashSet<string>();

// 2. Adding items (.Add returns a bool indicating success)
uniqueTags.Add("C#");
uniqueTags.Add("Programming");

// This will be completely ignored because "C#" already exists
bool wasAdded = uniqueTags.Add("C#");

Console.WriteLine($"Was duplicate added? {wasAdded}"); // Output: False
Console.WriteLine($"Total Count: {uniqueTags.Count}");  // Output: 2

// 3. High-performance lookup
if (uniqueTags.Contains("C#"))
{
    Console.WriteLine("Tag found instantly!");
}

// 4. Iteration works just like a List, but order is NOT guaranteed
foreach (var tag in uniqueTags)
{
    Console.WriteLine(tag);
}
```

- `HashSet<T>` ensures that all elements in the collection are unique and _unordered_
- `HashSet<T>` automatically prevents duplicate entries

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Enum and struct and record

### enum

```cs
enum OrderStatus
{
    Pending,
    Shipped,
    Delivered,
    Cancelled
}

enum Season
{
    Spring,
    Summer,
    Autumn,
    Winter
}

public enum FileMode {
    CreateNew = 1,
    Create = 2,
    Open = 3,
    OpenOrCreate = 4,
    Truncate = 5,
    Append = 6,
}

enum ErrorCode : ushort
{
    None = 0,
    Unknown = 1,
    ConnectionLost = 100,
    OutlierReading = 200
}
```

- Use `enums` in C# to define named constants and prevent invalid values.
- By default, the underlying type of an `enum` is `int`, and the values start at `0`, incrementing by 1 for each member
- Use singular nouns for simple enums and plural nouns for flag enums (?)
- Provide a value of zero for simple enums, typically named `None`.

### struct

```cs
public struct Point
{
    public int X;
    public int Y;

    public Point(int x, int y)
    {
        X = x;
        Y = y;
    }
}

public struct Rectangle
{
    private int width;
    private int height;

    public Rectangle(int width, int height)
    {
        // Whys this? I don't often see that
        this.width = width;
        this.height = height;
    }

    public int Area => width * height;
}
```

- Work with `structs` in C# to encapsulate related data into lightweight containers.
- Structs are value types in C#: they directly store their data rather than referencing it
- Structs are commonly used for representing lightweight data like geometric shapes, coordinates, or configuration settings
- Structs are best suited for small, immutable, and performance-critical data
- structs can't inherit from other structs or classes, but they can implement interfaces
  - If your type focuses on behavior rather than data, classes are often a better choice due to their reference semantics
- Encapsulation allows you to control access to the data within a struct. Use access modifiers like `private`, `public`, or `internal` to specify accessibility
- When you apply the `readonly` modifier to a struct, you can enforce immutability

### record

```cs
public record Product(string Name, decimal Price)
{
    public override int GetHashCode() => HashCode.Combine(Name.ToLower(), Price);
}

public record AccountHolderDetails(string Name, string CustomerId, string Address);

// inheritance
public record Animal(string Name);
public record Dog(string Name, string Breed) : Animal(Name);

var dog = new Dog("Buddy", "Golden Retriever");
Console.WriteLine(dog); // Output: Dog { Name = Buddy, Breed = Golden Retriever }
```

- Create `records` in C# to model immutable data and ensure consistency.
- Records in C# provide a way to create immutable data models with value-based equality
- Records automatically generate properties, constructors, and methods like ToString, Equals, and GetHashCode.
- Records are useful for scenarios like modeling API responses, configuration settings, or logging events where immutability and simplicity are critical
- Immutability: Records are immutable by default
- Equality: Records use value-based equality, whereas classes use reference equality, and structs rely on value equality
- Inheritance: Record classes support inheritance, but record structs don't (?)
- When you compile your C# code, the compiler takes your record and actually turns it into a standard class
- However, the compiler automatically injects custom `Equals()` and `==` code into that class so that it behaves like a value type when you compare them
- Use records when you need immutable data models with value-based equality. For mutable or behavior-focused types, consider using classes instead.
- Records are ideal for representing immutable data

> `records` are really confusing!

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Generics and anonymous types

```cs
// T is the type parameter: Box<int>,  Box<string>, etc
public class Box<T>
{
    public T Item { get; set; }

    public void AddItem(T item)
    {
        Item = item;
    }
}

// This generic method retrieves the first item from a list of any type
public T GetFirstItem<T>(List<T> items)
{
    return items[0];
}

List<string> names = new List<string> {"Hannah", "Mario"};
string firstName = GetFirstItem(names);
Console.WriteLine(firstName);
```

- When you use generics, the compiler replaces the type parameter with the actual type during compilation, ensuring type safety and avoiding runtime errors.
- Think of `T` as a "placeholder" for the type you want to use. It makes your code flexible and reusable.
- Generic classes and methods are commonly used with collections, such as `List<T>` and `Dictionary<TKey, TValue>`

### generic interfaces

```cs
// generic interfaces
public class Product : IComparable<Product>
{
    public string Name { get; set; }
    public decimal Price { get; set; }

    public int CompareTo(Product other)
    {
        return Price.CompareTo(other.Price);
    }
}

// example of using IComparer<T> to sort a list of products
// implements IComparer<Product> to sort products by price
public class ProductComparer : IComparer<Product>
{
    public int Compare(Product x, Product y)
    {
        return x.Price.CompareTo(y.Price);
    }
}

var products = new List<Product>
{
    new Product { Name = "Laptop", Price = 1200 },
    new Product { Name = "Tablet", Price = 600 }
};

products.Sort(new ProductComparer());
```

- Generic interfaces are a key feature of advanced generics, allowing you to define type-safe contracts for implementing classes
- Some commonly used generic interfaces in .NET include:
  - `IEnumerable<T>`: Represents a collection of objects that can be enumerated
  - `IComparer<T>`: Defines a custom comparison for sorting objects
  - `IEqualityComparer<T>`: Defines custom equality logic for comparing objects

> Skip Generic math

### Covariance & Contravariance

```cs
IEnumerable<string> strings = new List<string>();
// Covariance: string is a more specific type than object:
IEnumerable<object> objects = strings;

Action<object> handleObject = obj => Console.WriteLine(obj);
// Contravariance: object is a more general type than string:
Action<string> handleString = handleObject;
```

- Covariance: Allows you to assign a more specific type (derived type) to a more general type (base type).
  - Think of it like storing a collection of apples (`IEnumerable<Apple>`) in a basket that can hold any fruit (`IEnumerable<Fruit>`).
- Contravariance: Allows you to assign a more general type (base type) to a more specific type (derived type).
  - Think of it like using a handler for any fruit (`Action<Fruit>`) to process only apples (`Action<Apple>`).

### Anonymous types

```cs
var v = new { Amount = 108, Message = "Hello" };
Console.WriteLine($"{v.Amount} - {v.Message}");

// object initializer example
Cat myCat = new Cat { Name = "Fluffy", Age = 10 };
// Anonymous Type
var person = new { Name = "John", Age = 30 };

// how to create an anonymous type
var product = new { Name = "Laptop", Price = 1200 };
Console.WriteLine($"Product: {product.Name}, Price: {product.Price}");

// anonymous type used to group data temporarily
var customer = new { Name = "Mario Rogers", Age = 30 };
Console.WriteLine($"Customer: {customer.Name}, Age: {customer.Age}");
```

- Anonymous types in C# let you group related data into a temporary object without defining a full class
  - They allow you to create objects with read-only properties
- Anonymous types are created using the `new` operator and object initializers
  - object initializer: Instead of calling a constructor and then writing multiple assignment statements, you can set properties within a single expression
- They're commonly used in Language-Integrated Query (LINQ) queries to return subsets of properties from objects
- Anonymous types can't include methods, events, or null values as property initializers
- Anonymous types are often declared using implicitly typed variables (`var`)
- Anonymous types are commonly used in LINQ queries to _project results into objects_ with selected properties (?)
- Anonymous types allow you to only work with the data you need

```cs
var products = new[] {
    new { Name = "Laptop", Price = 1200 },
    new { Name = "Tablet", Price = 600 }
};

// This looks like SQL?
var filteredProducts = from p in products
                       where p.Price > 1000
                       select new { p.Name, p.Price };

foreach (var product in filteredProducts)
{
    Console.WriteLine($"Name: {product.Name}, Price: {product.Price}");
}
```

- The select clause creates instances of anonymous types
- The query returns an IEnumerable of the anonymous type
- Anonymous types are internal, so they can't be passed across assembly boundaries
- Anonymous types and tuple types both allow grouping of related data but differ in usability and performance

<br>

## Asynchronous programming

typical areas where asynchronous programming improves responsiveness:

- Web access: `HttpClient` - `Windows.Web.Http.HttpClient`, `SyndicationClient`
- Working with files: `JsonSerializer`, `StreamReader`, `StreamWriter`, etc. - StorageFile
- Working with images - MediaCapture, BitmapEncoder, BitmapDecoder
- WCF programming: Synchronous and Asynchronous Operations

```cs
// Example of how to create and call an asynchronous task
using System;
using System.IO;
using System.Threading.Tasks;

// public static async Task Main() is a problem:
// I never have Main in Program.cs!!!
public static async Task Main()
{
    string filePath = "example.txt";
    string content = await ReadFileAsync(filePath);
    Console.WriteLine(content);
}

public static async Task<string> ReadFileAsync(string filePath)
{
    using (StreamReader reader = new StreamReader(filePath))
    {
        string content = await reader.ReadToEndAsync();
        return content;
    }
}

// System.IO and System.Text.Json
using System.IO;
using System.Text.Json;
using System.Threading.Tasks;

public class Account
{
    public string Name { get; set; }
    public decimal Balance { get; set; }
}

public class Program
{
    public static async Task Main() // WFT with Main?
    {
        // Combine a directory and file name, then create the directory if it doesn't exist
        string directoryPath = @"C:\TempDir";
        if (!Directory.Exists(directoryPath))
        {
            Directory.CreateDirectory(directoryPath);
        }

        string fileName = "account.json";
        string filePath = Path.Combine(directoryPath, fileName);

        Account account = new Account { Name = "Elize Harmsen", Balance = 1000.00m };

        // Save account data to a file asynchronously
        await SaveAccountDataAsync(filePath, account);

        // Load account data from the file asynchronously
        Account loadedAccount = await LoadAccountDataAsync(filePath);
        Console.WriteLine($"Name: {loadedAccount.Name}, Balance: {loadedAccount.Balance}");
    }

    public static async Task SaveAccountDataAsync(string filePath, Account account)
    {
        string jsonString = JsonSerializer.Serialize(account);
        await File.WriteAllTextAsync(filePath, jsonString);
    }

    public static async Task<Account> LoadAccountDataAsync(string filePath)
    {
        string jsonString = await File.ReadAllTextAsync(filePath);
        return JsonSerializer.Deserialize<Account>(jsonString);
    }
}

// Code that demonstrates the use of asynchronous REST API calls in C#
using System;
using System.ComponentModel; // what is this
using System.Net.Http;
using System.Threading.Tasks;
using System.Text.Json;

using (HttpClient client = new HttpClient()) {
    try {
        // PetStore API endpoint
        string url = "https://petstore.swagger.io/v2/pet/findByStatus?status=available";
        HttpResponseMessage response = await client.GetAsync(url);
        response.EnsureSuccessStatusCode();
        string responseBody = await response.Content.ReadAsStringAsync();
        // Console.WriteLine($"Response: {responseBody}");

        // Deserialize the JSON response into a list of pets
        var pets = JsonSerializer.Deserialize<List<Pet>>(responseBody);

        // Iterate through the list of pets and display their details
        foreach (var pet in pets) {
            if (pet.id.ToString().Length > 4) {
                Console.WriteLine($"Pet ID: {pet.id}, Name: {pet.name}");
            }
        }
    }
    catch (HttpRequestException e) {
        Console.WriteLine($"Request error: {e.Message}");
    }
  }

public class Pet {
    public long id { get; set; }
    public string name { get; set; }
    public Category category { get; set; }
    public List<string> photoUrls { get; set; }
    public List<Tag> tags { get; set; }
    public string status { get; set; }
}

public class Category {
    public long id { get; set; }
    public string name { get; set; }
}

public class Tag {
    public long id { get; set; }
    public string name { get; set; }
}
```

- The asynchronous operations are typically implemented using the `Task` or `Task<T>` types, which represent an ongoing operation that can be awaited
- The `Task<string>` type is a generic task that represents an asynchronous operation that returns a string value
- The `Task` or `Task<T>` types represent ongoing operations that can be awaited in C#.
- The `Main` method is also defined as asynchronous, allowing it to call the `ReadFileAsync` method using the `await` keyword
  - **_I never have a Main method in my projects?!?_**
- When you use top-level statements, the compiler automatically assumes the hidden, behind-the-scenes Main method is async the moment you use the `await` keyword in your file
- file input and output (file I/O) can be performed synchronously or asynchronously
- Asynchronous file I/O is particularly useful for improving application performance and responsiveness
- The `System.IO` and `System.Text.Json` namespaces provide classes and methods for performing file I/O operations asynchronously

The HTTPClient class includes the following asynchronous methods:

- `GetAsync`: Sends a GET request to the specified URI and returns the response.
- `PostAsync`: Sends a POST request to the specified URI with the specified content and returns the response.
- `PutAsync`: Sends a PUT request to the specified URI with the specified content and returns the response.
- `DeleteAsync`: Sends a DELETE request to the specified URI and returns the response.
- `SendAsync`: Sends an HTTP request message and returns the response.
- The `using` statement ensures that the `HttpClient` instance is disposed of properly after use, releasing any resources it holds

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Terms or Keywords to learn

- `void`
- `static`
- `!` (null-conditional operator)
- `new string[#]` or `new int[#]`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>
