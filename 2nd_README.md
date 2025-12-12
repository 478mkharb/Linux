# ⭐ Bash Pattern & Number Utility Scripts

This repository contains two simple and useful Bash scripts:

- `drawStar.sh` — A star (`*`) pattern generator with multiple designs  
- `printTomcat.sh` — A number divisibility checker (3, 5, 15)

---

## 1️⃣ drawStar.sh — Star Pattern Generator

`drawStar.sh` prints different types of star (`*`) patterns based on the user input.

### 🔹 Supported Patterns

| Pattern | Function | Description |
|--------|----------|-------------|
| t1 | `t1 <n>` | Left-aligned increasing triangle |
| t2 | `t2 <n>` | Left-aligned decreasing triangle |
| t3 | `t3 <n>` | Right-aligned increasing triangle |
| t4 | `t4 <n>` | Right-aligned decreasing triangle |
| t5 | `t5 <n>` | Pyramid |
| t6 | `t6 <n>` | Inverted pyramid |
| t7 | `t7 <n>` | Diamond pattern |

### 🔹 Usage
```
./drawStar.sh <pattern> <number>
```

### 🔹 Examples
```
./drawStar.sh t1 5
./drawStar.sh t5 7
./drawStar.sh t7 9
```
### 🔹 Sample Output (Pyramid: t5 5)
 ````
         *
       * * *
     * * * * *
   * * * * * * *
 * * * * * * * * *
````

---

## 2️⃣ printTomcat.sh — Number Divisibility Checker

`printTomcat.sh` checks whether a given number is divisible by:

- **3**
- **5**
- **15**

### 🔹 Usage
```
./printTomcat.sh <number>
```

### 🔹 Examples
```
./printTomcat.sh 15
./printTomcat.sh 9
./printTomcat.sh 10
```
### 🔹 Possible Output
```
15 is divisible by 15.
9  is divisible by 3.
10 is divisible by 5.
7  is not divisible by 3, 5, or 15.
```

---

## ▶️ Make Script Executable

```
chmod +x drawStar.sh 
chmod +x printTomcat.sh
```

---

## ▶️ Run Them
