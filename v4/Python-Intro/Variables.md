<a href="/v4/Python-Intro/Jupyter-NB.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Python-Intro/User-Input.md">Next &gt;</a>
<hr>
The coding in this course will be done in Jupyter Notebooks. Follow these steps to create your first Jupyter Notebook.
<h1>Variables</h1>
Variables are like boxes; they hold important information, or data. A variable can hold different data types, such as numbers or words.
<br>
<img src="https://i.imgur.com/hFy3a70.jpg">
Think of a chest. You can store items inside it, and give the chest a name to help you remember what you put in there.
<br>
In this case, you'll store some doughnuts in the chest. If you want to remember how many doughnuts you put in the chest, you could name it:
<br>
<code>number_of_doughnuts</code>
<br>
The chest's name is the variable's name!
<br>
<b>Note:</b> When you're writing the name of a variable in Python, it should always be lowercase, with words separated by an underscore.
<h1>Initialize Variables</h1>
After naming a variable, you can give it a value, which is like filling the chest. This is called initializing.
<br>
Say you have three doughnuts in your chest. You'd initialize your chest variable by setting it equal to three:
<br>
<code>number_of_doughnuts = 3</code>
<br>
<img src="https://i.imgur.com/lZkvSlm.jpg">
<h1>Print Variables</h1>
To see the value of your variable when you run your program, you'll need to print it.
<br>
Type:
<pre>
number_of_doughnuts = 3
print("number_of_doughnuts is " + number_of_doughnuts"!")
</pre>
<h2>Strings</h2>
Variables can hold data besides numbers, including words. Programmers refer to variables holding words as strings.
<pre>
doughnut_name = "Kepler" 
print(doughnut_name)
</pre>
<h2>Escape Characters</h2>
These characters can be used to help format string output.
<ul>
  <li><code>\n</code> - new line</li>
  <li><code>\t</code> - tab</li>
  <li><code>\"</code> - quotation</li>
</ul>
<img src="https://i.imgur.com/pUHjSSJ.jpg">
<b>Tip:</b> You can make a multi-line string with three quotation marks. You won't need <code>\n</code> characters with this option!
<pre>
my_multiple_line_string = """This is the first line
This is the second line
This is the third line"""
</pre>
<h2>Boolean</h2>
You can also use variables to show if something is true or false; this type of data is called a boolean.
<br>
Create a variable to determine if these doughnuts exist.
<br>
Add the following to your program and then run it:
<pre>
doughnuts_exist = True
print(doughnuts_exist)
</pre>
To set it to not true, change the variable to:
<pre>doughnuts_exist = False</pre>
<img src="https://i.imgur.com/bd9E5tE.jpg">
<h1>Recap</h1>
Use variables to store different types of data to use later in your program. Types of data:
<pre>number_variable = 5</pre>
<pre>string_variable = "value"</pre>
<pre>boolean_variable = True</pre>
