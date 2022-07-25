<a href="/v4/Connected-Networks/Image-Recognition.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Connected-Networks/Building-a-Network.md">Next &gt;</a>
<hr>
<h1>Preparing the Data</h1>
Keras has code that will load a basic version of your data into lists in Python, but they aren't yet formatted in a way that your neural network will be able to use.
<br>
Reshaping and processing data into a format that the neural network can consume is a key step in any machine learning problem.
<br>
In this lesson, you will learn how to prepare the MNIST dataset so that it can be put into a neural network. 
<br>
There are some things you should know about the MNIST dataset.
<ul>
  <li><b>Image size</b> - Each image is 28 x 28 pixels.</li>
  <li><b>Amount of images</b> - There are 60,000 training images and 10,000 test images</li>
  <li><b>Amount of output classes</b> - Since each image is a digit from 0-9, there are ten possible output classes.</li>
  <li><b>Colors</b> - These images have one color channel, which means that each pixel is currently stored as a value between 0 and 255.</li>
</ul>
<h2>Set up and Importing</h2>
The first stage of this process is to import all the libraries you will need; to set up variables to keep track of the important information about your data. Then you will import the data and save it so that it is ready to be cleaned up and processed.
<br>
1. Make sure you have all the relevant libraries as indicated below. 
<pre>
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.datasets import mnist
from tensorflow.keras import backend as K
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
</pre>
2. Copy-paste these helper functions below the imported libraries. 
<pre>
# helper functions
def show_min_max(array,i):
  random_image = array[i]
  print(random_image.min(),random_image.max())<br>
def plot_image(array,i,labels):
  plt.imshow(np.squeeze(array[i]))
  plt.title(" Digit "+str(labels[i]))
  plt.xticks([])
  plt.yticks([])
  plt.show()
