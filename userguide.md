# User Guide
## Getting Started
### Requirements 
* [rust](https://www.rust-lang.org/tools/install)
* node [install from package manager](https://nodejs.org/en/download/package-manager/) or [download binary from web](https://nodejs.org/en/download/)

### Installation

You can run:

```sh
npx create-react-app my-app --template context-free-react
cd my-app
npm install
```

to set up a new project called `my-app` (you should probably change that name)

You now have

* now you'll have a configuration file located in `cfr.json` 
* a grammar file located in `src/grammar.ebnf`
* the source code for context-free-react copied and compiled in `Context-Free-React/` 

If you run 

```sh
npm run start
```

your default web browser should have a page with 'hello world' on it!


### Basic Config

If you edit `src/grammar.ebnf` you'll see

``` ebnf
program ::= 'hello world';
```

This represents a grammar with a single production rule. It means that the non-terminal symbol `program` can be turned into 'hello world'

The fact that it is called `program` is important because in our `cfr.json` we have

```json
"start" : "program",
```

This tells cfr that the first production rule is `program`

## Building a Calculator

Building a calculator might be an overused example for parsers but cfr isn't a parser so we're ok!

### User Interface

The user interface for our calculator will be built by editing our `src/grammar.ebnf` file

```ebnf
program ::= expr;
expr ::= binaryop | number;
binaryop ::= expr ('+' | '-' | '*' | '/') expr;
number ::= #'[0-9]+';
```

Here we are stating that 
* an `expr` is either a `binaryop` or a `number`
* a `binaryop` is an `expr` followed by some choice of operator followed by another `expr`
* a `number` is a regular expression consisting of 1 or more charactors between 0 and 9 (so stuff like `0`, `1`, `9`, `10`, `00000000`, `1293721837182378`)

now If you run `npm run start` again you should have an updated webpage with proper user input.

### Calculating a result

First we need to create a visitor to walk the tree created from user input. To do this we can extend the base visitor class provided to us from cfr located in `src/grammar-lib/`

Let's Create a file called `Calculator.ts` in `src/` and put in the following code

```typescript
import { Visitor } from './grammar-lib/visitor'

class Caclulator extends Visitor {
}
```

After writing this, your ide should be giving you errors saying that Calculator
