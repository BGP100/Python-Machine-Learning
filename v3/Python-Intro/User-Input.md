<a href="/v3/Python-Intro/Variables.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Python-Intro/Conditionals.md">Next &gt;</a>
<hr>
Whether it's in the form of them entering a username, or password, using a keyboard to control a player in a game, or moving around with a mouse, there's a lot of coding that's responding to input from users.
<br>
In the programs you've been working on, if you want the user to enter information with a keyboard you'll use the input function.
<br>
Add the following code to a python program:
<pre>input("Input You're Asking For")</pre>
A small cursor will appear in your output, and you can now type in the output!
<br>
In the output area, type something like:
<code>"then you can type"</code>
<img src="https://i.imgur.com/MT2rAHB.png">
<h1>Setting Input to Variables</h1>
You can also initialize a variable to input, so to get someone's name as input and then store it as a variable:
<pre>
name = input("What's your name?\n")
print(name)
</pre>
<h1>Combining Strings and Ints</h1>
When you print information out, you may want to combine multiple types of text, like a variable and a string.
<br>
To see it in action, add the following code to your program:
<pre>print("Hey " + name + " how are you?")</pre>
When you run that program, you'll see it all print out as one line. It works with no errors because the name variable is also a string.
<br>
Anything you enter with the input function will end up being a string.
<br>
In Python print statements can't print out numbers and strings together, it can only print out one type. So to make a number a string you can put str() before it.
<br>
<code>age = 14</code>
<br>
<code>age_as_word = str(age)</code>
<br>
<code>print("You're " + age_as_word)</code>
<br>
Then, if you want to make a string into a number, only if it converts, you'd put it between the parenthesis in  int() .
<br>
Change your program to:
<br>
<code>age = "14"</code>
<br>
<code>age_as_number =  <i>What would you write here?</i></code>
<br>
What would you set the variable age_as_a_number equal to, to turn the string into an int? <code>age_as_num = int(age)</code>
<br>
<code>print(age_as_number + 3)</code> 
<br>
Input has a lot more to it, but as long as you or people you know are the main users, this is a good start. Converting numbers to strings so you can display them, or converting strings to numbers so you can do math operations are a good place to get you started!
<h1>Recap</h1>
Now you know you can get input from users, and save that information to a variable for your program to use. Also you have some tools for dealing with input that needs to be changed to a number or a string.
<br>
Create a new program with at least one input from a user.
<br>
Convert the input to an int, or other information to a string to use it in your program!
