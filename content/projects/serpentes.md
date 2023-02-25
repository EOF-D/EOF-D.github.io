---
title: "Serpentes"
date: 2023-01-29T15:47:11-05:00
description: "Outline of my new project."
series: ["Serpentes"]
tags: ["python", "compiler design", "programming"]
ShowToc: true
TocOpen: true
---
A PVM (Python Virtual Machine) based programming language.
This essentially means that the programming language is meant to be ran using
Python.

The name of the project is named after snakes :)
View the [GitHub Repo](https://github.com/EOF-D/serpentes)

## Tools

* [Lark](https://github.com/lark-parser/lark)
* [ASTMonkey](https://github.com/mutpy/astmonkey)

**Lark is an extremely powerful PEG parser**. I'll be using this package to
write the grammar.

ASTMonkey is gonna be used for the code generation. Basically, the idea is to
create a new `ast.Module` then to generate valid python code from it.

I'll be using ASTMonkey until I decide to write my own codegen, but for now I'm
gonna be depending on it.

## Main Idea

The language will be a language that can cross compat with python.
It'll be ran using a custom codec that is hooked onto Python @ runtime.

Proof-of-concept.

```py
					---------------------------------
					| # -*- coding: rattlesnake -*- |
					|							    |
					| ndef hello-world() -> none {  |
					|	 print("Hello World!")      |
					| }							    |
					---------------------------------

							/
						   /
						  /

--------------------------------------
|	FuncDef(						 |
|		name="hesnakes|
|		body = [					 |
|			Call(					 |
|				name=Name("print")	 |
|				value="Hello World!" |
|			)						 |
|		]							 |
|	)								 |
--------------------------------------

					|
					|
					|

	----------------------------------
	|								 |
	|	def hello_world() -> None:	 |
	|		print("Hello World!")    |
	|								 |
	----------------------------------
```

```sh
python3 hello_world.py
> Hello World!
```
