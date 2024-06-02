# PHPislovePHPislife
## Description
In this challenge there's a web server with a PHP page. The user can input a string and the program will create a function with that string (but not execute it).
It's not that easy as it sounds though, because:
- `[*.\\= are banned
- all classes and function names are banned
- many other terms (like "flag", "echo", ...) are also banned
The flag is located in the variable ```$flag```.

## Exploit
Despite the pretty restrictive blacklist, there's multiple ways to solve one challenge.
One of them is the following: ```return 0; }; print ${$strings{4}}; //```.
... todo
