<a href="/v4/Loops-and-Functions/GuessTheNumber-Challenge.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Functions-and-Classes/Making-a-Class.md">Next &gt;</a>
<hr>
<h1>Intro</h1>
There will be times when you want to perform a series of actions, and instead of writing those statements over and over every time, you can use a function!
<br>
Function declarations look like this:
<pre>
def function_name():
  #Code to run goes here.
</pre>
<h2>Writing a Function Declaration</h2>
1. Make a new file and add:
<pre>import random</pre>
2. Declare and add content to a random number generating function:
<pre>
def random_number():
  rand = random.randrange(0, 2)
  print(rand)
</pre>
3. Below your function declaration, add the code below to call your function:
<pre>random_number()</pre>
<b>Tip:</b> To call a function, put the name of it followed by opening and closing parentheses wherever you want it to run in your program.
<h2>Return Value</h2>
You can have a function return a value, and you can use that value to pull information out of the function after it runs.
<br>
1. Change the print statement in your function to:
<pre>return rand</pre>
2. Change the function call to initialize another variable to be equal to your function:
<pre>a_number = random_number()</pre>
3. Print out the new variable:
<pre>print(a_number)</pre>
<h1>Arguments</h1>
<br>
An argument is a way for you to provide more information to a function. The function can then use that information as it runs, like a variable.
<br>
Arguments go inside the parentheses after a function.
1. Change the function declaration to:
<pre>def random_number(max_int)</pre>
2. Change the 2 in randrange to max_int:
<pre>rand = random.randrange(0, max_int)</pre>
3. Put a number in the parentheses when you call the function:
<pre>a_number = random_number(5)</pre>
All the code:
<pre>
import random<br>
def random_number(max_int):
    rand = random.randrange(0, max_int)
    return rand<br>
a_number = random_number(5)
print(a_number)
</pre>
<h1>Recap</h1>
Declare a function with:
<pre>
def function_name():
  print("Code to run")
</pre>
Call a function by typing its name:
<pre>function_name()</pre>
