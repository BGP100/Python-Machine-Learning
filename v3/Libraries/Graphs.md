<a href="/v3/Libraries/Arrays.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Libraries/Graphing-Challenges.md">Next &gt;</a>
<hr>
Graphs are fundamental when it comes to mathematics.
<br>
<b>Equation outputs</b> have patterns that make for interesting graphs when plotted out.
<br>
To see these graphs, begin with a simple equation: y = x2.
1. Create a function called "function1" using function declarations.
<br>
2. Pass in x and return the square of x.
<br>
3. Begin with the  def  keyword to create a new function with an input of list <code>x</code> from before:
<pre>def function1(x):</pre>
4. Create a return statement for the result of x squared:
<pre>return x * x</pre>
This function will square any value you pass it.
<br>
The values returned by  function1  need to be stored somewhere.
<br>
5. Create an empty list called "data" to store these values:
<pre>data = [ ]</pre>
<h1>Find and graph the squares of all the numbers from 1 to 100</h1>
Fill data with the squared values returned by <code>function1</code>. Use a for loop to pass in all the numbers from 1 to 100.
1. Create a for loop using the range method:
<pre>for i in range(100):</pre>
2. Use the list’s append function add it to the list called "data":
<pre>
output = function1(i)
data.append(output)
import matplotlib.pyplot as plt
import numpy as np<br>
def function1(x):
    return x * x<br>
data = [ ]<br>
for i in range(100):
    output = function1(i)
    data.append(output)<br>
print(data)
</pre>
3. Pass the list to a Matplotlib plot, like so:
<br>
<img src="https://user-images.githubusercontent.com/97191004/192492184-027eb00d-77bb-477e-b9f6-1ebf9f3305c5.jpeg">
<br>
<h1>arange(x)</h1>
You've graphed all the values from 1 to 100 using a for loop, but you can also do it using a NumPy function for quicker and cleaner code.
<br>
Remember the range function Python comes preloaded with?
<br>
NumPy has a <code>np.arange(x)</code> function, which produces into a NumPy array from 0 to x.
<br>
This function is noninclusive, so it stops right before x.
<br>
1. Call <code>data = np.arange(100)</code> to return numbers from 0 to 99.
<br>
<img src="https://user-images.githubusercontent.com/97191004/192492882-19eef2e7-886f-4c56-8ab2-8af9029f1940.jpeg">
<pre>
import matplotlib.pyplot as plt
import numpy as np<br>
def function1(x):
    return x * x<br>
data = np.arange(100)
print(data)
</pre>
Because NumPy arrays can have one operation performed on them rather than having to make a for loop to iterate through the whole array, you can pass it into a function as if it were a single value.
2. Pass the array <pre>data</pre> into <pre>function1</pre>:
<pre>output = function1(data)</pre>
<img src="https://user-images.githubusercontent.com/97191004/192492184-027eb00d-77bb-477e-b9f6-1ebf9f3305c5.jpeg">
<br>
3. Examine the two ways to graph the squares of all the numbers between 1 to 100.
<br>
Both work to produce the same graph, but are achieved through different techniques.
<h1>Recap</h1>
Matplotlib can also be used to graph equations. There are a lot of customizable options.
<ul>
  <li>Use a different math formula besides x * x.</li>
  <li>The function you plotted just now is a parabola; try finding the equation of a circle and printing that, as well as a higher-order polynomial. <code>e.g., y = x^3 + x^2 + x</code>.</li>
</ul>
Full code:
<pre>
import matplotlib.pyplot as plt
import numpy as np<br>
def function1(x):
    return x * x<br>
data = np.arange(100)
print(data)<br>
output = function1(data)
plt.plot(output)
plt.show()
</pre>
