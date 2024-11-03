# fixme2.py
Easy\
General Skills\
Beginner picoMini 2022\
Python\
Author: LT 'syreal' Jones
#### Description
> Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/6/fixme2.py)
## Solution
After downloading the file and loading the Python script into Visual Studio Code (if you haven't installed the Python Extension certified by Microsoft).

On line 22, change the `\=`to `\==`.  Python [Comparison](https://www.w3schools.com/python/gloss_python_comparison_operators.asp) Operators are used to evaluate two program control flow values.

![Screenshot 2024-11-03 at 11 44 29 AM](https://github.com/user-attachments/assets/17a93cba-3b72-41d2-88b5-aa3171328221)

After making the modification run the Python script either in the terminal `python fixme2.py` or from within Visual Studio Code.

### Flag
`picoCTF{3...c}`
