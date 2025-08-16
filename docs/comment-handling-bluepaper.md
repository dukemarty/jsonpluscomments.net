# 📘 JsonPlusComments.Net Blue Paper  
## Principles and Practices for Comment Preservation in Structured Data

---

### 1. Introduction

Comments in structured data formats like JSON are often treated as disposable — stripped during parsing, ignored during transformation, and lost in serialization. JsonPlusComments.Net challenges this norm by treating comments as **first-class citizens** in configuration files and tooling.

This blue paper outlines the **philosophy**, **rules**, and **use cases** for handling comments with care, especially when attributes are moved, merged, or transformed. It aims to guide developers, tool authors, and architects in preserving the **semantic intent** behind comments.

---

### 2. Comment Semantics

#### 📝 Types of Comments
- **Inline Comments (`//`)**: Typically short, contextual notes.
- **Block Comments (`/* */`)**: Used for longer explanations or multi-line annotations.

#### 📍 Positional Meaning
- **Leading Comments**: Appear before a key/value pair. Often describe the attribute.
- **Trailing Comments**: Appear after a value. May describe context or usage.
- **Detached Comments**: Stand alone within a structure. Often describe the structure itself.

#### 🧠 Ownership
- A comment is considered **owned** by the nearest key/value pair if:
  - It immediately precedes the key.
  - It is inline with the key or value.
- Otherwise, it may be **owned by the structure** or treated as **global context**.

---

### 3. Use Case Scenarios

#### a. Moving Attributes Between Structures

**Example**: Moving `"timeout"` from `network` to `global`.

```jsonc
{
  "network": {
    // Time to wait before retrying
    "timeout": 5000
  }
}
