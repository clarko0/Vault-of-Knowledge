
Here's a simple program I want to compile:
```c
int main() {
	return 2;
}
```

The GCC compiler produces the following x86 assembly:
```s
    .section __TEXT,__text_startup,regular,pure_instructions
    .align 4
    .globl _main
_main:
    movl    $2, %eax
    ret
    .subsections_via_symbols
```

We can ignore the `.section`, `.align` and `.subsections_via_symbols` directives, leaving us with our actual assembly instructions:
```s
_main:                  ; label for start of "main" function
    movl    $2, %eax    ; move constant "2" into the EAX register
    ret                 ; return from function
```

The most important point here is that when a function returns, the EAX register will contain its return value. The `main` function’s return value will be the program’s exit code.

We’ll split up the compiler into three stages: `lexing`, `parsing`, and `code generation`.

### Lexing

The lexer (also called the scanner or tokenizer) is the phase of the compiler that breaks up a string (the source code) into a list of tokens. A token is the smallest unit the parser can understand - if a program is like a paragraph, tokens are like individual words. (Many tokens _are_ individual words, separated by whitespace.) Variable names, keywords, and constants, and punctuation like braces are all examples of tokens.

Here are the list of tokens from our program:
- `int` keyword
- Identifier “main”
- Open parentheses
- Close parentheses
- Open brace
- `return` keyword
- Constant “2”
- Semicolon
- Close brace

Here are all the tokens your lexer needs to recognize, and the regular expression defining each of them:

- Open brace `{`
- Close brace `}`
- Open parenthesis `\(`
- Close parenthesis `\)`
- Semicolon `;`
- Int keyword `int`
- Return keyword `return`
- Identifier `[a-zA-Z]\w*`
- Integer literal `[0-9]+`

If you want, you could just have a “keyword” token type, instead of a different token type for each keyword.

### Parsing

The next step is transforming our list of tokens into an abstract syntax tree. An AST is one way to represent the structure of a program. In most programming languages, language constructs like conditionals and function declarations are made up of simpler constructs, like variables and constants. ASTs capture this relationship; the root of the AST will be the entire program, and each node will have children representing its constituent parts. Let’s look at a small example:

```c
if (a < b) {
    c = 2;
    return c;
} else {
    c = 3;
}
```

This code snippet is an if statement, so we’ll label the root of our AST “if statement”. It will have three children:

- The condition (`a < b`)
- The if body (`c = 2; return c;`)
- The else body (`c = 3;`)

Each of these components can be broken down further. For example, the condition is a binary `<` operation with two children:

- The first operand (variable `a`)
- The second operand (variable `b`)

An assignment statement (like `c=2;`) also has two children: the variable being updated (`c`), and the expression assigned to it (`2`).

The if body, on the other hand, can have an arbitrary number of children - each statement is a child node. In this case it has two children because there are two statements. The children are ordered - `c=2;` precedes `return c;` because it comes first in the source code.

Here’s the full AST for this code snippet:

![Image of diagram; text outline follows](https://norasandler.com/assets/AST.svg)
And here’s pseudocode for constructing this AST:

```python
//create if condition
cond = BinaryOp(op='>', operand_1=Var(a), operand_2=Var(b))

//create if body
assign = Assignment(var=Var(c), rhs=Const(2))
return = Return(val=Var(c))
if_body = [assign, return]

//create else body
assign_else = Assignment(var=Var(c), rhs=Const(3))
else_body = [assign_else]

//construct if statement
if = If(condition=cond, body=if_body, else=else_body)
```

For now, though, we don’t need to worry about conditionals, variable assignments, or binary operators. Right now, the only AST nodes we need to support are programs, function declarations, statements, and expressions. Here’s how we’ll define each of them:

```python
program = Program(function_declaration)
function_declaration = Function(string, statement) //string is the function name
statement = Return(exp)
exp = Constant(int) 
```

