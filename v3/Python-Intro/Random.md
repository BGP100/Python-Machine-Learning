<a href="/v3/Python-Intro/Conditionals.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Loops-and-Functions/While-Loops.md">Next </a>
<hr>
Programs often require the use of random numbers in everything from games to cyber security.
<br>
To see random numbers in action, you'll make a virtual board game where the player rolls dice.
<br>
<b>Note:</b> It's technically impossible to generate a truly random number with a computer. Because of this, programmers often call random numbers pseudorandom.
<h1>Generating Random Numbers</h1>
The first step in generating a random number is importing the random number generator. It's common for a programming language to have extra libraries that need to be imported.
Create a new Python file.
<br>
Add <code>import random</code> to the first line.
<br>
That's the random library. Now to generate some numbers!
<h2>Setting the Range</h2>
When using a random number, it's important to set the range. For example, a Roll the Dice program could roll a 12-sided die, generating a random number between 1 and 12, including the end numbers.
<br>
Type a print statement letting the user know that a random number is being generated.
<br>
Print:
<pre>random.randint(1, 12)</pre>
Run the program.
<br>
Add a new line of code to print a random number between 1 and 100.
<pre>
import random<br>
print ("Rolling the Dice!")<br>
print (random.randint(1, 12))<br>
print (random.randint(1, 100))
</pre>
The program will print a random number between 1 and 12.
<h1>Recap</h1>
Libraries are collections of premade code you can import and use in your programs. You have to import Python's random library to use it. <code>random.randint(x, y)</code> generates a random integer, with x as the minimum and y as the maximum.
