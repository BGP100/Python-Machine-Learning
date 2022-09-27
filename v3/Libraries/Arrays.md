<a href="/v3/Libraries/Matplotlib.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Libraries/Graphs.md">Next &gt;</a>
<hr>
You've successfully created NumPy arrays — now see what you can do to them!
<br>
Create two lists and fill them all with 5 ones.
<br>
1. In your notebook for numpy, create two lists:
<pre>
num1 = [1, 1, 1, 1, 1]
num2 = [1, 1, 1, 1, 1]
</pre>
Next, add the lists together with the <code>+</code> operator.
<br>
2. In the next cell, add:
<pre>num1 + num2</pre>
3. Run the program.
<br>
You should see 10 ones print out.
<hr>
Rather than extending the list, sometimes you might need to add values in the array together. In the previous example, how would you get the result <code>[2, 2, 2, 2, 2]</code>?
<br>
To accomplish this, you'll need a for loop. You can use a for loop to access each index in the array. To loop through all the values in the array you'll need to use <code>len(num1)</code>.
<pre>len(arrayName) # returns the number of elements in that array.</pre>
You'll also need a third new array to hold the new sums.
<pre>arrayName.append(value) # adds element to the array.</pre>
<img src="https://user-images.githubusercontent.com/97191004/192486808-b2182036-7e84-4035-beac-d35bf1e131a2.png">
<br>
You'll first create a holder list called <code>num3</code>. From there, use a for loop to loop <code>len(num1)</code> times to access each value in the two arrays. 
<br>
As the two values are added, they are appended to <code>num3</code>.
<pre>
num1 = [1, 1, 1, 1, 1]
num2 = [1, 1, 1, 1, 1]
num3 = [ ] #create a holder list<br>
for i in range(len(num1)): #a for loop that loops over every value in the loop based on the side of the array
  num3.append(num1[i] + num2[i]) #add the sum of the values at the ith position of the arrays and save them to num3<br>
print(num3)
</pre>
While this method works, NumPy arrays let you do the same thing in one line.
<h1>Addition</h1>
1. Create two NumPy arrays with the same values and numbers:
<pre>
arr1 = np.array([1, 1, 1, 1, 1])
arr2 = np.array([1, 1, 1, 1, 1])
</pre>
2. Add the arrays together:
<pre>print(arr1 + arr2)</pre>
3. Run the program.
<br>
You should see the array printed with values added together. As long as both numpy arrays are the same size, you can add them together this way.
<br>
<code>[1, 2, 3] + [1, 2, 3]</code> would become <code>[2, 4, 6]</code>. If you had <code>[1,2] + [1,2,3]</code> it would return an error because the size of the arrays are different.
<img src="https://user-images.githubusercontent.com/97191004/192487406-0ed3a68d-9e96-462d-8571-358d395c7ace.png">
<h1>Multiplication</h1>
The same goes for multiplication. Replacing the plus sign in the previous example gives you the product of both arrays:
<br>
<code>[1, 2, 3] * [1, 2, 3]</code> will become <code>[1, 4, 9]</code>.
<br>
This can be done for subtraction and division as well. 
<h1>Adding a Number to an Array</h1>
You can add an individual number to the other values in an array using an addition operator ( + ):
<pre>
arr1 = np.array([1, 2, 3, 4, 5])
arr2 = np.array([2, 3, 4, 5, 6])<br>
print(arr1+5)
</pre>
<h1>Recap</h1>
You can use the + operator to combine two regular python lists into a single list. Numpy arrays let you use the + operator to add two same-size arrays together, adding each element in matching locations together. Using the + operator with a Numpy array and a single value will add that value to every element in the array.
