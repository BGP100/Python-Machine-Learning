<a href="/v3/CNN/Test-Your-CNN.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Optional-CIFAR-Data/Creating-a-Network-for-CIFAR.md">Next &gt;</a>
<hr>
<h1>Understanding the CIFAR Data</h1>
Now that you understand how two different kinds of networks work for the MNIST dataset, you are going to prepare data for a more general image recognition problem. A lot of the same principles of neural networks apply, but this network is going to be a lot more complicated and robust.
<br>
For a more general image recognition challenge, you will need a more general dataset. Luckily, there is a dataset called CIFAR that has labeled images for ten different things. Just like the MNIST data, you are going to prepare it to be fed into a network.
<br>
Click the cards below to learn some important information about the CIFAR dataset.
<ul>
  <li>Image size - Each image is 32 x 32 pixels</li>
  <li>Amount of images - 50,000 training images and 10,000 test images.</li>
  <li>Amount of output classes - There are 10 possible output classes in this dataset.</li>
  <li>Colors - Since these pictures are in color, there are three color channels, one for red, green, and blue.</li>
</ul>
<h2>Preparing the Data</h2>
This process is very similar to that of the MNIST dataset. See if you can remember what code to add for each step, and click the accordion if you need help. 
<br>
1. Add import statements and add the helper functions you used in your MNIST notebook, or open this notebook with import statements and helper functions already added. 
<br>
2. Add variables to keep track of image size. 
<br>
3. Add a variable to keep track of the number of output classes. 
<br>
4. Add a variable to keep track of the input shape. 
<br>
5. Load the data into your program. 
<br>
6. Load a backup copy of the data. 
<br>
7. Add this code to set up an array for labels.
<pre>label_names=['airplane','automobile','bird','cat','deer','dog','frog','horse','ship','truck']</pre>
8. Add this code to convert the label arrays.
<pre>
train_labels_backup = [item for sublist in train_labels_backup for item in sublist] 
test_labels_backup = [item for sublist in test_labels_backup for item in sublist] 
</pre>
9. Use the helper functions to print out the 100th image to ensure the data has loaded correctly.
<br>
10. Show the min and max values of the 100th image before you normalize the data.
<br>
11. Print the shape of the test and train images to make sure you have the correct data. 
<br>
12. Convert the images to the float32 data type.
<br>
13. Normalize the data into values between 0 and 1.
<br>
14. Convert the labels using one-hot encoding. 
<br>
15. Show the 100th image, and min and max values again to ensure that data preparation has worked correctly.
<br>
Here's what your project could look like at this point:
<br>
<h1>Recap</h1>
Preparing data is an important part of starting a new machine learning project. Each dataset is a little different, and learning how to manipulate the data for a network is important. 
<ul>
  <li>Print out another random image.</li>
</ul>
