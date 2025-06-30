# JAVA
- **Not officially**: *Just Another Virtual Accelerator*
- High-level, Object-Oriented programming language.
- Supports hot-swapping, very dynamic language.

## How does JAVA run:
1. Code written in `.java` file.
2. **Compiling**: 
> It generate bytecode `.class` file.
   - Java being platform-independent programming language, doesn't work on one-step compilation. Instead, it involves a two-step execution
	 1. Through an OS-independent compiler
	 2. In virtual machine(JVM) *custom-built for every OS*.
   - `.java` file **passes through compiler**, **encodes source code** into machine-independent encoding, known as **Bytecode**.
   - This code is stored in `.class` file.
3. Run Bytecode in JVM

### Compilation
1. Parse: Read a set of `*.java` source files and maps resulting token sequence into AST - nodes.
2. Enter: Enters symbols for definitions into symbol table.
3. Process annotations: Can be found in specified compilation units if requested.
4. Attribute: Includes name resolution, type checking and constant folding.
5. Flow: Perform dataflow analysis on tree, checks for assignments and scopes.
6. Desugar: Rewrite AST and translates away some syntactic sugar.
7. Generate: `.class` file

### Execution
- Main class file is passed to JVM, go through 3 main stages before execution:
1. **ClassLoader:**
> - JVM doesn't accept file as parameter, instead JVM is responsible for locating and loading file itself
> - We are telling this is class I want to run
> - JVM are designed to think in terms of classes and packages not file paths. It uses class loader to locate and load file
```java
// loadClass function prototype

Class r = loadClass(String className, boolean resolveIt);
	// className: name of the class to be loaded
	// resolveIt: flag to decide whether any referenced class should be loaded or not.
```
> - It's B/c, Java is made of many classes (often in packages, spread across dir or JARs)
   - Part of JVM responsible for loading your compiled classes into memory.
   - When program it loads main class and as per references it loads other classes.
   - Maps *name of class* -> *class body in memory*
   - Uses hierarchy of class loaders (bootstrap loader, extension loader, application loader).
   - 2 type of class loaders
	 1. primordial: *embeded into alll JVM and default class loader*
	 2. non-primordial: *user-defined class loader, can be customize*
   **namespace**: a set of name each uniquely identifies something
   **flat namespace**: 
   > If two class loader, both load class `Main`, JVM treats these as different class b/c of diff namespace.
   - Inside class loader, part of JVM machinery, each class loader have its own flat namespace.
   - class loader keep single list or map, where each class name is unique, there is no nested or hierarchical structure in flat namespace.
   ```java
   "java.lang.String"  // → class object for String
   "com.mygame.Player" // → class object for Player
   "Main"              // → class object for Main

   ```
   - each class loader has its own namespace.
2. Bytecode Verifier:
   - After bytecode loaded by class loader, It is **inspected by bytecode verifier**.
   - It check that instruction dont perform damaging action.
   - It checks Variables *initialized before use*, Method *match type of object reference*, private data and method.
   - **When calling method**, JVM creates a stack frame on runtime stack *aka. call stack*
   > Runtime Stack doesn't overflow, due to value in heap and reference on stack
   - This frame holds:
	 - Local variables
	 - Operand stack *arithmethic*
	 - Return address *where to go after method end*
   > If anything fails, verifier doesnt allow class to load
3. Just-In-Time Compiler:
   - Convert bytecode into machine code.
   - When using JIT compiler, Speed java program by converting bytecode into native machine code at runtime, so CPU can execute it directly, rather than interpreting line-by-line.
   - JVM watches which part of code run often, translate entire method bytecode into native code, it get cached and run directly on CPU.

[![Buy more Internet](https://media.geeksforgeeks.org/wp-content/uploads/java.jpg)]

## JAVA history
- **1995:** Java 1.0 — Applets, basic networking, simple GUI.
- **1998:** Java 2 — Swing (new GUI toolkit), Collections framework, better performance.
- **2004:** Java 5 — Generics, enums, enhanced for-loop, annotations.
- **2011:** Java 7 — try-with-resources, better exception handling.
- **2014:** Java 8 — Lambda expressions, Streams API → functional-style programming.
- **2017 onwards:** better performance, modular system (Jigsaw), more functional features, pattern matching.
   
# Source
- [Google](google.com)
- [Getting Started](https://dev.java/learn/getting-started/)
- [Compilation and Execution of a Java Program](https://www.geeksforgeeks.org/java/compilation-execution-java-program/)
- [History](chatgpt.com)


- [emacs lisp](https://github.com/ianyepan/.wsl-emacs.d/)
