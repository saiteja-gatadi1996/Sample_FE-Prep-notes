### 1. Javascript Engine:

- There is a **_ECMAScript standard_** which tells that how things work in a specific pattern in Javascript.
- `ECMAScript` is the governing body of `JS` that essentially decides <ins>how the language should be standardized</ins>.

#### Javascript V8 Engine:

- Written in `C++` programming language
- When we provide the JS files, there will be lexical analysis happening (e.g. refer below screenshot)
  ![alt text](/js/JS_Advanced_Concepts/images_used/compressed_Images/Javascript_Engine.png)

#### <ins>**_Our JS code is broken into tokens (ex: parser is one of the token we can refer to)_**</ins>

- And these tokens are formed into <ins>**Abstract Syntax Tree** (AST)</ins>. For more details explore website: https://astexplorer.net
- And from `AST`, the code will go through the `Interpreter` and it spits out into `Bytecode` (which is able to be interpreted by Javascript engine)
- **Profiler** is also called as a `monitor` and **watches our code** as it runs and notes on optimizing the code.
- So if the same lines of code are run a few times we pass to the compiler (or JIT Compiler) and this compiler helps us to make optimizations **<ins>and then it replaces the sections on where it could be improved of the bytecode with optimized machine</ins>**

---

**Note**: There are **two** ways to run Javascript (Interpreter, Compiler)

#### <ins>Interpreter:</ins>

- `translates` and `read the files` **<ins>line by line on the fly</ins>**.
- **_<ins>Converts the JS code into Bytecode_**</ins>.
- Interpreters are usually fast as they don't need to translate into other language
- **The _problem_ with `interpreters`** is **<ins>running the same code more than once</ins>**, (e.g. loop over 1000 times even though it gives same result), it can get really slow.

#### <ins>Complier:</ins>

- **<ins>doesn't translates code on the fly</ins>** whereas it tries to understand what we want to do and **<ins>takes our language and changes</ins>** it into something else.

- Compiler actually **<ins>helps us to overcome the problem of Interpreter mentioned above</ins>**,
- It <ins>**_takes a little bit more time to start up_**</ins> because it has to go through that compilation (e.g. go through the entire code and spit into another language)
- Compiler is `smart` enough (e.g. when it sees code like this that we just loop over and over), it **<ins>can**</ins> just **<ins>simplify**</ins> the code.
- **So, instead of calling multiple times,** just replace this function with the output (output which is rendered after every iteration e.g. 5+4=9)
- **_As the compiler doesn't need to repeat the translation for each pass through in that loop_**, the code generated from it is actually faster. And these sort of things is called optimization

- As we have seen that both have pros and cons, <ins>**_that is why they came up with combining both Compiler & Interpreter_**</ins> and created **JIT Compiler** which is called as <ins>**_Just In Time Compiler_**</ins>.
- <ins>**_Browsers started using JIT compiler_**</ins> to make the engines faster.
