<a href="/v3/CNN/Intro-to-CNN.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/CNN/Test-Your-CNN.md">Next &gt;</a>
<hr>
<h1>Uploading Photos</h1>
There are a lot of ways to test how effective your network is. You have mostly been using the test data from the MNIST dataset This is a really good way to make sure that the network has been trained for the data it has. However, as you set your network to actually complete the task it has been trained for, you might want to use your own images to see what the network is doing.
<br>
Follow these steps to upload your own image.
<br>
1. Pick a network that you want to test with your own images. 
<br>
2. At the end of the model code add this line
<pre>model.save('my_model.h5')</pre>
<br>
3. Run the cell. You should see a file called <code>my_model.h5</code> appear in your Student folder.
<br>
<img src="https://i.imgur.com/Xb54TPJ.jpg">
<br>
1. Download <a href="https://drive.google.com/uc?id=1HesdGHyerT6KJQEOSu7YHuGIbu4ZF0zs&export=download">this</a> notebook to your student folder. It has helper functions and import statements added.
<br>
2. Open the <b>TestingNetworks</b> notebook in Jupyter Notebook.
<br>
3. Download an image to your student folder. You can draw your own using <a href="https://www.piskelapp.com/">Piskel</a> or you can use one of <a href="https://drive.google.com/uc?id=14BmZRVjeQz2Mv8hYZ_wRoFfMWU7DDscU&export=download">these</a>.
<br>
<img src="https://i.imgur.com/w9HPrOk.png">
<br>
4. Run the first cell to add the helper functions to your code.
<br>
5. Set the path variable to the name of your image.
<pre>path = "test3w.jpg"</pre>
<br>
6. Load the image into your Notebook.
<pre>img = image.load_img(path,target_size=(28,28),color_mode="grayscale")</pre>
<br>
7. Convert the image to an array
<pre>img_arr = image.img_to_array(img)</pre>
<br>
8. Call predict_image on your image array
<pre>arr = predict_image(model_1,img_arr)</pre>
<br>
9. Call plot_value_array.
<pre>plot_value_array(arr,3,1)</pre>
<br>
10. Run the cell.
<br>
<img src="https://i.imgur.com/ff9r3TR.jpg">
<h1>Running Tests</h1>
Try these things to try to learn about how your network is performing on specific images. These tests are about coming up with theories for why a network makes a certain guess, not about deciding the effectiveness of a network based on how it performs on one image. You might train the exact same network, on the same data and it will perform differently on a specific image each time you train it. This is why machine learning experts test large batches of data and look at accuracy on a larger scale. 
<br>
However, it can be illuminating to look at how a specific network might be misidentifying certain images, and try to understand what it might be doing. Creating theories about what a network is doing, and how you might be able to combat that specific flaw is a useful skill. 
<br>
For these images, look at the whole graph of predictions for each test and try to notice trends. For example, you might notice that the guesses that a convolutional network makes are different than those that densely connected one does. Think about how the information it is learning might be different. Often the guesses a densely connected network makes are more nonsensical than those that a convolutional network is. 
<br>
Continue working on your TestingNetworks notebook.
<ul>
  <li>Export more models to test using these tests.</li>
  <li>Follow the instructions to run tests on your network.</li>
</ul>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/knAeRfu.png">
<h1>Recap</h1>
After building networks it can be useful to see how they perform on different kinds of images. Creating different tests to run on your networks can help you start to understand how they think. 
<ul>
  <li>Follow all the tests in the notebook.</li>
  <li>Come up with your own tests to run.</li>
  <li>Make a new network, export it, and these tests on it.</li>
</ul>
