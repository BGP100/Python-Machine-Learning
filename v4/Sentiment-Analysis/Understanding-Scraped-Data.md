<a href="/v4/Sentiment-Analysis/Use-the-Model-in-Text.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Final-Touches.md">Next &gt;</a>
<hr>
<h1>Understanding Scraped Data</h1>
So far you have accomplished a lot: creating a website, scraping data from the website, organizing and preparing data for a TensorFlow model, vectorizing data, creating and training a model, and running test text through a model. Now it's time to put it all together. 
<br>
1. Open the notebook from the previous section (or use <a href="https://drive.google.com/uc?id=19bFYeifrVIqjx70tf3TclbsbrWpLNu0M&export=download">this</a> one).
<br>
2. Select Cell &gt; Run All to run all the cells and re-import all files.
<br>
<img src="https://i.imgur.com/HBWPPsf.png">
<h2>Scraping Data</h2>
You will use Beautiful Soup like you have been to scrape the review data from a website. Follow these steps, or use code from before to get all the review data into a list.
<br>
1. Create a soup object to use the Beautiful Soup library. Look at old code or follow this process to do so.
<br>
2. Now that you have the soup object, use it to find all the reviews on the page.
<pre>reviews = soup.find_all(id="content")</pre>
<h2>Clean-up on Aisle Review</h2>
You now have a list of all the reviews, but if you print it out you should see that it still has all of the HTML tags included in the text. In order to get the best prediction on these reviews you are going to remove all the extra text from these reviews.
<br>
1. Create an empty list called clean_reviews.
<pre>clean_reviews = []</pre>
2. Loop through each review in the list.
<pre>for review in reviews:</pre>
3. Create a variable called text that is set to the stripped text.
<pre>  text = review.get_text().strip()</pre>
4. Append text to the cleaned reviews list.
<pre>  clean_reviews.append(text)</pre>
5. Outside the loop, print cleaned_reviews to ensure it has the correct data.
<pre>print(clean_reviews)</pre>
<img src="https://i.imgur.com/tm81xFb.jpg">
<h2>Vectorize the Reviews and Predict</h2>
Remember that before you can put text into the model you need to vectorize it. Luckily, you already did most of the work for this, so you can just call your vectorize function on this data.
<br>
Then, you can use the predict function to create a prediction array based on the input. 
<br>
1. Use your vectorize function to create a new list of vectorized reviews.
<pre>x = vectorize(clean_reviews,vect)</pre>
2. Create a predictions array using the model.
<pre>pred_array = model.predict(x)</pre>
<img src="https://i.imgur.com/2TPP2rS.png">
<h2>Graph the Output</h2>
The final step is to graph the predictions array for each review.
<br>
1. Create a for loop that will run the same amount of times as there are reviews.
<pre>for i in range(len(clean_reviews)):</pre>
2. Print the review.
<pre>print(clean_reviews[i])</pre>
3. Graph the prediction array for the review.
<pre>graph_results(pred_array,i)</pre>
<img src="https://i.imgur.com/QVQnBPn.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/KT8ArfX.png">
<h1>Recap</h1>
Putting all the elements of this course so far together yields a notebook that can get review data from a website, use a TensorFlow model to predict if it's positive, negative, or neutral, and graph the results. 
<ul>
  <li>Add more reviews to your website.</li>
  <li>Test the network on any other website with reviews.</li>
</ul>
