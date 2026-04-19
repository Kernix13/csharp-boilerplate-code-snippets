# TITLE HERE: Generic README template for C# Console projects

Intro paragraph here, between 120-158 characters

<!-- Google: "sample readme for a c# console application" for good boilerplate -->

<br>

## Overview

More in-depth description of the project than the intro paragraph

<br>

## Prerequisites

- [.NET SDK 10.0](https://dotnet.microsoft.com/en-us/download)
- [Visual Studio Code](https://code.visualstudio.com/) with [C# Dev Kit](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit)
- Other...
  <br>

## Installation & Usage

1. Clone this repository and switch into project folder

   ```sh
   git clone https://github.com/USER_NAME/REPO_NAME
   cd REPO_NAME
   ```

2. Run the application

   ```bash
   dotnet run
   ```

3. Build the application

   ```bash
   dotnet build
   ```

### <span aria-hidden="true">⚡</span> Quick Start

<!-- I t hink h3 elements should have an emoji/icon at the beginning -->

```sh
git clone https://github.com/USER_NAME/REPO_NAME
cd REPO_NAME
dotnet run
```

<br>

> Other H2 & H3 sections that make sense for console projects:
> See [csharp-template.md](https://github.com/Kernix13/cy-pathway-readmes/blob/main/csharp-template.md) for more sections if your console app has more features to it.

## H3 Emoji list

For large READMEs I have a Table of Contents and include H3 sections unless the TOC is very large, then I just include H2 headings in the TOC. If I have a TOC then I also have a back-to-top "button" aligned to the right so that gives me some spacing.

I use `<br>` to add spacing between `h2` sections, but I do not want to do that for `h3` sections. However, I would like to make the H3 headings stand out, so that is where I will prefix the H3 text with an emoji. But here is how you shouls use a `<br>` element:

- `<span aria-hidden="true"><br></span>`

Screen readers will read the emoji's "Alt Text" name first

- Example: ### 🔍 Analysis Method
- What a Screen Reader says: "Heading Level 3: Magnifying glass tilted left Analysis Method"
- The Fix: Wrap the emoji in a `<span>` with an `aria-hidden="true"` attribute. This hides the emoji from screen readers while keeping it visible for your sighted users
  - `<span aria-hidden="true">🗃️</span>`

Here is a good starter list:

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
   📊 📈 📶 📉 Analysis
   📢 Announcement
   🚩 Not sures

Generic
   🔹 Small blue diamond → clean, minimal section marker
   🔷 Large Blue Diamond
   🔸 Small Orange Diamond
   🔶 Large Orange Diamond
   ▪️ Small square → even more subtle
```
