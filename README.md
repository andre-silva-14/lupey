# Assembler Interpreter

This repository is meant to be my implementation of the solution for a [`kata`](https://www.codewars.com/kata/58e24788e24ddee28e000053) present in [`Codewars`](https://www.codewars.com/).


## Kata Description

This is the first part of this kata series. Second part is here.

We want to create a simple interpreter of assembler which will support the following instructions:

`mov x y` - copies `y` (either a constant value or the content of a register) into register `x`
`inc x` - increases the content of the register `x` by one
`dec x` - decreases the content of the register `x` by one
`jnz x y` - jumps to an instruction `y` steps away (positive means forward, negative means backward), but only if `x` (a constant or a register) is not zero
Register names are alphabetical (letters only). Constants are always integers (positive or negative).

Note: the `jnz` instruction moves relative to itself. For example, an offset of `-1` would continue at the previous instruction, while an offset of `2` would skip over the next instruction.

The function will take an input list with the sequence of the program instructions and will return a dictionary with the contents of the registers.

Also, every `inc`/`dec`/`jnz` on a register will always be followed by a `mov` on the register first, so you don't need to worry about uninitialized registers.

Example
```python
simple_assembler(['mov a 5','inc a','dec a','dec a','jnz a -1','inc a'])

''' visualized:
mov a 5
inc a
dec a
dec a
jnz a -1
inc a
'''
```
The above code will:

set register `a` to `5`,
increase its value by `1`,
decrease its value by `2`,
then decrease its value until it is zero (`jnz a -1` jumps to the previous instruction if `a` is not zero)
and then increase its value by `1`, leaving register `a` at `1`
So, the function should return

```python
{'a': 1}
```
This kata is based on the [`Advent of Code 2016 - day 12`](https://adventofcode.com/2016/day/12).
