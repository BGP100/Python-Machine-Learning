<a href="/v4/Sentiment-Analysis/BeautifulSoup-Challenges.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Sentiment-Analysis/Use-the-Model-in-Text.md">Next &gt;</a>
<hr>
<h1>Creating the Network</h1>
So far you have cleaned up and prepared the data and vectorized it. Now, it's officially time to create the network to understand the text. Now that we have text as number input and three categories of output, this is essentially just a classification problem. Thus, you can create a network that does classification.
<br>
In order to create the model, you will use a sequential model. You will create an input layer, several calculation layers, dropout layers, and an output layer. 
<br>
Follow these steps to create the model.
<br>
1. Continue working in your Preparing Data and Vectorizing Text notebook.
<br>
2. Create a sequential model
<pre>model = Sequential()</pre>
<img src="https://i.imgur.com/SFUCa6U.png">
<h2>Input Layer</h2>
The input layer is the first layer of the network. It takes all of the text input and starts to perform calculations with it. This layer needs to be pretty large so that the network can start to get an idea of what it's dealing with. This one is set to 4000 neurons, but if you want to go larger you can!
<br>
Also, for this layer, you will be deciding on an activation algorithm. Relu is one that works well for these purposes. 
<br>
3. Add an input layer to the network.
<pre>model.add(Dense(units=4000,activation="relu"))</pre>
<img src="https://i.imgur.com/y1cZlmX.png">
<h2>Dropout Layers</h2>
Another important aspect of this model is the dropout layers. These help prevent the network from relying too much on specific neurons and force all the neurons to do some work. This is especially important for large networks like this one. This one is set to drop out at a rate of 0.5 which means half of the neurons. 
<br>
4. Add a dropout layer.
<pre>model.add(Dropout(0.5))</pre>
<img src="https://i.imgur.com/ZSkZTqD.png">
<h2>Calculation Layers</h2>
Once you have the input, it's time to start actually doing calculations with it. This part of the network will do the bulk of the calculation. It's important to include dropout layers in this part of the network as well so that the network continues to be versatile. 
<br>
5. Add some calculation layers to this network. You can add as many as you like.
<pre>
model.add(Dense(units=2000,activation="relu"))
model.add(Dropout(0.5))
model.add(Dense(units=500,activation="relu"))
model.add(Dropout(0.5))
model.add(Dense(units=250,activation="relu"))
model.add(Dropout(0.5))
</pre>
<img src="https://i.imgur.com/5MWChwo.png">
<h2>Output Layer</h2>
Finally, you will add a layer that outputs the network's decision. The number of neurons for this layer is going to be the number of possible categories. In this case, there are three possible outputs: positive, negative, neutral. The activation algorithm will be softmax, an algorithm that creates a probability that each review belongs in each category.
<br>
6. Add an output layer. This needs to have three neurons: one for each possible outcome. 
<pre>model.add(Dense(units=3,activation="softmax"))</pre>
<img src="https://i.imgur.com/TemDCn7.png">
<h2>Compiling the Network</h2>
Now that you have all the layers set up, it's time to finally compile the network. First, you will create a variable to hold the optimizer and then you will compile the network.
<br>
The optimizer is going to be a general-purpose algorithm called adam that will work well for this purpose. The loss algorithm is categorical crossentropy since this problem is bout sorting data into categories, and the metric to watch is accuracy. 
<br>
7. Create a variable to keep track of the optimizer. For this, you are going to use Adam, an extremely effective multi-purpose algorithm. 
<pre>opt = tf.keras.optimizers.Adam(learning_rate=0.001)</pre>
8. Compile the model. 
<pre>model.compile(loss="categorical_crossentropy",optimizer=opt,metrics=["accuracy"])</pre>
<img src="https://i.imgur.com/7BV5bDk.png">
<h2>Fit Data to the Network</h2>
Next, you will train the network using the data that you have prepared. During this stage, you will also decide on batch size and the number of epochs. Finally, you will set the validation data to the test datasets you created.
<br>
9. Fit the data to the model.
<pre>model.fit(x=x_rev_train_v,y=y_pol_train,batch_size=256,epochs=10,validation_data=(x_rev_test_v,y_pol_test))</pre>
<img src="https://i.imgur.com/B3K6wxh.png">
<h2>Evaluating the Network</h2>
Once the network is done training, you will get the scores from the model, and print out the accuracy. This will give you a good idea of how the network performs on the test data. This network should give an accuracy of about 0.70, which is pretty good. 
<br>
10. Get the scores by evaluating the model.
<pre>scores = model.evaluate(x_rev_test_v,y_pol_test,verbose=0)</pre>
11. Print the accuracy.
<pre>print('Test accuracy: ',scores[1],'%')</pre>
<img src="https://i.imgur.com/rPbgJmz.png">
<h2>Save the Model</h2>
In the same cell as all the other model creation code, make sure you add the code to export the model. This way you won't have to wait for it to train in the future. 
<br>
12. Export the model when it's done for future use.
<pre>model.save('sentiments.h5')</pre>
13. Run the cell to train the model.
<br>
<img src="https://i.imgur.com/oxXY0Uh.png">
<br>
This network is very large and contains a lot of information. It will take quite a while to train, so go ahead and let it run as long as it needs. Just be sure to leave the tab open while it makes its calculations.
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/W3PlfJw.png">
<h1>Recap</h1>
Creating a network that can classify text based on sentiment required a sequential network with a bunch of layers of neurons. You created, trained, and exported this model.
