# In-Class Project: The Ridiculous Life Advice Machine (RLAM) 🤖✨

A console application project demonstrating core C++ paradigms: procedural decomposition, function prototypes, loops, control structures, and standard library functions (`<iostream>`, `<cstdlib>`, `<ctime>`, and `<cmath>`).

## 📌 Project Overview

Congratulations! You have been hired by a highly questionable technology company to develop its newest software product: **The Ridiculous Life Advice Machine (RLAM)**.

This application provides three essential services:
1. **Motivational Message Generator:** Generates inspirational messages of dubious practical utility.
2. **Ridiculous Excuse Generator:** Produces randomized batches of recycled everyday excuses.
3. **Unscientific Luck Score Calculator:** Computes an official luck quotient using a completely unscientific mathematical formula.

Despite the questionable nature of the advice, your program architecture must be clean, robust, and strictly follow procedural C++ conventions!

## 🎯 Learning Objectives

This project evaluates your ability to:
* Organize a single C++ source file using **function prototypes** placed before `main()` and **function definitions** placed after `main()`.
* Implement value-returning functions for input handling and input validation.
* Implement a `while` or `do-while` loop for menu control.
* Use a counting `for` loop to repeat operations a variable number of times.
* Define and invoke **void functions** with and without parameters.
* Define and invoke **value-returning functions** that pass back calculated results.
* Utilize C++ standard libraries: `<iostream>`, `<cstdlib>`, `<ctime>`, and `<cmath>`.
* Format terminal input and output clearly and predictably.

## 📂 Source Code Architecture

All code must reside within a single source file named `main.cpp`. Do not create or include external header (`.h`) files.

Your file must follow this strict vertical layout:
1. **Header Includes & Directives:** Preprocessor directives (`#include`) and namespace declaration.
2. **Function Prototypes:** Forward declarations placed directly above `main()`.
3. **Main Driver Function:** `int main()` containing random seeding, loop control driven by `getMenuOption()`, and branching logic.
4. **Function Definitions:** Full implementations of all four functions placed *below* `main()`.

### Required Prototypes

Place these exact function prototypes directly above `int main()`:

```cpp
// ==========================================
// FUNCTION PROTOTYPES (Must be above main)
// ==========================================
int getMenuOption();
void motivationalMessage();
void generateExcuses(int quantity);
int calculateLuck(int age, int luckyNumber);
```

## 🛠️ Program Specifications

### Part 1: Menu Input Function (`getMenuOption`)
* **Prototype:** `int getMenuOption();`
* **Type:** Value-returning function, no parameters.
* **Responsibilities:**
  1. Display the formatted menu:
     ```text
     -----------------------------------------------
     RIDICULOUS LIFE ADVICE MACHINE
     -----------------------------------------------
     1. Motivational Message Generator
     2. Ridiculous Excuse Generator
     3. Calculate Your Luck Score
     4. Exit
     -----------------------------------------------
     Enter your choice (1-4): 
     ```
  2. Prompt the user for an integer choice.
  3. Validate that the input is between `1` and `4`. If the user enters an invalid number, output an error message and reprompt until valid.
  4. Return the validated integer choice back to the caller.

### Part 2: Main Driver (`int main`)
* Seed the random number engine at the start of `main()`:
  ```cpp
  srand(static_cast<unsigned int>(time(nullptr)));
  ```
* Call `getMenuOption()` repeatedly inside a loop (`while` or `do-while`).
* Use a `switch` or `if / else if` block to dispatch execution based on the returned choice:
  * **Option 1:** Call `motivationalMessage()`.
  * **Option 2:** Prompt for the quantity of excuses, then call `generateExcuses(quantity)`.
  * **Option 3:** Prompt for age and lucky number, call `calculateLuck(age, luckyNumber)`, and print the result.
  * **Option 4:** Terminate the loop and display:  
    `"Thank you for using the Ridiculous Life Advice Machine!"`

### Part 3: Option 1 — Motivational Message Generator
* **Prototype:** `void motivationalMessage();`
* **Type:** Void function, no parameters.
* **Requirements:**
  1. Generate a random integer between `1` and `5` using `(rand() % 5) + 1`.
  2. Use a `switch` or `if / else if` block to print one of the following quotes:
     * **1:** Believe in yourself. Even your Wi-Fi router believes it can reach the basement.
     * **2:** Never give up. Unless you're trying to fold a fitted sheet.
     * **3:** Success is 10% inspiration and 90% remembering your password.
     * **4:** Follow your dreams. But maybe check your bank account first.
     * **5:** You are capable of amazing things. Just not necessarily before coffee.
  3. **Do not return a value** from this function.

#### Sample Output:
```text
-----------------------------------
YOUR DAILY MOTIVATION:
-----------------------------------
Never give up. Unless you're trying to fold a fitted sheet.
```

### Part 4: Option 2 — Ridiculous Excuse Generator
* **Prototype:** `void generateExcuses(int quantity);`
* **Type:** Void function with one integer parameter.
* **Requirements in `main()`:**
  1. Prompt the user: `"How many excuses would you like? "`
  2. Store the user's input in an integer variable (e.g., `userQty`).
  3. Pass `userQty` as an argument to `generateExcuses(userQty);`.
* **Requirements inside `generateExcuses(int quantity)`:**
  1. Accept `quantity` as an argument.
  2. Use a `for` loop that runs from `1` through `quantity`.
  3. For each iteration, generate a random number from `1` to `5`.
  4. Print the numbered excuse corresponding to the generated number:
     * **1:** My computer was updating its feelings.
     * **2:** I was attacked by a particularly aggressive houseplant.
     * **3:** My alarm clock and I are no longer on speaking terms.
     * **4:** I accidentally entered a staring contest with my refrigerator.
     * **5:** My homework was abducted by highly educated aliens.
  5. Recycled excuses are acceptable.

#### Sample Output:
```text
How many excuses would you like? 3
YOUR OFFICIAL EXCUSES:
Excuse 1: My computer was updating its feelings.
Excuse 2: My homework was abducted by highly educated aliens.
Excuse 3: My alarm clock and I are no longer on speaking terms.
```

### Part 5: Option 3 — Calculate Your Luck Score
* **Prototype:** `int calculateLuck(int age, int luckyNumber);`
* **Type:** Value-returning function with two integer parameters.
* **Requirements in `main()`:**
  1. Prompt for user age: `"Enter your age: "`
  2. Prompt for lucky number: `"Enter your lucky number: "`
  3. Call `calculateLuck(userAge, userLuckyNumber)` and store the returned value.
  4. Print the returned score and confirmation message from inside `main()`.
* **Requirements inside `calculateLuck(int age, int luckyNumber)`:**
  1. Print `"Calculating your luck score..."`.
  2. Compute the score using `<cmath>` functions `sqrt()` and `ceil()`:

> **Calculation Formula:**  
> `Luck Score = ceil(sqrt(age) * luckyNumber)`


3. **Return** the integer score to `main()`.
4. **Important:** `calculateLuck` must **NOT** print the final score itself. Output must occur within `main()`.

#### Sample Output:
```text
Enter your age: 25
Enter your lucky number: 7
Calculating your luck score...
Your official luck score is: 35
This number has no scientific meaning, but it looks impressive!
```


## ⚙️ Compilation and Execution

Compile and execute your program to ensure that it functions properly.
