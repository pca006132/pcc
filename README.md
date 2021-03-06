# PCC

> Command functions, restructured.

PCC is a *language* which allows you to write complex command functions in a simple, elegant way.
Its syntax enables you to write nested command functions in 1 place, instead of writing lots of tiny broken pieces of command functions in different files.
Also, it supports some metaprogramming features, users can use function templates to generate functions from the parameters given.
Users can also define constants and macro, which would be replaced during compilation.

> We are still in beta stage, do not use the generated functions directly as the compiler may still have bugs.

## Example
```
import std:helper

#define $stack = std:helper/stack

@wrapper $stack(a):
def a:
    say a
    function b
@wrapper $stack(b):
def b:
    say b
    execute if score @p common matches 1.. run:
        #throw("Error! Your common score is larger than 0!")
    function c
@wrapper $stack(c):
def c:
    say test3
```

## Usage
> PCC requires [Node.js](https://nodejs.org/en/) as runtime, please install if you don't have it.

1. Clone this repository. (As this version is still in its beta, which is not published yet)
2. Run `npm install` to install dependencies.
3. Run `npm run build` to build the JavaScript files.
4. Run `node ./lib/index.js -h` for help.

## Syntax
see [Syntax](./syntax.md)

## Config
Users can setup `config.json` to specify the settings.

* `entry`: Entry PCC file
* `objective`: Scoreboard objective used for transferring data.
* `namespace`: Default namespace for functions/events not in any module.
* `output`: Output path of the generated namespace files.
* `global`: Define files that can be referenced/imported by calling its name.
    * Key: Name of the file.
    * Value: Path of the file
* `js`: List of JavaScript files to be loaded, i.e. to add functions that can be used directly during evaluation.
* `definitions`: Path of the definition file (PCD) to be generated. Note that if this is defined, the program would not output the compiled functions/events.

## Contribution
Feel free to give suggestions or bug reports.