</pre>
3. Set up variables to keep track of your image size
<pre>img_rows,img_cols = 28,28</pre>
4. ...and your output classes. 
<pre>num_classes = 10</pre>
5. Now, you can load the data into your program. This line will load data to train the model, and data to test it, as well as the labels to test the data against.
<pre>(train_images,train_labels), (test_images,test_labels) = mnist.load_data()</pre>
6. Since you are going to be processing this data and manipulating it, it makes sense to have a backup of the untouched data.
<pre>(train_images_backup,train_labels_backup),(test_images_backup,test_labels_backup) = mnist.load_data()</pre>
7. To check to make sure we have the correct data, you can print the shape of the train and test image data sets
<pre>
print(train_images.shape) 
print(test_images.shape)
</pre>
<img src="https://i.imgur.com/cbnGnap.png">
<h1>Sorting Through the Data</h1>
<h2>Data Formatting</h2>
Sometimes, data can be formatted in many different ways, and a Machine Learning expert will need to handle this in their code. Since the MNIST data is already so well prepared for machine learning applications there isn't a lot of reshaping or preparation that needs to go into it.
<br>
However, in other situations, you might come across data that needs more hefty reshaping and re-organizing. This is an important skill to develop, and as you expand your machine learning abilities you will learn more about how to deal with different types of data. 
<br>
For now, you will just reshape the data so that it is an appropriate size for your network.
<br>
1. Add the command to reshape the data. This command takes data that was originally a list of pixels, and reshapes it into a 28x28 grid, which matches how our neural network will process the data.
<pre>train_images = train_images.reshape(train_images.shape[0],img_rows,img_cols,1)</pre>
<br>
2. Do the same for the test images.
<pre>test_images = test_images.reshape(test_images.shape[0],img_rows,img_cols,1)</pre>
<br>
3. Create an input_shape variable to keep track of what shape this data is. 
<pre>input_shape = (img_rows,img_cols,1)</pre>
<img src="https://i.imgur.com/SfZy17x.png">
<h2>Data Cleaning</h2>
Now that the data is in the right format, we can do some simple data cleaning.  The color in pixels is stored as an integer value between 0 and 255. While your network can learn from this information, it will be easier if we replace these values with a decimal between 0 and 1.  This keeps the numbers the network is dealing with small.
<br>
We do this by changing the data to a float32, a kind of decimal number, and then doing some division to get the 0-1 values you want.
<br>
<img src="https://i.imgur.com/SfZy17x.png">
<br>
1. Use the helper functions to print out the 100th image in train_images, and the min and max value in that image.
<pre>
plot_image(train_images,100,train_labels)
show_min_max(train_images,100)
</pre>
2. Run the cell
<br>
<img src="https://i.imgur.com/J3a8gsf.png">
<br>
3. Convert that data into float32.
<pre>
train_images = train_images.astype('float32')
test_images = test_images.astype('float32')
</pre>
4. Divide the images by 255 to make sure that each pixel is stored as a value between 0 and 1.
<pre>
train_images /= 255
test_images /= 255
</pre>
5. Use the same functions to print out the image and it's min and max values.
<pre>
plot_image(train_images,100,train_labels)
show_min_max(train_images,100)
</pre>
<img src="https://i.imgur.com/ev2T4wC.png">
<h2>One-Hot Encoding</h2>
MNIST is a set of hand-drawn images of the numbers 0-9. The label for each image is then simply the number 0-9.
<br>
<img src="https://i.imgur.com/6KKxuBm.png">
<br>
However, there is a problem with this.  Due to how neural networks function, they intuitively believe that the image labeled "1" is more similar to the image labeled "0" or "2" than the image labeled "7".  However, that's not the case.  If you write a 0, 1, 2, and 7 on a sheet of paper, the 1 and 7 are more similar in structure, with a long straight line compared with the curves in 0 or 2.
<br>
One-Hot Encoding is a technique that helps solve this problem by replacing the label on each image with a representation that the network won't think is ordered, so it will view each number independently.
<br>
1. Add this code to employ one-hot encoding on your data.
<pre>
train_labels = keras.utils.to_categorical(train_labels,num_classes)
test_labels = keras.utils.to_categorical(test_labels,num_classes)
</pre>
<img src="https://i.imgur.com/GJ4Lgy4.png">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/7RZ7W9S.png">
<h1>Recap</h1>
Preparing data to go into a neural network is an important step of the process. You need to learn about the data that you are using and manipulate it to be effective as training and test data in your network.
<ul>
  <li>Practice looking at random images from your data set.</li>
  <li>Move on to learn about how to create a network.</li>
</ul>
All of the code:
<pre>
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras.datasets import mnist
from tensorflow.keras import backend as K
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline<br>
# helper functions
def show_min_max(array,i):
  random_image = array[i]
  print(random_image.min(),random_image.max())<br>
def plot_image(array,i,labels):
  plt.imshow(np.squeeze(array[i]))
  plt.title(" Digit "+str(labels[i]))
  plt.xticks([])
  plt.yticks([])
  plt.show()<br>
img_rows,img_cols = 28,28<br>
num_classes = 10<br>
(train_images,train_labels),(test_images,test_labels) = mnist.load_data()
(train_images_backup,train_labels_backup),(test_images_backup,test_labels_backup) = mnist.load_data()<br>
print(train_images.shape)
print(test_images.shape)<br>
train_images = train_images.reshape(train_images.shape[0],img_rows, img_cols,1)
test_images = test_images.reshape(test_images.shape[0],img_rows,img_cols,1)
input_shape = (img_rows,img_cols,1)<br>
plot_image(train_images,100,train_labels)
show_min_max(train_images,100)<br>
train_images = train_images.astype('float32') 
test_images = test_images.astype('float32')<br>
train_images /= 255 
test_images /= 255<br>
train_labels = keras.utils.to_categorical(train_labels,num_classes)
test_labels = keras.utils.to_categorical(test_labels,num_classes)
</pre>
