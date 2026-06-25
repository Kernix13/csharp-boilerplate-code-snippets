# CSharp Boilerplate Code Snippets: Generic Examples for Common Code Blocks

Code snippets and important syntax for important code blocks in C#.

> Check the other markdown files for more examples.

<div id="back-to-top"></div>

## Table of contents

1. [Shell commands](#shell-commands)
1. [Miscellaneous](#miscellaneous)
1. [Formatting](#formatting)
1. [Parse, Convert, and Cast](#parse-convert-and-cast)
1. [Loop examples](#loop-examples)
1. [Conditionals](#conditionals)
1. [String methods](#string-methods)
1. [Math methods](#math-methods)
1. [Array syntax](#array-syntax)
1. [List methods](#list-methods)
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
1. [Attributes](#attributes)
1. [Asynchronous programming](#asynchronous-programming)
1. [LINQ](#linq)
1. [Unit tests](#unit-tests)
1. [Building a CRUD REST Web API](#building-a-crud-rest-web-api)
1. [Basic Web Api](#basic-web-api)
1. [Terms or Keywords to learn](#terms-or-keywords-to-learn)

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
Console.WriteLine("New line");
Console.Write("Same line");

// Option 1: nullable reference type / nullable annotation
Console.Write("Enter your name: ");
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

// float example
float money = 1234.85f;

string text = "Hello";
char letter = 'A';
bool isTrue = true;

// Declaration then assignment
int score;
score = 100;

/* Latest language enhancements and syntax improvements: */
// Global using (C# 10)
global using System;
global using System.Collections.Generic;

// File-scoped namespace (C# 10)
namespace MyApp.Services;

// Raw string literals (C# 11)
string json = """
{
    "name": "John",
    "age": 30
}
""";

// Required members (C# 11)
public class Person
{
    public required string Name { get; init; }
}

// Collection expressions (C# 12)
int[] numbers = [1, 2, 3, 4, 5];
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Formatting

- You can use composite formatting or string interpolation to format strings.
- With composite formatting, you use a string template containing one or more replacement tokens in the form `{0}`. You also supply a list of arguments that are matched with the replacement tokens based on their order.
- Format currency using a `:C` specifier.
- Format numbers using a `:N` specifier. Control the precision (number of values after the decimal point) using a number after the :N like {myNumber:N3}.
- Format percentages using the `:P` format specifier.
- `:F2`: format with 2 decimal places?

Formatting currency

- `:C`: currency format specifier, used to present as currency
- Notice how adding the `:C` to the tokens inside of the curly braces formats the number as currency regardless of whether you use `int` or `decimal`.

```cs
decimal price = 123.45m;
int discount = 50;
Console.WriteLine($"Price: {price:C} (Save {discount:C})");
// Price: $123.45 (Save $50.00)
```

Formatting numbers

When working with numeric data, you might want to format the number for readability by including commas to delineate thousands, millions, billions, and so on.

- By default, the `N` numeric format specifier displays only two digits after the decimal point.
- If you want to display more precision, you can do that by adding a number after the specifier

The `N` numeric format specifier makes numbers more readable. Update your code as follows:

```cs
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N} units");
// Measurement: 123,456.79 units

// add 4 digits after decimal point
Console.WriteLine($"Measurement: {measurement:N4} units");
```

Formatting percentages

Use the `P` format specifier to format percentages and rounds to 2 decimal places. Add a number afterwards to control the number of values displayed after the decimal point. Update your code as follows:

```cs
decimal tax = .36785m;
Console.WriteLine($"Tax rate: {tax:P2}");
// Tax rate: 36.79%
```

```cs
int invoiceNumber = 1201;
decimal productShares = 25.4568m;
decimal subtotal = 2750.00m;
decimal taxPercentage = .15825m;
decimal total = 3185.19m;

Console.WriteLine($"Invoice Number: {invoiceNumber}"); // Invoice Number: 1201
Console.WriteLine($"Shares: {productShares:N3} Product"); // Shares: 25.457 Product
Console.WriteLine($"Sub Total: {subtotal:C}"); // Sub Total: $2,750.00
Console.WriteLine($"Tax: {taxPercentage:P2}"); // Tax: 15.83%
Console.WriteLine($"Total Billed: {total:C}"); // Total Billed: $3,185.19
```

_Composite formatting_ uses numbered placeholders within a string. At run time, everything inside the braces is resolved to a value that is also passed in based on their position.

- Externalized Strings: If you are pulling strings from a database or a `.resx` file for Localization (translating your app into different languages), you can't use interpolation because the string isn't "hard-coded." You need string.Format() to plug the values into the translated template at runtime.
- Complex Templates: If you have a very long, multi-line template that you want to define once and reuse multiple times with different data, `string.Format()` is the tool for the job.

```cs
string first = "Hello";
string second = "World";
string result = string.Format("{0} {1}!", first, second);
Console.WriteLine(result);
```

<br>

## Parse, Convert, and Cast

```cs
// Convert.ToInt32, int.Parse vs int.TryParse(strVar, out numVar)
```

<br>

## Loop examples

```cs
// for loop
for (int i = 0; i <= someArray.Length; i++) {
  // code here
}

// foreach loop
foreach (dataType name in names) {
  // code here
}

int[] numbers = { 1, 2, 3, 4, 5 };
foreach (int num in numbers)
{
    Console.WriteLine(num);
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
string status = age >= 18 ? "Adult" : "Minor";
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

The string data type, literal strings, and variables of type string each implement many helper methods to format, modify, and perform other operations on strings.

- Methods that add blank spaces for formatting purposes (`PadLeft()`, `PadRight()`)
- Methods that removes whitespace (`Trim()`, `TrimStart()`, `TrimEnd()`)
- Miscellaneous: `GetHashcode()`, the `Length` property
- Methods that help you determine what's inside of a string, or even retrieve just a part of the string (`Contains()`, `StartsWith()`, `EndsWith()`, `Substring()`)
- Methods that change the content of the string by replacing, inserting, or removing parts (`Replace()`, `Insert()`, `Remove()`)
- Methods that turn a string into an array of strings or characters (`Split()`, `ToCharArray()`)

The PadLeft() method adds blank spaces to the left-hand side of the string so that the total number of characters equals the argument you send it

```cs
// Split a string by each character
char[] chars = str.ToCharArray();

// Split a string but not by character
string[] words = str.Split(' ');

// other methods and properties
+=
str.Length;
str[i];
str + str2;

str.ToLower();
str.ToUpper();
str.Split(sep);
str.Remove(start, len);
str.Substring("sub");
str.TrimStart();
str.IndexOf(val);
str.LastIndexOf(val);
str.Trim();
str.EndsWith(val);
str.Replace("old", "new");
str.Replace("old", "");
str.Insert(i, val);

str.StartsWith(sub);
str.EndsWith(sub);
str.Contains(sub);
```

```cs
string input = "Pad this";
Console.WriteLine(input.PadLeft(12));
Console.WriteLine(input.PadRight(12));
Console.WriteLine(input.PadLeft(12, '-'));
Console.WriteLine(input.PadRight(12, '-'));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Math methods

```cs
Math.Abs(num)
Math.Max(num1, num2)
Math.Min(num1, num2)
MAth.Pow(num, exp)
Math.Sqrt(num)
Math.Round(num)
Math.Ceiling(num)
Math.Floor(num)

Random random = new Random();
int num = random.Next(1, 7);
double num = random.NextDouble(); // between 0 and 1
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

## List methods

```cs
list1.Length
list1.Count
list1[i]
list1[i] = item
var list2 = new List<T>(list1)
str.Join(sep, list1)
list1.Concat(list2).ToList()
list1.IndexOf(item)
list1.Clear()
list1.Add(item)
list1.Insert(i, item)
list1.Remove(x)
list1.RemoveAt(0)
list1.Reverse()
list1.Sort()
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

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
finally
{
    Console.WriteLine("Cleanup");
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

// Simple method
void SayHello()
{
    Console.WriteLine("Hello!");
}

// Method with parameters
void Greet(string name)
{
    Console.WriteLine($"Hello, {name}!");
}

// Method with return value
int Add(int a, int b)
{
    return a + b;
}

// Out parameters (must assign)
bool TryParse(string input, out int result)
{
    return int.TryParse(input, out result);
}

// Multiple returns with tuples
(int sum, int product) Calculate(int a, int b)
{
    return (a + b, a * b);
}

// Calling methods
SayHello();
Greet("Alice");
int sum = Add(5, 3);

// Named arguments
PrintInfo(age: 25, name: "Bob");
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
    get { return _name; }
    set { _name = value; }
}

// initialize automatically implemented properties similarly to fields
public string FirstName { get; set; } = "FirstName";

// restrict the accessibility of the set accessor
public static int TotalPets { get; private set; }

// public class
public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
    // instance constructor
    public Person(string name, int age) {
        Name = name;
        Age = age;
    }
}

// usage
Person person = new Person("Luna", 12);

// method (FullAddress) from another class (Address)
public Address HomeAddress { get; set; }
public string FullAddress => HomeAddress.FormatAddress();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## OOP examples: interfaces and inheritance

See [csharp-oop-interface-inheritance](https://github.com/Kernix13/csharp-oop-interface-inheritance) for detailed notes.

```cs
namespace ProjectName;

// Simple interface
public interface IPlayable
{
    void Play();
    void Pause();
}

public class Video : IPlayable
{
    public void Play() => Console.WriteLine("Playing video");
    public void Pause() => Console.WriteLine("Pausing video");
}

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

// Basic inheritance
public class Animal
{
    public virtual void MakeSound()
    {
        Console.WriteLine("Some sound");
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
}

// Usage
Animal myPet = new Dog();
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
- The `abstract` keyword: the class or members are incomplete and must be implemented in derived classes
  - You can not instantiate an object from an abstract class
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
/* 1️⃣ Directory */
// 1. Determine the current directory
Console.WriteLine($"1. CURRENT DIRECTORY: {Directory.GetCurrentDirectory()}");

// 2. Loop through files
IEnumerable<string> files = Directory.EnumerateFiles(Directory.GetCurrentDirectory());
Console.WriteLine("3. LOOP THRU FILES & GET FULL FILE PATH:");
foreach (var file in files)
{
    // Outputs full path to a file
    Console.WriteLine(file);
}

// 3. Check if a directory exists using Directory.Exists(folderName)
string currDir = Directory.GetCurrentDirectory();
char sep = Path.DirectorySeparatorChar;
bool doesDirectoryExist = Directory.Exists($"{currDir}{sep}data");

/* 2️⃣ Directory + Path */
// 4. Create a new folder using Directory.CreateDirectory(folderName)
string currDir = Directory.GetCurrentDirectory();
Directory.CreateDirectory(Path.Combine(currDir, "data"));

/* 3️⃣ FileInfo */
// 5. FileInfo(fileName)
FileInfo info = new FileInfo("users.json");
Console.WriteLine("8. FileInfo (5 properties):");
Console.WriteLine($"FullName: {info.FullName}\nName: {info.Name}\nDirectory: {info.Directory}\nCreationTime: {info.CreationTime}");

/* 4️⃣ File + Path */
// 6. Create a file using File.WriteAllText(fileName, text)
File.WriteAllText(Path.Combine(currDir, "text.txt"), "Testing File.WriteAllText");

// 7. Read data from files using File.ReadAllText(fileName)
string text = File.ReadAllText(Path.Combine(currDir, "text.txt"));
Console.WriteLine("7. File.ReadAllText (text.txt):");
Console.WriteLine(text);

// 8. Append data to files
var appendedText = "Added using File.AppendAllText";
File.AppendAllText(Path.Combine(currDir, "text.txt"), $"{Environment.NewLine}{appendedText}");
string newText = File.ReadAllText(Path.Combine(currDir, "text.txt"));
Console.WriteLine("15. File.AppendAllText (text.txt):");
Console.WriteLine(newText);
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
using System;
using System.Collections.Generic;

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

- .Add(item), .RemoveAt(index), .Remove(item), .Inset(index, item), .Count(), .IndexOf(item), .LastIndexOf(item), .Contains(item), .Sort(), .Reverse() but it just reverses the list, not reverse sort, .Clear(), ToArray()

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

- Note `.Key` and `.Value` - are they keywords?
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
- .Contains, .Add, .Count

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

// Set underlying types and values for enums
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

- Use `enums` in C# to define named constants and prevent invalid values (?)
- By default, the underlying type of an `enum` is `int`, and the values start at `0`, incrementing by 1 for each member
  - you must explicity cast to an `(int)` if you want to get the value
- Use singular nouns for simple enums and plural nouns for flag enums (?)
- Provide a value of zero for simple enums, typically named `None`.

> Look into the `ToString()` method

### struct

> Skip structs

<!--
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

> Structs are worth diving deeper into and incorporating into a project
-->

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

Generics are not specific to any kind of data type

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

// another example
int[] intArray = {1, 2, 3};
double[] doubleArray = {1.0, 2.0, 3.0};
string[] stringArray = {"1", "2", "3"};

public static void DisplayItems<T>(T[] array) {
    foreach (T item in array) {
        Console.WriteLine(item);
    }
}
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

- .CompareTo, .Sort
- Generic interfaces are a key feature of advanced generics, allowing you to define type-safe contracts for implementing classes
- Some commonly used generic interfaces in .NET include:
  - `IEnumerable<T>`: Represents a collection of objects that can be enumerated
  - `IComparer<T>`: Defines a custom comparison for sorting objects
  - `IEqualityComparer<T>`: Defines custom equality logic for comparing objects

> Skip Generic math

### Covariance & Contravariance

> Skip this section

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

> Confusing

### Anonymous types

These looks like a basic object or object literal but usint the `new` keyword. Are they dictionaries?

```cs
// how to create an anonymous type
// 1.
var v = new { Amount = 108, Message = "Hello" };
Console.WriteLine($"{v.Amount} - {v.Message}");
// 2.
var person = new { Name = "John", Age = 30 };
// 3.
var product = new { Name = "Laptop", Price = 1200 };
Console.WriteLine($"Product: {product.Name}, Price: {product.Price}");
// 4.
var customer = new { Name = "Mario Rogers", Age = 30 };
Console.WriteLine($"Customer: {customer.Name}, Age: {customer.Age}");

// object initializer example
Cat myCat = new Cat { Name = "Fluffy", Age = 10 };
```

- Anonymous types in C# let you group related data into a temporary object without defining a full class
  - They allow you to create objects with _read-only properties_
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

## Attributes

Think of attributes as metadata tags you stick onto your code (like classes, methods, properties, or fields) to give extra information to the compiler, the runtime, or other libraries. They don't change the core logic of your code by themselves, but they tell something else how to treat it.

Without attributes, you'd have to write a lot of repetitive "boilerplate" code to configure how libraries interact with your data. Attributes let you handle configuration declaratively right where the code lives.

We generally use them for three major reasons:

1. Controlling Serialization
   - `[Serializable]`: This is an older, native .NET attribute. It tells the runtime: it's safe to convert this entire class into a binary stream.
   - `[JsonIgnore]`: Used by JSON libraries (like System.Text.Json or Json.NET). It tells the serializer, "Even though this property is part of my class, skip it and don't include it in the final JSON string."
2. Instructing the Compiler or Runtime: to give instructions directly to the C# compiler or the .NET runtime
   - `[Obsolete]`: Marks a method or class as outdated. If another developer tries to use it, the compiler will pop up a warning (or error) telling them to use something else.
   - `[Conditional("DEBUG")]`: Tells the compiler to only execute a method if the app is running in Debug mode.
3. Framework Configuration (Web APIs and Testing)
   - ASP.NET Core (Web APIs): You use attributes like `[HttpGet]` or `[Route("api/users")]` above a method to tell the framework, "When someone visits this specific URL, run this method."
   - Unit Testing: Frameworks like xUnit or NUnit use `[Fact]` or `[Test]` to know which methods are actually test cases that need to be executed.

```cs
// Built-in attributes
using System;
using System.Text.Json.Serialization;

[Serializable] // Tells .NET this class can be binary-serialized
public class UserProfile
{
    public string Username { get; set; }

    [JsonIgnore] // Tells JSON serializers to skip this property
    public string InternalSessionToken { get; set; }

    [Obsolete("Use DisplayNewFormat() instead.")] // Warns other developers
    public void DisplayOldFormat()
    {
        Console.WriteLine(Username);
    }
}

// Custom attribute
[AttributeUsage(AttributeTargets.Property)]
public class RequiredAttribute : Attribute { }

// Using custom attribute
public class User
{
    [Required]
    public string Name { get; set; }
}
```

<br>

## Asynchronous programming

Typical areas where asynchronous programming improves responsiveness:

- Web access: `HttpClient` - `Windows.Web.Http.HttpClient`, `SyndicationClient`
- Working with files: `JsonSerializer`, `StreamReader`, `StreamWriter`, etc. - StorageFile
- Working with images - MediaCapture, BitmapEncoder, BitmapDecoder
- WCF programming: Synchronous and Asynchronous Operations

```cs
// Example of how to create and call an asynchronous task
using System;
using System.IO;
using System.Threading.Tasks;

// I never have Main in Program.cs! See below
public static async Task Main()
{
    string filePath = "example.txt";
    string content = await ReadFileAsync(filePath); // really bad name!
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
    public static async Task Main() // Main again?
    {
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
```

Code that demonstrates the use of asynchronous REST API calls in C#.

```cs

using System;
using System.ComponentModel; // what is this
using System.Net.Http;
using System.Threading.Tasks;
using System.Text.Json;

using (HttpClient client = new HttpClient()) {
    try {
        // PetStore API endpoint
        string url = "https://petstore.swagger.io/v2/pet/findByStatus?status=available";
        // GET request to endpoint:
        HttpResponseMessage response = await client.GetAsync(url);
        // Throws exception if code is NOT 200-299:
        response.EnsureSuccessStatusCode();
        // Catch the response JSON/value:
        string responseBody = await response.Content.ReadAsStringAsync();
        // Console.WriteLine($"Response: {responseBody}");

        // Deserialize the JSON response into a list of pets
        var pets = JsonSerializer.Deserialize<List<Pet>>(responseBody);

        // Iterate through the list of pets and display their details
        // Why > 4, and why ToString()
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
- The `using` statement ensures that the `HttpClient` instance is disposed of properly after use, releasing any resources it holds
- File input and output (file I/O) can be performed synchronously or asynchronously
- Asynchronous file I/O is particularly useful for improving application performance and responsiveness
- The `System.IO` and `System.Text.Json` namespaces provide classes and methods for performing file I/O operations asynchronously
- the `System.ComponentModel` namespace provides classes and interfaces used to implement the run-time and design-time behavior of components and controls
- `EnsureSuccessStatusCode()` is a method on the `HttpResponseMessage` class that throws an `HttpRequestException` if the HTTP response's status code falls outside the 200-299 range (success)
  - verify that a request was successful before you attempt to process the response body
  - the exception message typically includes the status code that caused the failure

The `Main` method:

- The `Main` method is also defined as asynchronous, allowing it to call the `ReadFileAsync` method using the `await` keyword
  - **_I never have a Main method in my projects?!?_**
- When you use top-level statements, the compiler automatically assumes the hidden, behind-the-scenes Main method is async the moment you use the `await` keyword in your file

The `HTTPClient` class includes the following asynchronous methods:

- `GetAsync`: Sends a GET request to the specified URI and returns the response.
- `PostAsync`: Sends a POST request to the specified URI with the specified content and returns the response.
- `PutAsync`: Sends a PUT request to the specified URI with the specified content and returns the response.
- `DeleteAsync`: Sends a DELETE request to the specified URI and returns the response.
- `SendAsync`: Sends an HTTP request message and returns the response.

> For better HttpClient and API usage, see my repos [csharp-async-httpclient-example](https://github.com/Kernix13/csharp-async-httpclient-example) and [csharp-coingecko-api](https://github.com/Kernix13/csharp-coingecko-api).

Miscellaneous

- Thread.Sleep(ms)
- the main thread

```cs
Thread thread1 = new Thread(MethodName);
Thread thread2 = new Thread(MethodName2);
thread1.Start();
thread2.Start();
// or if param in method
Thread thread1 = new Thread(() => MethodName(arg));
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## LINQ

JavaScript array methods that are the same as Linq methods:

- `.filter()` -> `.Where()`
- `.map()` -> `.Select()`
- `.sort()` -> `.OrderBy()` / `.OrderByDescending()`
- `.find()` -> `.FirstOrDefault()`
- `.some()` -> `.Any()`
- `.every()` -> `.All()`
- `.includes()` -> `.Contains()`
- `.length` -> `.Count()`
- `.reduce()` -> `.Aggregate()`
- `.slice()` -> `.Skip()` / `.Take()`

```cs
// code below would be in a file named Person.cs
namespace Sandbox;

public class Person
{
    public string Name { get; set; } = string.Empty;
    public int Age { get; set; }
    public string Dept { get; set; } = string.Empty;
    public int yrsExperience { get; set; }
}

// In Program.cs
using System.Linq;
using System.Collections.Generic;

using Sandbox;

List<Person> people = new()
{
    new Person { Name = "Alice", Age = 25, Dept = "Marketing", yrsExperience = 3 },
    new Person { Name = "Bob", Age = 42, Dept = "Sales", yrsExperience = 5 },
    new Person { Name = "Charlie", Age = 31, Dept = "Marketing", yrsExperience = 2 },
    new Person { Name = "David", Age = 42, Dept = "IT", yrsExperience = 7 },
    new Person { Name = "Eve", Age = 21, Dept = "Sales", yrsExperience = 1 },
    new Person { Name = "Frank", Age = 31, Dept = "IT", yrsExperience = 4 }
};

/* Linq methods */
/* These return IEnumerable<T> */
// Add .ToList() when you actually want a List<T>. Otherwise, leave it off.
// 1. Where
var seniorEmployees = people
    .Where(p => p.Age >= 30)
    .ToList();

// 2. Select
var names = people
    .Select(p => p.Name)
    .ToList();

// Where + Select
var names2 = people
    .Where(p => p.Age >= 30)
    .Select(p => p.Name)
    .ToList();

// 3. OrderBy / OrderByDescending
var youngestFirst = people
    .OrderBy(p => p.Age)
    .ToList();
var oldestFirst = people
    .OrderByDescending(p => p.Age)
    .ToList();

// Where + OrderBy
var salesPeople = people
    .Where(p => p.Dept == "Sales")
    .OrderBy(p => p.Name)
    .ToList();

// Where + OrderBy + Select
var names3 = people
    .Where(p => p.Age >= 30)
    .OrderBy(p => p.Name)
    .Select(p => p.Name)
    .ToList();

// 4. Take
var firstThree = people
    .Take(3)
    .ToList();

// 5. Skip
var remaining = people
    .Skip(3)
    .ToList();

// Skip + Take
var page = people
    .Skip(10)
    .Take(5)
    .ToList();

// 6. Distinct
var departments = people
    .Select(p => p.Dept)
    .Distinct()
    .ToList();

// 7. GroupBy + ThenBy
var groups = people
    .GroupBy(p => p.Dept)
    .ToList();
var sorted = people
    .OrderBy(p => p.Dept)
    .ThenBy(p => p.Name)
    .ToList();

/* These return a single value. These end the query and produce a value. */
// 8. FirstOrDefault
var firstSalesPerson = people.FirstOrDefault(p => p.Dept == "Sales");

// 9. Any
bool hasMarketing = people.Any(p => p.Dept == "Marketing");

// 10. All
bool allAdults = people.All(p => p.Age >= 18);

// 11. Count
int salesCount = people.Count(p => p.Dept == "Sales");

// Also consider Min, Max, Sum, Average

// 12. Aggregate

// 13. Contains
List<string> names4 =
[
    "Alice",
    "Bob",
    "Charlie"
];
bool hasBob = names.Contains("Bob");
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Unit tests

Types of tests in automated testing:

1. Unit: test a unit (or multiple units) of the app WITHOUT their external dependencies (files, DBs, etc)
2. Integration: tests te app WITH its external dependencies - take longer (read/write to DB) but give you more confidence than unit tests
   - tests a few classes as a whole
3. End-to-end: drives an app through its UI - gives the greatest amount of confidence about your app but

- Unit tests are great to test conditional statements and loops - and methods with complex calculations and logic
- Use integration tests for data read / write to database
- naming convention: `DemoLibrary.Tests`

> ...look under the `.NET CLI Tools `or `DevOps/Testing` sections of Microsoft Learn

You do not need Visual Studio or its graphical "Test Explorer" to run tests. The .NET Core CLI was built precisely so you can do everything from a terminal inside VS Code.

xUnit vs NUnit vs MSTest

- NUnit - one of the earliest
- MSUnit - microsoft's testing framework built into visual studio
  - `TestClass`, `TestMethod`
  - The test runners looks for all TestClass & TestMethod attributes
- xUnit - popular
- they all give you:
  - a framework to write your tests and
  - a test runner that runs your tests - report Pass/Fail
- xUnit. It is the default choice for modern ASP.NET Core web APIs.
- It forces good habits because it isolates every single test completely

```cs
// --- XUNIT STYLE ---
[Fact]
public void VerifyDiscount_xUnit() {
    var result = Calculator.GetDiscount(100);
    Assert.Equal(20, result);
}

// --- NUNIT STYLE ---
[Test]
public void VerifyDiscount_NUnit() {
    var result = Calculator.GetDiscount(100);
    Assert.That(result, Is.EqualTo(20));
}

// --- MSTEST STYLE ---
[TestMethod]
public void VerifyDiscount_MSTest() {
    var result = Calculator.GetDiscount(100);
    Assert.AreEqual(20, result);
}
```

- inside every test method is 3 parts (triple A)
  - Arrange: where initialize your objects
  - Act: where you act on the object (call a method)
  - Assert: verify the result is correct
- NOTE: Test Explorer window vs console
- All your test methods should be `public void`
- NOTE: You do not have to test EVERYTHING and you do not need every layer of testing - start off small - start with the most complex methods

### MSTest

```cs
// MSTest
[TestClass]
public class ReservationTests {
  [TestMethod]
  // public void MethodToTest_Scenario_ExpectedBehavior() {  }
  public void CanBeCancelledBy_AdminCancelling_ReturnsTrue() {
    // Arrange
    var reservation = new Reservation();

    // Act
    var result = reservation.CanBeCancelledBy(new User { IsAdmin = true });

    // Assert
    Assert.IsTrue(result);
  }
}
```

### NUnit

- You need to install NuGet packages - make sure you are in the correct folder
- attribute differences:
  - [TestFixture]
  - [Test]

```sh
dotnet add package NUnit
dotnet add package NUnit3TestAdapter
```

- Assert.IsTrue(result); needs to change

```cs
Assert.That(result, Is.True); // or:
Assert.That(result == true);
```

### XUnit

- install: xunit, xunit.runner.console (?)

```cs
using DemoLibrary;
namespace DemoLibrary.Tests;
using Xunit;

public class CalculatorTests {

  [Fact]
  public void Add_IntegersShouldCalculate() {
    // Arrange
    double expected = 5;

    // Act: do the action you are testing
    double actual = Calculator.Add(3, 2);

    // Assert
    Assert.Equal(expected, actual);
  }
}
// Tests > Windows > Test Explorer
```

How to shorten the name that shows in Test Explorer

- in the Solution explorer right-click on DemoLibrary.Tests folder > Add > New Item > search for "json" > click JSON File > rename it to xunit.runner.json > then add the following:
- Then right-click on the json file > Properties > select Copy to Output > Build

```json
{
  "methodDisplay": "method"
}
```

- normal: [Fact]
- instead: [Theory] - allows you to pass in data and run a test multiple times
- `InlineData`: this allows you to populate the params

```cs
public class CalculatorTests {

  [Theory]
  // [InlineData(param1,param2,expected)]
  [InlineData(4,3,7)]
  [InlineData(21,5.25,26.25)]
  public void Add_IntegersShouldCalculate(double x, double y, double expected) {
    // Arrange

    // Act: do the action you are testing
    double actual = Calculator.Add(x, y);

    // Assert
    Assert.Equal(expected, actual);
  }
}
```

Complex methods

- They tend to not be one unit of work - single responsibility - break it up so the method only does one thing
  - Then test the individual methods not the main method
- NOTE: Don't test private methods
- moq, fake, shim framework - File.WriteAllLines - that is MS/C# code - you could write code to pretend to do that
- You can have more than 1 Assert in a test method but purist say only have 1

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

### Terminal Commands

```sh
# 1. Create a new test project (using xUnit as the example):
dotnet new xunit -o tests/MyWebApi.Tests

# 2. Link your test project to your API project
dotnet add tests/MyWebApi.Tests/MyWebApi.Tests.csproj reference src/MyWebApi/MyWebApi.csproj

# 3. Run your tests
dotnet test

# 4. Run tests automatically
dotnet watch test
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Building a CRUD REST Web API

Benefits of creating APIs in ASP.NET Core:

- Endpoints automatically serialize your classes to properly formatted JSON out of the box
- API endpoints have built-in support for industry-standard JSON Web Tokens (JWTs).
- ASP.NET lets you define routes and verbs inline with your code by using attributes
  - Data from the request path, query string, and request body are automatically bound to method parameters

```sh
# Option 1: Modern Minimal API
dotnet new webapi -o MyWebApi

# Option 2: Traditional Controller-Based API
dotnet new webapi -controllers -o MyWebApi
```

- Controller-based API: approach to building APIs in which each endpoint is mapped to a specific controller class
  - The controller handles the request, performs any necessary business logic, and returns a response
  - Consists of one or more controller classes that derive from `ControllerBase`
  - The `ControllerBase` class provides many properties and methods that are useful for handling HTTP requests
- `Controllers/`: Contains classes with public methods exposed as HTTP endpoints.
- By convention, controller class names are suffixed with `Controller`
- A controller is a public class with one or more public methods known as actions
  - The actions are exposed as HTTP endpoints via routing - inside the web API controller
  - inherits from the ControllerBase base class, the base class for working with HTTP requests
  - includes the two standard attributes: [ApiController] and [Route]
- `[ApiController]` enables opinionated behaviors that make it easier to build web APIs.
  - Some behaviors include parameter source inference, attribute routing as a requirement, and model validation error-handlingenhancements\*.
- `[Route]` defines the routing pattern `[controller]`.
  - the `[Route]` attribute defines a mapping to the [controller] token
  - The controller's name (case-insensitive, without the Controller suffix) replaces the `[controller]` token
  - The controller's name (case-insensitive, without the Controller suffix) replaces the `[controller]` token

### API controller class attributes:

```cs
using Microsoft.AspNetCore.Mvc;

using ContosoPizza.Models;
using ContosoPizza.Services;

[ApiController]
[Route("api/[controller]")]
// [Route("[controller]")]
public class PizzaController : ControllerBase
{
    public PizzaController()
    {
    }

    // GET all action

    // GET by Id action

    // POST action

    // PUT action

    // DELETE action
}
```

### Http file:

- `.http` file: Contains configuration to test REST APIs directly from VS Code
  - Click the Sent Request command above the GET which sends a request to the running service

```http
@ProjectName_HostAddress = http://localhost:5118

###
GET {{ProjectName_HostAddress}}/api/endpoint/
Accept: application/json
```

### Data store and models

You need a model class to represent an object in your inventory. The model contains properties that represent the characteristics of the object. The model is used to pass data in the web API and to persist object options in the data store.

- Model classes can go anywhere in the project, but the `Models` folder is used by convention
- A model is a set of classes that represent the data that the app manages
- The model contains properties that represent the characteristics of the object
- The model is used to pass data in the web API

```cs
// namespace ProjectName.FolderName;
namespace ContosoPizza.Models;

public class Pizza
{
    public int Id { get; set; }
    public string? Name { get; set; }
    public bool IsGlutenFree { get; set; }
}
```

### Services

A Service is a class that holds your business logic.

- PizzaService.cs provides a simple in-memory data caching service (for demo purposes)
  - The constructor creates 2 pizza objects
  - method to retreive all pizza objects
  - method to find a pizza by id
  - method to add a new pizza object
  - method to delete a pizza object by id
  - method to update a pizza object by id

> See [PizzaService.cs](https://github.com/Kernix13/ContosoPizza/blob/main/Services/PizzaService.cs) for code examples

### CRUD actions in ASP.NET Core

- GET: Read -> `[HttpGet]`
- POST: Create -> `[HttpPost]`
- PUT: Update -> `[HttpPut]`
- DELETE: Delete -> `[HttpDelete]`

#### GET

The `ActionResult` type is the base class for all action results in ASP.NET Core. It automatically returns data with a Content-Type value of application/json

- The routing logic registers `[HttpGet]` (without id) and `[HttpGet("{id}")]` (with id) as two different routes

```cs
// controllers/PizzaController.cs
[HttpGet]
public ActionResult<List<Pizza>> GetAll() =>
    PizzaService.GetAll();
```

#### POST

To enable users to add a new item to the endpoint, you must implement the POST action by using the [HttpPost] attribute.

- The `[HttpPost]` attribute maps HTTP POST requests sent to `http://localhost:5000/api/pizza` by using the `Create()` method
- This method returns an `IActionResult` response
- `IActionResult` lets the client know if the request succeeded and provides the ID of the newly created pizza
- `CreatedAtAction`: uses the action name to generate a location HTTP response header with a URL to the newly created pizza
- NOTE: Because the controller is annotated with the `[ApiController]` attribute, it's implied that the Pizza parameter will be found in the request body.

```cs
[HttpPost]
public IActionResult Create(Pizza pizza)
{
    PizzaService.Add(pizza);
    return CreatedAtAction(nameof(Get), new { id = pizza.Id }, pizza);
}
```

#### PUT

Modifying or updating a pizza in our inventory is similar to the POST method that you implemented, but it uses the [HttpPut] attribute and takes in the id parameter in addition to the Pizza object that needs to be updated.

```cs
[HttpPut("{id}")]
public IActionResult Update(int id, Pizza pizza)
{
    if (id != pizza.Id)
        return BadRequest();

    var existingPizza = PizzaService.Get(id);
    if(existingPizza is null)
        return NotFound();

    PizzaService.Update(pizza);

    return NoContent();
}
```

#### DELETE

One of the easier actions to implement is the DELETE action, which takes in just the id parameter of the pizza to remove from the in-memory cache:

```cs
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    var pizza = PizzaService.Get(id);

    if (pizza is null)
        return NotFound();

    PizzaService.Delete(id);

    return NoContent();
}
```

### Methods in Program.cs

```cs
// Initialize the builder with command-line arguments:
var builder = WebApplication.CreateBuilder(args);

/* DEPENDENCY INJECTION */
// Add services: Registers API controllers:
builder.Services.AddControllers();
// Generates the data structure:
builder.Services.AddEndpointsApiExplorer();
// Creates the webpage UI:
builder.Services.AddSwaggerGen();

// Build the application instance:
var app = builder.Build();

/* MIDDLEWARE PIPELINE */
// Configure HTTP request path
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}
// Enable HTTPS redirection middleware
app.UseHttpsRedirection();
// Enable authorization in an ASP.NET Core application
app.UseAuthorization();

// Map Endpoints
app.MapControllers();

// Start the web application
app.Run();
```

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

## Basic Web Api

I am not interested in building a basic web api but here are the "best of" notes for that.

- ASP.NET core: a framework to build web apps, includes middleware, built-in support for building web APIs

```sh
# Creates a minimal ASP.NET Core application with very little included
dotnet new web -n ProjectName
```

```cs
// Starter code in Program.cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.Run();
```

- Web Application builder: The web application used to configure the HTTP pipeline and routes - provides you with APIs
- Minimal apis allow you to describe how requests should be processed by a server by using an endpoint
- There are 3 components for defining how a web request should be handled:

```cs
//    1     2    3 --------------- |
app.MapGet("/", () => "Hello World!");
/*
  1. The http method: MapGet
  2. The url route: "/"
  3. The handler: () => "Hello World!"
      - executes when an incoming request is processed that matches the method & the route
*/
```

- Run dotnet run or click the Play button top right in Program.cs, then open a browser to the API endpoint, or use the `.http` file to send requests

```cs
// Results needs the following using statement
using Microsoft.AspNetCore.Http.HttpResults;
// RewriteOptions needs the following using statement
using Microsoft.AspNetCore.Rewrite;
```

#### Middleware:

- Middleware: a piece of code that can run before & after each request is processed
  - Logic that runs on every http request sent to the server
- ASP.NET core has middleware built-in or you can write your own middleware
- NOTE: middleware is usually registered with the Use keyword - indicates you want to register a middleware
- `app.Use()`
  - `context`: represents the current request and response
  - `next`: to invoke the next middleware

```cs
// Logger middleware
app.Use(async (context, next) =>
{
    // code here, e.g.
    Console.WriteLine($"[{context.Request.Method} {context.Request.Path} {DateTime.UtcNow}] started");
    await next(context);
});
```

#### Dependency injection:

- Dependencies: are objects that other objects can depend on
  - Usually implemented via C# classes and interfaces
  - Dependencies can also be referred to as Services b\c they are stored in the service container
  - A Service is a class that holds your business logic

SKIP: Endpoint filters

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>

<br>

## Terms or Keywords to learn or use

- Jagged arrays
- `??`: null-coalescing operator - work this into my code more
- `static` properties
- `private` properties
- `readonly` properties
- `virtual` keyword for methods
- `abstract` keyword for methods
- `override` keyword for methods
- `params` keyword
- `this` keyword
- `base` keyword and `base()`
- `JsonSerializerOptions`
- `[JsonIgnore]`
- `required` modifier
- `using System.ComponentModel;`
- `HttpResponseMessage`
- `EnsureSuccessStatusCode`
- `.Content.ReadAsStringAsync`
- `JsonNamingPolicy`

<div align="right">&#8673; <a href="#back-to-top" title="Table of Contents">Back to Top</a></div>
