<a href="/v3/Connected-Networks/Keras.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Connected-Networks/Preparing-Data.md">Next &gt;</a>
<hr>
One common use of machine learning in modern computing is image recognition. Computers can learn to spot objects in images, recognize handwriting and drawings, and even learn to identify features in the road while operating a self-driving car.
<br>
The image to the left shows a photo processed by the TensorFlow Object Recognition Application Programming Interface (API) where objects it recognizes are highlighted, accompanied by the percent certainty of its identification.
<br>
<img src="https://i.imgur.com/t0x45NC.jpg">
<hr>
<b>Quick, Draw!</b>
<br>
Google has released a series of experiments with AI you can explore here. One of the experiments, Quick, Draw! uses a neural network to recognize doodles and is constantly using the drawings that users make to improve its abilities.
<br>
The game gives you six prompts to draw an object, and the AI will do its best to guess what you're drawing.
<br>
Play a couple rounds of Quick, Draw! <a href="http://quickdraw.withgoogle.com">here</a>. As you draw, watch the different guesses that the AI makes. You can see a bit of the thought process as it guesses based on what details you've created so far.
<br>
<img src="https://i.imgur.com/AKzApqF.gif">
<hr>
<h1>Building Your Own Neural Network</h1>
Most machine learning-powered image recognition uses a technique called convolutional layers.
<br>
These neural network layers are somewhat similar to how neurons in the brain process visual data.
<br>
<img src="https://i.imgur.com/CkzK3BJ.jpg">
<br>
Over the course of this section, you'll build your own image recognition neural network that will use convolutional layers to learn to classify the contents of images.
<hr>
<b>Image Datasets</b>
<br>
Quick, Draw! provides an image dataset you can use to train your own neural networks, but the number of different classes and complexity of the image data makes the training process pretty lengthy!
<br>
There are a couple simple image datasets that you can use to train networks faster.
<ul>
  <li>MNIST: a set of hand-drawn black and white images of digits between 0 and 9.</li>
  <li>CIFAR-10: a set of 32x32 color images of various objects.</li>
</ul>
You can see a sample of the CIFAR-10 dataset from <a href="http://www.cs.toronto.edu/~kriz/cifar.html">CIFAR's website</a> in the image to the right.
<br>
<img src="https://i.imgur.com/AppBLHH.jpg">
<br>
Keras has a built-in ability to load both the MNIST and CIFAR datasets.
<h1>Recap</h1>
<ul>
  <li>Quick, Draw! lets you experiment with a neural network image classifier in real time.</li>
  <li>The CIFAR and MNIST datasets provide simple images to learn from.</li>
</ul>
