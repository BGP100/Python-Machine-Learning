<a href="/v3/Optional-Challenges/Magic-8Ball.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Libraries/Matplotlib.md">Next &gt;</a>
<hr>
For machine learning, the libraries <b>NumPy</b> and <b>Matplotlib</b> help handle the datasets that are used. 
<br>
Before moving on, it's important to understand there are two types of data:
<ul>
  <li>Training data</li>
  <li>Testing data</li>
</ul>
For Training data there is an input and output. In Testing data there is only an input. You'll be using this a lot more later when creating a neuron for machine learning.
<h1>Arrays</h1>
An array is a collection of values, all identified by an array index.
<br>
For example, you can have an array called "foods" that will contain "apple," "cheese," and "bread." 
<br>
The <i>index</i> starts at 0, so the index of "apple" will be 0, "cheese" will be 1, and "bread" will be 2. 
<br>
<img src="https://user-images.githubusercontent.com/97191004/192342721-50950f9d-dd6e-4316-a7bd-e4ce684a3de7.png">
<br>
A value in an array can be referenced like any other variable.
<br>
"cheese" is <code>food[1]</code>, so if you were to say <code>print(food[1])</code>, "cheese" will print out.
<hr>
NumPy introduces many functions that help with large datasets.
<br>
Python lists can't be used because in order to apply a function, a loop is needed to go through every value in the list. A NumPy array can increase the value of all the elements at once.
<br>
Imagine the <code>foods[]</code> array from before. If you wanted to multiply each food item by 2, you'll need to go through each index in the array.
<br>
For NumPy arrays, however, the elements can all be multiplied by 2 simultaneously.
<br>
<img src="https://user-images.githubusercontent.com/97191004/192342721-50950f9d-dd6e-4316-a7bd-e4ce684a3de7.png">
<br>
Machine learning uses many operations on arrays of data. These data sets often contain thousands of numbers and to iterate through every single value one at a time would be difficult and lengthy. NumPy simplifies all of this.
<h1>Importing NumPy</h1>
Type:
<pre>import numpy as np</pre>
This code loads NumPy into your program. 
<br>
The NumPy library is renamed to make it quicker to access using the  as  keyword. The code above renames the library to “np;” when calling NumPy in your program, refer to it as "np."
<h2>You’re now ready to make your first NumPy array!</h2>
1. In a new cell, create a variable named "array".
<br>
2. Set array to equal to <code>np.array([])</code>.
<br>
The empty angled brackets (<code>[ ]</code>) represent an empty array. The starting array is going to be empty.
<br>
If you print the array you should get a set of empty brackets. Empty data is kinda boring, so next you'll add some values.
<br>
3. Inside the brackets, add the values "1, 2, 3, 4":
<pre>array = np.array([1, 2, 3, 4])</pre>
4. In the following cell, add:
<pre>print(array)</pre>
Now the print statement outputs <code>[1 2 3 4]</code>.
<br>
Knowing the size of data tells you how many different data points exist in the array. With machine learning algorithms, these sizes must be known in order for most of the algorithms to work.
<br>
To check the size of a NumPy array:
<br>
5. Type the name of the variable followed by a period <code>.</code>, then the word shape:
<pre>print(array.shape)</pre>
This calls the shape property of NumPy arrays and lets you see the size of the array.
<br>
After running the code above, the output is <code>(4, )</code> — this means there are four individual values inside the array.
<h1>Multidimensional Arrays</h1>
Next, you'll make this a two-dimensional array; Jupyter Notebook has shortcuts to make this process easier.
1. Highlight the data you want to put in an array.
<br>
2. Press the left angle bracket on the keyboard.
<br>
Now your data should be grouped <code>[1,2]</code> and <code>[3,4]</code>. 
<br>
You've just created an array of arrays! This means your first array value is the array <code>[1,2]</code> and the second array value is the array <code>[3,4]</code>.
<br>
3. Run the cell that prints the size of the array.
<br>
The size will be <code>(2,2)</code>, which is read as two sets of two values. There are two array values each with two values.
<br>
In the previous example, the shape was <code>(4, )</code>, which is read as just four array values.
<br>
If the NumPy array is <code>[[1, 2, 3],[2, 3, 4],[5, 4, 3]]</code>,the shape should be <code>(3,3)</code>, which is read as three sets of three values.
