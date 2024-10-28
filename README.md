java c
Problem Solving 2024 Fall
Assignment 1
October 9, 2024
1 Introduction
In this assignment, you will implement an interactive console program, QuadCalc; it takes a command from the user as text input through the console, executes the command, and prints the result to the console until an exit command is entered. QuadCalc manages a list of weighted quadratic functions. Let N be the number of the quadratic functions (1≤ N ≤ 300). The i-th (1≤ i ≤ N) quadratic function, Qi(x) is represented as follows:



where any of the coefficients (ai, bi, and ci) can be zero.
The prime function, P(x), is a weighted sum of Qi(x) and defined as follows:



where wi (∈ R) is the weight given to Qi(x). There is no case where the sum of the weights becomes zero.
The user can 1) add and remove quadratic functions to the prime (add and remove), 2) adjust their weights (setw), 3) evaluate the prime function at a certain point x (evaluate), and 4) find the root of the prime function (findroot).


2 The QuadCalc Commands
A command is a single-line string that ends with “\r\n” and consists of command type and arguments as follows:
 :=    · · · 
command type represents the type of the command and is one of: add, remove, setw, evaluate, check, and exit. The output of each command (if any) must be printed out immediately after each command is entered, not being queued until the exit is entered.
argi and typei are the name and type of the i-th argument in the command, respectively. The type of an argument is one of:
· size: a positive integer ranging from 1 to 300 (inclusive),
· number : a single-precision (4 bytes) floating-point number.
IMPORTANT: It is guaranteed that an exact number of the arguments of the correct types are always given (no insufficient or superfluous arguments, no wrong type).
2.1 The add Command
Usage: add   
The add command adds a quadratic function to the prime function with coefficients a, b, and c, initializing its weight to 1 (wi = 1). In the beginning, there is no function added to the prime function, i.e., P(x)=0, and it is guaranteed that the add command is always given as the first command of the input. Also, note that any of the coefficients can be zero, and the add command does not make any output.
Example: An add command to add a quadratic function Q1(x)=x2 + 2x+ 3 is “add 1 2 3”.
2.2 The remove Command
Usage: remove 
The remove command removes the quadratic function at the given index. After removal, the remaining functions are shifted accordingly (if necessary). If there’s only one function, removing it will reset P(x)=0. Print out “0” if the removal operation succeeds. If an invalid size is provided, e.g., index out-of-range, print out “-1”.
Example: “remove 1” will remove the first quadratic function.


2.代 写Problem Solving 2024 Fall Assignment 1Python
代做程序编程语言3 The setw Command
Usage: setw  
The setw command adjusts the weight wi of the quadratic function at the specified index. Weights are real numbers and can be positive, negative, or zero. Print out “0” if the operation succeeds. If an invalid size is provided, e.g., index out-of-range, print out “-1”.
Example:“setw 2 0.5” will set the weight of the second quadratic function to 0.5.
2.4 The evaluate Command
Usage: evaluate 
The evaluate command calculates the value of the prime function P(x) at the given x and prints the result. Print three decimal places of the result by using the %.3f format specifier.
Example: “evaluate 2” prints out P(2) with three decimal places.
2.5 The findroot Command
Usage: findroot
The findroot command prints out the root of the equation P(x)=0 if it exists. This command behaves as follows:
· If P(x) is a constant function, print out “CONST”.
· If P(x) is a linear function (a polynomial of degree 1), print out the root x such that P(x)=0.
· If P(x) is a quadratic function (a polynomial of degree 2) with two real roots, print out each of them in increasing order, separating them with one space ‘ ’.
· If P(x) is a quadratic function with one root, print it out only once.
· If P(x) is a quadratic function with no root, print out “NOROOT”.
Use the %.3f format specifier to print out the root.
2.6 The exit Command
Usage: exit
The exit command terminates QuadCalc.


2.7 Notes on Floating-Point Precision
Due to the limitations of floating-point representation, an error margin of less than or equal to 0.01 will be considered acceptable. Additionally, when comparing two floating-point numbers (e.g., checking if a coefficient is zero), use the same error bound. For example, a number is considered zero if its absolute value is less than or equal to 0.01. You may make a helper function or macro, e.g., is zero(x), and use it consistently throughout the code.




3 Input and Output Examples
· The text in black is the input to the program.
· The text in red is the output from the program.
· The text in blue is an explanation, not the output from the program.
add 1 2 3           Q1(x) = x2 + 2x + 3
add 3 2 1           Q2(x) = 3x2 + 2x + 1
remove 1           Q1 is removed, and Q2 becomes Q1.
0
remove 2           There is no Q2 anymore.
-1
evaluate 0.5        P(x) = 3x2 + 2x + 1
2.750
setw 1 0.5
0
evaluate 0.5
2.750
add 1 1 1            P(x) = 1.667x2 + 1.333x + 1
evaluate 0.5
2.083
setw 1 1             P(x) = 2x2 + 1.5x + 1
0
evaluate 0.5
2.250
findroot              P(x) = 2x2 + 1.5x + 1 has no real root.
NOROOT
add 0 3.5 0         Q3(x) = 3.5x
remove 2
0
findroot               P(x) = 1.5x2 + 2.75x + 0.5 has two roots.
-1.629 -0.205
exit







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
