<a href="/v4/Python-Intro/User-Input.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Python-Intro/Random.md">Next &gt;</a>
<hr>
<h1>If Statements</h1>
An <b>if statement</b> runs a block of code based on whether or not a condition is true.
<br>
1. Create two variables:
<pre>
a = 6
b = 3
</pre>
2. Add an if statement:
<pre>
if a > b:
  print("a is greater than b") 
</pre>
3. Run your program.
<br>
4. Switch the values of  a  and  b , then run the program again.
<br>
<img src="https://i.imgur.com/FRAoCP9.png">
<br>
Did anything happen?
<br>
If statements only run if the condition is true, so the above statement only runs when a is greater than b.
<h2>Indentation</h2>
In Python, indentation is how code relationships are shown. Anything indented from the line above it is part of the same statement.
<br>
Try typing:
<pre>
x = 2 
print(x) 
if x > 3:
  x += 2<br>
print(x)
</pre>
Run the above code.  You should see 2 printed to the screen.
<br>
Now, try running the code again, but with the second print not indented.
<pre>
x = 2 
if x > 3:
  x += 2<br>
print(x)
</pre>
<img src="https://i.imgur.com/Bt7f4kb.jpg">
<br>
Indenting <code>print(x)</code> includes it with the if statement above.
<h2>Boolean Values</h2>
Remember that a boolean value is either true or false.
<br>
Add the following line to your file:
<pre>has_key = True</pre>
Add an if statement to see if the boolean value becomes true, and if so, tell the player they've won:
<pre>
if has_key == True:
  print("You won! Unlock the door!")
</pre>
<b>Tip:</b> Always try to write boolean values so they read as true in plain English. For instance, setting <code>lost == True</code> would read as: <b>"if lost:"</b>
<h1>Relational Operators</h1>
You can use the following symbols, called relational operators, to compare two values in an if statement:
<ul>
  <li><code>&lt;</code> - Less than. For example, <b>a&lt;b</b> will return true if a is less than b.</li>
  <li><code>&gt;</code> - Greater than. For example, <b>a&gt;b</b> will return true if a is greater than b.</li>
  <li><code>&lt;=</code> - Less than or equal to. For example, <b>a&lt;=b</b> will return true if a is less than or equal to b.</li>
  <li><code>&gt;=</code> - Greater than or equal to. For example, <b>a&gt;=b</b> will return true if a is greater than or equal to b.</li>
  <li><code>==</code> - Equals. For example, <b>a==b</b> will return true if a is equal to b.</li>
  <li><code>and</code> - And means both statements must be true. For example, <b>(a&gt;b)</b> and <b>(b&lt;c)</b> will return true of both <b>a&gt;b</b> and <b>b&lt;c</b> returns true.</li>
  <li><code>or</code> - Or means either statement can be true. For example, <b>(a&gt;b)</b> and <b>(b&lt;c)</b> will return true of either <b>a&gt;b</b> and <b>b&lt;c</b> returns true.</li>
  <li><code>not</code> - Not returns true if the statement is not true. For example, <b>not a</b> will return true if a is false.</li>
</ul>
You can also print out true/false checks with a print statement! Guess what the output will be before you run the statement.
<ul>
  <li><code>print(5 &gt; 4)</code>  checks if 5 is greater than 4.</li>
  <li><code>print(10 == 10)</code>  checks if 10 is equal to 10.</li>
  <li><code>print(5&gt;10)</code>  checks if 5 is less than 10.</li>
  <li><code>print(not 4&gt;5)</code>  checks if 4 is not greater than 5.</li>
  <li><code>print(5&gt;4 and has_key == True)</code></li>
  <li><code>print(4&gt;5 or 4&gt;6)</code>  checks if either 4 is greater than 5 or 4 is greater that 6.</li>
</ul>
<h2>Elif and Else Practice</h2>
If statements pair up with elif (short for "else if") and else statements to perform a series of checks.
<br>
A full if/elif/else block is in the code box below.
<br>
Copy this code into your file.
<pre>
player_age = 12<br>
if player_age &gt;= 18:
  print("You could be in college.")
elif player_age &gt;= 13:
  print("You can also attend iD Academies!")
elif player_age &gt;= 7:
  print("You can attend iD Tech Camps!")
else:
  print("You're young.")
</pre>
Run your code and input multiple ages to see which part of the if/elif/else block prints out.
<h2>Specific Checks</h2>
If and elif statements always look for a specific condition:
<pre>
if player_age &gt; 18: #Happens if the age is greater than 18.
elif player_age &gt; 13: #Only happens if the age is not greater than 18 and greater than 13.
</pre>
An else statement doesn't look for a specific condition. Else statements occur after an if or elif statement in your code.
<pre>
if player_age &gt; 18: #Happens if the age is greater than 18.
else: #Would happen for any other age not specified above.
</pre>
Every if - elif - else block must begin with one regular if statement, and end with a single else statement, but you can have as many elif statements in the middle as you want!
<h1>Comparison Keywords</h1>
What if you want to check a couple of things at once? Use and to check if two conditions are true.
<pre>if x &gt; 2 and x &lt; 4:  #Does something only if both cases are true.</pre>
Copy the code below:
<pre>
player_has_item = False
score = 50
won = False<br>
if player_has_item and score &gt; 100:
  won = True<br>
if not won:
  print("You haven't beaten the game yet.")
elif won:
  print("You won the game!")
</pre>
Use or to check if either condition is true. If either one is true, the if statement will run its code.
<br>
Copy the code below:
<pre>
player_has_item = False
score = 100
won = False<br>
if player_has_item or score &gt; 200:
  won = True<br>
if not won:
  print("You haven't beaten the game yet.")
elif won:
  print("You won the game!")
</pre>
Change the code so it prints out the "You won the game!" statement. This time, you only need to change one of the variables to win this time.
<h2>Not</h2>
Another keyword, not, checks if something is false.
<pre>if not won: #Does something if this case is not true.</pre>
This statement is commonly used in games when you want the game to keep running if it isn't won.
<br>
Below is a number guessing program that has been modified to not run properly.
<br>
Copy the code below:
<pre>
import random<br>
computer_number = random.randrange(0, 101)<br>
guessed = False<br>
while True:
  if guessed:
    answer = input("Guess the number ")
    if int(answer) == computer_number:
      guessed = True
      print("You got it!")
      break
    elif int(answer) &gt; computer_number:
      print("Your guess is too high.")
    else:
      print("Your guess is too low.")<br>
  else:
    break
</pre>
Update the code to run by adding the not keyword to the proper if statement!
<h1>Recap</h1>
You can use relational symbols in conditional statements to see if two things are greater than, less than, etc. in relation to each other. Use and to check two conditions at once, or to check one of two conditions, and not to check if a condition is false.
<br>
Examples:
<ul>
  <li><code>if a == b</code> - checks if a is equal to b</li>
  <li><code>if a <= b</code> - checks if a is less than or equal to b</li>
  <li><code>if a > b</code> - checks if a is greater than b</li>
</ul>
