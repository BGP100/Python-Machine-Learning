<a href="/v3/CNN/Intro-to-CNN.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/CNN/Test-Your-CNN.md">Next &gt;</a>
<hr>
So far you have been working with densely connected networks. With enough training data and enough neurons, a densely connected network could solve just about any problem. 
<br>
However, a convolutional neural network is especially effective for image classification problems. This is because convolutional networks are really good at understanding how data is connected. The structure of the network is such that it inherently learns what parts of the data matter most, and how they are connected. Additionally, for more complicated data, a convolutional network helps keep the number of neurons needed down.
<br>
<b>Note:</b> Convolutional neural networks imitate the structure of neurons that process images in the brain and use techniques to reduce neuron count, as well as maintaining positional relationships in the data.
<br>
You are going to build a convolutional network for the MNIST set of data to recognize handwritten digits, and then be able to see what works differently.
<h1>Set Up Your Notebook</h1>
You have already written all the code needed to prepare the data for the Convolutional Neural Network. You will continue from that work for this network 
<br>
1. Make a copy of your data preparation notebook (or <a href="https://drive.google.com/uc?id=1Xokspa6dJAMGDjSbnfIeOpoPFtgR6N-L&export=download">download this one</a> to your class folder).
<br>
2. Rename it to "CNN.ipynb".
<br>
3. Run all the data preparation code again. 
<br>
4. Make a new cell to start writing code in.
<br>
<img src="https://i.imgur.com/fRryc4K.png">
<h1>Creating Your Network</h1>
Like with the densely connected network, you are going to set up epochs. Remember, epochs are how many rounds the network will have, or how many times it should pass over the data.
<br>
You will also define this network as Sequential. Convolutional networks, like densely connected ones, take the output from one layer to feed in as input in the next layer. However, the type of layers that this network uses will be different. 
<br>
Add epochs and define the model. 
<br>
1. Set a variable for epochs.
<pre>epochs = 10</pre>
<br>
2. Make a new model object using the Keras Sequential command. Make sure to capitalize the S.
<pre>model = Sequential()</pre>
<br>
<img src="https://i.imgur.com/v8DKDf6.png">
<h1>Adding Layers</h1>
With your densely connected network, you added three fully connected (or dense) layers. The layers in this network are convolutional layers and work a little differently. 
<br>
Convolutional layers use small clusters of neurons called filters that are moved across the image and activate based on the pixels they see. These clusters learn to recognize features in the data.
<br>
You can adjust the number and size of filters in the layer — larger filters observe larger areas of the image at once, while smaller filters spot finer detail. A higher filter count will allow recognizing a wider range of features.
<br>
There are multiple advantages to having filters that work this way:
<ol>
  <li>Small filters are more computationally efficient since they only examine a small portion of the image at once.</li>
  <li>Just like in real life, the filter can do a better job by focusing on a small simple problem and ignoring the distraction of the rest of the image.</li>
  <li>Because the filters are moved across the entire image, convolutional networks are good at identifying two images that have the same object but in different places in each image.</li>
