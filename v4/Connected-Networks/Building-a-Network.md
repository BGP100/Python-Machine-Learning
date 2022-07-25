<a href="/v4/Connected-Networks/Preparing-Data.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Connected-Networks/Improving-Your-Network.md">Next &gt;</a>
<hr>
Neural networks learn to accomplish their tasks by reading training data and adjusting their neuron weights to improve their chance of choosing the correct answer.
<br>
The first kind of network you will create is a densely connected network. In this network, layers of neurons are connected to each other. The output from one layer becomes the input for the next one. These layers manipulate and reshape the data so that the computer can make a guess as to what the output should be.
<br>
You are going to use a framework called TensorFlow to build, compile and run your first neural network that will be able to detect handwritten digits.
<br>
1. Add a new code cell to your notebook.
<br>
2. Import the relevent libraries
<pre>
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense,Flatten
</pre>
<h1>Epochs</h1>
Training is done in a sequence of rounds called epochs. Each epoch is one pass over the dataset.  Meaning, in each epoch, every image in the dataset is passed through your model once.  Generally, the more epochs you run, the better your results, but the longer it will take to train.  Finding the sweet spot between good results and reasonable runtime is a big challenge in training a model.
<br>
To start, run 10 epochs.
<br>
1. Add a variable to keep track of epochs
<pre>epochs = 10</pre>
<h1>Model Type</h1>
You'll be making a sequential model. Sequential models are split into layers. A layer is one set of neurons that processes the inputs from the previous layer, then passes it along to the next layer.  The first layer reads in the original data, and the final layer produces the network's prediction.
<br>
Determining how many and what kinds of layers to use, and configuring each individual layer is the meat of building a neural network. You'll do this in the next steps, but first, define your model:
<br>
1. Make a new model object using the Keras Sequential command. Make sure to capitalize the S.
<pre>model = Sequential()</pre>
<img src="https://i.imgur.com/sIPtyYA.png">
<h1>Add The First Layer</h1>
The first layer to add to this network is a flatten layer. This will take your prepared image data and flatten it into a long series of numbers representing pixels (remember when yo prepared the data for this?). This allows the network to take in the data from the image and begin to perform calculations with it. This layer is also known as the input layer, as it takes input.
<br>
This layer needs to know what the input shape is. Luckily, while preparing the data, you saved the input shape to a variable, so you can use that. 
1. Below your model declaration, add a flatten layer. You'll add parameters in the next steps. 
<pre>model.add(Flatten())</pre>
2. Indicate the input_shape. This should be equal to the 
<pre>model.add(Flatten(input_shape=input_shape))</pre>
<img src="https://i.imgur.com/jmQWw9h.png">
<h1>Adding the Calculation Layers</h1>
Next, we need to add a layer to perform predictions on the data. There are a lot of different configurations for this middle part, and a lot of machine learning research is about how to best set these layers up.
<br>
For right now, you are going to add just one, with 16 neurons. You will also need to decide on an activation algorithm. 
<br>
1. Add a Dense layer to your network.
<pre>model.add(Dense())</pre>
<br>
2. Update the line to add the size of the layer in neurons.
model.add(Dense(units=16))</pre>
<br>
3. On the same line, set the activation function. You will use relu in this case as it is the best one for this problem. 
<pre>model.add(Dense(16,activation='relu'))</pre>
<img src="https://i.imgur.com/jqQwYDG.jpg">
<h1>Output Layers</h1>
The final stage of the network is the output layer. It needs to shrink the previous layer down to just the number of possible classes.  Then, each output of this final layer represents the network's guess on how likely the input is to be from that class.
<br>
Note that this means that the network produces multiple results for each image, one for each class.  The final decision of the model is the class with the highest weight, determined during training and testing.
<br>
Since this data has digits from 0-9, there are ten possible answers. 
<br>
1. Add your output layer.
<pre>model.add(Dense(10))</pre>
2. Add this code to print a summary of your network so far. 
<pre>model.summary()</pre>
<img src="https://i.imgur.com/CTFtCCM.jpg">
<br>
Now, when you run the cell, you should be able to see output about what your network looks like.
<br>
<img src="https://i.imgur.com/wTab2CS.png">
<br>
As you can see from the output, we have a sequential model, with three layers that reshape the data. There are already 12,730 parameters to train. This means that the network is going to adjust 12,730 numbers each time it runs an epoch. Hopefully, this will be enough to correctly identify the number in the image.
<h1>Compiling and Training the Network</h1>
Now, it is time to compile the network. Tensorflow has a command that will do a lot of the work for you, but you still need to set up a few arguments so that this network is compiled in a way that is useful to you.
<br>
You are going to add this line to compile your network and then read below to learn more about what each argument represents.
<br>
<img src="https://i.imgur.com/dah7c16.jpg">
<br>
After adding the code below, your network will be able to output a decision on what class an image belongs to.
<br>
1. Add the compile function after the layers of the model:
<pre>model.compile()</pre>
<br>
2. Add the loss function to the compile function:
<pre>model.compile(loss='categorical_crossentropy')</pre>
<br>
3. Use the optimizer parameter to set the optimization algorithm:
<pre>model.compile(loss='categorical_crossentropy',optimizer='adam')</pre>
<br>
4. Add this line
<pre>model.compile(loss='categorical_crossentropy',optimizer='adam',metrics=['accuracy'])</pre>
<h1>Training</h1>
Now that you have a compiled model, you can fit that model to the actual data that you prepared. The fit stage will use the training data to train the model to recognize numbers.
<br>
The train_images data set will be the input, the train_labels will keep track of if the network guess is correct or not, and the epochs will be equal to the variable you set up earlier. 
<br>
1. Add the fit function:
<pre>model.fit()</pre>
<br>
2. Set the input data for this model.
<pre>model.fit(train_images,train_labels)</pre>
<br>
3. Add the epochs to the fit stage.
<pre>model.fit(train_images,train_labels,epochs=epochs)</pre>
<br>
4. Randomly shuffle the data so that the network doesn't rely on the order to learn. 
<pre>model.fit(train_images,train_labels,epochs=epochs,shuffle=True)</pre>
<img src="https://i.imgur.com/wihvACz.png">
<h1>Analyzing the Output</h1>
Knowing how well the model did on the training data isn't very useful.  It doesn't mean much if you can get an A on a test where you're given the answers.
<br>
The real test of a model is how well it does on data it hasn't seen before and doesn't know the labels for.  That's exactly what the model.evaluate function is for.
<br>
This function takes the trained model and the test data and produces a set of scores, or metrics, that show how well the model did on this test data.
<br>
While model.evaluate takes the test labels as input, they're never shown to the neural network, only used to compare the network's answer to the real answer.
<br>
After evaluation, the final point of this function is to return the model object for use later as needed.
<br>
1. Add this code to calculate the loss and accuracy of your model.
<pre>test_loss,test_acc = model.evaluate(test_images,test_labels,verbose=2)</pre>
2. Print out the test accuracy.
<pre>print('\nTest accuracy:',test_acc)</pre>
3. Run the cell.
<br>
<img src="https://i.imgur.com/d8LDaOv.png">
Your output should look something like the screenshot above! For each epoch, you can see the loss and the accuracy of the network on the training data. As you can see, the accuracy goes up with each epoch, and the loss goes down. 
<br>
Finally, the test accuracy tells you how accurate the network was with the test data. 
<br>
For this particular run, this model was 95% accurate on the test data. That's pretty good! 
<h1>Exporting your Model</h1>
Finally, now that you have a finished model, you can export it. Follow these steps to download a copy of your network.
<br>
1. Below your code, add another cell.
<br>
2. Inside that cell, add this code
<pre>model.save('my_model.h5')</pre>
<br>
3. Run the cell.
<br>
4. Go to the Jupyter Notebook dashboard.
<br>
<img src="https://i.imgur.com/LHlq3s3.jpg">
<br>
5. View the my_model.h5 output file.
<br>
<img src="https://i.imgur.com/WGnol24.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/3SpYgcp.png">
<h1>Recap</h1>
Neural networks add layers of neurons to perform calculations on the data. They use these layers to make predictions about the data that they are being used on. First, they are trained using training data, and then tested using test data. There are a lot of parameters that can be adjusted to make the network better.
<ul>
  <li>Look at the Improving Your Network lesson to make the network better</li>
</ul>
