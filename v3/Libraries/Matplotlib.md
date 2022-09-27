<a href="/v3/Libraries/NumPy.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Libraries/Arrays.md">Next &gt;</a>
<hr>
Matplotlib is great for plotting and works hand-in-hand with NumPy.
<br>
<img src="https://user-images.githubusercontent.com/97191004/192374419-45ab07e1-5635-4137-b23e-308257601429.jpeg">
<br>
Importing Matplotlib is similar to importing NumPy, again using the  as  keyword to shorten the library name:
<br>
1. Create a new Jupyter Notebook named MatPlotLib Challenges.
<br>
2. In your program, add:
<pre>import matplotlib.pyplot as plt</pre>
<h1>Graphing</h1>
With Matplotplib imported, you can use it to plot data.
<br>
Data visualization is a very important part of data analysis.
<br>
Machine learning commonly uses a graph called a scatter plot. Seeing the data plotted in a graph enables you to find patterns and clusters to better understand the data.
<br>
<img src="https://user-images.githubusercontent.com/97191004/192374424-0078371b-145a-4035-b6b2-38c14fb2cac0.jpeg">
<br>
You can also use line plots that connect data points with straight lines. This will visualize the trend and which direction the data is going
<br>
<img src="https://user-images.githubusercontent.com/97191004/192374425-f42dc3b6-2912-4993-9e65-6876966d473c.jpeg">
<h2>Make a New Set of Data</h2>
1. Make two lists of data:
<pre>
x = [1, 2, 3, 4, 5]
y = [1, 4, 9, 16, 25]
</pre>
Use the <code>plt.plot()</code> function to plot the line.
<br>
2. Input both your newly created lists, x and y, into <code>plt.plot()</code>:
<pre>plt.plot(x,y)</pre>
3. To make the line visible, include:
<pre>plt.show()</pre>
<h2>Change the Display</h2>
Say you want to plot something other than a line, like points.
<br>
To create a scatter plot, inside the <code>plt.plot()</code> function, pass in <code>"ro"</code> to modify the way your graph appears.
<br>
1. Update your code to plot red points on your graph instead of a blue line:
<pre>
plt.plot(x,y,"ro")
plt.show()
</pre>
<img src="https://user-images.githubusercontent.com/97191004/192374426-97214d38-f5af-448c-9fef-c3a52dba7453.png">
<br>
The first character,  r , sets the color, while the second character,  o , sets the type of line to be drawn.
<ul>
  <li>You can set the color to be red, blue, yellow, or green using <code>[r,b,y,g]</code>.</li>
  <li>Line types allowed are <code>[o,-,*,1,2,3,4,.]</code>.</li>
</ul>
2. Update your code to plot a different color and a different line type of your choice.
<hr>
For example, <code>plt.plot(x, y, "b.")</code> will print a blue set of points.
<br>
<img src="https://user-images.githubusercontent.com/97191004/192485566-94c65acc-e40d-4717-ab29-5faa8c27be9d.png">
<h1>Recap</h1>
Matplotlib can be used to plot large datasets and create graphs. 
<br>
Data visualization is very important for data driven stuff like machine learning!
<ul>
  <li>Replace the colors and the type of lines to see what the graph will look like.</li>
</ul>
