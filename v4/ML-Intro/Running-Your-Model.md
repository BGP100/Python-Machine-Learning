<a href="/v4/ML-Intro/Train-Models-with-TM.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/ML-Intro/Playable-RPS-Challenge.md">Next &gt;</a>
<hr>
Now that you've created a machine learning model with Teachable Machine, you can export it to use with Python projects.
<h1>Export the Model</h1>
When we show up to the present moment with all of our senses, we invite the world to fill us with joy. The pains of the past are behind us. The future has yet to unfold. But the now is full of beauty simply waiting for our attention.
<br>
1. Click Export Model to open the export menu.
<br>
2. Select the Tensorflow tab on the export window.
<br>
3. Select the option Keras and click Download Model to download a saved version of your model. Don't close the export window yet!
<br>
<img src="https://i.imgur.com/ObvOL09.jpg">
<br>
The resulting zip file contains two files:
<ul>
  <li><code>keras_model.h5</code> - the saved model and parameters. You can load this file with code to run your model in the machine learning library Keras.</li>
  <li><code>labels.txt</code> - a text file containing the human-readable labels for each of your classes.</li>
</ul>
With these two files, you can set up a Python program to load your model and test results.
<h1>Create a Google Colab Notebook</h1>
Machine learning can be computationally intensive, especially for home computers. In order to run your machine learning program, you can use Google Colab, an online coding environment that simplifies the installation of libraries as well as provides sufficient computing power for machine learning projects.
<br>
Colab uses a coding environment for Python called Jupyter Notebook.
<br>
1. Go to <a href="https://colab.research.google.com">colab.research.google.com</a>
<br>
2. Sign into your Google account.
<br>
3. If you've never been there before, an example notebook will open. From there, select File &gt; New Notebook.
<br>
If you have used Colab before, that link will open to this window: create a new notebook with the New Notebook button.
<br>
<img src="https://i.imgur.com/r6uZc5X.png">
<br>
<img src="https://i.imgur.com/E9bA2HJ.png">
<br>
Once you create a new notebook, you'll see a screen like the one below.
<br>
<img src="https://i.imgur.com/JHj8iYm.png">
<br>
Teachable machine provides example code you can use to run your model. You'll copy it over and modify it slightly to test your model with Python.
<br>
1. On your Teachable Machine export window, click the Copy button in the code box labeled "Code to Test your Model"
<br>
<img src="https://i.imgur.com/7cIXfOc.png">
<br>
2. Paste the copied code into the empty cell in the Colab notebook you created.
<br>
<img src="https://i.imgur.com/DhMwoVg.png">
<br>
<img src="https://i.imgur.com/Eg5it5I.jpg">
<br>
Once the code is pasted in, you'll need to upload a your model, labels, and a test image to run and test it.
<br>
1. Click the folder icon to open the file browser.
<br>
2. Drag and drop <code>keras_model.h5</code> and <code>labels.txt</code> into the file browser to upload them to the Colab runtime.
<br>
<img src="https://i.imgur.com/MfCR2cY.png">
<br>
Use your webcam camera app to take a photo in one of the poses to test the model. 
<br>
4. Rename the image to "test_photo.jpg".
<br>
5. Drag and drop the resulting file onto the file browser to upload it.
<br>
6. Replace the IMAGE_PATH with the name of your image ("test_photo.jpg").
<br>
<img src="https://i.imgur.com/j92y3rK.png">
<br>
7. Run it.
<br>
<img src="https://i.imgur.com/szpEzSg.png">
<br>
When you run your test code, you'll get an output array of predictions that corresponds to the model's percentage guesses of each category. This is pretty impossible to read for humans at a glance - that's what the labels.txt is for. You'll add a bit of python code to print out the correct label for your model's prediction.
<h1>Printing Labels</h1>
Add the follow code just below the lines that load the model (under the comment # Load the Model) 
<pre>labels = [line for line in open("labels.txt")]</pre>
<img src="https://i.imgur.com/yT4QRsm.png">
<br>
This will load each line of the labels text file into a list you can access later.
<br>
2. Just below the line that prints the predictions array, add the following line:
<pre>print(labels[np.argmax(prediction)])</pre>
This will print whichever entry in the labels list corresponds to the highest value in the predictions array (the model's best guess).
<br>
3. Run the program to see the human-readable label of the most likely guess printed in the output!
<br>
<img src="https://i.imgur.com/96BC26r.png">
<br>
Now you've got a functional python program that loads an image and guesses which rock, paper, scissors symbol it contains!
<br>
Below are some highlighted breakdowns of the example code that might be useful if you wanted to use this code for another project:
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/uHqPJGV.png">
<h1>Recap</h1>
You can use the models produced by Teachable Machine for any Python project by loading them with Keras.
<ul>
  <li>Export the model as an <b>.h5</b> file.</li>
  <li>Copy the sample code to load the model.</li>
  <li>Update the python code to utilize the model however your project needs.</li>
</ul>
