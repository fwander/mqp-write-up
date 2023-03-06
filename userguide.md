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


## Building a grammar

If you edit `src/grammar.ebnf` you'll see

``` ebnf
program ::= 'hello world';
```

This represents a grammar with a single production rule. It means that the non-terminal symbol `program` can be turned into 'hello world'




