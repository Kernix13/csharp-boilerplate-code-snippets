# CSharp Boilerplate Code Snippets: Generic Examples for Common Code Blocks

Code snippets and important syntax for important code blocks in C#.

> I have not updated this README much but the 2 "tables" markdown files list methods/properties actually used in Microsoft Learn exercises and list of methods not used in MS Learn. Use those files to focus on the syntax to learn and use.

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

## Terms or Keywords to learn

- `void`
- `static`
- `!` (null-conditional operator)
- `new string[#]` or `new int[#]`

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

Console.ReadLine()
```

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

<br>

## Methods

```cs
void MethodName() {}
int MethodName(int paramName) {}
string MethodName(string paramName, string param2 = "Hello") {}
```

<br>

## Classes

```cs
// syntax here
```

## ???

<br>
