# Conundrum
## Description
In order to prove your worth as a brilliant wizard, you are asked to... guess a random number. Only *one* try, of course.
## Exploit
Intuitively, the flag is given when the user guesses the number. Looking around the code of the web server (written in Go), the file main.go is the most interesting. Looking inside, one can see that the script contains an array of 4 digit values and keeps the index of the array as a session value. The index is chosen randomly at the start, and then incremented by 1 for each wrong try.
The exploit at this point is very obvious: write a random number, look at the solution of the previous attempt and then write down the next number on the array.
