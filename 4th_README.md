## 📘 File Editing & Template Processing Utilities

Two simple but powerful Bash scripts that help you modify files and replace variables in templates with ease.

---

## 📝 1. File Editing Utility Script

A Bash script that performs common file editing operations such as adding lines, updating text, inserting words, and deleting lines using sed.

## 🚀 Features
###     🔹 Features

-   ➕ Add a line at the top of a file

-   ➕ Add a line at the bottom

-   ➕ Insert a line at a specific line number

-   🔄 Replace first occurrence of a word

-   🔁 Replace all occurrences

-   📝 Insert a word after a match

-   ❌ Delete lines (entire line or only if it contains a word)

## 📂 What Concepts This Script Uses
### 🧩 Functions

Each operation is isolated into a function:
```
addLineTop

addLineBottom

addLineAt

updateFirstWord

updateAllWords

insertWord

deleteLine
```
🧩 Case Statement

The action name determines which function is executed.

🧩 Sed

Powerful stream editor used for:

Inserting text

Deleting lines

Word replacement

Pattern matching

Zero-occurrence (first-only) replacement

🧩 Command Argument Shifting

shift is used to reposition arguments after reading the action.

🔧 Usage Examples
➤ Add a line at the top
./script.sh addLineTop file.txt "Hello World"

➤ Add a line at the bottom
./script.sh addLineBottom file.txt "This is the last line"

➤ Add a line at line number 5
./script.sh addLineAt file.txt 5 "Inserted at line 5"

➤ Replace the first occurrence of a word
./script.sh updateFirstWord file.txt apple mango

➤ Replace all occurrences of a word
./script.sh updateAllWords file.txt error warning

➤ Insert a word after a match
./script.sh insertWord file.txt hello world insertedWord

➤ Delete a line (example: delete line 8):
./script.sh deleteLine file.txt 8

➤ Delete line if it contains a word:
./script.sh deleteLine file.txt 8 keyword

📝 2. Template Variable Replacement Script

A simple script to replace placeholders in a template file using key=value pairs.

🚀 Features

✔ Replace variables dynamically
✔ Unlimited key=value pairs
✔ Useful for config files, HTML templates, Kubernetes manifests, etc.

🔧 Usage
./replace.sh template.txt name=Mukesh city=Delhi role=DevOps

Example Template:
Hello {{name}},
Welcome to {{city}}.
Role: {{role}}

After running script:
Hello Mukesh,
Welcome to Delhi.
Role: DevOps

🧩 What This Script Uses
✔ Argument parsing

$1 = template file
Remaining arguments = key=value style pairs

✔ Parameter expansion

key="${pair%%=*}" → extract text before "="

val="${pair#*=}" → extract text after "="

✔ Sed replacement

Replaces all occurrences of each key with value.
