# There Five basic steps of the V8 Engine.
1. Parser
2. AST
3. Interpreter
4. Profiler
5. Compiler

## JIT
Now, these engines use a technology named Just-in-time compilation to convert JS into machine code.
just-in-time (JIT) compilation is a way of executing computer code that involves compilation during execution of a program (at run time) rather than before execution.

------------------------------------------------------------------------------------
Compiled languages compile code into the machine code all at once (they call it Ahead of Time Compilation or AOT), but in interpreted languages, codes are interpreted line by line But I think the most important difference here is compiler never executes code at all.
------------------------------------------------------------------------------------
Interpretation executes the code line by line. Some Javascript engines like Hermes, (the engine which React Native uses), doesn’t use a JIT compiler.

The most interesting part of JIT is Once the code starts running, it can optimize it.

## Working
***Check if the first second step is the fist one ***
1. Every javascript engine has its own implementation, but in V8, source code goes into the module name Tokenizer <sub> (Lexical analysis or lexer or scanner are another name for Tokenizer)</sub>.
The tokenizer is responsible for dividing the input stream into individual tokens.

2. Then those tokens goes to the Parser (or syntactic analysis). 
Parser is responsible for checking the syntax.
If it finds error, it sends the error, and if the code is valid, it generates something called AST .

3. We should also say that this happens at Static time or Compile time. This means by this moment; we haven’t actually started executing our program. All we did was just translate it to several intermediate representations. There is no actual execution yet. 

4. Then this AST goes to another module named **ByteCode Emitter** and it creates the next intermediate representation known as **bytecode**. We can think of it as an abstract of machine code.

5. Now this Bytecode, goes to another part named Interpreter (this happens at run time) and then Interpreter creates the MachineCode.

6. The reason that the ByteCode Emitter does not create a machine code directly is that machine codes depend on the architect of the Microprocessor, but bytecode is universal;
Another reason is we can do a lot of optimization on the bytecodes. This is where JIT does a lot.

------------------------------------------------------------------------------------
Imagine the situation when we have some heavy-weight function that does some complex calculation, and this function is called multiple times during the program execution. Eventually, calling this function might become a bottleneck. What JIT really do here is it gets the MachineCode from that part of the code. Getting MachineCode means now it knows e.g, where all variables related to that code are located in the memory and many more … So when you call this function again, if the parameters is the same, it uses that MachineCode.
------------------------------------------------------------------------------------

7. The module that do this optimization in V8 is called Turbofan. (in Firefox engines that call it Ionmonkey)

