# All about dem Virtual Machines
Repo for my notes on creating interpreters/virtual machines

## Fundamentals
* Language Design
  * EBNF
  * Parser Generators
    * Antlr
* Lexers/Tokenizers/Scanners
  * These words are all used interchangebly
  * Takes a stream of free-form text and returns tokens
* Parsers
  * Types of Parsers
  * Takes a stream of tokens and returns a tree-like structure (AST)
* Abstract Syntax Trees
  * Can be walked using Visitor pattern
    * Output of walking can be runtime interpretation and evaluation
    * Alternatively can emit compiled bytecode instructions
* Semantic Analysis
  * Sets expectations about the meaning of the AST
    * Example: An if block should have a condition and one or more else blocks
* Stack-based VMs
  * Push/Pop
  * Mimics evaluation of expression in [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation)
* Register-based VMs
  * Register Allocation
* Tree-walking Interpreters
  * Generally slower than bytecode solutions
  * Utilizes visitor pattern to walk AST and evaluate
* Bytecode Virtual Machines
  * Execute raw-byte instructions
  * Understanding Bytecode
    * Opcodes
    * Operands

## Reference Articles

### A Python Interpreter written in Python - Allison Kaptur
Byterun is a Python bytecode interpret written in Python itself in about 500 LOCS. It does some cheating to handle more advanced language features by dispatching operations to some of Python's real built-in feature set but it wonderfully demonstrates the concept of a stack-based VM such as CPython itself. It also supports a lot of language features but should largely be considered a learning experiemnt and not a productionized solution.

* [Article - About Byterun](https://www.aosabook.org/en/500L/a-python-interpreter-written-in-python.html)
* [Repo - Byterun Github](https://github.com/nedbat/byterun)
* [Presentation - 1500 line switch powers Python](https://www.slideshare.net/akaptur/a-1500-line-switch-statement-powers-your-python-allison-kaptur-con-2014)

### 16-Bit Virtual Machine in JavaScript
This series of videos on YouTube demonstrates using JavaScript to create a VM using low-level techniques in a higher-level language.

* [Video 001](https://www.youtube.com/watch?v=fTBwD3sb5mw&t=841s)
* 16-bit
* Interrupts

### Simple Virtual Machine - Bartosz Sypytkowski
Demonstrates a very basic bytecode interpret using C but avoids using any complex constructs. Limited to simple integer operations.

* [Site](https://bartoszsypytkowski.com/simple-virtual-machine/)
* Stack based
* C implementation
* Local/Global storage
* Jump/Call/Ret instructions

### Stack-based virtual machines
An incredibly easy to follow 8 part series on creating a simple toy stack VM with very clear code and explanations. The great thing about this tutorial is the unit tests and detailed instruction sets that actually demonstrate working programs.

* [Site](https://andreabergia.com/stack-based-virtual-machines/)
* Stack based
* Java
* functions, assembler, antlrv4

### Toy Machine - Robert Sedgewick (Princeton)
Princeton articles on the specification and implementation of the Toy machine which is a series of articles and exercises on a simple register-based VM.

* [Site](https://introcs.cs.princeton.edu/java/62toy/)
* Register based

### Bytecode - Game Programming Patterns
This article, demonstrates a simple VM solution written in C++ where the technique of treating code as data to illustrate a simple Domain Specific Language and a VM runtime can be utilized within the context of a game to simplify and express logic in a higher abstraction. (That was a mouthful)

* [Site - gameprogrammingpatterns.com](https://gameprogrammingpatterns.com/bytecode.html)
* Written in C++
* Emphasis on game DSL
* Stack-based

### So you want to build a language VM - Fletcher Haynes
This blog contains a multi-part (30+) overview of the theory and practice of building of significantly involved feature rich virtual machine. The Part 1 page also contains some great references to yet more VM articles. This series demonstrates code in Rust.

* [Site - blog.subnetzero.io](https://blog.subnetzero.io/post/building-language-vm-part-01/)

### Crafting Interpreters - Bob Nystrom
TODO
* [Site - craftinginterpreters.com](https://craftinginterpreters.com)


### Write your own Virtual Machine - Justin Meiners & Ryan Pendleton
Comprehensive mini-book that demonstrates an old-school [LC3](https://en.wikipedia.org/wiki/Little_Computer_3) virtual machine that was originally designed for the purpose as a teaching tool. 
* [Site](https://justinmeiners.github.io/lc3-vm/)
* [Repo](https://github.com/justinmeiners/lc3-vm)

### Further Reading

* Links
  * [Awesome Compilers](https://github.com/aalhour/awesome-compilers)
* Books
  * [Interpreter Book](https://interpreterbook.com/)
  * [Compiler Book](https://compilerbook.com/)
  * [CreateYourProgLang.com](http://createyourproglang.com/) (payed e-book)
* Talks
  * [How to Build a Virtual Machine](https://youtu.be/OjaAToVkoTw) - Terence Parr
    * [Related Code](https://github.com/parrt/simple-virtual-machine)
  * [Exploring Python Bytecode - Anjana Vakil](https://www.youtube.com/watch?v=GNPKBICTF2w)
    * Quick talk on using Python's built-in tooling to understand its internal bytecode opcodes


  
## Production Ready VMS

### Wren
Wren is a modern, small and embeddable scripting-language that supports classes and runs on a C-based virtual machine. It uses computed GOTOs in order to get a significant speed increase over having a large switch/case block. Wren is pretty damn fast and supports a light-weight C-language.

* [Site - wren.io](http://wren.io/)
  * [Performance](http://wren.io/performance.html)
* Features
  * Stack-based VM
  * C-like language
  * Concurrency via Fibers (coop)
  * Fast

### ScummVM

ScummVM is an open-source community-driven effort to build support for old games. The tool actually provides *many* different types of VMs for a myriad of game engines that have been analayzed and reverse engineered for many years now. Two particular game engines are worth reading the source: The first is the AGI (Adventure Game Interpreter) which is Sierra Online's original game interpreter for their mid-1980's games such as King's Quest 1 and Leisure Suit Larry 1. The other is the SCI interpreter which is for a newer generation of games by Sierra Online.

Due to the nature of these virtual machines being created via the effort of reverse engineering, they are not always fully implemented or contain hacks/workarounds that the original implementations probably didn't need.

* [Site - Scummvm.org](https://www.scummvm.org/)
* [Repo - github.com](https://github.com/scummvm/scummvm)
