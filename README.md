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

// field as an instance of another class (in Adoption):
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

See [csharp-system-io-classes](https://github.com/Kernix13/csharp-system-io-classes) for examples of PAth, Directory, FileInfo, and File examples in `Program.cs` and in `README.md`.

```cs
// Add examples for StreamReader and StreamWriter later

// Add examples for things like File.ReadAllText & File.WriteAllText
```

<br>

## JsonSerializer

See [csharp-JsonSerializer-example](https://github.com/Kernix13/csharp-JsonSerializer-example) for an example of many of the OOP and File examples above.

<br>

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

```cs
/* 📌 List<T> */
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

/* 📌 Dictionary<T> */
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

/* 📌 HashSet<T> */
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
- `Dictionary<TKey, TValue>`: ideal for scenarios requiring fast lookups based on unique identifiers
  - is part of the System.Collections.Generic namespace
  - Keys must be unique within the dictionary.
  - Values can be of any type, including custom objects.

<br>

## Enum and struct and record

```cs

```

<br>

## Terms or Keywords to learn

- `void`
- `static`
- `!` (null-conditional operator)
- `new string[#]` or `new int[#]`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>
