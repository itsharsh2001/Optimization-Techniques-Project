# lpp-py
Linear problem parser and dual converter in Python.

**YOU NEED [numpy](https://pypi.org/project/numpy/) FOR THE PROGRAM TO WORK. INSTALL IT WITH `pip install numpy`**

## Usage
```
python3 lpp.py -i <inputFile> [options]
```
### Example usage:
```
python3 lpp.py -i LP01.LTX
```

## Options
```
    -i, --input  <inputFile>  : define input file name (mutually exclusive with -l)
    -l, --load   <inputFile>  : define input JSON file name to load
    -j, --json                : export problem in JSON format
    -o, --output <outputFile> : define output file name
                                (Default: '(LP-2)<inputFile>')
    -p, --print               : print the human readable output in the console
    -s, --simple              : export the simple human readable format
    -d, --dual                : convert the problem from primal to dual form
```

## For help, use:
```
python3 lpp.py -h
```
or
```
python3 lpp.py --help
```

## About input files:
You can either load an already saved json file, created with this program via `-l` or `--load`, but should be used instead of `-i` or `--input`.


Otherwise, the input file should follow some specific rules. Take a look below about what is true as well.

* Start with the type of problem, `min` or `max`.
* Follow up with the objective function, preferably on the same line.
* Variable names must have specific names, like x1, x2, ..., xN. More specifically `x` and a number exactly after it.
* Capitalization does NOT matter, in anything.
* The order each variable is stated in an expression also does NOT matter.
* After objective function you must use the keyword(s) `s.t.` or `subject to` and state each one per line.
* Whitespace is irrelevant.
* Optionally, you can use the keyword `with` and state the natural constraints per line. To do so, state the variable name, then type `free` or `>=0` or `<=0`.
* You must ALWAYS type the `end` keyword when you are done.
* You can potentially write whatever else you like in the file and the parser will do it's utmost best to ignore them and only parse what it cares about. Take a look at the [examples folder](/examples), there are some examples that cover most cases and answer additional questions you might have.
