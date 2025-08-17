# JsonPlusComments.Net

**JsonPlusComments.Net** is a .NET library for parsing, editing, and serializing JSON—with full comment support and zero apologies. Inspired by JSONC, but not bound by it, this library preserves comment structure, position, and formatting like a pro.

Whether you're wrangling config files, building dev tools, or just tired of your JSON being a silent partner, JsonPlusComments.Net lets your data speak human.

> 🐞 **Tagline:** *“Comments aren’t bugs. They’re features.”*

---

### Why Use This?

- Supports both `//` and `/* */` comments
- Keeps comments exactly where you left them
- Ideal for readable configs, editors, and tooling
- Extensible for custom comment handling
- Built for .NET devs who like their JSON with a side of sass

---

### Coming Soon

- Sample usage
- NuGet install instructions
- API docs
- ...
- and first and foremost: some implementation 😅

---

### 📄 Project Rationale

💡 Why does this library exist?

Modern .NET apps rely heavily on JSON-based configuration files like appsettings.json. But when these configs evolve—new features, renamed keys, deprecated settings—developers are left manually updating files, often losing valuable comments and user edits in the process.

JsonPlusComments.Net aims to fix that.

By preserving comment structure and formatting, this library lays the groundwork for safe, systematic config migrations—where updates can be applied programmatically without erasing human context.

Check out the full whitepaper:  
📘 [Preserving Meaning: Comment-Aware JSON for Configuration in .NET](docs/comment-aware-json-whitepaper.md)

> *“Comments aren’t bugs. They’re features.”*


### 🧠 Philosophy of Comment Handling

Comments aren’t just decoration — they carry meaning, intent, and context. To explore how JsonPlusComments.Net treats comments during transformations like attribute moves, merges, and renames, read the blue paper:

📘 [Comment Handling Blue Paper](docs/comment-handling-bluepaper.md)  
A deep dive into how comments are preserved, transformed, and respected across JSON structures.

