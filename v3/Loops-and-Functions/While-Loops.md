<a href="/v3/Python-Intro/Random.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Loops-and-Functions/For-Loops.md">Next &gt;</a>
<hr>
In programming, loops allow you to repeat a block of code a number of times.
<br>
If there's a question like the one to the right, how many tries will it take to guess?
<br>
1 guess? 2 guesses? 4 guesses? 100 guesses?
<br>
For times when a block of code needs to run an uncertain or non-specific amount of times, you use a while loop.
<br>
<img src="https://i.imgur.com/7MYHZve.jpg">
<h1>Control Variables</h1>
You use a control variable to set when your loop does and doesn't run. If you want your loop to repeat until a user guesses correctly, use a boolean control variable.
<br>
Make a new project.
<br>
Add:
<pre>guessed = False</pre>
<h1>Loop Conditions</h1>
The loop repeats until a condition you set is met in what is called a conditional statement. Use your loop type and the control variable here.
<br>
Set the condition of the loop to run while guessed is not true:
<pre>while not guessed:</pre>
The body of the loop is the code that will run repeatedly.
<br>
Add the following code inside your while loop:
<pre>
guess = input("Pick a number")<br>
if int(guess) == 14:
  guessed = True
  print("You win!")
</pre>
The print statement will only run after the loop has ended.
<br>
Here's what your project could look like at this point:
<pre>
guessed = False<br>
while not guessed:
    guess = input("Pick a number")
    if int(guess) == 14:
        guessed = True<br>
print("You win!")
</pre>
<h1>Recap</h1>
Use while loops when a program must run an unknown amount of times. While loops are made of a loop control variable (made first), a conditional statement (the conditions that must be met for the loop to run), and a loop body (the actual code that will run).
<ul>
  <li>Update the code to handle entries with different capitalizations.</li>
  <li>Add code to make the guess input statement easier to understand for the user.</li>
</ul>
