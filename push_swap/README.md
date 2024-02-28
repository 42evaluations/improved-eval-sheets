# push_swap

## error handling

**_subject states:_**
```
Errors include for example: some arguments aren’t integers, some arguments are
bigger than an integer and/or there are duplicates.
```

⚠️ each testcase should be done as follows:
* once with quotes:
    * ```valgrind ./push_swap "<input>"```
    * ```funcheck -a ./push_swap "<input>"```
    
* once without quotes
    * ```valgrind ./push_swap <input>```
    * ```funcheck -a ./push_swap <input>```

⚠️ **'./push_swap "1 2 3"'** and **'./push_swap 1 2 3'** are (in most implementations) two different cases & therefore need to be tested separately

if funcheck shows errors, do not fail directly:
* compile again with the **-g** flag
* run the program again: you will get more information about where **_exactly_** the error happened
* set the value allocated on that line to **NULL**
* recompile & run again
* -> i promise you will find the segfault/leak, but **if not**:
    * ask the person you are evaluating
    * ask someone to come have a look
    * ask on discord
    
    -> if no one can find it, **DO NOT FAIL JUST BECAUSE FUNCHECK SAYS SO**


### some arguments aren't integers

⚠️ don't forget valgrind & funcheck!!

⚠️ test with **and** without quotes

```./push_swap a 2 3``` - expected output: ```Error\n``` - why?     'a' in input

```./push_swap "" 2 3``` - expected output: ```Error\n``` - why?    "" is not equal to zero!

```./push_swap --1 2 3``` - expected output: ```Error\n``` - why?   '--' is not a valid sign

⚠️ these should not be errors

```./push_swap 01 2 3``` - why? integers with leading zeros are valid in C - try declaring ```int i = 0001``` - it will compile :)

### some arguments are bigger than an integer

⚠️ don't forget valgrind & funcheck!!

⚠️ test with **and** without quotes

```./push_swap 1 2 2147483648``` - expected output: ```Error\n``` - why? integer overflow

```./push_swap 1 2 -2147483649``` - expected output: ```Error\n``` - why? integer underflow

```./push_swap 1 2 9223372039002500456``` - expected output: ```Error\n``` - why the extra case? if the overflow check only consists in storing the number into a long and checking it against INT_MAX/INT_MIN, **_it will fail here_**, because _9223372039002500456_ will make a 64bit long overflow back into 32bit int range

⚠️ this should not be an error:

```./push_swap 1 2 -2147483648```

### some arguments are duplicates

i think you can figure that one out :)

## sorting

download checker:

```wget https://cdn.intra.42.fr/document/document/24599/checker_linux```

```chmod +x checker_linux```

from here you can follow the eval sheet with some extra considerations:

⚠️ if valgrind & or funcheck show any errors, **_check the appropriate flag_** (crash, leak).

⚠️ when the eval sheet says **test with x random values**, check with x random values from **INT_MIN to INT_MAX**, _not from 0 to x_

number generator:

https://numbergenerator.org/100randomnumbersbetween1and100

## ask about implementation!

last but not least: ask the peer about their implementation. if they coded it themselves, **they should be able to explain it!**

ask them about the algorithm, how it works in the code, what kind of issues they ran into while implementing it, ...

if they are not able to, there is a flag for that, don't be scared to use it :)

xoxo @winstonallo