</ol>
Your network will use multiple layers of convolutions to learn its task.
<h2>Implementing Convolutional Layers</h2>
Keras provides functionality to easily create convolutional layers for your neural networks. You'll use the function  Conv2D  to create the first convolutional layer of your network.
<br>
1. Below the declaration of your model, add a Conv2D layer. You'll modify this by adding parameters in the next steps.
<pre>model.add(Conv2D())</pre>
2. Add filters, which each learn something different about the image before passing it on to the next layer. A good number to start with is 32.
<pre>model.add(Conv2D(filters=32))</pre>
3. Specify how big each filter is by adding the kernel size in pixels, in this case a 3x3 square.
<pre>model.add(Conv2D(filters=32,kernel_size=(3,3)))</pre>
4. Next is the activation function which is the same as before: relu. 
<pre>model.add(Conv2D(filters=32,kernel_size=(3,3),activation='relu'))</pre>
5. Finally, add the input shape. 
<pre>model.add(Conv2D(filters=32,kernel_size=(3,3),activation='relu',input_shape=input_shape))</pre>
<img src="https://i.imgur.com/iIwXwYm.png">
<h1>Pooling Layers</h1>
Processing images with convolutional layers can get computationally intense rather quickly. Successive layers of convolutions increase the number of neurons and computation time required.
<br>
<b>Note:</b> Convolutional networks use pooling layers to manage that growth of complexity by simplifying and shrinking the data set.
<br>
Pooling layers use a filter that moves across the data with a specified stride, simplifying the contents of each filter into a single value. This shrinks the size of the layer's output based on the filter's size.
<br>
This also helps reduce the network's translation variance, which is how sensitive the network is to an object's exact position in an image.
<br>
The most common pooling layer is a 2x2 filter with a stride of 2. This results in the width and the height of the input layer being reduced by half. This simplifies the data without too much loss of specificity in the image.
<br>
<h2>Adding a Pooling Layer</h2>
Keras uses the <code>MaxPooling2D</code> function to create 2D pooling layers.
<br>
1. Below the second Conv2D layer, add a new 2D pooling layer:
<pre>model.add(MaxPooling2D()))</pre>
<br>
2. Add the pool_size to the layer:
<pre>model.add(MaxPooling2D(pool_size=(2,2)))</pre>
If the stride isn't specified, it's set to match the <code>pool_size</code>, in this case, 2.
<br>
<img src="https://i.imgur.com/2YXgQJ1.png">
<br>
<b>Note:</b> Convolutional Neural Networks often have more then one set of alternating Convolutional and Pooling Layers.
<h1>More Convolutional Layers</h1>
By design, convolutional layers can examine the low-level features of an image. By adding more convolutional layers the network can start to work with higher-level features.
<br>
This layer is defined the same way as the last one, except for more filters, 64 here vs. 32 before. Also, the input shape doesn't need to be defined, since it's inferred from the previous layer.
<br>
1. Add another layer to the network.
<pre>model.add(Conv2D(filters=64,kernel_size=(3,3),activation='relu'))</pre>
<img src="https://i.imgur.com/omsKb2a.png">
<br>
Dropout Layers

A dropout layer takes a percentage of all the neurons in the input and deactivates them at random. This random dropout of neurons forces more of the network to adapt to the task.

