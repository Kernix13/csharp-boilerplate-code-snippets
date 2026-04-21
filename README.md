# CSharp Boilerplate Code Snippets: Generic Examples for Common Code Blocks

Code snippets and important syntax for important code blocks in C#.

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
  // process name here
}

for (int i = 0; i <> someArray.Length; i++) {
  // code here
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

// without {}

// Conditional operator

// switch
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

## Microsoft Learn Problems

These are some specific problems that I found difficult

### Add looping logic to your code using the do-while and while statements in C#

#### Exercise - Complete a challenge activity to differentiate between do and while iteration statements

1. Code project 1 - write code that validates integer input

- Your solution must include either a do-while or while iteration.
- Before the iteration block: your solution must use a Console.WriteLine() statement to prompt the user for an integer value between 5 and 10.
- Inside the iteration block:
  - Your solution must use a Console.ReadLine() statement to obtain input from the user.
  - Your solution must ensure that the input is a valid representation of an integer.
  - If the integer value isn't between 5 and 10, your code must use a Console.WriteLine() statement to prompt the user for an integer value between 5 and 10.
  - Your solution must ensure that the integer value is between 5 and 10 before exiting the iteration.
- Below (after) the iteration code block: your solution must use a Console.WriteLine() statement to inform the user that their input value has been accepted.

✅ **SOLUTION**:

```cs
string? readResult;
string valueEntered = "";
int numValue = 0;
bool validNumber = false;

Console.WriteLine("Enter an integer value between 5 and 10");

do {
    readResult = Console.ReadLine();
    if (readResult != null) {
        // This if block and the line below seems unnecessary - confusing ❌
        valueEntered = readResult;
    }

    validNumber = int.TryParse(valueEntered, out numValue);

    if (validNumber == true) {
        if (numValue <= 5 || numValue >= 10) {
            validNumber = false;
            Console.WriteLine($"You entered {numValue}. Please enter a number between 5 and 10.");
        }
    }
    else {
        Console.WriteLine("Sorry, you entered an invalid number, please try again");
    }
} while (validNumber == false);

Console.WriteLine($"Your input value ({numValue}) has been accepted.");

readResult = Console.ReadLine();

// Enter an integer value between 5 and 10
// two
// Sorry, you entered an invalid number, please try again
// 2
// You entered 2. Please enter a number between 5 and 10.
// 7
// Your input value (7) has been accepted.
```

<br>

2. Code project 3 - Write code that processes the contents of a string array

- Your solution must use the following string array to represent the input to your coding logic:

```cs
string[] myStrings = new string[2] { "I like pizza. I like roast chicken. I like salad", "I like all three of the menu choices" };
```

- Your solution must declare an integer variable named periodLocation that can be used to hold the location of the period character within a string.
- Your solution must include an outer foreach or for loop that can be used to process each string element in the array. The string variable that you'll process inside the loops should be named myString.
- In the outer loop, your solution must use the IndexOf() method of the String class to get the location of the first period character in the myString variable. The method call should be similar to: myString.IndexOf("."). If there's no period character in the string, a value of -1 will be returned.
- Your solution must include an inner do-while or while loop that can be used to process the myString variable.
- In the inner loop, your solution must extract and display (write to the console) each sentence that is contained in each of the strings that are processed.
- In the inner loop, your solution must not display the period character.
- In the inner loop, your solution must use the Remove(), Substring(), and TrimStart() methods to process the string information.

✅ **SOLUTION**:

```cs
string[] myStrings = new string[2] { "I like pizza. I like roast chicken. I like salad", "I like all three of the menu choices" };
int stringsCount = myStrings.Length;

// I forgot this variable - I mutated the original strings
string myString = "";
int periodLocation = 0;

for (int i = 0; i < stringsCount; i++) {
    myString = myStrings[i];
    periodLocation = myString.IndexOf(".");

    string mySentence;

    // extract sentences from each string and display them one at a time
    while (periodLocation != -1) {

        // first sentence is the string value to the left of the period location
        mySentence = myString.Remove(periodLocation);

        // the remainder of myString is the string value to the right of the location
        myString = myString.Substring(periodLocation + 1);

        // remove any leading white-space from myString
        myString = myString.TrimStart();

        // update the comma location and increment the counter
        periodLocation = myString.IndexOf(".");

        Console.WriteLine(mySentence);
    }

    mySentence = myString.Trim();
    Console.WriteLine(mySentence);
}

/*
 I Forgot myString:
 - Work with a separate, mutable string,
 - Practice reassigning a variable repeatedly
 - Avoid directly manipulating the array element
 🚫 My version: Directly modifies the array
*/

// I like pizza
// I like roast chicken
// I like salad
// I like all three of the menu choices
```

<br>
