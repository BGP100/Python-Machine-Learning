<a href="/v4/Sentiment-Analysis/Preparing-Data.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/BeautifulSoup-Challenges.md">Next &gt;</a>
<hr>
So far you have cleaned up all the text data from the reviews and separated them into input and output sets. Now that you have only the important words of the review, and a matrix to represent their polarity, it's time to turn that text into numbers that the network can understand. You will do this using a process called Vectorizing.
<br>
In order to do this, you are going to use sklearn. This library has a lot of built-in libraries for reworking data into its numerical form. This process has two phases: fit and transform.
<hr>
<b>Fit:</b> The fit stage creates a dictionary of counts of each word from a dataset. This dictionary is called a vocabulary.
<br>
<b>Transform:</b> The transform stage is all about taking a data set and applying it to the vocabulary created during the fit stage.
<hr>
Luckily, the sklearn library has built-in functions that will do most of the work for you during this stage. You are going to use a vectorizer called CountVectorizor that uses the count of each word to do the vectorization process. Follow these steps to create a vocabulary from the review data, and then transform the input datasets to that vocabulary.
<h1>Fit Stage</h1>
First, you are going to create a vocabulary using the fit function. You will use all of the review data from the dataset and create a dictionary of the frequency of each word. Then, you will export that data and save it.
<br>
1. Open the notebook that you created the data cleanup code in and use Cell &gt; Run All to re-run all your code. 
<br>
2. Create a vectorizer object.
<pre>vect = CountVectorizer()</pre>
3. Since we are somewhat limited in the Google Colab notebook about how much space and power the computer has, you are going to set a maximum amount of features for the vectorizer.
<pre>vect.max_features = 15000</pre>
4. Call the fit function to create the vocab. You are going to use all the review data so that the input is a consistent size. 
<pre>vect.fit(x_rev)</pre>
5. Save the vocab as a variable.
<pre>vocab = vect.vocabulary_</pre>
6. Print out the vocab to see what the function has created.
<pre>print(vocab)</pre>
7. Export the vocab so that you can re-use it later. 
<pre>joblib.dump(vocab,"vocab.pkl")</pre>
8. Run the cell to see the vocab.
<br>
<img src="https://i.imgur.com/FkH6fZq.jpg">
<h1>Transform</h1>
The transform is the stage that actually applies the data you are going to use to the vocabulary created by the fit stage. Follow these steps to transform the data into a form that the network can understand.
<br>
1. Create a new dataset called x_rev_train_v  for the vectorized data that has been transformed.
<pre>x_rev_train_v = vect.transform(x_rev_train)</pre>
2. Repeat this with the test data.
<pre>x_rev_test_v = vect.transform(x_rev_test)</pre>
3. Turn the datasets into an array.
<pre>
x_rev_train_v = x_rev_train_v.toarray()
x_rev_test_v = x_rev_test_v.toarray()
</pre>
4. Print out the shape of these datasets to verify that they have been vectorized. They may have different amounts of reviews, but they are both transformed onto the vocabulary, so the second argument should be 15000.
<pre>
print(x_rev_test_v.shape)
print(x_rev_train_v.shape)
</pre>
<img src="https://i.imgur.com/Aa3bMty.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/Iy64rfc.jpg">
<h1>Recap</h1>
Data needs to be vectorized in order to be run through the network. You used a python library to do this in two stages: fit and transform. You also exported the vocabulary to be used later, and uploaded it to Drive.
<ul>
  <li>Experiment with the vectorization process by changing the max features and seeing how that changes the shape of the datasets.</li>
</ul>
