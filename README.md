# CSharp Boilerplate Code Snippets: Generic Examples for Common Code Blocks

Code snippets and important syntax for important code blocks in C#.

## Snippets

### Shell commands

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

### Terms or Keywords to learn

- `void`
- `static`
- `!` (null-conditional operator)
- `new string[#]` or `new int[#]`

### Parse, Convert, and Cast

```cs
// Convert.ToInt32, int.Parse vs int.TryParse(strVar, out numVar)
```

### Loop examples

```cs
for (int i = 0; i < arr.Length; i++) {
    // code
}

foreach (int val in iterable) {
    // code
}
```

## Conditionals

```cs
// basic

// without {}

// Conditional operator

// switch
```

## Array syntax

```cs
int[] times = {800, 1200, 1600, 2000};

// 2D
int[,] result = { {-1,-1},{-1,-1},{-1,-1},{-1,-1},{-1,-1} };

// Jagged
```

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

### Methods

```cs
void MethodName() {}
int MethodName(int paramName) {}
string MethodName(string paramName, string param2 = "Hello") {}
```
