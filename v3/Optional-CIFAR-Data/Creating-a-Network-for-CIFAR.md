<a href="/v3//Optional-CIFAR-Data/Preparing-CIFAR-Data-Challenge.md.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v3/Optional-CIFAR-Data/Test-Your-CIFAR-Network.md">Next &gt;</a>
<hr>
Now that you have your data prepared it is ready to feed into a network. Since this data is so complicated, it makes sense to use another convolutional network. This kind of network will be slightly less computationally needy and will be able to draw conclusions about the data.  
<br>
Since you already understand most of the concepts for a convolutional network, this network will allow you to see how those apply to a larger, more general dataset. This network is going to be much more robust and therefore take more time and computing power to train. 
<br>
1. Import all necessary libraries. You'll notice the addition of Batch Normalization layers, which you will learn about in a few steps.
<pre>
from tensorflow.keras.models import Sequential 
from tensorflow.keras.layers import Dense,Dropout,Flatten,Conv2D,MaxPooling2D,BatchNormalization
</pre>
<br>
2. Decide on the number of epochs, batch size, and set the model type. Just like before, you can adjust these as you test your network.
<br>
<img src="https://i.imgur.com/CQ8BhG0.png">
<h1>Adding Convolutional Layers</h1>
Now that the model is set up, it's time to start adding layers to your network. The last convolutional network you made had one round of convolutional layers followed by a pooling layer, and then some layers to wrap up the network and output a decision.
<br>
This network is going to need more rounds of layers to figure out information about the pictures. As the layers at first start to decipher what is in the image, the network will start to understand what parts of the image it needs to focus on to understand what it is. This is what makes convolutional neural networks so effective for image recognition. 
<br>
Follow these steps to start to build out the layers of this network. 
<br>
1. To start add a convolutional layer with 32, 3x3 pixel filters.
<pre>model.add(Conv2D(filters=32,kernel_size=(3,3),activation='relu',input_shape=input_shape))</pre>
<br>
2. Add another one:
<pre>model.add(Conv2D(filters=64,kernel_size=(3,3),activation='relu',input_shape=input_shape))</pre>
<br>
3. Add a pooling layer to condense the information the network has learned so far.
<pre>model.add(MaxPooling2D(pool_size=(2,2)))</pre>
<br>
4. Add a dropout layer so the network doesn't get too dependent on any specific neurons.
<pre>model.add(Dropout(rate=0.2))</pre>
<h1>Batch Normalization</h1>
Batch normalization is a process that helps standardize the data in between layers. In a more complicated neural network, as each layer reshapes the data it can quickly become extremely complicated, and the network can lose sight of what the goal is. Batch normalization helps to keep each layer on the right track and working towards the desired goal. 
<br>
5. Add a batch normalization layer beloww the rest of the layers. 
<pre>model.add(BatchNormalization())</pre>
<img src="https://i.imgur.com/2obXzCM.png">
<br>
That rounds off the first stage of this network. You have added convolutional layers with filters to help learn about the image, a pooling layer to condense and organize the information that the network has learned, a dropout layer to prevent overfitting, and a batch normalization layer to help keep all the data normalized. Now it's time to add another set of layers.
<h1>Adding More Layers</h1>

Because this data is so complicated, you are going to add two more rounds of convolutional layers, pooling layers, dropout layers, and batch normalization. This will help the network to do what it needs to do.
<br>
1. Add a convolutional layer...
<pre>model.add(Conv2D(filters=64,kernel_size=(3,3),activation='relu'))</pre>
<br>
2. ...a max pooling layer....
<pre>model.add(MaxPooling2D(pool_size=(1,1)))</pre>
<br>
3. ....a dropout layer....
<pre>model.add(Dropout(rate=0.3))</pre>
<br>
4. ...and a batch normalization layer.
<pre>model.add(BatchNormalization())</pre>
<br>
<img src="https://i.imgur.com/YnUJEKu.png">
<h1>The Final Stage of Layers</h1>
Add another set of layers.. This one will need two layers with a lot of filters to help extract more information from the image.
<br>
Below the previous layers, follow the steps to add the last set of layers.
<br>
1. Add a convolutional layer with 128 filters.
<pre>model.add(Conv2D(filters=128,kernel_size=(3,3),activation='relu'))</pre>
2. Add another one, with 64 filters.
<pre>model.add(Conv2D(filters=64,kernel_size=(3,3),activation='relu'))</pre>
3. Add a pooling layer with a small pool size.
<pre>model.add(MaxPooling2D(pool_size=(1,1)))</pre>
4. Add a dropout layer.
<pre>model.add(Dropout(rate=0.3))</pre>
5. Add a batch normalization layer.
<pre>model.add(BatchNormalization())</pre>
<img src="https://i.imgur.com/XdvdVzR.png">
<h2>The Output Layers</h2>
Now it's time to prepare the data for the output. You will need to add some layers to organize the information that the network has and reshape it into the decision layer.
<br>
4. Add a flatten layer to start to prepare the network to produce output. 
<pre>model.add(Flatten())</pre>
5. Add a dense layer. 
<pre>model.add(Dense(units=128,activation='relu'))</pre>
6. Add the output layer. 
<pre>model.add(Dense(units=num_classes,activation='softmax'))</pre>
7. Print the summary of the network. 
<pre>model.summary()</pre>
<img src="https://i.imgur.com/LferMyT.png">
<h1>Compiling and Training the Model</h1>
Now that you have the network, you can compile and train it. Just like with all the other networks, you can use Keras's built-in functions to do this. First, you will compile the model and decide on a loss function, optimizer, and metrics. Then, you will use the fit function to train the model using the data. Finally, evaluate the model using the evaluate function. 
<br>
1. First, compile the network. 
<pre>model.compile(loss=keras.losses.categorical_crossentropy,optimizer='adam',metrics=['accuracy'])</pre>
<br>
2. Fit the model to the data you prepared. 
<pre>model.fit(train_images,train_labels,batch_size=batch_size,epochs=epochs,validation_data=(test_images,test_labels),shuffle=True)</pre>
<br>
3. And evaluate the model
<pre>
scores = model.evaluate(test_images,test_labels,verbose=0) 
print('Test accuracy:',scores[1])  
</pre>
4. Run the cell to train your network. 
<br>
<img src="https://i.imgur.com/ofNjIK8.png">
Training this network will take a lot longer than the previous ones. Leave the tab open and let it train for as long as it needs. The accuracy might be a bit lower on this one as well, but if you can get it up to ~70%, it is successful!
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/sGqzVyU.png">
<h1>Recap</h1>
More complicated datasets require more robust datasets that take a lot longer to train.  The CIFAR-10 Dataset is a more general image recognition dataset and requires a more robust network to solve it. 
<ul>
  <li>Adjust your network to see if you can make it more accurate.</li>
  <li>Run some test images through the network to see what kinds of things it can recognize.</li>
</ul>
