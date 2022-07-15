<a href="/v3/Loops-and-Functions/While-Loops.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Loops-and-Functions/Functions.md">Next &gt;</a>
<hr>
<h1>Intro</h1>
For loops, must have three components:
<ul>
  <li>A control variable</li>
  <li>A conditional statement</li>
  <li>A loop body</li>
</ul>
<h2>For Loops vs. While Loops</h2>
Remember, while loops run an unknown or unspecified amount of times. For loops run a specific or set amount of times, controlled by the programmer (that's you!).
<br>
<img src="https://i.imgur.com/gQq7L0I.jpg">
<h1>Parts</h1>
To do something to all 14 leaves on the tree, use a for loop.
<br>
Just like in a while loop, make a control variable:
<pre>number_of_leaves = 15</pre>
Also like a while loop, you'll write a conditional statement, though this one looks a little different:
<pre>for x in range(0, number_of_leaves):</pre>
As long as x (your count variable) is between 0 and 15 (<b>number_of_leaves</b>), the code inside the loop will run.
<br>
Each time the loop runs, it will add 1 to the count variable, ending when it reaches the <b>number_of_leaves</b> value.
<br>
Then you'll add the body:
<br>
Inside the for loop, add:
<pre>print("A leaf fell to the ground " + str(x) + " leaves have fallen.")</pre>
The variable x starts equal to zero, so at its highest value before the code stops, it will be equal to 14.
<h2>Result</h2>
Press Enter twice, and press Backspace to change the indentation back to the edge of the screen.
<br>
Type:
<pre>print("All the leaves fell. For loop complete.")</pre>
Run the program.
<pre>
number_of_leaves = 15<br>
for x in range(0, number_of_leaves):
    print("A leaf fell to the ground " +
    str(x) + " leaves have fallen.")<br>
print("All the leaves fell. For loop complete.")
</pre>
<h1>Recap</h1>
Use for loops to repeat a block of code if you know how many times it needs to run. For loops help you perform an action on multiple elements, if you know how many there are.
