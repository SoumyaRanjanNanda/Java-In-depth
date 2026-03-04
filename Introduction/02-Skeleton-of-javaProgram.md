#  Java Skeleton Code (Deep Explanation)

Java skeleton code means the **basic structure** of a Java program.

Here is the most basic Java program:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

Now we break it down deeply 

---

# 1️⃣ `public class Main`

### ➤ `class`

Everything in Java must be inside a class.

Java is:

* Object Oriented
* Class-based language

### ➤ `Main`

This is the class name.

Rule:

* File name must match class name.
* File name: `Main.java`
* Class name: `Main`

If mismatch → Compilation error ❌

### ➤ `public`
Definition:

public is an access modifier.

Meaning:

It makes the class accessible from anywhere. If you remove public, the class becomes package-private.

In Java:

* public

* private

* protected

* default

For main class, usually we write public.
Means this class is accessible from anywhere.

---

# 2️⃣ `public static void main(String[] args)`

This is the most important line.

This is the **entry point** of a Java program.

When you run:

```
java Main
```

JVM searches for:

```java
public static void main(String[] args)
```

If it does not find it → Program will not run ❌

---

## Let’s break it word by word:

### 🔹 `public`

JVM must access it from outside the class.

### 🔹 `static`
why static ? 

JVM calls main method **without creating object**.

If main was non-static:
```java
public void main(...)
```

Then JVM would need an object to call it.

But program hasn’t started yet 😄

So static is required.
We don’t write:

```java
new Main().main();
```

JVM directly calls it because it is static.

### 🔹 `void`

It returns nothing. only run and exit 

### 🔹 `main`

Special method name recognized by JVM.
Entery point of a program

### 🔹 `String[] args`

Command line arguments.
This is command line argument array.

Definition:

String[] → Array of Strings 

args → variable name
```
java Main Aapun 22
```

Then:

```java
args[0] = "Aapun"
args[1] = "22"
```
So main method receives input from command line.
You can also write:

```java
public static void main(String a[])
```

Both valid.
---

# 3️⃣ `System.out.println()`

Let’s break this 

* `System` → class
* `out` → static object inside System
* `println()` → method of PrintStream

Actually:

* `System`
* `out`
* `PrintStream`
* `println()`

Very clearly.

---

#  First Look at the Statement

```java
System.out.println("Hello");
```

This is NOT one thing.

It is a **chain of relationships**.

---

# 1️⃣ `System`

## System

### ✅ What it is:

A class inside `java.lang`.

### ✅ Role:

It provides system-level utilities.

Inside it, there is something important:

```java
public static final PrintStream out;
```

So `System` owns a variable called `out`.

---

# 2️⃣ `out`

### ✅ What it is:

A **static variable** inside `System`.

Type of `out` is:

## PrintStream

So:

```java
System.out
```

means:

Access variable `out` from class `System`.

---

# 3️⃣ `PrintStream`

### ✅ What it is:

A separate class in `java.io`.

It contains methods like:

* print()
* println()
* printf()

So `PrintStream` is the class that actually knows **how to print**.

---

# 4️⃣ `println()`

### ✅ What it is:

A method inside `PrintStream` class.

So when you write:

```java
System.out.println("Hello");
```

You are calling a method of the `PrintStream` object.

---

#  Now The Full Relationship

Here is the exact connection:

```
System (Class)
   |
   |-- static variable --> out
                             |
                             |-- object of --> PrintStream
                                                   |
                                                   |-- method --> println()
```

---

#  Step-by-Step Execution

When program runs:

1. JVM loads `System` class.
2. JVM creates a `PrintStream` object.
3. That object is stored inside `System.out`.
4. When you write:

```java
System.out.println("Hello");
```

It means:

* Go to `System` class
* Get static variable `out`
* That gives you a `PrintStream` object
* Call `println()` method on that object

---

#  Real Life Analogy

Imagine:

* `System` = Company
* `out` = Printer machine owned by company
* `PrintStream` = Type/model of printer
* `println()` = Pressing print button

You are doing:

"Company’s printer → press print button"

---

#  Technical Breakdown

This line:

```java
System.out.println("Hello");
```

Is equivalent to:

```java
PrintStream ps = System.out;
ps.println("Hello");
```

So:

* `System.out` returns a `PrintStream` object
* `println()` is called on that object

---

#  Important Concept

`System` is a class
`out` is a variable
`PrintStream` is a class
`println()` is a method

---

#  Final Professional Definition

> `System.out.println()` is a chained access expression where the static variable `out` of the `System` class (which holds a `PrintStream` object) is used to invoke the `println()` method defined inside the `PrintStream` class to write data to the standard output stream.

---


If `out` is static, but `println()` is not static,
how are we able to call `println()` without creating an object?

Think and answer ?


---
# 3️⃣ `Packages Com.Company`
packages are used to group the realted classes

The "packages" keyword is used to create packages in java

here Com.Company is the name of our Package







#  Full Professional Skeleton (Production Style)

```java
package com.aapun.app;

import java.util.*;

public class Main {

    public static void main(String[] args) {
        System.out.println("Application Started");
        
        Main app = new Main();
        app.run();
    }

    public void run() {
        System.out.println("Running business logic...");
    }
}
```

This is more realistic structure.

---

#  What Happens Internally (Very Important)

When you run Java:

### Step 1:

```
javac Main.java
```

Compiler converts to bytecode → `Main.class`

### Step 2:

```
java Main
```

JVM:

* Loads class into memory
* Verifies bytecode
* Finds main method
* Executes

---

#  Interview Level Question

 Can we overload main method?

Yes ✅

```java
public static void main(int a) {
    System.out.println(a);
}
```

But JVM only calls:

```java
public static void main(String[] args)
```

---

#  Advanced Skeleton (Multiple Classes)

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(5, 10));
    }
}
```

---

# 💡 Important Rules

✔ Only one public class per file
✔ File name must match public class name
✔ main method must be exactly correct signature
✔ Program execution starts from main

---
