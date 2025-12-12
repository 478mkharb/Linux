### 📘 Text Editing & Template Engine Scripts

- This repository contains two useful Bash utilities:

- otTextEditor.sh – A lightweight text-file editing toolkit

- tePlateEngine.sh – A simple template processing engine using key=value replacements

- Both scripts are designed to simplify common DevOps and Linux automation tasks.
  
---
### 🛠️ 1. otTextEditor.sh — Text Editing Script

A Bash script built around sed to perform common text-editing operations such as inserting, updating, and deleting lines.

###🔹 Supported Operations
Action	Description
```
echo "./otTextEditor.sh addLineTop <file> <line>"
echo "./otTextEditor.sh addLineBottom <file> <line>"
echo "./otTextEditor.sh addLineAt <file> <linenumber> <line>"
echo "./otTextEditor.sh updateFirstWord  <file> <word> <word2>"
echo "./otTextEditor.sh updateAllWords <file> <word> <word2>"
echo "./otTextEditor.sh insertWord <file> <word1> <word2> <word-to-be-inserted>"
echo "./otTextEditor.sh deleteLine <file> <line no>"
echo "./otTextEditor.sh deleteLine <file> <line no> <word>"
```
---
###🔹 Usage
#### ➤ Add a line at the top
```bash
./otTextEditor.sh addLineTop file.txt "Hello World"
```

#### ➤ Add a line at the bottom
```
./otTextEditor.sh addLineBottom file.txt "End of file"
```

#### ➤ Add a line at a specific line number
```
./otTextEditor.sh addLineAt file.txt 4 "Line inserted at number 4"
```

#### ➤ Update first occurrence of a word
```
./otTextEditor.sh updateFirstWord file.txt old new
```

#### ➤ Update all words
```
./otTextEditor.sh updateAllWords file.txt error warning
```

#### ➤ Insert word after match
```
./otTextEditor.sh insertWord file.txt hello world InsertedText
```

#### ➤ Delete a line
```
./otTextEditor.sh deleteLine file.txt 7
```

#### ➤ Delete line only if it contains a word
```
./otTextEditor.sh deleteLine file.txt 7 keyword
```
---
###🔹 Script Concepts Used

- sed for all text transformation

- Functions (addLineTop, updateAllWords, etc.)

- case statement for command selection

- shift for argument repositioning

- Conditional checks to validate inputs
  
---

### 🛠️ 2. tePlateEngine.sh — Template Processor

A simple template engine that replaces placeholders inside a template file using key=value arguments.

###🔹 Features

- Replace multiple variables at once

- Perfect for config generation, CI/CD pipelines

- Accepts unlimited key=value pairs

- Works with any text-based template
  
---
###🔹 Usage
```
./tePlateEngine.sh template.txt name=Mukesh city=Delhi role=DevOps
```

###🔹 Example
Template File (template.txt)
```
Hello {{name}}
Welcome to {{city}}
Role: {{role}}
```

After Running Script
```
Hello Mukesh
Welcome to Delhi
Role: DevOps
```
---
###🔹 Script Concepts Used

- Looping through arguments

- key=value parsing:

```
${pair%%=*} → key

${pair#*=} → value
```
- Replacing strings globally using sed

- Storing file contents in variables
  
---
### 📦 Folder Structure
```
Assignment4/
├── otTextEditor.sh
├── tePlateEngine.sh
└── README.md
```
