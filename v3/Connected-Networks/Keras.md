<a href="/v3/ML-Intro/Teachable-Machine-Challenges.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Connected-Networks/Keras.md">Next &gt;</a>
<hr>
<img src="https://i.imgur.com/tFOXrrX.png">
<br>
<b>Welcome to Keras</b>
<br>
Keras is a library developed to facilitate the creation and training of machine learning models and neural networks.
<br>
You'll use this library to create and train your own machine learning models. This section will break down the components of Keras you'll need.
<h1>Importing Keras and Tensorflow</h1>
Keras uses the TensorFlow library from Google as a backend. TensorFlow is usually imported as the shortened name <b>tf</b>. This makes typing out code that references TensorFlow functions quicker and easier.
<br>
1. In the first cell, import the TensorFlow library:
import tensorflow as tf 
<br>
2. Below, import the Keras Library:
<pre>from tensorflow import keras</pre>
<br>
3. Run the cell.
<br>
Now you can use the Keras library in your code.
<pre>
# TODO: Add imports.
import tensorflow as tf
from tensorflow import keras
</pre>
<hr>
<img src="https://i.imgur.com/PuZmx2l.jpg">
<br>
<b>Importing Matplotlib</b>
<br>
Matplotlib is a library that produces graphs and other visualizations.  In this case, you'll use it draw pictures of the images you're running your networks on.  You're specifically going to use the pyplot part of Matplotlib.
<br>
Matplotlib.pyplot is usually imported with the shortened name plt.
<br>
1. Below where you imported the Keras library add:
<pre>import matplotlib.pyplot as plt</pre>
<br>
2. Below this, add the command:
<pre>%matplotlib inline</pre>
This command tells Matplotlib to draw images in your Jupyter Notebook, below each cell.
<br>
3. Run the cell.
<pre>
# TODO: Add imports.
import tensorflow as tf
from tensorflow import keras
import matplotlib.pyplot as plt
%matplotlib inline
</pre>
<h1>Recap</h1>
<ul>
  <li>Keras is used to build models for Machine Learing.</li>
  <li>Matplotlib is used to make visualizations.</li>
  <li>Jupyter is used to run and annotate code dynamically.</li>
</ul>
