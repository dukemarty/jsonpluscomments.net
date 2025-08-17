# 📘 JsonPlusComments.Net Whitepaper  

## ReconfLang: A Declarative Language for Transforming Nested Data Structures in Comment-Aware JSON


### 📌 Abstract

This paper introduces a declarative rule format called **ReconfLang** for migrating comment-aware JSON configurations using *JsonPlusComments.Net*. Unlike traditional transformation engines that discard comments, this format preserves comment fidelity while enabling expressive, maintainable migration logic. It is designed to support schema evolution, key renaming, value rewriting, and conditional transformations in a human-readable syntax.

---

### 🎯 Goals

- Preserve comments during transformation
- Support schema evolution and config migrations
- Enable declarative, readable rule definitions
- Integrate seamlessly with JsonPlusComments.Net

---

### 🧱 Rule Format Overview

The migration rule format is a **JSON-based DSL** with the following structure:

```json
{
  "rules": [
    {
      "match": "logging.level",
      "action": "rename",
      "to": "log.level"
    },
    {
      "match": "features.enableBeta",
      "action": "delete"
    },
    {
      "match": "server.port",
      "action": "set",
      "value": 8080,
      "comment": "Updated default port for v2"
    },
    {
      "match": "security.auth",
      "action": "move",
      "to": "auth.config"
    }
  ]
}
```

---

### 🧩 Rule Actions

| Action     | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| `rename`   | Renames a key while preserving its value and comments                      |
| `delete`   | Removes a key and its associated comments                                  |
| `set`      | Sets a new value, optionally adding a comment                              |
| `move`     | Moves a key to a new location in the tree                                  |
| `copy`     | Copies a key to a new location, preserving comments                        |
| `transform`| Applies a custom function to the value                                     |

---

### 🧠 Advanced Features

- **Comment Injection**: Add or update comments during migration
- **Conditional Rules**: Apply transformations only if certain conditions are met
- **Wildcard Matching**: Use `*` or regex to match multiple keys
- **Rule Groups**: Organize rules by version or feature
- **Configurable Path Separator**: `.` by default, but also `:` (typical for IConfiguration context) and `/` are possible

---

### 🛠 Sample Migration Scenario

#### Original Config
```jsonc
{
  // Logging settings
  "logging": {
    "level": "info"
  },
  "features": {
    "enableBeta": true
  },
  "server": {
    "port": 3000
  }
}
```

#### Migration Rules
```json
{
  "rules": [
    { "match": "logging.level", "action": "rename", "to": "log.level" },
    { "match": "features.enableBeta", "action": "delete" },
    { "match": "server.port", "action": "set", "value": 8080, "comment": "Updated default port for v2" }
  ]
}
```

#### Resulting Config
```jsonc
{
  // Logging settings
  "log": {
    "level": "info"
  },
  "server": {
    // Updated default port for v2
    "port": 8080
  }
}
```

---

### 🔌 Integration with JsonPlusComments.Net

The migration engine will be exposed via:

```csharp
var migrated = JsonPlus.Migrate(originalConfig, migrationRules);
```

Internally, it will traverse the comment-aware AST, apply transformations, and preserve comment placement.

---

### 📈 Future Extensions

- Rule validation and dry-run mode
- Visual diffing of config before/after migration
- Rule versioning and rollback support
- Plugin system for custom transformation logic

---

Would you like me to expand this into a full Markdown document or help implement a parser for this rule format?