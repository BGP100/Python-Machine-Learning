<a href="/v4/Text-Generation/Text-Generation-with-RNN.md">&lt; Previous</a>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<a href="/v4/Text-Generation/Generate-Text-with-RNN.md">Next &gt;</a>
<hr>
<h1>Relational Neural Networks</h1>
Now that you have a dataset ready to be used to train a network, it's time to start building your network. In order to do text generation, you will be using a Relational Neural Network, or an RNN.
<br>
Your network will maintain an internal state that gets updated with each sequence that gets added to the network. This way, it will "remember" the input that came before it. Each time you run the network, you will be giving it input data, and the previous state of the network. It will use this information to update its state, and also predict what the next input should be. 
<br>
These networks are very powerful, and you are about to see them in action!
<h1>Building Your Network</h1>
Now it's time to start building your RNN. In the past, we have simply put together a sequential model by adding layers to it. However, since this network works a little differently, you will be setting up the structure of the network and also creating a way to maintain its internal state at the same time. 
<br>
This means that you will be creating a class called MyModel that will both outline the structure of your RNN and create a call function that will help update the network with the addition of a new character.
<br>
To start, set a few key variables that will be used when you create your network.
<br>
1. Continue working in your notebook from the previous lesson.
<br>
2. Set vocab size to the length of the vocab.
<pre>vocab_size = len(vocab)</pre>
3. Decide on an embedding dimension. This will set how many different dimensions the network should look at the data with.
<pre>embedding_dim = 256</pre>
4. Finally, decide on how many units the rnn will have.
<pre>rnn_units = 1024</pre>
<img src="https://i.imgur.com/yHR5qcx.png">
<br>
5. Define a class called MyModel inheriting the Keras Model class.
<pre>class MyModel(tf.keras.Model):</pre>
6. Inside the class, create an init function that takes vocab size, embedding dimension and RNN units as an argument. 
<pre>
def __init__(self, vocab_size,embedding_dim,rnn_units):
  super().__init__(self)
</pre>
7. Add the layers for this network:
<pre>
self.embedding = tf.keras.layers.Embedding(vocab_size,embedding_dim) 
self.gru = tf.keras.layers.GRU(rnn_units,return_sequences=True,return_state=True)
self.dense = tf.keras.layers.Dense(vocab_size)
</pre>
<img src="https://i.imgur.com/QucIw70.png">
<br>
8. Add your call method. This updates the internal state with each new letter that gets added.
<pre>
def call(self,inputs,states=None,return_state=False,training=False):
  x = inputs
  x = self.embedding(x,training=training)
  if states is None:
    states = self.gru.get_initial_state(x)
  x, states = self.gru(x,initial_state=states,training=training)
  x = self.dense(x,training=training)
  if return_state:
    return x,states
  else:
    return x
</pre>
<img src="https://i.imgur.com/W441cTe.png">
<br>
9. Create an instance of your model using the variables you set above.
<pre>model = MyModel(vocab_size=len(ids_from_chars.get_vocabulary()),embedding_dim=embedding_dim,rnn_units=rnn_units)</pre>
<img src="https://i.imgur.com/rHAFgyh.png">
<br>
10. Create an example batch using a random input example batch and target example batch from the dataset. Use that to see what the batch size, sequence length, and vocab size is.
<pre>
for input_example_batch,target_example_batch in dataset.take(1): 
  example_batch_predictions = model(input_example_batch) 
  print(example_batch_predictions.shape,"| (batch_size,sequence_length,vocab_size)")
</pre>
<img src="https://i.imgur.com/Li90q0m.jpg">
<br>
11. Print a summary of the model.
<pre>model.summary()</pre>
<img src="https://i.imgur.com/F9p8SEI.png">
<h2>Random Example</h1>
Just to see how the network will function, take a random sample of the data, and see how it could function. 
<br>
1. Create some random sampled indices from the data.
<pre>
sampled_indices = tf.random.categorical(example_batch_predictions[0],num_samples=1)
sampled_indices = tf.squeeze(sampled_indices,axis=-1).numpy()
</pre>
2. Print those indices.
<pre>print(sampled_indices)</pre>
3. Using your text_from_ids function, print the input text.
<pre>print("Input:\n",text_from_ids(input_example_batch[0]).numpy())</pre>
4. And view the predictions from the network.
<pre>print("Next Char Predictions:\n",text_from_ids(sampled_indices).numpy())</pre>
<img src="https://i.imgur.com/tPf6c1d.jpg">
<br>
As you can see, the predictions are nonsense. However, the output is the right amount of text. This tells you that the structure of the network is working, but since it is not trained the output is nonsense. Now it's time to train the network.
<h1>Training</h1>
Since you know the structure of your network works, it's time to train it. Now that you have input and target outputs, you are essentially just looking at a classification problem. You have input in the form of the internal state and character, and the task is to predict the next character.
<br>
Since this is a classification problem, a lot of the process will be familiar. The main difference will be the use of checkpoints. You will use checkpoints to save the model at different stages of the training. This way if the training fails, you will be able to restart it from a previous stage of training instead of having to start over. 
1. The loss function will be categorical crossentropy.
<pre>loss = tf.losses.SparseCategoricalCrossentropy(from_logits=True)</pre>
2. Using the example from before, calculate an example mean loss.
<pre>example_batch_mean_loss = loss(target_example_batch,example_batch_predictions)</pre>
3. Print your prediction shape and your mean loss.
<pre>
print("Prediction shape:",example_batch_predictions.shape,"| (batch_size,sequence_length,vocab_size)")
print("Mean loss:",example_batch_mean_loss)
</pre>
4. In order to check that everything is initialized and working properly, check that the exponential of the average loss is close to the vocab size.
<pre>tf.exp(example_batch_mean_loss).numpy()</pre>
<img src="https://i.imgur.com/jpXJjKB.jpg">
<br>
5. Compile your model, using adam as your optimizer.
<pre>model.compile(optimizer='adam',loss=loss)</pre>
6. Since this training will take some time, you are going to save checkpoints throughout the training process. 
<pre>
checkpoint_dir = './training_checkpoints'
checkpoint_prefix = os.path.join(checkpoint_dir,"ckpt_{epoch}")
checkpoint_callback = tf.keras.callbacks.ModelCheckpoint(filepath=checkpoint_prefix,save_weights_only=True)
</pre>
7. Set the epochs for this round of training.
<pre>EPOCHS = 20</pre>
8. And train the network using the fit function.
<pre>history = model.fit(dataset,epochs=EPOCHS,callbacks=[checkpoint_callback])</pre>
<img src="https://i.imgur.com/cuSOXfy.jpg">
<br>
Here's what your project could look like at this point:
<br>
<img src="https://i.imgur.com/Rt0wcAh.png">
<h1>Recap</h1>
To make an RNN you will set up a class and initialization function. Then you will add layers and set up a structure so that you can train your network. 
<ul>
  <li>Let your network train before moving on.</li>
</ul>