Without a dropout layer, larger networks run the risk of growing overdependent on a small set of competent neurons rather than the whole network learning the task.
<br>
1. Add a dropout layer using the Dropout function:
<pre>model.add(Dropout())</pre>
<br>
2. Set the percentage of inputs to be dropped, the rate.  Here it's 0.3, or 30%:
<pre>model.add(Dropout(rate=0.3))</pre>
<br>
3. Add another convolutional layer with 32 filters to finish off the network.
<pre>model.add(Conv2D(32,(3,3),activation='relu'))</pre>
<img src="https://i.imgur.com/n9bfTmq.png">
<h1>Dense and Flatten Layers</h1>
At the end of the convolutional and pooling layers, you'll need to set up some neurons to help make your final classification decision. This will be a standard, fully connected layer of neurons. In order to connect these layers, you'll first need to flatten the 2D image's filters.
<br>
Keras uses the <code>Flatten</code> function to create a flattening layer, and the  Dense  function to create dense layers.
<br>
<code>units=32</code> is how big the output of the Dense layer will be, in this case, 32 neurons.
<br>
1. Add a flattening layer using the <code>Flatten</code> function:
<pre>model.add(Flatten())</pre>
<br>
2. After this layer, add a dense layer using the <code>Dense</code> function:
<pre>model.add(Dense())</pre>
<br>
3. Set the size of the dense layer in neurons by changing the <code>units</code> parameter:
<pre>model.add(Dense(units=32))</pre>
<br>
4. The dense layer uses the same activation function, <code>relu</code> as the Convolutional Layers. Set the activation parameter accordingly:
<pre>model.add(Dense(units=32,activation='relu'))</pre>
<img src="https://i.imgur.com/WX7pw2x.png">
<h1>Output Layers</h1>
Just like with your fully connected network, the final layer needs to shrink the previous layer down to just the number of possible classes. Like before, the decision is represented by the class with the highest weight. 
<br>
1. The final layer is a dense layer. Add one after the dropout layer:
<pre>model.add(Dense())</pre>
<br>
2. The output layer should have as many outputs as there are classes, set with the  units  parameter:
<pre>model.add(Dense(10))</pre>
<br>
3. This layer uses a different activation function  softmax , which is more appropriate to this setting. Set it with the  activation  parmeter:
<pre>model.add(Dense(10, activation='softmax'))</pre>
<br>
4. Add this to print out a summary of your network.
<pre>model.summary()</pre>
<br>
<img src="https://i.imgur.com/fHhhqqW.png">
<br>
Now the brain of your image classifier is finished! Next, you'll need to establish training and testing operations so you can use it.
<h1>Compiling the Model</h1>
Just like with your first network, you are going to compile this network. The loss and metrics will be the same as your last network: categorical_crossentropy, and accuracy. This time, however, you are going to use a different training algorithm called RMSProp. 
<br>
RMSProp is one of several different training algorithms Keras defines to do the computation that actually teaches the network how to improve. For the neural network, the goal is to optimize the loss by making it as small as possible. RMSProp is one way the network can do this. 
<br>
Add this line to compile your network. 
<br>
1. Add the compile function after the layers of the model:
<pre>model.compile()</pre>
2. Add the loss function to the compile function:
<pre>model.compile(loss='categorical_crossentropy')</pre>
3. Use the optimizer parameter to set the optimization algorithm:
<pre>model.compile(loss='categorical_crossentropy',optimizer='rmsprop')</pre>
4. Add accuracy as one of the metrics output by the model:
<pre>model.compile(loss='categorical_crossentropy',optimizer='rmsprop', metrics=['accuracy'])</pre>
<img src="https://i.imgur.com/fHhhqqW.png">
<h2>Training</h2>
The fit function does the actual work of running the training. Now that the data has been processed and the model has been defined and compiled it is time to actually train the model on the data. In this network, you are going to use validation data to get an idea of how the network is performing with each epoch, instead of just once at the end. 
<br>
Let's look at the parameters of this function.
<br>
1. Add the <code>fit</code> function after the <code>compile</code> function:
<pre>model.fit()</pre>
2. Set the input data:
<pre>model.fit(train_images,train_labels)</pre>
3. Set the batch_size to 64 so the data gets fed through the network in batches of 64:
<pre>model.fit(train_images,train_labels,batch_size=64)</pre>
4. Set the epochs to match the epochs defined earlier:
<pre>model.fit(train_images,train_labels,batch_size=64,epochs=epochs) </pre>
5. Validation data is used to determine how well the model is during training. This is separate from testing, which is the next step. Use your test data:
<pre>model.fit(train_images,train_labels,batch_size=64,epochs=epochs,validation_data=(test_images,test_labels))</pre>
6. Randomly shuffle the input data before running the model. This is important so that each run is different and the model isn't relying on the order of the images to learn about them:
<pre>model.fit(train_images,train_labels,batch_size=64,epochs=epochs,validation_data=(test_images,test_labels),shuffle=True)</pre>
<img src="https://i.imgur.com/hUUAj8Y.jpg">
<h2>Evaluation and Returning the Model</h2>
Now that you have created your model, compiled it, and trained it, you need to figure out a way to test it and see how accurate it is on data it hasn't seen yet! Just like with your other network, you will need to evaluate your network.
<br>
The evaluate function returns an object that stores the results of the evaluation. You will be adding a few arguments to this function so the network knows what data to test itself on. 
<br>
Just like with the other stages, Tensorflow has some tools to help you out.
<br>
1. The evaluate function returns a scores object, which stores the results of the evaluation:
<pre>scores = model.evaluate()</pre>
2. Set the test data:
<pre>scores = model.evaluate(test_images,test_labels)</pre>
3. The other parameter to model.evaluate is <code>verbose=0</code>. This tells Keras to not print anything to the screen while the model is evaluating. Removing this causes a very long progress bar to fill up the screen as evaluation is occurring:
<pre>scores = model.evaluate(test_images,test_labels,verbose=0)</pre>
4. Print the accuracy to the screen:
<pre>print('Test accuracy:',test_acc,'%')</pre>
<img src="https://i.imgur.com/ZJYCXVC.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/9cpjib1.png">
<h1>Recap</h1>
Convolutional Neural Networks are a different kind of network that is more prepared to handle image recognition tasks. They use convolutional layers and pooling layers to help extract features from an image. Then, they use dense layers to output a decision.
<ul>
  <li>See if this network can recognize the handwritten 3 image.</li>
  <li>Adjust the network by changing numbers to see if you can improve the accuracy.</li>
</ul>
