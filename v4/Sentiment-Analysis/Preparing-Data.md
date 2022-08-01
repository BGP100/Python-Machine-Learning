<a href="/v4/Sentiment-Analysis/Understanding-Text.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Vectorizing-Text.md">Next &gt;</a>
<hr>
<h1>Cleaning Data</h1>
So far you have created a simple system for making a call on if a review has a positive or negative overall rating. This system works as long as the review uses words that you have predetermined as positive or negative.
<br>
But what about reviews with more complicated words or phrases? In order to have a more nuanced and general understanding of text from the reviews, you are going to build a neural network that is trained using data from reviews. This network will build a more nuanced understanding of the review data.
<br>
There are three main stages of creating this network:
<ul>
  <li>Importing and cleaning up the data</li>
  <li>Vectorizing the data</li>
  <li>Creating and training the network</li>
</ul>
To start, you are going to import the data and do some basic clean-up on it.
<br>
1. Create a new Colab Notebook. 
<br>
2. Download <a href="https://drive.google.com/uc?id=18UVOyFEZlPyTmFFkuueRIjV44RqBJhqX&export=download">this</a> file to your student folder.
<br>
3. Copy and paste the code below to import all the required libraries. You will learn what each one does as you proceed through this project.
<pre>
import pandas as pd
import numpy as np<br>
import string
from string import punctuation
import nltk
from nltk.corpus import stopwords
nltk.download('stopwords')<br>
import tensorflow as tf<br>
from tensorflow.keras.layers import Input,Dense,Dropout
from tensorflow.keras.models import Sequential<br>
import sklearn
from sklearn.model_selection import train_test_split
from sklearn.feature_extraction.text import CountVectorizer,TfidfTransformer,TfidfVectorizer<br>
import joblib
</pre>
4. Use the Pandas library to read the data into your program.
<pre>data = pd.read_csv('Reviews.csv')</pre>
5. Print out the first few lines of this data.
<pre>data.head()</pre>
6. Run this cell to see the first few rows of data.
<br>
<img src="https://i.imgur.com/BA8aiZo.jpg">
<h2>Cleaning Up Data</h2>
Now that you have the data imported, it's time to extract only the parts you need to train the network.
1. Before the data.head() line, add this code to drop unnecessary columns...
<pre>data = data.drop(['UserId','Id','Time'],axis=1)</pre>
2. ...and drop any empty columns.
<pre>data.dropna(inplace=True)</pre>
3. Run the cell again to see the changes.
<br>
<img src="https://i.imgur.com/fkNwLVg.jpg">
<h2>Adding a Polarity Column</h2>
Now it's time to add a new column that keeps a label of the rating as either positive, negative, or neutral. In order to do this, you will use the star rating of the reviews. If the reviewer gave the item 4 or 5 stars (more than 3) then it's a positive review, if the reviewer gave the item 1 or 2 stars (less than 3) then it's a negative review, and if it's 3 stars, then it is neutral.
<br>
1. Create a new column to keep track of if the review is positive, negative, or neutral.
<pre>data['Polarity_Rating'] = data['Score'].apply(lambda x:'Positive' if x>3 else('Neutral' if x==3 else 'Negative'))</pre>
2. Run the cell to see the changes.
<h2>Sampling the Data</h2>
Now it's time to separate the data into separate groups depending on if it's positive negative or neutral. You will use these lists to make sure that there is an equal amount of each kind of review. 
1. Create a new code cell.
<br>
2. Create a list of positive reviews.
<pre>data_positive = data[data['Polarity_Rating']=='Positive']</pre>
3. Repeat that with the negative and neutral reviews.
<br>
4. Print out the shape of each list.
<pre>
print("Negative: ",data_negative.shape)
print("Neutral: ",data_neutral.shape)
print("Positive: ",data_positive.shape)
</pre>
<img src="https://i.imgur.com/5XRh4la.png">
<br>
5. Get a sample from the positive reviews. For the sample size, 8000 is a good number, since it won't create a data set that's too large.
<pre>data_positive = data_positive.sample(8000)</pre>
6. Get a sample from the negative and neutral lists as well. 
<br>
7. Print out the shape of each dataset.
<br>
<img src="https://i.imgur.com/6f3cOyo.png">
<br>
8. Combine the lists together to create one large dataset.
<pre>data = pd.concat([data_positive,data_negative,data_neutral])</pre>
9. Print out the shape of the new dataset.
<pre>print(data.shape)</pre>
<img src="https://i.imgur.com/FUsoUPM.jpg">
<h2>Cleaning up the Data</h2>
Now that you have one large list of the data, it's time to clean the actual text in it. You will create a function that removes punctuation and stop words from the text. The string library has a built-in list of stop words. Stop words are words that don't contain important information and are extremely common in the English language. These are words like: "is", "are", "the". 
<br>
1. Create a new code cell and add this function.
<pre>
def text_cleanup(text):
  stopwrds = stopwords.words('english')
  no_punc = [char for char in text if char not in string.punctuation]
  no_punc = ''.join(no_punc)
  return ' '.join([word for word in no_punc.split() if word.lower
</pre>
2. Create a new column called reviews that applies the text cleanup function. 
<pre>data['reviews'] = data['Text'].apply(text_cleanup)</pre>
3. Use data.head() to see the first few rows of data.
<br>
4. Run the cell.
<br>
<img src="https://i.imgur.com/PBe6pk9.jpg">
<br>
5. Before the data.head(), add this code to reduce data to simply two columns: cleaned up review, and polarity rating.
<pre>data = data[["reviews","Polarity_Rating"]]</pre>
6. Re-run the cell.
<br>
<img src="https://i.imgur.com/x7IKoTN.png">
<h2>One Hot Encoding</h2>
One-hot encoding is a process of creating data categories that the network can understand, and that won't have an inherent bias. In this case, you will create a matrix of three columns (for positive, negative, and neutral) and put either a 1 or 0 in the row for the review text. This way the network can be trained using the matrix to validate it's guesses.
<br>
1. Create a new dataset called one_hot and use a function from the pandas library to turn the polarity rating into a matrix.
<pre>one_hot = pd.get_dummies(data["Polarity_Rating"])</pre>
2. Set data equal to the reviews column combined with the new dataset you just created.
<pre>data = pd.concat([data,one_hot],axis=1)</pre>
3. Drop the polarity rating column from data.
<pre>data.drop(['Polarity_Rating'],axis=1,inplace=True)</pre>
4. Call data.head() to verify that it worked as expected.
<br>
<img src="https://i.imgur.com/M4WEt0f.png">
<h2>Train and Test Split</h2>
Now that you have all the data cleaned up and formatted in a way that makes sense to the network, it's time to split it into train and test sets for the network! In order to split the data into these groups, you are going to use a library called sklearn. This should already be imported, and all you will need to do is call its train_test_split function to get a train and test data set.
<br>
To feed data into this network you need an input set and an output set. The input will be the reviews, and the polarity will be the output. First you will create these datasets, and then you will split them into train and test sets. 
<br>
1. Create an x_rev dataset the represent the input. This will be all of the reviews.
<pre>x_rev = data["reviews"].values</pre>
2. Create an x_pol dataset for the output. This should be everything except the reviews.
<pre>y_pol = data.drop("reviews",axis=1)</pre>
3. Then you can use train_test_split to split this data into two groups of input and output.
<pre>x_rev_train,x_rev_test,y_pol_train,y_pol_test = train_test_split(x_rev,y_pol,test_size=0.30,shuffle=True)</pre>
<img src="https://i.imgur.com/HYVQT1H.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/V3gRt2J.png">
<h1>Recap</h1>
You can use a few Python libraries to clean up and organize data from a spreadsheet. First, you separated the data into three groups and sampled from each of them to ensure that you have an equal amount of each type of review. Then, you removed stopwords and create a matrix for the polarity rating. Finally, you split the data into the appropriate groups to feed into a network to train it. 
<ul>
  <li>Learn about text vectorizing in the next section.</li>
</ul>
