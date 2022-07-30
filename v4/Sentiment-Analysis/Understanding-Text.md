<a href="/v4/Sentiment-Analysis/Publishing-Your-Website.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Preparing-Data.md">Next &gt;</a>
<hr>
1. Import beautiful soup and the requests library.
<pre>
import requests
from bs4 import BeautifulSoup
</pre>
2. Send your link to another student in your class. Set the link you receive equal to a variable called url.
<pre>url = "https://charlotteec.github.io/"</pre>
3. Just like in the last section, use requests to get the page, and initialize beautiful soup.
<pre>
page = requests.get(url)
soup = BeautifulSoup(page.content,'html.parser')
</pre>
<img src="https://i.imgur.com/lc5uIi1.png">
<br>
4. Save all the reviews to a variable. You might have to try a few ids or classes if the person whose webpage you are looking at used a different id.
<pre>reviews = soup.find_all(id="content")</pre>
5. Loop through the reviews and print them.
<pre>
for review in reviews:
  text = review.get_text().strip()
  print(text)
</pre>
<h1>Deciding on Sentiment</h1>
There are a few ways that you can do this. First, you are going to try counting up the amount of positive or negative words in a review.
<br>
1. Create a list of positive words. This could be whatever you think will work, and you can adjust it. Here is an example.
<pre>positive = {"good","like","wonderful","great"}</pre>
2. Create a list of negative words like this example. 
<pre>negative = {"dont","hate","dislike"}</pre>
3. Now it's time to do some clean-up on the text. You will do this for each review in the list so use a for loop to check each review.
<pre>for review in reviews:</pre>
4. Get the text from the review.
<pre>  text = review.get_text().strip()</pre>
5. Convert the string to lowercase.
<pre>  text = text.lower()</pre>
6
6
Loop through the text and remove all punctuation.
<pre>
  punctuation = '''[].,?1234'567890!()/\:;""'''
  for i in text: 
    if i in punctuation:
      text = text.replace(i,'')
</pre>
7. Split the text into a list of words.
<pre>word_list = text.split(" ")</pre>
<img src="https://i.imgur.com/wjY4HwV.png">
<br>
8. Create a count for positive and negative words.
<pre>
pos_count = 0
neg_count = 0
</pre>
9. Loop through the word list.
<pre>for word in word_list:</pre>
10. Check if the word is in positive and increase the pos_count variable.
<pre>
  if word in positive:
    pos_count += 1
</pre>
11. Do the same thing with negative words.
<pre>
  if word in negative:
    neg_count += 1
</pre>
12. Print out the positive word count and negative word count, as well as the review they correspond to.
<pre>
print(text)
print("Positive word count: ",pos_count)
print("Negative word count: ",neg_count)
</pre>
<img src="https://i.imgur.com/ghn1Vy9.jpg">
<h2>Making a Decision</h2>
Now that you have a count of positive or negative words, you can start to get an idea of which reviews are positive and which ones are negative. You are going to use these counts to have the program decide if a review is positive or negative.
<br>
You are going to use the pos_count and neg_count variables to decide if the review is positive or negative.
<br>
1. Create an if statement to check if pos_count is greater than neg_count.
<pre>if pos_count &gt; neg_count:</pre>
2. If it is, it is a positive review.
<pre>  print("This is a positive review")</pre>
3. Else if neg_count is greater than pos_count, it is a negative review.
<pre>
elif neg_count &gt; pos_count:
  print("This is a negative review")
</pre>
4. Otherwise, the result is inconclusive.
<pre>
else:
  print("Not sure if this is positive or negative")
</pre>
<img src="https://i.imgur.com/wESoIsF.jpg">
<h1>Pros and Cons of This Method</h1>
Now that you have a reliable way of deciding what reviews are positive and which are negative, it's time to review your method and figure out what flaws it has.
<br>
Follow this list of questions and think about what potential issues could arise with this method.
<ul>
  <li>What happens if you have a review with a lot of instances of phrases like "not great", "no good", etc?</li>
  <li>What happens if you have a review that uses words that aren't in your lists of positive and negative reviews? </li>
</ul>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/VtiP65A.png">
<h1>Recap</h1>
You can take the data that you gleaned from the webpage, and do some clean up with it. Then, you can split that text into a list and use that list to count how many times each word appears. You can use this to make a decision about if the review text is positive or negative. 
<ul>
  <li>Adjust your code to help prevent some of the potential flaws of this system.</li>
</ul>
