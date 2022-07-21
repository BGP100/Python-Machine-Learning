<a href="/v3/Connected-Networks/Improving-Your-Network.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/CNN/Build-a-CNN.md">Next &gt;</a>
<hr>
So far you have been working with fully connected, or densely connected networks. These networks work well for extremely well-defined problems, like with the MNIST dataset, but it isn't very good at extracting more general information about a picture.
<br>
Follow along with this to see how the network from the previous lesson does on a new picture of a handwritten digit.
<hr>
Look at a densely connected network's prediction for this image.
<br>
The predicted label is printed at the top (2). 
<br>
The image itself is next. 
<br>
The graph is a plot of the output layer. 
<br>
<img src="https://i.imgur.com/3skEMp6.png">
<hr>
1. Write down three things you notice about it.
<br>
Now, look at the prediction for the image with inverted colors.
<br>
<img src="https://i.imgur.com/DMvKEEv.png">
<br>
2. Write down the major changes in this image. Why do you think this is?
<br>
Forming theories for why a network is operating in a certain way is an important part of machine learning.
<br>
The network can correctly predict images, but only in a very specific set of parameters.
<br>
Since all of the training images are white drawings with black backgrounds, when the network tries to guess what an image with a white background is, it has a much harder time making conclusions.
<hr>
Your first guess might be to invert some of the training data so that the network is able to practice on both white backgrounds and black backgrounds. Let's see if it works.
<br>
1. Open your finished first neural network notebook.
<br>
2. Click File &gt; Make a copy to make a copy of it.
<br>
<img src="https://i.imgur.com/NcDD7OK.jpg">
<br>
3. In your cell for preparing the data, above where you convert the type to float32, add this code to invert half of the training images.
<pre>train_images[3000:] = 255 - train_images[3000:]</pre>
4. Run the data preparation cell again.
<br>
<img src="https://i.imgur.com/c8pKV9o.jpg">
<br>
5. Run the model training code again. 
<br>
6. Add a new cell below your model, and paste this code into it. 
<pre>
from keras.preprocessing import image
from PIL import Image,ImageChops<br>
def predict_image(x):
  x = x.astype('float32')
  x = x / 255.0<br>
  print(np.min(x))
  print(np.max(x))<br>
  # images = np.vstack([x])
  # print(images.shape)<br>
  x = np.expand_dims(x,axis=0)
  print(x.shape)<br>
  # x.reshape(0,28,28,1)
  # print(x.shape)
  image_predict = model.predict(x,verbose=0)<br>
  print(np.argmax(image_predict))<br>
  plt.imshow(np.squeeze(x))
  plt.xticks([])
  plt.yticks([])
  plt.show()<br>
  print(image_predict)
  return image_predict<br>
def plot_value_array(predictions_array,true_label):
  # true_label = true_label[0]
  plt.grid(False)
  plt.xticks(range(10))
  plt.yticks([])
  thisplot = plt.bar(range(10),predictions_array[0],color="#777777")
  plt.ylim([-1,1])
  predicted_label = np.argmax(predictions_array)<br>
  thisplot[predicted_label].set_color('red')
  thisplot[true_label].set_color('blue')
  plt.show()
</pre>
7. Download this image to your student folder
<br>
8. Add these lines to load the image into your notebook
<pre>
path = "test3w.jpg" 
img = image.load_img(path,target_size=(28,28),color_mode = "grayscale") 
</pre>
9. Convert the image to an array
<pre>img_arr = image.img_to_array(img)</pre>
10. Call predict_image on your image array
<pre>arr = predict_image(img_arr)</pre>
11. Call plot_value_array.
<pre>plot_value_array(arr,3)</pre>
12. Run the cell.
<br>
<img src="https://i.imgur.com/m8Ze3kt.png">
<h1>Conclusions</h1>
As you can see this does fix the problem you were having, but imagine having to adjust the training data for every new aspect of a test image. This network's usefulness decreases every time the problem that it is trying to solve gets more general. And, since the more general the data gets, the less accurate the network is, you can understand how this kind of network will be less and less effective as the complexity of a problem goes up. 
<br>
So what is the solution? 
<br>
There is another kind of network called Convolutional Neural Networks. These networks are modeled after how a brain thinks, and are much more effective in extracting more general information out of an image than your fully connected network is. 
<br>
Follow along in the next lesson to create a Convolutional Neural Network.
<h1>Recap</h1>
The more general your data is, the harder it is for the network to understand the image data. You can correct for some of these potential issues by pre-processing the data that the network uses to train, or by processing the image before sending it into the network,
<ul>
  <li>Think of another test to do with this network. Can you adjust the parameters to have it work for the new image?</li>
  <li>Try the same test with other images. Come up with theories for why the network isn't recognizing it, and ways to adjust the network for it.</li>
</ul>
