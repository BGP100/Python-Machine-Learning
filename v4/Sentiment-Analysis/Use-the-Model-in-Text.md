<a href="/v4/Sentiment-Analysis/Making-a-Network.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Understanding-Scraped-Data.md">Next &gt;</a>
<hr>
Now that you have your network built, you can use it to make more accurate estimations about the sentiment of each review. You are going to create some dummy data similar to the input data for your network. You will then run that data through the network and have it make a guess about if it's positive, negative, or neutral.
<br>
1. Create a new Jupyter Notebook.
<br>
2. Import the libraries that you will use for this project. 
<pre>
import pandas as pd
import numpy as np<br>
import tensorflow as tf<br>
import joblib
</pre>
3. Use the tensorflow method to load in your model.
<pre>model = tf.keras.models.load_model('sentiments.h5')</pre>
4. Load in the vocab.
<pre>vocab = joblib.load("vocab.pkl")</pre>
5. Print the summary of the model to make sure it's the right one.
<pre>model.summary()</pre>
5. Run the cell.
<br>
<img src="https://i.imgur.com/vhtXeg1.png">
<h1>Use the Model</h1>
Now that you have all the files you need to use the model imported to use the model, you can start to test it by running text through it.
<br>
This will happen in three stages:
<ul>
  <li>Mimic the vectorization process on some text.</li>
  <li>Run the text through the network to get predictions.</li>
  <li>Graph the predictions so they are human-readable.</li>
</ul>
<h2>Vectorize Text</h1>
You are going to start by creating a function that will replicate the vectorization process that you used on the reviews when preparing the data. This will convert text data into something that the model will understand. 
<br>
1. Import the required vectorizer libraries.
<pre>from sklearn.feature_extraction.text import CountVectorizer</pre>
2. Create a new CountVectorizer object.
<pre>vect = CountVectorizer()</pre>
3. Set the vocabulary of this vectorizer to the vocabulary loaded from drive.
<pre>vect.vocabulary=vocab</pre>
4. Create a new function called vectorize.
<pre>def vectorize(text,vectorizer):</pre>
5. Inside the method, apply the fit_transform function to the text.
<pre>  text = vect.fit_transform(text)</pre>
6. Convert the text to an array.
<pre>  text = text.toarray()</pre>
7. Return the text.
<pre>  return text</pre>
8. Run the cell to add the function to the notebook.
<br>
<img src="https://i.imgur.com/AbauMAQ.png">
<h2>Run a Review Through the Model</h2>
Now that we can vectorize text, let's make a test review to put through the network. The review needs to be in a list so that it can be vectorized. Then you will put the vectorized text into the model and get an array of the predictions it makes. 
<br>
1. Create a variable and set it equal to a test review.
<pre>review = ["I like these Heeleys so much I think they are extremely cool and they do a great job getting me places"]</pre>
2. Vectorize the review using the function you just created.
<pre>x = vectorize(review,vect)</pre>
3. Use the model to create an array of predictions.
<pre>pred_array = model.predict(x)</pre>
4. Print that array to see what the network thinks the review is.
<pre>print(pred_array)</pre>
<img src="https://i.imgur.com/ZUp3lZY.jpg">
<h2>Graph the Output</h2>
One of the most helpful ways to understand the output from a neural network is to create a bar graph of the predictions it makes. You are going to use matplotlib to create your very own graph to help you understand the output from your model. 
<br>
1. Import matplotlib to create a graph for the prediction array.
<pre>import matplotlib.pyplot as plt</pre>
2. Define a function called graph_results that takes a prediction array, index of that array.
<pre>def graph_results(prediction_array,index):</pre>
3. Inside the function,  create a list to hold the labels for each output category.
<pre>  labels = ["negative","neutral","positive"]</pre>
4. Still inside graph_results, set the predicted label to a variable called predicted.
<pre>  predicted = np.argmax(prediction_array[index])</pre>
5. Continue to create the graph inside the function by getting the title of the graph to the predicted outcome.
<pre>  title = "Prediction: " + labels[predicted]</pre>
6. Create a graph using matplotlib.
<pre>  graph = plt.subplot()</pre>
7. Set the graph type to a bar graph, use a range from 0 to 3 for the x-values, and use the prediction_array as the y-values.
<pre>graph.bar(range(3), prediction_array[index])</pre>
8. Add labels to the x-axis.
<pre>
  graph.set_xticks(range(3)) 
  graph.set_xticklabels(labels)
</pre>
9. And add the title to the graph.
<pre>  graph.set_title(title)</pre>
10. Finally, show the graph.
<pre>  plt.show()</pre>
11. Outside your new function, call graph_results using the prediction array and index 0 (since there's only 1 result).
<pre>graph_results(pred_array,0)</pre>
<img src="https://i.imgur.com/7viXcPf.png">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/DranMoe.png">
<h1>Recap</h1>
Running text through the model comes in three stages: vectorized, predicting, reading output. You created functions to help you understand the output of the network and to help make sure that the data going into the network is something that it will understand. 
<ul>
  <li>Create more reviews and run them through the model.</li>
  <li>Loop through the prediction array output and graph all the results.</li>
</ul>
