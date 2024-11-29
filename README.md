# Mini Compiler Project

This is a simple mini-compiler project implemented using **Lex** and **Yacc** (Flex and Bison in Linux). It performs lexical and syntax analysis on a source code file, generates intermediate code (Three Address Code), optimizes it, and produces machine code.

---

## How to Run

Follow these steps to run your mini-compiler on **Linux** or **Windows**.

### 1. Install Required Tools

#### For Linux (Ubuntu/Debian-based systems):

1. **Update your package list:**
sudo apt-get update

2. **Install Bison, Flex, and GCC:**
sudo apt-get install bison flex gcc

- **Bison** is the GNU version of **Yacc**.
- **Flex** is a tool for generating lexical analyzers (lexical scanning).
- **GCC** is the GNU Compiler Collection used for compiling C code.

#### For Windows (Using MSYS2 or Cygwin):

##### Option 1: MSYS2 (Recommended)

1. **Download and Install MSYS2:**
- Go to the [MSYS2 website](https://www.msys2.org) and follow the installation instructions.
- After installation, open the **MSYS2 terminal**.

2. **Install Bison, Flex, and GCC:**
- Run the following command in the **MSYS2 terminal**:
  ```
  pacman -S mingw-w64-x86_64-bison mingw-w64-x86_64-flex mingw-w64-x86_64-gcc
  ```

##### Option 2: Cygwin

1. **Download and Install Cygwin** from [Cygwin's official website](https://www.cygwin.com/).
2. During installation, **select Bison**, **Flex**, and **GCC** packages.
3. After installation, open the **Cygwin terminal**.

---

### 2. Prepare Your Files

Make sure you have the following files in your working directory:

- **`mini.l`** (Lex file for lexical analysis)
- **`mini.y`** (Yacc/Bison file for parsing)

---

### 3. Generate C Code from the `.l` and `.y` Files

Now that the necessary tools are installed, follow these steps to generate the required C files:

#### Step 1: Generate the Lexical Analyzer Code
In your terminal (whether on Linux or Windows), run:
flex mini.l

This will generate a file called **`lex.yy.c`**.

#### Step 2: Generate the Parser Code
Run the following command to generate the parser code:
bison -d mini.y

This will generate:
- **`y.tab.c`** (C code for the parser)
- **`y.tab.h`** (Header file for the parser)

#### Step 3: Compile the Generated Code
Once you have the **`lex.yy.c`** and **`y.tab.c`** files, compile them using **GCC**:
gcc -o minicompiler lex.yy.c y.tab.c

This command:
- Compiles the Lex and Yacc generated C files.
- (Optionally) Links the Lex library (`-ll`) and the Yacc library (`-ly`).
- Generates an executable file named **`minicompiler`**.

---

### 4. Run the Compiler

After successful compilation, you can now run the **minicompiler**.

Use the following command to run the compiler:
./minicompiler


Make sure you have an input file (e.g., **`input.c`** or **`input.txt`**) with source code to compile.
