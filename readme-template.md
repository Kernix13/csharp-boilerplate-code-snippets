# TITLE HERE: Generic README template for C# Console projects

Intro paragraph here, between 120-158 characters

<br>

## Overview

More in-depth description of prohect than the intro paragraph

<br>

## Prerequisites

- [.NET SDK 10.0](https://dotnet.microsoft.com/en-us/download)
- [Visual Studio Code](https://code.visualstudio.com/) with [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit)
- Other...
  <br>

## Installation & Usage

1. Clone this repository and switch into project folder

   ```sh
   git clone https://github.com/Kernix13/REPO_NAME
   cd REPO_NAME
   ```

2. Create a solution file

   ```sh
   dotnet new sln
   ```

3. Link the project to the solution

   ```sh
   dotnet sln add REPO_NAME.csproj
   ```

4. Run the application

   ```bash
   dotnet run
   ```

5. Build the application

   ```bash
   dotnet build
   ```

### ⚡ Quick Start

<!-- I t hink h3 elements should have an emoji/icon at the beginning -->

```sh
git clone https://github.com/Kernix13/REPO_NAME
cd REPO_NAME
dotnet new sln
dotnet sln add REPO_NAME.csproj
dotnet run
```

<br>

## Other H2 sections that make sense for console projects

### Related H3 sections

> See [csharp-template.md](https://github.com/Kernix13/cy-pathway-readmes/blob/main/csharp-template.md) for more sections if your console app has more features to it.

## H3 Emoji list

For large READMEs I have a Table of Contents and include H3 sections unless the TOC is very large, then I just include H2 headings in the TOC. If I have a TOC then I also have a back-to-top "button" aligned to the right so that gives me some spacing.

I use `<br>` to add spacing between `h2` sections, but I do not want to do that for `h3` sections. However, I would like to make the H3 headings stand out, so that is where I will prefix the H3 text with an emoji. Here is a good starter list:

```
⚡Action / getting started
   ⚡ Quick Start (perfect choice already)
   ⚙️ Setup / Configuration / Settings
   💻 Usage / Commands / Virtual Environment
   🛠️  Tooling / debugging / Troubleshooting
   🔧, 🔨 Repair, maintenance, construction

📚 Information / reference
   📌 Key info / notes
   📄 Documentation details
   ℹ️ General info
   🧩 Concepts / Component / piece of logic

🚨 Errors / problems / alert
   ⚠️ Warning
   🛠️ Troubleshooting
   ❌ Errors
   🚫 Something went wrong
   🛑 Stop (stronger emphasis)
   🔔, ⌛ Alert / alarm / time-dependent

🔗 External stuff
   🔗 Resources
   📎 Examples / attachments / docs
   🌐 live deploy / website

🎯 Insight / emphasis
   🎯 Key takeaway / best practice
   💡 Ideas / tips
   ❗ Important

Specific
   ✨ or 🚀 Features
   🚧 WIP
   🐛 Bug fix
   🎯 Bullseye: Key takeaway, Focus point, Goal/Target outcome
   📌,📍 Point of focus or To-Do
   ✅, ☑️, ✔️ - Done / complete
   📄, 📝 Docs
   🔍 → implies search
   💡 → ideas
   ℹ️ info
   👥 Contributors
   ❓, 🧐  Questions/Issues
   💖,💚, 💙, 💜, Sponsorship / Like
   👉, ➡️ Look here

Generic
   🔹 Small blue diamond → clean, minimal section marker
   🔷 Large Blue Diamond
   🔸 Small Orange Diamond
   🔶 Large Orange Diamond
   ▪️ Small square → even more subtle
```
